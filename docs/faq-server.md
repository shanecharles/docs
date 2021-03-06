## Server-side options in SAFE

The [SAFE template](safe-template) comes with three alternative server technologies out of the box:

* **Saturn** - A simple, flexible F# abstraction layer that runs on top of Giraffe that enables both MVC- and Web API-style services. 
* **Giraffe** - A flexible F# framework for creating web-enabled applications. Giraffe runs on top of ASP .NET Core and the Kestrel server. Giraffe's programming model is itself based on Suave's programming model, but has some differences.
* **Suave** - A flexible F# framework for creating web-enabled applications. Suave comes with its own built-in web server.

## Comparing servers

The diagram below illustrates some of the differences and similarities of the three stacks.

![](img/safe-server-1.png)

 This is also shown in the table below. Both Giraffe's HTTP Handler and  and Suave's WebPart are very similar abstractions; this allows a simple migration path between either server. Meanwhile Saturn, which lives "on top" of Giraffe, provides a set of new higher-level abstractions which delegate down to Giraffe's HTTP Handler.

| | Saturn | Giraffe | Suave |
|-|:-:|:-:|:-:|
| ASP .NET compatible? | Yes | Yes | No |
| F#-first? | Yes | Yes | Yes |
| Core Abstractions | scope, controller and HttpHandler | HttpHandler | WebPart

## Why Saturn?
** Saturn is the default and recommended web server in SAFE**.

Saturn (and Giraffe) runs on top of ASP .NET Core, which comes with an extremely high-performance server that is fully supported by Microsoft, has a huge community of developers and has excellent integration into cloud services such as Microsoft Azure and Amazon Web Services.

In addition, whilst the Giraffe and the Suave programming are extremely composable and fully functional-first, Saturn allows you to take advantage of abstractions such as `application { }`, `scope { }` and `controller { }` which are not only extremely simple to use but will also be familiar to developers from other (non-.NET) web programming models. And since Saturn's abstractions are all *optional*, you can always fall back directly to the lower-level Giraffe model if required.

You'll probably find more samples online that use Suave at the time of writing. However, since Giraffe's programming model is similar to that of Suave, porting them across to Saturn / Giraffe is relatively easy to do.
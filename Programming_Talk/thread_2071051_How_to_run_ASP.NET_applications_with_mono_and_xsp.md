---
title: "How to run ASP.NET applications with mono and xsp"
date: 2012-10-14
forum: Programming Talk
---

### Post by CrimpJiggler on 2012-10-14
I setup mono along with an xsp server and am using monodevelop to make  ASP.NET projects. Everything works but for some reason I can't point the  browser to files (such as css files or images), the browser can never  find them. To view the ASP.NET page I made, I point my browser to [http://localhost:8080](http://localhost:8080).  Lets say I make an images folder and put image.jpg into it. If I wanna  view the image, I should be able to just point the browser to [http://localhost:8080/images/image.jpg](http://localhost:8080/images/image.jpg)  but it doesn't work. If I use the HTML tag <img  src="images/image.jpg">, it can't display the image cuz it can't find  it. I've tried xsp2 and xsp4.
 
 If I open the source with firefox then click on the link to the image in the source code, heres what comes up:
 
 > 
 [System.Web.HttpException]: The controller for path '/images/image.jpg' was not found or does not implement IController.
 at  System.Web.Mvc.DefaultControllerFactory.GetControllerInstance  (System.Web.Routing.RequestContext requestContext, System.Type  controllerType) [0x00000] in <filename unknown>:0 
 at  System.Web.Mvc.DefaultControllerFactory.CreateController  (System.Web.Routing.RequestContext requestContext, System.String  controllerName) [0x00000] in <filename unknown>:0 
 at  System.Web.Mvc.MvcHandler.ProcessRequestInit (System.Web.HttpContextBase  httpContext, IController& controller, IControllerFactory&  factory) [0x00000] in <filename unknown>:0 
 at  System.Web.Mvc.MvcHandler+<>c__DisplayClass6.<BeginProcessRequest>b__2  () [0x00000] in <filename unknown>:0 
 at  System.Web.Mvc.SecurityUtil+<>c__DisplayClassb`1[System.IAsyncResult].<ProcessInApplicationTrust>b__a  () [0x00000] in <filename unknown>:0 
 at System.Web.Mvc.SecurityUtil.<GetCallInAppTrustThunk>b__0 (System.Action f) [0x00000] in <filename unknown>:0 
 at System.Web.Mvc.SecurityUtil.ProcessInApplicationTrust (System.Action action) [0x00000] in <filename unknown>:0 
 at  System.Web.Mvc.SecurityUtil.ProcessInApplicationTrust[IAsyncResult]  (System.Func`1 func) [0x00000] in <filename unknown>:0 
 at  System.Web.Mvc.MvcHandler.BeginProcessRequest  (System.Web.HttpContextBase httpContext, System.AsyncCallback callback,  System.Object state) [0x00000] in <filename unknown>:0 
 at  System.Web.Mvc.MvcHandler.BeginProcessRequest (System.Web.HttpContext  httpContext, System.AsyncCallback callback, System.Object state)  [0x00000] in <filename unknown>:0 
 at  System.Web.Mvc.MvcHandler.System.Web.IHttpAsyncHandler.BeginProcessRequest  (System.Web.HttpContext context, System.AsyncCallback cb, System.Object  extraData) [0x00000] in <filename unknown>:0 
 at System.Web.HttpApplication+<Pipeline>c__Iterator6.MoveNext () [0x00000] in <filename unknown>:0 
 at System.Web.HttpApplication.Tick () [0x00000] in <filename unknown>:0 
 
 

I  only have this problem with MVC projects, not with WebForms projects.  The problem seems to be that if I enter the URL  localhost:8080/images/image.jpg, it treats images as a controller rather  than a directory. Anyone know how to fix this?

---

### Post by oldos2er on 2012-10-14
Moved to Programming Talk.

---

### Post by directhex on 2012-10-15
Aren't you meant to put static content in Content/ with ASP.NET MVC?

Or add a second path to web.config along the lines of [http://pastebin.com/5Zqrm3tU](http://pastebin.com/5Zqrm3tU)

---

### Post by CrimpJiggler on 2012-10-15
I started a new project and I noticed that it works initially so I repeated the steps I made during my previous project one step at a time and I've isolated whats causing the problem. To get razor working on mono, I followed this tutorial:
[http://blog.yojimbocorp.com/2012/08/27/asp-net-mvc3-with-razor-view-engine-using-monodevelop-and-ubuntu-12-04/](http://blog.yojimbocorp.com/2012/08/27/asp-net-mvc3-with-razor-view-engine-using-monodevelop-and-ubuntu-12-04/)
Its titled "ASP.NET MVC3 with Razor view engine using Monodevelop and Ubuntu 12.04", I'm on Ubuntu 11.10 but that shouldn't matter should it?

Anyhow, in that tutorial they tell you to edit the Web.config file and replace the content with the following:
[http://pastebin.com/bnCKw5Hf](http://pastebin.com/bnCKw5Hf)
I've narrowed it down to this step. When I replace my Web.config file with that, static files stop working. If I change it back to the default Web.config file, it starts working again. With the default Web.config file, it doesn't read .cshtml files so I need to edit it but I'm a beginner to all this so I wouldn't know how to edit it manually. I tried adding my own Web.Config file that I got from a Visual Studio MVC3 project that I made myself but it didn't work, heres what happened when I ran the project:
[IMG]https://imageshack.us/scaled/landing/19/operapq.png[/IMG]
 Heres the Web.config file I got from my VS MVC3 project:
[http://pastebin.com/JW3rfemx](http://pastebin.com/JW3rfemx)

Heres the default Web.config file that mono makes when I start up a new MVC project:
[http://pastebin.com/hQFT0DLe](http://pastebin.com/hQFT0DLe)

I can see its very different from the one I got from the tutorial. The one from the tutorial has a lot of **** missing. I'm wondering if I can just add the extra things that the tutorial config file has to my default config file. For example, my default config file doesn't have this:
```
    <sectionGroup name="system.web.webPages.razor" type="System.Web.WebPages.Razor.Configuration.RazorWebSectionGroup, System.Web.WebPages.Razor, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35">
      <section name="host" type="System.Web.WebPages.Razor.Configuration.HostSection, System.Web.WebPages.Razor, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35" requirePermission="false" />
      <section name="pages" type="System.Web.WebPages.Razor.Configuration.RazorPagesSection, System.Web.WebPages.Razor, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35" requirePermission="false" />
    </sectionGroup>
```that code there is clearly required for the project to process razor pages.

---

### Post by CrimpJiggler on 2012-10-15
Okay, so I've been adding pieces of the tutorials Web.config file to my default Web.config file step by step and checking to see if things still work at each step and I've isolated the cause of the problem.

When I add this:
```
<add path="*" verb="*" type="System.Web.HttpNotFoundHandler"/>
```inside the <httpHandlers> tag, it stops working. In the default config file, heres whats inside that tag:
```
        <httpHandlers>
            <remove verb="*" path="*.asmx" />
            <add verb="*" path="*.asmx" validate="false" type="System.Web.Script.Services.ScriptHandlerFactory, System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35" />
            <add verb="*" path="*_AppService.axd" validate="false" type="System.Web.Script.Services.ScriptHandlerFactory, System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35" />
            <add verb="GET,HEAD" path="ScriptResource.axd" type="System.Web.Handlers.ScriptResourceHandler, System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35" validate="false" />
            <add verb="*" path="*.mvc" validate="false" type="System.Web.Mvc.MvcHttpHandler, System.Web.Mvc, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35" />
        </httpHandlers>
```

When I remove that line from the tutorials Web.config file, the problem is fixed.

---

### Post by vikvish on 2013-01-14
Hello there, I m new bie in **ubuntu.. ver. 12.**..   :)
well i have installed Ubuntu in **VMware **(virtual machine)
and  i have installed **monodevelop **too..

my requirement is how can i run a **desktop application** in **monodevelop **
after creating a **desktop application** in **visual studio 2008  (C#)**in windows Xp...?
and how can i play **.swf **files too...?
any other idea will be appreciated...



with regards
vik

---


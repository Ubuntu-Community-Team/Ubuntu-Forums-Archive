---
title: "Getting to know Spring MVC using Netbeans 7"
date: 2011-06-29
forum: Programming Talk
---

### Post by Uubnewb on 2011-06-29
I'm trying to learn Spring MVC using Netbeans 7 as my IDE and following [this tutorial]("http://sites.google.com/site/springmvcnetbeans/step-by-step/").

I have had quite a bit of trouble following the tutorial but was able to figure it out through trial-and-error and dear-old Google, but at the moment I am stuck once more and just cannot seem to find a solution.

My application is suppose to return the following:
> 
Header
Hello :: SpringApp

Greetings, it is now [current time]
Products
[sample-products 1, 2 and 3]

But the time and products are not printing.

When I run the Controller-test I get a NullPointerException (please see attachment: [ATTACH]196299[/ATTACH]).  The problem is that I have no idea how to find the point where the NullPointerException occurs.  I have never before used these test-files, and don't know how to really make use of them.

I'm attaching my "test" and "src" directories for anyone willing to look at the code: [ATTACH]196303[/ATTACH].

As always, any help will be greatly appreciated.

---

### Post by r-senior on 2011-06-29
Were you aware that the tutorial is out of date? It is showing you Spring 2.5, whereas the current production version is 3.0.5. Spring MVC changed a lot from Spring 2.5.x to Spring 3.0.x. Version 3.0.x was released December 2009.

Having said that (and possibly deflated you slightly), the null pointer exception appears to be on line 25 of InventoryControllerTest.java (the one I've put in red):

```

        InventoryController controller = new InventoryController();
        controller.setProductManager(new SimpleProductManager());
        ModelAndView modelAndView = controller.handleRequest(null, null);
        assertEquals("hello", modelAndView.getViewName());
        assertNotNull(modelAndView.getModel());
        Map modelMap = (Map) modelAndView.getModel().get("model");   
        [COLOR="Red"]String nowValue = modelMap.get("now").toString();[/COLOR]
        assertNotNull(nowValue);

```

So either modelMap is null, or the .get("now") returns null. You could confirm which is null by throwing in an assertion immediately before line 25.

I looked at your controller and I think I see what your problem is. Don't worry, I won't spoil it ;). Have a look at your controller with reference to this and see if you can see a problem:

[http://static.springsource.org/spring/docs/2.5.x/api/org/springframework/web/servlet/ModelAndView.html](http://static.springsource.org/spring/docs/2.5.x/api/org/springframework/web/servlet/ModelAndView.html)

---

### Post by Uubnewb on 2011-06-30
Hi r-senior,

I had a feeling you might reply to my post - after all, you were one of the first people to point me towards Spring MVC.  :)

I know this tutorial is very outdated, I'm actually using Spring 3.0.2 (it came with Netbeans 7).  That is part of the reason I'm having so many problems following the tutorial.  Unfortunately I could not find any other tutorials for Spring MVC using Netbeans execpt for very simplistic HelloWorld tutorials.  If you know of any, or if you know of any sample code I could go through, please let me know.

Anyway, back to the NullPointerException:  This might sound really stupid, but when you say "You could confirm which is null by throwing in an assertion" I suppose you mean "assertNotNull(someVavlue)" rather than adding some throw clause to the method declaration, right?

---

### Post by r-senior on 2011-06-30
> **Uubnewb said:**
> I had a feeling you might reply to my post - after all, you were one of the first people to point me towards Spring MVC.  :)

):P

> If you know of any, or if you know of any sample code I could go through, please let me know.
The Spring documentation, while not exactly a tutorial, is enough to get you going once you have the basics:

[http://static.springsource.org/spring/docs/3.0.x/spring-framework-reference/html/mvc.html](http://static.springsource.org/spring/docs/3.0.x/spring-framework-reference/html/mvc.html)

The basics are pretty much the same between versions, so it would be a useful exercise to convert your 2.5 version once you know what's going on.

This tutorial pretty much follows that page:

[http://viralpatel.net/blogs/2010/06/tutorial-spring-3-mvc-introduction-spring-mvc-framework.html](http://viralpatel.net/blogs/2010/06/tutorial-spring-3-mvc-introduction-spring-mvc-framework.html)

I only had a quick scan through but it looks good to me. OK, he's using Eclipse but it doesn't make that much difference. His Maven-based examples *should* work in Netbeans without modification.

> Anyway, back to the NullPointerException:  This might sound really stupid, but when you say "You could confirm which is null by throwing in an assertion" I suppose you mean "assertNotNull(someVavlue)" rather than adding some throw clause to the method declaration, right?
Yes. Sorry if I wasn't clear (bad use of the word throwing). The idea was to confirm my suspicion that modelMap is null.

So something like:

```
assertNotNull(modelMap);
```

It shouldn't be null. If it is, it's a programming error, not an exceptional runtime condition that you would want to trap with an exception handler.

---

### Post by Uubnewb on 2011-06-30
Thanks, I found my mistake.  Instead of writing 
```

return new ModelAndView("hello", "model", myModel);

```
I wrote
```

return new ModelAndView("hello", "now", now);

```

Thanks for your help and the links, I'll go through those tutorials as soon as I'm done with this one (I've put in too much effort to just let it go). 

```
The basics are pretty much the same between versions, so it would be a useful exercise to convert your 2.5 version once you know what's going on.
```
I was actually allready planning on doing that, which is partly why I didn't give up on it earlier.  But I wonder if I could impose on you some more:  When I get around to making a new tutorial, would you be willing to go through it for me to see that I got the facts straight?

---

### Post by r-senior on 2011-06-30
> **Uubnewb said:**
> Thanks, I found my mistake.
Well done. I only spotted it because I had to look at the API docs to remember how it used to work. ;)

> When I get around to making a new tutorial, would you be willing to go through it for me to see that I got the facts straight?
Yes, of course. Great idea to make a 3.0 tutorial.

---

### Post by Uubnewb on 2011-07-01
I've finally given up on the outdated tutorial - there is just too many problems, and I'm starting to run low on time.

So I've started with this tutorial: [http://viralpatel.net/blogs/2010/06/spring-3-mvc-create-hello-world-application-spring-3-mvc.html](http://viralpatel.net/blogs/2010/06/spring-3-mvc-create-hello-world-application-spring-3-mvc.html).  Unfortunately I'm having another problem:  When I add "<context:component-scan base-package="controller"/>" to dispatcher-servlet.xml I get the following Exception: "The matching wildcard is strict, but no declaration can be found for element 'context:component-scan'."  

I'm guessing it is because of the difference in the folder-structures between NetBeans and Eclipse.  Do you know what the base-package value should be in NetBeans?  My controller's name is "HelloWorldController" and is defined in the "controller" package.

---

### Post by r-senior on 2011-07-01
I don't think it's Netbeans vs Eclipse. It's specifiying a Java package, not a file path. Did you add the relevant part to the XML schema declaration in your config file? For example:

```

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	   [COLOR="Red"]xmlns:context="http://www.springframework.org/schema/context"[/COLOR]
	   xmlns:aop="http://www.springframework.org/schema/aop"
	   [COLOR="Blue"]xmlns:mvc="http://www.springframework.org/schema/mvc"[/COLOR]
	   xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
	   [COLOR="Red"]http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context-3.0.xsd[/COLOR]
	   http://www.springframework.org/schema/aop http://www.springframework.org/schema/aop/spring-aop-3.0.xsd
	   [COLOR="Blue"]http://www.springframework.org/schema/mvc http://www.springframework.org/schema/mvc/spring-mvc-3.0.xsd[/COLOR]">

<[COLOR="Blue"]mvc[/COLOR]:annotation-driven />
<[COLOR="Red"]context[/COLOR]:component-scan base-package="demo.web.controllers"/>

...

```
In my case the controllers start with "package demo.web.controllers;"

Generally speaking, when you use an XML tag with a prefix like mvc or context, you need to add a line to the schema declaration. It was done to make Spring more modular.

EDIT: Do you know why your config file is called dispatcher-servlet.xml? It's important to know the chain of events that configure these frameworks. Hint: look in web.xml.

---

### Post by Uubnewb on 2011-07-01
I didn't add anything to the XML schema declarations, but Netbeans automatically added the following:
```

<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:p="http://www.springframework.org/schema/p"
       xmlns:aop="http://www.springframework.org/schema/aop"
       xmlns:tx="http://www.springframework.org/schema/tx"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
       http://www.springframework.org/schema/aop http://www.springframework.org/schema/aop/spring-aop-3.0.xsd
       http://www.springframework.org/schema/tx http://www.springframework.org/schema/tx/spring-tx-3.0.xsd" 
       xmlns:context="http://www.springframework.org/schema/context">

```

When I added the lines in blue and red, I got the same message for the "mvc:annotation-driven" tag:
```

The matching wildcard is strict, but no declaration can be found for element 'mvc:annotation-driven'.

```

> 
EDIT: Do you know why your config file is called dispatcher-servlet.xml? It's important to know the chain of events that configure these frameworks. Hint: look in web.xml. 


Netbean's standard name for the dispatcher is "dispatcher-servlet."  I didn't think it was neccesarry to rename it.  Does it make much of a difference to Spring what the name of the dispatcher is?

---

### Post by r-senior on 2011-07-01
No the name of the servlet doesn't matter. It's just useful to know that the name doesn't matter and is what is defined in web.xml. Anyway, that was an aside.

I did a search and, although you do need the right schema definition, I've sent you down the wrong path:

[http://alberto-flores.blogspot.com/2010/01/xml-validation-within-eclipse.html#more](http://alberto-flores.blogspot.com/2010/01/xml-validation-within-eclipse.html#more)

[http://www.jroller.com/habuma/entry/fixing_spring_modules_xsd_errors](http://www.jroller.com/habuma/entry/fixing_spring_modules_xsd_errors)

What I'm struggling to understand is that I haven't had to add any xsd catalogs to my Netbeans to build Spring projects.

EDIT: I think it's because they are defined in spring-context-*.jar.

Are you building this with Maven?

EDIT: If you aren't, you might not be pulling in the dependencies that allow these XML files to validate.

---

### Post by Uubnewb on 2011-07-01
To be honest, I have no idea if I'm using Maven or not (not quite sure what it is).

When I created the NetBeans project I just kept the default settings: Apache Tomcat 7.0.11, JavaEE version 6 Web with Contexts and Dependency Injection disabled.

I don't know if this is worth mentioning, but I'm using NetBeans 7 on Wimdows 7 at the moment (still need to fix my LAMP installation).

> 
What I'm struggling to understand is that I haven't had to add any xsd catalogs to my Netbeans to build Spring projects.

EDIT: I think it's because they are defined in spring-context-*.jar.

I'm afraid I don't know what you mean by that - I'm still VERY wet behind the ears with this.

Once again, thank you for helping, I really appreciate it.

---

### Post by r-senior on 2011-07-01
> **Uubnewb said:**
> To be honest, I have no idea if I'm using Maven or not (not quite sure what it is).
You probably aren't then. Maven is a build system that manages dependencies between JAR files. It makes your life 100 easier with these projects.

> I don't know if this is worth mentioning, but I'm using NetBeans 7 on Wimdows 7 at the moment (still need to fix my LAMP installation)
It doesn't matter. I regularly move Maven projects between Ubuntu and Windows and there's no problem.

PM sent ...

---

### Post by Uubnewb on 2011-07-04
I've done some more reading over the weekend, and I think I understand the Spring framework a little better now.  My conclusion is based on my VERY limited understanding of the Spring framework, so please correct me wherever I'm wrong:

It seems to me that Spring offers two approaches; the conventional and the configuration approaches.  When I first did the Netbeans tutorial for Spring MVC (the standard tutorial provided on the Netbeans website) I used the configuration method, although I did not realize it then.  The tutorials I tried out on Friday, however, is based on the conventional approach.

Although I now realize that the approach I choose should make no difference to the program, it did cause some confusion:  I was under the impression that the configuration approach (the way I first tried Spring out) was an old way of coding and that it should be avoided, and the tutorial's use of a deprecated class (SimpleFormController) only strengthened this idea.

With that in mind I had another look at the tutorial I followed on Friday and having a better idea of what to search for, I came up with the following conclusion:  It seems like Netbeans favours the configuration approach and as such include schemas that leans toward this approach.  This does not mean that I cannot use the conventional approach; it just means that I will have to include the right schemas manually.

For now I've decided to follow the configuration approach (simply because it seems slightly easier at the moment) until I have a more in-depth understanding of the framework - then I will try out the conventional approach and finally decide which one I prefer.

---

### Post by Uubnewb on 2011-07-08
These last couple of days I could not spend as much time on Spring as I would like, but I did get around to test Maven out (thanks again for the tip r-senior). 

I have just one problem:  When I want to create an entity class in Netbeans I cannot get past the last step (Provider and Database).  The only option in the Database Connection dropdown box is "New Database Connection."  When I click this, I can choose my driver from a list of pre-installed database drivers.  Unfortunately, regardless of my selection, the connection test always seems to fail.  I know this is not a code or Spring problem, but I would still appreciate it if anyone could help me out with this.  

It must be something extremely elementary I'm missing since this is merely a GUI setup I must click through, but somehow I'm messing up. :confused:

---

### Post by Uubnewb on 2011-07-11
Hmmmm... Bump.

Anyone that can help me with this?  But I guess I should probably make a new topic for this since the current question is quite far removed from the original one.

---


---
title: "Soon to be an ubuntu coffee guy how many beans will it be? :)"
date: 2020-03-08
forum: New to Ubuntu
---

### Post by xcfstarflight1 on 2020-03-08
**Hello good people.**

Got a couple of questions. 
1. How do I check if I have java installed? 
     I am programming JavaScript some, HTML and CSS for homepages. Perhaps i should have the Java developer kit. 
2. My system is kinda boring. I like GNOME and what is wayland when i log in?
    Starting to feel comfertable with the desktop, but if I want to get like some new looks, I don't even know how to change the desktop wallpaper or even lay elements on the desktop..
3. I just love my system now, but i need the C, C++ and Csharp compilers it seems. used to be gpp or cpp, can someone name them for me? Just curious. 
4. Also, i wonder what /dev mount is used for USB.

All feedback is appreciated greatly. When I get used to the system again, I will absolutely use this forum to be helping out others as well! I hope I get to the level where I can add like
tags etc. in the forum. But like I said I am pretty new even thou i have set up many linux systems before. 

Greetings from me to all of you!:popcorn:

---

### Post by TheFu on 2020-03-08
1) Java and Javascript are not related.  Nothing to do with each other any more than C and Javascript are related.  You probably do not want the JDK installed. It can be quite bloated and isn't needed just to run Java programs.  There are 2 popular JREs - openjava and whatever Oracle sells. I avoid anything even near "Oracle" stuff.

2) There are many other DEs. Don't feel that Gnome3 is the best when you haven't looked at 20 others.

3) gcc is the normal C, C++ compiler.  I wouldn't now anything about C#.  I know how to manage memory. If you aren't trained already, best to get a book that starts from the beginning and specifically follow those development tool install instructions.  If you aren't a programmer in each of those languages, you don't need the compilers unless you've gotten some code from a project that doesn't make installation packages using 1 of the 5 other packaging solutions.

4) Device names are tied to the type of device and the operating mode of that device.  USB is just a bus, not a device type.

---

### Post by Frogs Hair on 2020-03-08
See the Ubuntu Flavors link in my signature.

---

### Post by webaake on 2020-03-08
Check out [www.gnome-look.org](www.gnome-look.org) for some bling and conky for desktop fiddling. Want more fun? Check out some docks like Cairo and Avant here: [https://mashtips.com/linux-docks-ubuntu/](https://mashtips.com/linux-docks-ubuntu/)

---

### Post by oldrocker99 on 2020-03-08
USB devices are found at /media/username/. Easiest way to find them.

---

### Post by TheFu on 2020-03-08
> **oldrocker99 said:**
> USB devices are found at /media/username/. Easiest way to find them.

My usb printer and usb scanner never show up there.  Should they?

---

### Post by CelticWarrior on 2020-03-08
> **TheFu said:**
> My usb printer and usb scanner never show up there.  Should they?

No, they shouldn't.
Only USB mass storage devices show up at /media/username/.

---

### Post by xcfstarflight1 on 2020-03-12
> **CelticWarrior said:**
> No, they shouldn't.
Only USB mass storage devices show up at /media/username/.

Thanks guys! Really liked the links with the Ubuntu flavours and I see the /media devices! 
Thank you so much!

---

### Post by xcfstarflight1 on 2020-03-12
So, found out most things just not the part with java.
I am not sure if java is installed at all. 
How can I check if it is and what package should I be downloading when doing some JS, CSS and HTML programming?

---

### Post by TheFu on 2020-03-12
> **xcfstarflight1 said:**
> So, found out most things just not the part with java.
I am not sure if java is installed at all. 
How can I check if it is and what package should I be downloading when doing some JS, CSS and HTML programming?

Java and JS, CSS, HTML have nothing to do with each other.  They are completely different languages with completely different development needs.

Java is like C++. There isn't just 1 package.  What you need depends on what you need.  There are 2 major camps.  Oracle's JDK and OpenJDK.  There are parts that are not compatible w/ each other.
"JDK" - Java Development Kit"
Then you add modules and libraries based on work performed by others, assuming you don't want to write those things yourself.  My best advice is to either follow a book which guides setting these things up or take a class where the instructor provides a guide.  

JS, CSS, HTML are all static page methods from the web-server standpoint.  The kewl-kids are learning server-side Javascript using something called "node.js".  This is fairly new for programming and they are making all the same mistakes that Ruby, Python, Perl made over the decades.  Node does have excellent marketing - they've taken over the "full stack development" marketing term, while the folks who "pass the training" usually can't setup a webserver or DBMS, so those of us who are truly full stack developers are offended.  I am.

Whatever.  Node.js skills are marketable in the workplace at younger companies.
Java is considered "legacy" now and mostly used at "enterprise" employers.  It will never end because there is just too much custom code written for enterprises in Java.  Same for C++.  They are the new COBOL.

---

### Post by sdsurfer on 2020-03-13
Changing the name of the client-side language that was originally named Mocha, then LiveScript, to JavaScript has confused front end developers since the Netscape days. As described, ***Java is something else***. When I say "client-side" I mean it is meant to be executed in a web browser (although Javascript has grown into something more robust than just that, that is it's basic usage.)

To answer the Java question open a terminal and enter
```
 java -version
```

If you get something like not found,  Java is not installed, ***but this is irrelevant to the question***

> what package should I be downloading when doing some JS, CSS and HTML programming?

The short story, nothing, outside of a good IDE (Integrated Development Environment, basically a super powered text editor.) HTML, css, and JavaScript can be created and edited in a simple text editor, but you will be faster using a good IDE. IMO the best is something like PhpStorm from IntelliJ, but it is a paid program and there are others out there - Eclipse, Sublime, Arduino, Atom, Komodo . . . many of them are better than others depending on what languages you work in. A Google search for IDE will get you started.

The longer story is ***how*** you develop. In Ubuntu/linux, one approach is to install what is called a **LAMP** stack - **L**inux (which you already have,) **A**pache, a server software, Apache/Apache 2, **M**ysql, and **P**HP. For straight HTML, you won't need the **M** or the **P** at first. Google for how to install Apache in Ubuntu, it is really easy. This is called a development environment, a way to develop without putting your stuff out there on a live server.

Once Apache is installed, as a web server it will "listen" for web requests. You can access your development files on your local computer by going to [http://localhost](http://localhost). You would develop your projects, if they are in the default location, at /var/www/html. By developing and testing your files locally, you avoid feux pas on a live server while you are working. When it works locally, you can then deploy to your live server.

There's more to it you will learn as you get started, but that is where you can begin.

---

### Post by TheFu on 2020-03-13
You don't need any IDE.  Linux + X/Windows **is** an IDE already.  
[https://sanctum.geek.nz/arabesque/unix-as-ide-introduction/](https://sanctum.geek.nz/arabesque/unix-as-ide-introduction/)

When I'm developing software, I'll have some terminal windows open.
* build 
* debugging
* editor
* tools
* documentation
* assorted others to show library or other code written by my and other teams.

When 1st starting to program, there is a tendency to use an IDE because it seems easier and more productive.  It is only easier if it was preconfigured perfectly ,otherwise, they become extremely frustrating because there are hundreds of options buries in both the tool and the project settings.

OTOH, as someone new, the understanding required to code just a little is usually beyond the current skills.  BTW, I don't consider CSS or HTML to be coding, they are layout/presentation layer stuff, not code.  *Code* requires the use of a language with loops, variables, math and character handling.  HTML+CSS it more like any Markdown layout tool and python.

In the ideal world, someone wanting to learn static website development would have a teacher to explain those 20 critical details, like why a web server has to push \n\n before every html page served and where files should (or can be placed) and file permissions. None of it is hard, just some details.  Plus, there are always things we don't know.  Happens to everyone.

---


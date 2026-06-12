---
title: "Switching from windows"
date: 2013-08-08
forum: Programming Talk
---

### Post by david40 on 2013-08-08
Currently, I'm a windows programmer and do it all for free(just a hobby ;]). I know vb.net, c#, xna, html, and I'm learning c++. I loved vb.net, with it's basic syntax, ease of use, and support with MSDN's documentation. I was doing quite a bit with xna and vb.net, I actually created a 2d tile based map engine with 0 slow down(with the exception of the initial load). But Microsoft screwed me when they decided to stop supporting XNA and I decided that's that. I've decided to switch to Unix. Before I do so, I want to know which is best for me. I want to continue programming, but more specifically I want to keep game programming. What do y'all suggest?

Edit - Also, what kind of programming languages are out there for unix? From what I've read, it was written in C, but to be honest I hate languages that you have end a line statement with a semi-colon.

---

### Post by King Dude on 2013-08-08
Welcome to the Linux (not Unix) community.

If you'd like to program applications for Linux, I suggest C++, Java, or Python for a primary programming language. If you learn C++, you may also learn Python or Lua as a secondary language to extend your C++ code. If you'd like to enhance the Linux kernel itself, you'd have to learn Assembly and C. If you'd like to program runtimes, I suggest learning Python and Perl. If you'd like to help with open source graphics driver support, I suggest C and/or C++.

---

### Post by lisati on 2013-08-08
*Thread moved to **Programming Talk**.*

---

### Post by kalaharix on 2013-08-09
Hi

If you want to use your vb experience try Gambas 3  (free) and PureBasic (commercial but very reasonable). PureBasic is favoured by gamers for its speed but is a very different kind of Basic. Xojo in the repository is a re-incarnation of RealBasic which then turned into Real Studio. Free to try but expensive to distribute and I suspect more than a little wip.

---

### Post by l3dx on 2013-08-09
You can program in just about any language on Linux. That the kernel is written in C doesn't mean anything to what YOU can program in. The biggest difference from Windows programming are the API's and the tools. If you're familiar with .NET programming, you should check out the mono framework. I have no idea on the state of VB support though.

---

### Post by King Dude on 2013-08-10
> **l3dx said:**
> You can program in just about any language on Linux. That the kernel is written in C doesn't mean anything to what YOU can program in. The biggest difference from Windows programming are the API's and the tools. If you're familiar with .NET programming, you should check out the mono framework. I have no idea on the state of VB support though.
Visual Basic is supported, but since it's a Microsoft product it will have a few kinks getting it to work with Linux, which is why I do not recommend that people use VB on Linux. I suggest either going straight BASIC or just continue learning C++. The most important thing is that you master at least one language, and C++ is used a lot in Linux.

---

### Post by nathan-b on 2013-08-11
Since the OP doesn't like semicolons I would highly suggest python. I don't program games but I've heard good things about the Pygame library and it should not be difficult to keep making 2d games with Python + Pygame.

---

### Post by DarkAmbient on 2013-08-12
Not unix-specific, but I'm convinced that Javascript will dominate in the future, as web-based applications is just to good to be true. ;) No need to end lines using a semicolon (except for when ending a anonymous function or something like that, then the browser req. a semicolon to not get an error)

The upside and dowside with JS is that it's not a strongly-typed language, I started out with c++. So JS was weird at first, but once you get used to it it's actually quite nice, except that it can be hard to debug sometimes.

---

### Post by lads on 2013-08-13
Hi David, I have two pieces of advice for you:

. Install Eclipse - it has extensions for pretty much every language there is. It might take some time to get used to, but the rewards will be worthy.

. Learn Python - and forget VB ever existed. Python is a powerful minimal language, easy to learn and fast in producing results.

Welcome to Linux, I can assure you you won't go back.

---

### Post by david40 on 2013-08-13
Sorry it's taken me a while to get back with y'all, I didn't realize that you had to manually subscribe to a thread. So I've been checking my subscribed threads and didn't see any new post :P

I didn't know that Java was supported in Linux, nor did I know the difference between Unix and Linux so please forgive my ignorance. I do agree with you DarkAmbient that web-based applications are booming, and I have kind of dug into the whole world of web-based programming a little bit. But OOP software development is really where I want to be.

I guess that my biggest concern is the documentation on the material. One thing that MS has that I don't think anyone can really touch, is their MSDN library. I can just type in say "Control.Bounds" in google and hit I'm feeling luck and find the most up to date documentation on that property.

---

### Post by dwhitney67 on 2013-08-13
> **david40 said:**
> Sorry it's taken me a while to get back with y'all, I didn't realize that you had to manually subscribe to a thread. So I've been checking my subscribed threads and didn't see any new post :P

I didn't know that Java was supported in Linux, nor did I know the difference between Unix and Linux so please forgive my ignorance. I do agree with you DarkAmbient that web-based applications are booming, and I have kind of dug into the whole world of web-based programming a little bit. But OOP software development is really where I want to be.

I guess that my biggest concern is the documentation on the material. One thing that MS has that I don't think anyone can really touch, is their MSDN library. I can just type in say "Control.Bounds" in google and hit I'm feeling luck and find the most up to date documentation on that property.

OOP = Object-Oriented Programming... which is supported in Java.  Java works on any platform that has a CPU (Windows, Linux, Unix, Mac, a glorified Toaster).

IMHO, MSDN and Microsoft are overrated.  Googling for information regarding VC++ varies depending on whether you're using 2008, 2010, or 2012 versions, and furthermore, depending on which release you have (Edition, Standard, Professional) there may also be other differences.  With Linux, you have various compilers, but GCC is the most popular.  For the most part, I've managed well using the Linux man-pages and the online C++ reference guide (at [http://www.cplusplus.com/reference/stl/](http://www.cplusplus.com/reference/stl/)).

---

### Post by david40 on 2013-08-13
I truly believe MSDN has the best documentation that I've ever seen, but that's just an opinion. It seems like Java will be the replacement for me, I'll just have to learn to live with the semi-colon being the end of line command. By the way, I'd love to program on a glorified toaster :]

---

### Post by dwhitney67 on 2013-08-13
> **david40 said:**
> I truly believe MSDN has the best documentation that I've ever seen, but that's just an opinion. It seems like Java will be the replacement for me, I'll just have to learn to live with the semi-colon being the end of line command. By the way, I'd love to program on a glorified toaster :]

Everyone at my office always teases me because they know that I hate Windows.  But here's a clear example of why I think that you are incorrect with respect to MSDN being up to date.  When I Googled for "MSDN fstream", the very first result pertained to Visual Studio 6 (which is ancient).  When I went directly to the [MSDN site]("http://msdn.microsoft.com/en-us/default.aspx") itself, again the same ancient information was presented as the first result.

```

fstream
Visual Studio 6.0
7 out of 20 rated this helpful - Rate this topic

#include **<fstream.h>**.
...

```
I found it quite comical that only 7 out of 20 people rated the topic as helpful.

---

### Post by The Cog on 2013-08-13
I was very impressed with the java tutorial (though I haven't used it since Oracle bought Sun):
 [http://docs.oracle.com/javase/tutorial/](http://docs.oracle.com/javase/tutorial/)

And the java docs are always up to date because they are auto-generated from comments in the source code. 
[http://docs.oracle.com/javase/7/docs/api/](http://docs.oracle.com/javase/7/docs/api/)

I've not looked at MS programming docs at all, but I find it hard to imagine they're better than Sun's docs.

---

### Post by david40 on 2013-08-13
I found [this]("http://msdn.microsoft.com/en-us/library/k8w40w6t.aspx"), second result on google where the search was "fstream msdn"

---

### Post by david40 on 2013-08-13
I'm actually pretty excited to start programming with Java because I can go to homeandlearn's website. That's where I picked up my basics with visual basic, so I'm sure it'll be just as good with Java.

---

### Post by DarkAmbient on 2013-08-13
Javascript is true OOP, everything in JS is an object, even functions. Think I read that the next iteration of ECMAScript will introduce classes aswell. But I see no problem with how JS is today, it's highly sugar-able.

In JS, you could mimic classes with:

```


var aClass = function(arg) {

    /*
     * this is an object attached to the object "this" refers to, in this case an instance of aClass. 
     */
    this.member1 = 'hello'

    /*
     * This is a pure private/local variable, existing only in the current scoop/context, unreachable from the outside
     */
    var localVar = arg

    /*  
     * a function, directly attached to the this-object
     */
    this.printStuff = function() {
        return this.member1 + " " + localVar
    }

    // a "setter-function", which demands parameter str to be a string
    this.setLocalVar = function(str) {
        if(typeof str != 'string') {
            throw TypeError('Need a string, got: ' + typeof str)
            return null
        }
        localVar = str
    }
}

var b = new aClass('david40')

console.log(b.printStuff()) // prints "hello david40"

b.localVar = 'jump' // Won't change the local localVar.. just attach a new object called localVar with the value "jump" to b

b.member1 = 'and' // update b.member1 directly, works

b.setLocalVar('everyone else') // update the local variable localVar with our setter-function 

console.log(b.printStuff()) // prints "and everyone else"


```

---


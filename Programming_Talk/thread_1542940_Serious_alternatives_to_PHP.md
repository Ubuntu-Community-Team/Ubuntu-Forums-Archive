---
title: "Serious alternatives to PHP"
date: 2010-07-31
forum: Programming Talk
---

### Post by bg11 on 2010-07-31
We all see plenty of hate for various programming languages.  But one language in particular is php.  There don't seem to be any fans of it, the vast majority of users agree that it is a horrible language.

But what are the serious linux compatible alternatives?

PHP is used to add functionality to webpages in a consistent manner, which is browser and platform independent.  Javascript is one answer, but programmers seem to hate that even more than php.

There are mentions here and there about using python, ruby, perl instead, but you can't just embed python or perl into webpages?  You can obviously run some python or perl stuff on the server.  But how would you create a user login feature using python or perl, for example?  Or, even something as simple and as easy as

```

<html><body>
<?php
$d = date("D");
if ($d == "Fri")
 {
  echo "It's Friday!";
  echo "See you on Monday.";
 }
elseif ($d == "Mon")
 echo "Welcome back.";
?>
</body></html>

```

One example of a comparison is [here to perl]("http://www.tnx.nl/php.html"), but how would you embed perl commands inside the webpage?

---

### Post by worseisworser on 2010-07-31
If your goal is to embed <some other language besides PHP> into HTML/CSS/JavaScript I'm pretty sure all the languages you've mentioned (and more) can do this.

E.g., I switched from PHP to Common Lisp years ago, but I can still mix Lisp and HTML when I want to:

```

SW> (defun test ()
      (who
        (:div :id "some-test-id" :style "background-color: blue"
         (:h1 "Hello World!")
         (:p "2 + 2 = " (str (+ 2 2)))
         (:p "Here's a random number: " (str (random 42))))))
TEST

SW> (test)
"<div id='some-test-id' style='background-color: blue'><h1>Hello World!</h1><p>2 + 2 = 4</p><p>Here's a random number: 11</p></div>"

SW> (test)
"<div id='some-test-id' style='background-color: blue'><h1>Hello World!</h1><p>2 + 2 = 4</p><p>Here's a random number: 18</p></div>"


SW> (defun test (x y)
      (who
        (:div :id "some-test-id" :style "background-color: blue"
         (:h1 "Hello World!")
         (:p (fmt "~D + ~D = ~D" x y (+ x y)))
         (:p "Here's a random number: " (str (random 42))))))
TEST

SW> (test 4 2)
"<div id='some-test-id' style='background-color: blue'><h1>Hello World!</h1><p>4 + 2 = 6</p><p>Here's a random number: 31</p></div>"

SW> (test 2 40)
"<div id='some-test-id' style='background-color: blue'><h1>Hello World!</h1><p>2 + 40 = 42</p><p>Here's a random number: 2</p></div>"

SW> 

```


..or I can of course use templating if I work with other people who prefer writing HTML the traditional way, i.e., *<p>hello world</p>* instead of "my way", *(:p "hello world")*. Templating is common in other languages and environments too!

---

### Post by CptPicard on 2010-07-31
> **bg11 said:**
> 
PHP is used to add functionality to webpages in a consistent manner, which is browser and platform independent.

PHP is server-side. It generates HTML for the browser to render.

> 
  Javascript is one answer, but programmers seem to hate that even more than php.

Well, Javascript is client-side. It actually runs in the browser. There, there really are no alternatives.

Really, one of the nicest alternatives at the moment is Python and Django for the server-side framework. I suggest you take a look at it.

---

### Post by simeon87 on 2010-07-31
> **bg11 said:**
> There are mentions here and there about using python, ruby, perl instead, but you can't just embed python or perl into webpages?  You can obviously run some python or perl stuff on the server.  But how would you create a user login feature using python or perl, for example?  Or, even something as simple and as easy as

The question is whether you want to do that. One of the complaints about PHP is that you can type anything and it'll run. A good design separates the content and the display of the web page.. embedding PHP arbitrarily can make for some pretty crappy code. It's like Java: for really small projects, there's a lot of boilerplate code but for big projects, a design can be more easily enforced.

---

### Post by bg11 on 2010-07-31
> **worseisworser said:**
> If your goal is to embed <some other language besides PHP> into HTML/CSS/JavaScript I'm pretty sure all the languages you've mentioned (and more) can do this.

E.g., I switched from PHP to Common Lisp years ago, but I can still mix Lisp and HTML when I want to:

```

SW> (defun test ()
      (who
        (:div :id "some-test-id" :style "background-color: blue"
         (:h1 "Hello World!")
         (:p "2 + 2 = " (str (+ 2 2)))
         (:p "Here's a random number: " (str (random 42))))))
TEST

SW> (test)
"<div id='some-test-id' style='background-color: blue'><h1>Hello World!</h1><p>2 + 2 = 4</p><p>Here's a random number: 11</p></div>"


```



Well that's really more of an example of using lisp to shorten down the typing.  I was looking for ways of producing something more dynamic, like taking details from a form and producing relevant output, or creating a login system.

Django looks like the closest thing to an alternative yet, although the "tutorial" at [http://docs.djangoproject.com](http://docs.djangoproject.com) looks terrible.  Can anyone recommend a better django resource or book?

As I understand it, django does separate the content from the display.

---

### Post by worseisworser on 2010-07-31
> **simeon87 said:**
> The question is whether you want to do that. One of the complaints about PHP is that you can type anything and it'll run. A good design separates the content and the display of the web page.. embedding PHP arbitrarily can make for some pretty crappy code. It's like Java: for really small projects, there's a lot of boilerplate code but for big projects, a design can be more easily enforced.

Yeah, I totally agree. I like doing the [MVC]("http://en.wikipedia.org/wiki/Model%E2%80%93View%E2%80%93Controller") thing, but after things already are separated and done, mixing in simple wrapper HTML at the very outer layer which in-itself or on its own might not always warrant an entire widget ("View instance") for what it does is nice and very convenient sometimes.

E.g., both Gtk+ and Qt does this, but instead of using (X)HTML they use XML.

[http://doc.trolltech.com/4.5/designer-ui-file-format.html](http://doc.trolltech.com/4.5/designer-ui-file-format.html)

[http://glade.gnome.org/](http://glade.gnome.org/) and [http://library.gnome.org/devel/gtk/stable/GtkBuilder.html](http://library.gnome.org/devel/gtk/stable/GtkBuilder.html)

***TLDR; I like combining several ways of doing things; each method depending on context!***

---

### Post by worseisworser on 2010-07-31
> **bg11 said:**
> Well that's really more of an example of using lisp to shorten down the typing.  I was looking for ways of producing something more dynamic, like taking details from a form and producing relevant output, or creating a login system.


Ah, but it being shorter does not mean that what you ask of is impossible. E.g., [http://sw.nostdal.org/mvc-validation](http://sw.nostdal.org/mvc-validation) or [http://sw.nostdal.org/text-input](http://sw.nostdal.org/text-input) shows simple form input and does separate the View and the Model; it uses MVC.

I'm not advocating Lisp or my own toys here; I actually would *not* recommend anyone using this because it is in a perpetual alpha stage. Instead, the point is to show that what you ask of and more is *very much possible* in other languages besides PHP, and yes, even in "obscure" non-mainstream languages like Lisp. :)

Now; rejoice, go forth and explore what is out there; there is true beauty to be found for the ones looking!

---

### Post by howlingmadhowie on 2010-07-31
> **bg11 said:**
> We all see plenty of hate for various programming languages.  But one language in particular is php.  There don't seem to be any fans of it, the vast majority of users agree that it is a horrible language.

But what are the serious linux compatible alternatives?

PHP is used to add functionality to webpages in a consistent manner, which is browser and platform independent.  Javascript is one answer, but programmers seem to hate that even more than php.

There are mentions here and there about using python, ruby, perl instead, but you can't just embed python or perl into webpages?  You can obviously run some python or perl stuff on the server.  But how would you create a user login feature using python or perl, for example?  Or, even something as simple and as easy as

```

<html><body>
<?php
$d = date("D");
if ($d == "Fri")
 {
  echo "It's Friday!";
  echo "See you on Monday.";
 }
elseif ($d == "Mon")
 echo "Welcome back.";
?>
</body></html>

```

One example of a comparison is [here to perl]("http://www.tnx.nl/php.html"), but how would you embed perl commands inside the webpage?

for ruby it's called eruby: [http://en.wikipedia.org/wiki/ERuby](http://en.wikipedia.org/wiki/ERuby) 
you have to install the eruby package.
for python it's called python server pages or just psp, you just have to install mod_python for apache.

mod_perl appears to provide <perl> tags for embedding perl code in html documents, but i'm not sure and i've never used it.

---

### Post by DanielWaterworth on 2010-07-31
One of the reasons no one likes php is because the code is in the pages. This is a terrible practise. 

At the moment my web-development technique of choice is to roll my own framework in python using various packages for big components (mainly SQLAlchemy and jinja2), but I'd recommend learning Django.

Once you get your head round the way Django works, you'll wonder how you ever managed before. The best resource for learning is [http://djangobook.com/en/2.0/](http://djangobook.com/en/2.0/)

---

### Post by WitchCraft on 2010-07-31
There are 8 other ways:
Python/Django (if you want to get hired by Gooooogle)
ASP.NET MVC/mono-xsp (if you want to work with .NET on Linux)
Java Server Pages (JSP), see apache tomcat (if you like java)
Perl
Macromedia/Adobe Cold Fusion
Ruby on Rails
LISP via CGI
C/C++ via CGI


To summarize:
The most commonly used is PHP.
The common industry standards are JSP or ASP.NET (ASP.NET MVC if they know what they do).

JSPs are nice, particularly on Linux, but when I tried it on Windows Vista x64, the configuration was a nightmare (i got it working, though). You need to be capable to code in the Java syntax, which is C-like, so I don't recommend it to programming-newbies (unless you like a challenge)

ASP.NET MVC is the Microsoft way. You can develop with it on Linux too. The key is the mono-project. You need xsp2 as the server and monodevelop, if you want to develop on Linux (I recommend visual studio on windows for development, though monodevelop has gotten much better). If you install monodevelop, it will install all the necessary dependencies for mono/C#, but not for visual basic.net. It's however supported, too, you just need to apt-get the vb cil. 

The good thing about ASP.NET is, it's a framework, and you actually code in C# or VB.NET. And with C#/VB.NET you can also develop desktop GUI & console applications, as well as services/daemons. You can basically port code for components between windows forms (.NET GUI programs, they work on Linux, too [the rendering quality of the Linux port is still quite bad]) and the web, such as a treeview.

I'd say asp.net is much better for a beginner, and VB.NET/C# is definitely better than Java. It must be said, that VB.NET on Linux yet only runs up to version .NET 2.0, while C# has support up to most of .NET 4.0.
(ASP.NET MVC requires .NET 3.5)

Perl and LISP are gay, because the programs are very unmaintainable. But they can also be good, because very few people actually understand them, so they won't be able to reverse-engineer or even steal the code. The definite advantage of Perl is, that it has many many scripts that you can download, which enables you to write many complex programs very fast (much faster than with Java/asp.net).

C/C++, has the touch of professionalism, but if used for everything, it really isn't. It is very good when you need something that is very speed-critical. If it isn't speed/performance critical, don't use it. It's as simple as that.

Can't really say anything on Ruby, and quite frankly, I'm not sure if anybody actually uses it commercially.

Cold Fusion is very good for multimedia and PDF insentive websites. Cold Fusion has native Linux support, but ONE server license costs 20'000 $.  On the other hand, with CF, you can develop faster than with anything else...

Python is IMHO quite good, and I don't understand why so few people use it. Maybe because it's too complicated to install - I don't know. Google certainly uses it, and they have it as a requirement in many of their job offerings.


I'd say you're a case for ASP.NET/mono. 
That is, because you find PHP too complicated, and you probably don't like the embedding of it in HTML, too.
And because ASP.NET webforms try to hide JavaScript as much as possible, which is good for its haters, but bad for everyone else.

If you use asp.net and not asp.net MVC, and want to do dynamic and creative things, it's not really a good idea (the ASP.NET web forms model is very bad if you want to put custom JavaScript on your page, because postbacks reset the user-generated javascript variables, and viewstates are sooo large, that it makes the page which needs to be transmitted over http very large, so it gets pretty slow in the end user perspective (slower than PHP, even though C# is definitely executes much faster than PHP)... 

ASP.NET MVC is about AJAX, which is a complete different story from ASP.NET webforms. It even integrates JQuery (very useful very simple to use cross-browser JavaScript framework) by default. You can still use webforms on MVC, but IMHO you really shouldn't. Also ASP.NET is very good for web services (very good in serializing JSON/XML). And also, asp.net separates HTML and VB/C# code.

The only problem for you will be that ASP.NET is not very popular on Linux. So if you want to sell something - bad luck. Additionally, ASP.NET development takes quite a bit longer than PHP.

In my opinon, the real point of using ASP.NET / .NET is the separation of the code from the markup, and the compilability of C#/.NET. It means you can compile your website/webapp and go closed-source when you sell.

The other big plus point is the (partial) portability of code between web/winforms/etc., which is a very nice feature. Also, IMHO, it works better than Java. It's still a bit beta quality on Linux, though. And on Ubuntu, you need to compile mono 2.6 yourselfs, because in the repository, there is only mono 2.4, which is a bit old and has many bugs that were corrected in 2.6 (such as XML and concerning MVC). Unfortunately, the compilation process is not very well documented, although it's pretty simple. 

Follow this link for how to compile mono 2.6 (replace 2.4 with 2.6)
[http://www.centriment.com/2009/04/01/building-mono-24-from-source-on-ubuntu-810/](http://www.centriment.com/2009/04/01/building-mono-24-from-source-on-ubuntu-810/)

---

### Post by worseisworser on 2010-07-31
> **WitchCraft said:**
> 
LISP via CGI

There is certainly no hard link between Lisp and CGI! :) The same holds for C/C++ of course.

edit: It holds for pretty much any language/environment out there, as most can do FFI which means they can access the native socket API of the environment/OS and thus pretty much do as they please.

---

### Post by Hellkeepa on 2010-07-31
HELLo!

If the only reason for not going with PHP is because "the vast majority of users agree that it is a horrible language", then you should reconsider a bit.

Now, I'm not saying that PHP is the perfect language, nor that it doesn't have its share of weaknesses; Just like any other language out there. PHP has some strengths too, some of which can be abused (and quite often are by people who don't really know what they're doing). These strengths also make PHP one of the most flexible languages you can use, and could be utilized to help you build a web app really fast.
One other advantage of PHP is precisely that it is so widely used (and abused), in that it has a whole boatload of information and documentation. The PHP.net manual is one of the best places to look up information.

Just be very mindful of what you're doing, and secure down your application (don't trust the user), and you should be perfectly fine.

Happy codin'!

---

### Post by howlingmadhowie on 2010-08-01
thinking about php some more, it does have a few interesting reflection shortcuts, which make programming with it a bit easier.

you can do something like this, for example:

```

class MyClass {

// class definition

}

$myClassname="MyClass";
$myInstance = new $MyClassname();

```

which is nice.

You can also access functions over strings as well:

```

function myFunc() { // do stuff }

$myFunctionname="myFunc";
$myFunctionname();

```
which takes some of the pain out of php not being functional.

---

### Post by soltanis on 2010-08-01
> **WitchCraft said:**
> Perl and LISP are gay, because the programs are very unmaintainable. But they can also be good, because very few people actually understand them, so they won't be able to reverse-engineer or even steal the code. The definite advantage of Perl is, that it has many many scripts that you can download, which enables you to write many complex programs very fast (much faster than with Java/asp.net).

Have you ever used Perl or Lisp? With rigid discipline, perl programs can be perfectly maintainable, and many people understand the language. While it's likely that fewer coders out there understand a Lisp dialect, these programs are hardly unmaintainable; in my view, these are actually the simplest programs to understand.

To refer back to the original post, PHP is a frequently-bashed language because of inconsistent naming, the cramming of hundreds of functions into the global namespace (Perl is also guilty of this, but not quite to the same extent), annoying sigils (Perl's are worse, they got a little better in Perl 6) and object-orientation as apparently an afterthought. See, I just bashed it, but this doesn't make it a bad language. Sometimes, it suits your needs perfectly. I find no other language better when I am forced to work with an SQL database, because the integration is very good. As for alternatives, any language is an alternative. Turns out, you can write CGI scripts in any language that can read environment variables and parse strings. Including sh/awk.

---

### Post by phrostbyte on 2010-08-01
I've heard PHP described before by it's author as "a language for people who don't like to program, but who want to solve problems as quickly as possible". This is sacrilege amongst professional software developers these days, where the consensus is maintainability is more important then speed of development. I don't think this is a universal hate for the language, and it is among the most popular languages out there (if not the most popular). Your using a PHP application right now. :)

---

### Post by WitchCraft on 2010-08-07
> **phrostbyte said:**
> 
the consensus is maintainability is more important then speed of development.


IMHO, actually the opposite is true.
Speed of development (+choice of platform [=volume]) is EVERYTHING !
Nobody gives a damn about maintainablity/quality.

But it's also my opinion that, as Mark Twain once said, whenever you've the same opinion as the majority, it's time to reconsider.

That's why I am an avid fan of maintainability.
I'm a long-term person, not a short-term person.
Because on the long run, being able to extend functionality easily and fast without introducing a lot of bugs in the process, as well as solid unit tests and keeping one solid and well designed and thought-over version of a project/product is far more important than getting out the latest version of your product of questionable quality in n varieties, all of them having some functions but lacking other things another version has, but the project versions are so divergent that you can't reunite them without significant effort [=expenditure].

---


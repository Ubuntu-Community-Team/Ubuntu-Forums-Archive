---
title: "Web Development Clarified"
date: 2009-06-21
forum: Programming Talk
---

### Post by sam191 on 2009-06-21
Hey all,

I have decided I want to try Web Development... But I have very little information on the subject. I've tried using Google but it just gives me really basic information. I have just a few specific questions and would be very grateful for even some links. So here we go,

-I know that client side scripting is parsed by the browser, and server side is done by the server, but what tasks do they specifically carry out? (Let's say I want to use Python instead of PHP, will the client side language stay the same?)

-Are there a limited number of languages that I can use for the client side? And if I'm correct, I can use pretty much any language for the server side? 

-Is it possible to run a server from my desktop for sites? 

-Let's say I wanted to create a SNES like game on the web. What Languages and tools am I limited to using to create games like these?

I'm very new to the web scene, and I found it a lot harder to find this information. I usually end up with a site trying to sell me tools to build sites! And I hope I posted this in the right section (it is programming, after all)

Thanks in advance

---

### Post by TheBuzzSaw on 2009-06-21
Your client side options are indeed limited. Unless you plan on having the user install some kind of fancy plugin, you're going to have to get at least somewhat comfortable using XHTML, CSS, and Javascript.

You can use any language that your server supports, but it also depends on what kind of information the server is supposed to cough up after processing your code. For "normal web sites", plan on using PHP starting out.

Yes, you can run a server from your desktop. I do that for testing. Are you planning on hooking up this desktop to the Internet for others to access? Or are you just looking to practice/test?

A SNES-style game would be best built in Flash or some similar technology.

---

### Post by Can+~ on 2009-06-21
> **sam191 said:**
> -I know that client side scripting is parsed by the browser, and server side is done by the server, but what tasks do they specifically carry out? (Let's say I want to use Python instead of PHP, will the client side language stay the same?)

You should stop seeing "code" as something different, it's just another file, the file is sent to the user and parsed by the browser.

As long as it's valid (X)HTML, any server-side language can do it; in fact, you could write a C that does a (tr)uckload of fprintf's and get a valid HTML page.

The language choice should be depending on what tools does the language provide to accomplish that task, php has the advantage (or burden) of being in-line with HTML, so you can suddenly escape to PHP with the <?php ?> tags, or python has a wide range of frameworks like CherryPy, Django, etc. 

Other thing that languages provide is a way to treat users, the most typical being the idea of "Sessions", where each user has a set of variables defined for him. For example Java handles this with a "bean" (getSessionBean()), PHP does it with a hash _SESSION['key'], etc.

There's also AJAX which is "on the middle" between the client and the server, as it doesn't need the whole page to be reloaded to pull information from the server.

> -Are there a limited number of languages that I can use for the client side? And if I'm correct, I can use pretty much any language for the server side? 

Any language that's supported by the browser, being CSS, HTML and javascript the most basic. But no one guarantees that the user has javascript switched on.

There's also plugins, like Java Applets and Adobe Flash. This are "embedded". I think flash is ubiquitous and very popular, so you can trust the user has it, specially if your page is centered around (but not limited to) video streaming.

> -Is it possible to run a server from my desktop for sites?

Sure.

> -Let's say I wanted to create a SNES like game on the web. What Languages and tools am I limited to using to create games like these?

I guess Flash.

Flash is actually just a .swf file that lands on the client, the browser parses the <embed ...>, summons the flash player, inserts it into the browser window and feed it with the .swf file.

---

### Post by sam191 on 2009-06-22
I think I understand now. So when people are talking about using python/perl etc, they are talking about the server side. Where would flash fall? 

Also, the web application itself is on the server correct? If I am getting this right, then all the client side does is layout the page? 

For example, I create a calculator that automates row operations on matrices (was thinking about actually doing this). Would I write that code with PHP/Python/Perl (actual application)? So then it would reside on the server where it is accessed by the client, HTML/CSS/Javascript (page layout) and is then seen by the user. Am I getting close? 

You guys have been a big help so far, thanks!

---

### Post by Oler1s on 2009-06-22
> So when people are talking about using python/perl etc, they are talking about the server side.Yes, precisely.

> Where would flash fall?Client.

> Also, the web application itself is on the server correct?Yes. Well, given the popularity of Javascript and significant client side interactivity, people may refer to the client side as well, when they talk about the web application. (Figure it out by context). But usually, yes, a web application refers to the software on the server.

> If I am getting this right, then all the client side does is layout the page?Technically, no. The most important thing for the client is to be able to properly interpret the base content (i.e. parse the HTML), and then create the correct layout (the CSS). But it has become quite commonplace to have significant functionality in Javascript or in plugins. The end result is that the client side can be implementing some rather significant functionality (which I hinted at above when I said that one might refer to the client side as well when talking about their web application).

> For example, I create a calculator that automates row operations on matrices (was thinking about actually doing this). Would I write that code with PHP/Python/Perl (actual application)? So then it would reside on the server where it is accessed by the client, HTML/CSS/Javascript (page layout) and is then seen by the user. Am I getting close?IT could beimplemented server side. But it can also be implemented client side with Javascript. The feasibility of doing it client side depends on some factors (how the input comes in, the size of the data, and other factors).

---

### Post by Can+~ on 2009-06-22
> **sam191 said:**
> I think I understand now. So when people are talking about using python/perl etc, they are talking about the server side. Where would flash fall? 

Client. Although flash can also retrieve data on it's own (like loading a video).

> **sam191 said:**
> Also, the web application itself is on the server correct? If I am getting this right, then all the client side does is layout the page?

Yeaaarrrmmmnn....no. Client side layouts the page, yes, but it's not the only thing it can do. Javascript provides certain "functionality", like hiding/displaying elements, or can do math or write to objects (Document.mydiv.write(...)).

The bad/good thing about javascript is that it hides all errors, so the user never knows when something is wrong (which can be good), but also means that the developer needs a tool like Firebug to do a proper tracing.

> **sam191 said:**
> For example, I create a calculator that automates row operations on matrices (was thinking about actually doing this). Would I write that code with PHP/Python/Perl (actual application)? So then it would reside on the server where it is accessed by the client, HTML/CSS/Javascript (page layout) and is then seen by the user. Am I getting close?

Hell no. Believe it or not, Javascript could do that. Requesting the server is expensive, and if something can be done on the client side and doesn't compromise security (like handling the password management to your client, heh), better there.

For example, imagine a site that has a page with information like product_name, quantity, id_client, etc (Typical things you pull from a Database).

What would be better:
1. Load the data to the client, and sort it there.
2. Sort the data on the server, send it sorted.

Now let's say said table has a 10.000 registers on it. Having the data transferred each time (case 2) for everytime someone wants to sort it would be ridiculous. Multiply that for every user on the system and watch your server burst into flames at any moment.

So option 1 is better, means that there's less load on your CPU and more on the client side. So the big idea of server <--> client transaction is to transfer the "essential data" and any information that can is derivative from the downloaded data can be done on the client side.

Then, you can see why AJAX is all the rage lately, it can pull specific data. For example, I used to play WoW, I admire wowhead's interface:

[http://www.wowhead.com/?items=2.8#0-3+1](http://www.wowhead.com/?items=2.8#0-3+1)

Look how by clicking on the title of the table it sorts everything, hovering your mouse over an item gives you a detailed list which is pulled from the server (notice the "loading") and how all the sort criteria is done on the client. It just refreshes the changing sections.

In your example, you don't even need server scripting to do anything, you could write a plain HTML + Javascript page that can do that, but still can be done on the server as a training exercise.

I suggest that you start learning from client to server:

-Learn HTML
-Learn CSS
-Learn Javascript

Finally learn your server side language. Although some frameworks hide all the HTML/CSS/JS magic, it's better to know what's going on down there.

---

### Post by sam191 on 2009-06-22
Alright, I'm getting closer now :D

I am currently learning Python and C, and I don't want that to go to waste completely (for sites that is). So I think I can use Django for the server side when I get there. But here's my question, why couldn't I use Python to write the game itself instead of flash? Would that mean installing a special plug-in for user? 

Here is what I want to do. I want to create a SNES like Street figheter like game (2d fighting game). Where we can upload characters on the go. It will have 2 player local capabilities and hopefully network play as well.

Does flash have the I/O capabilities to handle a game like this? (would users be able to use joysticks?)

I know how to do this using Python/Pygame, but I guess it's a whole different ball game online. 

I would just like to know if something like this is possible to make on the server side (without flash)? Or even possible at all, or will I have to use flash?

Thanks for all the replies! You guys have been a tremendous help. I just wanted to get the basics down, then it's off to the book store! :D

---

### Post by ad_267 on 2009-06-22
> **sam191 said:**
> Alright, I'm getting closer now :D

I am currently learning Python and C, and I don't want that to go to waste completely (for sites that is). So I think I can use Django for the server side when I get there. But here's my question, why couldn't I use Python to write the game itself instead of flash? Would that mean installing a special plug-in for user?
Because the Python script runs on the server, not the person who's viewing the website's computer.

> Here is what I want to do. I want to create a SNES like Street figheter like game (2d fighting game). Where we can upload characters on the go. It will have 2 player local capabilities and hopefully network play as well.

You would probably need flash for the actual client side game, then a server side Python application and a database to keep track of stats and characters. As for the 2 player stuff, I'm not sure how you'd go about doing that, that's getting pretty complicated.

> Does flash have the I/O capabilities to handle a game like this? (would users be able to use joysticks?)
I doubt it, probably just keyboard input.

> I know how to do this using Python/Pygame, but I guess it's a whole different ball game online.
Yes.

> I would just like to know if something like this is possible to make on the server side (without flash)? Or even possible at all, or will I have to use flash?

No, you'd have to use flash. The server can't accept input from the client computer and send back 2D graphics in real time. The client side can show an html/css/javascript website with flash content, the server can only send html/css/javascript to the client.

What you're doing sounds like it's better off not being a web app at all, but rather something with a server application and stand alone client application written in Pygame.

---

### Post by hessiess on 2009-06-22
Don't bother learning PHP, the whole language is a complete mess and lacks any sort of consistency. And unless you are very careful, the source code will quickly turn into one big unmaintainable mess.

---

### Post by TheBuzzSaw on 2009-06-22
> **hessiess said:**
> Don't bother learning PHP, the whole language is a complete mess and lacks any sort of consistency. And unless you are very careful, the source code will quickly turn into one big unmaintainable mess.
And what would you propose as an alternative? PHP is one of the best languages on the web.

---

### Post by hessiess on 2009-06-22
> **TheBuzzSaw said:**
> And what would you propose as an alternative? PHP is one of the best languages on the web.

Ruby on rails or Python. Seriously, you don't realise just how messy PHP actually is until looking into the alternatives.

---

### Post by TheBuzzSaw on 2009-06-22
> **hessiess said:**
> Ruby on rails or Python. Seriously, you don't realise just how messy PHP actually is until looking into the alternatives.
Oh, but I have looked at the alternatives. This "mess" you are referring to is when programmers refuse to use good systems of code organization. Handing a new language to a programmer will not magically make his code all pretty.

Python is horrible. Indent-based blocking? Silly.

Ruby on Rails has its place, but it is a struggling fad. Many more servers in the world support PHP.

---

### Post by Mirge on 2009-06-22
heh, I make my living using primarily PHP. The whole "PHP is junk" remarks I run across disgust me.

In most cases, don't blame the language, blame the programmer.

---

### Post by sam191 on 2009-06-22
I've also heard that about PHP... But I have also heard that about many other languages ;)

I'll tell you guys what I think about it after trying it.  

TheBuzzSaw, what's with the hate towards Python? I love it :D

---

### Post by s.fox on 2009-06-22
> **Mirge said:**
> heh, I make my living using primarily PHP. The whole "PHP is junk" remarks I run across disgust me.

In most cases, don't blame the language, blame the programmer.

I whole heartedly agree with you.  I mainly do development in PHP,  despite having a fair amount of knowledge in other alternative languages.  

-Ash R

---

### Post by CptPicard on 2009-06-22
> **TheBuzzSaw said:**
> 
Python is horrible. Indent-based blocking? Silly.


I wonder how much you've used Python... the "significant whitespace" argument is about as superficial as the "Lisp has parentheses" complaint :)

---

### Post by simeon87 on 2009-06-22
> **TheBuzzSaw said:**
> And what would you propose as an alternative? PHP is one of the best languages on the web.

One of the most used languages on the web, yes. But we all know examples of what's used the most isn't always the best.

> **TheBuzzSaw said:**
> Python is horrible. Indent-based blocking? Silly.

On one hand arguing that PHP is fine in the hands of a good programmer but at the same time complaining how hard it is to keep your code properly indented. Fail really :)

---

### Post by curvedinfinity on 2009-06-22
(Back on topic people...)

> **sam191 said:**
> Alright, I'm getting closer now :D

I am currently learning Python and C, and I don't want that to go to waste completely (for sites that is). So I think I can use Django for the server side when I get there. But here's my question, why couldn't I use Python to write the game itself instead of flash? Would that mean installing a special plug-in for user?


Starting from the beginning... When you go to a website, your browser is using Hyper-Text Transfer Protocol (HTTP) to "ask the server for something". HTTP acts a lot like the command line. You send the server a list of text arguments and it performs a process and usually sends something back to you. You give an HTTP server (an http server is just a program that listens for network connections and handles responding back) arguments in this format:

```
http://server/app.cgi?arg1=data1&arg2=data2
```

When the server gets the arguments, and the URL points to an executable file, it will use Common Gateway Interface (CGI) to pass the arguments to the program (you must enable CGI in most HTTP servers). Some languages (most scripting languages) circumvent CGI with special modifications to the HTTP server that will actually run an application environment in the daemon process (for instance, Apache has a number of mod_xxx modules, like mod_python). However, you can always use CGI with any executable.

After the application is done processing the data, it simply uses its normal text-out functions to send data back through CGI to the server and on to the client. For instance, in a C application running through CGI, you can send HTML back to a client using printf.

When the client receives the data the server sent back, the client is responsible for processing it however they choose. Usually we use a browser to process it -- a browser being basically a big package of interpreters for different kinds of data (HTML, text, images, videos, flash, javascript, etc.). In order for a user who is using a browser to view XXX, the browser has to support it. Thus, we can only send them relatively generic information that is well-supported. -- This is ultimately why if you want the client to do their own processing, you HAVE to use javascript, flash, or java applets -- because those are the only things a browser understands.

> 
Here is what I want to do. I want to create a SNES like Street figheter like game (2d fighting game). Where we can upload characters on the go. It will have 2 player local capabilities and hopefully network play as well.

Does flash have the I/O capabilities to handle a game like this? (would users be able to use joysticks?)


I'm not 100% sure about joysticks, but you would be able to make a good game with Flash.

> 
I know how to do this using Python/Pygame, but I guess it's a whole different ball game online. 

I would just like to know if something like this is possible to make on the server side (without flash)? Or even possible at all, or will I have to use flash?


Once again, you can only send a browser things it understands. It is possible to duplicate most of the things Flash can do with Javascript, however. Javascripts limitations ultimately stem from the fact that its output/display is limited to HTML. HTML is great for structuring data in easy-to-read text, but it isn't very flexible. You can do a lot of things using absolute-positioned elements, but HTML has no support for rotation, which is ultimately a requirement in a lot of games.

However, there is a hack that can get around this deficiency. Because browsers can understand images, you can make a server-side application that outputs a dynamic image. You'd basically have to query that image-spinner application for each increment of rotation you want, preload all of them on the browser, and then flip through them as the object rotates.

---

### Post by TheBuzzSaw on 2009-06-22
> **simeon87 said:**
> One of the most used languages on the web, yes. But we all know examples of what's used the most isn't always the best.
I don't think that PHP is the end-all be-all of web languages, but I believe it is one of the best options available.[/quote]

> **simeon87 said:**
> On one hand arguing that PHP is fine in the hands of a good programmer but at the same time complaining how hard it is to keep your code properly indented. Fail really :)
Hahaha touche. However, I wasn't referring to its prettiness; I was targeting its syntax. Maintaining code blocks relative to its indentation is a dangerous and painful endeavor. I wasn't implying that "Python accomplishes nothing"; I was pointing out that while PHP looks ugly to a lot of you, at least its code still runs even if most of the whitespace is wiped out by a stupid IDE. :P

---

### Post by curvedinfinity on 2009-06-22
A little follow-up:

Server-side programming has these advantages:
[list]
[*]No limitations in language, libraries, or environment
[*]Secure
[*]Data is easy to sync, since its all in one environment
[/list]

Client-side programming has these advantages:
[list]
[*]Low latency
[*]Less bandwidth usage for server
[*]Privacy
[/list]

---

### Post by Reiger on 2009-06-22
One of the main benefits of doing things on the server is that you have control over the enviroment. 

This is more than yet-another-security concern: it is also a `deployment concern'. It may hit sooner than you think: for instance most popular webbrowsers these days do support XSLT. That means you could indeed send raw database output from the server in an XML format, and have the *entire* web page itself be generated on the client side using XSLT.

Unfortunately: not all browsers are gifted with a very modern XSLT implementation. Most support XSLT 1 which is kind of old, and implies an XPath implementation that is so old many functions do not exist. That is however a relatively minor problem: you can write your own functions (or find plenty of those on the Internet) to solve that. The real problem is that *not all browsers fully support the XPath language itself*. For instance Firefox has no good support for the various types of axis in XPath.

---


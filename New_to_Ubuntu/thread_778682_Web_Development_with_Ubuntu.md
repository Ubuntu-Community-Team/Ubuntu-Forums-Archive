---
title: "Web Development with Ubuntu?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by JohnPain123 on 2008-05-02
Hi All,

Being a complete beginner and not knowing very much about Linux or web-development, I need to ask some really basic questions that I hope someone can answer in simple english :-D

I have 2 Windows laptops and I'd like to start some basic web-development.  Someone mentioned to me that I should use Linux to do it?  I went to the Ubuntu website and saw that there's a Desktop and Server edition available.  Now, I need to keep one of my laptops running on Windows (because it's not mine!) but the other one I can do whatever I want to it.

Could I use Ubuntu Desktop and use that as my web server?  Or do I have to install Server edition and Desktop edition (so that they co-exist on the same laptop)??

Apologies if this all sounds really stupid, but I really ama complete beginner! :-)

Thanks,

John.

---

### Post by edm1 on 2008-05-02
If you are hew to linux i would not recommned the server edition as it has no graphical interface so can be very daunting. Installing a web server on the Desktop can be done easily and im sure there are many Howtos about on the forums.

---

### Post by Tux Aubrey on 2008-05-02
You won't even need a web server unless you are planning to host your own site.  Most people (beginners) are really better off getting professional hosting unless you really want to learn the ins-and-outs of running servers 
[*](which is different from Web development)

I'll stick my neck out and suggest that all you really need for starting out learning web development is a good text editor and a web browser. Starting out with WYSIWG html/css editors is probably not a good thing to do.  Even a lot of pros seem to shun the Dreamweaver/MS Frontpage route in favor of hands-on coding.


I'd also say, if you are genuinely starting your learning from scratch:

[LIST]
[*]Start out looking at learning integrated HTML and CSS (ie learn them side-by-side).  Maybe leave PHP, Java, MySQL etc. till later, unless you have programming experience.  That way you will develop a feel for making your web sites simple and elegant rather than overkill problems that CSS can solve.

[*]Work with firefox (or another standards compliant browser) rather than try to learn all the work-arounds for IE6 and below (ie the very non-compliant browsers).  They are becoming less relevant anyway as MS sloooooowly comes to accept that someone other than themselves can actually set standards.

[*]There are lots of good tutorials on the web (and lots of sample code to learn from!)

[*]Move to a code-friendly text editor like Scite (its in the Ubuntu repos) once you get the hang of html/css.

[*]Give yourself a couple of weeks in which it is OK to feel totally confused and useless.  Competence will come.

[*]Enjoy your journey.
[/LIST]

---

### Post by neurostu on 2008-05-02
Its very easy to run a webserver on Ubuntu Desktop.  I would start out with a real light weight webserver to get you started. I have done a little work with BOA and it is easy to use and set up.
You can install it by opening a terminal and typing:
```

sudo apt-get install boa

```
I would read this [http://www.boa.org/documentation/](http://www.boa.org/documentation/) before you get started though.

Also you only need a webserver if you want to HOST the website from your computer. If you are going to use somebody else to host your website you don't need a webserver.  A webserver just puts a layer between internet traffic coming into your computer and your computers internals. If you are going to be looking at your webpages and don't need people from the internet looking at them you don't need a webserver.

It sounds like you might not have any experience in web development. I got started with webmonkey.com they where a great resource. I suggest you check them out: [http://www.webmonkey.com/webmonkey/authoring/html_basics/](http://www.webmonkey.com/webmonkey/authoring/html_basics/)

---

### Post by neurostu on 2008-05-02
> 
    * Start out looking at learning integrated HTML and CSS (ie learn them side-by-side). Maybe leave PHP, Java, MySQL etc. till later, unless you have programming experience. That way you will develop a feel for making your web sites simple and elegant rather than overkill problems that CSS can solve.

Those are all great skills to have, but not needed for a beginner. I would recommend figure out what you want your website to do and start with those feature sets.  Honestly things can get really confusing if you try to integrate across to many development languages too quickly.
> 
    * Work with firefox (or another standards compliant browser) rather than try to learn all the work-arounds for IE6 and below (ie the very non-compliant browsers). They are becoming less relevant anyway as MS sloooooowly comes to accept that someone other than themselves can actually set standards.
 YES Develop in firefox!

> 
    * Give yourself a couple of weeks in which it is OK to feel totally confused and useless. Competence will come.

These things can really take time, be patient and try to find people who are also trying to learn web development and you can help each other out.  Remember that most people you talk to are also still learning. Most of these things really take a couple years to master.

---

### Post by aheckler on 2008-05-02
I have to plug [Bluefish]("http://bluefish.openoffice.nl/") here (for coding HTML, CSS, etc.). I've been using it for some time now and I absolutely love it.

---

### Post by JoyceBabu on 2008-05-02
AFAIK, Ubuntu Server is for production use. If you want a development server, then Desktop is fine.

To install the LAMP server on Ubuntu 8.04, to to

*System > Administration > Synaptic Package Manager*

In Synaptic Package Manager
*Edit > Edit Packages by Tasks...*

In that you can see the option LAMP. It will install all the required packages. I have just done that :).

After installation you can see the apache2.conf file at /etc/apache2. The default document root is /var/www.

---

### Post by JohnPain123 on 2008-05-02
Wow... I can't believe I got so many responses in such a short space of time! :-)

Ok, it looks as though Ubuntu Desktop is the way to go and I'll try installing something like Apache on it.  I don't think I need any hosting yet because I'm just starting out.

I do have a little UNIX experience as I used it in my first job - but I can only do basic stuff.

So can I wipe Windows off of my laptop completely and just have Ubuntu Desktop on it?  Or would they co-exist side-by-side?  Pros/Cons?

Thanks!

---

### Post by Paqman on 2008-05-02
> **Tux Aubrey said:**
> 
[*]Start out looking at learning integrated HTML and CSS (ie learn them side-by-side)
There's a [really good book](http://www.amazon.co.uk/Integrated-HTML-CSS-Smarter-Faster/dp/0782143784/ref=sr_1_2?ie=UTF8&s=books&qid=1209734639&sr=8-2) that teaches exactly that.

One of the better html editors on Ubuntu is Kompozer. It's not quite Dreamweaver, but for static sites pretty good.

---

### Post by Paqman on 2008-05-02
> **JohnPain123 said:**
> 
So can I wipe Windows off of my laptop completely and just have Ubuntu Desktop on it?  Or would they co-exist side-by-side?  Pros/Cons?

You can do either. But setting up a dual boot gives you all the advantages of having both systems, with no real downside.

---

### Post by neurostu on 2008-05-02
You can totally dual boot windows and ubuntu. Search the forums and google for how to do it. Basicly if you want windows then dual boot, if you're ready for ubuntu only then don't. its that simple.

---

### Post by JohnPain123 on 2008-05-02
Even though I think it may make more sense for me to have both Windows and Linux, I think I'm going to scrap Windows completely :-D

Sounds much more interesting venturing into the unknown!

---

### Post by aheckler on 2008-05-02
> **JohnPain123 said:**
> Even though I think it may make more sense for me to have both Windows and Linux, I think I'm going to scrap Windows completely :-D

Sounds much more interesting venturing into the unknown!

Welcome to the fold! Be sure to bring all your data along. :) It might be a good idea to read [this]("http://ubuntuforums.org/showpost.php?p=338302&postcount=1") and [this]("http://linux.oneandoneis2.org/LNW.htm") first too.

---

### Post by DrMega on 2008-05-02
> **Tux Aubrey said:**
> You won't even need a web server unless you are planning to host your own site.

Unless of course he wants to learn PHP or any of the backend scripting/programming stuff. Even then, PHP, Apache and MySQL are all in the repositories.

---

### Post by JohnPain123 on 2008-05-02
Hi DrMega,

The programming stuff does interest me...

You say that there's all this programming stuff in the repositories.  What difference is that to Windows though?  Does it mean that I can just start programming in PHP for example, without having to install any extra stuff?  And what's the advantage over programming in Linux vs Windows?

---

### Post by neurostu on 2008-05-02
The programming is the same in windows and in linux (most web-development languages are platform independent, meaning the language doesn't change depending on the OS). The utilites and programs you run are what are different. 

Although I will say that Linux is more of a development friendly environment, as it give more power to the user.

When people talk about the repositories, they are mentioning servers run by Canonical that have programs ready to install on them. To access these servers you can use APT-GET, Aptitude, Synaptic Package Manager.  
To search for a package you can type:
```

aptitude search <program>

```

To install a  program you can type:
```

sudo apt-get install <Name Of Program>

```
and if the program is in the repostitories ubuntu will download and install the program. This is very different from windows where you have to find the program yourself, scan it for viruses (as you can't trust the source, ubuntu maintains the repositories so they are virus free) then install and configure it.  

So when I wanted to install python on my laptop I ran:
```

sudo apt-get install python

```
that was it. It was 100X easier than windows.

---

### Post by DrMega on 2008-05-02
> **JohnPain123 said:**
> Hi DrMega,

The programming stuff does interest me...

You say that there's all this programming stuff in the repositories.  What difference is that to Windows though?  Does it mean that I can just start programming in PHP for example, without having to install any extra stuff?  And what's the advantage over programming in Linux vs Windows?

If you learn PHP, I would definately recommend the Linux route. firstly, there are loads of good, free editors, but that's not the main reason for me.

MS stuff lets you get away with some pretty sloppy stuff (which might sound like an advantage but it isn't for reasons that would take a while to explain). If you work in Linux, then you can be pretty sure that your finished product will work equally well on Windows or Linux. If you do it the other way round, you can only be sure of Windows compaitibility.

Firefox enforces the W3C standards better than IE, and Apache and Linux enforces standards on server side. So if you get everything up and running on a Linux setup, then you can deploy without too much concern about the client's setup, or the hosts kit.

---

### Post by Tux Aubrey on 2008-05-02
I forgot to mention one other great tool - the Web Developer add-on for firefox.

Just go to "tools" on the Firefox menu, >Add-ons > Get Extensions

Just browse or search for "Web Developer"

It gives you a new menu bar with tools to write, dissect and analyze web pages.  

And under the Ubuntu "Applications" menu, you will find Add/Remove - lots of programming tools are available (its a simple graphical front-end for apt-get mentioned above - as is Synaptic Package Manager - under System>Administration)

---


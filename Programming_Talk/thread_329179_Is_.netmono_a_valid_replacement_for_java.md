---
title: "Is .net/mono a valid replacement for java?"
date: 2007-01-01
forum: Programming Talk
---

### Post by NoTiG on 2007-01-01
Just wondering.. i plan on making a pictionary like game through the browser.. i don't want it to be downloaded.... so i guess my options are flash, shockwave, and java, and .net? I was leaning towards ironpython.....

---

### Post by loell on 2007-01-01
if that's the case, do it with ajax, which is pretty much javascript.

---

### Post by Tomosaur on 2007-01-01
In my experience, Java is still better than C#, but C# is great for some things. I would reccommend AJAX or Flash for browser based games - Jave for applications.

You may want to take a look at iSketch to see how that was implemented, since it's pretty much browser based pictionary.

---

### Post by pmasiar on 2007-01-01
> **NoTiG said:**
> Just wondering.. i plan on making a pictionary like game through the browser.. i don't want it to be downloaded.... so i guess my options are flash, shockwave, and java, and .net? I was leaning towards ironpython.....

IronPython is great, but restricted to MS Windows platform - so I guess no much help on it here :-) Mono is promoted as "free" replacement of C# and .NET, but not many people are interested in it because unknown patent status. Flash and Shockwave are proprietary, so again you are in vendor-lock-in position. Both Java and C#/mono are static typed languages ==> slower to develop in. My first preference is always python. Fast to develop, easy to optimize later if required.

You forgot to mention your experience level and language preference. My advice would be Ajax on client side and Python on server. TurboGears is great plaftorm for this, designed for Ajax applications from very beginning. 

If you are not expert, you may start with plain CGI application. Page reload will be noticeable, but if under 1-2 sec, no problem, and *MUCH* simpler. This way you can avoid javascipt - which is little hairy, even with best JS libraries. 

Turbogears  uses mochitkit JS library -- it is really great for JS debugging. Opens new debug window and adds debug messages there, *much* better than clicking on dialog windows with debug messages. Javascript is crap language and no way around it, but with mochikit pain is tolerable. :-)

---

### Post by Mirrorball on 2007-01-01
I think Flash or Java would be your best options. Java if you want it free.

---

### Post by winch on 2007-01-01
I don't think java is an option becasue lots of people don't have a jvm installed. It's also a fairly big download so people won't download it just to play a small game.

---

### Post by viciouslime on 2007-01-01
> **winch said:**
> I don't think java is an option becasue lots of people don't have a jvm installed. It's also a fairly big download so people won't download it just to play a small game.

Hmmm, perhaps not as many people as have adobe flash player installed, but still a lot of people. Also, since sun have decided to opensource theirs i would think in the next year a whole lot more people will.

---

### Post by NoTiG on 2007-01-01
I want something thats open... but also fast... so i guess its .net vs aJax, vs plain java?

is it possible to do scalable vector graphics in real time? Since everyone will be using different resolutions, i want to be able to scale the images as they are drawn in real time instead of having a fixed window size for the lowest common denominator. I wonder if its even possible.........

---

### Post by Mirrorball on 2007-01-02
I wouldn't use .net on the client side if I wanted Linux/Mac users to play my game.

---

### Post by pmasiar on 2007-01-02
> **NoTiG said:**
> I want something thats open... but also fast... so i guess its .net vs aJax, vs plain java?

is it possible to do scalable vector graphics in real time? Since everyone will be using different resolutions, i want to be able to scale the images as they are drawn in real time instead of having a fixed window size for the lowest common denominator. I wonder if its even possible.........

Of course it is possible - it is a matter of simple programing...  :-)

For some vaues od "simple".  :twisted: 

Seriousle: speed is not a problem until it is a problem. 

How much functionality can reside on client, and what server needs to do?

You can go flash or java, but much cooler now is Ajax solution (looks better in your portfolio IMHO).

---

### Post by emperon on 2007-01-03
> **pmasiar said:**
> IronPython is great, but restricted to MS Windows platform - so I guess no much help on it here :-) Mono is promoted as "free" replacement of C# and .NET, but not many people are interested in it because unknown patent status.. :-)

The above is completely wrong. IronPython works fine on linux with mono. And for mono, it is patent status is not unkown. You guys may not be aware of the issue but, with fiesty (assuming it will include mono 1.2+) LINUX WILL HAVE NATIVE SUPPORT FOR .NET 1.1 applications  including with WINDOWS FORMS 1.1. This is a huge milestone in portability I suppose. Sun was ignorant on java and they were too late for recovery. I say, go for Python/Ruby if you only target linux. If you want windows as well, then going on mono is a descent option.

For the patent issue, note that mono it self is open sourced. And excluding the windows forms , ASP.NET, MS could never hinder the project. They could only claim patents on windows forms. And as Icaza him self told, in such a case, mono may drop the windows forms support and proceed its way as a good platform. Mono did what java couldn't so far. It is now a part of gnome!!

---

### Post by lnostdal on 2007-01-03
> **NoTiG said:**
> Just wondering.. i plan on making a pictionary like game through the browser.. i don't want it to be downloaded.... so i guess my options are flash, shockwave, and java, and .net? I was leaning towards ironpython.....

hum, if you "don't want it do be downloaded" - flash is probably your only option

..but ignoring that, i'd say java or python are your best bets as they are more mature than Mono..

---

### Post by emperon on 2007-01-03
It is true python and java are more mature than mono. But maturity for mono is not a concern  either. It is stable enough for general use

---

### Post by NoWhereMan on 2007-01-03
> **viciouslime said:**
> Hmmm, perhaps not as many people as have adobe flash player installed, but still a lot of people. Also, since sun have decided to opensource theirs i would think in the next year a whole lot more people will.

I wish this was true; they opensource'd only their JIT compiler, not the whole player...
btw, I would go with ajax, too, there are many great libs out there, which should help you (Yahoo UI, prototype; at the moment i like jQuery).

If you are a Java guy you may also want to have a look at google's Java to AJAX toolkit [http://code.google.com/webtoolkit/](http://code.google.com/webtoolkit/)

bye

---

### Post by emperon on 2007-01-04
> **NoWhereMan said:**
> I wish this was true; they opensource'd only their JIT compiler, not the whole player...


What do you mean by player ? Typically you would need two things. 1 is the compiler , 2nd is the vm. If you mean their VM Player thingie, then it is a completely different story. Mono is open source with its compiler and virtual machine and since from Gnome 2.16, it is a part of gnome

---

### Post by NoWhereMan on 2007-01-04
sorry I read Adobe instead of Sun. I thought you were talking about flash player :)

---

### Post by loell on 2007-01-04
lets stay on topic  and not make it mono vs several known languages.

practical browser games, can only have two options

its either ajax/javascript or flash with actionscript.

---

### Post by emperon on 2007-01-04
java applets are also an option. Although flash would be better.

---

### Post by loell on 2007-01-04
yeah it is, but not practical , who does it now a days?
making a game or an app through java applet might not be that attractive, the trend has always been that way since java's inception.

---

### Post by NoTiG on 2007-01-05
> **loell said:**
> lets stay on topic  and not make it mono vs several known languages.

practical browser games, can only have two options

its either ajax/javascript or flash with actionscript.


.Net / mono / ironpython isn't an option? My language of choice is python btw :P

---

### Post by daniel of sarnia on 2007-01-05
I herd on the FLOSS weakly pod cast Icaza say that mono is used to run even java by some banks. So I'd say it's pretty stable if that is that case.

I don't know how well it'd work for online gaming with Ironpython just because I myself have never used it that way.  But I don't think mono is getting enough credit here and it could turn out be a really good option. There are not patent issues no matter what Ballmer would like you to think about it and other open source projects, Microsoft made C# and I think .net and ISO stranded that can be implemented buy everyone although they did not obversely release the source code. 

Anyhow, I'd like to know how you make out when you get it done, because I am plaining on doing some fancy pants sites that entail the same sort of thing :). I'm not sure mono and asp are the thing to use but they might work well, I'm not sure. I'll likely end up using php css sql and flash because that is what I know best. I keep hearing all about ajax though, I think I'll investigate into that as well before I get started... I'm not sure, so many opines :confused:

EDIT: AHH now you guys really got me thinking too, is anyone here a pro web dev, if so what works best for you in this short of application?

---

### Post by emperon on 2007-01-05
> **NoTiG said:**
> .Net / mono / ironpython isn't an option? My language of choice is python btw :P


If you want a web application, then IronPython may not be an option unless you go with AJAX + ASP.NET which would be absurd for a game.

You should go for IronPython if and only if, you want to work on .NET /Mono and you want to use your python skills. If you only need python, then IronPython is no superior than Python it self (IronPython is much faster and have access to .NET libraries but these are rare requirements for a typical python developer)

If you will do conventional web application development ( not talking about games) then Ruby On Rails (or Django) is a must. It is far better than PHP, JEE or ASP.NET in terms of speed of development and/or joy of development.

---

### Post by daniel of sarnia on 2007-01-05
I herd that Django was way faster then rails, I almost forgot about it all together. Thanks for bringing it up. I'm headed over to the dejango page right now.

---

### Post by pmasiar on 2007-01-05
There is also another prime-time python web framework, TurboGears. While Django was designed and optimalized for content publishing (it runs Washington Post IIRC), autogenerates database management etc. Turbogears was designed with eye towards AJAX applications. And they say TG's javascript library is superior to Django. Just to show you more options.

Django's approach is: "we invent it and integrate it" (they started sooner when no much good parts were available). TG approach is: pick the best-of-the-breed parts and integrate it. So TG has better parts, and Django is better integrated :-)

Django **is** blessed by Guido as first choice py web frameworks, tho.

---

### Post by yaaarrrgg on 2007-01-05
For smaller games, Flash or Java are probably the best choices, IMO.  Both are well supported by the web browsers.  Flash is easier to develop with in many ways, but is not as free as I'd like it to be.

For Java, there is still plenty of interest in applets.  I don't have much interest personally in downloading and compiling a small game off the web, for time and security reasons.  But, I don't think much about playing an applet.  There's also some commercial demand for games as applets.

IMO .net and Python are not bad for development, but I would be much less likely to play the game if written in either.  I don't want to run something as a desktop app if I don't have to.  I'm not aware of any way to run .net "in the browser" except as a server side application.  THis will mean a lot of postbacks, and probably not what you want.

Ajax is probably the most interesting thing in web apps for a while, although not sure it's much easier to use than Java, or ready for prime time.  I'd expect you'd run into a few limitations in game development .. Also are you thinking of writing a server component?  To me, Flash, or an applet still seems simpler.

---

### Post by NoTiG on 2007-01-05
> **yaaarrrgg said:**
> For smaller games, Flash or Java are probably the best choices, IMO.  Both are well supported by the web browsers.  Flash is easier to develop with in many ways, but is not as free as I'd like it to be.

For Java, there is still plenty of interest in applets.  I don't have much interest personally in downloading and compiling a small game off the web, for time and security reasons.  But, I don't think much about playing an applet.  There's also some commercial demand for games as applets.

IMO .net and Python are not bad for development, but I would be much less likely to play the game if written in either.  I don't want to run something as a desktop app if I don't have to.  I'm not aware of any way to run .net "in the browser" except as a server side application.  THis will mean a lot of postbacks, and probably not what you want.

Ajax is probably the most interesting thing in web apps for a while, although not sure it's much easier to use than Java, or ready for prime time.  I'd expect you'd run into a few limitations in game development .. Also are you thinking of writing a server component?  To me, Flash, or an applet still seems simpler.

.Net can't be used in browser apps? I thought as long as you have the framework installed clientside, then it was possible. Granted most people don't yet but eventually with Vista they will......

I will use either ajax or ironpython. I would rather use ironpython but if its not possible then i will just use ajax.

---

### Post by pmasiar on 2007-01-05
> **NoTiG said:**
> . Granted most people don't yet but eventually with Vista they will.......

Vista on my desktop? NEVER!! [-(  Such heresy on Linux forum!!  :evil:  One of the reasons I started with Linux is to get rid of windows. And i am not alone: Some business people i presonally know are looking at Windows virus patching treadmill and they have enough. In USA cost (even if $400) is not as prohibitive, but in many countries Linux looks sweeter every day. :-)

Mind you I am not agains Bill Gates: I am against DRM on PC box I paid for.

---

### Post by NoTiG on 2007-01-05
> **pmasiar said:**
> Vista on my desktop? NEVER!! [-(  Such heresy on Linux forum!!  :evil:  One of the reasons I started with Linux is to get rid of windows. And i am not alone: Some business people i presonally know are looking at Windows virus patching treadmill and they have enough. In USA cost (even if $400) is not as prohibitive, but in many countries Linux looks sweeter every day. :-)

Mind you I am not agains Bill Gates: I am against DRM on PC box I paid for.

true... the game is intended for windows and linux though. so we will most likely hvae mono by default anyway. 

and the .net can be installed on xp.. i don't know about older versoins though... im still uncertain of it's client side purposes. like if it can actually make an isketch like game.... since this will be a big endeavor for me i will be planning

---

### Post by emperon on 2007-01-05
if you plan to run your game within a browser, then you have 3 practical options.
1-)Flash : this is your best bet
2-) Java applet: this is also okay, note that flash is installed 95%+ of the browsers. This ratio is much smaller for java plugin. Java applets in deed are in a downfall in recent years . For example yahoo games  are completely switched to flash from java.
3-) Ajax and javascript, this  is not a good option for  a game. Although it is possible, you will dig too much for graphics, prolly wont work for 3d graphics (although there are some few examples about how to achieve 3D rendering with pure javascript)

.NET  in browsers may be possible for IE only(not as a serverside). I am not expecting it will have any widely usage. Since there is now flash. So making a game running on a browser with IronPython doesn't make much sense.

There are a few things I'd like to add. Personally I am very much happy, that gnome welcomed mono project. .NET is definitely a valid replacement of java. Note that there were a lot of .NET versus Java  (or J2EE formerly, JEE now)  discussion went around. I have worked as a professional .NET developer and J2EE developer in several different projects. I can say when you deal with .NET , you play with MS's toys like Visual Studio 2005, VSTS and so on. But till now for enterprise development, .NET's database backend still works as set oriented where as j2ee has an Object Relational Mapping (like Hibernate and EJB 2/3) . World is leaning towards ORMs, like rails django and so on, so .NET is lagging huge in this sense. Although people discuss developing enterprise applications with .NET, I don't beleive it is feasable without any 3rd party database backend tools since as of .NET 2.0 , Microsoft is very weak on this part. Coming .NET 3.5, has technologies like DLINQ, LINQ , ADO.NET entity objects, which are official frameworks for ORM, released (in alpha) by MS. There are technology previews of these technologies, they are not ready for production. I think they will be ready for Visual Studio 2007 so called orcas. IMHO, they are not that good, VS generates hundreds of lines of code for a Entity mapper, and I dislike that much generated code. 

For C#, I have also studied the specs of coming C# 3.0. I think MS has realized the era for strongly typed languages is over. This is why in C# 3.0 they have keywords like "var" so that  a strongly typed language like C# can be more "dynamically typed". Comparing C# 3.0 to java 1.6 (1.5 and 1.4 are almost the same in terms of language syntax except generics), I have found C# overwhelmingly complex than java. I don't know if it is a good sign or bad sign, but I can definitely say, Ruby/Python is far better for general application development. Of course there are right tools for right jobs, but I really cannot think any situation C# is better than Python. MS is also aware of that, officially supports the project IronPython since last year. Nevertheless, there are some nice implementations of C# in gnome desktop like beagle and tomboy. Also Microsoft is planning to write its next OS kernel by a language called Sing# which is an extension of C# (mostly a contract based language)

As for java, IMHO sun killed java. There are many many java lovers now, and they will argue java still rocks. Only time will tell, but I can definitely say Sun also realized Java is verbose and the future is in the dynamically typed languages. This is why they hired the guys working on JRuby for fulltime work.

Coming for IronPython, I should admit, at first I was very much excited with  the idea. I was a fan of CLR at that time and I thought, I could use a language like python with the Power of CLR. The thing is CLR is not designed for dynamically typed languages, this is why it has no future. IronPython developer admits, he was expecting a lot of trouble for the integration of CLR and IronPython before he was starting the project. He adds, the project went surprisingly easy though. There is also a Ruby CLR integration. However the developer complains it is impossible to implement some idioms of Ruby to CLR without smart workarounds.

---

### Post by pmasiar on 2007-01-05
> **emperon said:**
> For C#, I have also studied the specs of coming C# 3.0. I think MS has realized the era for strongly typed languages is over.  

I agree. CPU speed is increasing, you need to waste it doing something - and programmer's productivity does not double every 18 months (maybe 18 years :twisted: ). Jelly-like wobbly windows is not right use of CPU cycles :-) Dynamically checking type might be smarter use. You check for many other things dynamically anyway.

>  I have found C# overwhelmingly complex than java. 

This usually happens to MS solutions :twisted: Backward compatibility, designed by committee, no thanks, I prefer wait to version 3 or 4. :-) As Linus famously said: "Linux is *not* inteligent design - it is evolution" :p 

> MS is also aware of that, officially supports the project IronPython since last year. 

Not only that: MS poached Jim Hugunin, who was working on Jython - Python build on top of Java. Jim is building IronPython now, preaching dynamic typing in MS, and making CLR better for dynamic languages.

> As for java, IMHO sun killed java. There are many many java lovers now, and they will argue java still rocks. Only time will tell, but I can definitely say Sun also realized Java is verbose and the future is in the dynamically typed languages. This is why they hired the guys working on JRuby for fulltime work.

Obviously Sun killed java. For Sun, releasing  java under GPL (free license, to add maybe 10 more years to lifetime) has more value than keeping it closed and proprietary. You won't release something which can make you money unless you have to. Java == Cobol++ :twisted: 

> Coming for IronPython, I should admit, at first I was very much excited with  the idea. I was a fan of CLR at that time and I thought, I could use a language like python with the Power of CLR. The thing is CLR is not designed for dynamically typed languages, this is why it has no future. IronPython developer admits, he was expecting a lot of trouble for the integration of CLR and IronPython before he was starting the project. He adds, the project went surprisingly easy though. 

CLR is easier to change than C# - has less users and most of them are inside MS. That is exactly what Jim Hugunin is paid to do. We'll see, MS has $50B to play with and learn new tricks - and Office is their main cash cow anyway. DRM is coming to computer near you :evil:

MS strategy is "embrace, extend, choke" .NET + mono are only in embrace phase ... :twisted: And they will need each other to fight free java.

---

### Post by loell on 2007-01-12
just an update of javascript base game, proof of concept :) 



[http://www.abrahamjoffe.com.au/ben/canvascape/]("http://www.abrahamjoffe.com.au/ben/canvascape/")

---

### Post by Tomosaur on 2007-01-12
> **loell said:**
> just an update of javascript base game, proof of concept :) 



[http://www.abrahamjoffe.com.au/ben/canvascape/]("http://www.abrahamjoffe.com.au/ben/canvascape/")

Woah, was that you who made that? I saw that months ago, it's great. Nice work :)

---

### Post by loell on 2007-01-13
no no =;  , well a digg addict , it just shows up in the programming section, i just thought to share this in this thread, for people who have an interest in doing browser base games. :mrgreen:

---

### Post by Tomosaur on 2007-01-13
Ah well, it's still cool :)

---

### Post by laxmanb on 2007-01-14
You can make cool games using Java as well... check out [www.puppygames.net](www.puppygames.net)

tho flash would be better... it's more ubiquitous than a JRE...

---

### Post by Grey on 2007-01-14
OpenGL is supposed to be included in the canvas element of Firefox 3.0.  That will completely blow the lid off of browser games.

I had really wanted to beat everyone to the punch by making some good DHTML browser games.  But it seems that it's just not going to happen.  I'm too busy, and I think other people are getting the idea too.

My thought was that it was entirely possible to make an RTS game, along the lines of Starcraft for a web browser, allowing 4 player matches, entirely with javascript.  I got the map displaying, and a mapping tool built.  But I don't have any real infrastructure for the game yet.  And I'm not likely to.  The map scrolling is plagued by performance issues if you make it full screen though.  (In everything but IE.  It loads slow in IE, but plays extremely fast)

---

### Post by emperon on 2007-01-15
yeah and it is possible to build an enterprise ERP or CRM application with assembly or machine code. I am fairly experienced with javascript. The current version of javascript is 1.5 or 1.6. Javascript sucks. This is even not arguable. We use javascript because it is the only scripting language widely adopted by most of the browsers. Other than that, I strongly believe we should throw away javascript to the garbage where COBOL lies.

---

### Post by rowlando on 2007-01-16
In order to defend JavaScript as a useful language, please read the following:

[JavaScript and "serious" programmers]("http://www.quirksmode.org/blog/archives/2005/11/javascript_and_1.html")

---

### Post by NoTiG on 2007-03-31
> **Grey said:**
> OpenGL is supposed to be included in the canvas element of Firefox 3.0.  That will completely blow the lid off of browser games.



can someone explain this? what language would you use ? javascript?

---

### Post by NoTiG on 2007-03-31
I have since changed my mind about flash... and am deciding to use the best tool for the job. I plan on using Fjax... just a combination of flash and ajax...  If anyone wants an idea of what the program will be for... it will be like a combination of spogg.com (with personal pages) and isketch.net ... a shockwave implementation. and then i will use Python server side.

---

### Post by NoTiG on 2007-03-31
Hate to bump my own thread, this will be the last time...

but is Openlaszlo the alternative i have been looking for ?

> OpenLaszlo is an open source development platform for web applications. It's main target today is generating macromedia flash files (swf)and AJAX/DHTML for use on web pages and sites. OpenLaszlo is script based with it's own LZX programming language - and eventhough it does not provide a wysiwyg user interface it a still simple to use and applications are easy to build. For building rich internet applications OpenLaszlo is a great tool. And recently OpenLaszlo and SUN made a joint announcement to make OpenLaszlo available on Java micro edition (J2ME), which includes mobilephones and set-top boxes.

---


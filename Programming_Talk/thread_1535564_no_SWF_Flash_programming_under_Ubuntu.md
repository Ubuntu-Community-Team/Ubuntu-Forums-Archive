---
title: "no SWF Flash programming under Ubuntu?"
date: 2010-07-21
forum: Programming Talk
---

### Post by rebeltaz on 2010-07-21
I want to learn to program Flash based games, but I cannot find a single program for doing so under Linux. Am I just missing it or is there a better alternative for net-based games?

---

### Post by lykeion on 2010-07-21
> **rebeltaz said:**
> I want to learn to program Flash based games, but I cannot find a single program for doing so under Linux. Am I just missing it or is there a better alternative for net-based games?

I'm not really sure what you're asking for here. Are you looking for an equivalent to Flash CS5 on linux?
Most Flash game developers don't use CS5, they write code using an IDE like Eclipse with FDT. 
These applications are available to linux also. FDT is commercial but there is a Free version you can use, or you could use Flex Builder.

Your second question about better alternatives is also very vague. Better for what? What kind of "net-based games" are you thinking of? 
Flash, JavaScript, Java Applets all have their pros and cons. You should pick the language based on what kind of game you are writing, the target audience for the game, and how capable you are in that language. 

If you are new to programming, my tip would be to would avoid JavaScript and learn to write a Java Applet, because Java it's a good foundation to learn other languages.
But if you think Flash is more interesting you should go for this. Start by doing some beginner tutorials, then move on to write a complete application. 
After you think you have some kind of grip of the basics of the language you could start thinking of writing a game.

---

### Post by ja660k on 2010-07-21
No, Flash, Photoshop, Illustrator ...etc are not available for linux.
if your really keen the best chance you have is either:
Install wine, then photoshop **OR**
get a vm with windows and install it... but you'd need ALOT of ram to do this because flash sucks down the juice

---

### Post by rebeltaz on 2010-07-21
> **lykeion said:**
> I'm not really sure what you're asking for here. Are you looking for an equivalent to Flash CS5 on linux?

I know... I'm not really sure what I was asking either. I want to learn to design a FarmVille type game for my website, but I'm not sure of the game yet. I thought I'd learn the laguage first, see what I could do with it and then decide on the basics of the game.

> **lykeion said:**
> Your second question about better alternatives is also very vague. Better for what? What kind of "net-based games" are you thinking of? 
Flash, JavaScript, Java Applets all have their pros and cons. You should pick the language based on what kind of game you are writing, the target audience for the game, and how capable you are in that language. 

If you are new to programming, my tip would be to would avoid JavaScript and learn to write a Java Applet, because Java it's a good foundation to learn other languages.
But if you think Flash is more interesting you should go for this. Start by doing some beginner tutorials, then move on to write a complete application. 
After you think you have some kind of grip of the basics of the language you could start thinking of writing a game.

I can program in all of the variants of BASIC, PHP, HTML, and with a reference book close by - C++. So I'm not new to programming, but I am totally lost in game programming. Especially for web-based games. 

> **ja660k said:**
> No, Flash, Photoshop, Illustrator ...etc are not available for linux.
if your really keen the best chance you have is either:
Install wine, then photoshop **OR**
get a vm with windows and install it... but you'd need ALOT of ram to do this because flash sucks down the juice

I do have both Wine and Sun Virtualbox installed. I just hate having to give in and run Windows software on a Linux machine. I feel like I'm cheating on my OS ;)

---

### Post by ja660k on 2010-07-21
> **rebeltaz said:**
> 
I do have both Wine and Sun Virtualbox installed. I just hate having to give in and run Windows software on a Linux machine. I feel like I'm cheating on my OS ;)
a little part of me dies inside when i have to **resort** to windows.

---

### Post by shadylookin on 2010-07-21
you could take a look into Flex. I think it's better for programmers. The sdk is open source and runs on linux. Though the last time I looked there were no IDEs for it.

I would consider using html, javascript, and css as an alternative. html5 especially.  

I would definitely not consider java applets or silverlight.

---

### Post by lykeion on 2010-07-22
> **rebeltaz said:**
> I can program in all of the variants of BASIC, PHP, HTML, and with a reference book close by - C++. So I'm not new to programming, but I am totally lost in game programming. Especially for web-based games.Basic - arcane, HTML - not a programming language, PHP - maybe for text-based games, C++ - there you go.
Here are som game development links you might find useful:

[http://wiki.gamedev.net/index.php/How_do_I_get_Started](http://wiki.gamedev.net/index.php/How_do_I_get_Started)
[http://www.gamedev.net/reference/start_here/](http://www.gamedev.net/reference/start_here/)
 

> **rebeltaz said:**
> I do have both Wine and Sun Virtualbox installed. I just hate having to give in and run Windows software on a Linux machine. I feel like I'm cheating on my OS ;)I am totally sure that you don't need to switch to Windows for game development. Most of the game frameworks are cross platform.

---

### Post by rebeltaz on 2010-07-22
> **lykeion said:**
> Basic - arcane, HTML - not a programming language, PHP - maybe for text-based games, C++ - there you go.
Here are som game development links you might find useful:

[http://wiki.gamedev.net/index.php/How_do_I_get_Started](http://wiki.gamedev.net/index.php/How_do_I_get_Started)
[http://www.gamedev.net/reference/start_here/](http://www.gamedev.net/reference/start_here/)


I wasn't suggesting that any of those languages were useful for what I wanted to do. I was only illustrating that I do understand programming - that I wasn't new to computer languages. I will check out those links tonight, though...

---

### Post by lykeion on 2010-07-23
If you plan to do a larger project like the game you mentioned, I suggest you work in an IDE.
For this I'd suggest Eclipse, but if you are familiar with another IDE you should use this, so that you don't have to spend a lot of time learning a new IDE.

My experince of game development is that it takes a lot of planning before you actually do any coding.
Also you should be aware that designing game graphics and sounds can be equally time consuming as the actual code writing.

As for the choice of platform I'd go for Flash. Farmville seems to be written in Flash (as well as the game they stole the idea from Farm Town). 
There's a good guide setting up Eclipse and FDT here:

_[Flash development in Ubuntu 10.04 with Eclipse and FDT]("http://www.brighthub.com/hubfolio/matthew-casperson/articles/73648.aspx#ixzz0uVxMCHYJ")_
 
Since you're familiar with C++ I also found this:

_[AS3 programming 101 for C/C++ coders]("http://blogs.adobe.com/kiwi/2006/05/as3_programming_101_for_cc_cod_1.html")_

---

### Post by gordebak on 2011-01-29
You can use Flex SDK for Flash development with ActionScript on Linux. If you don't have Flash, you can embed bitmap graphics into your Flash game. 

I've tried and seen a lot of Flash games with bitmap graphics, and they all worked fine.

Good luck.

---

### Post by The Kraken on 2011-12-19
I'm interested in game programing as well, though I'm still new to programing and trying to learn the basics. I'm not sure how much this will help or if they would work in linux, but I did find some game engines for flash. Pretty much just pre-made classes that do a lot of the coding for you so you can get into the actual game making part.

[http://flixel.org/](http://flixel.org/) more of a retro style game, this is free.

[http://citrusengine.com/](http://citrusengine.com/) as far as I know this is now free. 

[http://box2d.org/about/](http://box2d.org/about/)  this was intended for C++ but got a port to AS3 which is Box2DAS3 (or something similar)

Might be worth taking a look at to at least get some ideas where to start when coding your own game.

---


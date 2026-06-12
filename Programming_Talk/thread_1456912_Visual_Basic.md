---
title: "Visual Basic"
date: 2010-04-17
forum: Programming Talk
---

### Post by orphanlast on 2010-04-17
I'm sorry if I'm asking tons of stupid questions. I just finished off from work 3 hours ago and I've been googling this stuff for quite a while and found nothing. Getting into programming and just starting off with Linux and trying to find out what you're supposed to know, do, and find out is really difficult.

I've been told by people that if I'm going to start off in programming I should probably start off with VB. Now... I've gone off in left field and looked at Gambas which is not the same thing and from my reserach, no one uses it -- even if it's similar to VB.

Seeing as VB is a Microsoft developed programming language it's only until a program called MONO came out that VB is available to Linux users. (Hopefully I'll be able to open the programs after I program them with VB. Who knows they might just be an .exe... and wouldn't that just be wonderful.)

So, I now have Mono on my computer (not the VD but the program). From what I've seen, it appears to be a universal compiler for multiple programming languages including VB (sometimes reffered to as VBNET or VB.NET).

It's amazing. I've found the program but instead of talking about how to use it, every site I go to talks about how much of a revolution Mono is and general junk about how wonderful the program is.

So... Where's a good starting point? Some comprehensive information. A place where I might have some tutorials to work with that aren't just immediately steeped in Jargon but slowly work their way into that sort of thing?

---

### Post by MattTastic on 2010-04-17
If you just hang out and look for a few VB hello world tutorials then they should run fine in the mono development environment... maybe I don't know really cause I haven't tried it myself.

Just on a side note, I started programming in a language called QBASIC, which lead onto VB.

I guess VB would be a good language to mess about with, but it's very much more drawing boxes and very little written code. Maybe a simple crap language like javascript (it's actually quite powerful really) might be a good idea, all you need is a browser and a text editor to get some stuff going. 

But I'm probably just confusing the situation really. Google VB tutorial and find a beginners one, real simple like.

---

### Post by jkxx on 2010-04-17
Both Mono and .NET compile any/all of their languages to MSIL so your VB.NET app will run about as well as C# app once compiled, so far so good.

Please see this recent story [http://yro.slashdot.org/story/10/03/25/1331255/De-Icaza-Says-Microsoft-Has-Shot-NET-Ecosystem-In-Foot]("http://yro.slashdot.org/story/10/03/25/1331255/De-Icaza-Says-Microsoft-Has-Shot-NET-Ecosystem-In-Foot") on why you might want to avoid .NET if you are on a Linux platform, the warning comes from the man behind Mono himself.

And to your original question, right off the top of my head, you can look at programming examples at [http://www.codeproject.com/]("http://www.codeproject.com/") and they have plenty of languages covered.

---

### Post by orphanlast on 2010-04-17
Well... if vb is basically a trash program then there's really no reason to use it. I'm wanting to program for practical reasons.

You said I could just use a text program. But I think I'm starting to like Compilers because it monitors the code you've written and assigns each line to a number. So when it says "Error on line 65" you don't have to look for some small error through the whole document.

Is there any sort of compiler or any sort of programs that might be able to help with Javascript that you would personally recommend?

---

### Post by dominiquec on 2010-04-17
This'll take the thread sideways, so I hope you don't mind: if you're still open to other programming languages and development environments, a good starting point might be Python (for the language) and Geany (for the IDE).  Python is installed by default in Ubuntu and most other distros; Geany is a pretty intuitive IDE to get started in (also supports other languages like Perl, C/C++, Java, and yes, Javascript, among others.)

---

### Post by orphanlast on 2010-04-17
Well... ultimately, I'm interested in whatever program will be able to used for most anything.

Like... as an example. I look at Gimp and I can't help but think it's stupid. It's primitive and I can't see how anyone can think it even comes close to photoshop. Photoshop is supremely superior SUPREMELY. And I'd like to mess around with the program and submit whatever things I've done to it to the developers... maybe... Ultimately Linux is kind of a new thing, so I don't know if I'm not considering any type of open source etiquette. 

I've submitted various brainstorms to them but they haven't emailed me back. I don't think they take me seriously and if I knew how to program, I'm sure they'd do more than just brush me off.
***[[B]**]("http://www.google.com/search?hl=en&q=etiquette&revid=222406290&ei=_HDKS5TKD4L4sgOYqNH4Ag&sa=X&oi=revisions_narrow&resnum=4&ct=revision&ved=0CBoQ3gIwAw")*[/B]

---

### Post by orphanlast on 2010-04-17
I've been at this for two days. Yesterday was my day off. I spent near 24 hours trying to find a starting point to programming stuff. 5 hours more in trying to figure this junk out and I'm still at square one trying to find out where I need to start.

The tutorials I've found are all retarded because none of them explain how to work the compilers... Really, people just intentionally make this more complicated than it needs to be.

I'm sick of this. After I find the ultimate program there's all these tutorials that will explain how to mess with code but not how to use the compiler with it. So you can spend all the time in the world typing up all this code but if you don't know how to work the compiler, well, you're hosed.

So much for the practical use of a Tutorial if the Tutorial doesn't even do it's job.

---

### Post by madjr on 2010-04-17
> **orphanlast said:**
> Well... ultimately, I'm interested in whatever program will be able to used for most anything.

Like... as an example. I look at Gimp and I can't help but think it's stupid. It's primitive and I can't see how anyone can think it even comes close to photoshop. Photoshop is supremely superior SUPREMELY. And I'd like to mess around with the program and submit whatever things I've done to it to the developers... maybe... Ultimately Linux is kind of a new thing, so I don't know if I'm not considering any type of open source etiquette. 

I've submitted various brainstorms to them but they haven't emailed me back. I don't think they take me seriously and if I knew how to program, I'm sure they'd do more than just brush me off.
***[[B]**]("http://www.google.com/search?hl=en&q=etiquette&revid=222406290&ei=_HDKS5TKD4L4sgOYqNH4Ag&sa=X&oi=revisions_narrow&resnum=4&ct=revision&ved=0CBoQ3gIwAw")*[/B]


hmm i have to disagree about photoshop "superior SUPREMELY"

gimp is the second most used photo editor in the world (hundreds of thousands use it professionally, so you saying they're all wrong and should pay tons of $ to adobe they could use to live? not everyone has the resources or wants to use photoshop, for many it has [been quite buggy and unstable]("http://www.buzzfeed.com/awesomer/the-15-least-helpful-adobe-crash-reports"))

you can find a video to do about anything on youtube, it's just a matter of getting used to

in fact the primary critique about gimp is that it doesnt have 1 window, well it was made primary for Macs first about 14 years ago so mac uses have always been comfortable with it.

now when **2.8** version is released it will get the [1 window mode]("http://www.youtube.com/watch?v=r2gonFtc1yc") feature windows users wanted. so not much to complain about it anymore.

on a side note the latest photoshop cs5 had nothing new to offer so they're **copying features off GIMP now**

[http://www.omgubuntu.co.uk/2010/03/photoshop-cs5s-showpiece-is-plugin-gimp.html](http://www.omgubuntu.co.uk/2010/03/photoshop-cs5s-showpiece-is-plugin-gimp.html)

it's just code, you cant say commercial programs are "supreme", is just a matter of time all open source catches up and in many cases it already has or surpassed commercial solutions.

---

### Post by madjr on 2010-04-17
> **orphanlast said:**
> I've been at this for two days. Yesterday was my day off. I spent near 24 hours trying to find a starting point to programming stuff. 5 hours more in trying to figure this junk out and I'm still at square one trying to find out where I need to start.

The tutorials I've found are all retarded because none of them explain how to work the compilers... Really, people just intentionally make this more complicated than it needs to be.

I'm sick of this. After I find the ultimate program there's all these tutorials that will explain how to mess with code but not how to use the compiler with it. So you can spend all the time in the world typing up all this code but if you don't know how to work the compiler, well, you're hosed.

So much for the practical use of a Tutorial if the Tutorial doesn't even do it's job.

that's the programming world for you, yea it's **not easy**, that's why they get payed so much.

have you taken any classes, or have any background or experience ?

if you're a first timer, I've come across some courses, not too long ago, and might look em up for you if you're interested

the hardest part of programming is not writing the code, but understanding and breaking up the logic

writing the code sometimes is the easy part

---

### Post by orphanlast on 2010-04-17
I haven't taken any classes other than to learn HTML when I was in highschool and the teacher just told us to copy down a website's html word for word and keep looking at the website we were recreating and through that reference back and forth from the website and back to the HTML I was able to get rather good at it (before I stopped using it and forgot it all entirely).

I was thinking that doing something similar with some real coding programs might be a good way to try and learn... school of hard knocks....

I just can't seem to get to that point. And I wouldn't even be able to afford classes right now. This was supposed to be a hobby. Instead it has become this giant pain in the butt.

What I don't get is how Linux is this big reinforcement for developer creativity but none of the developers seem to have made Linux able to open Mac and Windows programs with just a simple double click (people like to say Linux plays all software... but that's only if you know what you're doing) and with so much freedom in Linux, I don't see why so many developers haven't used that freedom to simplify the method a little or to make any of this easier to get into.

This Linux community is really closed off.

Like... I would want to contribute. I would like to make Gimp awesome and I'd like to make Linux easier to use for the average consumer... (like how Linux developers should be doing in the first place). But... I can't even get started.

---

### Post by orphanlast on 2010-04-18
> **madjr said:**
>  gimp is the second most used photo editor in the world (hundreds of thousands use it professionally, so you saying they're all wrong and should pay tons of $ to adobe they could use to live? not everyone has the resources or wants to use photoshop, for many it has [been quite buggy and unstable]("http://www.buzzfeed.com/awesomer/the-15-least-helpful-adobe-crash-reports")) 

Gimp really lacks key attributes that photoshop has. I'm amazed at how much it's behind. I'm sure it's used by lots of people but it forces you to destroy and mutilate pixels, big no-no's if you're in the graphic design industry these days. 

And if people wanted to get programs for cheap or free, there's all sorts of ways to do it. Lol.

>  you can find a video to do about anything on youtube, it's just a matter of getting used to Youtube IS my first choice. I completely agree. It doesn't seem to be too helpful with C++, though. I think I might have found someone there that makes some half decent tutorials for it though... But of course, he's using a different compiler... one that's not compatable with Linux (though it should be... because... It's Linux... the magical OS that's said to run anything).

>  in fact the primary critique about gimp is that it doesnt have 1 window, well it was made primary for Macs first about 14 years ago so mac uses have always been comfortable with it. I'm comfortable with that. I love that. It takes a little of getting used to because sometimes I open up a picture without gimp and I start wondering why my art tools aren't working on it.... then I realise I need to open it through Gimp.

>  gimp now when **2.8** version is released it will get the [1 window mode]("http://www.youtube.com/watch?v=r2gonFtc1yc") feature windows users wanted. so not much to complain about it anymore. But layer masks and a straight forward way to morph things is key. Say I want to make a lady wearing a Bikini to look "flawless" (by magazine standard). I would have to go to FILTERS>DISTORTIONS>IMORPH and eye it and continually play with it without ever having a clear view of what I'm doing. The repetition of going into the IMORPH menu winds up damaging the pixels... I will admit that I've looked at a few tutorials, but I'm pretty competent with photoshop and after those few tutorials I feel as thought I have a good understanding of Gimp. The transition is somewhat easy. Now... hopefully I'm not just making a hasty generalization though.

What I do like is how smooth GIMP runs and how fast it loads. I really actually like the way the smudge tool feels and looks. There are some well executed things in Gimp. But it just doesn't compare. 

Though I'm frustrated with how long it takes for Photoshop to come up and how slow it can run after you have quite a bit of things going on with it... Photoshop undeniably has more tools. More options. And with all that, more freedom. More problem solving skills. More ways to solve one problem. Some faster, some slower... some more effective, some more professional and some not.

>  on a side note the latest photoshop cs5 had nothing new to offer so they're **copying features off GIMP now** I've only heard of CS4, so far. That's disappointing that Adobe is now stealing ideas from Gimp... but you'd think that Gimp would see something from Photoshop and try to one up it by executing the same sort of tool but used differently.

Like... as an example. I don't even like Photoshop's way of morphing images. It's better than Gimp's method though. What I think would be cool is to have another tool in the tool box be able to select it. Draw a line on the object you want morphed and then draw another line on where you want it to be and in what shape you want it to be. Press enter and *pop*. Done.

> 
  [http://www.omgubuntu.co.uk/2010/03/photoshop-cs5s-showpiece-is-plugin-gimp.html](http://www.omgubuntu.co.uk/2010/03/photoshop-cs5s-showpiece-is-plugin-gimp.html)

it's just code, you cant say commercial programs are "supreme", is just a matter of time all open source catches up and in many cases it already has or surpassed commercial solutions.... yeah... It has... but it's not comprehensive.

My first week using ubuntu was hell.  Heck... half the time I still don't know what I'm doing.

Again... People like to brag about how Linux can run any program from any operating system. So after hearing so many wonderful things about Linux, I finally got it. I thought it would be all ready to work just as well as Windows or Mac OS. I didn't know I'd have to download all sorts of junk just to get it to work comfortably.

... Again... I don't think Linux or open source has anything to brag about until you can install a linux os and be able to double click any file that's normally on MS Windows or Mac OS and have it instantly work.

The best we got is Wine... and the developers for Wine freely admit that it's not an emulator for windows... just something that sometimes works in opening some Windows programs.

that's like programming a calculator and deciding to only let the equals button work at random.

That's just lame.

---

### Post by madjr on 2010-04-18
> **orphanlast said:**
> Gimp really lacks key attributes that photoshop has. I'm amazed at how much it's behind. I'm sure it's used by lots of people but it forces you to destroy and mutilate pixels, big no-no's if you're in the graphic design industry these days. 

And if people wanted to get programs for cheap or free, there's all sorts of ways to do it. Lol.

Youtube IS my first choice. I completely agree. It doesn't seem to be too helpful with C++, though. I think I might have found someone there that makes some half decent tutorials for it though... But of course, he's using a different compiler... one that's not compatable with Linux (though it should be... because... It's Linux... the magical OS that's said to run anything).

I'm comfortable with that. I love that. It takes a little of getting used to because sometimes I open up a picture without gimp and I start wondering why my art tools aren't working on it.... then I realise I need to open it through Gimp.

But layer masks and a straight forward way to morph things is key. Say I want to make a lady wearing a Bikini to look "flawless" (by magazine standard). I would have to go to FILTERS>DISTORTIONS>IMORPH and eye it and continually play with it without ever having a clear view of what I'm doing. The repetition of going into the IMORPH menu winds up damaging the pixels... I will admit that I've looked at a few tutorials, but I'm pretty competent with photoshop and after those few tutorials I feel as thought I have a good understanding of Gimp. The transition is somewhat easy. Now... hopefully I'm not just making a hasty generalization though.

What I do like is how smooth GIMP runs and how fast it loads. I really actually like the way the smudge tool feels and looks. There are some well executed things in Gimp. But it just doesn't compare. 

Though I'm frustrated with how long it takes for Photoshop to come up and how slow it can run after you have quite a bit of things going on with it... Photoshop undeniably has more tools. More options. And with all that, more freedom. More problem solving skills. More ways to solve one problem. Some faster, some slower... some more effective, some more professional and some not.

I've only heard of CS4, so far. That's disappointing that Adobe is now stealing ideas from Gimp... but you'd think that Gimp would see something from Photoshop and try to one up it by executing the same sort of tool but used differently.

Like... as an example. I don't even like Photoshop's way of morphing images. It's better than Gimp's method though. What I think would be cool is to have another tool in the tool box be able to select it. Draw a line on the object you want morphed and then draw another line on where you want it to be and in what shape you want it to be. Press enter and *pop*. Done.

... yeah... It has... but it's not comprehensive.

My first week using ubuntu was hell.  Heck... half the time I still don't know what I'm doing.

Again... People like to brag about how Linux can run any program from any operating system. So after hearing so many wonderful things about Linux, I finally got it. I thought it would be all ready to work just as well as Windows or Mac OS. I didn't know I'd have to download all sorts of junk just to get it to work comfortably.

... Again... I don't think Linux or open source has anything to brag about until you can install a linux os and be able to double click any file that's normally on MS Windows or Mac OS and have it instantly work.

The best we got is Wine... and the developers for Wine freely admit that it's not an emulator for windows... just something that sometimes works in opening some Windows programs.

that's like programming a calculator and deciding to only let the equals button work at random.

That's just lame.

wow i agree that's lame..

i don't know who made you think linux can run any program from any other OS?

that's virtually impossible and whomever told you that needs to get kicked in the head.

every OS has some programs of it's own. is like saying that the iphone can run flash built for android.

i mean Wine/cedega is a windows layer **reversed engineered**. sure you can run lots of games and programs, but only the ones they were able to optimize/tweak.

it's been an uphill battle against the monopoly. These guys do all this stuff in their spare time, most of them dont even get payed. So is a miracle that wine is even usable at the moment, i give them credit for doing such incredible work.

anyway i might recommend some free virtualization software for you


virtualbox overview
[http://www.youtube.com/watch?v=DCylwztAJpI&feature=related](http://www.youtube.com/watch?v=DCylwztAJpI&feature=related)

installation
[http://www.youtube.com/watch?v=g_pRcLEXUu0&feature=related](http://www.youtube.com/watch?v=g_pRcLEXUu0&feature=related)
[http://www.youtube.com/watch?v=bfHRBIBFdsE](http://www.youtube.com/watch?v=bfHRBIBFdsE)


> **orphanlast said:**
> 

And if people wanted to get programs for cheap or free, there's all sorts of ways to do it. Lol.


piracy ;/
it's one of the reasons why open source was created so governments and average people wouldn't need to steal.
I know i did it back when i was a windows user, i didnt really feel good about it and always got my computer infected in some way. I was really glad when i discovered open source


i saw your other thread, i left a few tips and how it was for me
[http://ubuntuforums.org/showthread.php?p=9137957](http://ubuntuforums.org/showthread.php?p=9137957)

if you need further help just let us know :)

*edit:*
oh almost forgot. apart from gimp the next one most used is krita
[http://www.koffice.org/krita/](http://www.koffice.org/krita/)

is not as popular as gimp but you might feel more confortable with it till gimp releases it's new version.

and to learn some basic programming while having a bit of fun you could use something like 
robocode (in software center) 
[http://en.wikipedia.org/wiki/Robocode](http://en.wikipedia.org/wiki/Robocode)

or robomind
[http://www.robomind.net/en/index.html](http://www.robomind.net/en/index.html)

---

### Post by slavik on 2010-04-18
> **orphanlast said:**
> I'm sorry if I'm asking tons of stupid questions. I just finished off from work 3 hours ago and I've been googling this stuff for quite a while and found nothing. Getting into programming and just starting off with Linux and trying to find out what you're supposed to know, do, and find out is really difficult.

I've been told by people that if I'm going to start off in programming I should probably start off with VB. Now... I've gone off in left field and looked at Gambas which is not the same thing and from my reserach, no one uses it -- even if it's similar to VB.

Seeing as VB is a Microsoft developed programming language it's only until a program called MONO came out that VB is available to Linux users. (Hopefully I'll be able to open the programs after I program them with VB. Who knows they might just be an .exe... and wouldn't that just be wonderful.)

So, I now have Mono on my computer (not the VD but the program). From what I've seen, it appears to be a universal compiler for multiple programming languages including VB (sometimes reffered to as VBNET or VB.NET).

It's amazing. I've found the program but instead of talking about how to use it, every site I go to talks about how much of a revolution Mono is and general junk about how wonderful the program is.

So... Where's a good starting point? Some comprehensive information. A place where I might have some tutorials to work with that aren't just immediately steeped in Jargon but slowly work their way into that sort of thing?
To steer this thread back to topic. Install Monodevelop.

---

### Post by orphanlast on 2010-04-18
> **slavik said:**
> To steer this thread back to topic. Install Monodevelop.

I actually have mono on my computer right now. The problem that I'm facing right now is the fact that every tutorial just talks about code... and I'm not familiar with Mono. For example. If I go FILE>NEW it'll come up with FILE or SOLUTION... When I thought I'd need something that's more like "Project". If I select "FILE" then select VBNET it gets me a selection of ASP.net, General, GTK, and Misc... I'm assuming (off no logic at all) that I should pick "General" If I select that then I have a selection of more stuff that no tutorial seems to discuss. The selection is Empty Class, Empty Enumeration, Empty Interface, Empty Struct, and Empty file. I have no idea what I need. So I select "Empty File"... and it comes up with a screen full of red squiggles and looks nothing like an interface used for VB on any of the tutorials I've seen...

This looks like the program. I'm just litterally, VERY new at this.

---

### Post by slavik on 2010-04-18
"solution" is what you're looking for. this terminology is taken from Microsoft.

---

### Post by MattTastic on 2010-04-18
Hey buddy, sorry to hear you have had such a rough ride with you venture into the Linux world. And I should hope you now realise as Madjr pointed out that Linux never claimed it can run everything from everyone else.

It is true that Linux can seem like a bit of a mess,  sometimes it seems there are as many distros as there are user. But it is a triumph that it can even exist in this modern Microsoft/propriety driven world, especially considering it is mostly developed by guys and gals in their spare time.

On the programming issue, someone mentioned trying out python, it's a nice little language real easy to work with. I know you want a compiler based language, this one is what is called an interpretive language, i.e. the code you write is figure out on the fly by an interpreter (VB incidentally is an interpretive language also). But you should really get into the mode of a programming language i.e. control statements like if-then-else, and do loops, while statement all that nice stuff, you'll learn all about it in time.

I haven't had a chance to check out this magazine, it's an open source, free monthly online magazine dedicated to all things Ubuntu. They are on issue 35 at the moment, but as I was looking around at what kind of content they write about I noticed that they have a nine part guide on Python.

[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

This magazine is written by members of this forum, here is their section of the forum.

[http://ubuntuforums.org/forumdisplay.php?f=270](http://ubuntuforums.org/forumdisplay.php?f=270)

... compilers and object oriented programming (you'll learn about that in time too) are a whole other business. It's going to be a tough job getting into the real nitty gritty of programming and you don't want to try and go too deep too fast.

---

### Post by simeon87 on 2010-04-18
> **orphanlast said:**
> What I don't get is how Linux is this big reinforcement for developer creativity but none of the developers seem to have made Linux able to open Mac and Windows programs with just a simple double click (people like to say Linux plays all software... but that's only if you know what you're doing) and with so much freedom in Linux, I don't see why so many developers haven't used that freedom to simplify the method a little or to make any of this easier to get into.

Because Windows and Mac are not Linux's goal? Linux very much is a reinforcement for developer creativity if we look at the integration of compilers and languages like Python that make it easy to develop new applications, if you're willing take the necessary steps to learn it. Yes, some people are working on integrating and working with Windows/Mac applications and files on Linux. But, if you do not lead, you will forever follow: why not develop a free equivalent of a well-known Windows/Mac program and present it to the world?

> **orphanlast said:**
> This Linux community is really closed off.

Like... I would want to contribute. I would like to make Gimp awesome and I'd like to make Linux easier to use for the average consumer... (like how Linux developers should be doing in the first place). But... I can't even get started.

This is really your expectations at work.. nobody who's new to programming is going to improve GIMP right away. Programming is a skill like any other and it takes time to learn and improve.

---

### Post by rye_ on 2010-04-18
I'm a touched surprised that linux would be your chosen platform for learning VB, a Microsoft language.  Legal issues aside I understand the mono implementation to be something of a work in progress - and very dependant on the whims of M$.

You'll find linux/ unix is usually the development environment for a great number of programming languages, perhaps one of these may be more suitable?
 C/ C++/ D/ java/ python/ perl/ ruby ....I could go on quite a bit here.

A for as learning this stuff, it's not easy and no-one can do it for you. If it appears complicated it's because it is.  Advanced physics is tricky - that's not the fault of the physicists. Learning to program is a subject that takes years to master, certainly I've been learning various bits for years and I'm very amateur.  The best advice is to read/ try/ google.

I hope I wasn't overly negative.

---

### Post by orphanlast on 2010-04-18
> **simeon87 said:**
>  But, if you do not lead, you will forever follow: why not develop a free equivalent of a well-known Windows/Mac program and present it to the world? 

Well, Linux has lead in the "content aware fill" in Gimp, virtual desktops, and a few other things that Microsoft and Apple and other programs seem to be swiping. This is cool because Linux does have some innovation.

People are willing to go to MS Windows and Mac OS because so many programs are interchangeable and it's not a hassle to get those interchangeable programs to start working. With Linux, it's a hassle. You know, it'd be nice to have every program from Mac or Windows work, but I don't think it's unfair to want industry standard programs like Photoshop to work on it without having to research a lot of information. I'm still struggling with that one.

>  This is really your expectations at work.. nobody who's new to programming is going to improve GIMP right away. Programming is a skill like any other and it takes time to learn and improve.I really didn't think that I'd jump right into doing all that, but I might be able to catch some developer's attention by sounding informed and possibly able to make a few suggestions as to how something might be done. I might even find out the right channels to even get in touch with Linux Developers.

> **rye_ said:**
> I'm a touched surprised that linux would be your chosen platform for learning VB, a Microsoft language. 

I had a friend suggest VB. I don't know what he's smoking because he knows I made the switch to Linux. Python sounds like the good starting point. The only downside is that it sounds as though it's strictly for Linux, but I guess everyone has to start somewhere. From what I've seen of the code, it looks easier to grasp... up side is that since it's just for Linux, or at least so it seems, it won't be hard to find tutorials with familiar compilers.

>  ... perhaps one of these may be more suitable?
 C/ C++/ D/ java/ python/ perl/ ruby Oh yeah, I've kinda messed with C/C++ but I think that's trying to bight off more than i can chew, for now.

>  I hope I wasn't overly negative.

Not at all.


And right now I'm looking at [http://fullcirclemagazine.org/](http://fullcirclemagazine.org/) as we speak.

---

### Post by phrostbyte on 2010-04-18
VB.NET support in Mono isn't very good. If you want to do Mono development on Linux I'd use C#. It's not more difficult then VB.NET and arguably it's much more commonly used (VB.NET support isn't as good because of lack of demand), so there is better tutorials.

The way you are talking though, you might want to start with something a little easier to pick up and use and I'd recommend Python for that.

---

### Post by trent.josephsen on 2010-04-18
Python is not just for Linux.  It is written in standard C and can therefore (theoretically) run on any platform with a conforming C compiler (which is most platforms these days, embedded systems excepted).  Python's home page is [http://www.python.org/](http://www.python.org/) .

I answered a similar question earlier this week on another forum.  I advised the poster to study Python and become thoroughly acquainted with it before moving on to something else.  If you are sufficiently educated and motivated, you may be able to make the leap from Python straight to C, which I would recommend for its relative simplicity over C++ or Java.  However, you may want to look into Perl first.  Perl is also a multi-platform language (Windows/Mac/Linux/others) and it is very popular, especially as a glue language on Unix-like systems.

If you are looking for programming books, *Learning Python* is an excellent choice for Python, but I think *Learning Perl* has some stronger merits as an introduction to programming.  (Both books are O'Reilly books.)  You may be tempted to get all your programming knowledge from online tutorials, but I would strongly advise against that.  Anybody can put tutorials on the Internet, and many people do who are not knowledgeable enough to write good ones.  However, the online Python tutorial ([http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)) is quite good, while not really aimed at those new to programming.

In any case, it will take years to achieve real proficiency.  In the meantime, I suggest taking classes if they are available, possibly getting a job at a software shop if it's an option, and always be ready to learn.  I know 4 languages very well and I'm still only a coding peon at an in-house software shop.  Keep your options open and be ready to advance your knowledge at every opportunity.

---

### Post by Jive Turkey on 2010-04-18
Thanks to whoever posted that link to the python tutorial, I stumbled in here looking for just that.

To the OP, VB is not the language you want for programing on linux, and probably not even for windows IMHO.  You shouldn't hesitate to take a class that introduces you to programming with it though.

I'm very inexperienced with programing also, but I think I have a special talent for finding ambiguities in the english language as applied to programing and quickly find myself wondering which of several possible interpretations the author of a given document intended.  Sometimes I even write test code to figure it out by trial and error.

Your efforts will be boosted by a good programing class, as you will be exposed to concepts you may not have known about and you will have access to someone that can answer your questions before you get too frustrated.  Butting your head agianst these deep technical issues will make you want to kick a baby and you won't learn much unless you have some human help along the way.  I've heard of others getting good help on related IRC channels, but never tried it myself.

Also, it sounds like you might not be clear on what a compiler is, you should definitely take a class, in a classroom.

---

### Post by soltanis on 2010-04-18
> **orphanlast said:**
> This is cool because Linux does have some innovation.


I have plenty of friends who show me how cool they are because they turned on multiple desktops on a wall on their Mac. I try to explain to them that I've had desktops on cubes and windows that become transparent for years.

> 
People are willing to go to MS Windows and Mac OS because so many programs are interchangeable and it's not a hassle to get those interchangeable programs to start working. With Linux, it's a hassle.


This is part of the price you pay for going with a minority operating system.

> 
I really didn't think that I'd jump right into doing all that, but I might be able to catch some developer's attention by sounding informed and possibly able to make a few suggestions as to how something might be done.


I hope this doesn't put you off, but most developers do not appreciate that kind of attitude. The entire point of open source is that if you want a feature, you implement it yourself, and share it with the original developer so he can integrate it back into the program, thus contributing back. This is how you make inroads and make friends with the developer community.

Of course, no one expects this from a beginner. Be content with learning for the first few years.

> 
Python sounds like the good starting point. The only downside is that it sounds as though it's strictly for Linux, but I guess everyone has to start somewhere. From what I've seen of the code, it looks easier to grasp... up side is that since it's just for Linux, or at least so it seems, it won't be hard to find tutorials with familiar compilers.


Python is available for Windows, Mac OS X, and Linux, as well as several other systems. It is by no means a Linux-specific language, on the contrary, most of it is highly portable.

By the way, I'd like to point out that a "compiler" is a program that takes human-readable code in a specific programming language and translates it to either native machine code (processor instructions that your CPU directly executes) or some intermediate "byte-code" that another program, called a "virtual machine" or "interpreter" translates into CPU instructions later on. This is different from a "development environment" -- which is what you seem to be referring to, which is where you actually write the code in a friendly editor with specific features that makes writing code easier (like matching parentheses, indenting, line numbering, syntax highlighting...)

If you want to get started in programming, I seriously suggest Python for you, not VB. Why? A lot of programs in Ubuntu (as well as most other Linux distributions) are written in Python, and their sources are good to learn from and make your first contributions back to. Python enforces some specific programming styles on you, and though it is beginner-friendly, it is by no means beginner-only.

---

### Post by madjr on 2010-04-19
i wanted to say that to suggest features/ideas, you dont need to be such an experienced programmer, but you do need to know at least how the program internals work and what would be the best way to implement the feature. to sum it up you need to present your case

ubuntu brainstorm is the place where we discuss many ideas.
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

it's for ubuntu, but you should get the idea

to get an idea approved you may need to convince the community first (which is not always easy).

once the community is convinced, they will actually convince the developers for you or even help you implement/code/test your idea.

open source is a bit like a democracy since the community is the target, but the devs have the final word, since they will be doing all the work (for free) and they know best what they can and cant do

sometimes they're so busy/overwhelmed implementing important features that they may not even have time to check new suggestions at the moment.

anyway keep it up and remember that knowledge and persistency is power

---

### Post by CptPicard on 2010-04-19
> **orphanlast said:**
> Well, Linux has lead in the "content aware fill" in Gimp, virtual desktops, and a few other things that Microsoft and Apple and other programs seem to be swiping. This is cool because Linux does have some innovation.

You must be new to computing. Microsoft has caught up decently in the last decade or so, but for example, Windows of the 90s was dismally bad in all regards except market penetration. Linux was a very sound OS relatively quickly since its inception -- speaking of the under the hood stuff here which really counts... where it has come has been nothing short of miraculous.

I don't particularly care much about the end-user bells and whistles. Those can be coded by those who want to, the possibilities are there.

>  You know, it'd be nice to have every program from Mac or Windows work, but I don't think it's unfair to want industry standard programs like Photoshop to work on it without having to research a lot of information.

It's incredibly unfair. Please study the differences between different operating systems before making such statements. Binary formats are different, standard libraries are different, system calls are different, GUI widget toolkits are different...

> 
I really didn't think that I'd jump right into doing all that, but I might be able to catch some developer's attention by sounding informed and possibly able to make a few suggestions as to how something might be done.

Hmmh... I'm getting the impression you would "sound informed", but wouldn't be, and would be telling them what to do, while not understanding how to do it, and expecting them to do it. A great way to **** off a volunteer developer :)

> 
 I might even find out the right channels to even get in touch with Linux Developers.

Try the Linux Kernel Mailing List. Don't forget the asbestos underwear.

> The only downside is that it sounds as though it's strictly for Linux

No, it's not.

---

### Post by madjr on 2010-04-19
hey @orphanlast

here are more resources for you on your quest to learning python


python is the **new basic**:
[http://inventwithpython.com/](http://inventwithpython.com/)
*note: python is already installed by default*


**pyjunior** to be released by jonobacon:
[http://www.jonobacon.org/2010/04/08/making-programming-easier-for-kids-with-pyjunior/](http://www.jonobacon.org/2010/04/08/making-programming-easier-for-kids-with-pyjunior/)
[http://www.jonobacon.org/2010/04/08/pyjunior-call-for-documentation-help/](http://www.jonobacon.org/2010/04/08/pyjunior-call-for-documentation-help/)
*note: he's the ubuntu community chief :)*

Snake Wrangling for Kids
[http://www.briggs.net.nz/log/writing/snake-wrangling-for-kids/](http://www.briggs.net.nz/log/writing/snake-wrangling-for-kids/)


Programmer-style **logic and abstract** **thinking** game (similar to robocode/robomind, but a little simpler)
[http://armorgames.com/play/2205/light-bot](http://armorgames.com/play/2205/light-bot)
[http://www.kongregate.com/games/Coolio_Niato/light-bot](http://www.kongregate.com/games/Coolio_Niato/light-bot)
*note: programming is similar to this puzzle (step by step process), but more advanced and in writing. You may want to move to robocode/mind when you're done with this one.*

and like others said free ubuntu fullcircle mag (my signature)

---

### Post by medic2000 on 2010-04-19
Forget that Visual Basic crap and start programming with Python. It is very easy and powerful language. But the easiness or hardness of the language is not the problem as they said above. It is the programming logic you have to understand first. And for this 2 great source. Trust me they are great:

First: [http://rur-ple.sourceforge.net/](http://rur-ple.sourceforge.net/)download it from the site)
Second: How to think like a computer scientist: 
[http://openbookproject.net/thinkCSpy/index.html](http://openbookproject.net/thinkCSpy/index.html)

These two are explaning everything step by step. Be patient. It is a long way. 

For the GNU/Linux platform. You can run proprietary programs too. But what can we do if Adobe does not release Photoshop for us? And for an voluntary project GIMP is just behind the Photoshop and for free.

For a side note: I have been using Linux since 3 years and now doing things in Windows is very very hard and uncomfortable for me...

---

### Post by raydeen on 2010-04-19
+1 for Python.

Once you get started I think you'll find Python easy to learn. Mastering it is another story as it's capable of some pretty powerful stuff when used properly but that comes with time and experience. What's really nice about it is that it's EVERYWHERE! Nasa, Google, YouTube, BitTorrent, some of the major financial institutions... Guaranteed, you've touched something that was coded in Python at least once a day. And what you code in one platform will run in any other platform that has Python installed. There are different versions of it right now. The best bet is to get into Python 2.6 or 3.x. Most would recommend 2.6 as it's a bridge between the old and new (3.x being the new). Most recent books (4 years old or newer) will more than likely cover both 2.x and 3.x. Once you get into it, you'll find yourself writing little scripts to save you time and sanity. I wrote one the other day to generate .csv files for creating Google Group accounts based on our organization's account criteria. Took an hour or two but it saves a lot of copying and pasting in Excel when I get 30 or more email accounts that need to be created. :)

---

### Post by orphanlast on 2010-04-19
Wow, thanks everyone.

---

### Post by medic2000 on 2010-04-20
> **orphanlast said:**
> Wow, thanks everyone.

You are welcome. Hehe by the way i think you have just sipped a little from the cup of helpfulness of the free software community :) It is lightning fast :)

---

### Post by conradin on 2010-04-20
LOLZ, Yeah there is a learning curve to anything new you try. The beauty of VB isnt that its portable, but that you draw a picture of a program and youre done. BTW, I have made VB6.0 work under wine although, it is buggy. Web design is pretty simple. If you want to learn programing, you should ask yourself what you want to do with the programs you write. Me, I do network / hardware. So I started with C, C++, assembly, then html, and onward.. 

Check out QT for visual front end designers for C++.

If you want to do web pages, start simple with html [www.w3schools.com](www.w3schools.com), then maybe move to java, sql, asp, or php. 

Maybe scripting is better fit for what you want to do, aim at server back ends. Then maybe perl. 

maybe science and research, perhaps Fortran, or python or R. 

This site has plenty of tutorials, and interesting things to do. 
[http://www.codeproject.com/](http://www.codeproject.com/)

Gambas was all in spanish last time I looked at it, though ive heard its been improoved. There was a project called phoenix or something like that, that was a VB-esque IDE.  

Theres thousands of languages these days, choose one that meets your needs. No one programs webpages in assembly.

---

### Post by slavik on 2010-04-21
> **conradin said:**
> LOLZ, Yeah there is a learning curve to anything new you try. The beauty of VB isnt that its portable, but that you draw a picture of a program and youre done. BTW, I have made VB6.0 work under wine although, it is buggy. Web design is pretty simple. If you want to learn programing, you should ask yourself what you want to do with the programs you write. Me, I do network / hardware. So I started with C, C++, assembly, then html, and onward.. 

Check out QT for visual front end designers for C++.

If you want to do web pages, start simple with html [www.w3schools.com](www.w3schools.com), then maybe move to java, sql, asp, or php. 

Maybe scripting is better fit for what you want to do, aim at server back ends. Then maybe perl. 

maybe science and research, perhaps Fortran, or python or R. 

This site has plenty of tutorials, and interesting things to do. 
[http://www.codeproject.com/](http://www.codeproject.com/)

Gambas was all in spanish last time I looked at it, though ive heard its been improoved. There was a project called phoenix or something like that, that was a VB-esque IDE.  

Theres thousands of languages these days, choose one that meets your needs. No one programs webpages in assembly.
vb6 is as portable as the ENIAC ...

---

### Post by madjr on 2010-04-21
yea i would say

python or

dynamic webpages (html + **php + mysql**)


is the easiest way to go and both skills are extremely useful

---

### Post by nvteighen on 2010-04-21
> **conradin said:**
> The beauty of VB isnt that its portable, but that you draw a picture of a program and youre done.

Er... That's the **problem** with VB: That it encourages an upside-down way to program that has nothing to do with top-down programming although they sell it that way to you... 

And as slavik said, VB is not precisely portable... even between different versions of Windows. (There were issues installing VB 4.0/5.0 projects in Win98, because you were supposed to use VB 6.0 by that time... There were several DLL conflicts related to, e.g. CommonDialog)

> 
Check out QT for visual front end designers for C++.


Qt is a GUI toolkit, a framework, not a visual front end designer... There are GUI designers based on Qt that help you to use Qt in your programs.

---

### Post by kalaharix on 2010-04-22
Hi

Well, I must admit it is a bit of a joke to describe VB as portable. I am not sure, however, that it is much different with the majority of Linux programming environments which rely, as they do, on external libraries which themselves are subject to development. I have often thought of this as the Achilles heel in Linux. Is nvteighen quite sure there will not be problems for legacy software when going from py2 to py3 or when one of the included libraries changes?

Linux users continually bemoan the lack of acceptance of Linux and yet we seem all too ready to sneer at attempts to broaden that appeal. The separation of logic (say Python) from visual design (say Glade) may suit some. It does not suit me. It is analogous to designing the engineering of a car and then handing the bare product to the design department. This may have worked with a 1965 Chevy Impala (or may not depending on your viewpoint :)) but a glimpse under the bonnet/hood of a finely-crafted 2010 Merc saloon will tell you that modern engineering design involves the simultaneous application of both engineering and aesthetics. Why should software be any different?

I think Gambas is a great product. I sometimes think it is a Linux secret weapon. For every one programmer happy to footle with Glade or C, there are a thousand who would program with an competent programming language integrated with a half-decent gui. The logic side of Python and Gambas are very similar (as nvteighen suggests). I often wonder why nobody has developed a gui IDE for Python but suspect that if someone did do one half as good as the Gambas IDE then it would be so slow as to be unusable.

I also wonder at the automatic rejection of anything BASIC in this forum. It is normally accompanied by a surprising level of ignorance. I suspect that it is just a macho thing: "Oh! The B stands for Beginner. I'm not a beginner therefore it is beneath me." I came upon another analogy. We've all met him/her and they all go something like this:

"Linux? Nah, it's crap. It's only for geeks. How are you going to cope without Word? You know it doesn't even run Facebook. Nah, stick to Windows. They are the professionals."

---

### Post by trent.josephsen on 2010-04-22
Python is several orders of magnitude more sophisticated and cleaner than VB, and it enforces programming habits that become very valuable in other languages.  Not so at all with Visual Basic.

I didn't really understand the car analogy.  But I do use a GUI IDE for Python.  It has a nice visual layout, customizable menus, custom autocomplete, built-in make command, customizable syntax highlighting, features for Python as well as Java, LaTex, XML, C, C++, and more, and a selection of keyboard shortcuts second to none.  [Maybe you've heard of it]("http://www.vim.org").

I don't think the rejection of VB was "automatic".  I was surprised by how long it took for someone to say "ditch that crap", at least compared to some other message boards I frequent.  In any case, I have used VB and I wouldn't reject it offhand; it has its uses.  But I wouldn't recommend it for a beginner for a variety of reasons, and the IDE is not one of them.

---

### Post by kalaharix on 2010-04-22
Hi

'Python is several orders of magnitude more sophisticated and cleaner than VB' 

Yes, so is Gambas: it comes with age.:)

Vim is a text editor. Period. Can I use a mouse to drag a text box across a form with Vim? 

I really get annoyed when people say 'Gambas is rubbish because QuickBasic 4.5 was rubbish' so I suspect I'll annoy you by saying that Vim is rubbish because the vi I was was using 30 years ago was rubbish. It sure was.

---

### Post by medic2000 on 2010-04-22
Hey ho flames down! No flame war here please!

---

### Post by trent.josephsen on 2010-04-22
> **kalaharix said:**
> Hi

'Python is several orders of magnitude more sophisticated and cleaner than VB' 

Yes, so is Gambas: it comes with age.:)

I don't want to get involved in a flame war, but I'm truly confused by this statement.  Gambas is younger than VB, which is as far as I can tell about the same age as Python (both emerged in 1991).  Care to explain?  Or are you talking about VB.NET?

---

### Post by kalaharix on 2010-04-23
Hi

Medic2000: you are right. Not my intention but I did get a bit 'combative' there. Apologies to forum and trent.

I guess what I meant was that the Merc is a better car than the Chevy. Even though there is no lineage, it has built on that automotive history.

Gambas too, is stratigraphically above VB and has built on that heritage. It's concept of oo shares a lot with Java as well though. It's just a more modern piece of software.

---

### Post by eaglemob on 2010-04-23
Wow very nice thread !!
I have some comments to make.
First of all my first computer was a Zx spectrum 48k,back on the 80's.
After it i change to an Amiga, then as you all know commodore died.

Then had to change to pc.. of course after came windows 3.1, if i am not wrong. Since then started the problems with the virus and *Please wait windows is loading*. It takes ages just waiting to load. Each time we install a program on windows, we need to restart the ****** computer.

About programming:
Atm a friend of me is programing a kind of ripper gui that does everything for you with one press of a bottom. You just insert the dvd and makes a scan, it will ripp the main with the audio/sub titles. To the formats:avi, divx, xvid, mpeg4, mkv. 
All that automatic you just need to type in what language sub title you want to be converter to .srt, audio bitrate and how long the movie is in minutes. Then relax, go to the pub or make some programming during that process.
Ho btw he is using GAMBAS, he used VB on windows but since 2-3 years ago we don't use windows anymore.
Well i used linux on terminal wen i had my Amiga i use to run a MUD , but that was long time ago.

Myself i just use windows to play world of warcraft because linux doesn't have directx. And i don't think Blizzard is planing to support linux operating systems.
Anyway tested to play W.o.W via WINE and it works but i loose some speed.

Yesterday i upgraded from 9.10 to Lucid 10.04. But i notice that i had 9.10 32bits, so i had 3GB ram to short 10.04 was upgraded to 32 bits :) hehe my fault.

So today i installed again a version Ubuntu Lucid 64 bits. It took me about 2 hours including download,burning, setting up, installing libs ...etc. In other words *Everything works perfect*. All the hardware installed with no complain or errors. And i didn't need to insert any dvd/cd with drivers ..long live linux!!!

Next step, i am building together a system that will be a good test to Ubuntu vs windows.
Configuration:
i7 975 extreme edition,Mb GA-X58A-UD3R,2X 1000MB(1TB) S-ATA II*JPK,
HIS ATI Radeon HD5870 1024 Mb PCI-E, Coolmaster V8 Cooler for the Cpu,
LG Blu-Ray burner 8X,OZC 6GB ddr3 (that maybe will change for 12Xddr3 at 1800mhz),
Zalman Power Supply 750w Silence Psu, a mouse,a keyboard and a monitor :).
We will see how good Ubuntu is.  

Windows: flash player on 64bits hmm hugabuga, virus a lot, free programs don't exist, slow, etc..etc..

IMO if you want to be a programmer, then the best choice is any linux Os.
Ppl just use windows to play games, the rest on windows is JUST CRAP.

How deep you get in on linux how more you will discover how good linux is.
Each time that comes a linux update/upgrade is getting better and better.
Windows is getting more and more behind.
No one will make me change from Ubuntu to windows.
That is my opinion.

Further information, ideas or help (if i can), i will posted.

Good luck with your programing.

Ps. tell me wen you have made something :)

Grtx

---


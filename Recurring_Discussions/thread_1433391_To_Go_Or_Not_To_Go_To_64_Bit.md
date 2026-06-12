---
title: "To Go Or Not To Go To 64 Bit"
date: 2010-03-19
forum: Recurring Discussions
---

### Post by Khakilang on 2010-03-19
I have read the x86 64 bit thread but I am between 32 bit and 64 bit Linux. My computer spec is Dual Core 1.8GHz, 1.5GB RAM, 80GB hard disk and nVidia 7200GS graphic card. Look like the hardware can go 64 bit but I don't know about the software part. Is it still in its infant stage, are there many software that run on 64 bit, is it perform better than 32 bit, is my hardware good enough for 64 bit etc...?

What do you guys think? Many those who use 64 bit OS can share with me.:frown:

---

### Post by swoll1980 on 2010-03-19
I have Ubuntu 64 I think every piece of software on it is 64 bit if I'm not mistaken. The stuff in the repos are too I think.

---

### Post by Psumi on 2010-03-19
> **swoll1980 said:**
> I have Ubuntu 64 I think every piece of software on it is 64 bit if I'm not mistaken. The stuff in the repos are too I think.

flash is in the repos, but it isn't 64-bit.

It uses ia32-libs.

Java is the same from the ubuntu repos.

To get 64-bits of these, you need to do special things.

---

### Post by swoll1980 on 2010-03-19
I think foss is alot more 64 bit friendly than the other stuff.

---

### Post by Psumi on 2010-03-19
> **swoll1980 said:**
> I think foss is alot more 64 bit friendly than the other stuff.

On some drivers too, you need to use --force-architecture on the dpkg in terminal.

IE: Canon PIXMA MP190.

---

### Post by themarker0 on 2010-03-19
You know whats weird? I've never found a difference running 64bit to 32. Just how ram i can use. (Haven't tried on linux)

---

### Post by swoll1980 on 2010-03-19
> **themarker0 said:**
> You know whats weird? I've never found a difference running 64bit to 32. Just how ram i can use. (Haven't tried on linux)
We just had a discussion about this on the other thread. People are going to think your my other user account, and I'm just posting that to agree with myself. ;)

---

### Post by themarker0 on 2010-03-19
> **swoll1980 said:**
> We just had a discussion about this on the other thread. People are going to think your my other user account, and I'm just posting that to agree with myself. ;)

I actually didn't see that thread lol. Well i don't have a system that is 64 bit and linux compadible, so i can never test 64 *nix. Only windows. I've never had a broken app, because its mostly games.

---

### Post by 3rdalbum on 2010-03-19
Linux software is written to work on every different CPU architecture from ARM to SPARC to Itanium to M68K, including of course x86 and x86_64.

Some proprietary software has only been made for 32-bit, but you can usually get the 32-bit libraries and run it on 64-bit.

---

### Post by cascade9 on 2010-03-19
You migth as wel go 64bit, provided that your hardware supports it. You could have issues with some things that only have 32bit version (pretty rare now) but like Psumi posted you can use the --force-architecture switch on terminal and proetty much all of them should work. 

For all the standard programs though you shouldnt have any issues. 

> **Koh Kook Loon said:**
> I have read the x86 64 bit thread but I am between 32 bit and 64 bit Linux. My computer spec is Dual Core 1.8GHz, 1.5GB RAM, 80GB hard disk and nVidia 7200GS graphic card. Look like the hardware can go 64 bit but I don't know about the software part. Is it still in its infant stage, are there many software that run on 64 bit, is it perform better than 32 bit, is my hardware good enough for 64 bit etc...?

What do you guys think? Many those who use 64 bit OS can share with me.:frown:

Depends on the dual-core. They arent all 64 bit, but sounds like you have a Core2Duo, they are 64 bit capable. Core Duo isnt. Annoying isnt tit? Virtually the same name, but different capabilities.

> **Psumi said:**
> flash is in the repos, but it isn't 64-bit.

It uses ia32-libs.

Java is the same from the ubuntu repos.

To get 64-bits of these, you need to do special things.

Not that hard to do with flash (I've never bothed with java). There is even a script to do it with ubuntu- 

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

I dont do it that way, I just go to adobe, d/l the 64 bit version , unzip it then move the unzipped 'libflashplayer.so' to /usr/lib/mozilla/plugins (this can also work with other browsers) Adobe 64bit page here-

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by Paqman on 2010-03-19
I've been using 64-bit for years. There used to be some software that was a mild pain, but these days its absolutely the way to go. I don't see any point running 32-bit on a 64-bit chip.

---

### Post by J_Stanton on 2010-03-19
> **Koh Kook Loon said:**
> Is it still in its infant stage, are there many software that run on 64 bit, no it is not in the infant stage by any means. 64bit runs at least as well as 32 did, only a bit faster and seemingly more stable. i have yet to see an app that is not available in 64. let's put it this way, i will not use a 32bit os ever again, given the choice.

---

### Post by Psumi on 2010-03-19
> **J_Stanton said:**
> no it is not in the infant stage by any means. 64bit runs at least as well as 32 did, only a bit faster and seemingly more stable. i have yet to see an app that is not available in 64. let's put it this way, i will not use a 32bit os ever again, given the choice.

Most MMORPGs are not 64-bit.

WINE is NOT 64-bit.

---

### Post by J_Stanton on 2010-03-19
> **Psumi said:**
> Most MMORPGs are not 64-bit.

WINE is NOT 64-bit.

i don't play games, so i don't know, but i'm using wine right now so you're mistaken about that. any MMORPGs in the repos will be 64bit of course. i myself have not noticed any difference in the repos.

---

### Post by Psumi on 2010-03-19
> **J_Stanton said:**
> but i'm using wine right now so you're mistaken about that.

[http://packages.ubuntu.com/karmic/wine](http://packages.ubuntu.com/karmic/wine)

See ia32-libs

---

### Post by luctor on 2010-03-19
> **Paqman said:**
> I've been using 64-bit for years. There used to be some software that was a mild pain, but these days its absolutely the way to go. I don't see any point running 32-bit on a 64-bit chip.

Couldn't agree more with you.

---

### Post by J_Stanton on 2010-03-19
> **Psumi said:**
> [http://packages.ubuntu.com/karmic/wine](http://packages.ubuntu.com/karmic/wine)

See ia32-libs

all i know is that i can use it and it works. nit-picking is pointless. 99.9% of apps are ported over to 64bit. and the rare app that is not will work anyway.

---

### Post by Psumi on 2010-03-19
> **J_Stanton said:**
> all i know is that i can use it and it works. nit-picking is pointless. 99.9% of apps are ported over to 64bit. and the rare app that is not will work anyway.

ia32-libs makes it possible so that 86 apps can run on amd64 (much like SysWOW64<>System32 on Windows.)

Meaning it's not 64-bit.

---

### Post by J_Stanton on 2010-03-19
actually, after looking at the website:    *  karmic (otherosfs): Microsoft Windows Compatibility Layer (Binary Emulator and Library) [universe]       1.0.1-0ubuntu8: amd64 i386       also provided by: wine1.2 it clearly shows amd64 AND i386 try again

---

### Post by Psumi on 2010-03-19
> **J_Stanton said:**
> actually, after looking at the website:    *  karmic (otherosfs): Microsoft Windows Compatibility Layer (Binary Emulator and Library) [universe]       1.0.1-0ubuntu8: amd64 i386       also provided by: wine1.2 it clearly shows amd64 AND i386 try again

[http://packages.ubuntu.com/karmic/wine1.2](http://packages.ubuntu.com/karmic/wine1.2)

See ia32-libs.

Also this: [http://wiki.winehq.org/Wine64](http://wiki.winehq.org/Wine64)

Wine is NOT 64-bit on 64-bit. it is merely i386 using a wrapper to talk to the 64-bit os.

You can compile 64-bit wine for use on 64-bit OS... but you should really read what it says there on their wiki.

---

### Post by cascade9 on 2010-03-19
Ohh, wow, WINE is only 32bit (unless you want the development version). Quell suprise. 

Its splitting hairs anyway, as what Jstanton said was " have yet to see an app that is not available in 64." 

WINE might be 32 bit, but it runs on 64bit (which was what I think J_Stanton was driving at)  and besides that there is far less 64 bit software on windows compared to linux anyway.

---

### Post by Psumi on 2010-03-19
> **cascade9 said:**
> Ohh, wow, WINE is only 32bit (unless you want the development version). Quell suprise. 

Its splitting hairs anyway, as what Jstanton said was " have yet to see an app that is not available in 64." 

WINE might be 32 bit, but it runs on 64bit (which was what I think J_Stanton was driving at)  and besides that there is far less 64 bit software on windows compared to linux anyway.

Then he should've worded it better:

"...have yet to see an application that does not work on 64."

---

### Post by Jarmen_Deffs on 2010-03-19
> **swoll1980 said:**
> We just had a discussion about this on the other thread. People are going to think your my other user account, and I'm just posting that to agree with myself. ;)

:p

---

### Post by ndefontenay on 2010-03-19
I'm planning to re-install in 64bit too. 
I was wondering the same. It seems that all that is required to install a 32bit on a 64bit is to user force architecture.

It's time to do the jump I believe. Required if I want to use those extra 4GB sleeping in my hardware anyway.

---

### Post by d3v1150m471c on 2010-03-19
It's not much better for the trouble it currently entails. I'd wait a year or so on 64 bit.

---

### Post by Penguin Guy on 2010-03-19
> **themarker0 said:**
> You know whats weird? I've never found a difference running 64bit to 32.
+1: I have ran both 64-bit and 32-bit and couldn't see any difference at all.

---

### Post by kelvin spratt on 2010-03-19
> **d3v1150m471c said:**
> It's not much better for the trouble it currently entails. I'd wait a year or so on 64 bit.
And what trouble would that be.
Download 64bit version install wow thats extra trouble?

---

### Post by 3rdalbum on 2010-03-19
It doesn't matter that Wine is not 64-bit. The programs it will be running are usually 32-bit anyway, so it's not like having the extra address space and longer numbers will help anything.

---

### Post by cartman640 on 2010-03-19
Definitely go 64bit, been running it for years on various systems, and all I've noticed is more speed, the ability to use all 8Gb of my RAM and more stability.

> **d3v1150m471c said:**
> It's not much better for the trouble it currently entails. I'd wait a year or so on 64 bit.
64bit desktop class CPU's have been out for 7 years, and 64bit OS's even longer, pretty sure the benefits outweigh those elusive troubles that I'm yet to find.

---

### Post by madjr on 2010-03-19
people get mixed results

32 is the safe choice

download both isos and install them both, if 64 works better for u then go for it

---

### Post by hessiess on 2010-03-19
Use 64 bit, the AMD64 architecture is better than X86 in other ways besides the ability to address larder numbers (more registers for one thing).

---

### Post by smartinjose on 2010-03-19
I have heard that we can run 32 bit applications on 64 bit PC. But I am not sure its the same with Ubuntu and other Linux OS.

---

### Post by BrokenKingpin on 2010-03-19
I have been using 64-bit for years, with no issues (specific to 64-bit anyways). Anyone with a 64-bit machine should be moving to 64-bit software.

---

### Post by chris200x9 on 2010-03-19
do you watch hulu? It doesn't work on 64 bit because of the flash plugin.

---

### Post by _h_ on 2010-03-19
If your hardware can support 64bit, why not use it to it's full potential and go 64bit?

---

### Post by james_xxx on 2010-03-19
chris200x9,

I watch Hulu both through browsers and through the Hulu Desktop app all the time, on a few different 64-bit machines.

I am still using 32-bit Adobe Flash, however.

---

### Post by JDShu on 2010-03-19
64bit still requires more hoop jumping. Its possible, but more of a headache. Flash 32 bit is better supported and ubuntuzilla works only with 32bit - so that means less headache upgrading firefox. On the other hand, if you do alot of rendering stuff - video editing or 3D modelling, 64bit has a huge speed increase from 32bit.

---

### Post by samalex on 2010-03-19
> **Koh Kook Loon said:**
> I have read the x86 64 bit thread but I am between 32 bit and 64 bit Linux. My computer spec is Dual Core 1.8GHz, 1.5GB RAM, 80GB hard disk and nVidia 7200GS graphic card. Look like the hardware can go 64 bit but I don't know about the software part. Is it still in its infant stage, are there many software that run on 64 bit, is it perform better than 32 bit, is my hardware good enough for 64 bit etc...?

What do you guys think? Many those who use 64 bit OS can share with me.:frown:

I say go for it!  Unless you need to compile lots of third party apps from source you probably won't run into any problems.  The only thing I would recommend is removing 32-bit Flash which comes with 64-bit Ubuntu (plus remove the wrapper) and download the latest Alpha copy of 64-bit Flash from Adobe.  It's still alittle buggy, but honestly it works MUCH better then the 32-bit version+wrapper.  Plus using the 64-bit version you'll have webcam support and support for all sorts of other things the 32-bit version+wrapper just can't handle.

Sam

---

### Post by Psumi on 2010-03-19
> **hessiess said:**
> Use 64 bit, the AMD64 architecture is better than X86 in other ways besides the ability to address larder numbers (more registers for one thing).

And remember that ia* is different than x86-64/amd64/x86.

---

### Post by Penguin Guy on 2010-03-19
32-bit programs will run on 64-bit computers, just not as fast as 64-bit programs.

---

### Post by cascade9 on 2010-03-19
> **Psumi said:**
> And remember that ia* is different than x86-64/amd64/x86.

IA* is a complete misnomer. IA-64 is itanium, so its not x86 compible at all.....but IA-32 is i386, which sure is x86.

---

### Post by oldos2er on 2010-03-19
> **chris200x9 said:**
> do you watch hulu? It doesn't work on 64 bit because of the flash plugin.

Hulu desktop works great here with 64-bit flash.

---

### Post by wjm on 2010-03-19
64-bit Lucid here, working amazingly fast and no flash problems what-so-ever.  If you're holding off on 64-bit, I'd wait till Lucid.  I'm extremely impressed with it here.

---

### Post by fela on 2010-03-19
Yes of course you should use 64 bit.

Next question.

HTH

---

### Post by gymophett on 2010-03-19
I use Ubuntu 9.10 64-bit and Windows 7 64-bit.

Everything works exactly the same, and I've had no problems.

---

### Post by _h_ on 2010-03-19
> **wjm said:**
> 64-bit Lucid here, working amazingly fast and no flash problems what-so-ever. If you're holding off on 64-bit, I'd wait till Lucid. I'm extremely impressed with it here.
 
You aren't the only one impressed. :P

---

### Post by wojox on 2010-03-19
> **chris200x9 said:**
> do you watch hulu? It doesn't work on 64 bit because of the flash plugin.

It works on 64 bit. If your talking about Hulu Desktop you just need to edit your hulu.desktop file to tell it where the driver is. ;)

---

### Post by Swagman on 2010-03-19
> **gymophett said:**
> I use Ubuntu 9.10 64-bit and Windows 7 64-bit.

Everything works exactly the same, and I've had no problems.

Have you tried the Amazon mp3 .deb downloader on 64 bit ?

---

### Post by HappinessNow on 2010-03-19
You know what they say?

"Once you go 64bit you never back" LOL :p

Go...I've used it for years.

---

### Post by oldos2er on 2010-03-19
> **Swagman said:**
> Have you tried the Amazon mp3 .deb downloader on 64 bit ?

I was never able to get amazonpm3 downloader to work on 64-bit. But clamz (google code) works just fine.

---

### Post by Swagman on 2010-03-19
Indeed.

Well, I was pondering whether to go 64 bit when I clean install Lucid so I just did a dummy run with a 16gb USB stick and 9:10 64 bit


Result

[ **Phail No.1**](http://www.upload3r.com/serve/190310/1269035206.png)

[** Phail No.2**]( http://www.upload3r.com/serve/190310/1269035335.png)

Sod it. Staying 32 bit

Ok I freely admit I probably did the flash thing wrong but... there ya go.

---

### Post by Jarmen_Deffs on 2010-03-19
> **Swagman said:**
> Indeed.

Well, I was pondering whether to go 64 bit when I clean install Lucid so I just did a dummy run with a 16gb USB stick and 9:10 64 bit


Result

[ **Phail No.1**]("http://www.upload3r.com/serve/190310/1269035206.png")

[** Phail No.2**]("http://www.upload3r.com/serve/190310/1269035335.png")

Sod it. Staying 32 bit

Ok I freely admit I probably did the flash thing wrong but... there ya go.

Definitely did flash wrong, and [getlibs]("http://ubuntuforums.org/showthread.php?t=474790") will fix amazon for you.

---

### Post by Psumi on 2010-03-19
> **Jarmen_Deffs said:**
> Definitely did flash wrong

Yes, flash was done wrong... but can you blame the person?

1. Adobe's Website doesn't auto-detect the arch type on your machine, it makes you download i386.

2. The "select system/OS" dropdown doesn't have 64-bit.

3. The System Requirements Page doesn't provide a 64-bit link profusely anywhere so that the average human would notice it.

4. This page neither: [http://www.adobe.com/products/flashplayer/productinfo/instructions/](http://www.adobe.com/products/flashplayer/productinfo/instructions/)

5. neither this one: [http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

Doing it wrong is what the average human would do.

---

### Post by JDShu on 2010-03-19
I agree with Psumi.

---

### Post by Jarmen_Deffs on 2010-03-19
> **Psumi said:**
> Yes, flash was done wrong... but can you blame the person?

1. Adobe's Website doesn't auto-detect the arch type on your machine, it makes you download i386.

2. The "select system/OS" dropdown doesn't have 64-bit.

3. The System Requirements Page doesn't provide a 64-bit link profusely anywhere so that the average human would notice it.

4. This page neither: [http://www.adobe.com/products/flashplayer/productinfo/instructions/](http://www.adobe.com/products/flashplayer/productinfo/instructions/)

5. neither this one: [http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

Doing it wrong is what the average human would do.

Take it easy.  
I'm not blaming him, or passing judgement.  Just confirming what he already suspected.

---

### Post by oldos2er on 2010-03-19
You can try carlee's script: [http://ubuntuforums.org/showthread.php?t=1414595](http://ubuntuforums.org/showthread.php?t=1414595)

---

### Post by madhi19 on 2010-03-20
> **Penguin Guy said:**
> +1: I have ran both 64-bit and 32-bit and couldn't see any difference at all.

If you want to use more than 4GB of Ram you got to run a 64-bit OS! THAT one hell of a big difference in my book!

---

### Post by Khakilang on 2010-03-20
Well Ladies and gentlemen thank you for all your reply. I took the plunge to not only go for 64 bit Ubuntu but wipe out my Window XP and replace it on my main computer,  I currently download most of the updates and driver and everything work fine so far. keeping my finger cross that nothing will happen. 

Anyway I download Adobe flash using my Ubuntu Software centre. I don't care whether its a 32 bit or 64 bit as long as it work. Once again thanks!:popcorn:

---

### Post by Psumi on 2010-03-20
> **madhi19 said:**
> If you want to use more than 4GB of Ram you got to run a 64-bit OS! THAT one hell of a big difference in my book!

[*cough* PAE *cough*]("http://en.wikipedia.org/wiki/Physical_Address_Extension")

---

### Post by FuturePilot on 2010-03-20
> **Psumi said:**
> [*cough* PAE *cough*]("http://en.wikipedia.org/wiki/Physical_Address_Extension")

PAE is a dirty hack.

---

### Post by Jarmen_Deffs on 2010-03-20
> **FuturePilot said:**
> PAE is a dirty hack.

Yes, if you have 64 bit hardware just use a 64 bit OS and avoid the extra page table lookups.

---

### Post by 3rdalbum on 2010-03-20
> **Swagman said:**
> Indeed.

Well, I was pondering whether to go 64 bit when I clean install Lucid so I just did a dummy run with a 16gb USB stick and 9:10 64 bit


Result

[ **Phail No.1**](http://www.upload3r.com/serve/190310/1269035206.png)

[** Phail No.2**]( http://www.upload3r.com/serve/190310/1269035335.png)

Sod it. Staying 32 bit

You don't need the downloader in order to download from Amazon. And, as you acknowledge, you need to use the 64-bit plugin from the Sevenmachines PPA or from the Adobe website.

If it only took you two issues to refuse to switch to 64-bit (the ONLY two issues, I might add), it's a wonder you ever switched to Ubuntu in the first place. Windows to Ubuntu requires much more learning than 32-bit to 64-bit.

---

### Post by Swagman on 2010-03-20
> **3rdalbum said:**
> You don't need the downloader in order to download from Amazon. And, as you acknowledge, you need to use the 64-bit plugin from the Sevenmachines PPA or from the Adobe website.

If it only took you two issues to refuse to switch to 64-bit (the ONLY two issues, I might add), it's a wonder you ever switched to Ubuntu in the first place. Windows to Ubuntu requires much more learning than 32-bit to 64-bit.

I was Debian 64 with an Ati X800 card before switching to Ubuntu NOT windows.

I got sick of 3 days googling to get stuff to work and so changed to Ubuntu. Now it's only 1 day googling !!

lol

btw.. I ran Debian 64 for about a year and when I changed to Ubuntu i386 I never noticed one iota of difference - speed wise. I have 2gb ram and that's way more than I actually need.

---

### Post by gypaete09 on 2010-06-05
I'd say try it, you will not regret it.

I run Lucid AMD 64 on two machines now, and except for sometimes having to install from source, I haven't had any major issues. It depends on which apps you use most, which apps you really *need*.
My aging 1.8GHz machine races like a new box for years now.

I use Linux on my one and-only PC for my company, plus Virtualbox for the few apps I can't get other than for Windows.

---


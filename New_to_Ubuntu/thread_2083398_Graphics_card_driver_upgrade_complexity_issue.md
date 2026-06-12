---
title: "Graphics card driver upgrade complexity issue"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by deadscion on 2012-11-12
First of all, I have always been impressed with the extreme reliability of Ubuntu, but because the graphics driver install and adjustments are always difficult to perform without considerable research, I have had a tendency to stay with Windows O.S.

So after following Ubuntu progress and trying it out for years, I only recently started using it on a steady basis.

My question is:
Why, after all these years, is the issue of graphics card drivers install, upgrade and adjustment still a complex issue? 

Why haven't you taken the thousands of complaints in askubuntu.com into consideration and set up something the beginner can handle? 

I don't want to hear about all the available information on how to fix this or that. 

I want to know what you are going to do about all those complaints. 

I believe this issue to be the biggest obstacle preventing many Windows users from converting to Linux. 
Especially when it is so easy for a beginner to make a mistake which cripples the entire operating system, leaving a new user extremely frustrated, running back to Microcrap Windows.

---

### Post by QIII on 2012-11-12
The open source community has developed open source drivers.  They are getting better as the developers can peer into the poorly lit workings of proprietary hardware.  That is what the open source community has control over.

The open source community has no control over proprietary drivers.  That proprietary drivers are more difficult is something for the OEMs to address.

Still, those drivers are not so hard to install any more.

By the way, the "we" here on this forum are generally not developers nor employees of Canonical.

---

### Post by Cheesemill on 2012-11-12
Please bear in mind that this is a community forum, the Ubuntu developers don't read it.
'We' have nothing to do with the development of Ubuntu.

If you would like to file a bug report the correct place to do this is at [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

Also I've never had a problem with my Nvidia cards on Ubuntu, after installation the system prompts me to install the correct drivers which it does successfully.

The main problem isn't with Ubuntu, it's with AMD and Nvidia refusing to release details about their drivers.

---

### Post by critin on 2012-11-12
Have you ever tried an open source nouveau driver?   They're in Additional Drivers.  Or Synaptic.    There may be one or two there that work for you.

---

### Post by Mark Phelps on 2012-11-12
Actually, if by "you", you mean folks in the Linux community, then "we" did take action to make installation of restricted drivers for ATI and Nvidia an easy thing to do.

This was done using a FREE app known as Envy.  You downloaded and installed it, and it did everything for you: downloaded the right drivers, installed them, anbd configured the X-server.  Couldn't get much easier than that!

But, Alberto Milone, the developer and distributer of Envy, moved on to other things ... and Envy expired in 2010.

We are a community of "volunteers" -- and eventually, even the hardiest of us gets tired of it.

---

### Post by deadscion on 2012-11-12
> **critin said:**
> Have you ever tried an open source nouveau driver?   They're in Additional Drivers.  Or Synaptic.    There may be one or two there that work for you.

Sure, I looked into Nouveau drivers.
First the source code must be compiled in your O.S.
Then you have to use terminal commands to adjust. I could not find a binary install for it.

I saw nothing for the beginner on their website, but at least this is a step in some direction. 

I agree the manufacturers of graphics cards are somewhat at fault here.

I apologize for the aggressive topic, but the point is still clear, if this issue is not greatly simplified, many people will not consider Linux as any kind of alternative.

---

### Post by Bashing-om on 2012-11-12
My input.
 I have been an avid user of free open source software for many many years. I have ubuntu as my primary operating system of choice since version 8.10. I have installed ubuntu for my use on several systems over the years, and only one time (ATI) have I had a problem with graphics drivers. At any opportunity I still install 'buntu on client's machines and have yet to get a bad "experience". I find this response as  MAFoElffen states very apt:
> 
It's a combination of the changes made to grub, the kernel and xorg to implement KMS technologies... Translation? They are trying to get graphics technologies in the Linux OS to catch up to the capabilities of todays GPU's... There's a few growing pains in those adjustments for that.
In conclusion: If one is not an extreme gamer, and avoids bleeding edge graphics cards, then the available drivers perform very well. -The right tool for the right job-.
[INDENT]just my humble opinion ==> BDQ

[/INDENT]

---

### Post by grahammechanical on 2012-11-12
> Why haven't you taken the thousands of complaints in askubuntu.com into consideration and set up something the beginner can handle? 

AskUbuntu is completely separate from this forum. Have you put your complaints to Askubuntu?

I have never had any problems installing video drivers in Ubuntu not since I started using it more than five years ago. Ubuntu has a default video driver. Which worked fine. so, in one sense we do not need to install a driver.

From 12.04 onwards when we install Ubuntu and chose the option to install third party software the installer downloads, installs and activates the proprietary video driver. How easy can it get? There is also a Utility called Additional Drivers that will install and activate a proprietary video driver if we choose not to install third party software at installation time.

I do not agtree with this statement at all. It is simply not true.

> Especially when it is so easy for a beginner to make a mistake which cripples the entire operating system, leaving a new user extremely frustrated,

Of course, if you want to go out a buy the latest hardware on the market expecting Linux to install on it without issues, then you have more money than sense. That is what I say.

I have also noticed from posts on this forum that a lot of beginners mess things up because they attempt things that beginners should not do. Such as installing video drivers from the  makers web site. Or they do not research how to do things.

I had the sense to research the hardware that was compatible with Linux before I purchased the components for the machine that I was going to build myself.

Ubuntu makes it easy to find compatible machines.

[https://friendly.ubuntu.com/]("https://friendly.ubuntu.com/")

---

### Post by deadscion on 2012-11-12
> 
Especially when it is so easy for a beginner to make a mistake which  cripples the entire operating system, leaving a new user extremely  frustrated, 			 		

> **grahammechanical said:**
> .



Of course, if you want to go out a buy the latest hardware on the market expecting Linux to install on it without issues, then you have more money than sense. That is what I say.



Rarely are beginners aware of, let alone,  buy the latest hardware. They usually go to WalMart or Best Buy,,,,, shudder,,,, hah.   
So this opinion is way out of touch.

---

### Post by QIII on 2012-11-12
> **deadscion said:**
> Rarely are beginners aware of, let alone,  buy the latest hardware. They usually go to WalMart or Best Buy,,,,, shudder,,,, hah.   
So this opinion is way out of touch.

No.  I think that was his point.  Most people don't.

The open source driver is compiled into the kernel at install time by default.  No user intervention is required.

If you want to install the proprietary driver later, there is a simple GUI for doing that

For those rare occasions when that does not work, the terminal can be used.  AskUbuntu is not the only place, nor necessarily the best place, to learn how to do that.

The fact is that it is, in the vast majority of cases, no more difficult to install graphics drivers in modern Linux distros than in Windows -- except that a driver for the latest plaything may appear for Windows before Linux.

Furthermore, once the proprietary driver is installed, it has a graphical interface from the OEM that allows adjustment just as in Windows.

I think your basic premise is equal parts ancient history, urban myth and FUD -- but I'm not saying that was your intent.

---

### Post by squakie on 2012-11-12
This may be extremely difficult for someone without the technical background to understand, but since AMD(ATI) and nVidia don't release the details of their driver, nor does it appear do they release any information pertaining to the internals of their hardware, it's an EXTREMELY difficult task at best to try write drivers.  It's almost as if someone said "here's your PC hardware, but you can't load any OS because we're not telling you how it works - you'll have to figure out the hardware and the internals of using it on your own, then write your own OS to run on it from scratch".  Unlike a PC where there is a "standard" to the hardware - compatible CPU's, motherboards, etc.,  from multiple manufacturers, video adapters aren't quite the same.  Yes, they need to recognize a certain set of instructions, but communicating those instructions and in the format the adapter will understand is the duty of the driver.

People are used to Windows and downloading a driver and installing it.  This is because Microsoft forces manufacturers to be compliant.  Linux is open source - the manufacturers don't normally provide drivers for Linux.  It's not a Linux problem - it's an external of getting manufacturers to support Linux - and you can bet that somewhere down in the agreements they have with Microsoft are probably some words about non-competing operating systems.  Those with enough willingness probably negotiate around that, but most manufacturers are busy working on the next "latest and greatest" and don't do much for existing hardware - especially with drivers for a non-Windows OS.

A prime example of a manufacturer who does a great job of making things Linux-friendly is HP.  We all wish they were all like that.

---

### Post by dannyboy79 on 2012-11-12
I agree with the OP and note seeing hundreds of threads about fresh installs and the user being presented with a black screen. It's all to often. I think Ubuntu needs to work more on a fallback session (vesa driver or whichever basic driver) so that IF the system can't determine it needs to use nomodeset or whatever, it should at least present a basic graphical interface for the basic user to be able to do whats needed to get things working.

Just my 2 cents

(PS I know its the graphics card manufacturers fault here but Ubuntu could have a better fall back session thing in place)

---

### Post by QIII on 2012-11-12
You may see hundreds of threads.  But out of how many fresh installs?  People come here for help when things go wrong, not when they go right.  That makes for a very significant referral bias and makes a conclusion derived from the data set invalid.

---

### Post by dannyboy79 on 2012-11-12
> **QIII said:**
> You may see hundreds of threads.  But out of how many fresh installs?  People come here for help when things go wrong, not when they go right.  That makes for a very significant referral bias and makes a conclusion derived from the data set invalid.it's irrelavent how many "success" stories there are. Fact is IF Linux wants to have more adapters from the Windows Environment something as simple as having a GUI after a fresh install is paramount. The fact also that the "black or blank screen" has been happening in Ubuntu (Linux) since version 6.06 when I first started using Ubuntu says something IMO.

DOn't get me wrong either. I love Ubuntu and use it as my main workstation and server as well BUT I learned how to solve issues like that or installing WIFI modules where as other users may not want to take the time to learn and just go right back to windows. It's just my opinion and would think the graphics issues would have a better fall back  solution then it does after so many YEARS of the same problem.

---


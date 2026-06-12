---
title: "How do you create a distro?"
date: 2008-09-13
forum: Other OS Talk
---

### Post by ryclegman on 2008-09-13
Hello,

Iv been reading for some time now on how to create a Linux distro. I know my way around Linux very well.. Iv been working with reconstructor, but want to actually do it myself. Iv ready LFS but am not really a fan of it. Is there a scripting language i should learn?  Is there any program that can help you step by step, not having the computer do it, but it helping me do it myself. I am very determined to learn how do this. If you know how to do this, how did you learn?  I am not into giving up, so if you can help great if not thanks for reading!:)

---

### Post by zmjjmz on 2008-09-13
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

---

### Post by ryclegman on 2008-09-13
> 1- The host system. This is your current Ubuntu install. You will need to install syslinux squashfs-tools and mkisofs to be able to build the live cd with your current system. 

Does this mean my i will be overwriting my Ubuntu set up?

---

### Post by zmjjmz on 2008-09-13
> **ryclegman said:**
> Does this mean my i will be overwriting my Ubuntu set up?

No.
You make a folder, and you will build the distro in that folder. Then you take that folder and make an iso of it.

---

### Post by ryclegman on 2008-09-13
OK. i was confused on that one, because iv been to that post before..
Thanks for the help!

---

### Post by ryclegman on 2008-09-13
Do you know how to create a Live cd by chance? zmjjmz

---

### Post by smartboyathome on 2008-09-13
ryclegman: See [this thread]("http://ubuntuforums.org/showthread.php?t=852868") for a list of programs to help you make your own distro. I personally recommend Remastersys.

---

### Post by zmjjmz on 2008-09-13
> **ryclegman said:**
> Do you know how to create a Live cd by chance?

Actually, not by heart.
If I could, Icebuntu 2.4 would be out by now.

---

### Post by ryclegman on 2008-09-13
lol ic...

---

### Post by ryclegman on 2008-09-13
Im not looking ro make a Ubuntu spin off. I would like to base it off of arch, but im not sure how to make it a live cd.... is there any way to make it into an easy installer like Ubuntu, and a good live cd?

---

### Post by LaRoza on 2008-09-13
> **ryclegman said:**
> Im not looking ro make a Ubuntu spin off. I would like to base it off of arch, but im not sure how to make it a live cd.... is there any way to make it into an easy installer like Ubuntu, and a good live cd?

Yes, see the sticky.

There is no easier way. You have to learn and do work.

---

### Post by cardinals_fan on 2008-09-13
> **LaRoza said:**
> 
There is no easier way. You have to learn and do work.
*shock*

The horrors!

---

### Post by LaRoza on 2008-09-13
> **cardinals_fan said:**
> *shock*

The horrors!

Next thing you know people will be asking for people to do all the work...

Whoops: [http://ubuntuforums.org/showthread.php?t=919301](http://ubuntuforums.org/showthread.php?t=919301)

---

### Post by Whiffle on 2008-09-13
> **LaRoza said:**
> Next thing you know people will be asking for people to do all the work...

Whoops: [http://ubuntuforums.org/showthread.php?t=919301](http://ubuntuforums.org/showthread.php?t=919301)

I like your style.

*high fives*

---

### Post by smartboyathome on 2008-09-13
> **ryclegman said:**
> Im not looking ro make a Ubuntu spin off. I would like to base it off of arch, but im not sure how to make it a live cd.... is there any way to make it into an easy installer like Ubuntu, and a good live cd?

You might want to follow the Maryan Linux project. We're currently working on making an arch-based E17 distro using the larch scripts.

---

### Post by ryclegman on 2008-09-14
That is kinda what i would like to do something like that...

---

### Post by cardinals_fan on 2008-09-14
> **ryclegman said:**
> That is kinda what i would like to do something like that...
Any particular reason why?

---

### Post by ryclegman on 2008-09-14
I really like the E17 and that nice Ubuntu installation and boot up.

---

### Post by MaxIBoy on 2008-09-14
> **ryclegman said:**
> Im not looking ro make a Ubuntu spin off. I would like to base it off of arch, but im not sure how to make it a live cd.... is there any way to make it into an easy installer like Ubuntu, and a good live cd?


[LIST]
[*]Learn the command line inside and out.
[*]Write a BASH script to install the system, using simplified prompts for user input with explanations, and translating that into the commands which can be taken from the archlinux installing howto.
[*]Profit.
[/LIST]

You're not going to get a very good liveCD environment out of Arch, not without a lot more work, because Arch isn't designed to be usable out of the box-- it's [The Arch Way](http://wiki.archlinux.org/index.php/The_Arch_Way) to require extensive manual configuration, tailoring each installation to one computer.



There are other extra-lightweight distros you can build on, for instance DSL.

If you're willing to do it, you could also start entirely from scratch.

---

### Post by cardinals_fan on 2008-09-14
> **ryclegman said:**
> I really like the E17 and that nice Ubuntu installation and boot up.
Eh?  Sorry, but I still don't see why you want to create a distro.

---

### Post by Sorivenul on 2008-09-14
> **ryclegman said:**
> I really like the E17 and that nice Ubuntu installation and boot up.

Do something with even more minimal window managers.  There are so many E17 distros out there already: eLive, OzOS, Maryan, etc.  If you're looking to create something different do something that stays away from Gnome, KDE, Xfce, E17, Fluxbox, and Openbox.  That may seem pretty limiting, but there's a *lot* more out there.  Just my 2 cents.

---

### Post by snowpine on 2008-09-15
In my opinion, the word "distro" is over-used. If you're taking an existing distro and making a new live CD with a different windows manager or a different set of applications or new artwork, I consider that to be a "remaster" and not a new distro. Which is not to say it's not really, really fun. :)

---

### Post by ryclegman on 2008-09-15
Me and my partner have devised a plan for what out goal is.. we will have a webpage up within a week!

---

### Post by Sorivenul on 2008-09-15
> **ryclegman said:**
> Me and my partner have devised a plan for what out goal is.. we will have a webpage up within a week!

Care to share some preliminary info?

---

### Post by blogzzz on 2008-09-16
You could try [www.**linuxfromscratch](www.**linuxfromscratch)**.org.

---

### Post by ryclegman on 2008-09-16
> **Sorivenul said:**
> Care to share some preliminary info?

LOL we will share when ready!

---

### Post by Bart_D on 2008-09-16
I've heard that before....from the Mint Linux or PCLinux guys: "When it's ready it's ready."

---

### Post by Sorivenul on 2008-09-17
> **Bart_D said:**
> I've heard that before....from the Mint Linux or PCLinux guys: "When it's ready it's ready."

I have as well.  

However, with a new "respin/remaster/distro", that says they know their project goals and what they want to do to accomplish those, answering a question about what those are shouldn't be difficult.  One should be able to explain the project without having it developed first.  

It is good to know as a developer what the point of your project is, and it is a courtesy to potential users to be able and willing to explain that.  After that, a "When it's ready it's ready" is acceptable, IMHO.

I'm not trying to start a war or prevent the OP from completing this project, I just think a little more information may be helpful both to us as potential users, and to the OP as these forums may help offer insight, ideas, and possibly some help for the project.  Just my 2 pennies.

---

### Post by molom on 2008-09-18
> **Bart_D said:**
> I've heard that before....from the Mint Linux or PCLinux guys: "When it's ready it's ready."

Its also what the Duke Nukem Forever guys say ;) .

PS. The Chakra project also says that.

---

### Post by kelvin spratt on 2008-09-18
You can now get a Arch live cd that installs on your system, it uses lyde as the manager is very lite on resources  65mb on startup and in true Arch tradition it all works.

---

### Post by handy on 2008-09-18
I can't believe this thread is still going after LaRoza pointed you at the sticky.

Do you really want to create a Linux kernel based distro' or are you just here for a conversation?

***[Edit:]** Hey, conversation is fine, don't get me wrong... :-)*

---


---
title: "Will xubuntu run on a 500 mhz processor and 128 mb ram?"
date: 2008-07-28
forum: Other OS Talk
---

### Post by eragon100 on 2008-07-28
Will xubuntu run on a 500 mhz processor and 128 mb ram?

---

### Post by aysiu on 2008-07-28
> **eragon100 said:**
> Will xubuntu run on a 500 mhz processor and 128 mb ram?
Yes, but...

1. In order to install Xubuntu without having the installer freeze up on you, I'd highly recommend using the Alternate CD instead of the Desktop CD.

2. A lightweight window manager (IceWM or Fluxbox) will be slightly speedier than a full (if even lighter) desktop environment like Xfce (which is what Xubuntu uses).

---

### Post by eragon100 on 2008-07-28
Fluxbox... So fluxbuntu is a better option?

---

### Post by lukjad on 2008-07-28
Ignore me. See post below.

---

### Post by aysiu on 2008-07-28
> **lukjad007 said:**
> I would also add that if I were you I would only install feisty fawn on that PC. It is not as heavy as 8.04 and still has a bunch of programs. I'd have to disagree. 

Ubuntu 7.04 will receive security updates for only another two months, so it is not a good choice to install. 

Heaviness or lightness depends most greatly on the packages you choose to install, not how recent or old a release you install them from.

> **eragon100 said:**
> Fluxbox... So fluxbuntu is a better option? If Fluxbox is what you're comfortable with, yes. I prefer IceWM myself. If you like IceWM better, too, you might want to look into IceBuntu.

Alternatively, you can install Xubuntu and then install Fluxbox or IceWM on top of it and just choose to use the window manager at the GDM login screen instead of using Xfce.

---

### Post by schauerlich on 2008-07-28
> **eragon100 said:**
> Will xubuntu run on a 500 mhz processor and 128 mb ram?

If you're into tiling window managers, wmii is incredibly light and easy to use once you get used to the keyboard combos.

---

### Post by tel93 on 2008-07-28
> **eragon100 said:**
> Fluxbox... So fluxbuntu is a better option?

Not even that will run well.

Use Debian- the only user-friendly non-light os that'll run well.

---

### Post by snowpine on 2008-07-28
> **tel93 said:**
> Not even that will run well.

Use Debian- the only user-friendly non-light os that'll run well.

I disagree; I used to run Fluxbuntu every day on a 500mhz Piii with 256mb of ram and it ran very well. On my desktop I use Fluxbuntu in a 96mb virtual machine for testing stuff out. It will even install on some 64mb machines (though without much ram left for other tasks).

Full disclosure however--I have never tried Debian. I'm sure that is great too. :)

---

### Post by SunnyRabbiera on 2008-07-28
You can try antix mepis, its great for old computers.

---

### Post by molom on 2008-07-28
I highly recommend you using Debian. Maybe go with parsix or mepis, since it is based on debian I imagine it will be more capable. Maybe use an XFCE Debian distro, maybe DreamLinux will run perfectly. Xubuntu and Fluxbuntu aren't the way to go. Xubuntu = too heavy and fluxbuntu = Outdated and development is very very slow.

I think dreamlinux is the best for a computer like that.

---

### Post by Midwest-Linux on 2008-07-29
You know, I was almost going to ask the same question. I want to use Xubuntu/Ubuntu on a 166 Mnz machine (Omnibook 5700) with 48 MB of ram. (Can't upgrade the ram, it takes one of those obsolete ram sticks with fetch nearly $100 on E-Bay  which is a 64 MB RAM). Besides this machine can only go to 128 MB RAM.

 So been doing some reading and googling. Seems I can install 7.04 as a server, and then selectively install various things via command line. From what I read Gnome is out and so is XFCE (from what I read) but instead use IceWM or Fluxbox.

I saw another thread with using a combination of DSL, G-Parted. I prefer using a Ubuntu derivative.

 I found this 
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

And a older thread 

[http://ubuntuforums.org/showthread.php?t=174974](http://ubuntuforums.org/showthread.php?t=174974)

And another thread mentioning Ubuntu/Debian-Sarge Mini-RAM HOWTO

How to install an Ubuntu-Desktop on low memory systems
(Pentium II and III Processor, 32-256 MB RAM)

[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

I downloaded the minimal 7.04 and selected "server" as BOOT. I am going to follow the steps contained in the threads. If it doesn't work out then I will try selecting the command line from the alternate install CD from 7.04. I mention 7.04 because the thread said 8.04 might have some bugs. 

 Not only do I need to get this going on this 48 MB laptop. I will be getting two more laptops (from E-bay) with 64 MB RAM and if this pans out...I can use the same method on those laptops. (However those I believe takes the more "modern" 144 pin SODIMMs.) Some people collect stamps, I collect computers....


(Further complicating this is that the laptop (Omnibook 5700) that this is going on is 48 MB RAM, but the laptop doesn't boot from CD. So I have taken the hard drive from it, put it in another laptop Compaq Presario 1200 (with 96 MB) ram...which boots off the CD and will install it on it and then transfer the hard drive to the (Omnibook 5700) with 48 MB RAM that doesn't boot off the CD (due to the ancient bios which only allows floppy or hard drive boot only)....and the bios is as "up to date" as one could have.  

This has been a ongoing project for a few months. I did sucessfully install Windows NT 4.0 on the Omnibook 5700 with a floppy and the CD Rom which i bought off of E-bay last year. (It will boot to the floppy and them allow it to play the CD). BTW, NT 4.0 while a fine OS for its time...it is hopelessly out of date.

OK so...why didn't I just go with DSL. Tried that, either my DSL disc is shot...but when I tried to format the HD, it could not find the hard drive....maybe I needed to format and partition first?

Then again, It has been only a year playing with Linux and I still don't fully comprehend having to format and partition BEFORE installing....unlike Ubuntu and most other distros which does it on the fly.

So why didn't I try using the floppy boot disc from Puppy or DSL. Tried that too. Problem was my floppy drive is on my XP machine, the file is 147,000 and the floppy limit is 144,000. Obviously I am missing something here. 

I tried Tom's rtbt 2.0 floppy boot program...yes..you guessed it ..the file was too large. Again maybe its because I was trying to make a Linux boot floppy from a XP machine?

I also tried installing Xubuntu 7.04 in its entirety on the hard drive (using the stand in laptop with 96 MB)...hoping that I can use it in some fashion ...just maybe.

Well there is yet another problem. Since the Omnibook 5700 bios only recognizes small hard drives (like 2.1 GB) installing anything bigger like the spare 6.4 GB drive was not recognized on the Omnibook 5700. So yes I did try putting Xubuntu 7.04 on it...It got stuck a 85% through the installation and hung there for hours...yes I was using the alternate 7.04. I though xubuntu 7.04 only takes 1.5 GB space...yet I saw in another thread it takes more...(I'm still learning)

So why don't just toss the Omnibook 5700 and go to something else? Well first off its in nearly pristine condition and the battery still works for about 20 minutes to a half hour and I got it from my brother in law a year ago. I guess I could just throw NT 4.0 back on it and let it gather dust. But there has to be a way to throw Linux on it and be able to run even maybe only one app at a time.


So this is one of my ongoing projects...please pardon the long rant...I needed to explain why I am going by this method and if anyone wants to add to this...please do!
---------------------------------------------------------------


 P.S. maybe I will start a separate thread on the worst "out of date" computers to use with Linux. So far I have two in the running the .....Omnibook 5700.

 And the Chembook 6133...which I was unable to install any form of Ubuntu/Xubuntu on it, though Vector Linux installed and ran just OK on it. The Chembook has 164 ram and should run Xubuntu...but thats for another thread. 

Hint, you have to disassemble the whole computer bottom cover to access the ram....which is located behind the fan and the heatsink on the bottom......lol

---

### Post by wolfen69 on 2008-07-29
my vote goes to either debian or ubuntu minimal install with openbox. i would not run xubuntu without at least 192 ram. fluxbox may also be an option.

---

### Post by K.Mandla on 2008-07-29
> **eragon100 said:**
> Will xubuntu run on a 500 mhz processor and 128 mb ram?
Yes. Now if your question was ...
> **eragon100 said:**
> Will xubuntu run **well** on a 500 mhz processor and 128 mb ram?
I'd say no. But I have different standards than most people.

---

### Post by wolfen69 on 2008-07-29
hey midwest, i would do my best to get DSL to work on it. it's probably your best bet.

---

### Post by cardinals_fan on 2008-07-29
I would recommend Slackware or Vector on that machine.

---

### Post by molom on 2008-07-29
The funny thing about this is if this was a person that only runs Windows, he/she would chuck it away because there is no other solution than running 98 or 2000 :lolflag:

PS. Vector should even be better like cardinals says. The reason I suggested debian was because its the closest thing to Ubuntu.

---

### Post by darrelljon on 2008-07-29
Canonical should ditch Xfce and Xubuntu and build and support a Ubuntu distro with Enlightenment, Fluxbox, IceWM, Rox or JWM.

---

### Post by mips on 2008-07-29
> **darrelljon said:**
> Canonical should ditch Xfce and Xubuntu and build and support a Ubuntu distro with Enlightenment, Fluxbox, IceWM, Rox or JWM.

You have a valid point there. Xfce does not use that much less resources compared to the normal Gnome version.

Even better, they could make one distro with all the above you mentioned included or at least E17, Openbox, IceWM all depending how much they can fit on the cd. Or at least have prebuilt meta packages in the repos.

---

### Post by timzak on 2008-07-29
> **aysiu said:**
> I'd have to disagree. 

Ubuntu 7.04 will receive security updates for only another two months, so it is not a good choice to install. 

Heaviness or lightness depends most greatly on the packages you choose to install, not how recent or old a release you install them from.

 If Fluxbox is what you're comfortable with, yes. I prefer IceWM myself. If you like IceWM better, too, you might want to look into IceBuntu.

Alternatively, you can install Xubuntu and then install Fluxbox or IceWM on top of it and just choose to use the window manager at the GDM login screen instead of using Xfce.

Good point.  I have 7.04 (Xubuntu) running on my son's first "real" computer (he's 4 and only uses it for email and TuxPaint so far).  I have kept 7.04 on there because it only uses about 64 MB on bootup (compared to ~100 MB for 8.04) and the machine is very modest (Celeron 466Mhz, 256MB).  I need to keep this system simple and easy to use for him.  Would IceBuntu fill the bill?  Or should I just install Xubuntu 8.04 and IceWM on top.  All I really need to run on it is Thunderbird (for built-in HTML support, otherwise I'd use Sylpheed), TuxPaint, and a few other childrens' games like Gcompris and Childsplay.  I like the Ubuntu way to simplify security updates, so I'm hesitant to try other distros because I'm not familiar with them and don't have time to learn a new way.

Thanks for any tips.

---

### Post by Midwest-Linux on 2008-07-29
Well I went with DSL, I finally got to the desktop. I attempted to install it to the hard drive . I created a partition (hda1). But it won't install because I have to do cfdsk, I typed that into the command terminal and it said it was invalid.

I found on You Tube a excellent DSL install video.

[http://www.youtube.com/watch?v=PhP17LPOCOU](http://www.youtube.com/watch?v=PhP17LPOCOU)

---

### Post by Midwest-Linux on 2008-07-29
> **Midwest-Linux said:**
> 

I found on You Tube a excellent DSL install video.

[http://www.youtube.com/watch?v=PhP17LPOCOU](http://www.youtube.com/watch?v=PhP17LPOCOU)

I managed to install DSL on the HP5700 using another computer and swapping hard drives. 

The results are ....It is not finished...unfortunately, I am at a desktop with small silver like threads across the whole screen and the PS/2 mouse does not work. Still it is much more progress than ever had up to this time. 

Now I must somehow debug this, but at least a big hurdle is over...and thanks to the install video...I can at least redo it with ease using the command line. 

 The command line was a piece of cake, I just followed the video and the only difference I made was not using ext3 as it was not recommended for slower systems like this 166 Mhz pentium MMX  48 MB RAM and 2.1 GB hard drive.

 I think the only mistake I might have made is to allow for only a 128 MB swap...since the computer this is going into is only 48 MB RAM. I know I have to do something with the video settings and reset the mouse...it has a built in touchpad mouse though I didn't expect it to work anyway.

Need to take time out from this...after all it has been a long term project anyway.

---

### Post by mordak13 on 2008-07-29
I was running Xubuntu on a Athlon XP 2700 with 256mb ram and it was slow especially with Firefox. 512mb ram made it useable. What about eLive? It uses the E17 Enlightenment Window Manager. Pretty too. Just a thought.

---

### Post by gjoellee on 2008-07-29
you should check out wattOS (still in alpha I think)....
[http://news.softpedia.com/news/Introducing-wattOS-A-Lightweight-Ubuntu-89456.shtml](http://news.softpedia.com/news/Introducing-wattOS-A-Lightweight-Ubuntu-89456.shtml)

however I think Xubuntu will run just great! check this video:
[http://youtube.com/watch?v=_qddueXkD8E](http://youtube.com/watch?v=_qddueXkD8E)

this is pretty close to your system....

---

### Post by cardinals_fan on 2008-07-29
> **darrelljon said:**
> Canonical should ditch Xfce and Xubuntu and build and support a Ubuntu distro with Enlightenment, Fluxbox, IceWM, Rox or JWM.

> **mips said:**
> You have a valid point there. Xfce does not use that much less resources compared to the normal Gnome version.

Even better, they could make one distro with all the above you mentioned included or at least E17, Openbox, IceWM all depending how much they can fit on the cd. Or at least have prebuilt meta packages in the repos.
Or they could just give Xubuntu a tuneup...

---

### Post by eragon100 on 2008-07-29
Puppy would also run on that hardware, right?

---

### Post by cardinals_fan on 2008-07-29
> **eragon100 said:**
> Puppy would also run on that hardware, right?
Yes :)

---

### Post by tel93 on 2008-07-29
> **molom said:**
> The funny thing about this is if this was a person that only runs Windows, he/she would chuck it away because there is no other solution than running 98 or 2000 
Windows 2000 will never run well on that machine.

Unfortunately my father threw out all the old computers even after I asked him for them. He said that I was stupid for wanting such old crap. I saw a PIII with 256mb of RAM, Ethernet, CD-RW, a sound card and USB on eBay for $20 (FULLY WORKING) but my dad wouldn't let me buy it and he started insulting me for wanting it.

---

### Post by mikjp on 2008-07-30
I collected a few weeks ago my views and some information about distributions for this kind of hardware in my blog:

[http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html](http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html)

This information might help someone with similar problem.

Greetings,

mikko

---

### Post by molom on 2008-07-30
> **tel93 said:**
> Windows 2000 will never run well on that machine.

Unfortunately my father threw out all the old computers even after I asked him for them. He said that I was stupid for wanting such old crap. I saw a PIII with 256mb of RAM, Ethernet, CD-RW, a sound card and USB on eBay for $20 (FULLY WORKING) but my dad wouldn't let me buy it and he started insulting me for wanting it.

Thats the consumer market for you. If it doesn't run XP or Vista, its unusable, people think. 

I would love that computer for $20, you can use it for browsing, music and videos, you could also run OpenOffice on it pretty well. That PC would run lightning fast if running E17 or Fluxbox, some people just don't know the specifics, specialists would say someones crazy for chucking away a cord phone I guess. Don't know why people would say that anyway, but if you don't know much about something, people would chuck it away. If your a gamer, sure its useless, but if you do the basics, whats the problem?

---

### Post by mikjp on 2008-07-30
I will soon start my studies in a new town, and I am not going to buy yet another computer to use three or four days a week in another town. Instead, I'll try to find some "old crap" for free :-)

---

### Post by K.Mandla on 2008-07-30
> **molom said:**
> Thats the consumer market for you. If it doesn't run XP or Vista, its unusable, people think.
Big +1. Amen.

---


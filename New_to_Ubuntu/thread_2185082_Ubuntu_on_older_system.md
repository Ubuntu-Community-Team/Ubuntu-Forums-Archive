---
title: "Ubuntu on older system"
date: 2013-10-31
forum: New to Ubuntu
---

### Post by kromaz on 2013-10-31
Hello,

I have heard many good thing about Ubuntu and would like to install on an older computer. My system specs Pentium 4 2.8 GHZ (northwood), 2GB RAM (rambus) and ATI X800 PRO AGP 4X. Would Ubuntu 12.04.3 LTS be the best option or could I go with an older version for better performance? I also heard Unity can slow down older computers big time. Many thanks for any help the community can provide.

---

### Post by DuckHook on 2013-11-01
Ubuntu would choke on a system with your specs. I doubt that you could even get compiz to run on that video card. You have enough RAM though, which gives you lots of options.

You can try Lubuntu, which has no 3D effects and is quite plain, but should work smoothly and relatively responsively with the equipment you have. You can also try Bodhi which will run nicely as well. However, you would have to get used to the rather different Enlightenment desktop. Bodhi uses the Ubuntu repositories, which is a big plus for new users.

You can also leave the Ubuntu universe altogether and try CrunchBang, Puppy, SliTaz, Tiny Core or Damn Small Linux. If you decide to do so, my recommendation would be CrunchBang.

Make sure you install only the 32-bit OS. I highly encourage you to burn all of these to CD/DVD and take them for a test drive. Linux is amazing not least because you can try out so many alternatives for the price of a CD.

---

### Post by walterorlin on 2013-11-01
Lubuntu will run on that not sure about unity. Older version don't get security updates which is a problem.

---

### Post by kurt18947 on 2013-11-01
I just worked with a system similar - P4 w/ 1 GB RAM & ATI AGP video.  I sent along a Mint13 32 bit DVD for use when (not if) Windows craps again.  The DVD seemed to run pretty well in somewhat limited testing.

---

### Post by Bucky Ball on 2013-11-01
Xubuntu or Lubuntu will be fine. There are lots of other lightweight distros but try those two first as they are part of the Ubuntu family and easy to get help for (download 32bit ISO, burn disk, boot from disk and 'Try *buntu' to see how it rolls. If you like, install). 

The other option is a mini.iso install, but a bit involved for a beginner. It basically installs the ubuntu kernel only and you install the rest. You make that as light as you like (lightweight desktop environment and only the apps you need).

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) 

As you learn more about it you'll get it more fine tuned. It is really all about the desktop environment (Ubuntu uses 'Unity', a hog, Xubuntu and Lubuntu use xfce4 and lxde, respectively ... lighter on resources). And let's face it, if all you do is surf the web, send some emails, watch a vid and listen to some music, you don't need or want a full install of anything (which is where the mini.iso is great).

Incidentally, I have a P4, 3gHz, 1Gb RAM running Xubuntu without issue.

PS: As mentioned, don't go for anything older than 12.04 LTS (no support). 12.04 LTS of anything you do go for is perfect place for a beginner to start, though. Stable, a known entity and supported until April 2017. 13.04 and 13.10 have nine months support and '13.04' = 2013, April, if you get the syntax. 

13.10 has just been released so wouldn't advise if for starters. 

Good luck. ;)

---

### Post by elliotn on 2013-11-01
> **DuckHook said:**
> Ubuntu would choke on a system with your specs. I doubt that you could even get compiz to run on that video card. You have enough RAM though, which gives you lots of options.

He may not get compiz but I think Ubuntu would run great.. . I ran Ubuntu on 1.8GHz CPU with 1Gig of ram and an old ATI gfx but it ran well except Compiz

---

### Post by Bucky Ball on 2013-11-01
Yea, agreed. Don't think Compiz is really an issue or of any concern here. (Not everybody uses it and I, for one, never have.)

---

### Post by Pako Pako on 2013-11-01
You can run Ubuntu 12.04 without unity I believe... I forgot how to do that, but I know it IS possible to have the robust GNOME-style interface without the resource intensive Unity bar.

That said, Xubuntu, Lubuntu, and LXLE are all Unity-less Ubuntu installs and all work very well on even a Pentium III. (You could install Gnome afterwards, I suppose, but that's an extra step.) You have 2 GB of RAM which makes things even better for you.

---

### Post by mörgæs on 2013-11-01
> **anthonypineiro said:**
> ... or could I go with an older version for better performance? 

No, the latest Lubuntu (13.10) is by far the best performing, also on old or semi-old (like yours) hardware.

---

### Post by kromaz on 2013-11-01
Wow a lot of responses. What a great community! Time to get some testing done. What's the performance difference running off CD versus installed on hard drive? Thanks everyone. :D

---

### Post by Bucky Ball on 2013-11-01
You will find the CD experience a little slower. Also, there may be some drivers which will not install because running on CD but will install once you're running from hard drive (wireless and graphics mostly). 

So, welcome to the community! Burn some ISOs and have fun testing! Hope you find something that suits (I don't doubt you will) and hope you enjoy (and are prepared) for the learning curve. It's not unpleasant. ;)

---

### Post by Mopar1973Man on 2013-11-01
I've found that Lubuntu is a lighter weight option for older PC's and does fairly well with a Single code AMD 939 2.0 GHz and 1 GB of memory. Unity desktop and and Ubuntu is a but too much for that machine.

---

### Post by kromaz on 2013-11-01
When I run Ubuntu off a CD does it write to the hard drive or handled all in memory? Don't want any effect done to the OS currently on the hard drive while testing Ubuntu.

---

### Post by Impavidus on 2013-11-01
> **anthonypineiro said:**
> When I run Ubuntu off a CD does it write to the hard drive or handled all in memory? Don't want any effect done to the OS currently on the hard drive while testing Ubuntu.

It won't. Unless you command it to do so of course, but the live disk is intended to allow you to test Ubuntu without affecting the currently installed system(s).

---

### Post by newb85 on 2013-11-01
Running off a CD or DVD will be slow (limited by the read speed of your ROM).  From a USB Won't be as slow.  Hard drive is the best option for normal use.

---

### Post by protoss96 on 2013-11-01
I am recommending you to install Ubuntu with XFCE4, LXDE ot GNOME desktop enviroment, that will fit your hardware very well.

---

### Post by kromaz on 2013-11-01
> **protoss96 said:**
> I am recommending you to install Ubuntu with XFCE4, LXDE ot GNOME desktop enviroment, that will fit your hardware very well.

Can I choose the desktop environment during install or is this something that need to be done afterwards?

---

### Post by deadflowr on 2013-11-01
> **anthonypineiro said:**
> Can I choose the desktop environment during install or is this something that need to be done afterwards?

If you use Ubuntu's normal install disk, then no.
But if you use the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD"), which does a netinstall, then yes you can choose which desktop you would like to use during install.

Added: It's a little more complex of an install, and requires a tad more attention than a normal install.

---

### Post by kromaz on 2013-11-01
> **deadflowr said:**
> If you use Ubuntu's normal install disk, then no.
But if you use the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD"), which does a netinstall, then yes you can choose which desktop you would like to use during install.

Added: It's a little more complex of an install, and requires a tad more attention than a normal install.

Awesome! With the mini.iso can I also install applications the normal install disc offers? Example firefox etc...

---

### Post by whitesmith on 2013-11-01
CDs represent a big performance hit. After you've picked your poison, be sure to install it to an HDD. Today SDDs are so cheap you might want to drop $100 or so and speed up the IO part of the old computer -- if the BIOS supports them. A final 2¢ worth: remember that the prettier the interface, the more power is required to drive it.

---

### Post by deadflowr on 2013-11-01
> **anthonypineiro said:**
> Awesome! With the mini.iso can I also install applications the normal install disc offers? Example firefox etc...

Yes.
When you install from the mini you have the ability to choose full desktops with their packages they include.
Here's [amjjawad's blog with pictures]("http://amjjawad.blogspot.com/2013/07/ubuntu-mini-iso-installation-process.html") of what the process is like.

The one caveat is that the installation does require a working network connection.

---

### Post by kromaz on 2013-11-01
> **deadflowr said:**
> Yes.
When you install from the mini you have the ability to choose full desktops with their packages they include.
Here's [amjjawad's blog with pictures]("http://amjjawad.blogspot.com/2013/07/ubuntu-mini-iso-installation-process.html") of what the process is like.

The one caveat is that the installation does require a working network connection.

I want to thank you for posting that link. This is a great community. You all been so helpful. Thanks! :D

---

### Post by deadflowr on 2013-11-01
No problem.
To add, there is a selection(not seen in the photos) at the bottom of the install packages section for manual package selection.

Good Luck, in which ever way you choose to go.

---

### Post by shabuboy on 2013-11-01
I, as you, totally new to Ubuntu. Thru some research, trial and error, managed to install Ubuntu 12.04 to a very old Dell Inspiron 8600 with a Pentium M 1.4mhz, 2gb RAM and Broadcom wireless (what a pain the wireless, but I got it!!!!). Nevertheless, the first thing you need to find out, if you processor is PAE or not. Which by the took me the longest to figure it out. Anyhow, if it is NO PAE, you have to install xubuntu or lubuntu 12.04 (or older versions I think), as they support NON-PAE processor. From there I upgrade to Ubuntu 12.04 from the terminal. All running good, and not bad at all for and OLD OLD system. This is what I did:
- Install Lubuntu 12.04. No other change or upgrades
- Install Ubuntu 12.04LTS
- Run all upgrades
- Done.

The reason I decided to go for Ubuntu is LTS. Lubuntu 12.04 support expired yesterday.

---

### Post by DuckHook on 2013-11-01
> **shabuboy said:**
> ...totally new to UbuntuJust want to give you a well-deserved pat on the back. If you are new to  Ubuntu, posting for the first time and yet managed to install on a  museum piece, figure out the Broadcom wireless mess, non-PAE kernels and  the fact that Lubuntu has no LTS... well, let's just say that you'd be  one dude I want in my corner when the going gets rough.=D>

Welcome to Ubuntu and the forums.

---

### Post by kromaz on 2013-11-01
> **shabuboy said:**
> I, as you, totally new to Ubuntu. Thru some research, trial and error, managed to install Ubuntu 12.04 to a very old Dell Inspiron 8600 with a Pentium M 1.4mhz, 2gb RAM and Broadcom wireless (what a pain the wireless, but I got it!!!!). Nevertheless, the first thing you need to find out, if you processor is PAE or not. Which by the took me the longest to figure it out. Anyhow, if it is NO PAE, you have to install xubuntu or lubuntu 12.04 (or older versions I think), as they support NON-PAE processor. From there I upgrade to Ubuntu 12.04 from the terminal. All running good, and not bad at all for and OLD OLD system. This is what I did:
- Install Lubuntu 12.04. No other change or upgrades
- Install Ubuntu 12.04LTS
- Run all upgrades
- Done.

The reason I decided to go for Ubuntu is LTS. Lubuntu 12.04 support expired yesterday.

Thanks for sharing this with me. Pentium 4 does support PAE. When upgrading did you end up with Unity or the Lubuntu desktop environment?

---

### Post by shabuboy on 2013-11-01
You end up with a login window and select the flavor you want. I run Ubuntu 2D.

---

### Post by mörgæs on 2013-11-01
(As a side note: It's a joy to watch a thread with so many good vibes. This is indeed 'Ubuntu'. 
Now back on track before I have to give myself an infraction for dragging a thread off-topic.)

---

### Post by kromaz on 2013-11-01
> **shabuboy said:**
> You end up with a login window and select the flavor you want. I run Ubuntu 2D.

Cool this is what I wanted to hear! If I install Ubuntu 12.04.3 LTS from disc, will I have a choice of what desktop environment to use due to my system specs or do I install Lubuntu first then upgrade in terminal to get the login window to select my flavor?

---

### Post by Petro Dawg on 2013-11-01
You can choose at log-in, but if your specs are too low, it will automatically log you into 2D by default no matter what you choose.  At least it did so on my computers that couldn't render 3D effects.

---

### Post by kromaz on 2013-11-01
> **Petro Dawg said:**
> You can choose at log-in, but if your specs are too low, it will automatically log you into 2D by default no matter what you choose.  At least it did so on my computers that couldn't render 3D effects.

What is your system specs using 2D, are you using Ubuntu 12.04.3 LTS if so how you like the performance?

---

### Post by Petro Dawg on 2013-11-01
I have a [COLOR=#000000]Pentium4 2.8GHz, 2G RAM, and Integrated Intel Extreme Graphics 2 which cannot use the standard 3D effects due to the really bad graphics chip, but defaults to the 2D session with out an issue at all.  I found the resources required by the 2D session is comparable to resources required by Xubuntu.

I use for my main rig, an AMD 64 Athlon 1.8GHz, 2G RAM, and Integrated NVidia GeForce 6150 LE that runs the normal 3D session fairly snappy without a problem at all.  It seems as long as the graphics chip is supported the 3D session is fine.  

From my experience, any computer that could run WinXP and has 2G RAM will be able to run Ubuntu 12.04 (or Ubuntu 2D) without a problem. 

[/COLOR]

---

### Post by shabuboy on 2013-11-01
First, thanks DuckHook! You have no idea how many times I failed, tried about 6-8 different flavors before I found about about PAE. Once I got that, wireless just about made me want to slam it to the floor. :lolflag:
I guess I picked a dinosaur to try my first ever Linux install!!!
Any chance you can help with this?
[http://ubuntuforums.org/showthread.php?t=2185262](http://ubuntuforums.org/showthread.php?t=2185262)

Anyhow...
Dell Inspiron 8600 Specs:
Intel Pentium M 1.4 GHz
30gb HD
2gb RAM
Nvidia network
Nvidia GE Force5200


 it runs ubuntu ok, not the fastest but hard to tell the difference from lubuntu. At least for the simple tasks.
It is for my 7 year old nephew, just to browse and learn mainly.
Videos from youtube at full screen suck, so installed minitube, which works fine. This was another story as the one at the store does not work.

---

### Post by DuckHook on 2013-11-01
> **Petro Dawg said:**
> You can choose at log-in, but if your specs are too low, it will automatically log you into 2D by default no matter what you choose.In 12.04, you can force unity to start in 3D by adding the following to */etc/environment*:```
UNITY_FORCE_START=1
```...but it is risky. If your chipset doesn't support the 3D effects, then sometimes your desktop won't load completely, icons or menus will be missing, or you get wonky behaviour later on that you can't pin down to anything in particular until you remember that you forced the issue. Even if it works, on marginal HW it runs like a pig with lipstick.

Unity 3D just wasn't meant for older equipment. I believe that Canonical made the decision to radically differentiate their offerings so that modern HW would run Ubuntu, Mastodons would run Xubuntu, and Dinosaurs would run Lubuntu. Overall, not a bad strategy, in my opinion.

---

### Post by kromaz on 2013-11-01
Thanks for all the great information you all provided me! I will be doing my first Linux install this evening. I will post back soon with my results. You all rock! :guitar:

---

### Post by Bucky Ball on 2013-11-01
Repeat. You do NOT have a choice of desktop environments. Lubuntu = lxde desktop environment + Ubuntu kernel + default Lubuntu apps.

If you do a minimal install, then you can choose everything; default DE, apps, etc ...

Good luck.

---

### Post by DuckHook on 2013-11-01
> **Petro Dawg said:**
> [COLOR=#000000]From my experience, any computer that could run WinXP and has 2G RAM will be able to run Ubuntu 12.04 (or Ubuntu 2D) without a problem.[/COLOR][COLOR=#000000]This is largely true and I'm not disagreeing with you or with any of the others who have recommended Unity 2D. I guess my concern with this approach is that it's a dead end. Unity 2D will not take anyone past 12.04.x. I don't know if the upcoming 14.04 LTS will support it, but I doubt it. Canonical's strategy appears to be to position the Ubuntu flavour for the here-and-now and for current HW. They are positioning the other flavours for older HW. If so, then it makes more sense to transition to Xubuntu or Lubuntu now, so that the upgrade path exists and is relatively trouble-free. At least, that's my view of things anyways.[/COLOR]

---

### Post by Petro Dawg on 2013-11-01
> **DuckHook said:**
> [COLOR=#000000]This is largely true and I'm not disagreeing with you or with any of the others who have recommended Unity 2D. I guess my concern with this approach is that it's a dead end. Unity 2D will not take anyone past 12.04.x. I don't know if the upcoming 14.04 LTS will support it, but I doubt it. Canonical's strategy appears to be to position the Ubuntu flavour for the here-and-now and for current HW. They are positioning the other flavours for older HW. If so, then it makes more sense to transition to Xubuntu or Lubuntu now, so that the upgrade path exists and is relatively trouble-free. At least, that's my view of things anyways.[/COLOR]


That is very true, and definitely something to consider if you want to go the "upgrade route" every so often.  I never do upgrades, only fresh installs, so come end of life for 12.04LTS I will probably just switch to a lighter OS on my older computers if I still have them (hopefully my stock in computer hardware will be upgraded by then though).

I used Xubuntu for a long time, but when I got my wide screen monitor, I felt the Unity interface made more sense.  Otherwise, Xubuntu is a great alternative OS.

---

### Post by newb85 on 2013-11-01
In my mind, the biggest hurdle to switching from regular Ubuntu to Xubuntu or Lubuntu is not getting the machine switched over, but getting the user switched over.  I think as few as one apt-get command could have the XFCE and (if you want) the default Xubuntu applications and (if you want) the default Xubuntu configuration set up on your machine.  (The same applies to LXDE and Lubuntu.)  You wouldn't really even need to uninstall Unity or the heavier default Ubuntu apps; if you just stop using them, they won't burden your limited hardware.

E.g.,
```
sudo apt-get install xfce4
```
or
```
sudo apt-get install xubuntu-desktop
```
or
```
sudo apt-get install xfce4 xubuntu-default-settings
```

Meanwhile, the user would still need to get used to the layout of the different system and using the different default applications.

---

### Post by Bucky Ball on 2013-11-02
> **newb85 said:**
> 
or
```
sudo apt-get install xubuntu-desktop
```


No! Why do people always give this advice??? This drags in ALL of Xubuntu, default apps, dependencies, the LOT. You DON'T want that, especially on an older machine that is already struggling for air. You ONLY want the desktop environment, xfce4, as suggested in the first command. 

If you are going to install xubuntu-desktop, you may as well do a clean install of Xubuntu because you are basically doing one ON TOP of the existing Ubuntu install. BAD idea. Your menus will contain ALL default apps for both Ubuntu AND Xubuntu. You definitely don't need that clogging up an already struggling system. 

Please peoples, if someone wants to try a different desktop environment, DON'T advise them to install *buntu-desktop anything. xfce4, lxde ... just the desktop environment. If they want to try a new DE, advising them to install *buntu-desktop to do it is the WRONG advice. 

Rant complete. Thankyou. Carry on. ;)

---

### Post by vegan.philosophy on 2013-11-02
You can still use Unity 2D on Ubuntu 12.04 LTS if you are not satisfied with the speed of your system and do not give preference to pleasant graphics. Choosing 12.04 is good as it will be supported for a few more years. Newer versions of Ubuntu may still be useful for you but they'll require a bit better configuration for optimum performance. I used Unity 2D on my old Lenovo laptop which was four years old and got heated very fast.

---

### Post by kromaz on 2013-11-02
Install went awesome! (Ubuntu 12.04.3 LTS) It did default to 2D, may try the Xfce down the road. For the most part everything running smooth. Only slow down Ive seen is the web browser (Firefox) with flash player. Crazy how a web browser can use so many resources, wish flash would go goodbye and HTML5 take over. Again want to thank the community for all the help during this process. As I learn Linux I will have plenty of questions to post. Talk to you all soon, off to learning Linux! :D

---

### Post by Petro Dawg on 2013-11-02
You might try other browsers to see if they perform a little more to your liking.  I personally use [Google Chrome]("https://www.google.com/intl/en/chrome/browser/?&brand=CHMB&utm_campaign=en&utm_source=en-ha-na-us-sk&utm_medium=ha"), but there are many alternatives, some lighter than others.  

Also, did you check if there are additional drivers available for your on-board graphics?

---

### Post by kromaz on 2013-11-02
> **Petro Dawg said:**
> You might try other browsers to see if they perform a little more to your liking.  I personally use [Google Chrome]("https://www.google.com/intl/en/chrome/browser/?&brand=CHMB&utm_campaign=en&utm_source=en-ha-na-us-sk&utm_medium=ha"), but there are many alternatives, some lighter than others.  

Also, did you check if there are additional drivers available for your on-board graphics?

Ive been a long time fan of Firefox. Tried chrome didn't care for it much, but hey may try chrome again to compare the performance in Linux. The ATI X800 Pro is a AGP card not on-board and didn't have any additional drivers.

---

### Post by Bucky Ball on 2013-11-02
Nice to hear everything went well. You can mark this thread as solved by following the instruction in my signature.

Enjoy the OS, the forums and the learning curve. ;)

---

### Post by newb85 on 2013-11-02
> **Bucky Ball said:**
> No! Why do people always give this advice??? This drags in ALL of Xubuntu, default apps, dependencies, the LOT. You DON'T want that, especially on an older machine that is already struggling for air. You ONLY want the desktop environment, xfce4, as suggested in the first command. 

If you are going to install xubuntu-desktop, you may as well do a clean install of Xubuntu because you are basically doing one ON TOP of the existing Ubuntu install. BAD idea. Your menus will contain ALL default apps for both Ubuntu AND Xubuntu. You definitely don't need that clogging up an already struggling system. 

Please peoples, if someone wants to try a different desktop environment, DON'T advise them to install *buntu-desktop anything. xfce4, lxde ... just the desktop environment. If they want to try a new DE, advising them to install *buntu-desktop to do it is the WRONG advice. 

Rant complete. Thankyou. Carry on. ;)

Um...that was kind of the point.  I presented multiple options.  One was for only bringing in the DE, and one was for default apps, too.  Depending on what is limited in the old hardware, users may need to switch to the lighter applications.  Having those extra applications will only burden their system if they run both simultaneously.  (Unless, that is, their biggest limit is HDD space.)  In many cases, they're best off having different options, trying them, and then removing (if they want) the ones they don't want.

---

### Post by deadflowr on 2013-11-02
> **anthonypineiro said:**
> The ATI X800 Pro is a AGP card not on-board and didn't have any additional drivers.

And no doubt you wouldn't have seen drivers for the card, as AMD dropped support for cards older then radeonhd5XXX series.
There is a workaround to get the fglrx-legacy drivers installed, but it is probably too much a bother to deal with, as who knows what kind of problems arise by doing so.
If the open-source drivers function well enough, no need to try and install a potentially damaging workaround.

---


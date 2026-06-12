---
title: "Whats the lightest (fastest) version of Ubuntu?"
date: 2010-04-19
forum: Recurring Discussions
---

### Post by schwabdale on 2010-04-19
Please post!

---

### Post by seenthelite on 2010-04-19
Lightest is lubuntu.

[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by MorleyPotter on 2010-04-19
There are some comparisons [here]("http://penguininside.blogspot.com/2009/08/not-just-ubuntu-go-for-variants.html"). I have used Kubuntu on an old machine and it was fine if that is what you are trying to do?

---

### Post by thebigob on 2010-04-19
Server edition:

practically no overheads

---

### Post by neur0 on 2010-04-19
In my experience:
CrunchBang

---

### Post by snowpine on 2010-04-19
A minimal install: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Then, add only what you need.

---

### Post by skymera on 2010-04-19
Ubuntu 7.04 in my opinion.

---

### Post by Objekt on 2010-04-19
Ubuntu Studio has a "real time" kernel, which is supposed to dramatically reduce or eliminate video and audio latency.  I've been wondering whether this would be of benefit to Linux gaming as well.

I've tried playing Urban Terror 4.1 under my Ubuntu 9.10 install, but there's just a wee - but noticeable - bit of latency in the display.  It's impossible to measure, but the video just isn't quite as snappy as it is under Windows XP.

Could I perhaps install just the kernel from Ubuntu Studio?  I don't want to do a complete reinstall just to test the realtime kernel.  But, I'm wondering whether the Studio kernel is different enough that it would break some of my existing software.

---

### Post by snowpine on 2010-04-19
> **Objekt said:**
> Ubuntu Studio has a "real time" kernel, which is supposed to dramatically reduce or eliminate video and audio latency.  I've been wondering whether this would be of benefit to Linux gaming as well.

I've tried playing Urban Terror 4.1 under my Ubuntu 9.10 install, but there's just a wee - but noticeable - bit of latency in the display.  It's impossible to measure, but the video just isn't quite as snappy as it is under Windows XP.

Could I perhaps install just the kernel from Ubuntu Studio?  I don't want to do a complete reinstall just to test the realtime kernel.  But, I'm wondering whether the Studio kernel is different enough that it would break some of my existing software.

You can install the real time kernel like this:

```
sudo apt-get install linux-rt
```

Reboot and choose the linux-rt kernel from your Grub menu. Your previous kernel will still be available from Grub, so you can switch between them each time you boot, depending on your needs. It is unlikely that installing the real time kernel will "break" anything. :)

---

### Post by Objekt on 2010-04-19
Thanks, I'll give that a try. 

My kernel list @ boot time is getting way too long.  Now I get to learn how to reconfigure that in GRUB2.  Yay.

---

### Post by Kai69 on 2010-04-19
My kernel list was long as well I used ubuntu tweak to get rid of the older kernels 
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)  once its installed just use package cleaner to get rid of the old kernels on your boot list

---

### Post by Objekt on 2010-04-19
The realtime kernel (2.6.31-9-rt) seems to have done the trick for me.  Urban Terror 4.1 doesn't have that little bit of lag any longer.

Teamspeak 3 is also now usable, but that may be unrelated.  They just released a new version a couple of days ago, which may have been the fix.  Or it could be the realtime kernel.  Can't tell really.

I had a big problem installing the realtime kernel: at some point, my Gnu C Compiler (gcc) got upgraded to version 4.4.  That's no good, because Nvidia is still releasing Linux drivers that were compiled with gcc version 4.2.  So when you try to install them, it complains, in part like this:
```
The compiler used to compile the kernel was gcc 4.2; the current compiler is gcc 4.4 
```

I Googled the problem and found many others had this problem at one time or another, albeit mostly with different version numbers.  It seems Nvidia is slow to move to the new gcc version.

I never did get it fixed.  Although I reinstalled gcc-4.2 and made absolutely sure that it would be the version called, by replacing the symbolic link in /usr/bin, the Nvidia package still thought I was using gcc-4.4.  No idea why.  In the end, I overrode the warning & compiled the kernel modules anyway.  So far everything is working, so I guess the kernel modules got compiled with gcc-4.2, as I thought would happen, in spite of the warning.

The weird thing is, I had no problem installing Nvidia kernel modules for the 2.6.33 kernel, after reinstalling gcc-4.2.  I didn't have to override any gcc compatibility warning in that case.  Again, no idea why.

---

### Post by themarker0 on 2010-04-19
> **snowpine said:**
> A minimal install: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Then, add only what you need.


This.

---

### Post by Shining Arcanine on 2010-04-20
> **Objekt said:**
> The realtime kernel (2.6.31-9-rt) seems to have done the trick for me.  Urban Terror 4.1 doesn't have that little bit of lag any longer.

Teamspeak 3 is also now usable, but that may be unrelated.  They just released a new version a couple of days ago, which may have been the fix.  Or it could be the realtime kernel.  Can't tell really.

I had a big problem installing the realtime kernel: at some point, my Gnu C Compiler (gcc) got upgraded to version 4.4.  That's no good, because Nvidia is still releasing Linux drivers that were compiled with gcc version 4.2.  So when you try to install them, it complains, in part like this:
```
The compiler used to compile the kernel was gcc 4.2; the current compiler is gcc 4.4 
```

I Googled the problem and found many others had this problem at one time or another, albeit mostly with different version numbers.  It seems Nvidia is slow to move to the new gcc version.

I never did get it fixed.  Although I reinstalled gcc-4.2 and made absolutely sure that it would be the version called, by replacing the symbolic link in /usr/bin, the Nvidia package still thought I was using gcc-4.4.  No idea why.  In the end, I overrode the warning & compiled the kernel modules anyway.  So far everything is working, so I guess the kernel modules got compiled with gcc-4.2, as I thought would happen, in spite of the warning.

The weird thing is, I had no problem installing Nvidia kernel modules for the 2.6.33 kernel, after reinstalling gcc-4.2.  I didn't have to override any gcc compatibility warning in that case.  Again, no idea why.

Your lag was likely because the stock kernel is designed for servers, so it does not have things like kernel pre-emption enabled. The realtime kernel is overkill for your purposes, although I am not sure if Ubuntu has a regular kernel that is tuned for desktop users. It might be a good idea to compile your own kernel, as to my knowledge, the realtime kernel has high CPU overhead in comparison to a kernel tuned for desktop use.

---

### Post by mörgæs on 2010-04-20
I agree on the minimal installation. There is some advice here:

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

A long thread, but worth reading.

---

### Post by Objekt on 2010-04-20
Perhaps, only I don't have the slightest clue how to go about compiling my own kernel.  I wouldn't know where to even start.  Got links?

I did find an Ubuntu community doc on the topic ([https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")).  Perhaps it will be sufficient guidance.

---

### Post by Shining Arcanine on 2010-04-20
> **Objekt said:**
> Perhaps, only I don't have the slightest clue how to go about compiling my own kernel.  I wouldn't know where to even start.  Got links?

I did find an Ubuntu community doc on the topic ([https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")).  Perhaps it will be sufficient guidance.

That Ubuntu community documentation would probably be the best way to go. When you are in menuconfig, you will want to change the default settings to use TREE_RCU, CONFIG_NO_HZ, Timer frequency (1000 HZ) and Preemption Model (Preemptible Kernel (Low-Latency Desktop)). TREE_RCU is an option under RCU Subsystem under General setup. The rest can be found under Processor Type and Features.

Make sure that you set CONFIG_LOCALVERSION to some custom value so your custom kernel's modules will not overwrite those of the stock kernel.

Also, you can hit "/" to open a dialogue inside of menuconfig that will let you search. If you enter the names I provided, it should tell you exactly where to find them.

---

### Post by Shining Arcanine on 2010-04-20
> **mörgæs said:**
> I agree on the minimal installation. There is some advice here:

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

A long thread, but worth reading.

If you want a minimal OS, you probably are using the wrong distribution. I suggest you look at Gentoo Linux:

[http://www.gentoo.org/](http://www.gentoo.org/)

It is minimal by default.

---

### Post by juancarlospaco on 2010-04-20
*light test version of Ubuntu?*

---

### Post by Shining Arcanine on 2010-04-20
> **juancarlospaco said:**
> *light test version of Ubuntu?*

I realize that is what he asked, but the question is equivalent to asking, "what is the best hammer for installing a screw?". There are many varieties of hammers, but none of them are suited to installing a screw. In order to install a screw correctly, one needs to use a tool called a screwdriver, which is a different tool than a hammer.

In the same way a hammer is the wrong tool for a screw, Ubuntu and its derivatives are the wrong distributions for what the original poster wants, which is why I suggested looking at other distributions.

---

### Post by snowpine on 2010-04-20
> **Shining Arcanine said:**
> I realize that is what he asked, but the question is equivalent to asking, "what is the best hammer for installing a screw?". There are many varieties of hammers, but none of them are suited to installing a screw. In order to install a screw correctly, one needs to use a tool called a screwdriver, which is a different tool than a hammer.

In the same way a hammer is the wrong tool for a screw, Ubuntu and its derivatives are the wrong distributions for what the original poster wants, which is why I suggested looking at other distributions.

Curious how you know what the original poster wants? The question seems unambiguous to me. :)

---

### Post by Shining Arcanine on 2010-04-20
> **snowpine said:**
> Curious how you know what the original poster wants? The question seems unambiguous to me. :)

The words "lightest" and "fastest" should not appear with the word Ubuntu in the same sentence. Those two concepts often go together and Ubuntu is not meant to cater to either of them. You can modify/fork the distribution to try to address them, but by the time you are done, the distribution would be more closely related to Arch Linux than it is to Ubuntu Linux, at which point it probably would have been better to go with a minimalist distribution like Gentoo Linux from the start.

---

### Post by conradin on 2010-04-20
Depends on your hardware at least in part. Server edition would prolly be close. After that, if you removed all the kernel modules and other programs you were never going to use, you would have an optimized version of ubuntu for your specific hardware / uses. That was the idea with gentoo which to my knowledge is the fastest version of linux out there.

---

### Post by Shining Arcanine on 2010-04-20
> **conradin said:**
> Depends on your hardware at least in part. Server edition would prolly be close. After that, if you removed all the kernel modules and other programs you were never going to use, you would have an optimized version of ubuntu for your specific hardware / uses. That was the idea with gentoo which to my knowledge is the fastest version of linux out there.

Gentoo's approach is more fundamental than that in that it provides the concept of USE flags, which allow you to specify what features of various packages you want, so for example, you can install KDE without semantic-desktop or you can install hal without encryption support. Using USE flags, you can strip features out of software packages that you do not use, which is not possible when software is distributed in the form of compiled binaries.

That makes for a much lighter OS than you can get with Ubuntu, even if you go through the trouble of stripping everything out. Speaking of which, since Ubuntu is meant to have everything bundled, you could get into trouble down the road when some system upgrade expects something to be either installed that is not installed or configured in a way that it is not configured. Gentoo Linux makes no such assumptions, so Gentoo Linux users do not encounter those sorts of issues.

---

### Post by snowpine on 2010-04-20
> **Shining Arcanine said:**
> The words "lightest" and "fastest" should not appear with the word Ubuntu in the same sentence. Those two concepts often go together and Ubuntu is not meant to cater to either of them. You can modify/fork the distribution to try to address them, but by the time you are done, the distribution would be more closely related to Arch Linux than it is to Ubuntu Linux, at which point it probably would have been better to go with a minimalist distribution like Gentoo Linux from the start.

The question was "Whats the lightest (fastest) version of Ubuntu?" not "What's the lightest (fastest) Linux distro?" :)

I respectfully disagree with your opinion, anyway. :) I personally have found Ubuntu to be plenty fast on capable modern hardware, and some of its lightweight derivatives (CrunchBang is my favorite) to be fast even on modest hardware.

---

### Post by Shining Arcanine on 2010-04-20
> **snowpine said:**
> The question was "Whats the lightest (fastest) version of Ubuntu?" not "What's the lightest (fastest) Linux distro?" :)

I respectfully disagree with your opinion, anyway. :) I personally have found Ubuntu to be plenty fast on capable modern hardware, and some of its lightweight derivatives (CrunchBang is my favorite) to be fast even on modest hardware.
Have you tried a distribution that is meant to be lightweight from the start like Gentoo Linux? If you have not, you have never experienced such a distribution to have formed an opinion on the matter.

Yes, you can mutilate Ubuntu and get something that is relatively lightweight, but it will not be as lightweight as a distribution that is meant to be lightweight by design and it takes much less effort to get a lightweight distribution by using such a distribution in the first place.

This could probably be extended to my hammer and screw analogy, where by doing many strange movements with a hammer, it should be possible to install a screw, but the screw would have been tighter and it would have taken much less time to install it had you installed it by using a screwdriver instead of a hammer.

---

### Post by snowpine on 2010-04-20
> **Shining Arcanine said:**
> Have you tried a distribution that is meant to be lightweight from the start like Gentoo Linux? If you have not, you have never experienced such a distribution to have formed an opinion on the matter.

*sigh* Yes, I have tried dozens of Linux distros (including a few that make Gentoo look bloated) and I stand by my statement that the regular, Gnome desktop version of Ubuntu can be very fast on capable modern hardware. You are free to disagree with my opinion of course. :)

---

### Post by Shining Arcanine on 2010-04-20
> **snowpine said:**
> *sigh* Yes, I have tried dozens of Linux distros (including a few that make Gentoo look bloated) and I stand by my statement that the regular, Gnome desktop version of Ubuntu can be very fast on capable modern hardware. You are free to disagree with my opinion of course. :)

It seems that the issue here is being caused by differing preferences on how the "fast" attribute is attained. I prefer fast by default rather than fast by hacking, which is why I suggested Gentoo Linux. It seems that you are the reverse.

---

### Post by snowpine on 2010-04-20
> **Shining Arcanine said:**
> It seems that the issue here is being caused by differing preferences on how the "fast" attribute is attained. I prefer fast by default rather than fast by hacking, which is why I suggested Gentoo Linux. It seems that you are the reverse.

To what "hacking" are you referring? I have found Ubuntu to be fast "out of the box." 

I am not claiming it is "faster than Gentoo" but to claim "Ubuntu is not a screwdriver" is absurd. ;)

---

### Post by Tibuda on 2010-04-20
the minimal disk
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Shining Arcanine on 2010-04-20
> **snowpine said:**
> To what "hacking" are you referring? I have found Ubuntu to be fast "out of the box."

By hacking I mean stripping out software that is meant expected to be installed by default.

As for Ubuntu being fast "out of the box", I do not consider it to be such. The same goes for Ubuntu being light. Ubuntu takes roughly the same time Windows 7 takes to boot, and its memory footprint is comparable. With Gentoo Linux, both are a fraction of the former. To provide some figures, the time it takes to go from the screen's backlight flickering following a press of the power button when the system is in its off state to KDM displaying a login screen is approximately 15 seconds. With Ubuntu and Windows 7, this is roughly 30 seconds. System memory usage after logging into the system and opening a terminal to use free is approximately 200MB while Ubuntu and Windows 7 use much more than double of that. There are other metrics too, such as application load times, but those are the most profound.

---

### Post by snowpine on 2010-04-20
> **Shining Arcanine said:**
> By hacking I mean stripping out software that is meant expected to be installed by default.

As for Ubuntu being fast "out of the box", I do not consider it to be such. The same goes for Ubuntu being light. Ubuntu takes roughly the same time Windows 7 takes to boot, and its memory footprint is comparable. With Gentoo Linux, both are a fraction of the former. To provide some figures, the time it takes to go from the screen's backlight flickering following a press of the power button when the system is in its off state to KDM displaying a login screen is approximately 15 seconds. With Ubuntu and Windows 7, this is roughly 30 seconds. System memory usage after logging into the system and opening a terminal to use free is approximately 200MB while Ubuntu and Windows 7 use much more than double of that. There are other metrics too, such as application load times, but those are the most profound.

So if I understand you correctly, you are saying that, on your hardware, your optimized Gentoo install is roughly twice as fast as a "vanilla" Ubuntu install, and that Ubuntu's performance is roughly equal to Windows. Is that an accurate summary of your findings?

Even assuming your findings are typical, I still do not understand how they warrant your hammer/screwdriver analogy. At worst, it means unoptimized Ubuntu is no slower than the world's most popular operating system; at best, it means by switching to Gentoo, you save 15 seconds a day when you boot up your computer (time which can be quickly frittered away on Ubuntu Forums).

Please don't get the wrong idea here; I have nothing against Gentoo, and I don't currently use Ubuntu. :) I just want to be clear that, in my own personal experience, when run on modern hardware, Ubuntu is plenty fast enough for typical desktop use. I certainly did not experience the "wrong tool for the job" frustration that you claim (but I respect your opinion and experience).

ps My AntiX laptop uses 28mb of ram at startup; does that mean, at 200mb, Gentoo is bloated? ;)

---

### Post by Shining Arcanine on 2010-04-20
> **snowpine said:**
> So if I understand you correctly, you are saying that, on your hardware, your optimized Gentoo install is roughly twice as fast as a "vanilla" Ubuntu install, and that Ubuntu's performance is roughly equal to Windows. Is that an accurate summary of your findings?

Even assuming your findings are typical, I still do not understand how they warrant your hammer/screwdriver analogy. At worst, it means unoptimized Ubuntu is no slower than the world's most popular operating system; at best, it means by switching to Gentoo, you save 15 seconds a day when you boot up your computer (time which can be quickly frittered away on Ubuntu Forums).

Please don't get the wrong idea here; I have nothing against Gentoo, and I don't currently use Ubuntu. :) I just want to be clear that, in my own personal experience, when run on modern hardware, Ubuntu is plenty fast enough for typical desktop use. I certainly did not experience the "wrong tool for the job" frustration that you claim (but I respect your opinion and experience).

ps My AntiX laptop uses 28mb of ram at startup; does that mean, at 200mb, Gentoo is bloated? ;)

The answer to your question is yes. That is an accurate summary of my findings, although there is a bit more to it in practice than there is in theory.

For a laptop, those seconds are crucial, because the longer it takes to boot, the less convenient it becomes use your system as a reference while you are on the go. In such a context, the 15 seconds become much more important than most people would think at first glance.

By the way, I can modify Gentoo with a few simple commands to use about 25MB at startup and it would probably shave about 2 seconds off the system boot, however, that would mean that I would not have a X environment at boot. It is like that by default, so you could not say that Gentoo is bloated, but you could say that my specific instance of Gentoo is bloated, which is an opinion that other Gentoo users would likely share because I run KDE.

---

### Post by schwabdale on 2010-04-22
Thanks for all your replies! Maybe I should have been a little more clear. 
I was absolutely looking for a version of Ubuntu. As far as the lightest (fastest) version.... I think in 
terms of small installation, fast boot time, and pretty much just a GUI. 

It looks like from what everyone posted, the pyscocats website, Gentoo or Ubuntu server would be the way to go. 

Couple of questions though....

1. Does anyone know the install size of Ubuntu server?
2. Does anyone know a rough boot time of Ubuntu server?
3. If I download a Gentoo.iso file, does it have a GUI?
4. Does the post about the Pyscocats work with Lucid?

Thanks everyone!

---

### Post by snowpine on 2010-04-22
> **schwabdale said:**
> 1. Does anyone know the install size of Ubuntu server?
2. Does anyone know a rough boot time of Ubuntu server?
3. If I download a Gentoo.iso file, does it have a GUI?
4. Does the post about the Pyscocats work with Lucid?

1. No reason to do a Server install unless you actually plan to run a server. :)
2. Depends on your hardware...
3. Gentoo is very different from Ubuntu, it will take you a while to install for sure.
4. It should work in theory but keep in mind Lucid has not been released yet and there may be some small differences; I'm sure the Psychocats author will update the how-to once Lucid has a stable release. ;)

---

### Post by mörgæs on 2010-04-22
> **schwabdale said:**
> 
4. Does the post about the Pyscocats work with Lucid?


You can do a minimal install with older Ubuntus as well - there is no law of nature saying that the newest is best on all hardware. Just give them a try and see what works best for you.

I have a minimal 9.04 on a ten years old machine with 192 MB memory. Runs like a dream.

---

### Post by Objekt on 2010-04-22
I don't know about "lightest," but I believe I have found "fastest" as measured by "most responsive."  Using the realtime kernel is working out great for me.  I think if you're going to play 3D games under Ubuntu, the realtime kernel is almost a requirement.  The generic kernel seems to have some audio & video lag built in, even with Compiz and desktop effects turned off.

---

### Post by schwabdale on 2010-04-22
So is the Realtime Kernal make a system faster?

---

### Post by Objekt on 2010-04-23
> **schwabdale said:**
> So is the Realtime Kernal make a system faster?

I'm not sure what you're asking.

No kernel is going to magically increase the processing speed of your computer.  

However, using the realtime kernel can, in some cases, eliminate video or audio lag when running video- or audio-intensive applications.  In my case, the realtime kernel got rid of extra video lag in a 3D game.

---

### Post by Shining Arcanine on 2010-04-23
> **schwabdale said:**
> Thanks for all your replies! Maybe I should have been a little more clear. 
I was absolutely looking for a version of Ubuntu. As far as the lightest (fastest) version.... I think in 
terms of small installation, fast boot time, and pretty much just a GUI. 

It looks like from what everyone posted, the pyscocats website, Gentoo or Ubuntu server would be the way to go. 

Couple of questions though....

1. Does anyone know the install size of Ubuntu server?
2. Does anyone know a rough boot time of Ubuntu server?
3. If I download a Gentoo.iso file, does it have a GUI?
4. Does the post about the Pyscocats work with Lucid?

Thanks everyone!

Gentoo has no GUI by default. You will need to install it from the command line, pick the GUI that you want and install that too. If you insist on having a GUI environment while you do an installation, you could use either Gentoo 10.1 LiveDVD, which will boot into KDE by default (although installation is still done via the commandline) or the [Gentoo-based SystemRescueCD]("http://www.sysresccd.org/") that most Gentoo users use to install Gentoo Linux, which will allow you to start a lightweight window manager (Xfce I think) via startx.

My recommendation is to boot the SystemLiveCD, change the root password, make sure that the network connection is working, ssh into it from a remote PC and then follow the Gentoo Handbook's instructions remotely. A GUI environment will just waste system resources during installation.

If you want a lightweight desktop environment, I suggest you install LDXE via instructions from the unofficial Gentoo Wiki:

[http://en.gentoo-wiki.com/wiki/LXDE](http://en.gentoo-wiki.com/wiki/LXDE)

If you want things to be as fast as possible, I suggest you Gentoo's testing branch by following instructions at the official site:

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=3&chap=3#doc_chap1](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=3&chap=3#doc_chap1)

That will install OpenRC, which makes Gentoo a bit faster at booting, and all of the latest stable software from upstream, which tends to fix more bugs than it introduces. You will need to follow the OpenRC migration guide to do this. It can be done while you are installing Gentoo if you know what you are doing:

[http://www.gentoo.org/doc/en/openrc-migration.xml](http://www.gentoo.org/doc/en/openrc-migration.xml)

> **schwabdale said:**
> So is the Realtime Kernal make a system faster?

A realtime kernel will likely make your system slower. What do you intend to use it to do?

---

### Post by del_diablo on 2010-04-23
> [QUOTE]So is the Realtime Kernal make a system faster?

A realtime kernel will likely make your system slower. What do you intend to use it to do?[/QUOTE]

I think i undertstand the realtime kernel compared to the server kernel:
On a realtime kernel everything will be pushed trough at the fastest possible rate, meaning a very stable troughput and bit more resource useage.
The server edition runs a high latency variant, which means it will not get stable troughput BUT it will use less resources because of that.
The normal kernel is closer to the realtime than the server kernel, for the note.
So basically if you got the hardware for a realtimekernel(aka your not at the edge of what your system can handle under a normal kernel), then using the realtime one WILL give a performance boost from our point of view. I.E: A more stable FPS in games will look like a performance increase, while it under the hood uses more :P

---

### Post by smellyman on 2010-04-24
Crunchbang

---

### Post by schwabdale on 2010-04-24
Thanks for all the post! I think I am going to try all of the options and make a decision.

---


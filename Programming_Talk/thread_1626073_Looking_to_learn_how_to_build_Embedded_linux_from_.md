---
title: "Looking to learn how to build Embedded linux from rock bottom up"
date: 2010-11-19
forum: Programming Talk
---

### Post by andyzammy on 2010-11-19
I'm looking to learn the process to get a micro-processor (or even micro-controller) to boot the linux kernel (and so to run a linux OS).

I'm aware this forum isn't the ultimate resource on how to achieve this, but googling isn't getting me anywhere and i was kinda hoping someone would know a few places i could check out.

to give people an idea of what i'm after, here are some tutorials i'm working through:

[http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/Tutorial-A-simple-embedded-Linux-system/](http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/Tutorial-A-simple-embedded-Linux-system/)
[http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/Tutorial-Building-an-embedded-Linux-system-with-a-web-server/](http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/Tutorial-Building-an-embedded-Linux-system-with-a-web-server/)
[http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/Tutorial-A-web-kiosk-embedded-system/](http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/Tutorial-A-web-kiosk-embedded-system/)
[http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/Tutorial-An-ARMbased-web-kiosk-system/](http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/Tutorial-An-ARMbased-web-kiosk-system/)
[http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/Tutorial-Improving-an-embedded-Linux-system/](http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/Tutorial-Improving-an-embedded-Linux-system/)

I've done the 1st one up to the point of booting on a real machine. i've skimmed through the rest and I thought the answer would have been in the 4th paper, but it looks like the writer used a ready-made solution: the manufacturer of the board supply the software required to run the OS and the kernel loader (boot-strapper), but what i'm looking to do is a total and complete DIY.

I guess the tutorials concentrated more on getting the software packages onto the device and it's functionality rather than running the OS on the device - i'm very interested in both but to me it seems once you can boot the OS you can do the s/w too.

Any help will be appreciated with this

---

### Post by mmix on 2010-11-20
[http://wiki.openembedded.org/index.php/Main_Page](http://wiki.openembedded.org/index.php/Main_Page)

[http://www.scratchbox.org/](http://www.scratchbox.org/)

[http://cross-lfs.org/view/clfs-embedded/](http://cross-lfs.org/view/clfs-embedded/)

[http://kegel.com/crosstool/](http://kegel.com/crosstool/)
[http://ymorin.is-a-geek.org/projects/crosstool](http://ymorin.is-a-geek.org/projects/crosstool)

[http://yoctoproject.org/](http://yoctoproject.org/)


HTH

---

### Post by trent.josephsen on 2010-11-20
You won't learn how to build a computer from the Internet alone -- if that were possible, I wouldn't need a $50,000 education to get an entry-level job.  If you're interested in building embedded stuff as a career, you will almost certainly need a bachelor's in electronic or computer (hardware) engineering.

As a hobbyist, you might start with a microprocessor prototyping board of some sort, with (say) a low-power ARM processor.  Depending on how much you really want to know, you might start even lower with an Arduino-type device, and work your way up to something Linux will actually run on.

---

### Post by andyzammy on 2010-11-20
Thanks for your post!

Those look relevant to what i'm after, but even those links are to tasks that  are (in my eyes anyway) an intermediate stage of embedded development. These seem to concentrate on building up a working image, and while that is what i want to achieve in the long term, the first piece of code any u-processor runs on power up is at reset address (~0x00) - that's the place i want to start working, from the very lowest level (actually writing the bootloader myself). i am currently reading up on u-boot but would like to hear about others.

that being said though I have checked out the links and i already have a few questions about those (i'm just starting out with this all, and the sites are all built with the assumption that visitors to it have already got fully working knowledge)

it is obvious that there are a few routes to take when it comes to building an image for embedded: which distro should i use? angstrom vs openembedded vs cross lfs? even ubuntu?? i guess i'd learn the most from cross lfs so that'd be the ideal but possibly the learning curve would be a brick wall..

also why should i consider scratchbox or crosstool over gcc?

i realise this topic might be a little out of scope of ubuntuforums - are there any general mailing lists or IRC channels that would be better for this subject (with emphasis on the word general - i find mailing lists are extremely specific to certain subjects/hardware/sw and will discuss nothing else)

---

### Post by andyzammy on 2010-11-20
> **trent.josephsen said:**
> You won't learn how to build a computer from the Internet alone -- if that were possible, I wouldn't need a $50,000 education to get an entry-level job.  If you're interested in building embedded stuff as a career, you will almost certainly need a bachelor's in electronic or computer (hardware) engineering.

As a hobbyist, you might start with a microprocessor prototyping board of some sort, with (say) a low-power ARM processor.  Depending on how much you really want to know, you might start even lower with an Arduino-type device, and work your way up to something Linux will actually run on.

actually i've done just that. i've played with a LPC2k board and while i've found out how to write programs for it, i still don't know how to boot up linux on one. that's what the next step is for me. i have a beagleboard and i've run the demo angstrom image on it, which is a functional OS. like i said though, i'd like to DIY it all, from the ground up.

---

### Post by trent.josephsen on 2010-11-20
Boot loaders are pretty simple; all they do is transfer control to wherever the kernel is located.  As far as getting Linux on it, that boils down to cross-compiling everything you need and putting the kernel where the boot loader expects.  I'm not sure what else to say, not being familiar with the technology you're using.

There's a limit to how DIY you can get with Linux; after all, it's all somebody else's code.  (I'm thinking of someone I knew who wanted to learn Linux; I helped him install Gentoo and he was disappointed because there was no coding involved.  I guess he wanted to write all 13 million lines of code by himself.)

---

### Post by andyzammy on 2010-11-21
> **trent.josephsen said:**
> Boot loaders are pretty simple; all they do is transfer control to wherever the kernel is located.  As far as getting Linux on it, that boils down to cross-compiling everything you need and putting the kernel where the boot loader expects.  I'm not sure what else to say, not being familiar with the technology you're using.
I have no specific platforms in mind. I'd say my best bet is to stick with the beagleboard, as i already have one of those - and i can turn what i learn on that to other chips.

so my next steps now are to compile the u-boot bin for beagle, flash it on, compile the linux kernel and set up a FS on an SD card and stick kernel on it and power on.. 

if that is a success i take a look into the u-boot source used in the beagle and make appropriate changes to it for other chip architectures... right, i've got a rough idea of what needs to be done now.


> **trent.josephsen said:**
> There's a limit to how DIY you can get with Linux; after all, it's all somebody else's code.  (I'm thinking of someone I knew who wanted to learn Linux; I helped him install Gentoo and he was disappointed because there was no coding involved.  I guess he wanted to write all 13 million lines of code by himself.)

I kind of agree and disagree with that. It's not that I'm looking to "write" an OS, i just want to see if i can get one up and running on a chip nobody's tried it on before. otherwise all i'm doing is following instructions and to me that's not much of an achievement. I want to know what's involved in modifying existing software for new hardware - is it a case of just turning on a flag when compiling or do you have to jump right into the centre of the source code? if so that's very DIY to me.

I'm looking to learn linux too, i'm very new to it. I've found a few tutorials on the internet, but information overload, and i get bored easily and as i'm interested in electronics i thought i'd try it this way. to me it's the fastest way to see how linux works on all levels, giving me motivation to boot (pun not intended).

---


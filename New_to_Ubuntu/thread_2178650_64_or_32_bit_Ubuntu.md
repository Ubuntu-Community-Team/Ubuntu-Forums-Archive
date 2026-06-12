---
title: "64 or 32 bit Ubuntu?"
date: 2013-10-04
forum: New to Ubuntu
---

### Post by rami5 on 2013-10-04
Hey
I installed Ubuntu yesterday ( or day before yesterday ), 64 bit version.

However, some things are kinda slow.
- Startup is real quick! this is good
- Opening folders/ System Settings or the Software Center takes about 1 - 2 seconds

So, im kinda unsure if i chose the right version here.
Maybe i should have installed the 32 bit instead?
Did i make the wrong choice?

...
Machine: Toshiba Satellite L300 23K
Intel® Celeron(R) CPU 900 @ 2.20GHz
Newly installed 4 GB RAM ( although details say 3.7, how come? )
Newly installed 1TB SSHD hardisk
Graphics card unknown

---

### Post by Bucky Ball on 2013-10-04
Here's the specs for the processor:

[http://ark.intel.com/products/41498/Intel-Celeron-Processor-900-1M-Cache-2_20-GHz-800-MHz-FSB](http://ark.intel.com/products/41498/Intel-Celeron-Processor-900-1M-Cache-2_20-GHz-800-MHz-FSB)

It's 64bit. You have the correct version installed. ;)

Some of the RAM is used by the system. You can research for details of that. For your graphics card, open a terminal and:

```
sudo lshw -C video
```

That could be the issue, wrong or missing driver. Post the output back here please. 

For all your hardware details, you can:

```
lspci
```

Just thought I'd mention. Don't need that output though.

---

### Post by sudodus on 2013-10-04
I think you will have better results with a desktop environment with a lighter foot-print than standard Ubuntu with Unity. I saw in a review on the internet, that the computer is from 2009. Is that correct for your computer?

So I suggest that you try Lubuntu or Xubuntu. There are two ways to do it

1. Download an iso file of the desktop version of Xubuntu 12.04 LTS or Lubuntu 13.04

2. Install the corresponding desktop environments in Ubuntu and select which one to use at the login screen. Click on the round symbol near the password window (attachment).

```
sudo apt-get install lubuntu-desktop
```

```
sudo apt-get install xubuntu-desktop
```


It is possible to remove the desktops you don't want afterwards according to this link

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Bucky Ball on 2013-10-04
The above could work, but rather large leap for something that might be minor. A full install is a radical suggestion before we try anything or check the graphics. ;)

4Gb ram, 2.2 CPU? Should be able to handle this okay. But maybe not. I have Ubuntu running fine on less than that (1Gb RAM, 3mHz CPU, and I'm not alone).

Incidentally, you do NOT want to install *buntu-desktop. That drags in EVERYTHING! All apps, dependencies, the lot, for Xubuntu or Lubuntu. This causes duplication and leaves your menus packed with stuff you'll never use. In effect you'll have the three versions installed and a mess.

Instead, install 'xfce4' (the desktop environment ONLY for Xubuntu) or 'lxde' (Lubuntu DE). Example:

```
sudo apt-get install xfce4
```

Then choose it  from the login screen as described by sududos above.

---

### Post by rami5 on 2013-10-04
OK
The utput is:
PCI ( sysfs )

And thanks for the hardware detail code ;)

---

### Post by Bucky Ball on 2013-10-04
How long did you wait? It takes a little while. Should have spat something out giving details of your graphics card ... odd.

---

### Post by rami5 on 2013-10-04
Thats just the thing, if i view Details, next to Graphics it says "Unknown"
I dont think the system recognizes the graphics card
Could that be the problem maybe?

Ill try one more and try to wait abit
sudo lshw -C video
right?

---

### Post by rami5 on 2013-10-04
Aha!
here it is, dono what happened the first time:

  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d3500000-d35fffff

EDIT: And yes, the computer s quite old. Ive made a hbby out of fixing up old computers i guess

---

### Post by sudodus on 2013-10-04
Intel graphics as desribed in the link I found for specs :-) It is not fast, but there should be no particular issues. I suggest you try lighter desktops. Do it the way you want, and wipe duplicates according to the the psychocats link (in post #3) when you know what you want. It might also be possible to tweak the Ubuntu Unity desktop to make it more responsive.

---

### Post by rami5 on 2013-10-04
I see
Thanks for helping me out with this

Could the problem be that the system does not recognize the Graphic card ( because it says Graphics Unknown in details )?
Maybe it would help to reinstall the drivers?

Couldnt i just install a new OS from a cd instead of installing stuff ontop of eachother?

---

### Post by Bucky Ball on 2013-10-04
** Just saw your last post: YES, install a lighter OS, Xubuntu or Lubuntu. There are lighter but start there. You could try out if that's going to help by installing JUST the desktop environments, as described. 'sudo apt-get install xfce4'. Below is what I wrote before I saw your post. Hopefully it's of interest anyway. ;)

> **sudodus said:**
> Intel graphics as desribed in the link I found for specs :-) It is not fast, but there should be no particular issues. 

Yep. Agreed. Everything seems to be fine but slow. And now we know the graphics card, that would no doubt be the reason.

If you install '*buntu-desktop' you can weed out duplicates as described in the link or, to avoid getting them in the first place (and a whole bunch of other stuff you don't see but don't want/need) and save some time and possible headaches, just install the desktop environments, as described in my other post ('sudo apt-get install xfce4' in a terminal then log out and choose from 'Sessions' at the login screen, replace 'xfce4' with 'lxde' for the other). ;) 

Good luck. A lighter desktop environment should make a difference.

PS: As you've just installed, if you are going down the installing the '*buntu-desktop' track you may as well just do a clean install of Xubuntu or Lubuntu as by doing it that way you're basically doing the same thing ... except on top of a Ubuntu install. You have light specs already so you really don't want that. Even though you have installed a lightweight desktop you would have basically installed another operating system and it may slow things down anyway (cause unpredictable). 

As you're into refurbishing old hardware, as you get into it you will find all sorts of interesting ways to create feather-light installs which should run great. The mini.iso will be of interest to you, but maybe once you get your feet wet:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Basically, you get the kernel and that's it. You decide on the apps and desktop environment. Once you have a basic, lightweight 'template' ISO, you can create your own install disk from it and just bang that on to your next rebuild for a starting point and build from there as you go. Spoilt for choice! ;)

---

### Post by King Dude on 2013-10-04
Yeah, you installed the correct version. If you tried putting a 64bit OS on a computer with a 32bit CPU, the operating system would most likely give you an error when you try to install it. And even if you did manage to install a 64bit OS on a 32bit system somehow, you wouldn't be able to start up the operating system period.

---

### Post by Bucky Ball on 2013-10-04
> **King Dude said:**
> Yeah, you installed the correct version. If you tried putting a 64bit OS on a computer with a 32bit CPU, the operating system would most likely give you an error when you try to install it. And even if you did manage to install a 64bit OS on a 32bit system somehow, you wouldn't be able to start up the operating system period.

We're a long way from there now. ;)

---

### Post by whitesmith on 2013-10-04
> **rami5 said:**
> Couldnt i just install a new OS from a cd instead of installing stuff ontop of eachother?Yes, and it's often easier, unless the CD lacks essential drivers or wanted features.

---

### Post by rami5 on 2013-10-04
Hmmm, i came acrss something interestin.
The tec specs on Toshibas homepages say that the cmputer comes preinstalled with **Windows Vista 32 bit**

[http://translate.google.com/translate?hl=en&sl=no&u=http://www.toshiba.no/discontinued-products/satellite-l300-23k/&prev=/search%3Fq%3Dtoshiba%2Bdiscontinued%2Bsatellite%2Bl300%2B23k%26client%3Dubuntu%26hs%3DDfC%26channel%3Dfs%26biw%3D1280%26bih%3D642](http://translate.google.com/translate?hl=en&sl=no&u=http://www.toshiba.no/discontinued-products/satellite-l300-23k/&prev=/search%3Fq%3Dtoshiba%2Bdiscontinued%2Bsatellite%2Bl300%2B23k%26client%3Dubuntu%26hs%3DDfC%26channel%3Dfs%26biw%3D1280%26bih%3D642)

Desnt this mean that i should be using the 32 bit versin of Ubuntu, and that that may be the problem?

---

### Post by philinux on 2013-10-04
Since ubuntu is free try both.  :P

---

### Post by DuckHook on 2013-10-04
Windows purposefully hobbled their "home" versions of software by making them only 32-bit. Also, there was a maximum limit of CPUs and a maximium limit to addressable memory. Linux has never done that (another of the many reasons that I like Linux so much). Just because your Vista was 32-bit does not mean that your system was only capable of 32-bit. In fact, it is likely that this was a purely artificial MS limitation designed to force you to buy "professional" licenses.

But I agree with *philinux*. For the cost of a download, you can try both and see.

---

### Post by 3rdalbum on 2013-10-05
> **rami5 said:**
> Hmmm, i came acrss something interestin.
The tec specs on Toshibas homepages say that the cmputer comes preinstalled with **Windows Vista 32 bit**

[http://translate.google.com/translate?hl=en&sl=no&u=http://www.toshiba.no/discontinued-products/satellite-l300-23k/&prev=/search%3Fq%3Dtoshiba%2Bdiscontinued%2Bsatellite%2Bl300%2B23k%26client%3Dubuntu%26hs%3DDfC%26channel%3Dfs%26biw%3D1280%26bih%3D642](http://translate.google.com/translate?hl=en&sl=no&u=http://www.toshiba.no/discontinued-products/satellite-l300-23k/&prev=/search%3Fq%3Dtoshiba%2Bdiscontinued%2Bsatellite%2Bl300%2B23k%26client%3Dubuntu%26hs%3DDfC%26channel%3Dfs%26biw%3D1280%26bih%3D642)

Desnt this mean that i should be using the 32 bit versin of Ubuntu, and that that may be the problem?

No. As explained to you earlier, your system is 64-bit capable. It doesn't matter if your computer came with a 32-bit operating system, 16-bit operating system, or 8-bit operating system: It's suitable to run a 64-bit operating system. Besides, you've got 4 gigs of RAM in the computer, you need 64-bit in order to actually address it all.

Also, I'm having difficulty determining what your problem actually is. 1-2 seconds to start a program (the file browser is a program) is normal on a computer like yours - it's a bit low-end, although certainly good enough to run Ubuntu. Your graphics card is an Intel, which means it works out-of-the-box (don't worry that the Details thing says "Unknown", if it's an Intel graphics chip it is most certainly known and already fully in use).

Are you having any other issues?

---

### Post by grier-devon on 2013-10-05
> **rami5 said:**
> Hmmm, i came acrss something interestin.
The tec specs on Toshibas homepages say that the cmputer comes preinstalled with **Windows Vista 32 bit**

[http://translate.google.com/translate?hl=en&sl=no&u=http://www.toshiba.no/discontinued-products/satellite-l300-23k/&prev=/search%3Fq%3Dtoshiba%2Bdiscontinued%2Bsatellite%2Bl300%2B23k%26client%3Dubuntu%26hs%3DDfC%26channel%3Dfs%26biw%3D1280%26bih%3D642](http://translate.google.com/translate?hl=en&sl=no&u=http://www.toshiba.no/discontinued-products/satellite-l300-23k/&prev=/search%3Fq%3Dtoshiba%2Bdiscontinued%2Bsatellite%2Bl300%2B23k%26client%3Dubuntu%26hs%3DDfC%26channel%3Dfs%26biw%3D1280%26bih%3D642)

Desnt this mean that i should be using the 32 bit versin of Ubuntu, and that that may be the problem?

No, I had a HP desktop with 4 GB of memory and a quad core AMD CPU and the computer came with Vista 32 Bit, a system very capable of running 64 Bit and would have seen benefits from the CPU on a 64 Bit OS.

---

### Post by Bucky Ball on 2013-10-05
> **rami5 said:**
> 

Desnt this mean that i should be using the 32 bit versin of Ubuntu, and that that may be the problem?

Short answer? No. Irrelevant. I have provided a link to the specs for the processor already. It is a *_64bit processor_*.

---

### Post by asifnaz on 2013-10-05
If you don't have any specific needs for 64 bit . I would recommend 32 bit

---

### Post by rami5 on 2013-10-05
Hmmm, ill install the 32 bit in a minutte just to compair

What would be my potential loss and gain by switching from 64 bit OS to 32 bit OS?
My guess would be
- Cant run certaing 64 bit Software
+ Os is quicker/ more responsive in general

---

### Post by 3rdalbum on 2013-10-05
> **rami5 said:**
> Hmmm, ill install the 32 bit in a minutte just to compair

Don't bother unless you really have nothing else to do with your time; it's exactly the same as the 64-bit distro, just compiled to the x86 instruction set instead of the amd64 instruction set.

> What would be my potential loss and gain by switching from 64 bit OS to 32 bit OS?
My guess would be
- Cant run certaing 64 bit Software
+ Os is quicker/ more responsive in general

No. 64-bit is faster for intensive operations involving high-precision numbers, such as video encoding. Maybe even video decoding. 64-bit is also optimised for later CPUs, and there are a couple of security features that can be used in 64-bit CPUs that can't be used in many 32-bit CPUs (and so are turned off for all 32-bit CPUs).

32-bit uses slightly less RAM (not a major concern when you have 4 GiB of RAM, it's not like you'll get anywhere close to using it all), and there's literally one or two packages that can't be used in 64-bit. Nothing major.

The difference between 32-bit and 64-bit is not noticeable unless you benchmark the two together, but you might as well have the speed and security improvements of 64-bit.

---

### Post by vasa1 on 2013-10-05
I searched the site using "32 64 bit site:ubuntuforums.org" in Google Search. I got the following results on the first page:

[Why is 32 bit (recommended) vs 64 bit Ubuntu]("http://ubuntuforums.org/showthread.php?t=2089495")
[32-bit or 64-bit? 12.04.1 or 12.10?]("http://ubuntuforums.org/showthread.php?t=2077173")
[Install 32-bit or 64-bit ubuntu 12.04]("http://ubuntuforums.org/showthread.php?t=1992810")
[32Bit vs 64Bit]("http://ubuntuforums.org/showthread.php?t=2174701") and, in this thread, take a look at [http://ubuntuforums.org/showthread.php?t=2174701&p=12789977#post12789977](http://ubuntuforums.org/showthread.php?t=2174701&p=12789977#post12789977)
Incidentally, they're all in "**Recurring Discussions**".

---

### Post by oldfred on 2013-10-05
When I saw title I was ready to move this thread right next to the hundreds of other threads in recurring Discussions that have the same question answered.
But then I saw it was discussing other install issues and seemed less like the the 32 vs 64 bit discussions. 
But if back to rehashing that old issue, I will move it.

---

### Post by rami5 on 2013-10-05
Great

I now have 2 cds, 32bit and 64bit Ubuntu.
However...

How can i format the hardisk ( 1TB SSHD ) in Ubuntu?
Or more importaintly, what fileformat should i use when formating?

---

### Post by oldfred on 2013-10-05
I prefer to partition in advance with gparted, but you can do it during install.
Any of these examples with screenshot that also show Windows can be ignored it you do not have Windows. But still show install process.

 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)



 Install with screen shots:
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu - Post #6 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by rami5 on 2013-10-05
...The world just got more complicated...
Im totally confused

Iv tried reading up on some of this stuff, but i think i need to give it some more time

...
I know Windows uses FAT32 and NTFS
OSX ( Mac ) used HFS+
Theres also the ext2 - 4 which i have never heard of
I also understand that its not this black and white :)

I thought it would be like a relatively short list of options, and one of them would be the best:

- A
- B
- C <( relativey best file system for you my man! )
- D
- E

Oh well, silly me :P
Although i like learning, i dono what to do at this point

---

### Post by DuckHook on 2013-10-05
I hope you don't mind my saying this, but you are making things needlessly difficult on yourself. One hint should be the fact that forum moderators like Bucky Ball have recommended 64-bit. He knows what he is talking about. So do all forum mods/admins.

Different operating systems have different file systems. Ubuntu uses ext4, which in my opinion is better than the others, but I won't argue with those who have a different opinion. The point is that you don't want to install any other file systems unless you are prepared to make your system far more complex that it needs to be, so use the default ext4.

Last but not least, I am an "old-hardware" geezer who really likes to take computers that others consider obsolete, and raise them from the dead. You haven't given us that much info on your system, but based on what others have researched, it appears that it isn't that powerful. Combined with your initial posting indicating that what prompted you to post was perceived slowness, I highly recommend that you install Lubuntu instead of trying to fuss with and optimize Ubuntu.

Repeat: just install Lubuntu 64-bit with all of its defaults (including ext4) and you will be free thereafter to explore the nooks and crannies of Linux at your leisure.

---

### Post by rami5 on 2013-10-05
No i dont mind you saying so at all :)
In fact its made my decission all the more easier

So Lubuntu 64bit it is then!\\:D/ 			

A sincere thanks for all the help people, guess ive got alot to learn still

---

### Post by rami5 on 2013-10-06
Thanks a bounch everyone!
I think ive found my mate, Lubuntu.

Before i did all this up/ down grading, i decided to make a test of sorts, to see how the different setups would affect my performance.
I decided to consider 2 things for the test:
- How responsive/ how fast i could open folders
- How fast GIMP would tae to "oilify" ( filter effect ) a big picture

Ubuntu 64 bit
- Home folder took 1 - 3 seconds to open
- GIMP applied filter in 3:30 seconds

Ubuntu 32 bit
- Home folder took 1 - 3 seconds to open ( maybe a tad faster, but nothing significant )
- GIMP applied filter in 4:20 seconds

Lubuntu 64 bit
- Home folder opens almost instantly ( 0.5 sec )
- GIMP applied filter in 3:30 seconds

...
Im in no way an expert in any of this
But my conclusion is:
- Going down to 32 bit didnt seem to do much good ( image filtering only took longer to process, which is a drawback ).
- The OS seemed to be the general culprit, or my specs/ hardware, depending on how you look at it
Hopefully this will serve as help to others in the same situation

I personally think Lubuntu has a much cleaner look than Ubuntu, and in my case its more responsive as well.
Ubuntu reminds me more of OSX while Lubuntu looks and feels more like Windows, if one could make that comaprrison.

Thanks to all ov ya ive ended up with what i think is the best solution for my situation!
:popcorn:

---

### Post by Bucky Ball on 2013-10-06
> **rami5 said:**
> ... in my case its more responsive as well.


Lubuntu is more responsive for everyone because it's lightweight (I run Xubuntu on an i3 with 4Gb RAM and it flies). 

Great news you found something to suit. Good luck and enjoy! ;)

---


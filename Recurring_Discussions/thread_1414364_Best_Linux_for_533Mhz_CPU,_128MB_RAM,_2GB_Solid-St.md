---
title: "Best Linux for 533Mhz CPU, 128MB RAM, 2GB Solid-State Harddrive"
date: 2010-02-23
forum: Recurring Discussions
---

### Post by Colten on 2010-02-23
So I got a really cheap netbook for on-the-go. It came packaged with Windows CE, and I feel that Linux would make better-use of the the limited hardware.

Specs:
533Mhz Processor
128MB RAM
2GB Solid-State Harddrive (Expanded with 4GB SD Card)

So far Im liking [Vector Linux Lite]("http://vectorlinux.com/"), but figured Id make a topic as you guys have way more knowledge on Linux than I do - Ive only been using Ubuntu for a month or two as a secondary boot on my desktop. If it helps, Im a fan of [LXDE]("http://lxde.org/").

---

### Post by azagaros on 2010-02-23
a Linux kernel and xwindows... I wouldn't load gnome or kde... they would be too much for that box and depending on the graphics array it had.  This is all of the current versions of this stuff at least.

At one time I had linux and xwindows on a 486-100 and it ran fine but that was before resource intensive Desktops of gnome and KDE.

I hope this sheds some light on what you are trying to do.

---

### Post by kerry_s on 2010-02-23
debian lxde, i'm using it on 450mhz 256mb ram.
just grab the net installer, at the boot screen arrow down to alternative desktops, then select lxde. you'll have to do some trimming after install, which is easy enough once you get synaptic, but other then that it's fairly bare bone.

---

### Post by Colten on 2010-02-23
Ok Ive run into a problem. I forgot that the Windows CE OS is embedded into my computer. I dont see how Id be able to remove/replace it for Linux. Theres no way to like... kill it? :(

---

### Post by kerry_s on 2010-02-24
> **Colten said:**
> Ok Ive run into a problem. I forgot that the Windows CE OS is embedded into my computer. I dont see how Id be able to remove/replace it for Linux. Theres no way to like... kill it? :(

how did you run vector lite?

---

### Post by ubunterooster on 2010-02-24
U-lite or puppy I prefer.
Can you enter Bios? Select the USB drive you have the Linux OS on to boot off of.

---

### Post by Colten on 2010-02-24
> **kerry_s said:**
> how did you run vector lite?

Im not, but I can see how you would get that from the way I worded it. I just meant that I was interested in Vector Lite

---

### Post by ayenack on 2010-02-24
You know you can install LXDE on ubuntu.

```
sudo apt-get install lxde
```

Not sure how it runs or how well it's supported.

Edit:-

After that you could trim down the system. You could also use the Ubuntu  Minimal Install (net-install) and build a lite system that way installing LXDE desktop along the way.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) (These are the Minimal Install images.)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) (Scroll down to Minimal Instalation and have a look at the three options. Might be good for you.)

---

### Post by snowpine on 2010-02-24
Tons of great information on these new low-cost netbooks here:

[http://ubuntuforums.org/showthread.php?t=1349626](http://ubuntuforums.org/showthread.php?t=1349626)

Sounds like installing Linux is an advanced project for sure, good luck! :)

---

### Post by ayenack on 2010-02-24
OK. Just installed LXDE on a Mac PowerBook PPC G4 12", 1.5GHz CPU, 1.25GB memory and I can say that it runs very very very quick indeed. So I'd guess it's be fine on your system. It seems really very lite indeed.

If you want to go the Ubuntu way then I'd say use Minimal Install and LXDE I reckon it'll be a winner.

---

### Post by eriktheblu on 2010-02-24
My laptop runs a full Ubuntu install but with LXDE. It eats about 80MB of system RAM idle. With only 128, you'll probably want something lighter.

Masonux might be an option.

---

### Post by theaveng on 2010-02-24
I run Windows XP on 128 MB.  Works great.

Puppy Linux will also work, since it only needs 32 MB and you've got four times that amount.

---

### Post by jrusso2 on 2010-02-24
You guys are not paying attention.  He is running Windows CE which is for an ARM processor and its embedded in ROM.

Not an easy thing to change and Intel Linux won't run on it.

---

### Post by Sven6210 on 2010-02-24
If you are running a x86 CPU I suggest you have a look at 'Damn Small Linux'.
 
For details please see [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/) or [http://en.wikipedia.org/wiki/Damn_Small_Linux](http://en.wikipedia.org/wiki/Damn_Small_Linux)
 
But as 'jrusso2' mentioned above you probably have an ARM CPU (running with Windows CE) - and getting Linux to work on an ARM CPU probably requires some very good Linux knowledge. I wouldn't know how to do it.

---

### Post by ubunterooster on 2010-02-24
> **ubunterooster said:**
> 
Can you enter a Bios? Select the USB drive you have the Linux OS on to boot off of.

google's droid os runs on ARM.

---

### Post by 3rdalbum on 2010-02-24
I don't think you can change the operating system on it... at least not easily. You'd also need an ARM build of whatever distro you wanted. Ubuntu and Debian have them, but the specialty lightweight distros like Puppy and DSL do not.

I think you're stuck with Windows CE, or you could get a more capable netbook with an x86 processor.

---

### Post by ubunterooster on 2010-02-24
I say strip down debian

---

### Post by theaveng on 2010-02-25
> **jrusso2 said:**
> He is running Windows CE which is for an ARM processor    You don't know that.  It could be an Intel CPU.

---

### Post by kwacka on 2010-02-25
Debian has an ARM port (if it is ARM). Download their 'netinstall' cd for ARM or intel and boot from that to install via internet.

If you let us know the name/model of the netbook we may be able to point you in a more appropriate (if there is one!)  e.g. the 'small laptop forum at [http://preview.tinyurl.com/yl93h4m](http://preview.tinyurl.com/yl93h4m) or [http://www.littlelinuxlaptop.com/](http://www.littlelinuxlaptop.com/)

---

### Post by hiflyer780 on 2010-02-25
try xubuntu maybe? it's made for slower computers

---

### Post by kwacka on 2010-02-25
Unfortunately Xubuntu (despite it's reputation) is only marginally less resource-hungry than K/Ubuntu.

LXDE is much lighter.

---

### Post by Sir Jasper on 2010-02-25
Hi hiflyer,

I am delighted with Xubuntu on my old (and only) 1998 computer, but I do not think 128 MB RAM would be enough for it to run sweetly (or perhaps even at all).

I remember reading about one high flyer who was reported to be more of a glider than jet-propelled.

My regards

PS The comment just amused me. It is not meant to be nasty.

---

### Post by Colten on 2010-02-25
> **kwacka said:**
> Debian has an ARM port (if it is ARM). Download their 'netinstall' cd for ARM or intel and boot from that to install via internet.

If you let us know the name/model of the netbook we may be able to point you in a more appropriate (if there is one!)  e.g. the 'small laptop forum at [http://preview.tinyurl.com/yl93h4m](http://preview.tinyurl.com/yl93h4m) or [http://www.littlelinuxlaptop.com/](http://www.littlelinuxlaptop.com/)

Delstar DS700

---

### Post by snowpine on 2010-02-25
> **Colten said:**
> Delstar DS700

Looks like Windows CE is embedded in ROM and you cannot easily replace it with Linux, sorry. :(

---

### Post by cabbrick1243 on 2010-08-20
I sadly got one of these last Christmas :( and have been looking to make it run linux ever since.  I have found that there is a way to get it to boot somewhat from the sd card using the update instructions on Delstar's website (its for a youtube update).  I had also read that google droid os does suppourt this processor in this device (a Samsung Arm... forgot the exact model #).  I have no clue as to how to compile android though so :(

---

### Post by bodhi.zazen on 2010-08-20
Moved to recurring discussions.

---

### Post by Naitsirhc Hsem on 2010-08-20
If you can figure out how to put it on, try slitaz, slitaz.org

---

### Post by liquidfunk on 2010-08-20
> **ayenack said:**
> OK. Just installed LXDE on a Mac PowerBook PPC G4 12", 1.5GHz CPU, 1.25GB memory

Which distro do you run on your PowerPC?

---


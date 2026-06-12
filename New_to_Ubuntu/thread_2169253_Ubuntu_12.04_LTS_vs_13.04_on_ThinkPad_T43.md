---
title: "Ubuntu 12.04 LTS vs 13.04 on ThinkPad T43"
date: 2013-08-21
forum: New to Ubuntu
---

### Post by nedzad2 on 2013-08-21
Hello,

I'm new here and I'm want to install ubuntu on my old ThinkPad T43 (my secondary computer). As the title says, I want to know what works best on my laptop. My biggest concern is that my Intel Graphics won't work. I will post specs down below, thanks in advance. :)

IBM ThinkPad T43: 

CPU:  Intel Pentium M 750 1866 MHz
RAM: 1272 MBytes, 266.0 MHz
Chipset: i915GMS/i910GML
GPU: Mobile Intel 915GM/GMS,910GML Express Chipset Family
HDD: FUJITSU MHV2060AH ATA  56 GB

If you'll need more specs I'll post them here.

P.S And yes I know that 12.04 got support till 2017 and if I get 13.04 I'll need to upgrade 9 months after the release.

---

### Post by Cheesemill on 2013-08-21
How about downloading them both and trying them out in live mode to see if your hardware works with both of them.

Also you don't need to worry about Intel graphics. Intel is very good at providing open-source drivers and everything you need is already built in. The most problematic hardware is usually wireless drivers but by booting from a Live CD you can check if yours works before committing to an installation.

---

### Post by nedzad2 on 2013-08-21
Good idea I'll try it, I'm using a usb wireless adapter which is the TP-Link [COLOR=#000000]WN321G and according to this [/COLOR]guide ([http://nlpdotnet.com/Blog/2012/9/24.aspx](http://nlpdotnet.com/Blog/2012/9/24.aspx)) 12.04 has a built in driver for the TP-Link, so if the 12.04 has a driver built in, 13.04 should also. Right? Also thanks. :)

---

### Post by grahammechanical on 2013-08-21
You might want to read this post

[http://ubuntuforums.org/showthread.php?t=1975422](http://ubuntuforums.org/showthread.php?t=1975422)

My attention was drawn to it by this in your specifications

> CPU:  Intel Pentium M 750 1866 MHz

You may need a version of Ubuntu that uses a non-pae kernel. The Pentium M does not support Physical Address Extensions (PAE) according to this link.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

> PAE is supported by Intel Pentium Pro and later Pentium-series processors except most 400 MHz-bus versions of the [Pentium M]("http://en.wikipedia.org/wiki/Pentium_M")

Standard Ubuntu versions expect a CPU to support PAE and will not run on a CPU that does not support PAE. You need to check that your CPU has support for PAE which is designed to allow the CPU to address more than 4GB of RAM.

Regards.

---

### Post by MrSteve on 2013-08-21
your CPU: Intel Pentium M 750 1866 MHz supports PAE 32 bit

spec for CPU 
[http://ark.intel.com/products/27593/Intel-Pentium-M-Processor-750-2M-Cache-1_86-GHz-533-MHz-FSB](http://ark.intel.com/products/27593/Intel-Pentium-M-Processor-750-2M-Cache-1_86-GHz-533-MHz-FSB)

also suggest 12.04 LTS as your thinkpad maybe near end of life in 2017 ...

---

### Post by nedzad2 on 2013-08-21
[[COLOR=#000000]MrSteve[/COLOR]]("http://ubuntuforums.org/member.php?u=116055")[COLOR=#000000] , thanks for the info![/COLOR]

---

### Post by Cheesemill on 2013-08-21
@grahammechanical

I had thought about the PAE issue before posting, but I've checked the specs for the Pentium M 750 and it does support PAE.

---

### Post by OrangeCrate on 2013-08-21
I have a T43. It recognizes a PAE kernel. My T42 does not. The T43, with on-board Intel graphics runs either Xubuntu or Ubuntu 12.04 or 13.04, just fine, though Xubuntu is my first choice for the T43.

---

### Post by nedzad2 on 2013-08-21
> **OrangeCrate said:**
> I have a T43. It recognizes a PAE kernel. My T42 does not. The T43, with on-board Intel graphics runs either Xubuntu or Ubuntu 12.04 or 13.04, just fine, though Xubuntu is my first choice for the T43.

Is Xubuntu more lightweight than Ubuntu?

---

### Post by Cheesemill on 2013-08-21
Yes it is.

And Lubuntu is even lighter than Xubuntu.

---

### Post by nedzad2 on 2013-08-21
> **Cheesemill said:**
> Yes it is.

And Lubuntu is even lighter than Xubuntu.

Thanks, I'll try Ubuntu 13.04 for now, if I have some hardware problems or speed problems I'm switching to xubuntu. Thanks everybody. :)

EDIT: xubuntu looks for me better, but don't like the icons though. :D

---

### Post by OrangeCrate on 2013-08-21
> **nedzad2 said:**
> Thanks, **I'll try Ubuntu 13.04 for now**, if I have some hardware problems or speed problems I'm switching to xubuntu. Thanks everybody. :)

EDIT: xubuntu looks for me better, **but don't like the icons though**. :D

I installed the max of 2 GB RAM on my T43, which removed any question of having to use a lighter version of Ubuntu. It's a very quick machine. (Caution: installing RAM is not for the faint of heart on a T43 - the second bay is under the keyboard.)

I didn't choose Ubuntu, because I didn't like the way it rendered, including some odd page sizes that Ubuntu exhibited on the 1024x768 screen. Xubuntu, at least to me, just looked better.

If you decide to go with Xubuntu, you can easily change the icons if you don't like the default ones. Browse the monthly desktop thread for ideas:

[http://ubuntuforums.org/showthread.php?t=2164581](http://ubuntuforums.org/showthread.php?t=2164581)

---

### Post by nedzad2 on 2013-08-21
> **OrangeCrate said:**
> I installed the max of 2 GB RAM on my T43, which removed any question of having to use a lighter version of Ubuntu. It's a very quick machine. (Caution: installing RAM is not for the faint of heart on a T43 - the second bay is under the keyboard.)

I didn't choose Ubuntu, because I didn't like the way it rendered, including some odd page sizes that Ubuntu exhibited on the 1024x768 screen. Xubuntu, at least to me, just looked better.

If you decide to go with Xubuntu, you can easily change the icons if you don't like the default ones. Browse the monthly desktop thread for ideas:

[http://ubuntuforums.org/showthread.php?t=2164581](http://ubuntuforums.org/showthread.php?t=2164581)

EDIT: What version of Xubuntu are you using?

Thank you, awesome to have someone on the forums with the same laptop.

---

### Post by OrangeCrate on 2013-08-21
> **nedzad2 said:**
> 

Thank you, awesome to have someone on the forums with the same laptop.

You're most welcome, and good luck!

:)

Edit:

You added to your post after I read it...

I'm currently running Xubuntu 13.04 on the T43.

---


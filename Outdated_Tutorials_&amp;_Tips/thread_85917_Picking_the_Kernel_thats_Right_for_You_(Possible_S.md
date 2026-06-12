---
title: "Picking the Kernel thats Right for You (Possible Speed Increase)"
date: 2005-11-03
forum: Outdated Tutorials &amp; Tips
---

### Post by poofyhairguy on 2005-11-03
**[COLOR="Red"]STAFF NOTE:[/COLOR]**

Since the naming convention -- and the generic kernel -- changed after version 6.06, Dapper Drake, selecting a different kernel may or may not have any effect on your system. Please [research the kernel options]("http://packages.ubuntu.com/") that match your release, remembering that the default kernel -- [linux-generic]("http://packages.ubuntu.com/feisty/base/linux-generic") in Feisty -- in some versions of Ubuntu is probably already appropriate for your CPU.

Thanks.
K.Mandla

-----------

[B]Disclaimer

This section is about messing with the kernel and that can be tricky business. Has never messed up for me, but it is a little nerdy. Look here if you want to learn and maybe get a speed boast (or if you have a dual core/dual processor/hyperthreading machine because you WILL get a performance boost). Use at you own risk, I am not a kernel developer or anything.

Be sure not to install the linux-image package instead or things will probably break! If you have done that just install the correct package and things will fix themselves.

***********************
[/B]
**Introduction**

I have noticed some recent confusion in the forum when it comes to kernels, so I want to explain some things I have discovered. I hope it helps.

So you just installed Ubuntu but you don't think its going as fast as you think it should? Maybe you have just been advised to install a new kernel so you want to know more.

In Synaptic, if you search for &#8220;linux-image&#8221; you will find many kernels. Each its follows by some  numbers and letters in some order. I will now explain those differences and what each means.

**Notes:**

- This guide does not apply to the PPC or 64 bit version of Ubuntu.

- If you have a heavily modified setup this might not work. For example if you have installed some drivers "by hand" and not from the repositories.

- Its hard to measure the speed increase, so if in doubt leave it out. Don't follow the guide if you are uncomfortable

- You can always boot back into you old kernel if things mess up. When the OS Menu appears at boot (called the Grub menu) just hit down and then hit enter on the first line with a "386" in it. You might have to hit the ESC key when you boot to pull up this menu. 

- My steps will rewite your grub, so if you have a custom grub save it somewhere.

**The Many Kinds of Kernels**

386 &#8211; the default kernel in Ubuntu is the 386 kernel (but I hear its really a 486 kernel). What that means is that its the most compatible kernel because it supports the oldest tech. Here is wiki page to learn more:

[http://en.wikipedia.org/wiki/Intel_80386](http://en.wikipedia.org/wiki/Intel_80386)

686 &#8211; The kernel that is recommended for use with any Intel Processors in a computer that are more recent then a Pentium Pro. So even old Pentium 2s and 3s can get in on the act. Installing this kernel with may improve performance.

[http://en.wikipedia.org/wiki/Pentium_Pro](http://en.wikipedia.org/wiki/Pentium_Pro)

k7 &#8211; This kernel is recommended for a computer with a Athlon or newer AMD CPU.  New 64 bit AMD cpus can use it as well if you have the 32 bit version of Ubuntu installed. Installing this kernel with may improve performance.

[http://en.wikipedia.org/wiki/Athlon](http://en.wikipedia.org/wiki/Athlon)
[B]
smp &#8211; This kernel is NEEDED to use both CPUs in a multi-CPU setting. The kernel is also required to &#8220;enable&#8221; hyperthreading in modern Pentium 4 CPUs. Also needed for dual core processors (the letters stand for Symmetric Multiprocessing). Very important to install this, as it WILL improve performance. Sorry to bold it but I think this one is the most important.[/B]

[http://en.wikipedia.org/wiki/Symmetric_multiprocessing](http://en.wikipedia.org/wiki/Symmetric_multiprocessing)

**How to Install New Kernels**

You need to install the file below as indicated:

For a modern Pentium 2+ (686) kernel:

> sudo apt-get install linux-686

For a modern Pentium 2+  kernel for dual processors, dual cores, or hyperthreading:

> sudo apt-get install linux-686-smp

For a Athlon (k7) or for a Athlon 64 (with 32 bit Ubuntu) kernel.

> sudo apt-get install linux-k7

For a Athlon (k7) kernel for dual processors or dual cores:

> sudo apt-get install linux-k7-smp

**Conclusion**

I wish you the best of luck and please post comments if you notice any improvements or any problems.

**Note About Nvidia**

The Nvidia driver is not an open source driver. It is "restricted" because of that fact.

Therefore the actual official Nvidia driver's kernel module (the part that interacts with the kernel to make it work) is in the restricted package. If you follow my guide those packages should be installed automatically (they are for me) but they don't for legacy cards. If you have a Nvidia card older than a Geforce 3 (except maybe the Geforce 2 MX) you have to install the legacy drivers. 

Every time you switch to another kernel you have to reinstall the nvidia drivers for that specific kernel if you have used the nvidia installer. 

OR

If you use the drivers from the repos then you will need the restricted modules for your kernel (only the ones for the i386 kernel are installed by default). If apt-get did not install these automatically with my guide you MUST do it! In other words, boot as usual, and if you are stuck to the command line type:


> sudo apt-get install linux-restricted-modules-`uname -r`

OR (if you use the nvidia legacy drivers)

> sudo apt-get install linux-restricted-modules-`uname -r`-nvidia-legacy

---

### Post by kvidell on 2005-11-03
Is it a relevant point to mention how to clean up one's GRUB menu.lst if they find one they like but don't want 3 extraeneous kernel options listed?

---

### Post by poofyhairguy on 2005-11-03
[QUOTE=kvidell]Is it a relevant point to mention how to clean up one's GRUB menu.lst if they find one they like but don't want 3 extraeneous kernel options listed?[/QUOTE]

I thought about that, but that can get REALLY tricky and with the other options at least the person using the guide can go back to a safe spot. I also left out how to uninstall old kernels for the same reason. Going back to the old kernel in grub has saved my hide more than once....so...

---

### Post by kvidell on 2005-11-03
Ah, okay.. Understandable.
I've just been lucky with ubuntu kernels then... I've never had to revert back to an older one, even with my dual proc box...
*keeps his fingers crossed*
- K

---

### Post by sk545 on 2005-11-03
so which one do i use for a athlon 64 3000+ (lets say i want it running 32 bit apps)?  Should i use kernel k7 or 686?

---

### Post by poofyhairguy on 2005-11-03
[QUOTE=sk545]so which one do i use for a athlon 64 3000+ (lets say i want it running 32 bit apps)?  Should i use kernel k7 or 686?[/QUOTE]

If you have the 32 bit version of Ubuntu installed on there, then the k7 one. If you have the 64 bit version installed this guide does not apply.

---

### Post by teaker1s on 2005-11-03
sorry to sound thick but synaptic or apt-get don't find the k7 for my  amdxp2200

so is this direct from debian and if so how will it differ from a patched kernel

also second question konsole  see's i686 which I thought was 64 bit only see below

teaker1s@ubuntu:~$ uname -a
Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux

found k7 in synaptic today

---

### Post by Biased turkey on 2005-11-03
I installed ubuntu 32 bits 5.10 on my Athlon64.
Just saw this interesting trhead ( thanks ) and right away installed the k7 kernel using synaptic.
When booting the k7 kernel, Xorg doesn't start. I'm stucked in console mode.Of course, booting back with the original kernel works OK.
I have an Nforce4 mobo and an Nvidia 6600 video board.
What should I do to be able to boot the k7 kernel and be able to use the graphic mode ?
tia for any help.

---

### Post by poofyhairguy on 2005-11-03
[QUOTE=Biased turkey]I installed ubuntu 32 bits 5.10 on my Athlon64.
Just saw this interesting trhead ( thanks ) and right away installed the k7 kernel using synaptic.
When booting the k7 kernel, Xorg doesn't start. I'm stucked in console mode.Of course, booting back with the original kernel works OK.
I have an Nforce4 mobo and an Nvidia 6600 video board.
What should I do to be able to boot the k7 kernel and be able to use the graphic mode ?
tia for any help.[/QUOTE]


Make SURE you have the official nvidia drivers installed from the repo. The Ubuntu Guide says how.

---

### Post by stubby on 2005-11-04
My notebook is a Pentium M, so is that the 686 kernel ?

---

### Post by kvidell on 2005-11-04
[QUOTE=stubby]My notebook is a Pentium M, so is that the 686 kernel ?[/QUOTE]
That would be the boat I'm in, works great :)

---

### Post by stubby on 2005-11-04
[QUOTE=kvidell]works great :)[/QUOTE]

that's all i needed to hear =)

---

### Post by M7S on 2005-11-04
Maybe it should be worth mentioning that nvidia (and perhaps also ati) users who use nvidia's (or ati's) propriarity drivers have to install the linux-restricted-modules for their kernel to be able to use X. At least I had to when I changed my kernel some time ago.

Regards,
M7S

---

### Post by GoA on 2005-11-04
I have AMd athlon 2800+ and I am using 686 kernel. Previously I had K7 but then I tryed the 686 version. Only different wchic I have found out between 686, K7 and 383 is the fact that 386 kernel doesn't support 1 gb of memory. No speed difference otherwise and I think it doesn't matter are you using K/ or 686 with a new AMD processor.

---

### Post by poofyhairguy on 2005-11-04
[QUOTE=M7S]Maybe it should be worth mentioning that nvidia (and perhaps also ati) users who use nvidia's (or ati's) propriarity drivers have to install the linux-restricted-modules for their kernel to be able to use X. At least I had to when I changed my kernel some time ago.

Regards,
M7S[/QUOTE]

Thats why its important to install the 

linux-686 

package instead of the Linux-image package.

---

### Post by poofyhairguy on 2005-11-04
[QUOTE=GoA]I have AMd athlon 2800+ and I am using 686 kernel. Previously I had K7 but then I tryed the 686 version. Only different wchic I have found out between 686, K7 and 383 is the fact that 386 kernel doesn't support 1 gb of memory. No speed difference otherwise and I think it doesn't matter are you using K/ or 686 with a new AMD processor.[/QUOTE]

I have thought that maybe the improvement in speed was just in everyone's mind (including my own) so that why I tried not to use concrete language. Thanks for the tip about the RAM.

---

### Post by donar73 on 2005-11-04
It would be interesting to know which processor-specific optimizations (mmx, sse, 3dnow etc.) are compiled into each of these kernels. Do you have any information about this?
The reason why I'm asking is, that it seems to me that my Athlon XP 2800+ (Barton) works slightly faster (or maybe I should call it *smoother*) with the 686-kernel than with the K7-one... :confused:

---

### Post by Cyril on 2005-11-04
I installed the 686-smp kernel.

When I boot using the 686-smp-kernel, the boot screen shows the kubuntu logo instead of the ubuntu one.  Anyone knows why this happens and how can it back to the ubuntu logo?

---

### Post by tseliot on 2005-11-04
[QUOTE=Biased turkey]I installed ubuntu 32 bits 5.10 on my Athlon64.
Just saw this interesting trhead ( thanks ) and right away installed the k7 kernel using synaptic.
When booting the k7 kernel, Xorg doesn't start. I'm stucked in console mode.Of course, booting back with the original kernel works OK.
I have an Nforce4 mobo and an Nvidia 6600 video board.
What should I do to be able to boot the k7 kernel and be able to use the graphic mode ?
tia for any help.[/QUOTE]
The problem is that every time you switch to another kernel you have to reinstall the nvidia drivers for that specific kernel if you have used the nvidia installer. (you can use my guide for that)

OR

If you use the drivers from the repos then you will need the restricted modules for your kernel (only the ones for the i386 kernel are installed by default). In other words, boot as usual, and if you are stuck to the command line type:


sudo apt-get install linux-restricted-modules-`uname -r`

OR (if you use the nvidia legacy drivers)

sudo apt-get install linux-restricted-modules-`uname -r`-nvidia-legacy


Then type

startx


Enjoy


P.S. Jonathan, I think you should add it to your guide so as to avoid some problem.

---

### Post by DoeRayMe on 2005-11-04
Just want to say thank you, my computer is around 50% faster

thank you again

---

### Post by yesplease on 2005-11-04
Thanks PoofyHairguy, I have been searching for this information recently. In return I made you famous on the dutch Ubuntu forum :) .

Like Donar73 I am interested in the processor-specific optimizations that are implemented (in my case for a k8 processor). Do you have a link to a summary of this info?

@tseliot: In Synaptic one can make more specific choices, for example linux-restricted-modules 2.6.12-9-k7 for modern nvidia video-cards, or an smp version or a legacy version. I dont know if this matters much, but I just thought to mention it.

---

### Post by tseliot on 2005-11-04
[QUOTE=yesplease]@tseliot: In Synaptic one can make more specific choices, for example linux-restricted-modules 2.6.12-9-k7 for modern nvidia video-cards, or an smp version or a legacy version. I dont know if this matters much, but I just thought to mention it.[/QUOTE]

You're absolutely right, I'll modify the command. As far as "smp" is concerned it's included in the "uname -r" (i.e. if you use a smp kernel the restricted modules for smp will be installed).

These ones are the right commands:

sudo apt-get install linux-restricted-modules-`uname -r`

OR (if you use the nvidia legacy drivers)

sudo apt-get install linux-restricted-modules-`uname -r`-nvidia-legacy

I find them useful especially if you are stuck in the command line and you don't want to restart your computer

---

### Post by teaker1s on 2005-11-04
have booted k7 kernel and so far it appears that metacity etc run faster thanks-as for not removing old kernel I agree at least it's a safety net if things go wrong

---

### Post by Biased turkey on 2005-11-04
[QUOTE=tseliot]The problem is that every time you switch to another kernel you have to reinstall the nvidia drivers for that specific kernel if you have used the nvidia installer. (you can use my guide for that)

OR

If you use the drivers from the repos then you will need the restricted modules for your kernel (only the ones for the i386 kernel are installed by default). In other words, boot as usual, and if you are stuck to the command line type:


sudo apt-get install linux-restricted-modules-`uname -r`

OR (if you use the nvidia legacy drivers)

sudo apt-get install linux-restricted-modules-`uname -r`-nvidia-legacy


Then type

startx


Enjoy


P.S. Jonathan, I think you should add it to your guide so as to avoid some problem.[/QUOTE]

Thanks for the info, it looks like that it'll solve my problem
I use the drivers from the repository ( I don't want to live at the bleeding edge, I'm a coward lol ) so it looks like I'll have to install the restricted modules.How did you know that's those modules are only installed with the default ( i386 ) kernel 

I'm confused with those restricted and legacy modules etc...
Why are they required ?
Is there any good link that explains their requirements ?

I like HOWTOs, they solve problems, but I would like to see some WHYTOs, that goes a little deeper and give more details.

---

### Post by poofyhairguy on 2005-11-04
[QUOTE=tseliot]
P.S. Jonathan, I think you should add it to your guide so as to avoid some problem.[/QUOTE]

Done. Thanks for the heads up.

---

### Post by poofyhairguy on 2005-11-04
[QUOTE=Biased turkey]Thanks for the info, it looks like that it'll solve my problem
I use the drivers from the repository ( I don't want to live at the bleeding edge, I'm a coward lol ) so it looks like I'll have to install the restricted modules.How did you know that's those modules are only installed with the default ( i386 ) kernel 

I'm confused with those restricted and legacy modules etc...
Why are they required ?
Is there any good link that explains their requirements ?

I like HOWTOs, they solve problems, but I would like to see some WHYTOs, that goes a little deeper and give more details.[/QUOTE]

The Nvidia driver is not an open source driver. It is "restricted" because us nerds can't treat it like our own like we can with OSS stuff and because it has a semi- harsh license for distribution.

Therefore the actual official Nvidia driver's kernel module (the part that interacts with the kernel to make it work) is in that restricted package. If you have a Nvidia card older than a Geforce 3 (except maybe the Geforce 2 MX) you have to install the legacy drivers. All of these things might be installed so that you can use the driver.

---

### Post by poofyhairguy on 2005-11-04
[QUOTE=Cyril]I installed the 686-smp kernel.

When I boot using the 686-smp-kernel, the boot screen shows the kubuntu logo instead of the ubuntu one.  Anyone knows why this happens and how can it back to the ubuntu logo?[/QUOTE]


Uninstall the kubuntu-artwork-usplash package.

---

### Post by phanboy_iv on 2005-11-04
Just installed the 686 kernal on my laptop's 1.4 Ghz. Celeron M.
Works beautifully. Thanks! So simple too.(in my case, that is.)

---

### Post by tseliot on 2005-11-04
[QUOTE=poofyhairguy]If you have a Nvidia card older than a Geforce 3 (except maybe the Geforce 2 MX) you have to install the legacy drivers. All of these things might be installed so that you can use the driver.[/QUOTE]

Below are the legacy GPUs that are no longer supported in the unified driver.
These GPUs will continue to be maintained through the special legacy NVIDIA
GPU driver releases.

NVIDIA chip name Device PCI ID
------------------------------- -------------------------------
RIVA TNT 0x0020
RIVA TNT2/TNT2 Pro 0x0028
RIVA TNT2 Ultra 0x0029
Vanta/Vanta LT 0x002C
RIVA TNT2 Model 64/Model 64 Pro 0x002D
Aladdin TNT2 0x00A0
GeForce 256 0x0100
GeForce DDR 0x0101
Quadro 0x0103
GeForce2 GTS/GeForce2 Pro 0x0150
GeForce2 Ti 0x0151
GeForce2 Ultra 0x0152
Quadro2 Pro 0x0153

---

### Post by tseliot on 2005-11-04
[QUOTE=poofyhairguy]Done. Thanks for the heads up.[/QUOTE]
you're welcome

---

### Post by poofyhairguy on 2005-11-04
[QUOTE=yesplease]Thanks PoofyHairguy, I have been searching for this information recently. In return I made you famous on the dutch Ubuntu forum :) [/QUOTE]

You are welcome.

> 
Like Donar73 I am interested in the processor-specific optimizations that are implemented (in my case for a k8 processor). Do you have a link to a summary of this info?


I honestly don't know. I bet a doc somewhere says, or push comes to shove, there is tons of info about this on Gentoo forum.

---

### Post by william_nbg on 2005-11-04
First: Thanks for the how to.

I'm still fairly new with Linux so I want to be sure of this before I lose my X.

I have the amd64 3200+ and a 6600 nvidia card.

I installed 5.10 i386  as a fresh install, upgraded to the i686 kernel, and then installed the nvdia driver from the repo. as usual.

Everything works great. But were never happy with that until we try everything or bring down the house, whichever comes first. Meaning, I'd like to give the K7 a try.

My question: should I remove the i686 kernel and the nvidia driver and then install the K7 and the new nvidia driver before rebooting - note the i383 kernel is still installed??

---

### Post by tseliot on 2005-11-04
[QUOTE=william_nbg]My question: should I remove the i686 kernel and the nvidia driver and then install the K7 and the new nvidia driver before rebooting - note the i383 kernel is still installed??[/QUOTE]
No, please don't remove anything. Just install the new kernel and its restricted modules as described in the guide

---

### Post by yesplease on 2005-11-04
I like to use synaptic because it gives more info. 

Search on linux-k7 gives version 2.6.12.16, and there is a correspondent version of linux-restricted-modules. These versions depend on the latest package, but is that stable?

Earlier I searched for kernel k7 and found linux-image-2.6.12-9-k7 and linux headers of the same version. (There is a correspondent version of linux restricted modules, so that is ok.)  It seems to me that linux kernel still has to built from this linux-image and headers ?? , but would that give a more stable version?

---

### Post by poofyhairguy on 2005-11-04
[QUOTE=yesplease]I like to use synaptic because it gives more info. 

Search on linux-k7 gives version 2.6.12.16, and there is a correspondent version of linux-restricted-modules. These versions depend on the latest package, but is that stable?

Earlier I searched for kernel k7 and found linux-image-2.6.12-9-k7 and linux headers of the same version. (There is a correspondent version of linux restricted modules, so that is ok.)  It seems to me that linux kernel still has to built from this linux-image and headers ?? , but would that give a more stable version?[/QUOTE]

The 

linux-* (linux-686, linux-k7, etc.)

packages are meta packages (like ubuntu-desktop). They point to other packages. That way instead of installing just the kernel image or headers by themselves and messing everything up because you did not install the restricted packages, it gets everything you need. My guide is straight forward on this.

---

### Post by yesplease on 2005-11-04
But is version 2.6.12.16 stable, because I remember that ubuntu is stable is at 2.6.12.9 right now?

Edit: I see now that linux-386 is version 2.6.12.16 is installed, and that is the same version number, so that must be ok.

Apparently I am in a paranoid mood today :) , thanks for your answers.

---

### Post by TheIdiotThatIsMe on 2005-11-04
After asking a question about i386 and i686 in another thread, I was pointed over to this guide and followed the instructions. I have a Pentium 4 with HT, and installed the 686-SMP. I just wanted to say thanks! I've noticed a great improvement in the speed of the system. Many programs that took around 5 to 8 seconds to load now load almost instantly! OpenOffice.org now loads in about 1/3 of the time it used to. Also in Konqueror, especially when reading NTFS disks, it slowed considerably when loading a folder with a large amount of files, but now doesn't stall at all. So once again, thanks a bunch!

---

### Post by Griff on 2005-11-04
Installed the k7 via apt-get and everything went smoothly.  Restarted, but there was no selection as to which kernal to boot to at startup.  It boots straight to k7 with no problems, but what happened for me to not be able to choose?

---

### Post by tseliot on 2005-11-04
[QUOTE=Griff]Installed the k7 via apt-get and everything went smoothly.  Restarted, but there was no selection as to which kernal to boot to at startup.  It boots straight to k7 with no problems, but what happened for me to not be able to choose?[/QUOTE]
It boots in your latest kernel. If you want to select your kernel keep on pressing ESC as soon as you turn your computer on until you get to the GRUB menu. Then you can select the boot you need and press ENTER

---

### Post by Biased turkey on 2005-11-04
To Tseliot:
I followed your suggestion:
sudo apt-get install linux-restricted-modules-`uname -r`
And here I am with my brand-new k7 kernel and Xorg working.
Thanks a bunch.

To poofyhairguy:
Please, couldn't the starting post emphasise that step ? it should clear some confusion.

---

### Post by zerhacke on 2005-11-05
Nevermind, I didn't realize this was in Breezy's area.  I'm still using Hoary.

---

### Post by crypto178 on 2005-11-05
Thanks for the HOW-TO.

Are there any cpu benchmarking programs on linux?

---

### Post by poofyhairguy on 2005-11-05
[QUOTE=TheIdiotThatIsMe]After asking a question about i386 and i686 in another thread, I was pointed over to this guide and followed the instructions. I have a Pentium 4 with HT, and installed the 686-SMP. I just wanted to say thanks! I've noticed a great improvement in the speed of the system. Many programs that took around 5 to 8 seconds to load now load almost instantly! OpenOffice.org now loads in about 1/3 of the time it used to. Also in Konqueror, especially when reading NTFS disks, it slowed considerably when loading a folder with a large amount of files, but now doesn't stall at all. So once again, thanks a bunch![/QUOTE]

No problem. People with hyperthreading or dual CPUs or dual core have the most to gain from this guide.

---

### Post by TimelessRogue on 2005-11-05
My initial installation of Beezy was with the default 2.6.12-9-i386 kernel ... it was relatively painless and trouble free and I was satisfied with everything including speed.

However, earlier this evening and even before reading this post, I installed the 2.6.12-9-k7 kernel via Synaptic.  This was also a painless, trouble free operation and seems to have resulted in a speed increase both in booting and during use ... perhaps actual, perhaps perceptual.

And boot-up options include both kernels should I choose to revert.

---

### Post by bionnaki on 2005-11-06
I have a pentium 4 2.4ghz - I should use the 686, right?

---

### Post by linbetwin on 2005-11-06
I have an AMD Athlon XP and switching to k7 made Nautilus crash all the time. So I went back to 386.

---

### Post by kvidell on 2005-11-06
[QUOTE=bionnaki]I have a pentium 4 2.4ghz - I should use the 686, right?[/QUOTE]
That is indeed the correct selection for your archetecture and processor type :)
- K

---

### Post by bionnaki on 2005-11-06
thanks!

---

### Post by Biased turkey on 2005-11-06
to Poofyhairguy:
I apology for stating that your original post should be edited and add:
sudo apt-get install linux-restricted-modules-`uname -r`

Because after installing the K7 kernel on both my gaming rig ( AMD 64 ) and my firewall router ( Athlon XP ) I realised that using the command line or using synaptic are 2 different options:

If I use synaptic to add the new ( K7 ) kernel, then after that I have to reboot ( In console mode ) and run :
sudo apt-get install linux-restricted-modules-`uname -r`

But if I just type from the command line:
 sudo apt-get install linux-k7
It will automatically install the restricted modules.

 No opinion, JUST THE FACTS, MA'AM

---

### Post by kleeman on 2005-11-06
One interesting question poofy:
Can you run a smp kernel on a Pentium M and is hyperthreading present at all for such chips?

I was told about 6-12 months ago that this (running smp with an M) was unwise because the kernel support for speed stepping the cpu up and down did not work with smp kernels. Any thoughts? Perhaps the latest kernel is better or perhaps it's irrelevant since ht is not possible with the M......

---

### Post by sailor420 on 2005-11-06
Just a warning, this overwrites GRUB's menu.lst, so if you have changed anything (added initNG, framebuffer, etc), it will be overwritten. Back it up first :)

---

### Post by william_nbg on 2005-11-06
Thanks again for your tip on the kernels.

I installed the k7 kernel according to your 'how to' and everything seems to be working hunky-dory. Compared to the 686 kernel I'll need more time for testing.

One newbie question: It boots automatically into the k7 kernel as expected, but, of course, the 686 and 383 kernels are still installed. Can I safely take them out, or at least the 686, or is it better to just leave them in??

---

### Post by raublekick on 2005-11-06
<edit> nevermind

thanks, poofy

---

### Post by poofyhairguy on 2005-11-06
[QUOTE=kleeman]One interesting question poofy:
Can you run a smp kernel on a Pentium M and is hyperthreading present at all for such chips?

I was told about 6-12 months ago that this (running smp with an M) was unwise because the kernel support for speed stepping the cpu up and down did not work with smp kernels. Any thoughts? Perhaps the latest kernel is better or perhaps it's irrelevant since ht is not possible with the M......[/QUOTE]

Since the M's do not need hyperthreading (HT as made to make up for problems in the Pentium 4 chips) I do not recommend using the smp kernel till dual core models are made.

---

### Post by poofyhairguy on 2005-11-06
[QUOTE=william_nbg]
One newbie question: It boots automatically into the k7 kernel as expected, but, of course, the 686 and 383 kernels are still installed. Can I safely take them out, or at least the 686, or is it better to just leave them in??[/QUOTE]

My official recommendation is not to do that. But if you want you can uninstall the other kernel images.

---

### Post by Biased turkey on 2005-11-06
JUST THE FACTS, MA'AM
Is there any benchmark I can use to compare the default 386 vs. the K7 kernel performances ?

---

### Post by astronerd on 2005-11-07
Is there a command to check to see if your hyperthreading has been activated and you are using it?  I have a 686 installed on a P4 3.0 Ghz and need to see if I should use the 686smp(I am pretty sure its HT, but need to check....)
Thanks

---

### Post by poofyhairguy on 2005-11-07
[QUOTE=astronerd]Is there a command to check to see if your hyperthreading has been activated and you are using it?  I have a 686 installed on a P4 3.0 Ghz and need to see if I should use the 686smp(I am pretty sure its HT, but need to check....)
Thanks[/QUOTE]

Add the "system monitor" applet to your Gnome panel, then click on it. When it comes up, under the "Resources" tab it will tell you if the system detect two CPUs. That means its working.

---

### Post by yesplease on 2005-11-08
I use an AMD k8 processor, single core, and installed the k7 kernel. Install was very easy, but there was no discernible increase in performance in comparison to the i368 kernel. However, I havent found general benchmarks programs yet to test performance, and i368 cant use all of your memory when you have 1GB, while the k7 kernel can. (Edit: I think this last bit is outdated information; the i368 can handle 1GB of memory now).

Performance on both kernels is good, I do not have programs that start up or react very slow, so I have no complaints about that.

I installed the k7 kernel with synaptic. Search for linux k7 gives:
linux-k7 version 2.6.12.16
mark additional required changes:
linux-image-2.6.12-9-k7
linux-image-k7
linux-restricted-modules-2.6.12-9-k7 (non-free NVIDIA, etc.)
linux-restricted-modules-k7
total 70.6 MB
Grub automatically got an extra entry: Ubuntu, kernel 2.6.12-9-k7

---

### Post by Maverick911 on 2005-11-08
Hi PHG,

When I first installed ubuntu it booted up into an SMP kernel. I figured this was an error since I'm on a laptop with a P4 Pro 3.2 Ghz. I switched to 2.6.14-686 kernel. Then I read this: (bold added by me)> 
smp – This kernel is NEEDED to use both CPUs in a multi-CPU setting. **The kernel is also required to “enable” hyperthreading in modern Pentium 4 CPUs.** Also needed for dual core processors (the letters stand for Symmetric Multiprocessing). Very important to install this, as it WILL improve performance. Sorry to bold it but I think this one is the most important.

If I read this right, you are saying that I should have an smp kernel even though I only have 1 processor. Is this right?

Just wondering:???:

---

### Post by poofyhairguy on 2005-11-08
[QUOTE=Maverick911]Hi PHG,

When I first installed ubuntu it booted up into an SMP kernel. I figured this was an error since I'm on a laptop with a P4 Pro 3.2 Ghz. I switched to 2.6.14-686 kernel. Then I read this: (bold added by me)

If I read this right, you are saying that I should have an smp kernel even though I only have 1 processor. Is this right?

Just wondering:???:[/QUOTE]


Hyperthreading is a trick in which Intel forced the single Pentium 4 chips to act like two chips in order to overcome huge problems with the Pentium 4 design. If you have hyperthreading you need the smp kernel to enable it.

---

### Post by ephman on 2005-11-08
hi,

if i upgrade to the 686 from the 386, can i delete the 386 kernel?  and when i restart i assume it'll just automatically see the 686 kernel right (i know silly question, but i'm neurotic)?

thanks,
ephman

---

### Post by ephman on 2005-11-08
yup deleted all the 386's...

cool,
ephman

---

### Post by iltofa on 2005-11-09
Hi everybody!

I'm using a PC with AMD Athlon XP cpu.
The default package installed was Linux-386.
Today I've apt-get installed linux-k7... not benchmarked anything at all yet, but it seems faster.

Anyway I'm not going to benchmark the system and, if everything continue to works, I'll remove the 386 kernel...

---

### Post by adamb10 on 2005-11-09
How do you remove kernels?  
I have a Athlon XP so I need the k7 kernel?

---

### Post by Maverick911 on 2005-11-09
[QUOTE=poofyhairguy]Hyperthreading is a trick in which Intel forced the single Pentium 4 chips to act like two chips in order to overcome huge problems with the Pentium 4 design. If you have hyperthreading you need the smp kernel to enable it.[/QUOTE]
Hi everyone,

I installed the 2.6.12-9-686-smp kernel on my laptop which has a P4 3.2GHz processor. When I boot into the smp kernel, bootup takes 5 to 6 minutes as opposed to less than a minute with the 686 2.6.12-9-686 kernel. 
After logging in everthing loads and runs very, very slow.
System monitor resources shows 2 CPU's with usage fluctuating between 25% and 90%.
Processes shows that gnome is using most of the CPU%. In the plain 686 kernel, gnome only uses 2 to 3%.
Does anyone have any ideas on what the problem might be?:confused:

---

### Post by der_joachim on 2005-11-09
[QUOTE=adamb10]How do you remove kernels?  
I have a Athlon XP so I need the k7 kernel?[/QUOTE]

```
sudo apt-get remove linux-386
```

HOWEVER!!! Do this with care and after considerable testing! You have to edit your Grub config by hand after removal of your old kernel. 

For the record: switching from linux-386 to linux-k7 not only sped up my system, it also reduced heat production  for my Athlon Furnace XP 1800+. :p

---

### Post by iltofa on 2005-11-09
[QUOTE=adamb10]How do you remove kernels?  
I have a Athlon XP so I need the k7 kernel?[/QUOTE]

Yes, I think, but I'm a newbie! :D 

To remove the kernels, I use Aptitude (command shell) or Synaptic (GUI).
The packets will be: linux-386, for the latest 386 kernel and then after reboot, any
packet named linux-image-[version of previous kernel]-386.
May be this will also automatically remove the relative entries in the grub start menu...

May be an ubuntu expert would use *apt-get -remove uninstall*.... or something like that, but I'm not sure about the sintax...:confused:

---

### Post by DDM on 2005-11-09
I've been using the k7 kernel for a short while now, was previously using the 686. When I'm compiling something and co a ./configure I still get this:

[checking build system type... i686-pc-linux-gnu]

Is this a standard thing or is there some sort of speed loss involved with the resulting binaries?

---

### Post by poofyhairguy on 2005-11-09
[QUOTE=Maverick911]Hi everyone,

I installed the 2.6.12-9-686-smp kernel on my laptop which has a P4 3.2GHz processor. When I boot into the smp kernel, bootup takes 5 to 6 minutes as opposed to less than a minute with the 686 2.6.12-9-686 kernel. 
After logging in everthing loads and runs very, very slow.
System monitor resources shows 2 CPU's with usage fluctuating between 25% and 90%.
Processes shows that gnome is using most of the CPU%. In the plain 686 kernel, gnome only uses 2 to 3%.
Does anyone have any ideas on what the problem might be?:confused:[/QUOTE]


Maybe the power saving feature is messing up. I don't know hwo to fix it really, just use the 686 kernel.

---

### Post by guyomarj on 2005-11-09
Hi,

I've just installed the k7 kernel. I figured out that it was the right for me since I have a 750MgH AMD Athlon. All went well. I'm currently running on the k7 kernel. But I have two question:

[LIST=1]
[*]Why is there still a "**i686**" thing when I run the command:
j```
yves@ubuntu:~$ uname -a
Linux ubuntu 2.6.12-9-k7 #1 Mon Oct 10 13:47:52 BST 2005 i686 GNU/Linux

```
[*]
I also have a Nvidia card:
```
Section "Device"
        Identifier      "NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option  "NoLogo"
```

How do I know that I'm running the **good driver**? After the build of the k7 kernel, I didn't do anything about it. Everything seems to work, do I have still to apt-get the restricted modules like specified in the how-to?
[/LIST]

Thx...

---

### Post by tomrules345 on 2005-11-10
Hi i was just wondering if you could tell me how to save my grub file because i am running a dualboot with windows xp. I have a Dimension 4600 with a 3.0ghz HT processor with 4gb RAM so which kernel should i use because i dont seem to be able to use all my ram with the defult Kernel

---

### Post by iltofa on 2005-11-10
[QUOTE=guyomarj]
I also have a Nvidia card:
...
How do I know that I'm running the **good driver**? 
[/QUOTE]

I too. Just follow the instruction on [http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074")
by tseliot. 

After that you should see the nvidia logo during bootup, only if it hasn't been disabled during installation.

An easy test may be the screensaver "humfo's tunnel". It doesn't start with a wrong driver...:)

---

### Post by poofyhairguy on 2005-11-10
[QUOTE=tomrules345]Hi i was just wondering if you could tell me how to save my grub file because i am running a dualboot with windows xp. I have a Dimension 4600 with a 3.0ghz HT processor with 4gb RAM so which kernel should i use because i dont seem to be able to use all my ram with the defult Kernel[/QUOTE]

Unless you did some stuff to your grub by hand, it will be fine.

---

### Post by sailor420 on 2005-11-10
[QUOTE=tomrules345]4gb RAM so which kernel should i use because i dont seem to be able to use all my ram with the defult Kernel[/QUOTE]

You've gotta enable large memory support in the kernel to do that, which may (though I'm not sure, someone around here probably knows more) involve recompiling your kernel.

See [here.]("http://www.ubuntuforums.org/showthread.php?t=85064")

---

### Post by tseliot on 2005-11-10
[QUOTE=sailor420]You've gotta enable large memory support in the kernel to do that, which may (though I'm not sure, someone around here probably knows more) involve recompiling your kernel.

See [here.]("http://www.ubuntuforums.org/showthread.php?t=85064")[/QUOTE]
Well this was true in Hoary but in Breezy even i386 kernel (which comes with Ubuntu by default) supports up to 4GB RAM by default.

---

### Post by sailor420 on 2005-11-10
[QUOTE=tseliot]Well this was true in Hoary but in Breezy even i386 kernel (which comes with Ubuntu by default) supports up to 4GB RAM by default.[/QUOTE]

OK then. That's good to know.

---

### Post by tseliot on 2005-11-10
[QUOTE=guyomarj][LIST=1]
[*]Why is there still a "**i686**" thing when I run the command:
j```
yves@ubuntu:~$ uname -a
Linux ubuntu 2.6.12-9-k7 #1 Mon Oct 10 13:47:52 BST 2005 i686 GNU/Linux

```
[*][/QUOTE]
I don't know why but it seems that's the way it works (for me too)

[QUOTE=guyomarj]I also have a Nvidia card:
```
Section "Device"
        Identifier      "NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option  "NoLogo"
```

How do I know that I'm running the **good driver**? After the build of the k7 kernel, I didn't do anything about it. Everything seems to work, do I have still to apt-get the restricted modules like specified in the how-to?
[/LIST]

Thx...[/QUOTE]

When you installed the package "linux-image-k7" Synaptic installed automatically also the restricted module for your kernel. Moreover the package "nvidia-glx" is the same for all the architectures (k7, i686, etc.).

Don't you worry, you have the right version of the drivers (otherwise they wouldn't work and you wouldn't even see the graphical interface)

---

### Post by guyomarj on 2005-11-10
Thx tseliot... I got another one for you ;): Is there an "How to tweak Nvidia Settings", because I want to get as much as I can from my videocard but I don know how to use the Nvidia Setting application.

---

### Post by tseliot on 2005-11-10
[QUOTE=guyomarj]Thx tseliot... I got another one for you ;): Is there an "How to tweak Nvidia Settings", because I want to get as much as I can from my videocard but I don know how to use the Nvidia Setting application.[/QUOTE]

No, sorry (since I don't use my nvidia card for playing games,etc.) but you can always have a look at the unofficial nvidia forums and ask questions there (where you can find the developers of the drivers and some linux geek):
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14")

---

### Post by JimLittle on 2005-11-17
WRT the question about the kernel to install for a Pentium M.

Yes you want the 686.

[http://www.intel.com/pressroom/kits/quickreffam.htm](http://www.intel.com/pressroom/kits/quickreffam.htm)

---

### Post by dudus on 2005-11-17
Just installed the k7 kernel here and everything went fine. Thank you very much

---

### Post by domino on 2005-11-18
Thanks for the information. I posted this in the n00b forum, but I think this is a more appropriate thread for such question.

I have a P4 2.8C HT processor. All this time, I was under the impression that the 686-smp kernel was better than the 386 kernel. I looked at the boot logs and I noticed that on the i686-smp, HT was disabled! So I'm saying to myself, @#&%^!? Being relatively new Linux, this is NOT GOOD, correct? How can I enable HT on the kernel I'm using?

unmae -r = 2.6.12-9-686-smp

If you need to know more, just tell me what commands to copy/past.

---

### Post by kenweill on 2005-11-18
I have tried running the command:

sudo apt-get install linux-686

But it just displays:

 E: Coudn't find package linux-686

What else can i do about this?

---

### Post by tseliot on 2005-11-19
[QUOTE=kenweill]I have tried running the command:

sudo apt-get install linux-686

But it just displays:

 E: Coudn't find package linux-686

What else can i do about this?[/QUOTE]
```
sudo gedit /etc/apt/sources.list
```

uncomment (i.e. remove the "##" before the lines) all the lines beginning with "deb-http" and "deb-src" but the backports.

Save and exit

Then:
```
sudo apt-get update
```

```
sudo apt-get install linux-686
```

---

### Post by erikpiper on 2005-11-19
yessir!

---

### Post by mcrofutt on 2005-11-20
[FONT="Century Gothic"][COLOR="SeaGreen"][/COLOR][/FONT]
 :)  Thanks for this,poofyhairguy! The 686 kernel seems to make quite a difference in my AMD 1,2G :KS .
 
 Off topic: I ALSO live in Texas. NE part of the state, up near Texarkana. Where do you call home?


 You Ubuntu Team members do a GREAT job! Keep up the good work!

---

### Post by gk_jam on 2005-11-20
I installed ubuntu x86 on my pc with an AMD Athlon 64 3200+. As expected, it initially used the i386 kernel, but I followed the instructions in this thread to install the k7 kernel and rebooted. Everyhting seems to be working fine. My question, when I type 'uname -m' I get 'i686', and when I type 'uname -r' I get '2.6.12-9-k7'. Is that ok, or should the machine name match the kernel release?

---

### Post by poofyhairguy on 2005-11-20
[QUOTE=mcrofutt][FONT="Century Gothic"][COLOR="SeaGreen"][/COLOR][/FONT]
 :)  Thanks for this,poofyhairguy! The 686 kernel seems to make quite a difference in my AMD 1,2G :KS .
 
 Off topic: I ALSO live in Texas. NE part of the state, up near Texarkana. Where do you call home?
[/QUOTE]

College Station and no problem.

---

### Post by poofyhairguy on 2005-11-20
[QUOTE=gk_jam]I installed ubuntu x86 on my pc with an AMD Athlon 64 3200+. As expected, it initially used the i386 kernel, but I followed the instructions in this thread to install the k7 kernel and rebooted. Everyhting seems to be working fine. My question, when I type 'uname -m' I get 'i686', and when I type 'uname -r' I get '2.6.12-9-k7'. Is that ok, or should the machine name match the kernel release?[/QUOTE]


Its ok, unless you soon find a big problem in function.

---

### Post by ekravche on 2005-12-04
for the pentium 4 515 2.93Mhz should I install the 686 kernel or the 686-smp kernel?

Thank you in advance.

---

### Post by ^NoX on 2005-12-04
[QUOTE=ekravche]for the pentium 4 515 2.93Mhz should I install the 686 kernel or the 686-smp kernel?

Thank you in advance.[/QUOTE]

I don't think that this is P4.. I think it's a Celeron.
[http://processorfinder.intel.com/scripts/list.asp](http://processorfinder.intel.com/scripts/list.asp)

---

### Post by ekravche on 2005-12-04
[QUOTE=^NoX]I don't think that this is P4.. I think it's a Celeron.
[http://processorfinder.intel.com/scripts/list.asp](http://processorfinder.intel.com/scripts/list.asp)[/QUOTE]

It's a p4 trust me. I have 1Mb L2 cache, while celerons only have 256Kb. Anyhooo, if you look on the intel's site you'll see  ([http://www.intel.com/products/processor_number/proc_info_table062705.pdf](http://www.intel.com/products/processor_number/proc_info_table062705.pdf)). Nonetheless, my cpu doesn't support HT from the looks of it and the 686-smp kernel doesn't boot at all. The 686 kernel works great and I've noticed some performance increase.


If anyone needs help deciding which kernel they need to install this link can help those with an intel cpu [http://www.intel.com/products/processor_number/proc_info_table062705.pdf](http://www.intel.com/products/processor_number/proc_info_table062705.pdf).

---

### Post by bored2k on 2005-12-04
[QUOTE=ekravche]for the pentium 4 515 2.93Mhz should I install the 686 kernel or the 686-smp kernel?

Thank you in advance.[/QUOTE]
Does it have HT-tech? If not, use regular 686 kern.

---

### Post by poofyhairguy on 2005-12-04
I think I found out why Hyperthreading gets kinda second class status in Linux. Turns out it hurts server performance:

[http://news.zdnet.co.uk/hardware/0,39020351,39237341,00.htm](http://news.zdnet.co.uk/hardware/0,39020351,39237341,00.htm)

And we all know that almost EVERY Linux distro (even Ubuntu) fancies itself to exist on a server. That said I hear that in Windows HT makes things feel more responsive.

---

### Post by masingerz on 2005-12-15
Dear Forum 

I have a P4 3.2 Ghz 800mhz with 1M L2 with HT, please advise on how to get the HT kernel installed.

regards Masingerz

---

### Post by avilella on 2005-12-20
any of those kernel working with 4G RAM Dell Dimension 5000?

---

### Post by ShirishAg75 on 2005-12-20
[QUOTE=tseliot]```
sudo gedit /etc/apt/sources.list
```

uncomment (i.e. remove the "##" before the lines) all the lines beginning with "deb-http" and "deb-src" but the backports.

Save and exit

Then:
```
sudo apt-get update
```

```
sudo apt-get install linux-686
```[/QUOTE]


Just saw this & couldn't help wondering, why the backports should be commented? Noob here but would like to know.

---

### Post by tseliot on 2005-12-20
[QUOTE=shirishag75]Just saw this & couldn't help wondering, why the backports should be commented? Noob here but would like to know.[/QUOTE]
You shouldn't keep the backports enabled all the time. Use them only when you need it (but the backports won't damage your Ubuntu installation).

Anyhow if you need to install a new kernel there's no problem whatsoever.

---

### Post by ShirishAg75 on 2005-12-21
can u tell why backports shouldn't be enabled all the time. I'm trying to also look the issue up at the wiki but if not there then it should be added if there's a reason to be used sparingly. I know there is some difference between apt-get update & apt-get upgrade but haven't been able to know the difference. Maybe related or not? Sorry for going off-topic here.

---

### Post by tseliot on 2005-12-21
[QUOTE=shirishag75]can u tell why backports shouldn't be enabled all the time. I'm trying to also look the issue up at the wiki but if not there then it should be added if there's a reason to be used sparingly. I know there is some difference between apt-get update & apt-get upgrade but haven't been able to know the difference. Maybe related or not? Sorry for going off-topic here.[/QUOTE]
The backports are packages which have been ported from Dapper Drake (the development/unstable version of Ubuntu). Therefore you'd better not keep them enabled when you update your system (but it won't break anything).

Please read this document (it explains it's safe to use them):
[http://ubuntuforums.org/showthread.php?t=40291]("http://ubuntuforums.org/showthread.php?t=40291")

---

### Post by rajaiskandarshah on 2005-12-22
upgraded from linux-386 to linux-686 via synaptic on my acer travelmate 2301lci notebook with intel celeron m 320 1.3ghz processor and 512mb ddr ram.

starting oo.o1.9.x is now about 50% faster. in i386 about 25 sec, in i686 about 15 sec. speed is very noticeable when opening large files (more than 1mb). a ms word file of 4mb size opened up in about 10 sec. a ms ppt file of 1mb size opened up in about 15 sec.

---

### Post by myha on 2005-12-23
Hi all!

I'm having a little trouble here and I need some help...

I installed linux-686 kernel (have pentium M) and everything worked ok, the speed increase was noticable. But today I booted up my computer (with 686 kernel) and there was an update from 2.6.12-9-686 to 2.6.12-10-686 kernel. I installed kernel, rebooted and now I get:

RAMDISK: ran out of compressed data
invalid compressed format (err=1)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

:/
I only have 1 686 kernel in my grub, it somehow erased 9-686 and left only 01-686.
When I boot with my old kernel (386) everything is ok, and the grub parameters are the same as with the 686.

Any idea?

edit: Can someone tell me which package to remove and than to install again? Everything with linux*-686 maybe?

---

### Post by kleeman on 2005-12-23
[QUOTE=myha]Hi all!

I'm having a little trouble here and I need some help...

I installed linux-686 kernel (have pentium M) and everything worked ok, the speed increase was noticable. But today I booted up my computer (with 686 kernel) and there was an update from 2.6.12-9-686 to 2.6.12-10-686 kernel. I installed kernel, rebooted and now I get:

RAMDISK: ran out of compressed data
invalid compressed format (err=1)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

:/
I only have 1 686 kernel in my grub, it somehow erased 9-686 and left only 01-686.
When I boot with my old kernel (386) everything is ok, and the grub parameters are the same as with the 686.

Any idea?

edit: Can someone tell me which package to remove and than to install again? Everything with linux*-686 maybe?[/QUOTE]
Sounds a bit like corrupted downloads of the new kernel. Try reinstalling linux-image-**-686 (synaptic can do this- look in packages menu)

---

### Post by myha on 2005-12-23
Hi!

I reinstalled everything with *686 from synaptics and it works again! :)

Thank you very much!

br, Miha

---

### Post by canadianwriterman on 2005-12-23
I have an AMD Athlon 2000XP (which is not 64 bit) and installed the k7 kernel last night. I can't say I really notice any difference. Anyone else with a similar experience?

Also, I notice in some previous threads that the file to install is kernel-k7. I installed one called image-kernel-**-k7. Is there a difference?

---

### Post by punkr0x on 2005-12-23
Hey guys, forgive my ignorance:  is an AMD mobile semperon 2800+ a k7 processor?  (Which kernel is best suited for my processor?)

---

### Post by tseliot on 2005-12-23
[QUOTE=canadianwriterman]Also, I notice in some previous threads that the file to install is kernel-k7. I installed one called image-kernel-**-k7. Is there a difference?[/QUOTE]
No, it's the same kernel. The main difference between linux-k7 and linux-image-2.6.12-10-k7(etc.) is that the former is a kind of metapackage which installs also the restricted modules and headers (things you can do whenever you want)

---

### Post by tseliot on 2005-12-23
[QUOTE=punkr0x]Hey guys, forgive my ignorance:  is an AMD mobile semperon 2800+ a k7 processor?  (Which kernel is best suited for my processor?)[/QUOTE]
Yes, that's right.

---

### Post by canadianwriterman on 2005-12-25
[QUOTE=tseliot]No, it's the same kernel. The main difference between linux-k7 and linux-image-2.6.12-10-k7(etc.) is that the former is a kind of metapackage which installs also the restricted modules and headers (things you can do whenever you want)[/QUOTE]

Should I install the restricted modules and headers? What do they do?

---

### Post by tseliot on 2005-12-25
[QUOTE=canadianwriterman]Should I install the restricted modules and headers? What do they do?[/QUOTE]
Kernel headers are useful if e.g. you need to install the drivers for your graphic card or compile the modules for vmware, etc. In other words it's almost like having the kernel source.

The restricted modules contain the modules (which are already compiled for your kernel) such as:
```
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcdslusba,
   fcpci, fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)
 - ltmodem (Winmodem)

These modules are "restricted" because they are not available under a
completely Free licence.
```

---

### Post by canadianwriterman on 2005-12-25
Thanks, tseliot. Sounds like those are capabilities I haven't needed. I'll probably leave well enough alone and not install them for now. I was curious about whether they would enhance the performance of the K7 kernel, as I haven't seen any difference between it and the i386 kernel I have been running under.

---

### Post by tseliot on 2005-12-25
[QUOTE=canadianwriterman]... as I haven't seen any difference between it and the i386 kernel I have been running under.[/QUOTE]
that's the reason of the title of this thread: "Picking the Kernel thats Right for You ([COLOR="Red"]Possible[/COLOR] Speed Increase)".
Not everybody has a speed increase.

---

### Post by infoseeker on 2005-12-25
I have a Celeron D at 2.8 GHz
I presume the 686-smp kernel would be ok?

---

### Post by tseliot on 2005-12-25
[QUOTE=infoseeker]I have a Celeron D (with HT) at 2.8 GHz
I presume the 686-smp kernel would be ok?[/QUOTE]
686 for sure. I don't know if "smp" is right for you though (anyhow it won't do any damage)

---

### Post by eriqk on 2005-12-25
I would like to upgrade to the K7 kernel. Does this affect anything I've compiled myself? Do I need to rebuild anything?

Groet, Erik

---

### Post by poofyhairguy on 2005-12-25
[QUOTE=eriqk]I would like to upgrade to the K7 kernel. Does this affect anything I've compiled myself? Do I need to rebuild anything?

Groet, Erik[/QUOTE]


Unless you compiled your own kernel or kernel drivers (such as Nvidia by hand), its fine.

---

### Post by quonsar on 2005-12-26
wow. installed the 2.6.12-10-686 kernel on this 1.4 ghz celeron and this 3 week n00b is getting a whole new respect for ubuntu. big diff on this box! gnome is very much snappier now! then i installed firefox 1.5 and now i'm surfing like greased lightning. :-D

---

### Post by byen on 2006-01-05
Hey poofy,
Just installed the k7 kernal for my amd and so far it looks good.will try to update here if any wierdness occurs. So if anyone has an AMD XP 2800+ processor....i can surely say this install would work for you too. 
Thanks yet again poofy and goodluck.

PS- I get the kubuntu boot splash for some reason instead of ubuntu... I tried removing kubuntu usplash through synaptic but the problem persists. Not a big deal but Id rather have ubuntu there..... any ideas?
thanks guys.

---

### Post by byen on 2006-01-06
ok never mind. I fixed it. If anyone comes across a similar problem do this:
Open the terminal and type:
sudo update-alternatives --config usplash-artwork.so
(this will open a selection box that lets you decide which splash you would prefer 1.default(ubuntu) 2.kubuntu and 3.xubuntu. select one and then press <enter>)
Now enter:
sudo dpkg-reconfigure linux-image-`uname -r`
(this will build your choice into the initramfs) (enter)

It will take about 10-30 seconds and thats it you are done. 
Restart and enjoy!

---

### Post by poofyhairguy on 2006-01-06
[QUOTE=byen]Hey poofy,
Just installed the k7 kernal for my amd and so far it looks good.will try to update here if any wierdness occurs. So if anyone has an AMD XP 2800+ processor....i can surely say this install would work for you too. 
Thanks yet again poofy and goodluck.

PS- I get the kubuntu boot splash for some reason instead of ubuntu... I tried removing kubuntu usplash through synaptic but the problem persists. Not a big deal but Id rather have ubuntu there..... any ideas?
thanks guys.[/QUOTE]


Glad to help. Anything thats an Athlon should be able to use a K7 kernel.

I use upower personally:

[https://wiki.ubuntu.com/Upower?highlight=%28upower%29](https://wiki.ubuntu.com/Upower?highlight=%28upower%29)

---

### Post by zahidism on 2006-01-06
hmm, i have a 2.0 ghz Pentium M dothan, do you think installing the 686 will increase performance?  im worried it might a.) ruin my ATI driver (although i never installed one i just use the 2d one ubuntu installed) and b.) ruin my ndiswrapper driver because i spent hours upon hours fixing that.  do you think those are possibilities?

---

### Post by poofyhairguy on 2006-01-06
[QUOTE=zahidism]hmm, i have a 2.0 ghz Pentium M dothan, do you think installing the 686 will increase performance?  im worried it might a.) ruin my ATI driver (although i never installed one i just use the 2d one ubuntu installed) and b.) ruin my ndiswrapper driver because i spent hours upon hours fixing that.  do you think those are possibilities?[/QUOTE]


If you EVER are worried about something like this...then just don't. Really. It won't make a huge difference.

---

### Post by zahidism on 2006-01-06
hmm, well i just updated and everything seems to be working fine.  how do i tell what kernel im running? (i know i clicked it in GRUB but i just want to see it in the terminal)

---

### Post by tseliot on 2006-01-07
[QUOTE=zahidism]hmm, well i just updated and everything seems to be working fine.  how do i tell what kernel im running? (i know i clicked it in GRUB but i just want to see it in the terminal)[/QUOTE]
type:
```
uname -r
```

---

### Post by Zlatan on 2006-01-25
should i care to install a new kernel if i'm using 2.6.12-10-386 on my old amd athlon 1600+ and nvidia geforce2 64mb and with 256mb RAM?
thank you

---

### Post by oimon on 2006-01-25
It would be interesting if we could quantify these speed increases with a benchmark tool, rather than guesswork. 
Anyone know of a good tool to test it before and after?

It would be particularly useful to make a list with results from different CPUs

---

### Post by zasf on 2006-01-25
```
 sudo apt-get install linux-686
```

I recently compiled my own kernel, following tseliot's guide for both fun and challenge. Are these kernel just precompiled ones with processor specific options?

I checked my own kernel config and I noticed that I didn't flag the right cpu (686 I guess since I have a pentium M), can you take a look at it (attachment)? Should I recompile?

Thanks

[COLOR="Red"]EDIT:[/COLOR] I recompiled it with Pentium-M option enabled and took the chance to install new ati drivers :cool:

```
matteo@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5582 (8.21.7)

matteo@ubuntu:~$ uname -r
2.6.12-z2
```

---

### Post by thoffmeyer on 2006-01-25
awsome guide, thanks :)

---

### Post by Twizz on 2006-01-25
Thanks a lot.  This worked really good for me.  I run a P4 2.8GHz HT computer.  I noticed things like OO, and AmaroK loading a lot faster.

---

### Post by stalefries on 2006-01-26
just installed 686, no hitches yet!

---

### Post by eriqk on 2006-01-26
[QUOTE=poofyhairguy]Unless you compiled your own kernel or kernel drivers (such as Nvidia by hand), its fine.[/QUOTE]

Alright, that's very cool.
Sorry about the late reply, btw.

Groet, Erik

---

### Post by dcast on 2006-01-26
a little bit of a speed increase with my p3 thanks a lot.

---

### Post by kenweill on 2006-02-07
I have a question.

What if i install and use linux-686, can I still install 'package-386.deb' files? 
Or I should have to install 'package-686.deb' files?

I was just confused. Installing 386.deb files under 686 linux kernel.

---

### Post by Subbu.exe on 2006-02-07
I'm a Little Confused, The Stock Kernel Which Comes with the CD is Linux-386,
I Had to Compile my Own Kernel Because I Had to Add some Drivers for my Lan Card. I Selected the Processor as **Opetron/Athlon64/K8**, But I havent Installed K7, Since I Hace Compiled my Own Kernel Do I Have to Install K7 too?

---

### Post by tseliot on 2006-02-07
[QUOTE=Subbu.exe]I'm a Little Confused, The Stock Kernel Which Comes with the CD is Linux-386,
I Had to Compile my Own Kernel Because I Had to Add some Drivers for my Lan Card. I Selected the Processor as **Opetron/Athlon64/K8**, But I havent Installed K7, Since I Hace Compiled my Own Kernel Do I Have to Install K7 too?[/QUOTE]
No, what you chose is ok. Stick to your kernel.

---

### Post by tseliot on 2006-02-07
[QUOTE=kenweill]I have a question.

What if i install and use linux-686, can I still install 'package-386.deb' files? 
Or I should have to install 'package-686.deb' files?

I was just confused. Installing 386.deb files under 686 linux kernel.[/QUOTE]
You can install 386.deb with a 686 or a k7 kernel. Don't you worry ;)

---

### Post by VCSkier on 2006-02-07
please excuse me if my question is stupid; i'm very new to linux...

how does this compare to the vanilla kernel or nitro kernel?

---

### Post by tseliot on 2006-02-07
[QUOTE=VCSkier]please excuse me if my question is stupid; i'm very new to linux...

how does this compare to the vanilla kernel or nitro kernel?[/QUOTE]
What do you mean?
A vanilla kernel is the kernel source from kernel.org
A nitro kernel is a vanilla kernel which has been patched with a nttro patch and should perform better but it might cause you problems (never tried myself though).
Ubuntu kernels (the ones which this guide refers to) are vanilla kernels patched by Ubuntu developers with their patches. You can find them in the repositories. They should work fine (I use them all the time).

If you are a newbie you should stick to Ubuntu kernels for now. Use 686 if you use a pentium or k7 if you use an AMD CPU.

---

### Post by VCSkier on 2006-02-07
thanks tseliot. *goes to work on 686 kernel*

---

### Post by MystaMax on 2006-05-24
Hello I have attempted the instructions here and I am having problems. 1st thing I noticed is that the howto states not to install the image packages (also clarified [here]("http://www.ubuntuforums.org/showpost.php?p=466105&postcount=15")), but after running "sudo apt-get install linux-686-smp" it states it'll install:

[LIST]
[*]linux-image-2.6.12-10-686-smp
[*]linux-image-686-smp
[*]linux-restricted-modules-2.6.12-10-686-smp
[*]linux-restricted-modules-686-smp[/LIST]I also got the same results when attempting this through synaptic.

After installing these packages (just to see if it'll work) I am unable to use X once I log in. After logging in, it'll lock up maybe after 20 seconds. I have a [thread]("http://www.ubuntuforums.org/showthread.php?p=1029751") started which has notes on what I've done. I got some help from some folks on IRC (great place for quick support btw) stating that he had similar problems and that I need to make some changes to my xorg.conf file. Which I did, and it worked just fine for a while at least. I attempted to VNC to the server from my house (the server is @ work) and the computer locked up, just as it had previously done. 

I'm in a real bind, and not sure what to be looking for. I dont even know why its locking up (possibly something w/ X, not sure). Even if I did, I do not know how to diagnose the problem. Can someone help me out? Thanks. Here are my system specs:

Dell PowerEdge 2850 (2U Server)
ATI Technologies, Inc. Radeon 7000 VE
Intel Xeon Dual 2.8
2 GIGS of RAM
700 GIGS setup in a RAID-5 (6 Total hard drives)

[Thread w/ details on my issue]("http://www.ubuntuforums.org/showthread.php?p=1029751")

---

### Post by Getwild2 on 2006-05-26
This is a total noob question but I am a noob, therefore it is okay.  ](*,) 

I'm brand-new to Ubuntu and even Linux in general.  I was talking to my buddy at work who runs Gentoo and he mentioned having multiple kernels to fall back on so that spawned my research.  

I run an AMD Athlon XP processor, so I would need the K7.  IF I run sudo apt-get install linux-k7, is it going to just install an 'additional' kernel that will show up in Grub on my next boot?  Will it mess anything up with my current kernel?  Anything additional I'd need to do for this secondary kernel? 

Also, is there such a thing as saving an additional copy of my current kernel the way it is right now so revert back to if I stumble upon issues later?  Meaning, sort-of like the Windows Snapshot utility?  I ask because I JUST set my system up and it is running very well.  I would like to revert back to this point if at all possible in the event there is a major catastrophe.  I wondered if a backup copy of my current kernel is possible or is what I am seeking. 

Thanks for the kernel education, this is a great thread.

---

### Post by jazzgossen on 2006-05-27
[QUOTE=Getwild2]
I run an AMD Athlon XP processor, so I would need the K7.  IF I run sudo apt-get install linux-k7, is it going to just install an 'additional' kernel that will show up in Grub on my next boot?  Will it mess anything up with my current kernel?  Anything additional I'd need to do for this secondary kernel? 
[/QUOTE]

Exactly. The kernel itself will not be changed. You can just select whichever kernel you want to run when you boot. The kernel itself doesn't change any of your settings, so it is perfectly safe to try it. Something that can happen though, is that you have some *kernel modules* that aren't in the new kernel. In that case, some things won't work, but you will still be able to simply reboot with your old kernel instead.

---

### Post by zigoto on 2006-05-30
Hi, i have installed 686 smp and work fine... But when grubs start i have 2 kernel versions, how can i remove 
> 
ubuntu, Kernel 2.6.15-23-386
ubuntu, Kernel 2.6.15-23-386(recovery mode)



Regards!

---

### Post by zigoto on 2006-05-30
Hi, if i install 686 the openoffice does not work!
What can i do??

---

### Post by msekolpsu on 2006-05-30
How would I get the correct setup going for an Intel Pentium D 805?

It's a dual core 64-bit processor.  I can get both processors to show up running the i386 distro and then adding in the linux-686-smp and headers.

however...

when I go to run VMWare, it tells me that 64 bit guest OSes won't run, which I'm assuming means I'm not in 64 bit mode.

I tried running the AMD64 distro, but that's a no go either because I can't get both processors to show up (since the linux-686-smp doesn't work in that build).  Any thoughts?  Is there any way to confirm the 64-bit mode?

Great thread btw
 
Thanks!

---

### Post by Keith_Beef on 2006-05-30
[QUOTE=guyomarj]
[LIST=1]
[*]Why is there still a "**i686**" thing when I run the command:
j```
yves@ubuntu:~$ uname -a
Linux ubuntu 2.6.12-9-k7 #1 Mon Oct 10 13:47:52 BST 2005 i686 GNU/Linux

```
[/LIST]
[/QUOTE]

man uname

The i686 is what you would get from just uname -m to find out the CPU type.

K.

---

### Post by Keith_Beef on 2006-05-31
I've read through this thread with interest.

I can't remember what the box said, when I bought this CPU. Here's what /proc/cpuinfo tells me:
```

$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm)
stepping        : 0
cpu MHz         : 1152.769
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips        : 2277.37
```

So I downloaded and installed the linux-k7 virtual package, and I'll try running that K7 kernel tomorrow.

Several posts in the thread claim things like "definite speed increase", "gnome is snappier", even that the CPU temperature is lower. 

**Are there any benchmarking utilities I can use** to see if there really is any performance gain?

I'm trying right now to get lm-sensors and the Gnome Sensors Applet 1.5.2 working, to check the temperatures... 

```
$ sensors
Philips -i2c-2-60
Adapter: bt878 #0 [sw]

tveeprom-i2c-2-50
Adapter: bt878 #0 [sw]
```

and the applet tells me "No sensors found"


Beef.

---

### Post by tommcd on 2006-05-31
Thanks for this great thread! This cleared up a lot of confusion for me about the various kernels. I did:
sudo apt-get install linux-k7
for my AMD socket 754 Athlon64 2800+ CPU and it installed perfectly, along with the linux-restricted-modules for k7.

tom@ubuntu02:~$ uname -r
2.6.12-10-k7
tom@ubuntu02:~$

---

### Post by ELD on 2006-06-05
I have an AMD Athlon XP so do i installed the k7 kernel?

---

### Post by bruce89 on 2006-06-08
I don't think creating a spesification is a good idea, especially one with such a long name - [https://launchpad.net/distros/ubuntu/+spec/ubuntu386-right-kernel-automatic-picking](https://launchpad.net/distros/ubuntu/+spec/ubuntu386-right-kernel-automatic-picking)

---

### Post by syxbit on 2006-06-10
i have a core duo, so i'm gonna try 
```
sudo apt-get install linux-686-smp
```
i assume thist works in Dapper ?

btw. from what i understand, i just type the above code, then reboot into that kernel, and then install my ati drivers just the same as i did before ?
another question. Does the above code just give me the 686smp kernel version of the latest kernel, or is it an older kernel ?
i'm wondering, cause this was written in the days of breezy.
thanks

---

### Post by pubwho on 2006-06-10
It doesn't seem to work for me. What am I doing wrong?

```
$ sudo apt-get install linux-restricted-modules-`uname -r`-nvidia-legacy
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-restricted-modules-2.6.15-23-k7-nvidia-legacy
```

---

### Post by OPaul on 2006-06-11
I installed 686-smp, but when I boot up only 686 and 386 are in the grub menu (I was previously using 686). When I look in Synaptic it shows 686-smp installed. But in the /boot/ folder I don't see 686-smp. Does 686-smp overwrite 686 and keep the 686 name? How can I tell if Hyperthreading is running?

---

### Post by Twizz on 2006-06-11
[QUOTE=OPaul]I installed 686-smp, but when I boot up only 686 and 386 are in the grub menu (I was previously using 686). When I look in Synaptic it shows 686-smp installed. But in the /boot/ folder I don't see 686-smp. Does 686-smp overwrite 686 and keep the 686 name? How can I tell if Hyperthreading is running?[/QUOTE]
I think if you go to System Monitor, under the Resources tab, it should show 2 CPU's running.  When I boot up it only sayd 686, and I have the smp one installed.

---

### Post by OPaul on 2006-06-12
[QUOTE=Twizz]I think if you go to System Monitor, under the Resources tab, it should show 2 CPU's running.  When I boot up it only sayd 686, and I have the smp one installed.[/QUOTE]
Should it show 2 even if I have 1?

---

### Post by Twizz on 2006-06-12
It should if you have the hyperthreading on your P4.  It makes it so it works as 2 CPU's even if you have one.

---

### Post by OPaul on 2006-06-12
[QUOTE=Twizz]It should if you have the hyperthreading on your P4.  It makes it so it works as 2 CPU's even if you have one.[/QUOTE]
Well I'm pretty sure I have one of the three P4-Ms with HT, but the Resources tab is only showing 1 CPU. Is there another way I can tell if I'm running the 686-smp kernel and not just 686?

---

### Post by Twizz on 2006-06-12
It should be   ```
uname -a  
```  I would of posted this before, but I just figured it out.  Still learning my way around linux.

---

### Post by OPaul on 2006-06-12
[QUOTE=Twizz]It should be   ```
uname -a  
```  I would of posted this before, but I just figured it out.  Still learning my way around linux.[/QUOTE]
Ah, I was doing uname -r. Yea, -a says smp. Thanks.

Now does this mean my processor doesn't support HT? Because I do only have 1 CPU listed in Monitor.

---

### Post by Twizz on 2006-06-12
I think it dosent then.  But I'm not 100% sure on that.

---

### Post by Krusty Ruffle on 2006-06-13
[QUOTE=pubwho]It doesn't seem to work for me. What am I doing wrong?

```
$ sudo apt-get install linux-restricted-modules-`uname -r`-nvidia-legacy
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-restricted-modules-2.6.15-23-k7-nvidia-legacy
```[/QUOTE]

I'm just guessing, but I think you need a space between `uname -r` & -nvidia-legacy

---

### Post by jakeee on 2006-06-13
I have question. uname -m tells that my processor is i686. My processor is AMD Athlon XP 1600+. So should I pick 686 or k7?

---

### Post by galeron on 2006-06-13
On 6.06 with a Pentium 4 HT processor, I get the following:

dick@ubuntu:~$ sudo apt-get install linux-686-smp
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-686-smp

Anyne knows why this is happening?

---

### Post by Twizz on 2006-06-14
[QUOTE=galeron]On 6.06 with a Pentium 4 HT processor, I get the following:

dick@ubuntu:~$ sudo apt-get install linux-686-smp
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-686-smp

Anyne knows why this is happening?[/QUOTE]
Wild Guess but maybe you dont have the repository you need selected.  I think I'm wrong... but who knows...

---

### Post by lzap on 2006-06-18
Yes

---

### Post by ????? on 2006-06-18
How do I disable the effect you see when you use a launcher on the panel?


(New kernel, 686)

---

### Post by chameleonkid on 2006-06-19
Do I have to just delete the old kernals from the GRUB menu.lst or from the /boot? OR both? I am curious because I got the GRUB error 15 a few days back which caused me some headaches...

---

### Post by lzap on 2006-06-19
Just from grub. To uninstall old versions of kernel use Synaptic! You need to remove linux-image-[old version] etc

---

### Post by gmanpsycho on 2006-06-19
OK I downloaded the SMP kernel (thanks for the guide). However when I boot up into it, I have no sound and I'll need to re-install my nVidia drivers and also reconfigure my wireless card. But I'm puzzled about some of the other information in this thread. I am currently running the 686 kernel (I have a Dell Inspiron 5150 P4 3.2GHz with HT) and I see two CPUs in the System Monitor (see partial screenshot). After booting up with the SMP kernel I still only see 2 CPUs in Sys Monitor.

---

### Post by nealklomp on 2006-06-20
dell inspiron 6m, running 6.06, went up to 686, more responsive and stable. Less degradation of0 performance when OS is under strain. In Xfce it is stupid fast, although in Gnome the drop off is not as much as before.
Thanks Poof and TS.

---

### Post by Franko30 on 2006-06-21
Hello,

in Ubuntu 6.06 LTS, did anybody encounter the following bug?

[https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/50180](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/50180)

Secenario: Gnome desktop loaded, no special applications running.

With the linux-686 kernel and a Pentium M processor (like on my Latitude X1) the CPU load never drops below 40-50%. Whereas, using the linux-386 kernel in the same scenario, CPU load drops to 5-6%.

I switched back to only using the linux-386 kernel.

Cheers

Franko30

---

### Post by Gr4v3 on 2006-06-21
Hey thanks for all your works keep up guys

---

### Post by snek on 2006-06-23
I was wondering if there's a K8 32bit kernel..
Cuz I have a Sempron64 3400+ but am running 32bit ubuntu.
Right now I am using the K7 kernel which seems to be working fine, but I guess it would be even more optimised if I could run a K8 kernel?

---

### Post by dronepower on 2006-06-24
thanks for the help

---

### Post by Brando569 on 2006-06-24
[QUOTE=snek]I was wondering if there's a K8 32bit kernel..
Cuz I have a Sempron64 3400+ but am running 32bit ubuntu.
Right now I am using the K7 kernel which seems to be working fine, but I guess it would be even more optimised if I could run a K8 kernel?[/QUOTE]

yea i wish there was the same thing since i have an amd64 x2 +3800 but im running the k7 kernel. hopefully 64 bit will be (easily) usable soon....

---

### Post by DavidFourer on 2006-06-25
I installed the 686 kernel with synaptic first and then again as suggested here with [COLOR="Navy"]sudo apt-get install linux-686[/COLOR].  Either way, I get a peculiar slow-down.  All the menues operate with delays.  I have to click the trackpad buttons real slowly.  It seems the hold-up is with some simple graphic rendering.  Also some other minor bugs I don't understand.  

Rebooting and seldecting 386 kernel from the GRUB menu fixes the problem (thanks for your help on this).  My Dell inspiron 6000 packing slip says I have Intel Celeron M processor.  

First, how do I set the grub to boot 386 kernel automatically, for the time being.  2)what might be wrong?  3)what processor speed diagnostics come with Dapper and do I really want the 686 kernel?

I was having a lot of trouble with Breezy and the Dapper upgrade was a big help.  Everything worked well after that, untill I tried to install the 686 kernel.

---

### Post by OPaul on 2006-06-25
[QUOTE=DavidFourer]
First, how do I set the grub to boot 386 kernel automatically, for the time being. [/QUOTE]
Temporary, you can modify the /boot/grub/menu.lst file, and place the 386 section above the 686.

---

### Post by Schroeder on 2006-07-01
So, since I am running Dapper Drake on a Acer Centrino Laptop I thought it would be a good idea to upgrade from 386 to a 686 kernel (2.6.15-25-686). Installation worked like a charm and there were no errors whatsoever (boot up fine). 

Is there a difference between SMP and not-SMP kernels? I tried installing apt-get install linux-686-smp first and then realized that my processor doesnt have hyperthreading. So I deinstalled and installed with apt-get install linux-686. Now, uname -a still says the 686 SMP kernel is installed. Whats up with that? :-s 

I noticed a slight overall speed increase using the new kernel but it definitely didnt change too much.  

Chris

---

### Post by OPaul on 2006-07-02
[QUOTE=Schroeder]... So I deinstalled and installed with apt-get install linux-686. Now, uname -a still says the 686 SMP kernel is installed. Whats up with that? :-s ...
Chris[/QUOTE]
I also noticed this when going back to just 686 from 686-SMP.

---

### Post by Exile29 on 2006-07-04
I have an AMD64 3200.
I was running 386 but after reading this post I switched to k7. 
Works great! Thanks!!!

---

### Post by nickless on 2006-07-04
This is really nice! I was always too lazy to built my own kernel, well it seemed not very easy, too. I installed the k7 alternative and Im pretty shure that everything is a little faster now :D and even my mother could have typed this in the terminal and reboot. NVDIA card works fine, too.
Thanks!

---

### Post by PingunZ on 2006-07-04
If I install the k7 kernel, will I be able to run 32bit-only software ?


Grtz PingunZ

---

### Post by raffytaffy on 2006-07-06
Sony Vaio VGN-FS660/W with 1.7ghz pentium M ..changed to i686 kernel..rebooted..works good...not much differance...still testing everything

---

### Post by michael1977 on 2006-07-07
I recently installed the k7 kernel I am running a laptop with an AMD XP+ 3000 with 1 gb ram.  I did not have to re-install the nvidia drivers I had installed under 386 in fact in my terminal it stated the change for the nvidia drivers downloaded them installed them and bang I was up and running again and did not loose XGL Compiz through the whole thing.  I did use the terminal to install as opposed to synaptic.  Graphics card is Nvidia Geforce go 420 something.  

I have noticed at least maybe just in my mind that things are a tiny bit more responsive when opening and closing programs.  Could be wishfull thinking lol.

---

### Post by rgsproductions on 2006-07-09
New to ubuntu.  install, setup and documentation is great.  Upgraded kernal from 386 to K7 with the nvidia drivers in 10 min and all is fantastic.  I did it through  synaptic and everything was configured right.  Great forum

---

### Post by william_nbg on 2006-07-28
I have a noob hardware question.

Last year a picked up an amd 64 bit, 939 pin cpu from a friend.

OK, I knew enough to install the K7 kernel - no problem, works good.

Though, as I was looking in the device manager I noticed the cpu says it's a K8 hyper-transport: my question is, because I don't have the paperwork on this cpu is, how do I tell if it's a dual core and should be using the dual core cpu??

---

### Post by tseliot on 2006-07-28
> **william_nbg said:**
> I have a noob hardware question.

Last year a picked up an amd 64 bit, 939 pin cpu from a friend.

OK, I knew enough to install the K7 kernel - no problem, works good.

Though, as I was looking in the device manager I noticed the cpu says it's a K8 hyper-transport: my question is, because I don't have the paperwork on this cpu is, how do I tell if it's a dual core and should be using the dual core cpu??

It's not dual core. Mine has "hyper-transport" too

---

### Post by william_nbg on 2006-07-28
Thanks for the quick reply!

Another hardware noob question if you have a second.

If I got an amd dual core do you need a special motherboad for it as well, or will it run on the same 939 socket board?

---

### Post by william_nbg on 2006-07-28
OK - now I'm just being lazy.

I had a look on the asus site (my board is an asus a8n) and according to their site it should work??

---

### Post by jharris on 2006-07-28
> **william_nbg said:**
> Thanks for the quick reply!

Another hardware noob question if you have a second.

If I got an amd dual core do you need a special motherboad for it as well, or will it run on the same 939 socket board?
You'll be fine with a regular AMD Dual Core X2 on a 939 socket. However, if you decide to opt for an X2 AM2, you'll need a new 940 socket motherboard.

---

### Post by Malta Soron on 2006-07-28
Actually a AM2 motherboard. There are also 940 pin motherboards on the market, but they aren't compitable with AM2.

---

### Post by william_nbg on 2006-07-28
One more simple hardware question:

Maybe this is just a Windows-mind-wrap feeling, which I haven't yet shaken loose. If I pop off the 64 bit amd, and pop on a 64 bit dual core amd, would I have to do a fresh install or would it work well on the same install??

Any major hardware change on windows I would have done a fresh install.:sad:

---

### Post by jms1989 on 2006-08-02
Hi, My computer is running a Pentium 4 HT (Hyper-threading) 2.8GHz proccesser on a dual boot system, What would be the recommanded kernal?

---

### Post by Ftpmaster on 2006-08-02
> **jms1989 said:**
> Hi, My computer is running a Pentium 4 HT (Hyper-threading) 2.8GHz proccesser on a dual boot system, What would be the recommanded kernal?

686-smp of course.

---

### Post by evil_elman on 2006-08-02
I'm running both the 386 and 686 kernels on my laptop (which have got a Pentium M 1.6 GHz with 533MHz FSB, 'Centrino mkII') for testing purposes.

Whenever I run the 686 kernel the computer is slower. I can really notice it. For example, the animation for minizing windows is slower, mounting the / file system during boot i slower, buttons reacting to mouse clicks are slower, video playback is not possible (jerky) and general 2D is slower when moving windows on top of other windows (it doesn't repaint the window in the background properly).

My fglrx driver works fine with both 386 and 686 kernerls. The 2D is fairly sluggish with 386 kernel as well but I can live with that. Not as bad as witht he 686 kernel, though.

SimplyMEPIS 6, SUSE Linux 10.1 and the Edgy Knot 1 release with 686 kernels works fine, but not Dapper for some reason. 

Any ideas?

Complete HW specs and other general info can be found here: [http://www.rotoni.net/travelmate_4601LCi.html](http://www.rotoni.net/travelmate_4601LCi.html)

---

### Post by gurgle on 2006-08-02
what smp kernel can i use for ubuntu 64-bit version?

---

### Post by H.E. Pennypacker on 2006-08-02
Some people have reported that switching to the 686 kernel on an Intel Celeron M processor results in a speed difference, but I have not found that to be true in my case.  I switched back to 386, but for no particular purpose.  Speed is the same on both kernels.

---

### Post by MyBigToe on 2006-08-14
I installed the 686 kernel (Intel P4 3.06ghz), but after booting to the sign in screen, i have keyboard/mouse issues.

Either my keyboard wont work or my mouse and keyboard wont work, but the keyboard worled when selecting which to boot from on the Grub menu.
Have had no problems with 386 kernel.

Any suggestions?

---

### Post by techgnome on 2006-08-14
Hi, I posted this first on the laptop board (since it concerns my Vaio laptop), but thought I would try here, too.

I am running Ubuntu 6.06 on a Sony Vaio SZ240 with a Core Duo processor. I have followed all of the core duo recommendations I can find online for getting the dual processor feature running to no effect. I started with the Live CD install, then ran sudo apt-get update && sudo apt-get install linux-686-smp. After rebooting, /proc/cpuinfo atill shows only one processor. Booting this same system into Windows XP shows both processors running, so I know it can work. Here is a capture of both my uname -a and cat /proc/cpuinfo:

$ uname -a
Linux techgnome 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006 i686 GNU/Linux

$ cat /proc/cpuinfo
processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 14
model name : Genuine Intel(R) CPU T2300 @ 1.66GHz
stepping : 8
cpu MHz : 1667.113
cache size : 2048 KB
physical id : 0
siblings : 1
core id : 255
cpu cores : 1
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 10
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor est tm2 xtpr
bogomips : 2003.30

Anyone have any ideas? Thanks in advance!

---

### Post by Klaidas on 2006-08-14
A very nice guide. 
And I finally installed a 686 kernel! :)

---

### Post by OPaul on 2006-08-15
> **Ftpmaster said:**
> 686-smp of course.
I'm a little confused. I thought SMP was a method that two processors used to communicate with one another. So what advantage does installing it with 1 processor have?

---

### Post by FizDev on 2006-08-15
Well if your processor supports HyperTrading (HT) you should get the smp kernel... otherwise..
(HT is a little bit as if you had 2 processors instead of just one)

---

### Post by secretlondon on 2006-08-15
It looks like you can't not install an SMP kernel if you have an AMD K7 CPU. 

I've got one 32 bit Athlon XP and noticed that I had an SMP kernel installed. It looks like *linux-k7* and *linux-k7-smp* both depend upon the same packages.

---

### Post by vilto on 2006-08-25
i have done every thing listed in the tutorial but .....instead of increasing the speed it decreased......im using amd athlon x2 3800+
i installed k7-smp

expecially when im using firefox its going to 40% and another around 50% some times even more......remaining all seam to be fine

im new to linux .....plz explain whts the problem is and how to fix it

---

### Post by vilto on 2006-08-25
got the problem its not kernel issue but about nvidia drivers

---

### Post by msolano on 2006-08-26
Hi!.  I did the :
"For a modern Pentium 2+ kernel for dual processors, dual cores, or hyperthreading:
sudo apt-get install linux-686-smp"

because i have a Intel Dual Core 2.8MHz.

I have a big problem with this 'cause when i boot Ubuntu with 686 kernel version my 'Mounting file system' (second step) freeze the computer.

Is there somebody with the same issue?  do you know something about this?

THanks!  ](*,)

---

### Post by pansz on 2006-09-04
> **stubby said:**
> My notebook is a Pentium M, so is that the 686 kernel ?

Of course, Yes.

---

### Post by cactaur on 2006-09-04
I installed the 686 kernel, but when I boot up, the keyboard and mouse do not respond. Tried it many times, stays consistent. When I use the 386 kernel, everthing's fine. Anyone know what's wrong?

---

### Post by djRobbieF on 2006-09-04
I wanted to try this, because I'm all about the speed - but after doing the Kernel update, I can no longer get on my wireless network.  The wireless settings are still there, but apt no longer connects, and I cannot browse, so I'm guessing I've lost my wireless card.
Is there a way to do the kernel update, but then restore drivers that "come with" the initial ubuntu install so I can still use my wireless?

THANKS!!

EDIT>> ISSUE RESOLVED.  I posted in another thread the resolution.

---

### Post by djRobbieF on 2006-09-07
HUGE speed increases - thank you!

I posted my procedure and story here:
[http://www.blog.djrobbief.com/?p=17]("http://www.blog.djrobbief.com/?p=17")

---

### Post by mighty_myte on 2006-09-07
I just found out my kernel does not support 3dnow etc.
Recently i installed winxp and was surprised by it's speed,
hopefully this will make things better.

By the way: seems like apt-get installs the Nvidia-legacy drivers automaticly.

I'll reboot now, hopefully able to post some good news.. :rolleyes:

---

### Post by aos101 on 2006-09-10
> **poofyhairguy said:**
> smp – This kernel is NEEDED to use both CPUs in a multi-CPU setting. The kernel is also required to “enable” hyperthreading in modern Pentium 4 CPUs. Also needed for dual core processors (the letters stand for Symmetric Multiprocessing). Very important to install this, as it WILL improve performance. Sorry to bold it but I think this one is the most important.[/B]

[http://en.wikipedia.org/wiki/Symmetric_multiprocessing](http://en.wikipedia.org/wiki/Symmetric_multiprocessing)
How do I know if SMP support is working?  I'm running Kubuntu 6.06 on a P4 3.06GHz HT processor, and I first saw point 10 [here](http://tips.linux.com/article.pl?sid=06/06/08/1651225&tid=50) and installed the 686 kernel (package linux-image-2.6.15-26-686).  Now I saw this HOWTO so ran this to ensure I have SMP support for my processor with HT:
```
sudo apt-get install linux-686-smp
```
uname -r returns:
```
adam@kubuntu:~$ uname -r
2.6.15-26-686
```
So would I have SMP support after that?  Thanks for any help.

---

### Post by missmoondog on 2006-09-10
just tried this on my old 800mhz celery system. along with the "how to" trick of enabling profile readahead i found yesterday, the system is not much, if any, snappier than before. always wondered if i could use the 686 kernel though.

---

### Post by missmoondog on 2006-09-11
now, i just tried this on an amd athlon xp 3000+. whoa!! slow down horsey!!
for one thing, i was using the default 386 kernel. now using the k7.

simple question though. it did automatically install the nvidia drivers, but do i have to run that command (sudo nvidia-glx-config enable) to enable/update them again? i did still get the nvidia splash screen up. just wondering if it automatically update the /etc/X11 file, before i go screwing around with that!

thanks

edit:
nope didn't have to run that command to enable them again. cool!

---

### Post by bitwise5 on 2006-09-11
I've seen plenty of this:

> **poofyhairguy said:**
> 
k7 – This kernel is recommended for a computer with a Athlon or newer AMD CPU.


But what about the kernels optimized for K8? I haven't found them in default Ubuntu repositories. 
Anyone using them with Ubuntu?

Thanks-

---

### Post by Crashmaxx on 2006-09-12
Doing this how-to I can only get the 2.6.15-23-686 kernel. How do I get it to upgrade to the 2.6.15-26-686 kernel? My laptop upgraded to 26 automatically, but the desktop won't. Any help?

---

### Post by kleeman on 2006-09-12
Go to synaptic and search for "linux-image" You will see the 26-686 version listed. Install it. The 23 version will remain on your system unless you choose to remove it manually (to save space).

---

### Post by Crashmaxx on 2006-09-12
It isn't listed, just the 26-386, not the 26-686.

---

### Post by kleeman on 2006-09-13
Well that is mighty odd. Both are on my system which is very standard. You may want to checks your repositories carefully and update synaptic. If the 686 is there for 23 and the 386 for 26 it is very odd that the 686 for 26 is not there.

---

### Post by tylerjames on 2006-09-14
I've got a Dell Inspiron 6400 with a Centrino Duo 1.83Ghz

Just installed the 686-smp kernel and now I have no sound!!!

Please help!

---

### Post by swaaye on 2006-09-18
> **snek said:**
> I was wondering if there's a K8 32bit kernel..
Cuz I have a Sempron64 3400+ but am running 32bit ubuntu.
Right now I am using the K7 kernel which seems to be working fine, but I guess it would be even more optimised if I could run a K8 kernel?

K8 is actually extremely similar to a K7. There are only a few changes to the execution core. The biggest changes between Athlon64 and Athlon are 64->128-bit L2 cache data bus, x64, and the integrated memory controller.

Personally I doubt that these kernel versions do much in terms of performance, other than the obvious benefit of the SMP kernel. You'd need to profile what is actually slowing your system down, and I bet it's not the kernel. The GUI is going to be a lot more demanding than anything else I imagine. A recompiled kernel probably nets a small percentage boost for the kernel itself.

---

### Post by buffy^ on 2006-09-19
I would really like to know to remove my old kernels.
Please could you advise, thanks.

Thanks i sorted it.

---

### Post by OPaul on 2006-09-19
> **buffy^ said:**
> I would really like to know to remove my old kernels.
Please could you advise, thanks.

Thanks i sorted it.

You can remove them via Synaptic Package Manager.

---

### Post by swaaye on 2006-09-20
By the way, the Pentium Pro fits in the 686 family too. Pentium II is actually slower than Pentium Pro per clock. :)

---

### Post by cactaur on 2006-09-20
When I use the 686-kernel, my keyboard and mouse do not work, I can't even log in. Is there a way to fix it, or is it just because the 686 isn't right for my processor. I have a Pentium 4 3.2 gHz. My Conky says that it should be 686 compatible, but it doesn't work. Any recommendations. Oh, and the 386 kernel works wonderfully.

---

### Post by MattM on 2006-09-21
<deleted>

---

### Post by jdunn on 2006-09-21
I have Kubuntu Dapper installed on a P4.  I've been using the 686 kernel and have had trouble lately installing the 686-SMP kernel (So I can enable support for Hyper Threading).  I need help.  Details are in this thread:

[http://www.ubuntuforums.org/showthread.php?t=262089](http://www.ubuntuforums.org/showthread.php?t=262089)

---

### Post by Aberrix on 2006-10-18
Is this

```
Linux haddax 2.6.15-27-k7 #1 SMP PREEMPT Sat Sep 16 02:35:20 UTC 2006 i686 GNU/Linux
```

the proper kernel I should have for my system? I installed the linux-k7-smp I am just looking for a confirmation that everything looks right now. Thanks in advance

---

### Post by rigol on 2006-11-20
[edit]Stupid me. Alright, I figured out by myself.

---

### Post by DigitalDingo on 2006-11-20
I may need some help here...
I use a dual core cpu on an i386 laptop (ASUS A6Ja), so I chose “sudo apt-get install linux-686-smp”. What do I do now? When I reboot there's no change to GRUB, and the “uname -r” gives: “2.6.17-10-generic”.
Don't I need to configure GRUB?

---

### Post by DigitalDingo on 2006-11-20
Sorry, just forget about that post. I just read that Ubuntu Edgy has dual core support as standard...

---

### Post by rajaiskandarshah on 2006-12-07
looked at synaptic for linux-686 and the note says obsolete by linux-generic (it's not marked).

does this mean that i have linux for 686 already ?

---

### Post by TDsai on 2006-12-15
Hi i have the same question as rajaiskandarshah. 

dmesg 
CPU: Hyper-Threading is disabled   <<< is this relevant on edgy?

cat /proc/cpuinfo |grep processor
processor       : 0
processor       : 1

uname -a
Linux ubuntus 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

---

### Post by mells on 2006-12-17
sorry, fairly new. I've used the SMP upgrade to the kernel has it worked?

output:

carl@Angel:~$ uname -r
2.6.17-10-generic
carl@Angel:~$ uname -a
Linux Angel 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux
carl@Angel:~$

---

### Post by WebMania on 2006-12-25
Fine, took your k7-smp example, and my AMD 64 X2 (am3 socket) is now real fast with 6.10 Kubuntu. Great help. Only my beloved Firefox shows now a little trouble. If scrolling a large screen, it goes very slow and the mouse is frozen till scrolling is finished. And its going often to teh top or bottom even if want only scroll one line. Konqueror does not show that mouse freezing! Only FF. Only advise on that? I did reinstall my Nividia drivers twice. and restarted twice, but... Any idea on that? 
But nevermind your above advise with smp was a great help. Thank you a very much, and allow me to wish you a peaceful Xmas and a great 2007.

---

### Post by Theimon on 2006-12-25
I chose the k7 kernel (going with the advice of this threads first post) at first which gave me a slight performance increase. But now I have built my own, with features specific for my cpu and with a lot less stuff I don't need etc....it's not mindblowing but it's still some performance gain. I'd recommend it to anyone :) Include some C flags as well, just for the fun of it and you're ready to go. 
Still this thread is very good to start from... :)

---

### Post by WebMania on 2006-12-27
I getting a bit crazy, yesterday all worked fine and today all back to 2.6.17-10-386!
... to shorten my post.
I have a AMD 64 X2 processor and only the 2.6.17-10-generic OS supports that fine!
No need under 6.10 for any 686 or k7/k8 variant!!
So I installed GrubEd and set the default OS to 2.6.17-10-generic.
So far so fine but then an new trouble came to the light!!

The Monitor driver was set to vesa... Makes all video output slow and it freeze the mouse whilst scrolling a page. 
As I have on board Gforce6100 Nvidia and all Nvidia drivers installed, I did set it to Gforce6 and as result Generic crashes and disables the X server!!! Whilst the 386 version -which only supports the first processor- works fine with that settings. Guess its a bug in that generic version... 

Any idea on how to set under 2.6.17-10-generic Kernel an Acer AL1916 LCD Monitor with the Nvidia Gforce6100 card without to crash the Generic X server???

RESOLVED:
did use : sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`
and all works now finest!!

---

### Post by happy-and-lost on 2007-01-02
I've probably missed a vital step... but just doing sudo apt-get install linux-686 doesn't do anything, it's still using the generic 386 kernel and there's nothing new in my menu.lst.

---

### Post by chinocracy on 2007-01-05
I will try the 686 kernel on my Celeron 1.2 Tualatin Socket 370. Please comment if this is compatible. 
Also, my install method is that I will download the linux-image-* and other deb files elsewhere, then put them into my computer and manually install. I'm on dial-up at home, so installing it from there is going to take eons. Thus, my deb-take-home method. Please comment on this, and on how multiple deb files could be installed at once. Thanks.

---

### Post by cd-r80 on 2007-01-05
Where from that grub reads partitions? It throws /root to wrong place! Fstab = /dev/hda7 & grub puts it to /dev/hda8.

Quickcam modules do not work. zb1211b wireless neither, but I already knew it.

Perhaps little faster Duron 750MHz, now. Or can a human notice +10-15% speed?
A small benchmark test?

---

### Post by chinocracy on 2007-01-05
Follow up to my last post. I tried what I described. Works. Speed difference not too noticed. But it works.

---

### Post by drippy on 2007-01-06
> **msolano said:**
> Hi!.  I did the :
"For a modern Pentium 2+ kernel for dual processors, dual cores, or hyperthreading:
sudo apt-get install linux-686-smp"

because i have a Intel Dual Core 2.8MHz.

I have a big problem with this 'cause when i boot Ubuntu with 686 kernel version my 'Mounting file system' (second step) freeze the computer.

Is there somebody with the same issue?  do you know something about this?

THanks!  ](*,)

msolano, I don't know if you ever fixed this problem, but I am getting the same thing.  I installed 686-smp (on a P4 w/ HT), and the computer completely freezes when loading the second step of "mounting file system".  Is there any way to get a more detailed output to see what is happening at that step?

---

### Post by mlissner on 2007-01-07
Hey, I just installed the smp kernel on my dual core, and when I booted it, dual core worked but my wireless card was gone! Any ideas? Does this mean I need a custom kernel, cause, though that sounds kind of fun, I'm not sure I'm interested in that kind of craziness yet.

Help?

---

### Post by .::welemski::. on 2007-01-17
What's the best kernel for Pentium D820 (Dual Core)?

---

### Post by nickless on 2007-01-19
not shure what happened
I use Ubuntu 6.10 and installed as in Dapper via apt:
```
apt-get install linux-k7 linux-headers-k7 nvidia-kernel-source
```
but this time the new kernel didn't get added to menu.lst 

EDIT: Ok I tried to find the kernel now... but I didn't succeed.
should be something like /boot/vmlinuz-2.6.15-26-k7
well.. nothing there :(

---

### Post by Ted_Smith on 2007-01-23
Hi

Firslty, thanks for writing this great HOWTO. I have recently brought home from a work A Dell Precision P530 that has two Xeon 1.7Ghz Processors in it (it was about £6000 5 years ago!). 

I have been running it with Ubuntu for a few weeks not realising it was not utilising both CPU's! Now, having installed the 686 kernel using the easy to follow instructions, it is. As a result it is churning through my work units from World Community Grid ([www.worldcommunitygrid.org](www.worldcommunitygrid.org)) for the [Ubuntu Linux Team]("http://www.worldcommunitygrid.org/team/viewTeamInfo.do?teamId=69P91PFQP1") twice as fast!! 

In addition, there's a point raised twice (between pages 1 - 8 by which time I gave up reading) about the generic 386 kernel not being able to address more than 1Gb of RAM, and the second entry loosly suggests that it now does due to updates to it. Well I have 1.5Gb on my AMD machine and this is the output of my 'cat /proc/meminfo' : 

```

** MemTotal:      1556280 kB**
MemFree:        841116 kB
Buffers:         92900 kB
Cached:         316236 kB
SwapCached:          0 kB
Active:         380248 kB
Inactive:       273392 kB
HighTotal:      655296 kB
HighFree:       163336 kB
LowTotal:       900984 kB
LowFree:        677780 kB
SwapTotal:           0 kB
SwapFree:            0 kB
Dirty:             204 kB
Writeback:           0 kB
Mapped:         321576 kB
Slab:            43716 kB
CommitLimit:    778140 kB
Committed_AS:   488568 kB
PageTables:       2004 kB
VmallocTotal:   114680 kB
VmallocUsed:     28868 kB
VmallocChunk:    84468 kB

```

Which seems to confirm that it can address > 1.5Gb RAM. 

Cheers

Ted

---

### Post by golem3 on 2007-01-25
I'd be curious to see benchmarks. I run Pentium M (Sonoma) and the 686 "feels'" better. I don't know how much of a placebo effect it is.

---

### Post by firstc624 on 2007-01-25
that is weird, i just did the guide for the k7 kernel and it didn't add anythign to my rub menu....how come?

---

### Post by BunnyEars on 2007-01-26
I just installed Ubuntu 6.10 Edgy (default install) on Jan 20 2007. On a Athlon XP 2600.

$uname -a
2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

I  am a new user, but this is what i understand. Correct me if wrong, cos many newbies read these posts.

** For all those who visited this forum thread looking to use processor specific kernels, the current version (6.10 default/generic) has made the k7/686/686-smp kernels OBSOLETE (only for upgrades). I think it applies to all the other processor specific kernels.

**As proof, refer to the "uname -a" output (in Ub 6.10). It says SMP, i686 in the default installation.
Also In Synaptics Pkg Mgr (Ub 6.10), search for "linux-k7". It will describe as OBSOLETE by linux-generic. Same for linux-686/linux-686-smp.

** edit -This might explain why some of the late2006/2007 kernel modifications by users don't show any changes in GRUB. The initial "processor specific kernels" thread was made in year 2005.

Correct me if Wrong. Hope this clarifies for the newbies :).
Jan 2007.

---

### Post by exoren22 on 2007-01-27
Hi, all. I'm a budding linux user, and I have a dual boot system on my laptop, windows and ubuntu edgy. I have a Pentium 4 mobile (not to be confused with the pentium m) with hyperthreading technology, and I tried to install the 686-smp kernel. I rebooted,and there was no new kernel to select. Just the generic. I didn't know if it was just supposed to replace it or what, but i did not notice anything different on startup, so I want to know what might be wrong. 
I typed 'sudo aptitude remove linux-686-smp' and it 'looked' like it installed. Is there another command I have to make? I'm still pretty much a newbie to linux, so help would be greatly appreciated.
**edit** Well, I just read the rest of this thread, and I realized this is how edgy works. Thx anyway.

---

### Post by jonthenerd on 2007-01-27
I've followed the instructions given and have some issues.  Here's what I'm currently running:

Ubuntu 6.10 Edgy, Athlon X2 3800

I did the install instructions for the K7-smp, and everything goes fine.  However, it DOES NOT overwrite grub - as it is still running the 686-smp kernel (that Ubuntu ran by default for my machine).  I checked this by doing a [ uname - a ] in the terminal.  So here's my questions:

1) Is it just me or is something different with Edgy?
2) Should I be concerned with just running 686-smp?  I'd like all the performance I can get as this is a media center machine.
3) Are there further instructions out there for this type of thing (besides compiling my own kernel)?

Thanks,
One Happy Ubuntu User

---

### Post by jonthenerd on 2007-01-27
Perhaps this info should be added to the initial post by the OP or a moderator?  

> **BunnyEars said:**
> I just installed Ubuntu 6.10 Edgy (default install) on Jan 20 2007. On a Athlon XP 2600.

$uname -a
2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

I  am a new user, but this is what i understand. Correct me if wrong, cos many newbies read these posts.

** For all those who visited this forum thread looking to use processor specific kernels, the current version (6.10 default/generic) has made the k7/686/686-smp kernels OBSOLETE (only for upgrades). I think it applies to all the other processor specific kernels.

**As proof, refer to the "uname -a" output (in Ub 6.10). It says SMP, i686 in the default installation.
Also In Synaptics Pkg Mgr (Ub 6.10), search for "linux-k7". It will describe as OBSOLETE by linux-generic. Same for linux-686/linux-686-smp.

** edit -This might explain why some of the late2006/2007 kernel modifications by users don't show any changes in GRUB. The initial "processor specific kernels" thread was made in year 2005.

Correct me if Wrong. Hope this clarifies for the newbies :).
Jan 2007.

---

### Post by PrinceArithon on 2007-01-28
This didn't do anything different for me than what the 386 was already doing, I'm getting rid of this generic kernel and going back to 386.

---

### Post by lukew on 2007-02-08
The modules have been depreicated and replaced by generic ones; I interpreted this as what this thread was intending to do for you is automatically managed in Edgy?

Does anyone else know different?

Luke

---

### Post by dckirba on 2007-02-22
Hiyya all,

I have a P4 with HT, so I installed the 686-smp kernel ( using Dapper).

Overall I haven't noticed too much of a performance increase. However, I can now enable rendering with threads in Blender and I've noticed a drop in rendering time. Around 25-30% , so all in all, I'm happy!

Cheers,
David K

---

### Post by foureight84 on 2007-02-22
i've been trying to compile a custom kernel for my dell latitude x1 (pentium M). i figured that removing certain modules that i don't need in the default kernel would improve performance, but so far every kernel i compile would not boot. i've compiled custom kernels before for my desktop and everything is great, but i can't do the same on laptops. is there a guide for pentium m specific kernel building?

---

### Post by PartisanEntity on 2007-02-23
Anyone know which kernel is needed for the Turion? Specifically its a Turion 64 but I am running **32** bit Edgy.

---

### Post by Ob1 on 2007-02-25
686 is the default one in edgy, right?

---

### Post by pixelstuff on 2007-03-07
I installed using the guide because I followed a link from the new Ubuntu Edgy guide :( . After seeing no difference I find out how old the guide is... But at least no harm done, I hope.

---

### Post by allen84us on 2007-03-08
i'm using sempron64 2800+.....can i using kernel k7?

---

### Post by zero-Q on 2007-04-05
hi, i want to learn that i have core2duo and i installed edgy with generic so should i install 686-smp or generic is enough??? and generic=386???...

---

### Post by Huzudra on 2007-04-23
hey all, i just updated to v7.04 and its nice, but the kernel listed that im booting from is 386...now when i go and do the steps for the 686 kernel....

> bob@bob-desktop:~$ sudo apt-get install linux-686
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-686 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bob@bob-desktop:~$ uname -r
2.6.20-15-386

i get that, why does it say its already installed?  i dont see a 686 listed in my menu.lst or on the grub bootloader screen.  i'm not entirely new to ubuntu but i'm still very much new to linux in general.  im thinking that im just missing something simple and obvious.

---

### Post by kleeman on 2007-04-24
Try 

sudo apt-get install linux-generic

instead. The 686 package is obsolete.

---

### Post by Huzudra on 2007-04-24
> **kleeman said:**
> Try 

sudo apt-get install linux-generic

instead. The 686 package is obsolete.

ok, when i tried to boot to the generic kernel (which is on the grub bootloader and in the menu.lst) it seemed to just hang at the ubuntu splash screen :confused: is there a new generic kernel i should be using or anything more northwood specific?

---

### Post by pclark99 on 2007-04-28
> **drippy said:**
> msolano, I don't know if you ever fixed this problem, but I am getting the same thing.  I installed 686-smp (on a P4 w/ HT), and the computer completely freezes when loading the second step of "mounting file system".  Is there any way to get a more detailed output to see what is happening at that step?

Hello All:

I just started using Ubuntu and am using 6.06 on a P3. I tried to use the linux-686 but my machine also completely freezes when mounting the file system. The only way to fix this is to go back to linux-386. Has anybody found a fix for this?

If there is some kind of log people need to see to figure out what is going wrong please let me know and give me the command to run. I am pretty new to linux.

Thanks for you help.

---

### Post by MrGreen on 2007-05-02
Is it possible to update kernel to latest version ? or do I have to wait for Ubuntu update?

sorry to go O/T.....

---

### Post by derekguy on 2007-05-09
Many thanks, 

I have an Intel Centrino (Compaq Presario B1800) and installed the linux-686 package, nothing appeared when I rebooted and entered the Grub menu.

I just read the post explaining that the 686 package is obsolete but it appears to have updated the generic kernel and works fine for me.

Not a hugely noticeable improvement but Beryl runs better :guitar: 

Thanks for your howto.

---

### Post by Havoc on 2007-05-11
What the hell happened to the SMP-enabled i686 kernels? I just realised Ubuntu is using only one core (gkrellm only shows one CPU, and "cat /proc/cpuinfo" does the same).

Unless I'm missing something, I don't feel that these "generic" kernels take full advantage of the system... Anyone?

---

### Post by dnzz on 2007-05-11
My computer has centrino 1.86 core solo CPU.
Ubuntu installed generic kernel by default.
I had some problems like slow desktop effects, slow videos, not saving nvidia drivers.
I changed it to i386 now everything works fine.

---

### Post by RichJacot on 2007-05-16
I've just done a fresh install of Feisty on a 

```
CPU0: AMD Opteron(tm) Processor 152 stepping 01

```

The default install installed:

```
Linux borg 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
```

Can someone let me know which kernel I should have/get?  Or am I good to go...

Thanks

---

### Post by medya on 2007-05-17
hey  I intstalled linux686 and linux-image686 packages...and nothing happens and in my menu list I dont see it to choose ...what to do?

---

### Post by Lucifiel on 2007-05-17
The kernels mentioned in the first post are now obselete for Feisty fawn at least. They're now included under the package "linux-generic" which was installed in Feisty fawn. 

Not too sure about the previous versions of Ubuntu. But if you want to check, just search for the package name like "linux-k7" in Synaptic. And then, the results will tell you if the package is now obselete.

---

### Post by glennric on 2007-05-17
> **Lucifiel said:**
> The kernels mentioned in the first post are now obselete for Feisty fawn at least. They're now included under the package "linux-generic" which was installed in Feisty fawn. 

Not too sure about the previous versions of Ubuntu. But if you want to check, just search for the package name like "linux-k7" in Synaptic. And then, the results will tell you if the package is now obselete.

This isn't really true.  The generic kernel does not include the kernels compiled for specific types of processors.  Ubuntu has stopped providing that type of kernel.  They now only provide the generic kernel which is literally a generic kernel with generic processor options compiled in.  To get the 686, k7, or other kernels compiled for a specific processor you need to compile your own kernel.  There are processor specific features that are enabled by doing this, and this can give boosts to performance.

---

### Post by Lucifiel on 2007-05-17
> **glennric said:**
> This isn't really true.  The generic kernel does not include the kernels compiled for specific types of processors.  Ubuntu has stopped providing that type of kernel.  They now only provide the generic kernel which is literally a generic kernel with generic processor options compiled in.  To get the 686, k7, or other kernels compiled for a specific processor you need to compile your own kernel.  There are processor specific features that are enabled by doing this, and this can give boosts to performance.

So... it's inadvisable to use the kernels as mentioned in the first post and recommended to compile your own kernel?

Hmmm... darn. =P My apologies and I stand corrected. :)

---

### Post by glennric on 2007-05-17
> **Lucifiel said:**
> So... it's inadvisable to use the kernels as mentioned in the first post and recommended to compile your own kernel?

Hmmm... darn. =P My apologies and I stand corrected. :)

That is not what I said at all.  I said the kernels on the first post no longer exist.   If you want the performance enhancements of the processor specific kernels you have to compile your own kernel.  It is probably recommended that you use the generic kernel.  Particularly if you don't want to take the time to understand the intricacies of configuring and compiling a custom kernel.

What you said that is not true is that the 686 or K7 kernels are included in the generic kernel.  That is simply not the case.

---

### Post by Havoc on 2007-05-20
That's a bit...regressive, isn't it? Too much workload?

---

### Post by hammedhaaret on 2007-06-05
Hi... im on a laptop with a core 2 duo cpu and ubuntu 7.04.... so.
even though i read some of the posts I wasn't able to tell wether this is relevant for me...
how do i check which kernel im currently using?

and yes im very very new to ubuntu, but it was love at first sight ;)

---

### Post by ucsblaw on 2007-06-17
I posted this on another thread but i need all the help i can get :)

Hi people...im calling on anyone who can try and lend a hand. I'm in a panic myself!

I have a sony vaio s580. 2 gigs of ram and 100gig sata HDD. 

I installed feisty using wubi... i managed to get everything up and running but then i got cocky.

I tried to fix the hibernation/ suspend problem using a guide i found on this forum



In terminal put:



> sudo apt-get install uswsusp  

it gave me some blue box that said that i cant install uswsusp (i think that's what it said) and then i pressed ok. Since Im an idiot...I then decided i should remove what i just tried to install so I typed



> sudo aptitude remove uswsusp  
i then restarted my computer and got this


> 
wubi/boot/initrd.img-2.6.20-16 low latency
[Linux-initrd @ 0x1f9af000, 0x640000 bytes]
boot
[16.297381] RAMDISK: ran out of compressed data
[16.297448] invalid compressed format (err=1)
[16.298258] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block (8,3)
[16.298323]  
then....i cant do anything...my computer is completely dead...I cant even power off...I HAD TO REMOVE THE BATTERY


IM DYING HERE....I spent 2 months getting everything working correctly,,,and customizing my entire desktop and now its gone. 

respectfully yours

---

### Post by ucsblaw on 2007-06-17
anyone?

---

### Post by bcw on 2007-06-18
People are reading this thread to learn about which kernel to run.  I'll bet a lot of them are newbies.

If you want help, post your questions where more (knowledgable) people will see them intead of burying them in a thread that has nothing to do with your issue.

And make backups.  No one here can turn back time.

Best of Fortune to you.

---

### Post by andrew510 on 2007-07-11
i have an AMD Sempron Mobile 2800, (sockect 754) do i use the K7 kernel then ??

---

### Post by protenniser on 2007-09-08
Hi all,

First thanks all who helped us two use our pc with full power :)
I tried to read as much as I can, and if it is solved before in this thread, sorry but I couldn't read all of it.
My computer is a laptop (toshiba tecra m7) which uses nvidia quadro m110 chipset. 
As suggested I have installed the 686 kernel to use both processors, my first question is:
- In the grub menu, I have only seen and chosen the .....-generic kernel (I can't remember the first part), is that correct?
After installation of the new kernel, I could see my two processors but my nvidia installation just died. And now, in the restricted manager I can't see nvidia driver! I can't reactivate my graphics card! So gurus, please help a newbie, if I can activate and use my graphics card too, I will have the perfect laptop I always dreamed :)
All help will be appreciated, thanks in advance.
Regards....

Btw I forgot to mention, I use ubuntu feisty fawn.
Another edit: I also have to use dpkg-reconfigure xserver-xorg because my screen went down after the kernel upgrade. Maybe that is the problem?

---

### Post by protenniser on 2007-09-08
Sorry from all for my stupidness. Problem solved after reinstalling all the restricted modules and drives for the new kernel. (At least I think so). I am not editing the thread in order it may help someone in the future. 
Thanks for the great howto! Rock on :D

---

### Post by Alkaif on 2007-09-10
hmmm how bizzare, i just tried to do this:
```

apt-get install linux-k7

```

and it installed something, but it was only 24.5kb big...surely a kernel is not that small is it? :P

any help is much appreciated :).

---

### Post by K.Mandla on 2007-09-11
linux-k7 is now the same as linux-generic.

[http://packages.ubuntu.com/feisty/base/linux-k7](http://packages.ubuntu.com/feisty/base/linux-k7)

So basically, you installed a little file that said you already have it installed. ;)

---

### Post by Yes on 2007-09-12
How do you know if it worked?  I ran

```
sudo apt-get install linux-686-smp
```

because I have a processor with hyperthreading, and I didn't get any errors.  But my GRUB menu.lst file didn't change at all.  Does that mean that it didn't install correctly?

Great guide, by the way.

---

### Post by Rui Pais on 2007-09-12
> **Yes said:**
> How do you know if it worked?  I ran

```
sudo apt-get install linux-686-smp
```

because I have a processor with hyperthreading, and I didn't get any errors.  But my GRUB menu.lst file didn't change at all.  Does that mean that it didn't install correctly?

Great guide, by the way.

This thread is obsolete for feisty. The default kernel image is already for 686 and with smp enabled.
[Check it here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-686-smp&searchon=names&subword=1&version=feisty&release=all").

---

### Post by Elemental_TJ on 2007-09-12
Thanks for this topic! I got the K7. I don't see a real improvement, but
in the long run, I think it'll help. Tanx. ;)

---

### Post by abhilash82 on 2007-09-12
> **poofyhairguy said:**
> **[COLOR="Red"]STAFF NOTE:[/COLOR]**

Since the naming convention -- and the generic kernel -- changed after version 6.06, Dapper Drake, selecting a different kernel may or may not have any effect on your system. Please [research the kernel options]("http://packages.ubuntu.com/") that match your release, remembering that the default kernel -- [linux-generic]("http://packages.ubuntu.com/feisty/base/linux-generic") in Feisty -- in some versions of Ubuntu is probably already appropriate for your CPU.

Thanks.
K.Mandla

-----------

[B]Disclaimer

This section is about messing with the kernel and that can be tricky business. Has never messed up for me, but it is a little nerdy. Look here if you want to learn and maybe get a speed boast (or if you have a dual core/dual processor/hyperthreading machine because you WILL get a performance boost). Use at you own risk, I am not a kernel developer or anything.

Be sure not to install the linux-image package instead or things will probably break! If you have done that just install the correct package and things will fix themselves.

***********************
[/B]
**Introduction**

I have noticed some recent confusion in the forum when it comes to kernels, so I want to explain some things I have discovered. I hope it helps.

So you just installed Ubuntu but you don't think its going as fast as you think it should? Maybe you have just been advised to install a new kernel so you want to know more.

In Synaptic, if you search for “linux-image” you will find many kernels. Each its follows by some  numbers and letters in some order. I will now explain those differences and what each means.

**Notes:**

- This guide does not apply to the PPC or 64 bit version of Ubuntu.

- If you have a heavily modified setup this might not work. For example if you have installed some drivers "by hand" and not from the repositories.

- Its hard to measure the speed increase, so if in doubt leave it out. Don't follow the guide if you are uncomfortable

- You can always boot back into you old kernel if things mess up. When the OS Menu appears at boot (called the Grub menu) just hit down and then hit enter on the first line with a "386" in it. You might have to hit the ESC key when you boot to pull up this menu. 

- My steps will rewite your grub, so if you have a custom grub save it somewhere.

**The Many Kinds of Kernels**

386 – the default kernel in Ubuntu is the 386 kernel (but I hear its really a 486 kernel). What that means is that its the most compatible kernel because it supports the oldest tech. Here is wiki page to learn more:

[http://en.wikipedia.org/wiki/Intel_80386](http://en.wikipedia.org/wiki/Intel_80386)

686 – The kernel that is recommended for use with any Intel Processors in a computer that are more recent then a Pentium Pro. So even old Pentium 2s and 3s can get in on the act. Installing this kernel with may improve performance.

[http://en.wikipedia.org/wiki/Pentium_Pro](http://en.wikipedia.org/wiki/Pentium_Pro)

k7 – This kernel is recommended for a computer with a Athlon or newer AMD CPU.  New 64 bit AMD cpus can use it as well if you have the 32 bit version of Ubuntu installed. Installing this kernel with may improve performance.

[http://en.wikipedia.org/wiki/Athlon](http://en.wikipedia.org/wiki/Athlon)
[B]
smp – This kernel is NEEDED to use both CPUs in a multi-CPU setting. The kernel is also required to “enable” hyperthreading in modern Pentium 4 CPUs. Also needed for dual core processors (the letters stand for Symmetric Multiprocessing). Very important to install this, as it WILL improve performance. Sorry to bold it but I think this one is the most important.[/B]

[http://en.wikipedia.org/wiki/Symmetric_multiprocessing](http://en.wikipedia.org/wiki/Symmetric_multiprocessing)

**How to Install New Kernels**

You need to install the file below as indicated:

For a modern Pentium 2+ (686) kernel:



For a modern Pentium 2+  kernel for dual processors, dual cores, or hyperthreading:



For a Athlon (k7) or for a Athlon 64 (with 32 bit Ubuntu) kernel.



For a Athlon (k7) kernel for dual processors or dual cores:



**Conclusion**

I wish you the best of luck and please post comments if you notice any improvements or any problems.

**Note About Nvidia**

The Nvidia driver is not an open source driver. It is "restricted" because of that fact.

Therefore the actual official Nvidia driver's kernel module (the part that interacts with the kernel to make it work) is in the restricted package. If you follow my guide those packages should be installed automatically (they are for me) but they don't for legacy cards. If you have a Nvidia card older than a Geforce 3 (except maybe the Geforce 2 MX) you have to install the legacy drivers. 

Every time you switch to another kernel you have to reinstall the nvidia drivers for that specific kernel if you have used the nvidia installer. 

OR

If you use the drivers from the repos then you will need the restricted modules for your kernel (only the ones for the i386 kernel are installed by default). If apt-get did not install these automatically with my guide you MUST do it! In other words, boot as usual, and if you are stuck to the command line type:




OR (if you use the nvidia legacy drivers)

I would like to know if this HOWTO is still active and applies to all the current kernels. Please clarify if I require any update of the kernel to suit my system spec.?
```

uname -r

```

results in the output:

```

2.6.20-16-generic

```

and 


```

uname -a

```

results in the output:

```

Linux abhilash-desktop 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

```

This means I am having the appropriate kernel for my system?

My System Spec.: Intel 865GBF, 2.4 GHz with HT, 256 MB RAM.

---

### Post by Rupertronco on 2007-09-13
Fiesty already has support for multi core processing (hyperthreading is a virtual multi processor). You don't need a new kernel. The default one will suit you just fine.

---

### Post by Masteroc on 2007-10-24
Is there a 686 kernel out for Gutsy yet? it says when i try and do a "sudo apt-get install linux-686" that :

"Package linux-686 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-686 has no installation candidate"

So does that mean they just havent gotten around to compiling one for it yet?

Thanks

---

### Post by K.Mandla on 2007-10-24
The default kernel is 686 with SMP enabled. Check which kernel you're running with 

```
uname -a
```
Check the disclaimer at the top of the original post. The CPU-specific kernels are much different in Gutsy, and unless you are running a 386 or another extremely esoteric computer, you probably don't need one.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-image&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-image&searchon=names&subword=1&version=gutsy&release=all)

---

### Post by joker67 on 2007-10-25
Hmm...

it would be nice if someone could tell me if im wrong.

i did the uname -a in the terminal and i got...

2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

and thats the kernel för intel cpu with dual core, right?

How do i change the kernel to be right for my AMD Athlon64 cpu with single core?

Thanks for answers.

/Peter H

---

### Post by Bram-NL on 2007-12-24
Hey Peter,

If you look at the [link]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-image&searchon=names&subword=1&version=gutsy&release=all") in the post by K.Mandla, you will see that the generic is for amd_64 *and* i386. Of course, if you really want to optimize it, you can recompile the kernel for your system. You might also consider using a 64-bit kernel.

Here is my uname -a for a AMD Athlon64 4200+
Linux bram-desktop 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64 GNU/Linux

---

### Post by dbbolton on 2008-07-20
What is the right kernel for an AMD Athlon 64 X2 4000+ on Hardy? I was thinking k8-smp, but I can't find anything like that in the repos.

---

### Post by jocko on 2008-07-31
> **dbbolton said:**
> What is the right kernel for an AMD Athlon 64 X2 4000+ on Hardy? I was thinking k8-smp, but I can't find anything like that in the repos.

-generic is the correct kernel for ALL processors except VERY old (think antique) processors (which only works with the -386 kernel).
This thread was outdated in june 2006 when dapper was released and all optimized kernels (-k6, -k7, -686, -k8) were replaced by one (-generic) kernel that activates the optimizations the processor support.

---

### Post by dbbolton on 2008-08-03
> **jocko said:**
> -generic is the correct kernel for ALL processors except VERY old (think antique) processors (which only works with the -386 kernel).
This thread was outdated in june 2006 when dapper was released and all optimized kernels (-k6, -k7, -686, -k8) were replaced by one (-generic) kernel that activates the optimizations the processor support.
That's what I heard from the IRC channel. I thought about editing my post, but I didn't think anyone would actually respond :D

Thanks anyhow.

---

### Post by Pro-reason on 2008-09-21
> **dbbolton said:**
> That's what I heard from the IRC channel. I thought about editing my post, but I didn't think anyone would actually respond :D

Thanks anyhow.

You should mark in big letters at the top of the post that it is out of date.

---

### Post by thegizmoguy on 2008-12-08
Well even if you were to run the commands given it just says "Not Found" (basically).

At least this is +1 Ubuntu not needing "extra work" to be optimized.

---

### Post by TL225 on 2010-07-21
hi,my laptop processor is intel centrino dual  core.when i try the sudo apt-get install linux-686-smp it say 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-686-smp

can u help me out?

---

### Post by krimzonstarr on 2010-07-22
> **TL225 said:**
> hi,my laptop processor is intel centrino dual  core.when i try the sudo apt-get install linux-686-smp it say 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-686-smp

can u help me out?

Just a heads up... the last reply to this thread before you was Dec 2008, and I believe the thread itself is dated from 2005. Doubt much of it is still relevant.

---


---
title: "dual boot -  wubi  method or partition method - thoughts?"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by MeTylerDurden on 2008-07-21
[SIZE="2"][COLOR="DimGray"]To do the wubi method do you need to download just the installer or a whole other copy of hardy heron? The Wubi sound like an interesting option, whats your thoughts[/COLOR][/SIZE]

---

### Post by wolfen69 on 2008-07-21
i've never done the wubi method, but from what i've read, a real dual boot may give you a better experience. wubi seems good for someone wanting just to try out ubuntu with a minimum of fuss.

---

### Post by MeTylerDurden on 2008-07-21
[SIZE="2"]I was just looking and noticed that you can do the wubi method without downloading a cd ,  so I presume you just go to the wubi installer website and download as you would any other file-directly to pc ?[/SIZE]

---

### Post by mick222 on 2008-07-21
I installed the wubi on my daughters computer it works well great if you dont want a full install. I used my ubuntu install live cd but think if you download the iso you can install without burning a cd.

---

### Post by YaroMan86 on 2008-07-21
I prefer making Linx a dominant OS on my machines. Wubi doesn't do that for me. I have Linux dominating most of my computer. Windows is contained on a mere 30 GiB hard disk versus 120 GiB Ubuntu is installed on, with 10 GiB unallocated for my LFS project.

You'd get the best performance and capability out of a free-standing Ubuntu, rather than an Ubuntu hindered by a crummy Windows install.

---

### Post by Potatoj316 on 2008-07-21
I would sugest a dual boot instead of Wubi.  The ubuntu CD makes a dual boot instal by default, it is very easy to do.

---

### Post by mick222 on 2008-07-21
If you have never installed linux before the wubi is great as it's much faster than a live install and gives you a real feel for ubuntu. I hate live cd's ,too slow and you cant save anything. If you intend to keep ubuntu dual boot is best.

---

### Post by billgoldberg on 2008-07-21
Do a real dual boot. 

Wubi is only for testing purposes in my eyes.

--

I haven't tried wubi but from what I've read, you just install wubi like you would another app in windows. 

Then wubi will download and install ubuntu for you.

---

### Post by MeTylerDurden on 2008-07-21
After much info (thanks to all):popcorn: I have decided on  installing Ubuntu on own partition.  Pass on the Wubi thing..

---

### Post by billgoldberg on 2008-07-21
To OP: you're abusing the thanking system a bit.

---

### Post by steveneddy on 2008-07-21
> **wolfen69 said:**
> i've never done the wubi method, but from what i've read, **[COLOR="Blue"]a real dual boot may give you a better experience[/COLOR]**. **[COLOR="Red"]wubi seems good for someone wanting just to try out ubuntu with a minimum of fuss[/COLOR]**.

Wubi is an installed Live CD in my opinion.

Use it to check it out, but not for serious computing.

If you dual boot, actually instlling Ubuntu on a seperate partition, you can actually use the OS. Try it out. Kick the tires.

You wouldn't go to buy a new car and only test drive it through a simulation on the computer, would you?

Yeah - me neither.

---

### Post by djamu on 2008-07-22
> **steveneddy said:**
> Wubi is an installed Live CD in my opinion.

Use it to check it out, but not for serious computing.

If you dual boot, actually instlling Ubuntu on a seperate partition, you can actually use the OS. Try it out. Kick the tires.

You wouldn't go to buy a new car and only test drive it through a simulation on the computer, would you?

Yeah - me neither.


I accidentally stumbled upon this thread, can't refrain myself..
What a bunch of #!$é from people commenting on Wubi without having a grasp of how it really works.

So here whe go... It works the same way as Vmware treats partitions without having to emulate any hardware it only emulates a partition. Wubi renders a partition into a ( large ) file that resides on a host partition.
In other words **it doesn't run inside windows**.

In fact I use wubi on Linux to test drive/install other OS's without having to repartition any disks installing dozens of different linux flavors.
I've got no idea how people come to think of it as a kind of emulated / simulated virtual machine as some people suggested.
**It doesn't run inside a host, it's not emulated, there's absolutely no performance degradation.** 

Ooh wait there might be... if you have a stuffed NTFS host HD which is fragmented like hell a very slight HD performance degradation might happen.

my rig
6.5TB 15disk raid6 NFS with daily evms snapshots / PXE'd diskless wokstations / 1GBs networked
gives me much higher disk I/O then any local HD


:lolflag:

---

### Post by fidamehran on 2008-07-22
> **djamu said:**
> I accidentally stumbled upon this thread, can't refrain myself..
What a bunch of #!$é from people commenting on Wubi without having a grasp of how it really works.

So here whe go... It works the same way as Vmware treats partitions without having to emulate any hardware it only emulates a partition. Wubi renders a partition into a ( large ) file that resides on a host partition.
In other words **it doesn't run inside windows**.

In fact I use wubi on Linux to test drive/install other OS's without having to repartition any disks installing dozens of different linux flavors.
I've got no idea how people come to think of it as a kind of emulated / simulated virtual machine as some people suggested.
**It doesn't run inside a host, it's not emulated, there's absolutely no performance degradation.** 

Ooh wait there might be... if you have a stuffed NTFS host HD which is fragmented like hell a very slight HD performance degradation might happen.

my rig
6.5TB 15disk raid6 NFS with daily evms snapshots / PXE'd diskless wokstations / 1GBs networked
gives me much higher disk I/O then any local HD


:lolflag:

I totally agree, there is no need to give the newcomers the scare.

Why is everybody advising the newcomers to install with partitioning? I remember when I tried installing Fiesty (Ubuntu 7.04) for the first time, I was quite tense about the partitioning. What's the harm in installing Ubuntu through Wubi and trying it out? I think, when a user will be confident enough, he can ditch the whole junkload of Windows and do a fresh install of Ubuntu by CD booting.
I am still very fresh to Ubuntu and being delighted to see the Wubi option for the first time in 8.04, I used it to install it. My Ubuntu 8.04 is running like magic.
Don't discourage it. This could be a whole new dimension of doing things.

---

### Post by fidamehran on 2008-07-22
And one more thing I agree upon. The first thread poster MeTylerDurden is misusing the Thanks option. Number of Thanks Received is a way of knowing how much the guy (guy whom you thanked) knows. So don't thank anybody for anything. Say thank you. That's ok. :-) 

:-)
Just kidding.

---

### Post by MeTylerDurden on 2008-07-23
Kick the tires..  I downloaded the cd from Switzerland and was ready to install and make a partition.  Then I just decided to kick the tires and try Wubi, and I was amazed .   Very simple to do, and I am not sure how it takes hours to download a cd and minutes to do the wubi install..  ( ok i didn't have a stopwatch)      Anyway the Switzerland mirror download around 50kb which was good, the cd was fun to make anyway.  Wubi was worth the roll.

---

### Post by kansasnoob on 2008-07-23
Well, I've tried Wubi, it's OK. It works. But I prefer a dual boot. then again I prefer a dual-boot to creating a "virtual" Win machine via VMWare.

But, at the end of the day it's all a matter of preference.

Easiest dual boot guides I've found: (they do work)

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

Best dual boot guide: (more advanced)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

A must read:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by Paqman on 2008-07-23
> **steveneddy said:**
> 
Use it to check it out, but not for serious computing.


What a load of nonsense! :)

A Wubi install is just as powerful as one installed to it's own partition. Apparently there is a very small disk access time penalty, but it's not something you'd ever notice, especially on a desktop.

I suspect a lot of the people who recommend against using Wubi have never actually done a Wubi install. I'd encourage them to do one as soon as possible so that they can evaluate it for themselves, instead of repeating the same inaccurate assumptions about it over and over in Absolute Beginners.

---

### Post by djamu on 2008-07-23
> **kansasnoob said:**
> Well, I've tried Wubi, it's OK. It works. But I prefer a dual boot. then again I prefer a dual-boot to creating a "virtual" Win machine via VMWare.



As a matter of fact **Wubi creates a dual boot for you** ...
-10 for pretending to claim you tried/understand wubi

Vmware doesn't require dual boots as it is a hosted system ( runs inside ) like qemu, uml chroots etc...
-5 for using the Vmware word in conjunction with dual boot


> 
But, at the end of the day it's all a matter of preference.


Yeah sure this is the absolute beginners talk forum after all.
Maybe I should lecture a bit on everything that can go wrong with grub.

The bios bootloader stack vs grub 1 / 1.5 vs initramfs
in case you got multiple ( like in 2 or more HD's / controllers )

or

Why not advice noobs to learn bash for starters, it will surely drive some wannabee nix fanboys back to winblows..
might cleanup the forum a bit 
( actually ubuntu defaults to dash ) 

Guess that at least some people will understand my point here..

> 
Easiest dual boot guides I've found: (they do work)
......



scrap that > **easiest dual boot WUBI > thumbs up**


> 
A must read:
....
Other peoples posts, because I obviously don't know s**t... 



you got it coming dude

:mad:

---

### Post by MeTylerDurden on 2008-07-23
speaking of Absolute beginners talk.. I thought dual boot originally meant to boot and use Ubuntu and Windows at the same time, actually you get a choice of which to use...  One or the other.  You learn something new everyday. 



**[SIZE="2"][COLOR="DarkOrange"]The liberator who destroyed my property has realigned my perception[/COLOR][/SIZE]**

---

### Post by fidamehran on 2008-07-23
Dear djamu, you declared a war out there. I also liked Wubi. And the one silent guy was MeTylerDurden. He didn't type, he just clicked, clicked the star medal on the right side... "Thank you". Well Thank You, MeTylerDurden, for thanking all. I must say people in Michigan are very polite.
Dear djamu, maybe this is not the place to ask, but I want to ask anyway, will my Ubuntu installation go ka-put if my Windows crashes? Since it shows as a program installed in the Add/Remove of Control Panel?

---

### Post by djamu on 2008-07-23
> **fidamehran said:**
> Dear djamu, you declared a war out 
there. 


Well yeah.  in my humble opinion forums are here to help ( well most off them anyway ), not to fog a topic without justification, so I couldn't care less. Conclusions based on rumors, isn't really helpful. Bare facts might help state your point, but that requires some research....

> 
...will my Ubuntu installation go ka-put if my Windows crashes? Since it shows as a program installed in the Add/Remove of Control Panel?

No as long as nothing touches the [[COLOR="Blue"]bootsector.[/COLOR]]("http://en.wikipedia.org/wiki/Bootsector")
The installer is just there to facilitate / alter the boot procedure, creating a system that resides in a file on the original partition, nothing else. The installer is just there because that's the way windoz works..
Uninstalling will cleanup any linux/wubi related files > read delete the linux OS system file.
The only other way to destroy your dual-boot is to clear/rewrite your [[COLOR="Blue"]bootsector.[/COLOR]]("http://en.wikipedia.org/wiki/Bootsector")



**Clearing windoz & keeping your linux:** 

Prior to deleting the windows partition & uninstalling wubi you have to copy the wubi file / contents of the wubi file.


**2 routes.**

1. The wubi way in which you keep that ( those ) large file(s) as system partition(s) and move it to another empty partition

2. The normal way in which case you just copy the contents of the wubi system file to an empty partition.
( kind of abstract maybe, but just compare the wubi system file to a large ZIP/RAR file, 1 file that contains lots of files.


I for instance find it very easy manipulating these large files instead of it's contents ( I'm not even running windoz ) because it lets me easily install systems within systems.
( forget what i said, this is not a topic for this list )


Both ways require you to alter the [[COLOR="Blue"]bootloader/grub[/COLOR]]("http://en.wikipedia.org/wiki/GNU_GRUB") to point it to the new location of the file / partition / disk .
So it's perfectly possible to keep your wubi dualboot without wubi installed.


If anyone is interested I'll write a quick howto for both methods.. maybe even a script


 ;)

---

### Post by djamu on 2008-07-23
> **MeTylerDurden said:**
> speaking of Absolute beginners talk.. I thought dual boot originally meant to boot and use Ubuntu and Windows at the same time, actually you get a choice of which to use...  

Lol.

This is what qemu, uml or Vmware does, Vmware is by far the easiest to install ( free ) 
both for windows & linux as host > runs any x86 compatible client OS. ( it's not really an emulator / simulator ) 


grab a free copy [[COLOR="Blue"]here[/COLOR]]("http://www.vmware.com/products/server/") for the server version.
I use it all the time for development + mount your wubi files in there :p ( requires a trick ), just keep in mind that it doesn't offer ( yet ) video acceleration. 


there's also a workstation version but it's not free..

:KS

---

### Post by Jon Monreal on 2008-07-23
I tried Wubi when I got this new (inexpensive, general home-use) Compaq F767 laptop because it (of course) came with Windows. I was pretty impressed. However, as I later discovered, something wasn't working right with the power management, and the computer shut off. Unfortunately, this damaged Wubi's somewhat more delicate file system.

From the Wubi Installer website:
> Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.

This was, of course, no problem for me, as I was planning on doing a regular install of Ubuntu anyways.

So Wubi does have its limitations and disadvantages. However, I doubt that most users would have a problem with Wubi, and I encourage new users who use Windows to try it out. You'll be glad you did. And if you want to do a full-fledged install, djamu's method is an easy way to do so.

---

### Post by Paqman on 2008-07-23
> **fidamehran said:**
> will my Ubuntu installation go ka-put if my Windows crashes? Since it shows as a program installed in the Add/Remove of Control Panel?

It possibly might if you experienced corruption of the file system that the virtual partition resides in. Any corruption of Windows system files however would have no effect on Ubuntu. Wubi installs to the same partition as Windows, but isn't dependent on Windows to run.

In short: theoretically possible, but only under certain rare types of failure. 

It should be noted that damage to the file system on which it is resident will cripple any OS, including Linux installed on its own partition. It's not a problem specific to Wubi.

---

### Post by Paqman on 2008-07-23
> **djamu said:**
> 
If anyone is interested I'll write a quick howto for both methods.. maybe even a script

Wouldn't you just use [LVPM](http://lubi.sourceforge.net/lvpm.html)?

---

### Post by djamu on 2008-07-23
> **Paqman said:**
> Wouldn't you just use [LVPM](http://lubi.sourceforge.net/lvpm.html)?
ow that's way cool..

---

### Post by Paqman on 2008-07-24
> **djamu said:**
> ow that's way cool..

Indeed it is. Besides migrating a Wubi install to it's own partitions, it can also resize virtual disks. Picking the wrong size for the virtual disk at install time is a pretty common mistake, so it's a very handy package to know about.

---

### Post by Jammy4041 on 2008-07-24
In would plump for the dual boot option. 

if you want to try Linux though, the WUBI installer is fine.

---


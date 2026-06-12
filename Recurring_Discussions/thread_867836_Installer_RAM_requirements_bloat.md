---
title: "Installer RAM requirements bloat"
date: 2008-07-23
forum: Recurring Discussions
---

### Post by Trinoc on 2008-07-23
As a Windows sufferer for many years, I have looked forward to a version of Linux reaching the level of functionality at which I can seriously consider it as a replacement. Ubuntu 8.04 looked to be exactly what I'd been looking for, and I planned to install it on some older PCs to run in parallel with Windows on other PCs until I am happy it can do everything I need.

Linux has always been trumpeted as being able to run on much lower spec machines - even old 386s in some cases - without the code and processor time bloat which we have come to expect from Microsoft etc.

I wasn't planning on trying to install Ubuntu on anything less than a Pentium, but I did think I would be able to try it on a couple of old Pentium 3s with only 256MB of RAM, but first on an even older Gateway 2000 which can only support 64MB of RAM.

No such luck ... the graphical installer requires 384MB of ***physical RAM***, and even the text-based installer requires 256MB. Not just virtual RAM including a swap partition, but actual, physical RAM! Why, for heaven's sake? You can control a trip to the Moon and back using less memory than this!

Back in the *Good Old Days (TM)* something like this would probably have been written to run in less than 256 *kilobytes*. I'm not expecting anything quite like that, but honestly ... over 256 *megabytes* of RAM-resident code and data just for an installer? I really don't believe that it couldn't be made *a lot* smaller than that.

I now need to look for a different Linux distro to try out on my old machines, which is a great pity because Ubuntu really looks like the way forward in almost all other respects. Can something please be done about this unnecessary bloat? It is a serious obstacle to what I see as one of Linux's great advantages, namely the ability to run on modest-spec PCs which don't have to be exponentially upgraded with every new system release - the very problem that I think/hope might stop Microsoft and friends in their tracks some time soon.

---

### Post by paul101 on 2008-07-23
why not use the xubuntu alternate install cd ;)



i bet it will work :razz:

---

### Post by unoodles on 2008-07-23
If you are trying to install on a machine with that little RAM, you should seriously consider Xubuntu [http://www.xubuntu.org/](http://www.xubuntu.org/) it has extremely low hardware requirements and is much more lightweight then the regular Ubuntu.

---

### Post by Potatoj316 on 2008-07-23
DSL and Puppy are also good for low RAM and low diskspace machines.

---

### Post by LaRoza on 2008-07-23
> **Trinoc said:**
> 
No such luck ... the graphical installer requires 384MB of ***physical RAM***, and even the text-based installer requires 256MB. Not just virtual RAM including a swap partition, but actual, physical RAM! Why, for heaven's sake? You can control a trip to the Moon and back using less memory than this!
Why? **Because it runs the entire OS from the disk**. Use the alternative disk for lower requirements.

Windows has no such thing. The disk for Ubuntu is a live disk, so it runs Ubuntu in full (you can install software and such, but you can't really do anything that requires a reboot, because it runs in RAM). You can get the alternative disk to install it.

---

### Post by insane_alien on 2008-07-23
ubuntu isn't really designed for being light weight. variants like Xubuntu and fluxbuntu however are much more light weight. and you can always go for puppylinux or damn small linux if you want ultra light weightness.

if you are willing to sacrifice initial software then you can get some distros that are fully contained on a floppy disk and don't require more than a megabyte of RAM. linux covers the spectrum of lightweight to heavyweight, windows is just super heavyweight.

---

### Post by dje on 2008-07-23
[crunchbang linux]("http://crunchbang.org/projects/linux/") and [fluxbuntu]("http://fluxbuntu.org/") (both based on ubuntu) would both be much better choices for those machines (especially the Gateway). They use the openbox and fluxbox window managers respectively, personally i would go for crunchbang on all the machines as i have xubuntu on a machine with 256mb ram and although it is much more useable than windows xp it can be sluggish at times

hope that helps,
dje

---

### Post by snowpine on 2008-07-23
> **Trinoc said:**
> As a Windows sufferer for many years, I have looked forward to a version of Linux reaching the level of functionality at which I can seriously consider it as a replacement. Ubuntu 8.04 looked to be exactly what I'd been looking for, and I planned to install it on some older PCs to run in parallel with Windows on other PCs until I am happy it can do everything I need.

Linux has always been trumpeted as being able to run on much lower spec machines - even old 386s in some cases - without the code and processor time bloat which we have come to expect from Microsoft etc.

I wasn't planning on trying to install Ubuntu on anything less than a Pentium, but I did think I would be able to try it on a couple of old Pentium 3s with only 256MB of RAM, but first on an even older Gateway 2000 which can only support 64MB of RAM.

No such luck ... the graphical installer requires 384MB of ***physical RAM***, and even the text-based installer requires 256MB. Not just virtual RAM including a swap partition, but actual, physical RAM! Why, for heaven's sake? You can control a trip to the Moon and back using less memory than this!

Back in the *Good Old Days (TM)* something like this would probably have been written to run in less than 256 *kilobytes*. I'm not expecting anything quite like that, but honestly ... over 256 *megabytes* of RAM-resident code and data just for an installer? I really don't believe that it couldn't be made *a lot* smaller than that.

I now need to look for a different Linux distro to try out on my old machines, which is a great pity because Ubuntu really looks like the way forward in almost all other respects. Can something please be done about this unnecessary bloat? It is a serious obstacle to what I see as one of Linux's great advantages, namely the ability to run on modest-spec PCs which don't have to be exponentially upgraded with every new system release - the very problem that I think/hope might stop Microsoft and friends in their tracks some time soon.

Hi Trinoc, I somewhat share your frustration, but I do want to make a few points. 

1. Ubuntu and Linux are not synonymous. Linux comes in hundreds, if not thousands of flavors, and not all of them are going to be right for everyone. There are flavors designed to run on modern supercomputers, and flavors designed to run on your ancient computer.
2. Ubuntu is the flagship 'buntu product, designed to be attractive and have a user-friendly interface. This takes system resources.
3. Ubuntu runs on just about every new computer out there today. Try walking into Best Buy and buying a computer with less than 512mb of ram. 
4. Xubuntu is available for older computers. It runs on 128mb of RAM, and rumor has it that the upcoming 8.10 release will be even lighter.
5. Fluxbuntu, while not official, will run on 64mb of ram.

Bottom line is that every project needs goals, should supporting ancient hardware be the new goal of the ubuntu project? Should they spend hundreds of thousands of dollars so that you don't have to spend a few dollars on ram? :)

I do agree with you philosophically. I think that old hardware should be reused instead of discarded, and that Linux is the best tool to make this happen. I think that Xubuntu 8.10 II is going to be a step in this direction. But I also think that there will always be a place for distros like DSL and Puppy, and I do not expect Ubuntu to ever directly compete with them.

---

### Post by overdrank on 2008-07-23
> **Trinoc said:**
> 
I wasn't planning on trying to install Ubuntu on anything less than a Pentium, but I did think I would be able to try it on a couple of old Pentium 3s with only 256MB of RAM, but first on an even older Gateway 2000 which can only support 64MB of RAM.

No such luck ... the graphical installer requires 384MB of ***physical RAM***, and even the text-based installer requires 256MB. Not just virtual RAM including a swap partition, but actual, physical RAM! Why, for heaven's sake? You can control a trip to the Moon and back using less memory than this!



You could look at installing without a cd or the minimal Ubuntu install
[https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD](https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD)

---

### Post by snowpine on 2008-07-23
ps as to why the Alternate CD installer requires 256mb, well, Ubuntu won't run well with less than 256mb, so why should they make an installer than only needs 64mb if the OS isn't going to run well once installed? :)

---

### Post by Trinoc on 2008-07-23
Lots of excellent advice - and damned quick ... thank you everyone!

I'll try out xubuntu, crunchbang, fluxbuntu etc., when I get a chance. I still think, though, that for standard Ubuntu to reach the critical mass needed to make it a serious contender against Windows, it needs improvement in this area. Surely it is not necessary to copy the entire OS into physical RAM. It is there on the CD, albeit with rather slow access, and it could make use of either an existing Linux swap partition found on a disk, or could run a lightweight partitioner before the main installation process begins if one needs to be created.

I can't help thinking that the installer must have been written with the philosophy that there is going to be plenty of RAM, so just blast everything into memory and work from there. Doubtless this makes programming a bit easier, but it isn't very efficient practice to do it this way. Even if the program is written to run in 256MB or more of *virtual* RAM, it should be possible for the kernel to page it out to a swap partition. OK, so it would make it run more slowly, but at least it would run at all.

---

### Post by LaRoza on 2008-07-23
> **snowpine said:**
> ps as to why the Alternate CD installer requires 256mb, well, Ubuntu won't run well with less than 256mb, so why should they make an installer than only needs 64mb if the OS isn't going to run well once installed? :)

The alt disk only needs 64 MB of RAM.

---

### Post by LaRoza on 2008-07-23
> **Trinoc said:**
> 
I'll try out xubuntu, crunchbang, fluxbuntu etc., when I get a chance. I still think, though, that for standard Ubuntu to reach the critical mass needed to make it a serious contender against Windows, it needs improvement in this area. Surely it is not necessary to copy the entire OS into physical RAM. It is there on the CD, albeit with rather slow access, and it could make use of either an existing Linux swap partition found on a disk, or could run a lightweight partitioner before the main installation process begins if one needs to be created.
Considering Ubuntu runs on computers with 256 MB of RAM and Vista requires 1 GB, I think Ubuntu is ahead here ;) The alt disk only needs 64 MB. 

> 
I can't help thinking that the installer must have been written with the philosophy that there is going to be plenty of RAM, so just blast everything into memory and work from there. Doubtless this makes programming a bit easier, but it isn't very efficient practice to do it this way. Even if the program is written to run in 256MB or more of *virtual* RAM, it should be possible for the kernel to page it out to a swap partition. OK, so it would make it run more slowly, but at least it would run at all.
Ubuntu is a desktop OS aimed at modern computers. It has to have a line somewhere. Ubuntu is pretty bloated. For a lighter (but still modern) distro, try Debian.

---

### Post by snowpine on 2008-07-23
> **Trinoc said:**
> Lots of excellent advice - and damned quick ... thank you everyone!

I'll try out xubuntu, crunchbang, fluxbuntu etc., when I get a chance. I still think, though, that for standard Ubuntu to reach the critical mass needed to make it a serious contender against Windows, it needs improvement in this area. Surely it is not necessary to copy the entire OS into physical RAM. It is there on the CD, albeit with rather slow access, and it could make use of either an existing Linux swap partition found on a disk, or could run a lightweight partitioner before the main installation process begins if one needs to be created.

I can't help thinking that the installer must have been written with the philosophy that there is going to be plenty of RAM, so just blast everything into memory and work from there. Doubtless this makes programming a bit easier, but it isn't very efficient practice to do it this way. Even if the program is written to run in 256MB or more of *virtual* RAM, it should be possible for the kernel to page it out to a swap partition. OK, so it would make it run more slowly, but at least it would run at all.

The whole point of a Live CD is that you can try out a fully-functional Ubuntu without touching anything on your hard disk. If it created a swap partition or otherwise messed with your hard drive in any way, that would be a HUGE turn-off for most Live CD users. (I do think it will use an existing Linux swap, though.)

As pointed out, there are other ways to install without using a Live CD, so I don't really see the problem. :)

---

### Post by Trinoc on 2008-07-23
> **LaRoza said:**
> Considering Ubuntu runs on computers with 256 MB of RAM and Vista requires 1 GB, I think Ubuntu is ahead here ;) The alt disk only needs 64 MB.
That's good to know - I'm sure the docs I read say it needs 256MB.

---

### Post by snowpine on 2008-07-23
> **LaRoza said:**
> The alt disk only needs 64 MB of RAM.

I certainly believe you if that is your experience; I don't have a 64mb computer so I was getting my numbers from this page: [http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

"The minimum memory requirement for Ubuntu 8.04 is 384MB of memory for desktop CDs, and 256MB for other installation methods."

---

### Post by LaRoza on 2008-07-23
> **Trinoc said:**
> That's good to know - I'm sure the docs I read say it needs 256MB.

See "Bare Minimum": [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by LowSky on 2008-07-23
The alt install cd still requires 256 MB as the OP clearly states aswell. Do I feel that OSes are becoming too bloated, well yes but its due to all the software they come standard with that most people never use or know is included. For instance Ubuntu comes preinstall with bluetooth support, games, openoffice, and 4 media applications. Does this make it easier for new users to use, of course but it also puts a strain on older systems.

What should be mentioned is that this website isn't maintained by Canonical but by users.
If you have a suggestion request it here [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

Also Ubuntu and its many flavors do claim to run on older machines and they do. *buntu can support machines from as long ago as 10 years. You get an new OS on an old machine which means security and newer apps. Try doing that with Windows 98, Me, or 2000. you can even create your own version of the distro with all the added or deleted applications.

Now I see your consern for a much simpler installer that requires less memory but look at it from a different point of view. 1.Ubuntu is simpler to install than Windows, no worry about installing drivers. 2. LiveCDs allow users to use a computer that may have hard drive  problems. 3. Most computer have a actual life span of 7 years. After that point the hardware failure rate increses 10 fold, things like capacitors, , and processors all give out. Don't forget CDROMs, floppy drives, fans and power supplies are more error prone than the none moving parts.

Lastly I know Windows XP originally ran on a machine with as little as 450Mhz and 128MB of RAM, but that was before 3 service packs and all the newest software. Don't forget computer design revisions, including new motherboard designs (from AT to ATX), and power management, and the Os industry for retaining code and drivers for hardware that hasn't been used for decades except by institutions that run older hardware for historic value. So if you want a distro that work on early anthing look to DSL or Puppy; both offer the actual lowest requirement out there. If you want a Distro that will run all of the newest Linux apps then look to the big names like Debian (inc. Ubuntu), Suse (openSuse), and Redhat (Fedora).

---

### Post by LaRoza on 2008-07-23
> **LowSky said:**
> The alt install cd still requires 256 MB as the OP clearly states aswell. Do I feel that OSes are becoming too bloated, well yes but its due to all the software they come standard with that most people never use or know is included. For instance Ubuntu comes preinstall with bluetooth support, games, openoffice, and 4 media applications. Does this make it easier for new users to use, of course but it also puts a strain on older systems.

As I said, it can be used with 64 MB (although you certainly can't use Ubuntu in full like that...).

OS's are not. Some distros are,  but many are very lean. Linux can be made to run on very low specs, but distros can include more software by default and services which adds to them. If you take Debian Unstable and install it, you'll see it flies with GNOME, whereas Ubuntu doesn't.

---

### Post by Trinoc on 2008-07-23
> **snowpine said:**
> The whole point of a Live CD is that you can try out a fully-functional Ubuntu without touching anything on your hard disk. If it created a swap partition or otherwise messed with your hard drive in any way, that would be a HUGE turn-off for most Live CD users. (I do think it will use an existing Linux swap, though.)
I wouldn't dream of suggesting it should mess with the user's disk without permission, particularly when running in live CD mode. However, even in live CD mode there could be a non-default option to use any existing Linux swap partitions found on the disk, and when doing an actual installation a swap partition is created if necessary anyway, so it may as well be used in the installation process.

> As pointed out, there are other ways to install without using a Live CD, so I don't really see the problem. :)
The problem is that Ubuntu is presumably aimed at ordinary computer users who are accustomed to getting a computer with Windows already installed on it. It has to be made as easy as possible if the Microsoft behemoth is ever to be defeated, just as Microsoft defeated IBM before with MS-DOS.

Ubuntu's quasi-African theme seems to suggest it is the system for people all over the world, particularly those places where going down to PC World to buy a new, high-spec machine is not an option. The amount of perfectly good discarded computer power around the world is scandalous, and I feel any proposed replacement for the bloated systems we are sold at the moment should make the ability to utilise this resource a priority.

---

### Post by LaRoza on 2008-07-23
> **Trinoc said:**
> 
The problem is that Ubuntu is presumably aimed at ordinary computer users who are accustomed to getting a computer with Windows already installed on it. It has to be made as easy as possible if the Microsoft behemoth is ever to be defeated, just as Microsoft defeated IBM before with MS-DOS.
It is as easy as possible! What more do you want? It can be installed on computers that XP can't easily be installed on. Microsoft didn't defeat IBM with MS-DOS. IBM hired MS to supply the OS for their PC's. It was Compaq who made the IBM legal clones that resulted in IBM's demise.

> 
Ubuntu's quasi-African theme seems to suggest it is the system for people all over the world, particularly those places where going down to PC World to buy a new, high-spec machine is not an option. The amount of perfectly good discarded computer power around the world is scandalous, and I feel any proposed replacement for the bloated systems we are sold at the moment should make the ability to utilise this resource a priority.
I have installed Ubuntu on computers that originally ran Windows 98, which is beyond any modern OS's expectation.

---

### Post by halitech on 2008-07-23
I brought a 9 year old compaq armada laptop back to life using Xubuntu that was designed for windows 98 and while it may not run as fast as my desktop (P4 1.8  ) it does the job AND works with a brand new USB wireless adapter so I'm not teethered to a wire when I want to use it. It's just a matter of finding out what to strip out and what is out there for lighter apps so it runs better.

---

### Post by snowpine on 2008-07-23
> **Trinoc said:**
> The problem is that Ubuntu is presumably aimed at ordinary computer users who are accustomed to getting a computer with Windows already installed on it. It has to be made as easy as possible if the Microsoft behemoth is ever to be defeated, just as Microsoft defeated IBM before with MS-DOS.

No offense (this conversation is all in good fun :)), but I think you are projecting your own values here... I really don't think "defeating the Microsoft behemoth" is Canonical's explicit goal. I think they are just trying to make the best product they are capable of making. 

Besides, Microsoft is doing just fine defeating themselves with Vista!

---

### Post by Trinoc on 2008-07-23
> **LaRoza said:**
> As I said, it can be used with 64 MB (although you certainly can't use Ubuntu in full like that...).

OS's are not. Some distros are,  but many are very lean. Linux can be made to run on very low specs, but distros can include more software by default and services which adds to them. If you take Debian Unstable and install it, you'll see it flies with GNOME, whereas Ubuntu doesn't.
I don't have a problem about large numbers of packages occupying a large amount of disk space - I can either choose not to install things I don't need, or fit a larger disk. My problem is with the use of basic motherboard resources, particularly RAM. If you can't even get as far as installing a basic system ... say GUI, Firefox, email ... without a mass of RAM, then you don't get over the first hurdle of escaping from Windows.

I run Windows 2000 in my main PCs at the moment, and I don't plan ever to update to XP or Vista or beyond if I can possibly avoid it. They have 1GB or RAM each, but according to Task Manager the majority of this is used most of the time as disk cache - a good speed-up, but non-essential to basic running. Virtual memory should allow just about anything to run in a system provided it has enough RAM for the resident kernel and a reasonable part of the active application(s). Of course it will run slowly, but it will run.

I come from the old school of programming where 64K used to be regarded as a big program. More sophisticated software obviously requires more memory, but what I see in most cases is not this at all ... it is a realisation by programmers that they can ask for as much memory as they like so they make no effort at all at even the most basic optimisation. With the advent of 64-bit processors, I expect that programs bigger than 4 gigabytes will soon become common. It is Parkinson's law ... the software expands to fill the available space. It would help if people learning programming these days had to write a few applications to run in thumbnail processors with 4K-16K of RAM, then they might realise that small can sometimes be beautiful.

---

### Post by Trinoc on 2008-07-23
> **snowpine said:**
> No offense (this conversation is all in good fun :)), but I think you are projecting your own values here... I really don't think "defeating the Microsoft behemoth" is Canonical's explicit goal. I think they are just trying to make the best product they are capable of making. 

Besides, Microsoft is doing just fine defeating themselves with Vista!
No offence taken! :)

I agree that Vista is a classic case of shooting in the foot - and the best opportunity Linux has ever had do gain a foothold of its own. Whether by accident or by design, Ubuntu seems to have become the Linux distro to do this if anything can. For the first time, when friends complain that their old Windows PCs are limping along and they can't face the thought of "upgrading" to Vista, I can seriously suggest they try Ubuntu instead, without having to defend it as a too-complex system for geeks. If this opportunity to get free software out to the masses is missed, we might not get another chance for a long time.

---

### Post by markjensen on 2008-07-23
> **snowpine said:**
> No offense (this conversation is all in good fun :)), but I think you are projecting your own values here... I really don't think "defeating the Microsoft behemoth" is Canonical's explicit goal.
...
Might this be an (in)opportune time to post Ubuntu's #1 bug listed?
[https://launchpad.net/ubuntu/+bug/1](https://launchpad.net/ubuntu/+bug/1)

As for the original post/premise, I think that the responses and conversation that has followed shows that comparing the Ubuntu LiveCD install method to a Windows method (which is amazingly like the Alternate CD) isn't quite comparing them on the same plane.

---

### Post by snowpine on 2008-07-23
> **markjensen said:**
> Might this be an (in)opportune time to post Ubuntu's #1 bug listed?
[https://launchpad.net/ubuntu/+bug/1](https://launchpad.net/ubuntu/+bug/1)


I've never read that before; very funny, and I stand corrected!
Thanks for the link.

---

### Post by LaRoza on 2008-07-23
> **Trinoc said:**
> I don't have a problem about large numbers of packages occupying a large amount of disk space - I can either choose not to install things I don't need, or fit a larger disk. My problem is with the use of basic motherboard resources, particularly RAM. If you can't even get as far as installing a basic system ... say GUI, Firefox, email ... without a mass of RAM, then you don't get over the first hurdle of escaping from Windows.
You can do that...

> 
I come from the old school of programming where 64K used to be regarded as a big program. More sophisticated software obviously requires more memory, but what I see in most cases is not this at all ... it is a realisation by programmers that they can ask for as much memory as they like so they make no effort at all at even the most basic optimisation. With the advent of 64-bit processors, I expect that programs bigger than 4 gigabytes will soon become common. It is Parkinson's law ... the software expands to fill the available space. It would help if people learning programming these days had to write a few applications to run in thumbnail processors with 4K-16K of RAM, then they might realise that small can sometimes be beautiful.

Try floppix [http://floppix.ccai.com/](http://floppix.ccai.com/)

Linux can be very light (it runs on bare hardware in NASA probes) or very heavy (OpenSUSE...). Ubuntu is somewhere in the the middle, but it pretty heavy because it includes a lot. Making it lighter would be simple, just make it like Slackware (32 MB of RAM needed to run it!) but that would defeat its purpose.

---

### Post by Trinoc on 2008-07-23
I've now tried installing the Ubuntu 8.04 alternate CD on the 166MHz Gateway 2000 with 64MB of RAM, a 6GB ext3 root partition and a 2GB swap partition. It all seemed to be going well, if a bit slow, until 75% through the "Installing the base system" phase with "Storing language" displayed, then it seemed to hang up ... except that the hard disk is still getting accessed. It's been in that state for about 20 minutes, and I'll have to pack up for the night soon and try again tomorrow. The disk accesses sound irregular, suggesting something is going on, but the progress bar just isn't moving.

---

### Post by dje on 2008-07-23
> **Trinoc said:**
> I've now tried installing the Ubuntu 8.04 alternate CD on the 166MHz Gateway 2000 with 64MB of RAM, a 6GB ext3 root partition and a 2GB swap partition. It all seemed to be going well, if a bit slow, until 75% through the "Installing the base system" phase with "Storing language" displayed, then it seemed to hang up ... except that the hard disk is still getting accessed. It's been in that state for about 20 minutes, and I'll have to pack up for the night soon and try again tomorrow. The disk accesses sound irregular, suggesting something is going on, but the progress bar just isn't moving.

Normal Ubuntu 8.04.1 with GNOME will not run useably on 64mb of ram ;)

---

### Post by halitech on 2008-07-23
Ubuntu will need 256 to run, even if the installer will work on 64meg. I'd really recommend going with Puppy or DSL on that machine as even Xubuntu will have trouble running unless you go with 7.04 or 6.06 and that will just open up a whole new can of worms.

---

### Post by Trinoc on 2008-07-23
> **dje said:**
> Normal Ubuntu 8.04.1 with GNOME will not run useably on 64mb of ram ;)
The bare minimum requirements say that 64MB is runnable, but slow. Anyway, I'm not getting to the point of running Gnome - as I say, it's stuck 75% through text-based installation.

[https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

(OK, it says 300MHz, so I expect it to run even slower at 166MHz, but it should still install).

I'm downloading the XFCE version of LinuxMint - maybe I'll have better luck with that tomorrow.

---

### Post by dje on 2008-07-23
> **Trinoc said:**
> The bare minimum requirements say that 64MB is runnable, but slow. Anyway, I'm not getting to the point of running Gnome - as I say, it's stuck 75% through text-based installation.

[https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

(OK, it says 300MHz, so I expect it to run even slower at 166MHz, but it should still install).

I'm downloading the XFCE version of LinuxMint - maybe I'll have better luck with that tomorrow.

Well from experience with a 256mb machine which is no speed demon even with xubuntu, i would suggest you just try [crunchbang linux]("http://crunchbang.org/projects/linux/"), seriously it will run much much faster than xfce on that machine

dje

---

### Post by halitech on 2008-07-23
```
Bare Minimum requirements

It should be possible to get Ubuntu running on a system with the following minimum hardware specification, although it is unlikely that the system would run well. You should use the Alternate install CD to attempt such an installation.

    * 300 MHz x86 processor
    * 64 MB of system memory (RAM)
    * At least 4 GB of disk space (for full installation and swap space)
    * VGA graphics card capable of 640x480 resolution
    * CD-ROM drive or network card 

```

these are the minimums, not 4 out of 5 but 5 out of 5. If you have a 166mhz cpu, you just failed 1 requirement which means Ubuntu will not run. You should try Xubuntu if you are determined to get *buntu running on that machine with the text based installer.

```

Low-spec computers (Xubuntu)
Minimum requirements

    * 166 MHz processor
    * 64 MB of system memory (RAM)
    * At least 1.5 GB of disk space
    * VGA graphics card 

```

---

### Post by Trinoc on 2008-07-23
> **halitech said:**
> ```
Bare Minimum requirements

It should be possible to get Ubuntu running on a system with the following minimum hardware specification, although it is unlikely that the system would run well. You should use the Alternate install CD to attempt such an installation.

    * 300 MHz x86 processor
    * 64 MB of system memory (RAM)
    * At least 4 GB of disk space (for full installation and swap space)
    * VGA graphics card capable of 640x480 resolution
    * CD-ROM drive or network card 

```

these are the minimums, not 4 out of 5 but 5 out of 5. If you have a 166mhz cpu, you just failed 1 requirement which means Ubuntu will not run. You should try Xubuntu if you are determined to get *buntu running on that machine with the text based installer.
Please explain how a slower CPU will prevent a system from running altogether (rather than just running slower).

---

### Post by dje on 2008-07-23
> **Trinoc said:**
> Please explain how a slower CPU will prevent a system from running altogether (rather than just running slower).

it would "run" but you couldn't use it, it would just lag way too much

---

### Post by halitech on 2008-07-23
the same way that it can stop you from running a windows game that needs a P4 2.0gig to run and you try to run it on a P3. The base code can tell what you have for a CPU and it will stop things and not allow you to continue.

---

### Post by Trinoc on 2008-07-23
> **dje said:**
> it would "run" but you couldn't use it, it would just lag way too much
I'm not expecting it to be a fast enough system for normal use - it's just an experiment on a disposable setup to check out that I can install it as dual boot with Windows 2000, without messing everything up.

---

### Post by Trinoc on 2008-07-23
> **halitech said:**
> the same way that it can stop you from running a windows game that needs a P4 2.0gig to run and you try to run it on a P3. The base code can tell what you have for a CPU and it will stop things and not allow you to continue.
Games are frequently time-critical - ordinary console operations are not. If it objects to a less than P3 processor then surely it would say so, not just hang up. The minimum requirements say x86 processor, which presumably means it would even run on a 386, though I think that would be ridiculously slow.

---

### Post by halitech on 2008-07-23
if you want to get picky, it says for minimal install
```

# Intel 486 processor
# 32 MB of system memory (RAM)
# 300 MB of disk space

```
but that is also for a barebones no gui install with very few packages installed and wouldn't allow you to do much. for a low end machine such as you are dealing with, if you expect to do anything including install, you need to go with the alternate install cd for Xubuntu.

I know you say you are experimenting to see if you can set up a dual boot with windows 2000 and ubuntu but the only thing I see you really getting done is frustrating yourself with an OS that will not install because you do not have a machine to run it. If you want to learn how to do it, go with Xubuntu and learn cause the steps will be the same on both versions.

---

### Post by cariboo on 2008-07-23
Why is it that everbody insist that to have a useable a ditribution it has to have a gui. I just used  dsl to intall a minimal installation on a AST Bravo 75Mhz with 128MB of 30pin ram. I don't bother with the gui as it is not needed for the intended use. I enapled apt, and installed the applications I need and this computer runs quite acceptabley and it uses .deb's like a real distribution should:)

Tomorrow I'm going to try a minmal Ubuntu 8.04 installation, just to see if I can.

Jim

---

### Post by lswb on 2008-07-23
> **Trinoc said:**
> Please explain how a slower CPU will prevent a system from running altogether (rather than just running slower).

Suppose the cpu is in the middle of processing some hardware interrupt service routine. Another hardware interrupt could occur before a slow processor has enough time to finish the 1st. If the ISRs are dealing with any time-sensitive volatile data in registers or IO ports, it is possible that one or both will be unable to complete without errors.

---

### Post by sydbat on 2008-07-23
This may seem a bit out of line, but this is 2008. Modern OS's like Ubuntu have higher expectations for hardware because it is readily available...and the minimum has been around for years. The days of running 64K programs are 35 - 40 years in the past. 

While I understand the OP would like to run a current Linux flavour on an older machine, I think it is unreasonable to expect a specific Linux/Unix OS to fit his narrow view of "what should be able to run". There are, as has been pointed out, several distro's that will most likely run on his older box. If he is unhappy with those choices, perhaps he should consider an upgrade to enable running a larger distro like Ubuntu.

Or he's spreading FUD...

---

### Post by a0u on 2008-07-23
> **Trinoc said:**
> I did think I would be able to try it on a couple of old Pentium 3s with only 256MB of RAM

That I did, with an early 2000s Toshiba Satellite with 123 MB of functional RAM (128 MB original) and a 700 MHz processor.

I believe the main reason Ubuntu appears "bloated" is because of the heavy GNOME desktop, but the base system actually performs quite well.  Building from the ground up would give you a better result.  I opted to install only the base system using the minimum install CD and then manually construct the desktop using more lightweight components (e.g., Openbox, SLiM, Dillo, PCManFM) than what the default distribution has.  Less than a minute to boot and two seconds to log in...

I should also add that the installation took around 30 minutes to complete.

---

### Post by eriqjaffe on 2008-07-24
I always enjoy an opportunity to break this out:

[img]http://img367.imageshack.us/img367/685/20080511160503scrotko3.png[/img]

Granted, that was a low water mark for RAM consumption, and that was without anything running.  But even with Opera 9.5 going, I'd rarely break 95mb used.

---

### Post by Trinoc on 2008-07-24
> **halitech said:**
> if you want to get picky, it says for minimal install
```

# Intel 486 processor
# 32 MB of system memory (RAM)
# 300 MB of disk space

```
but that is also for a barebones no gui install with very few packages installed and wouldn't allow you to do much. for a low end machine such as you are dealing with, if you expect to do anything including install, you need to go with the alternate install cd for Xubuntu.
I'm sure everything you say is right, but it still doesn't explain why a text-based installer hangs up 75% of the way through the process, long before any GUI has even been contemplated.

> I know you say you are experimenting to see if you can set up a dual boot with windows 2000 and ubuntu but the only thing I see you really getting done is frustrating yourself with an OS that will not install because you do not have a machine to run it. If you want to learn how to do it, go with Xubuntu and learn cause the steps will be the same on both versions.
That is the next thing to try ... but when I tried the Xubuntu live CD (on a larger PC) it lacked Ubuntu's automatic ability to mount my existing Windows partitions and to connect to my Windows shares over the LAN - both essential features if I am to make a seamless transition from Windows to Linux. No doubt I could edit "mount" commands into some file or other, and set up a Samba client, but this sort of stuff is daunting even to a geek like me. To an ordinary user who wants to do browsing, email and word processing it would be an impenetrable barrier.

---

### Post by Trinoc on 2008-07-24
> **sydbat said:**
> Or he's spreading FUD...
Oh well ... this thread started so well, with lots of helpful suggestions, but now someone thinks I'm some sort of troll. I'm not ... I'm just a techie person whose area of expertise happens to be small programs in small processors, so when it comes to stuff like Windows and Linux I'm basically a user, albeit one who can find his way around a computer and understands the sorts of things the system has to be doing down inside the works. I want to see Linux or something like it become the OS of choice for ordinary users who neither know nor care what is going on in the box. Ubuntu is the closest thing I've seen to that so far, but it won't take many little things to go wrong in installation to make the average punter think "Sod it - I'll buy a Vista machine instead!".

---

### Post by mjwhitfield on 2008-07-24
> **Trinoc said:**
> but it won't take many little things to go wrong in installation to make the average punter think "Sod it - I'll buy a Vista machine instead!".If they brought a machine that was capable of running Vista, Ubuntu would install and run without any issues :)

---

### Post by Trinoc on 2008-07-24
> **mjwhitfield said:**
> If they brought a machine that was capable of running Vista, Ubuntu would install and run without any issues :)
I was thinking of the alternatives as being (1) Install Ubuntu on an existing machine and get many more years of good work out of it instead of taking it to the dump, or (2) Dump it and buy a machine with twice the speed, memory and disk capacity, which will run Vista, but not any faster or better than anything done before (very probably slower and more complex), but whose inflated spec has no justification other than to accommodate the ever-increasing bloat of Windows software. I think it would be tragic if Linux systems went the same way. Yes, it is possible for a Linux system to have the capability of running very large and processor-hungry applications on high spec machines, but I don't believe it is necessary for a system capable of running such applications to have a high spec machine as its *minimum* requirement.

I could probably go down to the council dump right now and pick up more discarded computing power than all of the mainframes I worked on up to the end of the 1970s. Some of it will need repair or replacement, but for the most part it will have been thrown out either because the owner needed to "upgrade" to the latest version of Windows or, even more wastefully, the system simply crashed losing all of the user's data, and they discovered that, even if they had been running Windows Backup regularly (highly unlikely), that it was no use at all to restore a system that has stopped working at a fundamental level.

This waste of computing power is something Linux could solve, but it won't do that if it follows the Microsoft route of making the software expand to fill whatever is the latest new machine spec.

---

### Post by philinux on 2008-07-24
The latest spec machine have either 1 gig or 2 gig of ram.

I ran Ubuntu on my pentium 3 500mhz with 320 meg ram.

---

### Post by Trinoc on 2008-07-24
> **philinux said:**
> The latest spec machine have either 1 gig or 2 gig of ram.

I ran Ubuntu on my pentium 3 500mhz with 320 meg ram.
That's reasonable, so long as Linux does not follow the trend of getting more and more power and space-hungry as machine specs improve. If people who want to upgrade to Ubuntu 12.5 in three years time have to throw away the machines on which they are installing Ubuntu 8.04 today, we will have made little progress beyond the current Windows philosophy.

Back in the days of 1970s mainframes, there was a memory-hungry IBM system feature which went by the initials "CICS". I remember seeing a cartoon in one of the trade papers ... Manager: "Why have you put in a request for all of that extra memory?"; Techie: "Oh, just for CICS!" ... The moral is that improved computing speed and capacity should be so that larger and more CPU-hungry applications can run, or so that existing applications can run larger data sets or the same data sets much more quickly; the purpose of increased machine capacity is *not* so that it can be immediately swallowed up by making the operating system larger and slower (or, worse, because the increased capacity is the only way to run a system that is already out there, like Vista).

---

### Post by Trinoc on 2008-07-24
A quick update ... I've now run the text-based installer on the Xubuntu alternate CD - which looks identical to that on the Ubuntu alternate CD - and, guess what, it has stalled at 75% displaying "Storing language", and with the hard disk apparently still being accessed regularly, though no CD access ... exactly the same problem as with Ubuntu. I didn't think the Gnome/XFCE difference could be the problem, since it is nowhere near starting up a GUI yet.

It's been like that for over half an hour now. I'll let it run for maybe an hour, but if it hasn't progressed after that I think I can safely assume it's stuck in a loop.

---

### Post by philinux on 2008-07-24
I hope your burning at 4x speed and check the cd for defects from the menu option.

I always use cdrw's now - no more coasters.

I'd try something else like knoppix or dsl or puppy.
[http://www.knopper.net/knoppix-info/index-en.html](http://www.knopper.net/knoppix-info/index-en.html)

---

### Post by Trinoc on 2008-07-24
> **philinux said:**
> I hope your burning at 4x speed and check the cd for defects from the menu option.
Burning at lower speed doesn't necessarily produce a better CD - in fact out of the Ubuntu variants I have made in the last few days the only one that failed was one I burned at less than full speed. Anyway, yes, I do check then for readability after writing.

> I'd try something else like knoppix or dsl or puppy.
[http://www.knopper.net/knoppix-info/index-en.html](http://www.knopper.net/knoppix-info/index-en.html)
That would defeat the object. I want to use some version of Ubuntu because I think it is likely to become the de facto standard for ordinary folks to use, and hence the one I'm likely to recommend to friends who don't want to go to Vista.

However, before risking the data on my two main PCs I want to make sure I understand perfectly how to make Ubuntu dual boot with Windows 2000 (using either the Win2k boot menu or something independent like GAG - not relying on GRUB in the Ubuntu partition). This means trying to install it on older, lower-spec machines first. It looks like the 64MB Gateway is just too old, but I hope I can at least get it running on a Pentium 3 with 256MB.

The Xubuntu text installer has been stuck on 75% for nearly an hour and a half now, and the hard disk is still making noises like something is happening. I think it's time to assume it is never going to complete and to give up on the Gateway machine - at least as far as Ubuntu variants are concerned.

---

### Post by overdrank on 2008-07-24
Its my belief this thread has run it's course and moving to  Recurring Discussions
Moved:)

---

### Post by Trinoc on 2008-07-24
> **overdrank said:**
> Its my belief this thread has run it's course and moving to  Recurring Discussions
Moved:)
Is 24 hours a typical time for a thread to be classified as stale?

---

### Post by Yes on 2008-07-24
The minimum amount of RAM for Xubuntu is 192 MB.

Ubuntu isn't designed to run on old hardware.  It's designed to be a modern operating system, full with all the features you would expect a modern operating system to have.  Try DSL or Puppy, either of those will run great.

---

### Post by Hospadar on 2008-07-24
If you want to run linux on teeny-tiny machines, I'd suggest you stay away from regular ubuntu, while it gets great performance out of hardware in comparison to vista or osx, it has lots of great features, which even when well written, require a sizeable amount of RAM.

You may want to try starting with ubuntu server, and installing fluxbox and xdm on top to get a light desktop environment.  Or consider using a debian basic installation and installing your desktop on top of that.  Alternatively, there are some great super-light distros out there (dsl, puppy) that you might try if all else fails (these tend to be a little feature-deficient, but run *very* light)

---

### Post by Trinoc on 2008-07-24
> **Yes said:**
> The minimum amount of RAM for Xubuntu is 192 MB.
This appears to contradict post no. 34.

> Ubuntu isn't designed to run on old hardware.  It's designed to be a modern operating system, full with all the features you would expect a modern operating system to have.  Try DSL or Puppy, either of those will run great.
As I've explained already, the purpose is to dry run Ubuntu, not just to get any old Linux system onto the PC. I would have thought that any PC capable of running Windows 2000 *ought* to be able to run a decent Linux GUI.

What will happen in years to come, assuming Ubuntu or some other Linux variant becomes established? Will everyone who wants to upgrade to the latest version have to throw away their computers and buy new ones, as they have to do for Vista now?

As I've said, I have no problems at all with a system being able to make use of increased processing power if it is available, but it seems, in Linux as in Windows, that improved power gets swallowed up by the system as soon as it comes onto the market, and the actual improvement seen by the user for all of the extra money - apart from a few prettier graphics - seems minimal.

---

### Post by zmjjmz on 2008-07-24
Wait hold on stop right there.
**It is *not* hanging up on installing language packs**
Since there are a lot of language packs to install, it just takes a while.
Far longer than 20 minutes, if my experience with a 192MB RAM, 400MHz Celeron, 4.3GB HDD eMachine is any indication.

But seriously, the Gateway can run a decent Linux GUI, just not one powered by Ubuntu.
On those machines, you can get away with installing Arch (a bit hard, but follow the beginners wiki) and then building it up yourself.
DSL-N also has a decent Linux GUI, and uses the current Linux kernel. It should run nicely on that machine.


Seriously though, I'd recommend a distribution based off of the 2.4.x kernel (which is as old as XP, and since most 2.4.x distros use 2.4.31, it isn't so old) like Damn Small Linux or DeLi Linux.

---

### Post by Yes on 2008-07-24
> **Trinoc said:**
> This appears to contradict post no. 34.


As I've explained already, the purpose is to dry run Ubuntu, not just to get any old Linux system onto the PC. I would have thought that any PC capable of running Windows 2000 *ought* to be able to run a decent Linux GUI.

What will happen in years to come, assuming Ubuntu or some other Linux variant becomes established? Will everyone who wants to upgrade to the latest version have to throw away their computers and buy new ones, as they have to do for Vista now?

As I've said, I have no problems at all with a system being able to make use of increased processing power if it is available, but it seems, in Linux as in Windows, that improved power gets swallowed up by the system as soon as it comes onto the market, and the actual improvement seen by the user for all of the extra money - apart from a few prettier graphics - seems minimal.

I got it from here: [http://xubuntu.com/get](http://xubuntu.com/get) (scroll down).  You could probably run Ubuntu without X on 64 MB of RAM, which is probably what they're talking about when they say "*Bare Minimum* Requirements".

There are a number of distros that are designed to run on older hardware.  Ubuntu is not one of those distros.  If you want to run Linux on 64 MB of RAM, try DSL or Puppy.  Xubuntu will run fine your 256 MB computers, though.

---

### Post by Trinoc on 2008-07-24
> **zmjjmz said:**
> Wait hold on stop right there.
**It is *not* hanging up on installing language packs**
Since there are a lot of language packs to install, it just takes a while.
Far longer than 20 minutes, if my experience with a 192MB RAM, 400MHz Celeron, 4.3GB HDD eMachine is any indication.
I'm now running the Ubuntu alternate CD text-based install onto a clean disk on a 600MHz Pentium 3 with 256GB of RAM. Everything ran a lot faster, as expected, and in particular the language storing bit was gone in a minute or two - compared with an hour and a half on the Gateway before I gave up. I may be wrong, but it doesn't seem likely to me that the Gateway install was ever going to finish.

The P3 install got through the language install bit and everything else on that progress bar in maybe 20 minutes since first boot. Then it went on to "Select and install software" and after roughly another 40 minutes it has reached 83%. At least something is happening and the progress bar is moving, if slowly. I don't remember a stage as long as this when I used the graphic installer on a friend's machine - it was a 1400MHz machine with 512MB RAM, but I still think I would have noticed something taking this long.

---

### Post by snowpine on 2008-07-24
Hi Trinoc, when I first posted yesterday, I agreed with you 49% and disagreed 51%--now I think I agree 51% and disagree 49%. :) Every day, I help someone on these forums whose installation fails due to insufficient ram, but they don't know that's the reason. While I still disagree that Ubuntu should support 64mb computers (sorry), I think it would be a great idea if 1) the system requirements were more clearly posted on the download page; 2) the installer ran a system scan and gave clear feedback if the minimum requirements are not met.

Finally, have you checked out Fluxbuntu? I don't recommend it to everyone, but I think it might be perfect for you with your techie background.

---

### Post by snowpine on 2008-07-24
One last tip... have you played around with virtualization? You can use your faster computer to create virtual machines with various amounts of ram (64, 128, 256, etc) and practice your installation skills without actually messing up your system.

---

### Post by Trinoc on 2008-07-24
> **snowpine said:**
> Hi Trinoc, when I first posted yesterday, I agreed with you 49% and disagreed 51%--now I think I agree 51% and disagree 49%. :) Every day, I help someone on these forums whose installation fails due to insufficient ram, but they don't know that's the reason. While I still disagree that Ubuntu should support 64mb computers (sorry), I think it would be a great idea if 1) the system requirements were more clearly posted on the download page; 2) the installer ran a system scan and gave clear feedback if the minimum requirements are not met.
I'm prepared to accept that trying to get it running on a 64MB Pentium 1 was probably pushing my luck a bit, even though as I say it runs Windows 2000, if a bit slowly. To run on 256MB will be OK, though it will exclude all of my old laptops, and not being able to use the graphic installer is a disappointment.

My main worry is for the future. Will the Ubuntu (or whatever) of 2012 require a 4-core, 128-bit, 12GHz processor with 64 gigabytes of RAM and a minimum 8 terabytes of disk space? Computing for the masses (and I don't mean only the affluent masses) isn't going to happen if every "improvement" in software makes everything larger and slower, and people have to buy the latest hardware (and waste the old stuff) just to stand still.

I decided when I discovered that XP would require me to seek permission from Microsoft to activate it every time I upgraded my PC or even restored a backup, that the last Windows system I ever wanted to use was Windows 2000. Sooner or later, things I need to be able to do will not be supported in Win2k any more, and, just as with USB under Windows NT, new hardware will come along which I can't use. I saw Linux as my salvation from this, with Ubuntu looking like being the closest to achieving that goal. OK, I won't have to pay anything for Ubuntu 2012 (I hope), but if the only way I can support the latest gadgets is to use a system which requires a bigger and bigger PC to run it, then the spiral of bloat will continue much as it does now under Microsoft.

> Finally, have you checked out Fluxbuntu? I don't recommend it to everyone, but I think it might be perfect for you with your techie background.
It's on the list of things to try ... :)

---

### Post by Trinoc on 2008-07-24
> **snowpine said:**
> One last tip... have you played around with virtualization? You can use your faster computer to create virtual machines with various amounts of ram (64, 128, 256, etc) and practice your installation skills without actually messing up your system.
Not so far. It's worth a go.

---

### Post by Yes on 2008-07-24
> **Trinoc said:**
> My main worry is for the future. Will the Ubuntu (or whatever) of 2012 require a 4-core, 128-bit, 12GHz processor with 64 gigabytes of RAM and a minimum 8 terabytes of disk space? Computing for the masses (and I don't mean only the affluent masses) isn't going to happen if every "improvement" in software makes everything larger and slower, and people have to buy the latest hardware (and waste the old stuff) just to stand still.

Why would you expect a modern distro to run on old hardware?  As any software grows and matures, it requires newer hardware to run it.  You won't need to buy new hardware for every new release, but you can't expect it to run on everything.

---

### Post by halitech on 2008-07-24
the good thing about most versions of linux, is that most are supported for 2-5 years (depends on the distro) and in that time, most of the bugs are fixed, security holes are patched and afterwards, should run forever (long as the hardware holds out). If something does need to be upgraded, most can upgrade just the parts you need (like the kernel, new app, etc) without updating everything so unless you were borderline to start with, you can pick and chose what needs to be upgraded.

I'll admit, I havent tried to install a new kernel manually but it used to be done so no reason why it shouldn't be able to be done today with a little elbow grease :)Maybe I'll install warty on my old P2 and see what happens when I try to put a new kernel in it, see if I can make the machine work or go boom :D

---

### Post by a0u on 2008-07-24
> **Trinoc said:**
> My main worry is for the future. Will the Ubuntu (or whatever) of 2012 require a 4-core, 128-bit, 12GHz processor with 64 gigabytes of RAM and a minimum 8 terabytes of disk space? Computing for the masses (and I don't mean only the affluent masses) isn't going to happen if every "improvement" in software makes everything larger and slower, and people have to buy the latest hardware (and waste the old stuff) just to stand still.
 
Increasing minimum requirements is an inevitability as hardware advances over time. Today's minimum specs would seem like a nightmare compared to those from the 1990s, but simply comparing numbers is inherently misleading, because I can arguably accomplish more with the present Ubuntu distro (e.g., multimedia and gaming) than I can with a 1990s GNU/Linux system. Thus, a heavier resource usage does not necessarily mean "wasteful"...what matters is how a developer justifies it.
 
The future's minimum requirements might seem titanic to us - and I hope you are exaggerating - but let's remember that we cannot assume that the future's computer experience will be exactly the same as the present's. As for older hardware, that's one reason we have so many distros: to cover every possible niche there is. In addition, it's been shown that Ubuntu can be easily customized to fit specific needs.
 
If you are concerned about where Ubuntu is heading, might I pursuade you to consider [contributing to the project]("http://www.ubuntu.com/community/processes/newdev"). Criticism becomes more productive when you suggest solutions. :)
 
...
By the way, I believe the bloat you're referring to actually originates from the heavy [GNOME desktop]("http://www.gnome.org/") (which isn't directly part of the "Ubuntu" project), not the base system. In general, though, I agree with you that the entire distribution can be made lighter...
 
> **Trinoc said:**
> Is 24 hours a typical time for a thread to be classified as stale?
This isn't your typical thread. ;) Normally, there wouldn't be so many replies is such a short time, with the debate going in a roundabout fashion (since everyone apparently holds strong beliefs)...but this is still an interesting subject to discuss.

---


---
title: "Distros to learn help please"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Mobidoy on 2008-07-07
Hello everyone, 

it is not my first try at linux and ubuntu but, i had life issues that prevented me to give the time needed to learn. 

What i would like, is to learn how linux works out and how to play with it.

I have a notebook that i have setup for it, at the moment, i have ubuntu installed and 5 other partitions of 10 Gb ext3 just for distros, one will be used for linux from scratch. I can set up more if i need to, this is only a start, i also have a 20gb ext3 partition for files and programs that i will use in all distros, i have a 500Mb ext3 partition for /tmp and another 5Gb for swap.

I also have some live Usb in case things go wrong lol :) 

My questions:  

1- What other distros should i install to try out and help in my learning process ?

2- Where should i start to learn properly ? 

3- What are the good links to learn how to optimize your distro to your computer hardware ?

My background is fairly good, i did a lot of tech support for any flavor of Microsoft OS, even DOS. I also know how a computer work, how to build one, most of the technical term and specification for hardware, and, i also did some hacking starting back on basic on a TI99/a back in the mid 80's and on C, C++ and C#.

I started with Ubuntu because i know the community is the best out there :) 

Thanx for your help !!

---

### Post by iaculallad on 2008-07-07
For the list of Linux Distributions to install and learn, try to visit [distrowatch.com]("http://distrowatch.com/"), that site has a comprehensive list of distro's, including utilities.

*List is updated regularly.

---

### Post by tjwoosta on 2008-07-07
i think the best way to learn linux is with a live cd 
(that way you dont have to make any changes to your computer)

then if you decide your ready, you can go ahead and install to the harddrive

here is the most complete list of linux live cd's that ive ever found
[http://www.frozentech.com/content/livecd.php]("http://www.frozentech.com/content/livecd.php")
one that is not on this list for some reason is Fedora

---

### Post by BGFG on 2008-07-07
You should also check out OpenSolaris if your interest is learning and experimenting. The ZFS filesystem seems interesting and the desktop is GNOME. I have a live cd and was thinking of installing it in VirtualBox for a test drive. The speed of the live cd is also impressive.

---

### Post by Mobidoy on 2008-07-07
Thanx for the input so far, i dont mind installing it on my notebook, it is dedicated to that, learning, and, i want to be able to save the changes i did to the kernel, Xorg.conf etc... If something goes wrong, and i hope it will (it is the best way to learn) i have ways to get the system back, i will probably create image of the installation before i go and do major changes so i can get back and running :)

What i am mostly looking for is your opinion of: which ditros should i install ( open solaris is one), good sites with fairly updated how-to's, guides, tutorial etc for configuration and optimization (kernel, video card (ati radeon mobility x1400), cpu setting, sata disk speed up tricks etc...), and, good up to date info for the terminal command (i know some already), usefull terminal applications (like fsdik), scrpting, grub and other bootloaders, fstab etc etc... 

Thanx again !

---

### Post by Gamma746 on 2008-07-08
1. Gentoo is a fantastic distro for learning.
2. Read the handbook ([http://www.gentoo.org/doc/en/handbook/index.xml](http://www.gentoo.org/doc/en/handbook/index.xml)) and install it.
3. Set appropriate CFLAGS for your CPU ([http://gentoo-wiki.com/Safe_Cflags](http://gentoo-wiki.com/Safe_Cflags)), run ```
emerge -e system && emerge -e world
``` and everything should be optimised for your hardware.

---

### Post by cprofitt on 2008-07-08
Gentoo is a little bit on the difficult side... graduate to that...

I would personally recommend --

Arch - [www.archlinus.org](www.archlinus.org)
Debian (stable)

or really taking a deep look at Ubuntu

I learned the most from Arch (though not all knowledge transfers due to differences in how distros handle things) and continue to learn by being a member of the beginners team and unanswered posts team.

---

### Post by Mobidoy on 2008-07-08
> **PrivateVoid said:**
> Gentoo is a little bit on the difficult side... graduate to that...

I would personally recommend --

Arch - [www.archlinus.org](www.archlinus.org)
Debian (stable)

or really taking a deep look at Ubuntu

I learned the most from Arch (though not all knowledge transfers due to differences in how distros handle things) and continue to learn by being a member of the beginners team and unanswered posts team.

This is exactly why i wanted many distros, difference between each...

some are debian, some are slackware etc etc (i dont know them all lol), things are different so, there is some variants to learn from one to the other.

So, i will have: 

Ubuntu
ArchLinux
Gentoo
OpenSolaris
LFS

Any others i should look into :) Any good distro for windows gaming ? What about site to learn optimization of hardware, kernel and other files ? 

I really love this and, i was expecting someone to say Gentoo, but was waiting on it. Even if it is a distro for expert, i am a fast learner and with my previous life experience, i have found out that when you want it, no mountain is too high ! 

Keep it coming, I will edit or make a new post with the info when i will feel having enough info... I know others that had similar question but never got the proper answer :)

---

### Post by shano26 on 2008-07-08
I'm also in a similar boat (trying to get back into learning linux and finally have some dedicated hardware to try it on, live cd's/virtual machines are nice but i prefer a dedicated box :P ).

Personally i'm going to stick predominately with Ubuntu (maybe the SuSE variations for work) and learn as much as I can from it  with reasons being mainly the community seems so damn helpful and each release goes through a lot of testing and any issues that pop up other people usually experience first and are on here when I look for them. Later on down the track I'd probably investigate Gentoo as it seems to have a higher learning curve and isn't as newbie friendly.

You seem like you might already know your way around the command line but if you need a refresher I would recommend this website [http://www.linuxcommand.org/]("http://www.linuxcommand.org/") . It is a great resource on how to work your way around the command line and linux shell in general. Cheers

---

### Post by aktiwers on 2008-07-08
I have not had any good luck with gentoo yet, I guess I did not have enough time. :(

---

### Post by stoneybroke on 2008-07-08
Go here and download this free ebook it will tell you everything about Ubuntu from using the GUI to the shell all about files disks etc etc. I think this book should be available for every new user to Ubuntu it is excellent.

[http://rapidshare.com/files/63360951/Beginning_Ubuntu_Linux_2nd_Edition_-_Apress.rar](http://rapidshare.com/files/63360951/Beginning_Ubuntu_Linux_2nd_Edition_-_Apress.rar)

Enjoy and if you want any free ebooks rapidshaire.com is the place to go.

---

### Post by Mobidoy on 2008-07-08
> **shano26 said:**
> 

You seem like you might already know your way around the command line but if you need a refresher I would recommend this website [http://www.linuxcommand.org/]("http://www.linuxcommand.org/") . It is a great resource on how to work your way around the command line and linux shell in general. Cheers

Awesome, this is the kind of site i was looking for.

I want multiple distros so i can see the difference between each flavors so if someone needs some help, i have a clue of what i am looking for and, i will be able to help him/her.

I still have to review my list to see if i go thru all the variants (deb, rpm, slack, etc...)

But so far: 

Linux from scratch
Ubuntu
Gentoo
Archlinux
OpenSolaris

I dont even know what flavor they are other than ubuntu which is deb :)

---

### Post by lazyart on 2008-07-08
> **Mobidoy said:**
> Any good distro for windows gaming ?

Yeah, it's called Windows.  Don't come to Linux looking for it to run Windows apps.  Yeah, with wine many things can be done, and quite a few done very well, but it's the proverbial square peg in a round hole.

As for trying distros, I would use a virtual machine as a playground to check stuff out (have done with Hardy, Mint and Debian all while keeping my Gutsy).  No burning cds, no grubbing, etc etc.

---

### Post by Frak on 2008-07-08
> **Mobidoy said:**
> Any others i should look into :) Any good distro for windows gaming ?

Windows

There is no substitute.

---

### Post by Mobidoy on 2008-07-08
> **lazyart said:**
> Yeah, it's called Windows.  Don't come to Linux looking for it to run Windows apps.  Yeah, with wine many things can be done, and quite a few done very well, but it's the proverbial square peg in a round hole.

As for trying distros, I would use a virtual machine as a playground to check stuff out (have done with Hardy, Mint and Debian all while keeping my Gutsy).  No burning cds, no grubbing, etc etc.

> **Frak said:**
> Windows

There is no substitute.

Hehe, i am not here for the gaming, it is for personnal info and, if someone ask, i know what to answer :) 

I have my plan made, for distros, my HD is already split and i left over 80 Gb of un partition space... i also have my usb keys (1-2Gb each) ready to put images of the installation i make of every distros so, if i do something wrong, i only need to boot with another distro and put the image back in the partition then, find out what went wrong :)

---

### Post by Frak on 2008-07-08
And for learning the basics

1. Start with Ubuntu with apt-build and apt-get build-dep
2. Build your own Ubuntu OS (even just doing sudo apt-get install ubuntu-desktop works just as well for my tastes)
3. Use arch for awhile, learn how services work and how applications are built. This will teach you alot about the more major underlyings of a system
4. If you're up to it (and don't mind wasting tons of time compiling), use Sabayon (beginners Gentoo) or Gentoo to learn about major application customizations (make flags for example)


I will have to end with, at least my opinion, compiling is a useless process if you already have an application optimized for the 686 platform. Unfortunatley, Ubuntu is optimized against the 386 (old Pentium Pros that couldn't run Ubuntu anyways). Though, wereas Arch Linux is optimized against newer 686 processors. So, of course, Arch packages have an advantage over Ubuntu packages just in terms of optimized speed.

---

### Post by Mobidoy on 2008-07-08
> **Frak said:**
> And for learning the basics

1. Start with Ubuntu with apt-build and apt-get build-dep
2. Build your own Ubuntu OS (even just doing sudo apt-get install ubuntu-desktop works just as well for my tastes)
3. Use arch for awhile, learn how services work and how applications are built. This will teach you alot about the more major underlyings of a system
4. If you're up to it (and don't mind wasting tons of time compiling), use Sabayon (beginners Gentoo) or Gentoo to learn about major application customizations (make flags for example)


I will have to end with, at least my opinion, compiling is a useless process if you already have an application optimized for the 686 platform. Unfortunatley, Ubuntu is optimized against the 386 (old Pentium Pros that couldn't run Ubuntu anyways). Though, wereas Arch Linux is optimized against newer 686 processors. So, of course, Arch packages have an advantage over Ubuntu packages just in terms of optimized speed.

I do agree that compiling can be a waste of time but, i think that it is something that you need to know for a tech. As i said, i've been doing tech support as a hobby for over 20 years now and, Linux is the missing string i always wanted to have. 

Now i have time to give to it and i plan to be serious about it. I dont want to burn any steps but, i don't want to stall on things that are mostly on the user side. 

Peeps here are awesome, i am slowly filling my bookmarks and, building my multi distro istallation... i will have to look at grub and install it on it's partition soon :)

---

### Post by Frak on 2008-07-08
> **Mobidoy said:**
> I do agree that compiling can be a waste of time but, i think that it is something that you need to know for a tech. As i said, i've been doing tech support as a hobby for over 20 years now and, Linux is the missing string i always wanted to have. 

Now i have time to give to it and i plan to be serious about it. I dont want to burn any steps but, i don't want to stall on things that are mostly on the user side. 

Peeps here are awesome, i am slowly filling my bookmarks and, building my multi distro istallation... i will have to look at grub and install it on it's partition soon :)
You can learn more about compiling just using make on an Ubuntu system than using emerge on a Gentoo system.

The best way to learn is to go in, modify files and mess with the makefile to come up with a different result.

---

### Post by Inxsible on 2008-07-08
+1 to Arch. Just going through the install makes you learn more stuff than Ubuntu.

I simply love Arch. Great distro to learn. The only reason, I have shied away from Gentoo is that there is no package manager - which is good to learn how software is compiled...but once I know that, I want my OS to work for me - at least a little.

And if I really want to learn how to compile.. i can always compile a software from source in any other distro. 

Of course, I am sure Gentoo offers much more than that...but as of now it hasnt really piqued my interest so much that I would leave Arch and Debian.

---

### Post by Frak on 2008-07-08
> **Inxsible said:**
> +1 to Arch. Just going through the install makes you learn more stuff than Ubuntu.

I simply love Arch. Great distro to learn. The only reason, I have shied away from Gentoo is that there is no package manager - which is good to learn how software is compiled...but once I know that, I want my OS to work for me - at least a little.

And if I really want to learn how to compile.. i can always compile a software from source in any other distro. 

Of course, I am sure Gentoo offers much more than that...but as of now it hasnt really piqued my interest so much that I would leave Arch and Debian.
Meh, Gentoo has always struck me as a bloated OS. I say that because I easily racked up 24GB of space just used for sources and compilation within the first week. (I recompiled my kernel)

---

### Post by Inxsible on 2008-07-08
> **Frak said:**
> Meh, Gentoo has always struck me as a bloated OS. I say that because I easily racked up 24GB of space just used for sources and compilation within the first week. (I recompiled my kernel)Well...that doesn't bode well for a person like me who likes the OS to be minimalist  :D

---

### Post by Frak on 2008-07-08
> **Inxsible said:**
> Well...that doesn't bode well for a person like me who likes the OS to be minimalist  :D
:lolflag:

I do like the idea of customizing your builds, but I'm lazy, and I don't like to waste space, so I stay with Arch.

---

### Post by ptn107 on 2008-07-08
Ubuntu is definitely the easiest distro to learn on.  I've personally been using Ubuntu 8.04.1 for my home/multimedia boxes.  Another good choice would be Debian* (Ubuntu's parent).  I've been using that on my business/work laptops.  It functions similarly, but with a bit more stuff you can play around with.

*[http://www.debian.org/](http://www.debian.org/)

---

### Post by Frak on 2008-07-08
> **ptn107 said:**
> Ubuntu is definitely the easiest distro to learn on.  I've personally been using Ubuntu 8.04.1 for my home/multimedia boxes.  Another good choice would be Debian* (Ubuntu's derivative).  I've been using that on my business/work laptops.  It functions similarly, but with a bit more stuff you can play around with.

*[http://www.debian.org/](http://www.debian.org/)
You mean, Ubuntu is a derivative of Debian right? (I'm confused)

---

### Post by bodhi.zazen on 2008-07-08
The best way to learn Linux is to use linux.

Pick a distro, it does not matter. Install it, use it on a daily basis. Learn everything about it.

Most of what you learn on any distro applies to all the others, especially bash (the CLI).

Once you know a single distro really good you will find learning a second and a third much faster.

Then +1 for LFS.

---

### Post by Inxsible on 2008-07-08
> **Frak said:**
> :lolflag:

I do like the idea of customizing your builds, but I'm lazy, and I don't like to waste space, so I stay with Arch. I love my Arch with Openbox !

---

### Post by bobnutfield on 2008-07-08
I have not read too much about it in this thread, but I can certainly recomment Slackware as both a good learning tool for linux and one hell of a good distro.  There is no hand holding, but the learning curve is not too steep and once you master it, you will know linux.  It is one of the oldest linuxes out there (1993) and many consider it the purest linux of all distros.  

Just my opinion, but I, like the OP, use many distros and Slackware is hands down the most stable and fastest.

Bob

---

### Post by Frak on 2008-07-08
> **bobnutfield said:**
> I have not read too much about it in this thread, but I can certainly recomment Slackware as both a good learning tool for linux and one hell of a good distro.  There is no hand holding, but the learning curve is not too steep and once you master it, you will know linux.  It is one of the oldest linuxes out there (1993) and many consider it the purest linux of all distros.  

Just my opinion, but I, like the OP, use many distros and Slackware is hands down the most stable and fastest.

Bob
Well, that's only what you consider to be "pure". It's the purest Unix of all the Linux Distributions. Though, Debian could be considered the most "pure" of the LSB (Linux Standard Base) compliant distributions.

---

### Post by Inxsible on 2008-07-08
> **bobnutfield said:**
> I have not read too much about it in this thread, but I can certainly recomment Slackware as both a good learning tool for linux and one hell of a good distro.  There is no hand holding, but the learning curve is not too steep and once you master it, you will know linux.  It is one of the oldest linuxes out there (1993) and many consider it the purest linux of all distros.  

Just my opinion, but I, like the OP, use many distros and Slackware is hands down the most stable and fastest.

Bob
Someday, I plan to get my lazy a$$ to start using Slackware. Eventually ....;)

---


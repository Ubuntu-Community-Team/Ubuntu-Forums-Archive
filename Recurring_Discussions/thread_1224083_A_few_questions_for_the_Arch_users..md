---
title: "A few questions for the Arch users."
date: 2009-07-27
forum: Recurring Discussions
---

### Post by Blittzd on 2009-07-27
Hi everyone. :)

I'll make this short. I've downloaded the Arch Linux .ISO and burned it to a disk, ready for installation. I'm thinking of switching over to Arch completely from Ubuntu Jaunty, as I've heard lots of users praise it for it's simplicity and customization. I'm not a fan of Ubuntu's pre-installed "bloat" (for example, the games package and Open Office :P), and I like to be on the cutting edge of software (which the Ubuntu repos sometimes cannot provide). I'm reasonably experienced with Linux and the terminal. I've just got a few questions for those who use Arch:

Which desktop environment do you prefer to use? I've been using gnome since I discovered Ubuntu, and like the looks of a light window manager like XFCE or Openbox.

Newbie question; is it hard to install and configure 3D acceleration and graphics drivers in Arch? Or is it similar to Ubuntu?

I'm looking forward to trying out a mean, lean and speedy distro!
Any general Arch tips for newbies would also be helpful. I'm posting this on the Ubuntu forums because I'm switching from Ubuntu, so I'll probably get more advice about alternatives to Ubuntu options/methods of configuring or installing.

Thanks, the help is appreciated! :D

---

### Post by earthpigg on 2009-07-27
have you played with it in virtualbox yet?

---

### Post by Icehuck on 2009-07-27
> **Blittzd said:**
> Hi everyone. :)

I'll make this short. I've downloaded the Arch Linux .ISO and burned it to a disk, ready for installation. I'm thinking of switching over to Arch completely from Ubuntu Jaunty, as I've heard lots of users praise it for it's simplicity and customization. I'm not a fan of Ubuntu's pre-installed "bloat" (for example, the games package and Open Office :P), and I like to be on the cutting edge of software (which the Ubuntu repos sometimes cannot provide). I'm reasonably experienced with Linux and the terminal. I've just got a few questions for those who use Arch:

Which desktop environment do you prefer to use? I've been using gnome since I discovered Ubuntu, and like the looks of a light window manager like XFCE or Openbox.

Newbie question; is it hard to install and configure 3D acceleration and graphics drivers in Arch? Or is it similar to Ubuntu?

I'm looking forward to trying out a mean, lean and speedy distro!
Any general Arch tips for newbies would also be helpful. I'm posting this on the Ubuntu forums because I'm switching from Ubuntu, so I'll probably get more advice about alternatives to Ubuntu options/methods of configuring or installing.

Thanks, the help is appreciated! :D

I use Arch 64 bit on my laptop. I use DWM or Musca as my window manager. I find that I don't need a full desktop environment and I'm more efficient without one.

Installing and setting up X.org is not difficult. If you have never done it, make sure you read the directions. If your card is supported you won't have any issues with 3D acceleration. 

Since you're new to Arch. Read the wiki, read the wiki, and then read the wiki. If you have a problem, then read the wiki. 

You may never have compiled from source on Ubuntu, but you may end up doing it on Arch. It gets pretty addicting and doing it the Arch way means you can compile and then install it as a package. 


[Beginners Guide, Read it!]("http://wiki.archlinux.org/index.php/Beginners_Guide")

---

### Post by swoll1980 on 2009-07-27
> **Blittzd said:**
>  I'm not a fan of Ubuntu's pre-installed "bloat" (for example, the games package and Open Office :P), 

```
sudo apt-get remove openoffice.org-base gnome-games
```

In case that doesn't work out for you.

---

### Post by cariboo on 2009-07-27
I installed opera using yaourt the other day, I was amazed how easy it was. THe biggest problem  was that the wiki is wrong about how to install yaourt.

---

### Post by doorknob60 on 2009-07-27
Arch sounds perfect for you! Give Openbox/LXDE a try oo. Also, I find that setting up accelerated drivers much smoother and easier in Arch than in any other distro, I'm not gonna lie, I've had problems in the past with Ubuntu (works fine more recently, but still), but not so much in Arch.

^ What's wrong with the Yaourt wiki entry, looks fine to me...

---

### Post by Icehuck on 2009-07-27
> **cariboo907 said:**
> I installed opera using yaourt the other day, I was amazed how easy it was. THe biggest problem  was that the wiki is wrong about how to install yaourt.

I think the wiki had 3 ways to install it at one point. They all worked though...


> In case that doesn't work out for you.

What about jockey? Or the other miscellaneous crud?

---

### Post by &#32 Greg on 2009-07-27
> **cariboo907 said:**
> I installed opera using yaourt the other day, I was amazed how easy it was. THe biggest problem  was that the wiki is wrong about how to install yaourt.

Doesn't it say to download the tarball, extract it, cd, type makepkg -s, then pacman -U yaourt-something.pkg.tar.gz?

@OP: Personally, I use xmonad. Download a few WMs and try them out.

---

### Post by chris4585 on 2009-07-27
If you still want gnome, you may find out that gnome on arch is not the same as on ubuntu.  You can have the basic gnome DE if you want by just typing

```
pacman -S gnome
```

Read the arch beginners guide it compares the common desktops.  If you have nvidia its as simple as the following:

```
pacman -S nvidia mesa
```

---

### Post by P1umb3r on 2009-07-27
Installing video drivers  for my nvidia 200 series card was as simple as running

```
# pacman -S nvidia
```Then configuring xorg to work with the driver:

```
# nvidia-xconfig
```

---

### Post by Blittzd on 2009-07-27
I haven't tried out Arch yet (not even in Virtualbox). But it looks promising, so I think I'll dive right in. If I screw it up, I could always format the partition and start over. The wiki and beginners guide are pretty impressive. I'll remember to refer to them whenever possible. :D

Also, @ the poster who suggested removing the packages I don't want: It's not as simple as that. I was just using those programs as examples, sorry if I caused any confusion. It's hard to explain- I don't want anything but a package manager installed when I first log in. I know this could be achieved with an Ubuntu minimal install, but synaptic still won't have the most cutting-edge updates (for example, Firefox 3.5).

I think I'll give Openbox a try. And I'm glad to hear GPU driver installation is as easy as in Ubuntu. :)

Thanks for the feedback!

---

### Post by hessiess on 2009-07-27
1) Mixture of Xmonad and DWM (Xmonad breaks suspend to ram)
2) Not difficult, just read the wiki.

---

### Post by Eisenwinter on 2009-07-27
Arch is very easy to install. The installation process is really straight forward. You just need to know your machine a little bit more, and it's no problem.

It's so simple, I was able to install and configure Arch the first time I tried it, without even reading the Wiki.

---

### Post by chris4585 on 2009-07-27
the whole process is easier then it sounds:

1. Install
2. Update, and run rankmirrors to improve pacman
3. Configure: user, xorg, alsa, desktop environment
tada

---

### Post by imlinux on 2009-07-27
my experience with arch is i installed it as directed pretty much easily configured it too. then at the end as i booted it up, i was encounted with shell prompt,so now what? i don't know any command to install window managers like open box or lxde or gnome or xfce,this was like 4 months back.even the huge documentation of arch linux wasn't of any help, as never had habit of reading manuals. so moral of the story is if anyone can tell me how get my sweet window manager as in ubuntu or what packages to install i would be more than happy, just give me list of commands to install windows managers in arch linux......till then i have trim downed my ubuntu with unecessary services and happy sailing with it.....but i do like to try arch linux.

---

### Post by tarps87 on 2009-07-27
I'm using gnome, did use kde for a bit, but after the stability issues I tried various others and there are a lot out there :) Some fun ones are ude and rox although rox is aimd a whole redesign of the Linux file management. Oh and ude really needs a three buttoned mouse.
You may be better off diving straight in as recently there has been an issue with the latest kernel and vbox.

---

### Post by Skripka on 2009-07-27
> **chris4585 said:**
> the whole process is easier then it sounds:

1. Install
2. Update, and run rankmirrors to improve pacman
3. Configure: user, xorg, alsa, desktop environment
tada

4. Odds are some DeviceKit/HAL configuration might be desired for mount permissions


Other than that-it is quite simple and elegant.  It is also far more vanilla, and tries to avoid using patches wherever possible.

---

### Post by Barrucadu on 2009-07-27
> **imlinux said:**
> even the huge documentation of arch linux wasn't of any help, as never had habit of reading manuals.

Well, of course the extensive documentation isn't going to help if you don't read it.

---

### Post by Skripka on 2009-07-27
> **Barrucadu said:**
> Well, of course the extensive documentation isn't going to help if you don't read it.

To intenionally not RTFM in Arch, is rather like going to take a driver's license test without RTFM.  Sure you can do it--but it won't end happily.

---

### Post by decoherence on 2009-07-27
This link is your best friend:

[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

...and PekWM/PyPanel FTW!

---

### Post by .Maleficus. on 2009-07-27
For WMs, I've had great luck with a few.  PekWM with bmpanel was really nice but Dwm is what I use currently.  For a full DE, I use KDEmod, a great, modular version of KDE.

Oh yeah, and read the wiki and Beginner's Guide.  It will simplfy everything and has answers to most of the questions you'll have as a new user.

---

### Post by tarps87 on 2009-07-27
> **imlinux said:**
> my experience with arch is i installed it as directed pretty much easily configured it too. then at the end as i booted it up, i was encounted with shell prompt,so now what? i don't know any command to install window managers like open box or lxde or gnome or xfce,this was like 4 months back.even the huge documentation of arch linux wasn't of any help, as never had habit of reading manuals. so moral of the story is if anyone can tell me how get my sweet window manager as in ubuntu or what packages to install i would be more than happy, just give me list of commands to install windows managers in arch linux......till then i have trim downed my ubuntu with unecessary services and happy sailing with it.....but i do like to try arch linux.

> **Skripka said:**
> To intenionally not RTFM in Arch, is rather like going to take a driver's license test without RTFM.  Sure you can do it--but it won't end happily.

+1

The Ubuntu community is very much a "hold your hand community" in other words you will be walked through each step without needing to know what each command or step does. From my experience the Arch community is very much do it your self, as in here is the documentation read it and then use what you have learnt. This could be just my view as I have not had to ask any questions because all the info is just there.

---

### Post by Skripka on 2009-07-27
> **tarps87 said:**
> +1

The Ubuntu community is very much a "hold your hand community" in other words you will be walked through each step without needing to know what each command or step does. From my experience the Arch community is very much do it your self, as in here is the documentation read it and then use what you have learnt. This could be just my view as I have not had to ask any questions because all the info is just there.

They are two very different support models.  Ubuntu primarily uses forums as the 1st stop for help, and Arch uses a Wiki document.  Each has pluses and minuses.  Personally having one Wiki entry to find and read on a topic through is better than sorting through 50,000 threads on Nvidia GFX drivers.

---

### Post by RiceMonster on 2009-07-27
> **Blittzd said:**
> Which desktop environment do you prefer to use? I've been using gnome since I discovered Ubuntu, and like the looks of a light window manager like XFCE or Openbox.

That's entirely up to you. I reccomend you try out all the window managers that interest you. I've played around with pretty much everything, but in the end Xfce is my favorite. However, others are using KDE, openbox, dwm, ratpoison, fluxbox, etc, etc.

> Newbie question; is it hard to install and configure 3D acceleration and graphics drivers in Arch? Or is it similar to Ubuntu?

Nope. I had an intel card for the longest time, then I bought my desktop with an nVidia 9800 GT and it was litterly just installing it then following one or two steps in the beginners guide.

---

### Post by chucky chuckaluck on 2009-07-27
even i read the documentation for arch. it's *not* the usual tl/dr mess that brags about this or that algorhythm and then doesn't bother with the howto parts.

---

### Post by ngsupb on 2009-07-27
Just installed Arch yesterday. I wanted to make my system faster. Ubuntu worked without any problems, it is just my nature to maximize things. 


I couldn't configure xfce in the way I liked to work in gnome (Thunar != Nautilux). So removed it and installed Gnome again and configured everything in the same way as on Ubuntu and moved my applications data settings into Arch from Ubuntu. 

So my first impression after installation:

1. Faster! really Gnome works faster. Booting is faster. Less memory usage ~150mb after booting to compare like 260mb in Ubuntu. 
2. Easy package management the same as in Ubuntu but through console. Other say it is even better. Not sure why yet :)

3. Awesome wiki!. Must read while installation and if you have any problem read it first. (I didn't read anything when installed Ubuntu).
After installing of Arch I can say I learned a lot about desktop Linux and how the things work :)

4. I loved rc.conf. and I know what start on my pc and what is installed. No bloats.
5. I am on 2.6.30 Oo3 and ext4 now :D


bad things:
1. It is harder to install but not so hard. You will learn a lot though. Just read and do what is advised. It took for me 1 day to configure everything.
2. Had a problem with gnome disk mounter until I found some fix. 
3. If something doesn't work, it isn't a bug, you just haven't installed it yet (module, deamon... ):D Read wiki ....


Except of the time it took to install and configure and figure out things. So far I like it.

---

### Post by SuperSonic4 on 2009-07-27
Automounting: [http://bbs.archlinux.org/viewtopic.php?id=65070](http://bbs.archlinux.org/viewtopic.php?id=65070) - check out post 17 for advice on how to get hal to play your game and mount as user (or anyone in the wheel group)

Personally I am using KDEmod 4.3 and it blows Kubuntu out of the water.

Have you tried out the AUR yet? Thanks to that I've never needed to compile. I installed yaourt by adding [archlinuxfr] to /etc/pacman.conf and then ```
pacman -Sy yaourt
```

I also made an alias for yaourt in .bashrc. 

```
yaourt -Syu --aur
``` is like sudo pacman -Syu [yaourt is run as user] but it updates the AUR too.

If you want to search for a package pass the -Ss flag eg:```
pacman -Ss atanks
```

edit: the more times you reinstall arch the quicker it becomes - that's not to say you need to reinstall but I do so every now and again for the fun of it XD. Also arch is good because you can use DE/WM what you like - the laptop runs a cli!

---

### Post by calrogman on 2009-07-27
> **earthpigg said:**
> have you played with it in virtualbox yet?

Arch doesn't play well with VirtualBox.  Everytime I install it, it goes fine, then it randomly breaks.  Arch does not like being virtualised.

---

### Post by tarps87 on 2009-07-28
> **ngsupb said:**
> ...
1. It is harder to install but not so hard. You will learn a lot though. Just read and do what is advised. It took for me 1 day to configure everything...

You can't have finished then ;) I'm still configuring/ tweaking my install on a AA1 which is at lest two months old now.

> **calrogman said:**
> Arch doesn't play well with VirtualBox.  Everytime I install it, it goes fine, then it randomly breaks.  Arch does not like being virtualised.

There is a bug in the latest kernel that causes virtual box to crash, I haven't see it reported that it effects a 'real' install.
You can revert the kernel version or if it is a fresh install just tell pacman not to update the kernel package.
In /etc/pacman.conf
IgnorePkg = kernel26 kernel26-firmware

---

### Post by handy on 2009-07-28
I'll just add that the Beginners Guide is not something you just have a look at.  Follow it to the letter as best you can as Arch is like no other distro.

There is an official installation guide in the wiki also, for those that require more detail, & most everything involved in the installation should have even more detail elsewhere in the brilliant Arch wiki.

The major problem that I have found with Arch over the last months is that due to Arch's cutting edge nature, it has been really pushing the AMD/ATi Catalyst (proprietary) GPU drivers.  There has been & still is a lot of trouble in this area due to AMD/ATi really not putting the effort in to keep up.  

If you are a potential new Arch user that runs an ATi GPU, have a look in [***_AUR_***]("http://aur.archlinux.org/"), search for catalyst & read the comments, you will see what is going on, also the last couple of pages of this thread are well worth looking at too:

[http://bbs.archlinux.org/viewtopic.php?id=57084](http://bbs.archlinux.org/viewtopic.php?id=57084)

The above two sources will keep you up to date with the best way to deal with the ownership of an ATi GPU & running the latest kernel, x.server & whether you are best off with the open or closed drivers for your ATi GPU.

---

### Post by bodhi.zazen on 2009-07-28
> **Blittzd said:**
> Hi everyone. :)

I'll make this short. I've downloaded the Arch Linux .ISO and burned it to a disk, ready for installation. I'm thinking of switching over to Arch completely from Ubuntu Jaunty, as I've heard lots of users praise it for it's simplicity and customization. I'm not a fan of Ubuntu's pre-installed "bloat" (for example, the games package and Open Office :P),

So use the minimal iso and build up only what you want.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

> and I like to be on the cutting edge of software (which the Ubuntu repos sometimes cannot provide). I'm reasonably experienced with Linux and the terminal.I tend to agree, Ubuntu is not exactly "bleeding edge", but watch out for stability (not that Arch is unstable mind you).

> I've just got a few questions for those who use Arch:

Which desktop environment do you prefer to use? I've been using gnome since I discovered Ubuntu, and like the looks of a light window manager like XFCE or Openbox.Fluxbox, Openbox, or XFCE.

> Newbie question; is it hard to install and configure 3D acceleration and graphics drivers in Arch? Or is it similar to Ubuntu?Installing the nvidia drivers is pretty much the same on all distros.

> I'm looking forward to trying out a mean, lean and speedy distro!
Any general Arch tips for newbies would also be helpful. I'm posting this on the Ubuntu forums because I'm switching from Ubuntu, so I'll probably get more advice about alternatives to Ubuntu options/methods of configuring or installing.

Thanks, the help is appreciated! :D

Best tip for Arch noobs : read, read, read.

---

### Post by Bigtime_Scrub on 2009-07-28
> **Blittzd said:**
> Hi everyone. :)

I'll make this short. I've downloaded the Arch Linux .ISO and burned it to a disk, ready for installation. I'm thinking of switching over to Arch completely from Ubuntu Jaunty, as I've heard lots of users praise it for it's simplicity and customization. I'm not a fan of Ubuntu's pre-installed "bloat" (for example, the games package and Open Office :P), and I like to be on the cutting edge of software (which the Ubuntu repos sometimes cannot provide). I'm reasonably experienced with Linux and the terminal. I've just got a few questions for those who use Arch:

Which desktop environment do you prefer to use? I've been using gnome since I discovered Ubuntu, and like the looks of a light window manager like XFCE or Openbox.

Newbie question; is it hard to install and configure 3D acceleration and graphics drivers in Arch? Or is it similar to Ubuntu?

I'm looking forward to trying out a mean, lean and speedy distro!
Any general Arch tips for newbies would also be helpful. I'm posting this on the Ubuntu forums because I'm switching from Ubuntu, so I'll probably get more advice about alternatives to Ubuntu options/methods of configuring or installing.

Thanks, the help is appreciated! :D

Try Sidux. You get everything you want and you get to keep the fantastic Debian repositories!

---

### Post by handy on 2009-07-29
I may have detected a my repo' is bigger than yours post! :lolflag:

How you build your repo's certainly has an effect on the number of packages in it. :)

---

### Post by handy on 2009-07-30
There is a leaked beta version of Catalyst, in the wild, which is apparently working very well, have a look at the AUR site & search up Catalyst & have a read of the comments & the last few pages of this page in the Arch forums is very educational:

[http://bbs.archlinux.org/viewtopic.php?id=57084](http://bbs.archlinux.org/viewtopic.php?id=57084)

---

### Post by Blittzd on 2009-08-01
Hey guys.

Thanks so much for all the advice & tips! :D
However, now that I've read up about it, a minimal installation of Ubuntu (with a WM & DE of my choice) seems more and more appealing... Perhaps it would be better than diving straight into Arch? I've read over the Arch wiki & beginner's guide briefly, to be honest it looks a bit daunting... 

Maybe I'll just have to get used to the stable (rather than cutting edge) repos in Ubuntu? Decisions decisions...

---

### Post by chris4585 on 2009-08-01
> **Blittzd said:**
> Hey guys.

Thanks so much for all the advice & tips! :D
However, now that I've read up about it, a minimal installation of Ubuntu (with a WM & DE of my choice) seems more and more appealing... Perhaps it would be better than diving straight into Arch? I've read over the Arch wiki & beginner's guide briefly, to be honest it looks a bit daunting... 

Maybe I'll just have to get used to the stable (rather than cutting edge) repos in Ubuntu? Decisions decisions...

Ubuntu minimal is a great option too, a lot easier to setup, but you won't get the same control as Arch does with its simplicity with rc.conf and other text files.  All in all either or is a great choice, but I bet cha Arch would be faster. ;)

---

### Post by &#32 Greg on 2009-08-01
> **Blittzd said:**
> Hey guys.

Thanks so much for all the advice & tips! :D
However, now that I've read up about it, a minimal installation of Ubuntu (with a WM & DE of my choice) seems more and more appealing... Perhaps it would be better than diving straight into Arch? I've read over the Arch wiki & beginner's guide briefly, to be honest it looks a bit daunting... 

Maybe I'll just have to get used to the stable (rather than cutting edge) repos in Ubuntu? Decisions decisions...

Both are good choices, but obviously I prefer Arch (for a number of reasons). I won't try and persuade you either way, but I'd just like to say that diving into Arch is not nearly as difficult as it sounds (unless you need Wireless internet and have an annoying card). 

The process of the installation is actually simple- you'll find that many things, like editing mkinitcpio, are extraneous.

---

### Post by SuperSonic4 on 2009-08-01
> **Blittzd said:**
> Hey guys.

Thanks so much for all the advice & tips! :D
However, now that I've read up about it, a minimal installation of Ubuntu (with a WM & DE of my choice) seems more and more appealing... Perhaps it would be better than diving straight into Arch? I've read over the Arch wiki & beginner's guide briefly, to be honest it looks a bit daunting... 

Maybe I'll just have to get used to the stable (rather than cutting edge) repos in Ubuntu? Decisions decisions...

Both are good choices - however I maintain that pacman is better than apt and even minimal ubuntu is still fixed release

---

### Post by Blittzd on 2009-08-03
Alright, you've convinced me to go for Arch. Extra speed would be great. I'm not a fan of the Ubuntu 6-month upgrade cycle, either. :D

I have a few more newbie questions, though:

- Do I need to install/add SATA/IDE modules or drivers manually to Arch?
- Are network/internet connections easy to set up? (I don't use wireless).
- Do I need to install a package that will let me see USB devices (And will my wireless keyboard & mouse work)?
- Could I read/write to my NTFS partitions?
- Is ALSA installed by default? In other words, is sound hard to get up & working?

Thanks for your advice guys! :)

---

### Post by penguindrive on 2009-08-03
> **Blittzd said:**
> Alright, you've convinced me to go for Arch. Extra speed would be great. I'm not a fan of the Ubuntu 6-month upgrade cycle, either. :D

I have a few more newbie questions, though:

- Do I need to install/add SATA/IDE modules or drivers manually to Arch?
- Are network/internet connections easy to set up? (I don't use wireless).
- Do I need to install a package that will let me see USB devices (And will my wireless keyboard & mouse work)?
- Could I read/write to my NTFS partitions?
- Is ALSA installed by default? In other words, is sound hard to get up & working?

Thanks for your advice guys! :)
1.no
2.yes
3.no
4.not at first
5.Yes, alsa is part of the kernel, as for setting it up, just install alsa-utils.

---

### Post by handy on 2009-08-03
**@Blittzd:** Just follow the Beginners Guide as close as you can, it really isn't hard (especially if you don't have a contrary wireless internet problem).

If you don't have a 2nd computer to use to reference the Beginners Guide, the Official Install Guide is also on the Arch installation disk, see below:


[I] **Documentation**

The official install guide is available on the live system. The official guide covers installation and configuration of the base system only. Change to vc/2 (virtual console #2) with <ALT>+F2 and invoke /usr/bin/less:

# less /arch/arch-linux-official-guide.txt

less will allow you to page through the document. Change back to vc/1 with <ALT>+F1.

Change back to vc/2 if you need to reference the Official Guide at any time.[/I]

---

### Post by Kenda on 2009-09-14
I have just installed Arch as a guest in VirtualBox being hosted on Jaunty. I really like it and it seems marginally faster than Jaunty when opening openoffice etc but there is not much in it at all. 

I do however have one major problem with arch: watching flash video in a web browser is slow at the best of times and quite often freezes the whole system up and I have to poweroff to restart. This even happens when looking at sites like [www.thisislondon.co.uk](www.thisislondon.co.uk) (the Evening Paper).

I did not have this problem running Karmic or Mandriva in VB.

Can any of the Arch Gurus shed any light on this- I have looked on the Arch site but I can't find  anything to fix it?

Apart from  the one issue I have enjoyed tinkering with Arch.

---

### Post by Kenda on 2009-09-14
> **Kenda said:**
> I have just installed Arch as a guest in VirtualBox being hosted on Jaunty. I really like it and it seems marginally faster than Jaunty when opening openoffice etc but there is not much in it at all. 

I do however have one major problem with arch: watching flash video in a web browser is slow at the best of times and quite often freezes the whole system up and I have to poweroff to restart. This even happens when looking at sites like [www.thisislondon.co.uk](www.thisislondon.co.uk) (the Evening Paper).

I did not have this problem running Karmic or Mandriva in VB.

Can any of the Arch Gurus shed any light on this- I have looked on the Arch site but I can't find  anything to fix it?

Apart from  the one issue I have enjoyed tinkering with Arch.

PS. I seemed to have improved things enormously by installing the Catalyst 9.9 driver in the Host (Jaunty) system.

---


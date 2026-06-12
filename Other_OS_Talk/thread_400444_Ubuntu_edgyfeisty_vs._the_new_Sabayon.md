---
title: "Ubuntu edgy/feisty vs. the new Sabayon"
date: 2007-04-03
forum: Other OS Talk
---

### Post by mshale on 2007-04-03
Hi, I'm thinking of trying out the sabayon distro of linux.  What are the major diferences and can i still install all of the software i presently use?  My main attraction is this distro uses beryl by default.  I know that you can install it in ubuntu, beut is is still unstable.  I would jult like to know some pros and cons of using this distro.

Thanks in Advance!

I guess what i'm trying to ask is is it worth the 3.5 gig download file? lol
I'm having some trouble location the mini version.  hey that brings another question up... what is the diff in the mini and dvd versions??

---

### Post by hanzomon4 on 2007-04-03
Sabayon and Ubuntu exist in two different dimensions. 

[list][*]Sabayon is Gentoo based - Ubuntu is Debian based[/list]

The main difference between these two distros is package management. With Gentoo-based Sabayon you use the portage system instead of apt-get/synaptic. The portage system is like the ports system on BSD, basically it downloads and builds apps from source code. Portage also handles dependices. However the system is much more complex the apt-get/synaptic and you will face a learning curve, possibly a very step learning curve. - [Read up on the package management before you install  ]("http://www.sabayonlinux.org/wiki/index.php?title=Portage")

[list][*]Beryl is installed by default and configured automagically[/list]
Yes beryl/aiglx-or-xgl is installed and configured even on the live cd. This is a plus but you should still weigh that against the more complex package management. If you have an nvidia card and you only want to switch to sabayon because of beryl I would say just set it up on ubuntu because it's easy with a nvidia card. 

With all of that said sabayon is a good distro to use and you'll learn a lot by using it. You can find the[ mini-here ]("http://www.sabayonlinux.org/forum/viewtopic.php?t=5631")and an [introduction guide-here ]("http://www.sabayonlinux.org/wiki/index.php?title=Introduction")

---

### Post by mshale on 2007-04-03
yeah, it seems nice, but it might be too steep of a curve for me.  I just got introduced to linux here in the past month:)

---

### Post by igknighted on 2007-04-03
As mentioned above, there is a single CD version which I highly recommend.  It will run a lot faster and there are a few bug fixes from the 3.3 DVD b/c it came out a week later.  If you read the planet sabayon blog on their homepage there is an expirimental binary package installer they are working on, so hopefully by the next release that will be fully available (it is on the CD version in a basic form).  Also, if you really want the DVD, wait a week or so, a new version (3.3.1) is coming out that should fix a lot of the issues people had with 3.3.

---

### Post by hanzomon4 on 2007-04-04
> **igknighted said:**
> As mentioned above, there is a single CD version which I highly recommend.  It will run a lot faster and there are a few bug fixes from the 3.3 DVD b/c it came out a week later.  If you read the planet sabayon blog on their homepage there is an expirimental binary package installer they are working on, so hopefully by the next release that will be fully available (it is on the CD version in a basic form).  Also, if you really want the DVD, wait a week or so, a new version (3.3.1) is coming out that should fix a lot of the issues people had with 3.3.

Good information, thanks. 

I just installed the mini(my 2nd time trying sabayon) and I think I'll try the dvd because for some reason, after emerging some apps missing from the mini, I kill kde. I think it's because I start messing with the package.mask file and other stuff I don't fully get right now.

---

### Post by mips on 2007-04-04
Packages are masked for a reason. Running the DVD will not change that as they will still be masked in portage.

What packages do you want that are masked ?

---

### Post by hanzomon4 on 2007-04-04
Getting things like the suse-style menu, which comes default on the dvd, requires removing the kicker lines from /etc/portage/package.mask.

---

### Post by mips on 2007-04-04
Ok fair enough. Best bet would be to ask on the IRC channel or their forums.

Personally I can't stand the suse menu.

Only package i wanted so far that has been masked has been Frostwire.

---

### Post by hanzomon4 on 2007-04-04
> **mips said:**
> Ok fair enough. Best bet would be to ask on the IRC channel or their forums.

Personally I can't stand the suse menu.

Only package i wanted so far that has been masked has been Frostwire.

Yeah the forums had it listed and the upgrade went smoothly. Actually 3.3 is lot smoother then 3.25 was for me. I'm going to take it real slow so I can learn the portage system, this is also my first kde experience.... so I'm really out of my element but I like it.

---

### Post by mshale on 2007-04-05
So, the only difference between gnome and KDE is the menu style/interface?  Wow, I was thinking that I was going to have to find all new programs and all kinds of stuff :)  So if i switch from ubuntu feisty to sabayon, the biggest thing that will change is how i accuire and manage programs... 

If I'm wrong, please guide me in the right direction!! lol

Thanks again!

---

### Post by darksong on 2007-04-05
I love Sabayon, it looks and feels good - portage is very very easy to learn - check this guide on the sabayon forums:

[http://www.sabayonlinux.org/forum/viewtopic.php?t=1183](http://www.sabayonlinux.org/forum/viewtopic.php?t=1183)

There are alot of apps on Sabayon dvd, you will need 11 gigs for a dvd install.

---

### Post by mshale on 2007-04-05
wow, 11 gigs, that seems like a waste of space. can you chose not to install some if that?  Will all of the programs i used in ubuntu edgy and feisty still work if i switch?

and does anyone know how i can find out what kind of graphics card i have in my laptop, i'm sure its integrated, so it's not going to say invidia on it.  what aobut the drivers for it?  I would like to use beryl if i switch.  what is that desktop konqueror program do?

I know that is a lot of questions... now just think how many i would ask if i was buying a car!!  I just want to be sure that i can work with the distro if i do decide to switch.

Thanks again!

---

### Post by hanzomon4 on 2007-04-05
Well no, kde and gnome have different subsystems and portage is different from apt in that it's all source based. Stick with the dvd and play around with the live version before you install it, goodluck....

It's hard to explain and it's not as hard as I described earlier, so just give it a go..

---

### Post by pirothezero on 2007-04-05
Get used to compiling compiling compiling if you decide to move.

> **mshale said:**
> Will all of the programs i used in ubuntu edgy and feisty still work if i switch?
!

Yes. Not sure if it was mentioned already but the applications having issues running depends on the desktop then the distribution. All programs that run in gnome will run in all distributions of gnome.

---

### Post by hanzomon4 on 2007-04-05
Gnome apps will also run in kde but they depend on gnome-libs(portage handles this automagically). On the dvd you can pick kde or gnome or fluxbox(?) as your DE(Desktop enviroment)

---

### Post by hanzomon4 on 2007-04-05
> **mshale said:**
> wow, 11 gigs, that seems like a waste of space. can you chose not to install some if that?  Will all of the programs i used in ubuntu edgy and feisty still work if i switch?

and does anyone know how i can find out what kind of graphics card i have in my laptop, i'm sure its integrated, so it's not going to say invidia on it.  what aobut the drivers for it?  I would like to use beryl if i switch.  what is that desktop konqueror program do?

I know that is a lot of questions... now just think how many i would ask if i was buying a car!!  I just want to be sure that i can work with the distro if i do decide to switch.

Thanks again!

Yes! you can pick and choose what to install, as for the video card.... If you have an Intel cpu you most likely have Intel graphics, Sabayon will let you know if you can run beryl.

---

### Post by Marc_UK on 2007-04-06
I treid Sabayon, I thought it was bloated with crap and despite their being many Linux OS's similer to Ubuntu, nothing compares to its Add/Remove programs thats something which has kept me with UBuntu.

---

### Post by igknighted on 2007-04-06
> **mshale said:**
> wow, 11 gigs, that seems like a waste of space. can you chose not to install some if that?  Will all of the programs i used in ubuntu edgy and feisty still work if i switch?

and does anyone know how i can find out what kind of graphics card i have in my laptop, i'm sure its integrated, so it's not going to say invidia on it.  what aobut the drivers for it?  I would like to use beryl if i switch.  what is that desktop konqueror program do?

I know that is a lot of questions... now just think how many i would ask if i was buying a car!!  I just want to be sure that i can work with the distro if i do decide to switch.

Thanks again!

11 gigs is a lot.  However, there is a single CD version that is comparable in footprint to Ubuntu.  Unfortunately, there is no option to select what things not to install from the DVD, so you must install it all.  The footprint for the DVD is more like 7-8 GB (still a ton...), as I have put it on a drive with ~9.3 gigs before and had some free space until I synced portage.

For your graphics card, run the command "lspci".  Look for a live that looks like this:
```
01:00.1 Display controller: ATI Technologies Inc R480 [Radeon X800 GTO (PCIE)] (Secondary)
```
Thats your graphics card info

> Get used to compiling compiling compiling if you decide to move.

Well, it is based on Gentoo, so I would hope that one would expect that.  Of course, compiling on gentoo is nearly as easy as installing a .deb package with apt.  "emerge mozilla-firefox" is all you need to install it, it just takes a lot longer (and leaves you with a more customized system for that time) than "apt-get install mozilla-firefox".

There is a new binary installer, I would go out on a limb to say that when it is done it might well be the most advanced binary package tool in existence.  Read this for more info: [http://planet.sabayonlinux.org/](http://planet.sabayonlinux.org/)

> I treid Sabayon, I thought it was bloated with crap and despite their being many Linux OS's similer to Ubuntu, nothing compares to its Add/Remove programs thats something which has kept me with UBuntu.

If a "good gui" for installing programs is a big deal for you, don't use Sabayon or any gentoo based distro.  There is a gui (called Kuroo), but there is very little development on it due to the simplicity of the terminal commands for portage, and the need for detailed feedback if something goes wrong.  Also, most Gentoo folk aren't terribly afraid of the terminal, as the terminal is a necessity when installing Gentoo.

---


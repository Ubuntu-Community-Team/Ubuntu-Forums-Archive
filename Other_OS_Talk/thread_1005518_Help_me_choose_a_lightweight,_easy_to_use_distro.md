---
title: "Help me choose a lightweight, easy to use distro"
date: 2008-12-08
forum: Other OS Talk
---

### Post by muadnu on 2008-12-08
(Sorry to open yet another thread about this...)

My sister got an old laptop a couple of months ago, and I just found out that she doesn't use it because "it is too slow". So I figured it is the perfect time to free here from Windows.

The laptop is a Toshiba Portege (don't know the exact model) with:
- Pentium III, 497 MhZ
- 192 Mb RAM
- 14 Gb hard disk
- A PCMCIA wireless card, D Link G DWA-610 (not sure about the model number)

What she will use it for is mostly browsing, email, and OpenOffice.

What I need is to find a lightweight distro that is very easy to use (she obviously doesn't know anything about Linux and I don't expect here to learn). An option would be Xubuntu (it satisfies the minimum requirements), which would be good because I could help her easily, but I'm afraid it might be much slower than other really light distros. I think Puppy could be a good choice, but I've never used it... Any suggestions?

---

### Post by glotz on 2008-12-08
Here's a few options. [http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by smoker on 2008-12-08
my fav small distro is puppy, but damn small linux may be worth a try also:
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by snowpine on 2008-12-08
Puppy will be the fastest beginner-friendly distro, for sure.
Personally I am very fond of the Ubuntu-based distros, both because the software repositories are huge and because of the friendly forums. Plus Ubuntu is what I learned first. :) Xubuntu is a pretty good choice, if it runs fast enough. My personal favorite is Crunchbang; I find it to be even faster than Xubuntu. It is great for beginners because it already includes the codecs (mp3, flash, etc) that Ubuntu newbies sometimes have trouble with. :) There is a new Crunchbang Lite 8.10 that's supposed to be even faster, but it is still in the early stages of testing...

---

### Post by muadnu on 2008-12-08
Thanks for the replies...

I also want to give DSL a try, but it somehow seems to me as less beginner-friendly (but I actually don't really know). About CrunchBang, I had never even heard of it before, but it really looks interesting. I'm downloading it now to try it in VirtualBox. By the way, snowpine, do you know what's the difference between standard and lite versions? Is there any, apart from the number of packages included?

---

### Post by fistfullofroses on 2008-12-08
Try GoboLinux.
It uses the runit init system, which is extremely fast.
Also, there are not many services loaded by default,
which also increases response time. With specs you listed
you ought to be alright with nearly any distro that doesn't
use compiz/beryl/kde4/gnome.

---

### Post by Hallvor on 2008-12-08
TinyMe. Very light and very n00b friendly.

---

### Post by kerry_s on 2008-12-08
if you go custom, you can set it up exactly how you want.
use a light wm, pcmanfm, leafpad, iceweasel/firefox, etc...

i use jwm for my window manager, pcmanfm can also do icons on the desktop, just copy the launcher from /usr/share/applications to the desktop. i don't use desktop icons, but it only takes seconds to copy and paste the launchers, so it would look something like this.

---

### Post by muadnu on 2008-12-08
Custom sounds like a good and fun way to go. But the problem is that I live really far from my sister (different countries) which makes me helping her a little difficult, and thus I'd prefer to go for something more standard... I'm trying CrunchBang now and it looks solid, but I still have the guess that something like Puppy or DSL will be faster. I'll have to try them with the laptop in hand... Thanks for all the suggestions!

---

### Post by cardinals_fan on 2008-12-08
SliTaz would be a good choice.  You could also consider Debian Stable.

---

### Post by kpkeerthi on 2008-12-09
Yeah. Go with Debian Stable. Put openbox on top it.

---

### Post by spcwingo on 2008-12-09
+1 for Puppy.  I have run Puppy on an old Portege from the live CD...it does pretty good even from the CD!  If you want fast and pretty look into Macpup:

[http://macpup.org/]("http://macpup.org/")

Macpup has everything that Puppy has plus Icewm, wbar, and a pretty Mac theme.  I'm running it on an ancient Compaq Armada 1592DMT with a super fast Pentium @ 233Mhz and a whopping 98MB ram.  I have it on another franken-comp that I have pieced together with a Pentium II @ 300Mhz and 384MB ram.  On that one it's very responsive and just as fast as my Pentium III @ 1Ghz with 1GB ram running Ubuntu Hardy.

---

### Post by mikjp on 2008-12-09
Vector Linux might be lightweight enough.

---

### Post by muadnu on 2008-12-09
> **spcwingo said:**
> +1 for Puppy.  I have run Puppy on an old Portege from the live CD...it does pretty good even from the CD!  If you want fast and pretty look into Macpup...

Macpup looks nice. Which is good, because the nicer it looks, the more probable my sister's gonna keep it. So I think I'll definitely give it a try (I might need more hard disk to put all these distros in VirtualBox!)

---

### Post by ugm6hr on 2008-12-09
Puppy is excellent (I've just given the new 4. version a try).

However, it always runs as root, so is designed to be installed "frugally" rather than on HD for security reasons.  I also find the ROX single-click function confuses a lot of new users, and means it is easy to accidentally move things around on the desktop.  Newbie friendly: yes, but my mum couldn't cope with it.

I have also recently tried Austrumi.  It looks great (FVWM with pseudo-transparency).  Unfortunately, while you can boot it to English, it doesn't change the keyboard to US automatically (and has no UK/GB option at all).

If she needs OO.org (rather than Gnome Office), you might want to check whether it is possible to get OO3 for any of the light distros.  I suspect a Debian / Ubuntu base may prove a better fit if it really is necessary.  Or perhaps Arch (I haven't tried it, but I gather it's good); it has an i686 version, which should be OK for a P3 (I think).

The other thing is wifi. I believe the DWA-610 is an RT chipset, so should be OK.  However, connecting with wifi is easy with Puppy, not so easy DSL, and there are plenty of GUI options for Ubuntu etc.

Not an easy choice...

---

### Post by muadnu on 2008-12-09
I just installed Puppy in VirtualBox and it's blazing fast. But I think she'll definitely need to use OO.org, so I'll begin by trying to get it for Puppy tonight.

If not, some light version of Ubuntu is tempting. I'm trying CrunchBang and it looks good and fast, but I'll have to try it with the laptop in hand.

---

### Post by spcwingo on 2008-12-09
If you decide on Puppy and OpenOffice is a must, check out these links:

[http://www.murga-linux.com/puppy/viewtopic.php?t=31985](http://www.murga-linux.com/puppy/viewtopic.php?t=31985)
[http://www.murga-linux.com/puppy/viewtopic.php?t=32000](http://www.murga-linux.com/puppy/viewtopic.php?t=32000)
[http://www.puppylinux.org/wiki/applications/pre-installed/openoffice](http://www.puppylinux.org/wiki/applications/pre-installed/openoffice)

---

### Post by ugm6hr on 2008-12-09
I've been toying with various WMs in the recent past to look for lightweight options.

However, adding stuff on top of the standard Gnome setup, merely offers all the usual Gnome GUI controls, thereby making it difficult to assess what the lighter WMs offer.

So I've started experimenting in a VM (Virtualbox) too.

Figured I may as well keep a record of what I'm doing: [http://ubuntu-lxde.wikidot.com/](http://ubuntu-lxde.wikidot.com/)

Having done this, I would recommend a custom Ubuntu + LXDE.  It is a lot easier than it sounds, and means she will be using a distro you are already familiar with for support.  It also has precompiled .debs for gitso ([http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)), so provided her wifi works, she should be able to ring you, click a button, and you could remote into her desktop.

I think LXDE is also slightly less confusing for former Windows users than Openbox alone (or JWM/ROX).  In my 128MB RAM VM, it appears to use 50-76MB as a baseline.

---

### Post by mikjp on 2008-12-09
What about Zenwalk?

---

### Post by cardinals_fan on 2008-12-09
> **mikjp said:**
> What about Zenwalk?
Zenwalk is nice, but not that light anymore.  A Zenwalk Core install + X + *box might work though...

---

### Post by smartboyathome on 2008-12-10
> **cardinals_fan said:**
> Zenwalk is nice, but not that light anymore.  A Zenwalk Core install + X + *box might work though...

But then, user friendliness is a must. I would go with Puppy. I use it on my 8 year old laptop with its SMC 10/100 PCMIA ethernet card, since it is so light and painless on it (its got 1 128mb PC100 ram stick which has gone corrupt and instead is just over 100mbs). I am on it right now in fact, it is perfect for web browsing, hasn't gotten past 60MBs ram. If you remaster puppy with the apps your sister would need and the apps she wouldn't uninstalled, then send it to her, it should be easy enough for her to use. I think you could even make a tool to set up users and such after a full hard drive install, so it can  be run securely.

---

### Post by mangoes on 2008-12-10
I have an old inspiron with similar specs as yours (pIII, 192mb ram, dlink wireless card)  and I've run in it:
- puppy
- dsl
- xubuntu 7.10
- crunchbang 8.04 (ubuntu with openbox)
- vector linux standard gold 5.9
- vector linux lite 5.9

Puppy and dsl were run as live distro so maybe they dont count. The other four were installed. These four all had wireless working out of the box. On speed (with these particular specs), Xubuntu is by far the slowest. Vector linux lite is impressively fast (I'm writing this from it now). VL standard and crunchbang are also very fast. 

Crunchbang struggled a bit as a live distro in this laptop but once installed it's breezy (although the graphical installer almost didnt make it...)I like the simple,glossy black look of crunchbang, but maybe your sister won't. 

One thing I don't like about vector is that slapt-get is not as extensive and easy to use as apt-get (which you get in crunchbang).  But for your purpose it maybe adequate. I currently have a full openoffice  running in VL light.

Hope that helps. Why dont you give VL and crunchbang a try. All very easy to install.
edit:
sound works with xubuntu and crunchbang. havent worked out sounds in VL

---

### Post by snowpine on 2008-12-10
Hi Mangoes, a couple of things:
First, there is an alternate install method of Crunchbang that you can use if your computer won't install from the live cd. You install a minimal command line system from the Ubuntu mini or alternate CD, then run a few terminal commands to install Crunchbang on top: [http://crunchbanglinux.org/forums/post/1601/](http://crunchbanglinux.org/forums/post/1601/)

Second, I've been using the beta version of Crunchbang Lite 8.10 for a couple of days on a few different computers. So far I can say it is much faster than Crunchbang 8.04 on the same hardware. I'm still not sold on the Kazehakase browser though; it is light but kind of weird. :) Easy enough to install a different browser. 

Vector Lite sounds very cool, I will have to check it out one of these days. Thanks for the recommendation!

---

### Post by muadnu on 2008-12-10
> **ugm6hr said:**
> 
...

Having done this, I would recommend a custom Ubuntu + LXDE.  It is a lot easier than it sounds, and means she will be using a distro you are already familiar with for support.  It also has precompiled .debs for gitso ([http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)), so provided her wifi works, she should be able to ring you, click a button, and you could remote into her desktop.

I think LXDE is also slightly less confusing for former Windows users than Openbox alone (or JWM/ROX).  In my 128MB RAM VM, it appears to use 50-76MB as a baseline.

I actually have never tried LXDE, but I'll give it a try in a VM using your guidelines. In any case, I'll be with her in a couple of weeks, so I'll be able to install it myself.

There are really lots of options! I'll try to use (at least part of) my weekend to try some. Maybe a good question now is, what do you think is the easiest WM for a Windows user with little hope of learning a lot about Linux? ugm6hr thinks LXDE is a good choice, any other opinions?

---

### Post by spcwingo on 2008-12-10
That would be LookXP, of course:

[LXP sourceforge page]("http://lxp.sourceforge.net/")

---

### Post by muadnu on 2008-12-10
> **spcwingo said:**
> That would be LookXP, of course:

[LXP sourceforge page]("http://lxp.sourceforge.net/")
Wow... But that might be a little too much (not for her, but definitely for me).

---

### Post by ugm6hr on 2008-12-10
> **Hallvor said:**
> TinyMe. Very light and very n00b friendly.

In case you haven't tried this... It's also worth having a look.

It's basically PCLinuxOS + a heavily modded LXDE.  It does include some of the heavier System apps (like Synaptic etc) too.  Main benefit is the very slick user interace - if your sister likes it, it may be a good choice.

Although I still think going with an Ubuntu (or perhaps Debian) based system is best if you are going to be remotely helping her with potential future problems, if that's what you are most comfortable with.

---

### Post by timzak on 2008-12-10
I have a 650Mhz PIII laptop that comes with Windows 2000 Pro.  I've tried Puppy, Xubuntu, Ubuntu, and Debian on it.  Puppy was hands-down fastest, especially for web browsing.  It was the only one that played YouTube videos fairly smoothly.  Of the rest, Win2k was fastest feeling followed by Debian.  Surprisingly, Ubuntu felt no slower than Xubuntu (I'd stripped it down to reduce memory usage).

---

### Post by snowpine on 2008-12-10
> **timzak said:**
> Surprisingly, Ubuntu felt no slower than Xubuntu (I'd stripped it down to reduce memory usage).

Not surprising... Xubuntu was a good idea, but they added too much to it in an attempt to imitate Ubuntu. In my opinion. If you want to check out a really fast Xfce distro, give Sidux Xfce Lite a try! Despite being on the "unstable" side of things, it has really incredible backwards hardware recognition for old PCs.

---

### Post by muadnu on 2008-12-10
> **ugm6hr said:**
> 
Having done this, I would recommend a custom Ubuntu + LXDE.  It is a lot easier than it sounds, and means she will be using a distro you are already familiar with for support.  It also has precompiled .debs for gitso ([http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)), so provided her wifi works, she should be able to ring you, click a button, and you could remote into her desktop.

I just tried this in a VM, although using Xubuntu 8.10. Everything went ok until I logged in: there was no terminal (the terminal emulator was not installed). I logged off and logged in a terminal, but I had not network, thus couldn't install anything... I might try it again, though maybe I'll start with something else like CrunchBang or Ubuntulite.

---

### Post by snowpine on 2008-12-10
> **muadnu said:**
> I just tried this in a VM, although using Xubuntu 8.10. Everything went ok until I logged in: there was no terminal (the terminal emulator was not installed). I logged off and logged in a terminal, but I had not network, thus couldn't install anything... I might try it again, though maybe I'll start with something else like CrunchBang or Ubuntulite.

Hi Muadnu, LXDE doesn't install a terminal by default, so you can either apt-get install lxterminal, or you can tell it to use an existing terminal like xterm or xfce4-terminal as the default terminal. To be honest with you, I forgot exactly how to do this, but I remember it is really easy to set the default terminal application... maybe one of the other LXDE experts can chime in?

---

### Post by muadnu on 2008-12-10
snowpine, the problem is precisely that not even xterm is there... And not being able to get the network working, I cannot install it easily through apt-get.

---

### Post by snowpine on 2008-12-10
> **muadnu said:**
> snowpine, the problem is precisely that not even xterm is there... And not being able to get the network working, I cannot install it easily through apt-get.

Aren't you starting from Xubuntu? Xubuntu includes a terminal...

---

### Post by muadnu on 2008-12-10
No, I also removed Xubuntu, which I guess might be the problem now that I think about it (if you look at the link provided by ugm6hr, it points to another place saying how to get rid of Gnome and KDE, and the instructions include a command to get rid of remnants of Xubuntu, which maybe I wasn't supposed to execute).

---

### Post by cardinals_fan on 2008-12-10
> **smartboyathome said:**
> But then, user friendliness is a must. I would go with Puppy. I use it on my 8 year old laptop with its SMC 10/100 PCMIA ethernet card, since it is so light and painless on it (its got 1 128mb PC100 ram stick which has gone corrupt and instead is just over 100mbs). I am on it right now in fact, it is perfect for web browsing, hasn't gotten past 60MBs ram. If you remaster puppy with the apps your sister would need and the apps she wouldn't uninstalled, then send it to her, it should be easy enough for her to use. I think you could even make a tool to set up users and such after a full hard drive install, so it can  be run securely.
An easy installation is **not** a must, as I assume muadnu will handle installing it.  It just needs to be stable (hence my recommendation of Debian stable).

---

### Post by ugm6hr on 2008-12-11
> **muadnu said:**
> snowpine, the problem is precisely that not even xterm is there... And not being able to get the network working, I cannot install it easily through apt-get.

Sorry about that. 

I typed up the blog after installing, and thought I'd remembered everything.  It's still a work in progress.  I was planning to start again from the beginning once I had finished.

It's still a work in progress, but I have now edited it to advise installation of lxterminal.  I had remembered it being a dependency, but it obviously isn't.

You should still be able to access a Terminal with Ctrl+Alt+F1.  Although the lack of networking might be a problem.

Perhaps try removing slim, and rebooting into a Terminal.  Hopefully, networking will default back on again.  Then you should be able to use apt-get again.

---

### Post by snowpine on 2008-12-11
It is strange because in Debian Lenny, LXDE *does* depend on lxterminal: [http://packages.debian.org/lenny/x11/lxde](http://packages.debian.org/lenny/x11/lxde)

---

### Post by muadnu on 2008-12-11
> **ugm6hr said:**
> 
You should still be able to access a Terminal with Ctrl+Alt+F1.  Although the lack of networking might be a problem.

Perhaps try removing slim, and rebooting into a Terminal.  Hopefully, networking will default back on again.  Then you should be able to use apt-get again.

Thanks... Tried this, but no network. I'll try reinstalling and see how it goes.

---

### Post by Diabolis on 2008-12-11
Instead of a light distro I would give here a light Ubuntu, so she can take advantage of the repositories and the forums. Install Ubuntu and get rid of the heavy stuff like the tracker tool, compiz, gnome. And install fluxbox, thats what DSL uses.

---

### Post by ugm6hr on 2008-12-11
> **muadnu said:**
> Thanks... Tried this, but no network. I'll try reinstalling and see how it goes.

If you are using Xubunutu 8.10 as a base, those commands to remove XFCE are also slightly different: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Consider installing LXDE first (I have edited the install command to include all LXDE components, in case dependencies are different), and log into LXDE with GDM before removing XFCE and GDM.

---

### Post by gjoellee on 2008-12-11
I guess your computer is screaming for Arch Linux or TinyMe!

---

### Post by muadnu on 2008-12-11
> **ugm6hr said:**
> If you are using Xubunutu 8.10 as a base, those commands to remove XFCE are also slightly different: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)


Thanks, though that was not the problem, I had realized that...

> **ugm6hr said:**
> Consider installing LXDE first (I have edited the install command to include all LXDE components, in case dependencies are different), and log into LXDE with GDM before removing XFCE and GDM.

I reinstalled with your new install command (though not following your last piece of advice here). Now I do have lxterminal, but I still have no network. I don't know if this is due to having used Xubuntu 8.10 or maybe because what's left of the Xubuntu installation is not recognizing the VirtualBox ethernet driver. Anyway, I'm now installing U-Lite ([http://u-lite.org]("http://www.u-lite.org")), which is basically a script that takes a minimal installation of Ubuntu (Hardy in this case) and puts LXDE + extra software on top. I'll see how this goes...

---

### Post by smartboyathome on 2008-12-11
> **Diabolis said:**
> Instead of a light distro I would give here a light Ubuntu, so she can take advantage of the repositories and the forums. Install Ubuntu and get rid of the heavy stuff like the tracker tool, compiz, gnome. And install fluxbox, thats what DSL uses.

Actually, I thought that DSL uses JWM starting with DSL 4. :confused:

---

### Post by ugm6hr on 2008-12-11
> **smartboyathome said:**
> Actually, I thought that DSL uses JWM starting with DSL 4. :confused:

As default - yes it does start with JWM.  I think it still has Fluxbox on the CD though (I never use Flux - not a big fan).

EDIT: My wiki has now been re-edited, and tested again to ensure there are no hidden problems.  Feel free to try again: [http://ubuntu-lxde.wikidot.com/](http://ubuntu-lxde.wikidot.com/)

---


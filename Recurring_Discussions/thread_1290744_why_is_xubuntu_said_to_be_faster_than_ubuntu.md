---
title: "why is xubuntu said to be faster than ubuntu?"
date: 2009-10-13
forum: Recurring Discussions
---

### Post by Balsaq Fabrizio on 2009-10-13
:guitar::-({|=i have had ubuntu for a couple weeks now and really like it. it runs good on an 11 year old computer. i can't help but read all the posts and read all the text in the chats about how xubuntu is faster. many people have asked the question...why is xubuntu faster than ubuntu? 

i have read many of the answers yet not one makes any sence too me. it took me many many hours to get ubuntu installed with all the updates so i am not in a rush to  switch to xubuntu unless i understand-for sure: (1) why is xubuntu is faster.....and....(2) is it something i will actually notice when using the computer. 

if i don't understand and if it doesn't make sence, i prolly will not switch due to the nice clean install i did on the ubuntu. i must admit ubuntu is slow but still i can't complain because it works and the computer is old. please comment if you can, i would really appreciate it. thank you.

---

### Post by beastrace91 on 2009-10-13
Xbuntu runs on "xfce" desktop environment which is "light weight" compared to the standard Gnome desktop. Personally I feel it looks rather crude and lacks some features. But it does run a bit faster than standard Gnome.

Also if you are interested in just trying it run the following in terminal: ```
sudo apt-get install xbuntu-desktop
``` And it will download and install everything contained in the Xbuntu desktop (then you can choose between the two at the login Window)

~Jeff

---

### Post by hockeytux on 2009-10-13
Its faster mainly because the desktop environment is a bit lighter. Xubuntu uses Xfce while Ubuntu uses Gnome.

To be honest its actually not that much faster. Really it may be better to try Ubuntu Minmal + LXDE as desktop environment. That made a real difference in performance for me on my old comp.

---

### Post by xuCGC002 on 2009-10-13
> **beastrace91 said:**
> 
Also if you are interested in just trying it run the following in terminal: ```
sudo apt-get install xubuntu-desktop
```

~Jeff

Fixed.

---

### Post by PhoHammer on 2009-10-13
I'm not sure about an older rig, but anything considered half-way up-to-date (i.e. my 
laptop with a dual-core CPU and 2 GB of RAM) will see no difference between Xubuntu and 
Ubuntu. Trust me, I have used both extensively.

---

### Post by joebodo on 2009-10-13
Xubuntu does not seem to be any lighter than Ubuntu according to this article: [http://www.linux-mag.com/cache/7520/1.html]("http://www.linux-mag.com/cache/7520/1.html")

---

### Post by benj1 on 2009-10-13
xubuntu is *supposedly* faster because it uses the xfce desktop which is lighter than gnome (uses less memory etc) unfortunately theyve bogged it down with loads of stuff so it isn't actually lighter or faster

@phohammer you couldn't notice a difference witha 2gb dual core setup, i couldn't see a difference on my 192mb 333mhz 

if you want something fast try crunchbang, wait around for lubuntu (and hope they dont weigh that down) or go non ubuntu with something like puppy

---

### Post by hockeytux on 2009-10-13
> if you want something fast try crunchbang, wait around for lubuntu (and hope they dont weigh that down) or go non ubuntu with something like puppy

+1 for Crunchbang also which is a good alternative to Lubuntu (or use another ready-made Ubuntu LXDE distro like Masonux which is really good).

---

### Post by anonymous_user on 2009-10-13
Xubuntu isn't really faster (see sig) :D

But if you install minimal Ubuntu + Xfce it would be faster than Ubuntu.

---

### Post by mkendall on 2009-10-13
For my usage, Xubuntu is faster because it uses Thunar instead of Nautilus for the file manager.

---

### Post by Algus on 2009-10-13
I was going to come in and say something about Fluxbuntu but after checking out some info I see that there hasn't been a released version in a couple years.   Still, they seem to be working on it.  It might be worth checking out if you're looking into a more lightweight version of Ubuntu.  

I was kind of let down by Xubuntu, I know some folks who are really into Xfce but the cuts it made didn't really seem like a fair trade for the (nonexistant) performance change.  

I wonder if someone's put together a custom spin with a barebones Xubuntu.  That might actually be cool to check out.  

I'm obsessed with Firefox and my bajillions of add-ons though so, unfortunately, I don't think a truly lightweight system and program suite will ever work for me.  (good thing my comp is new enough that it's a nonissue!)

---

### Post by Warpnow on 2009-10-13
Xfce *is* faster than Gnome, but the DE is such a small part of resource usage when both distributions have so many things running you can't tell the difference.

XFCE's compositor is much more lightweight than compiz, though. Much.

Thunar is also lightyears faster than nautilus.

---

### Post by benj1 on 2009-10-13
> **anonymous_user said:**
> Xubuntu isn't really faster (see sig) :D

But if you install minimal Ubuntu + Xfce it would be faster than Ubuntu.

judging from your avatar shouldn't you be recommending crunchbang :)

---

### Post by Jerry N on 2009-10-13
I have never seen any speed improvement with Xubuntu but I have been playing with a server install (9.04) with GDM and IceWm. (See Pschocats.net) This seems pretty fast but I keep coming back to Nautilus as the file manager because of its features.  

Jerry

---

### Post by Lukios on 2009-10-14
Im guessing that you are fairly new to ubuntu and linux in general, so I suggest that you stick with gnome for now if it works just fine for you. Xubuntu really is a beast and really is not that much faster then gnome. If you do have a little experience or would like to experiment, I would suggest either installing from mini.iso and installing lxde or installing gnome-core and/or replace nautilus and metacity with pcmanfm and openbox respectively. You can also replace nautilus and metacity on your current system and easily revert back if you decide to.

---

### Post by Grifulkin on 2009-10-14
Yeah you can also check out #!Crunchbang once you get to the point where you know mostly what you are doing, installed it last week and love it, also I've been using Ubuntu since for over a year now I think I can't really remember exactly.  I have also sat through an entire install of Arch so I feel like an accomplished Linuxer.

---

### Post by iKonaK on 2009-10-14
Actually, from my experience, the RAM usage is actually bigger in xubuntu(xfce) then in ubuntu(gnome) with no effects, but I had the feeling that xubuntu is faster because it loads applications faster.

---

### Post by Warpnow on 2009-10-14
> **Jerry N said:**
> I have never seen any speed improvement with Xubuntu but I have been playing with a server install (9.04) with GDM and IceWm. (See Pschocats.net) This seems pretty fast but I keep coming back to Nautilus as the file manager because of its features.  

Jerry

Its advisable to do a command line install with an alternate disk rather than use a server install. Just as lightweight, really.

> **iKonaK said:**
> Actually, from my experience, the RAM usage is actually bigger in xubuntu(xfce) then in ubuntu(gnome) with no effects, but I had the feeling that xubuntu is faster because it loads applications faster.

In all fairness, gnome nowadays (as it is in ubuntu) doesn't look or work very well without effects. Add in effects and that is where XFCE is more lightweight.

---

### Post by Grifulkin on 2009-10-14
I honestly don't see the big deal over XFCE or for that matter any of the DE that people may use, in my opinion the one that the looks the best is KDE.  Also I think it looks the best but then again I don't really like Kubuntu because I don't think KDE and Ubuntu mix as well as it does with other Distro's that use it as its main DE.  Just saying.

---

### Post by Warpnow on 2009-10-14
> **Grifulkin said:**
> I honestly don't see the big deal over XFCE or for that matter any of the DE that people may use, in my opinion the one that the looks the best is KDE.  Also I think it looks the best but then again I don't really like Kubuntu because I don't think KDE and Ubuntu mix as well as it does with other Distro's that use it as its main DE.  Just saying.

Yeah, obviously functionality on 5-10+ year old hardware and not having to deal with instability issues is no big deal.

---

### Post by Grifulkin on 2009-10-14
> **Warpnow said:**
> Yeah, obviously functionality on 5-10+ year old hardware and not having to deal with instability issues is no big deal.

Yeah I guess but that isn't anything a Window Manager couldn't handle and not only that but give it more speed than XFCE.  I just don't personally see, why people really like it.  Personally I'm starting to not like the whole idea of a Desktop Environment and am really starting the like the idea of a Window Manager.

---

### Post by NightwishFan on 2009-10-14
Really, Xubuntu is just a usable XFCE with an Ubuntu base. I think the project should really strive toward just keeping the XFCE feel. Some of the Xubuntu apps are more suited to older PCs such as Mousepad, but they still have gstreamer and Firefox. Conserving a few MB of RAM can mean a good bit of extra performance on an old machine. A 'lighter' Ubuntu should actually be it's own project and not a remix. For example, they could work on and distribute a more stripped down kernel and perhaps use more lightweight defaults.

I have had many issues with Xubuntu, mostly due to Abiword. For example I installed Xubuntu on an older PC for my friend. They use the machine to do artwork and write documents, something Win2000 is slow and useless for. They love GIMP and do great work with it. However Abiword does not manage memory well. It loads a document into RAM, and slows their machine (which actually has about 500mb RAM) to a crawl. Abiword is actually less reactive than Open Office when it is in use. (On their 300+ page .doc files). Standard Ubuntu works fine.

---

### Post by K.Mandla on 2009-10-15
There's a little bit of history here though. A few years ago, when Xubuntu started out into the world, the developers promised to stick to XFCE plus GTK2 applications whenever possible, and in truth, it was a quick, snappy alternative to normal Ubuntu.

Over the years it gained a reputation for being a better alternative for pre-Pentium 4 machines, but in the same time it gained a lot more users with faster machines that preferred XFCE. 

As a result, much of the development of Xubuntu moved toward a "Gnome-plus-XFCE" idea, with many of the same applications between the two, and only the XFCE rendition of the same desktop as the major difference. And as a result of that, a lot of the old, outdated hardware that it was originally intended for became underpowered to run it.

Nowadays there are still occasionally people who recommend it as a "solution" for an "old" machine, but their definition of old certainly doesn't include 700Mhz Celerons. 

Lubuntu seems to be the next big answer for out-of-date hardware, and anybody bouncing from Ubuntu to Xubuntu in search of a speed bump might do better to skip Xubuntu altogether, and go straight to Lubuntu. 

Sorry for the history lesson. It's something I've been trying to correct for a looong time. ... 

P.S.: [http://kmandla.wordpress.com/2009/01/03/fair-but-honest-xubuntu-810/](http://kmandla.wordpress.com/2009/01/03/fair-but-honest-xubuntu-810/)

---

### Post by perspectoff on 2010-05-25
> **NightwishFan said:**
> Really, Xubuntu is just a usable XFCE with an Ubuntu base. I think the project should really strive toward just keeping the XFCE feel. Some of the Xubuntu apps are more suited to older PCs such as Mousepad, but they still have gstreamer and Firefox. Conserving a few MB of RAM can mean a good bit of extra performance on an old machine. A 'lighter' Ubuntu should actually be it's own project and not a remix. For example, they could work on and distribute a more stripped down kernel and perhaps use more lightweight defaults.

I have had many issues with Xubuntu, mostly due to Abiword. For example I installed Xubuntu on an older PC for my friend. They use the machine to do artwork and write documents, something Win2000 is slow and useless for. They love GIMP and do great work with it. However Abiword does not manage memory well. It loads a document into RAM, and slows their machine (which actually has about 500mb RAM) to a crawl. Abiword is actually less reactive than Open Office when it is in use. (On their 300+ page .doc files). Standard Ubuntu works fine.

Well, there is Puppy Linux, which is one of the greatest lightweight distros ever made.

Recently they decided to be an Ubuntu Remix, instead of continuing to be a completely independent distro.

There are two packaging repository systems that are tough to ignore -- Debian (which Ubuntu/Kubuntu also use) and Red Hat (which Fedora and CentOS also use).

It is extremely difficult to recreate the juggernaut that these two package and repository systems represent, and keeping an independent packaging system going is very tough work (which is the reason, I think, that Puppy switched).

So while it's nice to say "create a new distro from scratch", the folks who have done that are moving their systems the way of either Debian/Ubuntu/Kubuntu or Redhat/Fedora/CentOS.

---


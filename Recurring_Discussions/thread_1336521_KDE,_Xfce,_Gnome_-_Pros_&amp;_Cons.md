---
title: "KDE, Xfce, Gnome - Pros &amp; Cons?"
date: 2009-11-24
forum: Recurring Discussions
---

### Post by booksnmore4you on 2009-11-24
Alright, I've installed each of these desktop enviros on my Ubuntu machine, **KDE, Xfce, Gnome,** and am in the process of giving each a good going over.  

If you've tried more than Gnome, why did you afterward stay with Gnome, or why did you afterward switch to either KDE or Xfce?

And if you were a college freshman just starting out with Linux, which for this population of users would you think is the superior default desktop enviro ?


-------------------

---

### Post by Amix on 2009-11-24
I think KDE is more similar to Windows style so it may be the easiest for Linux newcomers,
As i think; thanks

---

### Post by gradinaruvasile on 2009-11-24
Gnome - Packed with features, easily customizable, OOTB support (well a few clicks away) for Samba/SFTP/NFS/etc, many apps by default. Also easy to use. The GTK toolkit has many programs that use it for basis and even QT apps mimic quite right its looks thus has a more unified looking interface. I think its a natural choice for default DE.
Oh, and it has Compiz by default...
On the dark side the Ubuntu devs have come to the conclusion that PulseAudio is mature enough to be at the core of sound processing. It turned out that lots and lots of users had audio problems - thats inexcusable on the default DE for the most popular(?) linux distro.

Xfce - I am a fan  of this one. Its a more minimalistic approach, but has applications for basically everything Gnome has. A plus is that these applications are not tied to the DE/each other so they can be removed without problems unlike Gnome where some tings like evolution-server cannot be removed.
It is far more snappier than Gnome (essentially  a light-gnome), and naturally has fewer features OOTB. I would recommend only to those who know Ubuntu's workings and such because some stuff isnt as straightforward as in Gnome. 
But it can be expanded as necessary. One minus is the menu handling (Karmic) that is halfway implemented (basically you have to edit .xml s to accomplish this, never did it i created 2 launchers to contain my 3 party apps). The menu structure differs a bit from Gnome's, some applications icons will not be visible in the menu.
Very good on older hardware/for people who dont want wobbly windows/fishes in transparent cubes/mounting everything(almost) via gigolo  but speed and simplicity. It is also based on Gtk+ as Gnome so all Gtk+ apps will run under it without problems. No default PulseAudio here. Clean and simple are 2 words that describe it.
One problem though: some packages need to be installed (gnome-mount and something else) to make Gigolo (the disk mounter) actually work.

KDE - i didnt try it extensively, but looks very much like vista/windows7's interface. It is based on the Qt toolkit - unfortunately as far as i could tell the interface of the programs is kinda messy - lots of Qt3 (that have their own windows-bare looking interface) apps in the repos that look different from the Qt4 apps (that can "steal" the widgets from the system theme making them look more alike). The Gtk+ apps again have their own looks (i am not sure, might be some compatibility theme with those too). All in all its shiny-flashy at the core, but once you install some apps it becomes riddled with inconsistent Ui - the worst is the Qt3 look that i hate. In Karmic doesnt have PulseAudio by default - thats also a plus. What i didnt like is the myriad of configuration options for everything - it got annoying when i saw dozens of checkboxes i never needed and/or didnt understand.
It might have a bright future though, because of the new KDE that is rumored to be stable (in contrast with older versions that were not very). That and coupled with a UI overhaul for older apps or replacing them for something newer/ Windows resemblance might increase its popularity.

---

### Post by JBAlaska on 2009-11-24
You might want to check out LXDE also, I've been playing with it for a couple of days and I like what I see so far.

---

### Post by Melcar on 2009-11-24
I'm always torn between GNOME and KDE.  On one hand, I much prefer KDE as a desktop simply because it's more customizable from the get go, the panels are nicer, and the menu system is much better.  On the other hand however, I much prefer GNOME (or gtk rather) applications since I like their presentation, the way they work, and seem far more robust and stable compared to qt applications; qt applications in my opinion try (and often fail) to do a lot of things, while gtk ones have this no-nonsense approach that allows you to perform your task quickly.  So I often end up with a KDE desktop and a bunch of gtk apps. :).
XFCE is like GNOME-lite in my opinion.  If you want minimalistic, there are far better DEs out there.  I don't mind XFCE on a machine that works mostly as a backup, but on a machine that I have to work all the time I prefer more feature rich DEs like GNOME and KDE.
Oh, and one other thing, Kubuntu is a bad KDE experience.  Go for OpenSuse or Fedora if you want a good KDE desktop.  Debian works too.

---

### Post by XubuRoxMySox on 2009-11-24
I played with LXDE too and it definitely is lightweight and snappy! But for me it was plagued with persistent, annoying bugs. It has alot of promise, though, and I wish them well. It's constantly "under heavy development," so it's hard to keep up with... it's like Beta software or something.

I've learned that LXDE takes most of its code from Xfce, so I naturally imagine that when LXDE "matures" it'll prob'ly be little different from Xfce anyway. I do like the file manager (PCManFM) much better than Xfce's default (Thunar), though. It's a keeper!

I started in Gnome, then in an obsessive quest for ultralight weight and superfast speed, I played with plain ol' Openbox (wonderful, minimalistic, powerful!) using [Crunchbang Linux]("http://crunchbanglinux.org") which is still my "main" distro on the laptop, then LXDE - lightweight and graphical but so very buggy on my machines, and settled for what I feel is a perfect balance between ultralight and superduper-graphical: Xfce (Xubuntu Karmic). 

Oh, just to see what all the fuss was about I toyed with KDE too. It's very Windowsy (which I hated, but lots pf people prefer) and much slower on my old hardware - but it did work, and I have a few favorite QT applications that I carry over to both my Openbox and my Xubuntu boxes.

Xubuntu does not ship with PulseAudio (thank God) and uses much less of my 'puter's limited resources, but still has all the simplicity of Gnome. Karmic Xubuntnu is gorgeous, fast, and bug-free for me so far.

-Robin

---

### Post by hoppipolla on 2009-11-24
Gnome is polished, refined and friendly, but IMO lacks well integrated visual flair, and can have a tendency to OVER-simplify. I also think GTK and Nautilus need work.

XFCE is lightweight and well-built, it's great for older machines but again lacks integrated and functional visual flair.

KDE is my fave, I love it but it needs a little more work on the 4.x branch to become complete. It's also just a little slower sometimes, and doing things like editing menus and creating icons is currently a little more complex and long-winded than would be preferable!

Oh, and yeah KDE software can sometimes not be as nice as the Gnome equivalents, but I feel this is just due to the dip of support and attention suffered during the earlier KDE 4 releases (4.0-2)

Overall I like XFCE and Gnome equally, but KDE is my fave (as everyone is well aware xD)

---

### Post by Roasted on 2009-11-25
> **gradinaruvasile said:**
> Gnome - Packed with features, easily customizable, OOTB support (well a few clicks away) for Samba/SFTP/NFS/etc, many apps by default. Also easy to use. The GTK toolkit has many programs that use it for basis and even QT apps mimic quite right its looks thus has a more unified looking interface. I think its a natural choice for default DE.
Oh, and it has Compiz by default...
On the dark side the Ubuntu devs have come to the conclusion that PulseAudio is mature enough to be at the core of sound processing. It turned out that lots and lots of users had audio problems - thats inexcusable on the default DE for the most popular(?) linux distro.

Xfce - I am a fan  of this one. Its a more minimalistic approach, but has applications for basically everything Gnome has. A plus is that these applications are not tied to the DE/each other so they can be removed without problems unlike Gnome where some tings like evolution-server cannot be removed.
It is far more snappier than Gnome (essentially  a light-gnome), and naturally has fewer features OOTB. I would recommend only to those who know Ubuntu's workings and such because some stuff isnt as straightforward as in Gnome. 
But it can be expanded as necessary. One minus is the menu handling (Karmic) that is halfway implemented (basically you have to edit .xml s to accomplish this, never did it i created 2 launchers to contain my 3 party apps). The menu structure differs a bit from Gnome's, some applications icons will not be visible in the menu.
Very good on older hardware/for people who dont want wobbly windows/fishes in transparent cubes/mounting everything(almost) via gigolo  but speed and simplicity. It is also based on Gtk+ as Gnome so all Gtk+ apps will run under it without problems. No default PulseAudio here. Clean and simple are 2 words that describe it.
One problem though: some packages need to be installed (gnome-mount and something else) to make Gigolo (the disk mounter) actually work.

KDE - i didnt try it extensively, but looks very much like vista/windows7's interface. It is based on the Qt toolkit - unfortunately as far as i could tell the interface of the programs is kinda messy - lots of Qt3 (that have their own windows-bare looking interface) apps in the repos that look different from the Qt4 apps (that can "steal" the widgets from the system theme making them look more alike). The Gtk+ apps again have their own looks (i am not sure, might be some compatibility theme with those too). All in all its shiny-flashy at the core, but once you install some apps it becomes riddled with inconsistent Ui - the worst is the Qt3 look that i hate. In Karmic doesnt have PulseAudio by default - thats also a plus. What i didnt like is the myriad of configuration options for everything - it got annoying when i saw dozens of checkboxes i never needed and/or didnt understand.
It might have a bright future though, because of the new KDE that is rumored to be stable (in contrast with older versions that were not very). That and coupled with a UI overhaul for older apps or replacing them for something newer/ Windows resemblance might increase its popularity.

Being an avid KDE and Gnome user, I can assure you the only reason KDE resembles Windows is the fact it defaults to the bottom. Kick the KDE panel to the top and presto - you have something that looks oddly similar to Gnome. All menus are in the upper left in KDE, just like in Gnome, clock in the upper right, etc. Imagine that? :P

XFCE - Simple, lightweight, great for older computers. 
Gnome 2.x - Boring as default, but stable and can be customized with a decent theme.
KDE - Great looking out of box, newer versions are more stable, easily customizable (even moreso than Gnome). 

I like Gnome and KDE a lot. Haven't used XFCE much. I'm more experienced in Gnome than I am KDE, but I've been using KDE a lot lately and I'm having a lot of fun with it. It just might overcome my main rig here shortly. :D

Like everything else, there's pros and cons to each scenario. Fortunately for us Linux users there aren't THAT many cons to any of the options. I think personal preference is what may be key to play a role in what avenue you take.

> **hoppipolla said:**
> 

Oh, and yeah KDE software can sometimes not be as nice as the Gnome equivalents, but I feel this is just due to the dip of support and attention suffered during the earlier KDE 4 releases (4.0-2)


It's ironic you bring that up. I've actually used KDE apps in Gnome-land long before I even tried KDE, just simply based on preference. I always felt like I could get more done in apps like Ktorrent, K3B, etc than I could in comparable Gnome applications. It was kind of funny for me to start messing with KDE on a regular basis because all of the same applications I used in Gnome were already native in KDE. :P

---

### Post by Roger Allott on 2009-11-25
Both Gnome and KDE have some great points, but both also have some not-so-good points.

Xfce is GnomeLite. Damn good on older lower spec machines.

The thing that really infuriates me is that each DE has its own name for what seem pretty much identical apps. Gnome has gedit, which appears on the Apps list as Text Editor, and Xfce has exactly the same thing but called Mousepad for some unfathomable reason.

I run Gnome on my day-to-day PC, although I've deleted one of the panels and kept the bottom one as I found that if it's at the top, it's near the close app cross and I often found myself quitting the O/S when all I actually wanted to do was close an app.

What I would like to see is the Gnome developers and the KDE developers working together to create a unified DE, perhaps named Knome, and then strip it down to create a KnomeLite.

---

### Post by hoppipolla on 2009-11-25
> **Roasted said:**
> It's ironic you bring that up. I've actually used KDE apps in Gnome-land long before I even tried KDE, just simply based on preference. I always felt like I could get more done in apps like Ktorrent, K3B, etc than I could in comparable Gnome applications. It was kind of funny for me to start messing with KDE on a regular basis because all of the same applications I used in Gnome were already native in KDE. :P

ah yes well, I mean some are outstanding! 1.x Amarok, Kopete in it's KDE3 days at least, K3B, Ktorrent and all those are brilliant :)

It does vary a lot, I mean I do think Qt is more powerful than GTK and can make for some wonderfully flexible and attractive apps! :)

---

### Post by crimesaucer on 2009-11-27
> **gradinaruvasile said:**
> "......some applications icons will not be visible in the menu....." (in the xfce4-menu)


Here are 2 easy fixes I did for missing icons for apps, and missing icons for menu categories (and also for apps being placed in the wrong category). 


For missing icons with apps just go to the "/usr/share/applications" directory and in there you will see your installed programs that are in your xfce4-menu.


Each app should have a desktop configuration file.


I had a missing icon for my ePDF app and I fixed it by opening the ePDF desktop configuration file in root. All you have to do is name the icon you want to use (in this case I linked it to the acroread icon for adobe PDF files)


```

[Desktop Entry]
Categories=Viewer;Office;GTK;
Comment=Lightweight PDF document viewer
Comment[ca]=Visor de documents PDF lleuger
Comment[es]=Visor de documentos PDF ligero
Exec=epdfview %f
GenericName=PDF Viewer
GenericName[ca]=Visor PDF
GenericName[es]=Visor PDF
Icon=acroread
Name=ePDFViewer
Name[ca]=ePDFViewer
Name[es]=ePDFViewer
MimeType=application/pdf;
Terminal=false
Type=Application

```


You could link it to any icon that your system is using.


I also had this annoying "Other" section that had my Celestia, Gpredict, and grig in it..... and the "Other" section was using this generic star icon that didn't look as good as the other icons in the menu. So, I really wanted Celestia and Gpredict in the same "Educational" menu section that had my Stellarium app (since they are all similar programs).


What I did to fix this was I opened up the desktop configuration files of those 3 apps (Celestia, Gpredict, and grig), and I changed the Categories section to be the same as the Stellarium Categories section:


```
Categories=Education;Science;Astronomy;
``` 


This put all four of those apps in the same "Education" menu section, and the "Other" menu section disappeared.


grig (which is the ham radio part of Gpredict) was also missing an icon so I found one that matched it and then edited the file to use the icons name.


Just check in your icon theme pack in the apps section for the correct name that you want to use (with out the .svg or .png part).


My last fix was for the missing icon for the "Education" section. Instead of having no icon, I had a big red error "X" icon for "missing icon".....


What I did to fix this was I went to the "/usr/share/desktop-directories" directory and I found the 2 files called "Education desktop configuration".


In both of those files was a section for the icon (I can't remember if it was left blank like "Icon= ", or if it had a bad name to a non-existent icon). But it was easily fixed by putting the correct name of the icon I wanted to use (from my hydroxygen icon pack):


```
Icon=applications-science
```


Anyway, writing this post took more time than correcting those icons/menu categories.

---

### Post by jwbrase on 2009-11-27
> **Roger Allott said:**
> I run Gnome on my day-to-day PC, although I've deleted one of the panels and kept the bottom one as I found that if it's at the top, it's near the close app cross and I often found myself quitting the O/S when all I actually wanted to do was close an app.


That's easy to solve: Just right click on the User switcher applet and hit "remove from panel". The shutdown and logout options will then be under the System menu. I got used to that under Intrepid, and was always a bit dissatisfied with Jaunty until I figured out that I could get the shutdown/logout options back under the menu simply by removing the applet.

---

### Post by Pasdar on 2009-11-28
Default look:
KDE: ++
GNOME: --
No explaining needed here

Customization:
KDE: ++
GNOME: --
I wonder why some people have this as pro for GNOME. You have to do all kinds of things to make GNOME look nice, including:
add fonts, maybe edit confs, change all kinds of things all over the place. Its quite a hassle and takes some time to do all these things.

In KDE you can change everything in gui, click here, click there... and if you're  freak that wants to do everything in conf files and edit things, copy files from here to there... that's also possible. So this is definitely a plus for KDE and minus for GNOME.

Speed:
KDE: ++
GNOME: --

Uniformity:
KDE: ++
GNOME: --

Number of programs available as part of the DE:
KDE: ++
GNOME: --

Update of DE and its programs:
KDE: ++
GNOME: --

That's why I use KDE.

---

### Post by Tibuda on 2009-11-28
> **Pasdar said:**
> Customization:
KDE: ++
GNOME: --
I wonder why some people have this as pro for GNOME. You have to do all kinds of things to make GNOME look nice, including:
add fonts, maybe edit confs, change all kinds of things all over the place. Its quite a hassle and takes some time to do all these things.

In KDE you can change everything in gui, click here, click there... and if you're  freak that wants to do everything in conf files and edit things, copy files from here to there... that's also possible. So this is definitely a plus for KDE and minus for GNOME.
So Openbox was renamed to Gnome?

---

### Post by cascade9 on 2009-11-28
> **Roasted said:**
> Being an avid KDE and Gnome user, I can assure you the only reason KDE resembles Windows is the fact it defaults to the bottom. Kick the KDE panel to the top and presto - you have something that looks oddly similar to Gnome. All menus are in the upper left in KDE, just like in Gnome, clock in the upper right, etc. Imagine that? :P 

+1. I have actually had arguments with people over this, mainly when they see my Xfce setup (with a single bottom bar). I've had people insist that I've got to be running KDE (or a really odd win XP theme).  Even when I showed them the 'about Xfce' they still insisted tat I've just done soem neat hacking. LMAO. 

> **Pasdar said:**
> 
Speed:
KDE: ++
GNOME: --

Number of programs available as part of the DE:
KDE: ++
GNOME: --


Odd, I've found Gnome and Xfce are consistently faster than KDE. As for number of programs...er....you can run gnome apps on KDE/Xfce, etc. etc. The number of programs is the same IMO. I would guess that there are actually more gnome native apps, but I'm just guessing.

---

### Post by Pasdar on 2009-11-28
> **danielrmt said:**
> So Openbox was renamed to Gnome?

Maybe I exaggerate a bit, but anyone who has used both for a long time knows that its much more of a hassle to make GNOME look nice, than in KDE.

---

### Post by Pasdar on 2009-11-28
> **cascade9 said:**
> Odd, I've found Gnome and Xfce are consistently faster than KDE. As for number of programs...er....you can run gnome apps on KDE/Xfce, etc. etc. The number of programs is the same IMO. I would guess that there are actually more gnome native apps, but I'm just guessing.

Well how fast it is really depends on your hardware now doesn't it? When you benchmark something you don't do it on a slow PC for a reason. ;)

Also when I say more Apps, I mean more apps that come from either the KDE team or GNOME team... not third party applications that added with a distro... that usually hurts the uniformity of the DE... which is another weak point of GNOME.

---

### Post by cascade9 on 2009-11-28
> **Pasdar said:**
> Well how fast it is really depends on your hardware now doesn't it? When you benchmark something you don't do it on a slow PC for a reason. ;) 

Actually...I'm more likely to benchmark with crappy, older hardware. When you are way over minimum specs, who cares? When you are trying squeeze as much out of some old box, its a bit more important. 

I've never done Serious benchmarking between KDE and Gnome, but from my limited tries KDE always came out slower. I do know that some distros are more Gnome based, some are more KDE based, it possible that KDE on a KDE 'friendly' distro (e.g. OpenSUSE, Mandriva) would be faster than Gnome. But from the last time I did any real benchmarks with OpenSUSE gnome still ran faster. That was a while ago though, it might have changed.

If you've got any reliable KDE vs Gnome benchmarks, linkies, please :) 

> **Pasdar said:**
> Also when I say more Apps, I mean more apps that come from either the KDE team or GNOME team... not third party applications that added with a distro... that usually hurts the uniformity of the DE... which is another weak point of GNOME.

Uniformity? Apart from the old 'KDE apps look out of place on Gnome,' and vice versa, I havent had any problems with that. Mainly using Xfce, with XFCE apps and some Gnome apps though I doubt I would. 

I'm not that fussed on everything looking like everything else in DEs (or WMs for that matter). If I perfer, say K3B (which I do) last thing I care about it that the window has a different border, buttons etc.. IIRC, thats fixable anyway. 

I'm not sure that KDE has more native apps than Gnome anyway, but I cant be stuffed to analize the data...

[http://en.wikipedia.org/wiki/List_of_KDE_applications](http://en.wikipedia.org/wiki/List_of_KDE_applications)
[http://en.wikipedia.org/wiki/List_of_GNOME_applications](http://en.wikipedia.org/wiki/List_of_GNOME_applications)

---

### Post by Roasted on 2009-11-28
> **cascade9 said:**
> 


Odd, I've found Gnome and Xfce are consistently faster than KDE. As for number of programs...er....you can run gnome apps on KDE/Xfce, etc. etc. The number of programs is the same IMO. I would guess that there are actually more gnome native apps, but I'm just guessing.

With older versions of KDE, I'd probably go along with this. But with the newer version of KDE out (4.0+) I don't see a difference in speed, and I dual boot Ubuntu 9.04 and Kubuntu 9.04 on the same computer. 

Oh, and for everyone out there who insists KDE is a bloated memory hog, I decided to test this theory out. I booted up my Ubuntu partition and without clicking anything else, launched system monitor. Then I did the same thing in Kubuntu.

Ubuntu - 362mb RAM used upon fresh boot.
Kubuntu - 274mb RAM used upon fresh boot.

Same computer.
Both Jaunty 64 bit.
Both with 3d effects enabled.
Both with no start-up applications enabled.

Memory hog? 
Bloated?
Slow?

:lolflag:

This isn't me saying that KDE is better than Gnome. I use both heavily. But my point is, the days of "KDE is bloated" are long gone, and an argument that is shockingly still used.

---

### Post by Pasdar on 2009-11-28
Kubuntu definately uses less memory and less CPU... not just a bit less, a lot less actually... I've posted about that several times. HOWEVER, I think you do require a much better videocard for Kubuntu to handle all the eye candy.

In other words, I think it would perform less on a:
Quadcore CPU + Intel GMA GPU

But perform way faster on a:
Single core (2Ghz) + a good dedicated GPU (at least GeForce 6200 or something).

---

### Post by Roasted on 2009-11-28
> **Pasdar said:**
> Kubuntu definately uses less memory and less CPU... not just a bit less, a lot less actually... I've posted about that several times. HOWEVER, I think you do require a much better videocard for Kubuntu to handle all the eye candy.

In other words, I think it would perform less on a:
Quadcore CPU + Intel GMA GPU

But perform way faster on a:
Single core (2Ghz) + a good dedicated GPU (at least GeForce 6200 or something).

Although I agree, I don't think the difference is really that substantial. I have a spare rig here on my desk that I use to play around with different operating systems. It's a 3.0 ghz Pentium 4 with onboard graphics and 1gb of RAM. It ran Kubuntu 9.04 acceptably well. No doubt that Gnome ran a little more seamless on it, but we're talking about a system that was brand new about 5 years ago. 

Any new computer out there, even with integrated video, should have enough kahunas to run KDE in a decent manner.

---

### Post by lightningfox on 2009-11-28
I use KDE and I think KDE is the best for new Linux users.

---

### Post by crimesaucer on 2009-11-29
When I first installed xubuntu in 2006 I didn't know much about Linux. I chose xubuntu first, but when I tried ubuntu with gnome I decided that xubuntu was faster on my old HP Pavilion dv4230us (1.6GHz Celeron M chip with 512MB RAM 60GB hd and intel graphics). Using Beryl/Emerald back then I found that it worked better with my low specs using Xfce4.


After a while I really liked how the xfce4 desktop is designed, and it's minimalism and simplicity. I also liked how it handled my user permissions, and I preferred editing the conf files rather than using the GUI apps for gconf settings.


A year latter I switched to Arch (on that old laptop) and I decided to try Gnome again. There were some things that I liked better like computer sounds for clicking buttons and the log-in/log-out. I also liked the gnome-panel's true compositing which xfce4-panel didn't have. But as soon as I installed Compiz/Emerald I noticed it becoming slower. I also tried a development metacity w/compositing and I didn't like it that much.


So I reformatted my laptop with a minimal install of xfce4. When I added compiz fusion it stayed fast. I eventually ditched compiz for native xfwm4 compositing since it was a bit faster and didn't spike my cpu when scrolling long pages. I used gtkrc-2.0 files to make my panel look better but I still missed the real transparency of gnome-panel and the gnome-sounds.


Then a year later I broke that laptop (and it wasn't worth repairing it with such low specs) so I got a new HP Pavilion with 4GB RAM, AMD Turion 64 x2 TL-60, NVIDIA GeForce 7150m / nForce 630m, 250 GB that I installed Arch64 onto.


I tried Gnome again on my new specs, I figured I had a 64-bit x2 chip, much better NVIDA graphics, and more RAM so it wouldn't matter. 


Again I found myself enjoying the gnome-panel and gnome-computer sounds, and I found that gnome also had my multimedia keys working out of the box as well as my vista partition. I liked this but I still felt that gnome was slower, and when I added compiz-fusion it had no snap.


So I reinstalled Arch64 with a minimal install of xfce4 and found it running super fast. Even with compiz-fusion. I found that the app called "keytouch" could be used to enable my multimedia keys, and there was a cairo patch that could be used for true transparency for the xfce4-panel. (I still can't figure out how to enable computer sounds)


I've stayed with xfce4 ever since. I used compiz-fusion for a while and the when xfce4 4.6 came out I dropped compiz and used the xfwm4 compositing which made things faster and feel more stable (like scrolling pages). Recently I dropped xfwm4 for the Xmonad tiling window manager on top of the Xfce4 desktop: [http://haskell.org/haskellwiki/Xmonad/Using_xmonad_in_XFCE](http://haskell.org/haskellwiki/Xmonad/Using_xmonad_in_XFCE)



Here are a couple pics to show what can be done with the Xfce4 desktop:
-----------------------------------------------------------------------

This is Xfce4 using Compiz/Emerald and the xfce4-panel with a cairo patch for transparency:
[[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-41-6.png[/IMG]](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-41-7.png)



This is Xfce4/Xfwm4 using an embedded terminal and the xfce4-panel cairo patch:
[[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-13-7.png[/IMG]](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-13-6.png)



This is Xmonad tiling window manager running with Xfce4 Desktop Enviornment:
[[img]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-Xmonad-new-1.png[/img]](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-Xmonad-new.png)

[[img]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-Xmonad-new2-1.png[/img]](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-Xmonad-new2.png)




-------------------------------------------------------------------------
This is my deviantART gallery of my homemade gtk themes for xfce4 (there are some gnome desktops in there as well):

First page is Xmonad/Xfce4(newest), and Xfce4/Xfwm4 using terminator: [http://crimesaucer.deviantart.com/gallery/#_featured](http://crimesaucer.deviantart.com/gallery/#_featured)

Second page is mostly Xfce4/Compiz-fusion: [http://crimesaucer.deviantart.com/gallery/#_featured--2](http://crimesaucer.deviantart.com/gallery/#_featured--2)

Third page is all Xfce4/Compiz: [http://crimesaucer.deviantart.com/gallery/#_featured--3](http://crimesaucer.deviantart.com/gallery/#_featured--3)

Fourth page is some Gnome, some Xfce4/Xfwm4, and some Xfce4/Compiz: [http://crimesaucer.deviantart.com/gallery/#_featured--4](http://crimesaucer.deviantart.com/gallery/#_featured--4)

Page five has a few Gnome/compiz clearlooks themes: [http://crimesaucer.deviantart.com/gallery/#_featured--5](http://crimesaucer.deviantart.com/gallery/#_featured--5)

..... Everything after that is really old Gnome/Compiz and Xfce4/Beryl (and pretty ugly).




In my opinion KDE has the best looking desktop right now (I've never used it)..... Gnome shell looks like it will be really nice (again I have only seen the videos of it)..... but after using Xmonad for the last few days I think I have found my new window manager/desktop combo.

---

### Post by kevCast on 2009-11-29
GNOME is disgusting.

KDE is disgusting, but better.

XFCE is the best out of the three.

---

### Post by rudihawk on 2009-11-30
> **kevCast said:**
> GNOME is disgusting.

KDE is disgusting, but better.

XFCE is the best out of the three.

Agreed :)

---

### Post by Roasted on 2009-11-30
> **kevCast said:**
> GNOME is disgusting.

KDE is disgusting, but better.

XFCE is the best out of the three.

I'm not going to lie, I love all 3 of them, and I'm a big KDE fan now. But MAN does Xubuntu make that old POS computer I have sitting around zoooom.

---

### Post by Marvin666 on 2009-12-02
I've ran xubuntu since I started linux. Personally, I use a mix of gnome, kde, and xfce programs to my preference. No bugs or instability from it.

---

### Post by Stan_1936 on 2009-12-02
> **Melcar said:**
> ...
XFCE is like GNOME-lite in my opinion.......

There's enough of a difference(less) between Xubuntu and Ubuntu for me to feel a significant speed boost when using Xubuntu(XFCE)....relative to Ubuntu(Gnome).  And this is despite the fact that most people believe that Xubuntu's implementation of XFCE is bloated.

> **Melcar said:**
> ...
.....I don't mind XFCE on a machine that works mostly as a backup, but on a machine that I have to work all the time I prefer more feature rich DEs like GNOME and KDE....

You must be needing specifics that aren't available in XFCE.  For the OP, a linux beginner, I believe that XFCE would get the job done.

---


---
title: "HOWTO: Fluxbox inside GNOME (BETA)"
date: 2005-09-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Brunellus on 2005-09-08
Earlier, I asked whether it would be possible to run [Fluxbox]("http://www.fluxbox.org") as Gnome's default windowmanager instead of metacity. 

I am pleased to report that this is possible.  Consider this a draft howto, as I am busy trying to tweak things.

I am indebted to poofyhairguy's "enlightened gnome" howto, as well as Stormy Eyes' excellent advice on running Openbox within Gnome

**STEP ONE: Installing Fluxbox**

This is the easy part.  Fluxbox is in universe;  enable universe, fire up your terminal, and ```
$ sudo apt-get install fluxbox
``` that sucker.

You can restart the Xsession here, if you like.  When GDM comes up, you'll see Fluxbox added to your "Sessions" menu.

However, I would NOT restart the Xsession at this point.  Fire up your terminal and ```
$ sudo /usr/share/xsessions/fluxbox.desktop
```

where you see ```
exec=fluxbox
``` replace that line with ```
exec=startfluxbox
```

If you do this, Fluxbox will, on its first execution, generate a configuration file:

~/.fluxbox/startup

For a more complete discussion of what the startup file does in Fluxbox, please see [This page in the Gentoo Wiki]("http://gentoo-wiki.com/HOWTO_Fluxbox#Startup_Applications")

Log into fluxbox, and confirm that it does, indeed work.  We are now ready for 

**STEP TWO:  Cramming Fluxbox into Gnome**

This next section is essentially ripped off of poofyhairguy's excellent, and recently slashdotted, Enlightened Gnome Howto.

First,  execute the following in a regular terminal: ```
$ sudo cp /usr/share/gnome/default.session ~/.gnome2/session
```

Then, edit that session file: ```
 sudo gedit ~/.gnome2/session
```

Find this line: ```
 1,RestartCommand=gnome-wm --sm-client-id default1
``` and change it to this: ```
 1,RestartCommand=gnome-wm --default-wm fluxbox --sm-client-id default1
```

Save the file, restart your Xsession (CTRL+ALT+BKSPACE), and log back into gnome. 

This will take a while.  You will see fluxbox first, then the gnome-panel, and finally the desktop will appear and draw over all the fluxbox desktop.

**Fluxbox in Gnome: First impressions**

Fluxbox is a very lightweight windowmanager.  Not for nothing is it the wm of choice of  [DamnSmallLinux]("http://www.damnsmalllinux.org") From what I can tell, it takes up VERY little RAM.

It also draws and redraws faster than metacity, at least on my equipment--AMD k7, 512 MB RAM, nvidia geforce 5200 128mb VRAM-- and much neater as well.

Here's a neat trick that Fluxbox does:  open two windows.  Now middle-click drag one onto another.  The two windows are now docked together:  clicking on the titlebar will switch between windows.  In this way, you can tab through any number of windows.  This is particularly nice if you run stuff from terminals--that way, you can have the app in one window, then click the window itself and get the debug output.

Things I've got to figure out:

The nautilus desktop draws over fluxbox.  Thus, no flux taskbar and no slit (the flux name for the dock).

Also, I can't get flux's right-click menu.  Middle-click works.

Comments are ALWAYS welcome.  A huge shout and thanks to the whole Ubuntu community--y'all rock, hard.

And of course, a [screenshot]("http://static.flickr.com/27/41568346_aa996d0e15_o.png") of my desktop.  The wm is fluxbox, and an assload of gdesklets running.

---

### Post by UrbanSlayer on 2005-09-09
After doing the E16 into Gnome, I think you can get the right click menus and get some of Flux back by going into the Configuration Editor and telling Nautilus to not draw the desktop.  I forget exactly where it is, but that should do it.

---

### Post by xequence on 2005-09-09
It worked decently, just gnome and fluxbox conflict... Fluxbox brings along its bottom bar thingy...

Also, wikipedia says fluxbox isnt good in ubuntu because of some utf-8 encoding or something.

But, good trick to change WMs :)

---

### Post by traherom on 2005-09-10
[QUOTE=Brunellus]Fire up your terminal and ```
$ sudo /usr/share/xsessions/fluxbox.desktop
```[/QUOTE]Should be:
```
$ sudo **gedit** /usr/share/xsessions/fluxbox.desktop
```

:)

---

### Post by Dethlin on 2005-09-28
Thank you for this guide. I love this mix

One problem I seem to have is that Gnome takes about 2 mins to load up every time. Fluxbox starts straight away but the splash screen for gnome seems to stop at the Windows Manager stage for 2 mins then it loads up fine.

Anyone else have this problem?

thanks in advance :)

---

### Post by pay on 2007-01-16
> **Brunellus said:**
> Things I've got to figure out:

The nautilus desktop draws over fluxbox.  Thus, no flux taskbar and no slit (the flux name for the dock).If you run nautilus from the terminal with```
nautilus --no-desktop
```it won't draw over fluxbox.

---

### Post by tommytrying2linux on 2009-02-14
I'm going to try this, will report any problems here.

---

### Post by Twitch6000 on 2009-07-15
is there an updated version of this? i am trying to do this and the files mention are either not there or somewhere else.

---

### Post by stanca on 2009-07-27
Somehow I screwed my pseudo-transparency and especially menu alpha transparency in my fluxbox session.I installed xcompmgr too but I didn't know I have to disable the force pseudo-transparency first.So,despite the fact I removed completely xcompmgr and transset,the problem still persists.
I can't even disable the pseudo-transparency from configuration menu,it remained stuck with focused window alpha:255,unfocused window alpha:175,and menu alpha:255.
Do I have to reinstall the fluxbox wm again?
Edit:Solved in the end.Disabled pseudo-transparency from init file from ~/fluxbox/,reinstalled xcompmgr,restart,and now all is OK.Fluxbox in its maximum way:

---

### Post by SiKing on 2009-12-24
Hi.
Just found this great HOWTO. I am trying it on Ubuntu 8.04 (equivalent). Have a few questions if I may:

[LIST=1]
[*]  Everything seems to be running fine. Just as Brunellus mentioned: windows do appear to be drawing faster. How do I know if I _really_ am running Flux? I tried 'ps -elf | grep flux' and got nothing.
[*]  The application tabbing, which is the primary reason why I wanted to do this, does not seem to be working. When I middle-click on a window, it gets sent to the background! I think this may be some sort of GNOME setting, however I have no idea where it is. Any help?
[/LIST]
 Thank You.

---

### Post by tweaksource on 2010-01-22
> 

wikipedia says fluxbox isnt good in ubuntu because of some utf-8 encoding or something.




Wikipedia is not always correct.:)

---


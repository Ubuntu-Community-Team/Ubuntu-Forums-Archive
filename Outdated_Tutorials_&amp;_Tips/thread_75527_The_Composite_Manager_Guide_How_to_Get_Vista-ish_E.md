---
title: "The Composite Manager Guide: How to Get Vista-ish Effects in (K)(X)Ubuntu."
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by poofyhairguy on 2005-10-13
The Composite Manager Guide: How to Get Vista-ish Effects in (K)(X)Ubuntu.

HUGE UPDATE -December 23, 2005

You MUST get the new Nvidia drivers people. With the newest drivers, I HAVE STABLE COMPOSITE!!!!!!

The logout bug is gone. The artifacts are gone. Its all gone. 2005 ends and I get what I want- a modern desktop!

**Introduction**

Do you like drop shadows? Do you want a faster feeling desktop? Have you seen screen shot of Vista and wished Ubuntu could do the same? Then you might want a Composite Manager.

 It adds these effects that users would want:

1.Drop Shadows -OSX style. Almost all fast computers can do this.
2.What I call &#8220;the fading trick&#8221;- as windows are minimized they fade into the windows behind them or the desktop. Needs an Nvidia card. Vista does this. (note: the XFCE Composite Manager does not do this)
3.Windows that are more responsive to commands. At 100% CPU use I can still move windows with no ugly trails or jerkiness.
4.Transparent windows

These effects can not be given justice in a screenshot....so here is a video

[http://linux.jannol.com/ubuntu/demos/demo-1.mpg](http://linux.jannol.com/ubuntu/demos/demo-1.mpg)

That Jannol provided. Thanks.

Who can use a Composite Manager? I hate to say it, but only people with Nvidia cards, an ATI 9250 card (or lower) and Dapper, or a fast enough computer. 

PEOPLE WITHOUT SUPPORTED CARDS: You are not left out if your machine is fast enough. I do not know what fast enough is. Read my guide and be sure that you do the steps that are in bold and you use the command I suggest.

**What do you need to use a Composite Manager?**

1.Nvidia Card, a supported ATI card (a 92xx model or lower) or a fast CPU (just for drop shadows)
2.Time
3.The official Nvidia drivers installed if you have Nvidia card
4.Universe repo is accessible 
5.Internet Connection

******DISCLAIMER********

Composite Managers as they are now are a toy. I can promise that if you use one, it will crash on you. It will. One day it will crash your xserver and take everything you are doing with it. I will talk about ways to deal with that in the guide, but I can promise it will happen. Xcompmgr is an ACTIVE project with a new release recently. Please don't ask if Ubuntu or its developers can provide better support and don't hope for it to get better magically the next release or something (unless you use XFCE or KDE). The Linux desktop is going in a different direction than this. This is a &#8220;band aid&#8221; to get there. I tolerate its quicks and live with it maybe you can too. Now on to the guide.

***************************

**Steps to Use a Composite Manager**

**FIRST PART**

Open a normal terminal (applications, accessories, terminal) and put this in the terminal:

```
sudo gedit /etc/X11/xorg.conf
```

[B]USERS WITH UNSUPPORTED CARDS MUST DO THIS STEP TOO

A file will come up. Add these lines to the end of the file:

```

Section "Extensions"
        Option  "Composite" "Enable"
EndSection
```[/B]

For Nvidia Cards:

FIRST INSTALL NEWEST DRIVERS!!!!! Directions here:

[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

Now look through the file. Find the part called &#8220;device.&#8221; Add these two lines to that section:
```

        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true" 

```

Make it look like this:

```
Section "Device"
	Identifier	"NVIDIA Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
    	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
EndSection
```

For Supported ATI Cards (ATI 9250's and below) in Dapper (as soon as Dapper gets Xorg 7):

Make it look like this:

> Section "Device"
        Identifier  "Generic Graphics Card"
        Driver      "radeon"
        Option      "AccelMethod" "EXA"
        Option      "AGPMode" "4"
        Option      "EnablePageFlip" "true"
        Option      "DDCMode"
        Option      "RenderAccel" "true"
        Option      "SubPixelOrder" "NONE"
        Option      "ColorTiling" "false"
EndSection

Save the file. The hardest part is done.  If it does not restart type the command &#8220;startx &#8220; Save all the work you are doing, and restart the xserver by pressing the CTRL, ALT, and Backspace keys at the same time. I put these two sentences backwards for a reason.

**SECOND PART**

If you use KDE or XFCE you can stop now. For XFCE just log in and its native composite manager will now work by default ( I find this one crashes less than xcompmgr) and for KDE go to

 System Settings -> Desktop -> Window Behavior->Transparency

To configure KDE's built in composite manager. But be warned, just like Xcompmgr, both the XFCE and KDE Composite Managers have crashed on me. You are still a very early adopter.

If you are a gnome user, then log back into Gnome.

For Gnome we have to use Xcompmgr to get the effects. 
[B]
USERS WITH UNSUPPORTED CARDS MUST DO THIS STEP TOO

Open a terminal and put this in:

```
sudo apt-get install xcompmgr transset
```

Tell apt-get yes if it askes something and wait till its done. [/B]

Here are the commands for xcompgr:
> 
-d display Specifies which display should be managed.
-r radius Specifies the blur radius for client-side shadows. (default 12)
-o opacity Specifies the translucency for client-side shadows. (default .75)
-l left-offset Specifies the left offset for client-side shadows. (default -15)
-t top-offset Specifies the top offset for clinet-side shadows. (default -15)
-I fade-in-step Specifies the opacity change between steps while fading in. (default 0.028 )
-O fade-out-step Specifies the opacity change between steps while fading out. (default 0.03)
-D fade-delta-time Specifies the time between steps in a fade in milliseconds. (default 10)
-a Use automatic server-side compositing. Faster, but no special effects.
-c Draw client-side shadows with fuzzy edges.
-C Avoid drawing shadows on dock/panel windows.
-f Fade windows in/out when opening/closing.
-F Fade windows during opacity changes.
-n Normal client-side compositing with transparency support
-s Draw server-side shadows with sharp edges.
-S Enable synchronous operation (for debugging).

Yeah it hurts my brain too. So if I as was you, I would stick to only a few simple commands.

the command:

```
xcompmgr -cC & killall gnome-panel
```

will give you drop shadows and window acceleration. The command:

```
xcompmgr -fF & killall gnome-panel
```

Will give you the fading trick  and window acceleration.

The command:

```
xcompmgr -cCfF & killall gnome-panel
```

Will give you both. The command:

```
xcompmgr -a & killall gnome-panel
```

will just give you the window acceleration without the two tricks. This command is the most stable one by far. Its worth it to try it even if you don't like drop shadows and fading just to feel what an nice accelerated desktop feels like.

Advanced Commands I use (you should try them too- recommended):

```
xcompmgr -fF -I-.002 -O-.003 -D6
```

That one just does fading in a fashion thats much better than the default.

```
xcompmgr -fF -I-.002 -O-.003 -D6 -cC -t-5 -l-6 -r5
```

That one does fading in the best way and has drop shadows that look much better overall- especially with drop down lists such as the Applications menu. This could be called "The Perfect Setting." (I know its not for everyone)
[B]
BEST SETTING FOR PEOPLE WITH NON SUPPORTED CARDS

```
xcompmgr -cC -t-3 -l-5 -r5
```

That setting gives sane drop shadows that work well with the Gnome menu's. It should be possible to use this command by itself if you add the composite lines to your xorg and you computer is fast enough (who knows what fast enough is- just try). This is where xcompmgr is useful for most people.[/B]

But try what you can try and if it crashes just restart the xserver and don't use that command again. If you want to stop xcompmgr, hit CTRL and the C key at the same time.

If you want xcompgr to start when Gnome starts, the go to &#8220;System, Preferences, Sessions.&#8221; Click the last tab called &#8220;Startup Programs.&#8221; Click &#8220;Add.&#8221; Type in what command you liked best or worked best for you. Then for order pick &#8220;41&#8221; Then click &#8220;close,&#8221; log out and log back in.

This part (actually most of this guide) I credit to arnoct:

Using Transset for transparent windows in Gnome:

This is just an extra little command. If you want to set certain windows as transparent, then run the command "transset" in the console. Your mouse will turn into a crosshair; simply click on the window you want to set as transparent. The transparency value can be anywhere from 0 (completely transparent) to 1 (opaque.) It defaults to .75, and back to 1 if the window is already transparent.

For example, if you want to make a window half-transparent:

```

transset 0.5

```

**Tricks To Deal With Composite Manager Bugs.**

After prolonged use of xcompmgr, I have come across many bugs that can be quite annoying. To get around these, here are some tricks I have found.

****Most Important Trick and why I use Gnome and xcompmgr over any of the others****

As I said before, all the Composite Manager's crash. One advantage of xcompmgr is with this script you can turn it off and on easily. Credit for this goes to frodon.

Put this command in the terminal:

gedit toggle_xcompmgr.bash 

Copy this into the empty file:
```

#!/bin/bash
a=`ps -aef | grep -i xcompmgr | awk ' {if ($8 == "xcompmgr"){printf "2"}} '`
if  [[ $a = "" ]]
then
	**yourcommand **&
	killall gnome-panel
else
	kill -9 `ps -aef | grep -i xcomp | awk ' {if ($8 == "xcompmgr"){printf $2}} '`
	killall gnome-panel
fi
```

See The part I bolded? Thats where you need to put the xcompmgr command that works best for you. Here is a good default one:
```

#!/bin/bash
a=`ps -aef | grep -i xcompmgr | awk ' {if ($8 == "xcompmgr"){printf "2"}} '`
if  [[ $a = "" ]]
then
	xcompmgr -fFcC &
	killall gnome-panel
else
	kill -9 `ps -aef | grep -i xcomp | awk ' {if ($8 == "xcompmgr"){printf $2}} '`
	killall gnome-panel
fi
```

Now save the file to your home folder. Close gedit. Put this command in the terminal:

```
sudo mv toggle_xcompmgr.bash /usr/bin/
```

then this command:

```
sudo chmod +x /usr/bin/toggle_xcompmgr.bash
```

Then right click on gnome panel and add a shortcut, choose custom shortcut in the menu and add

```
/usr/bin/toggle_xcompmgr.bash 
```

in the command field. You can make a desktop launcher by right clicking on the desktop, choosing &#8220;create launcher&#8221; then use the same command.

Now each time you click on the icon xcompmgr is toggled on/off! This is essential and its the only way around many bugs.

**First Bug: Media Players Crash or Have Artifacts When in Full Screen Mode**

The solution to this problem was gvien to us in the new release of Breezy, and is enough to warrant praise as the was the most annoying bug before Breezy. 

Totem-xine was upgraded in Breezy a lot. Its way better to use and IT IS VERY STABLE WITH XCOMPMGR! Sorry I screamed but it makes me happy. Full screen, no problem. Any type of file, no crashes. So just use totem-xine for all video files. All the audio players I tried work already, but only Breezy Totem-xine works for video everytime. The second best by far the is VLC, and then all others trail by a lot- even other xine's like xine-ui, gxine, or kaffine. Don't use them.

**Second Bug: When you try to logout in Gnome, it seems to crash!**

THIS BUG IS GONE WITH NEWEST DRIVERS AND NVIDIA CARDS!!!!!  DANCING IN THE STREETS!!!!!

**Third Bug: Games don't work or are slow**

Turn off xcompmgr for all opengl games. 

**Fourth Bug:  Open GL screen savers crash my computer!**

This is a bad one. Only way around it is to use a screensaver that does not use opengl. Luckily Ubuntu comes with many, unfortunately they are not the default. To fix this, turn off xcompgr, and go to &#8220;System, Preferences, Screen Saver&#8221; Choose the blank screen option, or pick a screensaver that looks SO old school (like Windows 95 old school) that you know it does not use opengl.

**Fifth Bug: Xcompmgr crashes when using Firefox**

Easy solution is to use Epiphany. It crashes way less. Like it might end crashing almost completely for you. And when you install its pluggins it has an automatic session saver. But we all can't do that. For those like me who are Firefox addicts, use this extension:

[https://addons.mozilla.org/extensions/moreinfo.php?id=436](https://addons.mozilla.org/extensions/moreinfo.php?id=436)

**Sixth Bug: Xcompmgr Crashing when you are doing important things.**

This is one area where Breezy is a lot better as well. 

The problem is that xcompmgr crashes. I can go weeks without seeing one, then boom one will hit one day. Its annoying if you are typing a big rant in Firefox or on GAIM, or whatever else you are doing. 

Best way around this it to use the first trick to just turn xcompmgr off when you are doing important things. It can turn on and off without crashing things, so even if you remember half way through a email or project click that icon and turn it off! 

Another thing is to do all writing beyond a few lines in OpenOffice.org2 writer. It has GREAT crash recovery &#8220;skills&#8221; and does a wonderful job of getting you right back where you are if any of the composite managers act up.

**Seventh Bug: Problems with Flash in Firefox**

Credit goes to varunus for this one.

First, open up your firefox launcher file with the following:
```
sudo gedit /usr/bin/firefox
```

Find the part that looks like this:
```
##
## Variables
##
MOZ_DIST_BIN="/usr/lib/mozilla-firefox"
MOZ_PROGRAM="/usr/lib/mozilla-firefox/firefox-bin"
```

Add a line, making it look like this:
```
##
## Variables
##
##Added for composite extension to work
export XLIB_SKIP_ARGB_VISUALS=1
MOZ_DIST_BIN="/usr/lib/mozilla-firefox"
MOZ_PROGRAM="/usr/lib/mozilla-firefox/firefox-bin"

```

Flash will no longer have any issues.  This makes firefox ignore the extra alpha channel that xcompmgr gives it for color.  Because the application itself doesn't do anything with the alpha channel, all of the effects still work, and flash will no longer complain.


**Eighth Bug: You get addicted to using xcompmgr and can't go back**

I still have not found a solution for this one!

Well I wish you luck in your hunt for eye candy and I hope it goes well. In the future new technologies will come about to further modernize the Linux desktop. Till then the Composite Managers allow us to live on the edge and have the future today. If you have and suggestions, please make them!

New additions:

I have included my xorg.conf file, because at one point I discovered the magic that allowed me to use xcompmgr with two screens and I want to share it!

Also I have included the newest xcompmgr that I personally compiled. All you (should) have to do in untar the file into....say your home folder...and the use the "cd" command to get into the fold made then use all of the xcompmgr commands as I indicated above.

**_HUGE EDIT!!!!!!_**

Ok, I have a GUI for you xcompmgr fans. Download the deb file I attached to this post:

[http://ubuntuforums.org/showpost.php?p=555510&postcount=170](http://ubuntuforums.org/showpost.php?p=555510&postcount=170) 

to your home folder and extract the deb file there (forum won't let me attach a deb file). First use apt-get to get the dependancies you need:

> sudo apt-get install libgtkmm-2.4-1c2

Then install the deb file in the terminal with this command:

> sudo dpkg -i gcompmgr_0.21-2_i386.deb

To use it, run the command:

> gcompmgr

I hope you enjoy, it makes messing with Xcompmgr more fun!

---

### Post by Quartus on 2005-10-13
And I don't have an Nvidia card... :(

---

### Post by kdavison007 on 2005-10-13
Why do you have to have an Nvidia card?

---

### Post by poofyhairguy on 2005-10-13
[QUOTE=kdavison007]Why do you have to have an Nvidia card?[/QUOTE]

You don't HAVE to have an Nvidia card to try it out, but only Nvidia cards and their official drivers accerate the current set of composite managers.

Without an Nvidia card, your CPU will do all the work. That will work for maybe the drop shadows, but the fading and the rest would kill a not super fast system.

---

### Post by Paulus on 2005-10-13
Thanks poofhairyguy, that is probably the best how-to I have ever read- I particuarly enjoyed the "bug's" section- a part i didn't expect. Though as previously pointed out there is nothing regarding ati cards- perhaps a mention in the title would be niiice.:rolleyes: EDIT: You have :)

Thanks again!


btw > xcompmgr -fF -I-.002 -O-.003 -D6
 rocks!

---

### Post by tommy04 on 2005-10-13
Well, I tried "xcompmgr -cCfF & killall gnome-panel", and it was really pretty, until you get to the part where X froze up and I couldn't even CTRL+ALT+BACKSPACE out of it :/

Any ideas why that's happening? Firefox was running at the time... I don't want to try it again because i'm worried it might mess up the hard drive next time I have to hard reboot...

---

### Post by poofyhairguy on 2005-10-13
[QUOTE=Paulus]Thanks poofhairyguy, that is probably the best how-to I have ever read- I particuarly enjoyed the "bug's" section- a part i didn't expect. Though as previously pointed out there is nothing regarding ati cards- perhaps a mention in the title would be niiice.:rolleyes:

Thanks again!


btw  rocks![/QUOTE]

Cool. I edited it a little to add a section about what happens without a Nvidia card, but I'll do it more so. I'm glad you like that setting, it took forever for me to get it. I'm glad you enjoyed the guide, I tried my best!

---

### Post by deception on 2005-10-13
Great job! Just would like to add if anyone experiences the "overlapping of the gnome-panel by applications".. just type "killall gnome-panel" in a terminal :KS 


Thanks poofyhairguy :D

---

### Post by rosslaird on 2005-10-13
In breezy, using the latest kde and a somewhat older nvidia card, kde crashes my whole system when I have the composite extension and rendering effects enabled in the kde control module. Since kde simply fails to load after the changes to xorg.conf and kde window settings, this presents an issue: how to turn off the composite effects in kde if kde will not start? The workaround, which I eventually discovered, is to run another window manager (like xfce) and run kcontrol from within it. The kde composite settings can then be changed back.

Xfce, by the way, works great with the composite effects.

Ross

---

### Post by scourge on 2005-10-14
> Either buy a new card if you want this, or if you can't email your hardware maker and ask them for better Linux support!

Better Linux support is always good, but it's not the same thing as support for xcompmgr. I read that ATI's stance is something like: "If the X.org developers don't think Composite is worthy of support, why should we think it is?". I think it makes sense.

---

### Post by poofyhairguy on 2005-10-14
[QUOTE=scourge]Better Linux support is always good, but it's not the same thing as support for xcompmgr.[/QUOTE]

True. Xcompmgr is a dead end. But better Linux support will hopefully allows ATI users to not get left out of next big eye candy upgrade.

> 
 I read that ATI's stance is something like: "If the X.org developers don't think Composite is worthy of support, why should we think it is?". I think it makes sense.

Buying an  Nvidia card to get the effect I want makes sense to me. ATI's excuses never make sense to me.

Maybe if ATI drivers where great and this was the one thing holding them back.....but thats not the case.

---

### Post by ssam on 2005-10-14
it just about works for me on a 64 mb Radeon Mobility 9000 with the opensource drive, on a powerbook g4 1ghz. but i get funky yellow colours and a couple of games can crash the xserver (whether xcompmgr is running or not).

xorg 7 should make things work better

---

### Post by scourge on 2005-10-14
> Buying an Nvidia card to get the effect I want makes sense to me. ATI's excuses never make sense to me.

Considering that the Composite extension is buggy even on systems with an nVidia card I'd say you're in a small minority here. Most people just want better OpenGL support, so that's where ATI's focus should be. I also switched to nVidia about 9 months ago, but I still read the boards at Rage3D.com, and from what I've read it seems that ATI is making progress.

---

### Post by poofyhairguy on 2005-10-14
[QUOTE=scourge]Considering that the Composite extension is buggy even on systems with an nVidia card I'd say you're in a small minority here.[/QUOTE]

Its a nice minority to be in.

> 
 Most people just want better OpenGL support, so that's where ATI's focus should be. I also switched to nVidia about 9 months ago, but I still read the boards at Rage3D.com, and from what I've read it seems that ATI is making progress.

If ATI supports all the tricks that are comming with Xorg 7.0 then I'll be happy for sure. Till then I'll survive with xcompmgr.

---

### Post by scourge on 2005-10-15
> Its a nice minority to be in.

I kind of agree here. GPU accelerated desktop is definitely the way to go. I've experimented with xcompmgr quite a lot myself and I think it has great potential. If it was stable it would be a good reason to switch to Nvidia.


> If ATI supports all the tricks that are comming with Xorg 7.0 then I'll be happy for sure.

I wouldn't hold my breath. ATI's Linux development team has very limited resources (proportional to Linux's market share) and they're still struggling with basic OpenGL compatibility. When they accomplish that goal they can focus on performance. And then, X.org tricks. At least that's what I think their plan is.

---

### Post by flibble on 2005-10-15
Hi :)

Well, I've been reading about xcompmgr for a few weeks, how it's buggy and a deadend and I've been thinking, "Sounds like a waste of time". Then I tried it. It's beautiful.  Really... beautiful... I had to smurk at myself, repeatedly hitting ctrl+alt+D, sending multiple windows fading in and out, rolling my mouse along the firefox bookmarks toolbar,  menus gliding their shadows into one another. Lol. Xmas in X land. Thanks for a great howto phg.

---

### Post by poofyhairguy on 2005-10-15
[QUOTE=flibble]Hi :)

Well, I've been reading about xcompmgr for a few weeks, how it's buggy and a deadend and I've been thinking, "Sounds like a waste of time". Then I tried it. It's beautiful.  Really... beautiful... I had to smurk at myself, repeatedly hitting ctrl+alt+D, sending multiple windows fading in and out, rolling my mouse along the firefox bookmarks toolbar,  menus gliding their shadows into one another. Lol. Xmas in X land. Thanks for a great howto phg.[/QUOTE]


No problem. Ever since Breezy made Xcompmgr tolerable to use (by almost never crashing it) I have been hooked myself.

---

### Post by norwyn on 2005-10-17
Hi folks, and thank you poofyhairguy for a very nice guide!
I'm using XFCE and I wonder what the command is to disable the shadow effects, or I think it is the shadow effects that I want to disable. 

Problem:
When I'm changing the windows seize everythings freeze. That is the function i want to disable ;). I know that I should expect it to crash often, but everything else work close to perfect.

Thanks in advance, and sorry for my poor english.

---

### Post by poofyhairguy on 2005-10-17
[QUOTE=norwyn]Hi folks, and thank you poofyhairguy for a very nice guide!
I'm using XFCE and I wonder what the command is to disable the shadow effects, or I think it is the shadow effects that I want to disable. 

Problem:
When I'm changing the windows seize everythings freeze. That is the function i want to disable ;). I know that I should expect it to crash often, but everything else work close to perfect.
[/QUOTE]

Thats just how the XFCE composite manager works. I don't think you can control its functions, and it crashes a lot me. Personally, I wouldn't advise anyone to use XFCE's composite manager, but if you want to please know that such crashes are part of its program.

---

### Post by william_nbg on 2005-10-17
First off - thanks for the how to, it written really clear and detailed.

Would really like to try this, but have one question.

When you said I would need the official nvidia drivers do you mean the ones found int the repositories, or the one from the nvidia web site??

sorry for the noob question, but just want to be sure.

---

### Post by poofyhairguy on 2005-10-17
[QUOTE=william_nbg]First off - thanks for the how to, it written really clear and detailed.

Would really like to try this, but have one question.

When you said I would need the official nvidia drivers do you mean the ones found int the repositories, or the one from the nvidia web site??

sorry for the noob question, but just want to be sure.[/QUOTE]

Both will work. I use the repo ones. I know people that do it with the newer ones installed by hand. You just need some Nvidia drivers installed.

---

### Post by phend-one on 2005-10-17
This is REALLY nice!

Thanks for sharing this!

*hugs old GeForce 4200Ti* And they told me you were useless! :cool:

---

### Post by ba5e on 2005-10-18
What a great How-to.

It works great on my pIII 733 w/nvidia FX5200.

---

### Post by poofyhairguy on 2005-10-18
[QUOTE=ba5e]What a great How-to.

It works great on my pIII 733 w/nvidia FX5200.[/QUOTE]


Works great with old machines.

---

### Post by ad0 on 2005-10-19
Can someone put some screenshots to see how that looks?

---

### Post by hesee on 2005-10-19
[QUOTE=poofyhairguy]Works great with old machines.[/QUOTE]

Any hope to get this working with my old Geforce2 mx400? processor is AMD 2600+ XP...

---

### Post by Neo40 on 2005-10-19
[QUOTE=hesee]Any hope to get this working with my old Geforce2 mx400? processor is AMD 2600+ XP...[/QUOTE]


I have a GeForce2 mx400 and it works fine. However, I find drop shadows a little bit slow. Is it my card? I don't know...

---

### Post by xingmu on 2005-10-19
The HOWTO is excellent, had no problems following it.  But the results were disappointing to me.  The "shadows" are really just a fuzzy gradient border around every window, panel, and menu.  I wouldn't really call it a shadow because it doesn't follow basic principles of physics (i.e. the shadow is on all four sides of a window??).  It was also a little overkill to have a shadow on my already semi-transparent side panel and my auto-hide mini panel.

The fade in and fade out was not bad...but it made GNOME seem a lot slower and clunkier (quite the opposite of being more responsive).  I notice the problem a lot when Alt-Tabbing between windows (which is how I switch windows all the time).

BTW, this was all on a Toshiba Tecra M2 with a GeForce FX Go 5200....cpu is...I forget...Pentium 1.6Ghz plus or minus some.

Anyways, my big question is what the original poster meant by saying that xorg is moving in a different direction than composite.  What direction?  What will be seeing for eye candy in the future?

Some screenshots:
[[IMG]http://i19.photobucket.com/albums/b179/xingmu/th_Screenshot-1.png[/IMG]](http://i19.photobucket.com/albums/b179/xingmu/Screenshot-1.png)

[[IMG]http://i19.photobucket.com/albums/b179/xingmu/th_Screenshot.png[/IMG]](http://i19.photobucket.com/albums/b179/xingmu/Screenshot.png)

---

### Post by poofyhairguy on 2005-10-19
[QUOTE=Neo40]I have a GeForce2 mx400 and it works fine. However, I find drop shadows a little bit slow. Is it my card? I don't know...[/QUOTE]


Yeah, older Nvidia cards have problems with shadows.

---

### Post by JazzCrazed on 2005-10-19
Just FYI... Things seem to work well on my Acer Aspire 3002LCi using an SiS Mirage chip! I don't know whether that's accelerating it, or whether my Sempron 2800+ is powerful enough to do it on its own (I know that driver support for SiS Mirage is lacking). Shadows run really fast, though, and the window acceleration is pleasurably noticeable. Fades are too sluggish to use, though.

Also, sometimes when I started up xcompmgr with the appropriate commands, the Gnome panels wouldn't show up, and I'd be forced to restart GDM. Since I added xcompmgr to my startup options, I haven't encountered that problem again.

Ultimately (meaning, after about an hour of straight use), I ended up turning off shadows because the panels also get shadows, and the shadows overlay all the other windows - which is annoying when I have a window maximized (the shadow is cast over the window's title bar). The disappearance of the annoying ugliness when dragging windows is welcome change, enough!

Thanks for this howto!

---

### Post by poofyhairguy on 2005-10-19
[QUOTE=JazzCrazed]Just FYI... Things seem to work well on my Acer Aspire 3002LCi using an SiS Mirage chip! I don't know whether that's accelerating it, or whether my Sempron 2800+ is powerful enough to do it on its own (I know that driver support for SiS Mirage is lacking). Shadows run really fast, though, and the window acceleration is pleasurably noticeable. Fades are too sluggish to use, though.[/QUOTE]

Its all your CPU. As I said, if you have a fast one drop shadows are fine. I'll define that better.

But unless you have smooth fades (really smooth) its being done by the CPU. Either you lack an Nvidia card, or the driver is not installed right.

Thats why I bought the Nvidia card. I only like the fades, and without and Nvidia card they won't work!

[/QUOTE]
Also, sometimes when I started up xcompmgr with the appropriate commands, the Gnome panels wouldn't show up, and I'd be forced to restart GDM. Since I added xcompmgr to my startup options, I haven't encountered that problem again.> 

Do this command next time (trust me):

[QUOTE]killall gnome-panel

> 
Ultimately (meaning, after about an hour of straight use), I ended up turning off shadows because the panels also get shadows, and the shadows overlay all the other windows - which is annoying when I have a window maximized (the shadow is cast over the window's title bar). The disappearance of the annoying ugliness when dragging windows is welcome change, enough!

Thanks for this howto!

No problem. I don't really like the drop shadows. Since xcompmgr is a hack, they do not look natural like in Vista/OSX. By KDE 3.5 I think that side will be fixed though.

---

### Post by seethru on 2005-10-20
I can't stay away from xcompmgr :/
Poofy awesome script, one bug about killall gnome-panel though is that it doesn't seem to reload everything into the tray. I had amarok, xchat, and gaim all in the tray and only gaim came back up D:

---

### Post by poofyhairguy on 2005-10-20
[QUOTE=seethru]I can't stay away from xcompmgr :/
Poofy awesome script, one bug about killall gnome-panel though is that it doesn't seem to reload everything into the tray. I had amarok, xchat, and gaim all in the tray and only gaim came back up D:[/QUOTE]


I can confirm the bug. Darn!

---

### Post by rjwood on 2005-10-20
I really like all this stuff but its just too much trouble.

I seem to remember P.H.Guy doing a thing of replacing metacity with e-17 in hoary a while back. Will you be doing another "how to" for that with breezy?

---

### Post by hesee on 2005-10-21
[QUOTE=xingmu]

Anyways, my big question is what the original poster meant by saying that xorg is moving in a different direction than composite.  What direction?  What will be seeing for eye candy in the future?
[/QUOTE]
I was wondering the same thing, is there going to be same kind of effects done by xorg itself? (don't know if this is stupid question, i'm still noob)

---

### Post by pizzach on 2005-10-21
I love the shadow effects done by xcompmgr.  I hate the fading effect.  It feel like a joke that just wastes time to me.  But I suppose that is because my Second OS is Mac OS (X). aka, I can also use Mac OS's before that....

Anywho, xcompmgr rules for useability in that respect!  The Mac OS 9 themes even without realtime shadows at least did a fake drop shadow.  A lot of Gnome themes don't and are a pain in the @ss on the eyes that way.

---

### Post by seethru on 2005-10-21
[QUOTE=hesee]I was wondering the same thing, is there going to be same kind of effects done by xorg itself? (don't know if this is stupid question, i'm still noob)[/QUOTE]
xorg 7 will have exa, which from my understanding, is built in composite.

---

### Post by hesee on 2005-10-21
[QUOTE=seethru]xorg 7 will have exa, which from my understanding, is built in composite.[/QUOTE]

I see... Does anyone happen to know if there's any time schedule for xorg7, couldn't find it from xorg website? Surely we should have impressive and stable "Vista" effects before Vista users ;)

---

### Post by poofyhairguy on 2005-10-21
[QUOTE=hesee]I see... Does anyone happen to know if there's any time schedule for xorg7, couldn't find it from xorg website? Surely we should have impressive and stable "Vista" effects before Vista users ;)[/QUOTE]


Here is info:

[http://wiki.x.org/wiki/X11R6970ReleasePlan](http://wiki.x.org/wiki/X11R6970ReleasePlan)

Remember to not get too excited. Once the foundation is in place it will take a little time for the software and drivers to catch up. I might buy a ATI 9200 just because I hate waiting (then nvidia sits on shelf, lol), and switch to KDE (of course I think KDE will use it better first).

---

### Post by poofyhairguy on 2005-10-21
[QUOTE=pizzach]I love the shadow effects done by xcompmgr.  I hate the fading effect.  It feel like a joke that just wastes time to me.  But I suppose that is because my Second OS is Mac OS (X). aka, I can also use Mac OS's before that....[/QUOTE]

Thats funny, because now when I use Apples I think "they are pretty, but they can't do the awesome fading effect my Linux box can do."

> 
Anywho, xcompmgr rules for useability in that respect!  The Mac OS 9 themes even without realtime shadows at least did a fake drop shadow.  A lot of Gnome themes don't and are a pain in the @ss on the eyes that way.

E17 has those nice fake dropshadows.

---

### Post by poofyhairguy on 2005-10-21
[QUOTE=rjwood]
I seem to remember P.H.Guy doing a thing of replacing metacity with e-17 in hoary a while back. Will you be doing another "how to" for that with breezy?[/QUOTE]

I can, but I won't be able to support it that well because I don't use that trick anymore.....because of xcompmgr. It and E17 fight worse than it and Metacity.

---

### Post by pizzach on 2005-10-21
[QUOTE=poofyhairguy]E17 has those nice fake dropshadows.[/QUOTE]
Sigh.  Reminds me.  Gotta get a new copy of e17 and check the for the newest changes.  Either that or wimp back to e16.  Got gnome all tricked out though so I'm not in as much of a rush.:p

Hehe, just noticed a bit of misunderstanding maybe.  Mac Os 8/9 basically as part of the the theme used a black lined down the left and bottom sides on the frontmost window.  It was as fake a shadow as you could get.  But it was a very good visual cue.

---

### Post by piedamaro on 2005-10-21
Nice HOWTO! However I have a couple of question on the script:

if  [[ $a = "" ]]

why do you use a double bracket? I'e read thi is only in the korn shell. Also the right way of doing a test is something like: 

if [ "$a" = "" ] 
or better 
if [ x$a = x ]

if you use [ $a = something ] it can become [ = something ] and it will generate an error because 'test' (the program linked by [ ) is expecting a binary condition.

---

### Post by pizzach on 2005-10-22
Okay, I just want to illustrate this a bit more clearly:  Notice the two pictures I have attached to this message.  Look closely at the window borders of the active and inactive windows.  The active window has a dark black drop ***shadow***.  The inactive windows also have shadows but aren't as dark.  What disappoints me about XWindows/gnome themes is that the active windows doesn't have shadows or anything the like period. It makes theme easier to disern even Mac OS 9 style.  You don't need fancy processor heavy things that crash stuff to do the job.

xcompmgr throws out some nice shadows.  But I miss the functionality of Mac OS X/9 shadows.  The formost window casts a larger shadow.  (look at the attached)  Mac OS X does the same as 9 but it isn't noticeable until you look close.  The beauty is in the details.

People understand what I'm talking about now?

Edit:  8 minutes of grammar/spelling fixes

---

### Post by joflow on 2005-10-23
[QUOTE=poofyhairguy]I can, but I won't be able to support it that well because I don't use that trick anymore.....because of xcompmgr. It and E17 fight worse than it and Metacity.[/QUOTE]


I was just about to ask if it was possible to get this working with e17+gnome.  I really like e17+gnome.  Do you recommend this over e17?  Which is prettier?

---

### Post by poofyhairguy on 2005-11-07
Ok, I was doing some research on the Gentoo Wiki and it seems that with the next release of Xorg some ATI cards (up to a 9200) will be able to get in on the fun:

> 
You can get hardware accelled Render (EXA) for 9200 and below, using X.org CVS, thus making Composite ridiculously fast and even overcome NVidia cards, cause they don't support EXA yet. This is with Open Source "radeon" driver. 

[http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency#ati-drivers_.2B_Xorg](http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency#ati-drivers_.2B_Xorg)

---

### Post by poofyhairguy on 2005-11-07
When I am wrong I can admit it, but this time I'm VERY happy to be wrong. 

Turns out that because the next Xorg (the big 7) is going to allow the card with the best open source drivers in existence (the ATI 9250's and below) to get in on the accerated Composite Manager party development in xcompmgr has started up again:

[http://xapps.freedesktop.org/release/](http://xapps.freedesktop.org/release/)

Its there. A new version released at the end of last month. Joy!

I compiled it for myself and its working fine. I can already tell its more stable. I will try to make a deb file so that other can use it too, but if you can't wait this page will tell you what to do:

[http://64.233.167.104/search?q=cache:gUCWnw7hL_4J:mandrakeusers.org/lofiversion/index.php/t18626.html+%22configure.ac:+9:+required+file+%60./%5Bconfig.h%5D.in%27+not+found%22&hl=en&client=firefox](http://64.233.167.104/search?q=cache:gUCWnw7hL_4J:mandrakeusers.org/lofiversion/index.php/t18626.html+%22configure.ac:+9:+required+file+%60./%5Bconfig.h%5D.in%27+not+found%22&hl=en&client=firefox)

And I included the xcompmgr file I compiled on my machine. Just untar the file and then use the terminal to cd to the directory that is made and then use the normal commands. I have my whole set-up changed for this new xcompmgr and I will tell an easy way to do that soon!

---

### Post by poofyhairguy on 2005-11-07
No wait, here is the post with the new xcompmgr.

---

### Post by kashms on 2005-11-07
Excellent news!!

Hope they will keep up developement so we can get some bling bling on our desktops :cool:

---

### Post by neuschnee on 2005-11-07
In my experience, xcompmgr or xcomposite in general is only really good for one thing: taking pretty screenshots and then immediately turning it off.

It's buggy as hell and even when "accelerated" is slow (try moving a big window around with drop shadows with xcompmgr with a 2ghz athlon, then do the same in OSX on an old iMac... heh).

It's not really worth it to me, at least until it is truly accelerated, unbuggy and clean like it is in OSX or (though awfully ugly) in Vista.

---

### Post by Manny C on 2005-11-07
[quote=neuschnee]In my experience, xcompmgr or xcomposite in general is only really good for one thing: taking pretty screenshots and then immediately turning it off.

It's buggy as hell and even when "accelerated" is slow (try moving a big window around with drop shadows with xcompmgr with a 2ghz athlon, then do the same in OSX on an old iMac... heh).

It's not really worth it to me, at least until it is truly accelerated, unbuggy and clean like it is in OSX or (though awfully ugly) in Vista.[/quote] 
Yep. Agree. But read poofyhairguy's initial post. Expect breakage.

---

### Post by poofyhairguy on 2005-11-07
[QUOTE=neuschnee]In my experience, xcompmgr or xcomposite in general is only really good for one thing: taking pretty screenshots and then immediately turning it off.[/QUOTE]

I use it for weeks on end. About once a week or so it might crash the xserver on me, but otherwise it works great.

> 
It's buggy as hell and even when "accelerated" is slow (try moving a big window around with drop shadows with xcompmgr with a 2ghz athlon, then do the same in OSX on an old iMac... heh).

Actually the acceration really depends on how good your video card is. I experiance less crashing and a greater overall speed with my 6600 GT compared to my 5200 FX.

And I'm hoping that the new framework that allows the ATI cards to accerate xcompmgr with EXA will be even more stable and fast. I'm willing to buy an old ATI card to find out. If thats the case.....

> 
It's not really worth it to me, at least until it is truly accelerated, unbuggy and clean like it is in OSX or (though awfully ugly) in Vista.

Have fun waiting a year or more likely two or three till its up to your standards and I hope you have the correct video card even then. 

Personally I am a desktop user so a little crashing deos not bug me especially if I can get the effects that Vista users will get late next year today.

I like an accerated desktop and I'm sick of waiting for the future. Xcompmgr might be a toy, but it a toy that is in active development and is already more usable than any other compsitor on the Linux Desktop.

---

### Post by frodon on 2005-11-07
I'm a happy xcompmgr user with a fx5200 nvidia card and like poofyhairguy i can't wait to have a composite manager without bug.
So yes there's some users who use xcompmgr all the time and enjoy using it :)

Poofy, is xcompmgr still in development or not, i'm lost ?

---

### Post by poofyhairguy on 2005-11-07
[QUOTE=frodon]I'm a happy xcompmgr user with a fx5200 nvidia card and like poofyhairguy i can't wait to have a composite manager without bug.
So yes there's some users who use xcompmgr all the time and enjoy using it :)

Poofy, is xcompmgr still in development or not, i'm lost ?[/QUOTE]

As of very recently it is. In this post there is a version I compiled. It might work if you want to try it:

[http://ubuntuforums.org/showpost.php?p=472499&postcount=48](http://ubuntuforums.org/showpost.php?p=472499&postcount=48)

Its very exciting. I thought that this was no longer a work in progress, but the new Xorg made it relevent again. 

Whats even more exiting is the thought that KDE's might get a lot better too.

---

### Post by zachtib on 2005-11-07
i have installed xcompmgr on my desktop, and i want to use it on my laptop, but not until the "cannot log out" bug is fixed.  for me, that one inconvenience isn't worth the eye candy of the composite manager, so does anyone know if the new version fixes this?

---

### Post by pizzach on 2005-11-07
[QUOTE=zachtib]i have installed xcompmgr on my desktop, and i want to use it on my laptop, but not until the "cannot log out" bug is fixed.  for me, that one inconvenience isn't worth the eye candy of the composite manager, so does anyone know if the new version fixes this?[/QUOTE]


Just tried it.  By God, it fixed the log out problem.  It's a miracle!!  WHOOHOHOHOHOHOHOH!  Now if only it wouldn't mess up my precious mplayer.  :)

---

### Post by frodon on 2005-11-07
Does someone here tried [that]("http://sourceforge.net/projects/gcompmgr/") ?

See this screenshot : [http://sourceforge.net/project/screenshots.php?group_id=140598&ssid=13855](http://sourceforge.net/project/screenshots.php?group_id=140598&ssid=13855)

---

### Post by JazzCrazed on 2005-11-07
[QUOTE=zachtib]i have installed xcompmgr on my desktop, and i want to use it on my laptop, but not until the "cannot log out" bug is fixed.  for me, that one inconvenience isn't worth the eye candy of the composite manager, so does anyone know if the new version fixes this?[/QUOTE]

I included a launcher, per the original poster's howto, for turning off and on the xcompmgr. I have to make sure it's turned off b4 i try to log off. Annoying, for sure, but I tolerate it cause I like my shadows. :)

If you do try to log out and the logout window doesn't show up because xcompmgr is still on, u can press "escape" to get your control over the desktop back. The logout window actually is there - it's just invisible. Then turn off xcompmgr, and try to logout again.

---

### Post by zachtib on 2005-11-07
[QUOTE=pizzach]Just tried it.  By God, it fixed the log out problem.  It's a miracle!!  WHOOHOHOHOHOHOHOH!  Now if only it wouldn't mess up my precious mplayer.  :)[/QUOTE]

i just built the new xcompmgr from source (running amd64 and wasnt sure the prebuilt on would work) and the logout bug still applys to me

---

### Post by pizzach on 2005-11-07
[QUOTE=zachtib]i just built the new xcompmgr from source (running amd64 and wasnt sure the prebuilt on would work) and the logout bug still applys to me[/QUOTE]

That's odd.  I build it from source too from poofyhairguy's link. (The directory expands as 1.1.3 while the actualy built version is 1.1.2.)  I'm running a Pentium M though.  Oh well.  I'm happy I can log out at least...:???:

---

### Post by zachtib on 2005-11-07
[QUOTE=pizzach]That's odd.  I build it from source too from poofyhairguy's link. (The directory expands as 1.1.3 while the actualy built version is 1.1.2.)  I'm running a Pentium M though.  Oh well.  I'm happy I can log out at least...:???:[/QUOTE]

my laptops a pentium m, but its got ati graphics, dont really think that will work well

---

### Post by pizzach on 2005-11-07
[QUOTE=zachtib]my laptops a pentium m, but its got ati graphics, dont really think that will work well[/QUOTE]

On a side note, I'm only using shadows.  I initialize xcompmgr as:
xcompmgr -cC -r 8 -l -9 -t -9 && killall gnome-panels 

Otherwise it sounds like you might be out of luck.

---

### Post by ThomThom on 2005-11-07
And this work with older ATI card, but not newer? (I have an ATI 9800)

---

### Post by ljamie82 on 2005-11-07
Well i got everything installed and it does look nice, though not to the degree i was expecting from this board. . . anyway one thing is i don't see any shadows, maybe i'll just tinker with the code some . . . it is supposed to have obvious shadow's though, right?

---

### Post by neuschnee on 2005-11-07
[QUOTE=poofyhairguy]Actually the acceration really depends on how good your video card is. I experiance less crashing and a greater overall speed with my 6600 GT compared to my 5200 FX.[/QUOTE]
In OSX with cards much less powered than these two examples (6600 GT and 5200 FX) there is no lag. Why?... because it isn't a hack, and they did it *right* from the ground up.

It's not the card's fault, it's the framework. Requiring a certain card using EXA for unlaggy drop-shadows sounds just as ridiculous as Vista requiring a DX9-capable card. OpenGL is common and works... Apple gets it. :) (Xgl is our closest equivalent.. but does anyone actually *use* it?)

[QUOTE=poofyhairguy]Have fun waiting a year or more likely two or three till its up to your standards and I hope you have the correct video card even then.[/QUOTE]
By your standards, I already have the so-called "correct" video card for using xcompmgr. Don't assume. Anyway it doesn't at all bother me that xcomp sucks... if it did I would have switched to OSX ages ago.

---

### Post by poofyhairguy on 2005-11-07
[QUOTE=ThomThom]And this work with older ATI card, but not newer? (I have an ATI 9800)[/QUOTE]

Yes. The ATI 92XX and 9000 cards have excellent open source drivers that do not come from ATI. These open source drivers are what allow the new ATI acceration to work. These card are the most power cards on the market with open specifications.

I hate to say it, but something tells me the worst situation to be in for compositing right now is to own an ATI card newer than a 9250. There are open source drivers but it seems it will be a while before they are able to fully accerate a composite manager while the open source ATI drivers and the Nvidia drivers do it today.

---

### Post by poofyhairguy on 2005-11-07
[QUOTE=zachtib]i have installed xcompmgr on my desktop, and i want to use it on my laptop, but not until the "cannot log out" bug is fixed.  for me, that one inconvenience isn't worth the eye candy of the composite manager, so does anyone know if the new version fixes this?[/QUOTE]

The new xcompmgr did not fix this bug for me, but there are ways to deal with it.

One is to follow my guide and make an "on/off" button and turn it off before logging out.

The other is to find a way to make a script that turns it off automatically when you log out.

The first solution is a good one because xcompmgr is so buggy that you want an on /off switch anyway.

---

### Post by poofyhairguy on 2005-11-07
[QUOTE=ljamie82]Well i got everything installed and it does look nice, though not to the degree i was expecting from this board. . . anyway one thing is i don't see any shadows, maybe i'll just tinker with the code some . . . it is supposed to have obvious shadow's though, right?[/QUOTE]

Not if you use my custom xcompmgr command, as I don't like shadows. They make my gdesklets look bad.

---

### Post by poofyhairguy on 2005-11-07
[QUOTE=neuschnee]In OSX with cards much less powered than these two examples (6600 GT and 5200 FX) there is no lag. Why?... because it isn't a hack, and they did it *right* from the ground up.[/QUOTE]

If you pay upper class prices you should get an upper class product. The Linux Desktop is putting together its eye candy revolution on a shoe-string budget.

Comparing the Linux desktop to OSX is a surefire way to get depressed and it does not help anyone.

> 
It's not the card's fault, it's the framework. Requiring a certain card using EXA for unlaggy drop-shadows sounds just as ridiculous as Vista requiring a DX9-capable card. OpenGL is common and works... Apple gets it. :) (Xgl is our closest equivalent.. but does anyone actually *use* it?)

You don't seem to get it. Its not the framework's fault, its not the card's fault. Its the fault of poor Linux drivers. The two best Linux drivers are Nvidia's closed one and the ATI 92xx open source one. They both work now with composite.

It has nothing to do with opengl. Having a fully developed opengl xserver (the xegl) means nothing if there are no good opengl Linux drivers to work with. Luckily it seems that as a result of the next Xorg release's effort to make the drivers independent, the open source drivers for most card can rapidly get better. If not there is always the old ATI cards or new Nvidia ones...

Again comparing to Apple is fruitless. Apple controls their hardware and has GREAT drivers for every video card in every Mac. If Linux had the same driver situation the Xegl would probably be where the effort would be focused, not on EXA. EXA was created because it the driver situation is so bad that if we had to wait for it to settle after the xorg 7.0 release to start making an accerated desktop, then Linux would not have one for two years after Vista was released. 

> 
By your standards, I already have the so-called "correct" video card for using xcompmgr. Don't assume.

My only assumption is the obvious one that unlike OSX or even Windows, desktop Linux has to care more about legacy hardware (if only because so many people use it to "save" machines the other OSes left behind) and this fact makes it so that the majority of Linux users lack the specific cards needed to have a nicely accerated desktop.

> 
 Anyway it doesn't at all bother me that xcomp sucks... if it did I would have switched to OSX ages ago.

For me the fact that xcompmgr became semi-stable is the reason why I don't own a Mac today. I'm willing to invest time and money to help develop the Linux solution (or at least help bug test it) because now that I have used an accerated desktop on my sister's Powerbook and my computer with xcompmgr turned on I can't go back.

Honestly if getting a new ATI card keeps me from buying an expensive and soon to be obsolete PPC Mac before they get the Intel ones than its money well spent. I hate waiting.

---

### Post by zachtib on 2005-11-07
[QUOTE=poofyhairguy]Yes. The ATI 92XX and 9000 cards have excellent open source drivers that do not come from ATI. These open source drivers are what allow the new ATI acceration to work. These card are the most power cards on the market with open specifications.

I hate to say it, but something tells me the worst situation to be in for compositing right now is to own an ATI card newer than a 9250. There are open source drivers but it seems it will be a while before they are able to fully accerate a composite manager while the open source ATI drivers and the Nvidia drivers do it today.[/QUOTE]

and where would i go to get these drivers (as it is, ive got great 3d acceleration on my radeon 9000 with the official drivers, if these are better, that would be great)

---

### Post by neuschnee on 2005-11-07
[QUOTE=poofyhairguy]You don't seem to get it. Its not the framework's fault, its not the card's fault. Its the fault of poor Linux drivers. The two best Linux drivers are Nvidia's closed one and the ATI 92xx open source one. They both work now with composite.

It has nothing to do with opengl. Having a fully developed opengl xserver (the xegl) means nothing if there are no good opengl Linux drivers to work with. Luckily it seems that as a result of the next Xorg release's effort to make the drivers independent, the open source drivers for most card can rapidly get better. If not there is always the old ATI cards or new Nvidia ones..[/QUOTE]
I don't understand what is so bad about Linux/X11 OpenGL drivers? How are they "poor", exactly? I've been using GL on Linux/X11 since the age of 3dfx and Matrox G200/400's... I actually prefer it to Windows in some ways. I get around the same FPS as in windows (sometimes more, sometimes less.. always near the same).

The problem IS the framework. If we had a good GL-driven framework, adding drop shadows on windows and "true" transparency would prove trivial. OSX doesn't shine because of its drivers (though you're right of course, they are excellent), but because of the display-postscript-driven framework they have used since the first version of OSX.

In Vista, everything is a vector in D3D. Same idea...

---

### Post by joflow on 2005-11-07
Yeah, I have to agree.  The graphic/video driver situation is very bad especially with ATI products.  As it stands, I have a Radeon 9500 that I can't get accelerated (even screeen savers run at 3-4 fps) and a TV Tuner (theater 550 pro) that has no driver at all and has no prospects of having linux support in the near future.  I think we (ATI users) need to email ATI and demand better linux support for their products.

---

### Post by poofyhairguy on 2005-11-07
[QUOTE=neuschnee]I don't understand what is so bad about Linux/X11 OpenGL drivers? How are they "poor", exactly?[/QUOTE]

2D acceration is slower with the official ATI drivers than with with the open source driver, even for newer cards. Yet because ATI does not open their specs the open source 3D drivers for the newer ATi cards have to reverse engineer and they are slow. So unless you have a ATI 9200 or lower you cannot get accerated 2D and 3D on the same card.

The Nvidia drivers are far better and can do Opengl work as fast as their Windows counterparts, but most cards are not Nvidia cards. Plus the Nvidia drivers are not open like the rest of the OS so its hard to make them work well together all the time.

Intel Cards have open source drivers, but onlyt recently are they getting to the point where they even get a fraction of the performance of the Windows drivers. This is bad because those cards are slow anyway.

> I've been using GL on Linux/X11 since the age of 3dfx and Matrox G200/400's... I actually prefer it to Windows in some ways. I get around the same FPS as in windows (sometimes more, sometimes less.. always near the same).

Being as good as Windows is not good enough if Vista is going to need Directx 9 cards to work well.

> The problem IS the framework. If we had a good GL-driven framework, adding drop shadows on windows and "true" transparency would prove trivial.

OSX doesn't shine because of its drivers (though you're right of course, they are excellent), but because of the display-postscript-driven framework they have used since the first version of OSX.

OSX shines because its a locked box. Apple knows everything that in there and can plan for all the possibilities. An Apple box is more like a gam console in that the developers know EXACTLY what platform they are shooting for and what people have. Thats what makes the magic (notice complaints of those who tried to hack in onto Dell laptops only to find many thigns did not work).

It comes down to drivers. Framework does not matter if you do not have the hardware support to back it up. Most Opengl acceration on the Linux desktop is done through Mesa drivers - a very poor solution but the only one Linux has for now. when this changes (after Xorg 7 brings about better drivers) the desktop can improve and a framework can be built.

There is a reason that Xcompmgr died in between last year and right now- because the developers wanted to wait for the open source drivers to be ready before they started development again.

---

### Post by pizzach on 2005-11-07
So....I guess I'm the only one who is using xcompmgr and when logging out it doesn't give the bug? :confused:  Wonder why.  I kind of feel like I won the lottery or something.  Except for not being any richer.

---

### Post by poofyhairguy on 2005-11-07
[QUOTE=pizzach]So....I guess I'm the only one who is using xcompmgr and when logging out it doesn't give the bug? :confused:  Wonder why.  I kind of feel like I won the lottery or something.  Except for not being any richer.[/QUOTE]


Be happy.

---

### Post by bunkee on 2005-11-07
I tried this with my radeon 9700 and none of the commands worked well but i did notice that when i add 

Section "Extensions"
    Option  "Composite" "Enable"
EndSection

to my xorg.conf it changes my opengl from ati 1.3.5395(X4.30-8318blah blah blah to mesa3d

not sure if that is why i'm having such poor results.

---

### Post by poofyhairguy on 2005-11-07
[QUOTE=bunkee]I tried this with my radeon 9700 and none of the commands worked well but i did notice that when i add 

Section "Extensions"
    Option  "Composite" "Enable"
EndSection

to my xorg.conf it changes my opengl from ati 1.3.5395(X4.30-8318blah blah blah to mesa3d

not sure if that is why i'm having such poor results.[/QUOTE]

Only ATI cards that are 9250's or lower have composite support.

[http://xorg.freedesktop.org/wiki/ExaStatus](http://xorg.freedesktop.org/wiki/ExaStatus)

> 
Supported: (Will be included in 6.9/7.0)- radeon (r100/r200 with Render accel, r300 core-only. May be issues in non-DRI mode, and DGA unsupported).

Only the r100/r2xx cards now have the ability to use render accel which is needed to accerate the effects.

I'm THIS close to buying a cheap ATI 9250 just to test this new driver and see hwo it works. 

The drivers for the r300 cards (aka ATI 9500's+) might be rapidly improved after Xorg 7 is officially released in Decemeber but no one knows really.

---

### Post by poofyhairguy on 2005-11-07
Because of a suggestion I just read on a mailing list, I am now playing with changing the priority of Xcompmgr to see if it crashes less.

If this turns out this helps at all I will add it to the guide. Already I can tell that the newest xcompmgr works better than before, so included a version I compiled in the first post. Just as I guessed, the developers were waiting for the ATI 92xx cards to catch up before really getting serious about composting.

Finally I edited the guide so I won't give people with newer ATI cards false hope. My recommendation to those of you with ATI cards that are 9500 series or better- if you are not a gamer sell them on Ebay while they still have value and get a compatible card. Xcompmgr is fun to play with.

---

### Post by Maverick911 on 2005-11-07
OK, so now I really would like to see these effects.I've got an ATI Radeon 9200 mobile. I edited xorg.conf, but I'm getting the following messages when i try to enable universe repo.:???:  Can anyone tell me what's wrong? Thanks

[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by pizzach on 2005-11-07
Okay.  I feel better.  I got my computer to freeze on log out just like the old days by re-enableing System>Sessions>the check if you really want to logout option.:D  I rolled back a version and it doesn't seem to have a connection to the problem now.

---

### Post by poofyhairguy on 2005-11-07
[QUOTE=Maverick911]OK, so now I really would like to see these effects.I've got an ATI Radeon 9200 mobile. I edited xorg.conf, but I'm getting the following messages when i try to enable universe repo.:???:  Can anyone tell me what's wrong? Thanks

[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)[/QUOTE]

I need to see your sources.list:

sudo gedit /etc/apt/sources.list

and post it here.

Or use the xcompmgr I provide as an attachment in the first post.

---

### Post by poofyhairguy on 2005-11-07
Even Rasterman is joining the xcompmgr party:

[http://www.mail-archive.com/enlightenment-users@lists.sourceforge.net/msg05050.html](http://www.mail-archive.com/enlightenment-users@lists.sourceforge.net/msg05050.html)

---

### Post by poofyhairguy on 2005-11-08
Ok, the stability of the new xcompmgr has driven me to think about using drop shadows again. So after much tweaking I have created an awesome setting:

xcompmgr -fF -I-.002 -O-.003 -D6 -cC -t-3 -l-5 -r5

That one gives the fade like I love it, plus it has drop shadows that look better overall. The main thing that I did not like about the drop shadows is how they looked on drop down menus such as the Firefox url box or the Applications menu. The shadows are way less wild now. This command's drop shadows are what I came up with after messing with a Mac all day- its the best I can do. 

I hope you enjoy this new super setting, I know I will.

---

### Post by poofyhairguy on 2005-11-08
Ok, final update of the night. I have added extra steps to help those with cards that do not accerate xcompmgr.

Someone please test this for me so I can get an idea of how fast a CPU you need to do drop shadows.

---

### Post by rjwood on 2005-11-08
hi p.h.g! Thanks for all the updates and investigating. I kind-a follow you around when it comes to most eye-candy stuff. Everyone is so helpful and fun.
I just finished reading kryle's window manager thread and I have read in the past where you have expressed some disappointment with metacity. What do you use as a wm? I have xcompmgr installed and running from your thread info and 23megs 'how to' on terminal transparancy. Not much else, just like to fool around with my ubuntu so as to learn a little. I have read some good things about sawfish. Does that interfere with all the eye candy I have? I have tried e-17 but not quite ready for it yet until either I or it is more developed. Thanks in advance.

---

### Post by Maverick911 on 2005-11-08
[QUOTE=poofyhairguy]I need to see your sources.list:

sudo gedit /etc/apt/sources.list

and post it here.

Or use the xcompmgr I provide as an attachment in the first post.[/QUOTE]

Thanks for the reply. Here is my sources.list
```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free

deb http://wine.sourceforge.net/apt/ binary/


```

Thanks again.

---

### Post by rjwood on 2005-11-08
Also I have included the newest xcompmgr that I personally compiled. All you (should) have to do in untar the file into....say your home folder...and the use the "cd" command to get into the fold made then use all of the xcompmgr commands as I indicated above.

Should I remove the existing version before I begin using this new one?

---

### Post by poofyhairguy on 2005-11-08
[QUOTE=rjwood]hi p.h.g! Thanks for all the updates and investigating. I kind-a follow you around when it comes to most eye-candy stuff. Everyone is so helpful and fun.
I just finished reading kryle's window manager thread and I have read in the past where you have expressed some disappointment with metacity. What do you use as a wm? [/QUOTE]

Honestly I use Metacity because I find the version that comes with Breezy is the most compatible with xcompmgr. The version in Hoary was compiled with its worthless compositor enabled, but that is not the case for Breezy.

---

### Post by poofyhairguy on 2005-11-08
```
deb http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free

deb http://wine.sourceforge.net/apt/ binary/


```

See if that works. Be sure to do a 

> sudo apt-get update

---

### Post by poofyhairguy on 2005-11-08
[QUOTE=rjwood]Also I have included the newest xcompmgr that I personally compiled. All you (should) have to do in untar the file into....say your home folder...and the use the "cd" command to get into the fold made then use all of the xcompmgr commands as I indicated above.

Should I remove the existing version before I begin using this new one?[/QUOTE]

I haven't. But I did replace the old one with the new one by copying it to the 

/usr/bin/

folder using

> gksudo nautilus

---

### Post by 23meg on 2005-11-08
I still have the logout bug with the new version as well. I'll report about overall stability a while later. Btw, my favorite setting is ```
-cfF -D9 -r14 -O 0.02 -I 0.040
```

---

### Post by poofyhairguy on 2005-11-09
[QUOTE=23meg]I still have the logout bug with the new version as well. I'll report about overall stability a while later. Btw, my favorite setting is ```
-cfF -D9 -r14 -O 0.02 -I 0.040
```[/QUOTE]


The fade on yours (I might steal that one day) is nice, but the drop shadows are crazy.

---

### Post by 23meg on 2005-11-11
Right, the shadows may be a bit big but they look good to me on a high resolution display. By the way, I've only had one crash with the new xcompmgr in more than 48 hours, which is a big improvement over the old one. And I did all sorts of crazy things such as resizing the gnome panel, dragging and dropping files onto the bmp playlist, launching totem and switching to virtual terminals ;)

---

### Post by poofyhairguy on 2005-11-11
[QUOTE=23meg]Right, the shadows may be a bit big but they look good to me on a high resolution display. By the way, I've only had one crash with the new xcompmgr in more than 48 hours, which is a big improvement over the old one. And I did all sorts of crazy things such as resizing the gnome panel, dragging and dropping files onto the bmp playlist, launching totem and switching to virtual terminals ;)[/QUOTE]

I can only make it crash if I drag a playing video file (in Totem) under my translucent Gnome panels. Then it hard crashes.

Otherwise stable.

---

### Post by MetalMusicAddict on 2005-11-11
I have a couple of questions. 

1st my stats:
Ubuntu
Dell Inspiron 2200 with onboard GFX
Celeron 1.4
786megs memory
**xcompmgr -cC -t-2 -l-3 -r3 -o.35 -f -D3** is the command I use.
Using xcompmgr from repos

Heres a screenshot of what it currently looks like. 
[[IMG]http://img80.imageshack.us/img80/930/screenshot9in.th.png[/IMG]](http://img80.imageshack.us/img80/930/screenshot9in.png)
Very minimal shadows. Just enough to give depth.

1. Can you exclude apps from xcompmgr? ie: gDesklets
2. When I 1st boot it takes 2 mins for my session apps to come up after xcompmgr is loaded. Any way to speed this up?
3. On my nVidia system I get artifacts on the desktop. They vanish if I move a window over the area to refresh it. Ever seen this?
4. Can I make **xcompmgr -cC -t-2 -l-3 -r3 -o.35 -f -D3** into **xcompmgr -cC -t2 -l3 -r3 -o.35 -f -D3** and still work?

Great job on this man. Thanx.

---

### Post by tipi on 2005-11-12
anyone could help me , i tried doing this vista like thing 
and now at boot i get error "starting x server failed, possible ....
x server now dissabled, restart gdm when all is reconfigured"

and than it get's to a command line

how do i reset all to default from this command line?

---

### Post by 23meg on 2005-11-12
MetalMusicAddict:

1. No, but IIRC gDesklets had a translucency option in its configuration; disabling that may help.
2. Play with the order setting or launch xcompmgr manually after session startup
3. Seen it, but no longer seeing it with the latest version except some slider artifacts in totem.
4. Try it; if it works it works.

---

### Post by 23meg on 2005-11-12
[QUOTE=tipi]
how do i reset all to default from this command line?[/QUOTE]
```
sudo nano /etc/X11/xorg.conf
```

remove the following section 

```
Section "Extensions"
	Option	"Composite" "Enable"
EndSection
```

hit ctrl+x, and then y.

---

### Post by Biased turkey on 2005-11-12
Merci a lot for that HowTo Poofyhairguy.
Just followed the instructions on page 1 of the thread and got nice shadows and transparency with my xfce4 desktop.
Later today I'll try it on my gnome desktop after installing xcompmgr then I'll do it on my Gentoo KDE distro too.
Now that I get the composite manager installed and running, could someone please be kind enough to tell me how to use that feature ?
So my question is :
How do I adjust the transparency level in xfce4 windows ?
Any URL, tip , info or R.T.F.M.  :) advise is welcome.

Just tried it with gnome:
sudo apt-get install xcompmgr transset
So far, so good.
Maybe I'll encounter some bug when running some specific application.
And yes, I installed that feature on Gentoo ( 64 bits version ) too.
Ubuntu and Gentoo rock

---

### Post by mikko.ohtamaa on 2005-11-13
I have an old Dell Inspiron 5000e laptop with ATI Rage Mobility M3 display card (16 mb memory). Though this card doesn't have enough muscles (or it is a driver problem) to run composite manager (tested it!) here is an useful hint.

This laptop has 1400x1050 LCD screen. By default, Ubuntu runs it in 32-bit colors mode without direct rendering mode enabled. Direct rendering speeds up window handling a lot.

The display card doesn't have enough video memory to run direct rendering in 1400x1050x32. You must drop color depth to 16 bit by modifying your /etc/X11/xorg.conf:

> 

Section "Device"
        Identifier      "ATI Technologies, Inc. Rage Mobility M3 (AGP)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option "AccelMethod" "EXA" #  doesn't work with Mobility M3
        Option "AGPMode" "4"
        Option "EnablePageFlip" "true"
        Option "DDCMode" # doesn't work with Mobility M3
        Option "RenderAccel" "true" # doesn't work
        Option "SubPixelOrder" "NONE" # doesn't work
        Option "ColorTiling" "false" # doesn't work
EndSection

...

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Rage Mobility M3 (AGP)"
        Monitor         "Generic Monitor"
        DefaultDepth    16 *** here***
        SubSection "Display"

...




If direct rendering is enabled you should see the following line in /var/log/Xorg.0.log:

> 
(II) R128(0): Direct rendering enabled


---

### Post by 23meg on 2005-11-14
[QUOTE=Biased turkey] 
How do I adjust the transparency level in xfce4 windows ?
 [/QUOTE]
Tried transset? I'm not sure if it conflicts with XFCE's composite manager but trying wouldn't hurt; type "transset 0.5", click a window and see what it does.

By the way, here comes my new faster, less buggy favorite with which I've had no crashes: ```
-fF -n -D9 -r14 -O 0.05 -I 0.075
```

No more shadows, fast fades, translucency.

---

### Post by poofyhairguy on 2005-11-14
[QUOTE=MetalMusicAddict]
1. Can you exclude apps from xcompmgr? ie: gDesklets[/QUOTE]

I wish. Good point. I like the shadow on many of my desklets though.

> 
2. When I 1st boot it takes 2 mins for my session apps to come up after xcompmgr is loaded. Any way to speed this up?

What order do you run it in?

> 
3. On my nVidia system I get artifacts on the desktop. They vanish if I move a window over the area to refresh it. Ever seen this?

Yes. And I get weird scrolling mess ups too. Its part of it. Worth it for me because I have less outright crashes.

---

### Post by MetalMusicAddict on 2005-11-14
[QUOTE=poofyhairguy]I wish. Good point. I like the shadow on many of my desklets though.[/QUOTE]
Weird thing is shadows appear around the desklets screengrab which is sometimes well away from the desklet. ie: StarterBar. Oh well.
> What order do you run it in?
41. Like the guide says. Should I go higher or lower?

I see a new xcompmgr mentioned. Im having trouble finding it to download. Is it a .deb or source?

---

### Post by 23meg on 2005-11-14
It's a source but there's also a binary in the package as well. I easily built it from source and checkinstalled it, no extra dependencies.

---

### Post by poofyhairguy on 2005-11-16
[QUOTE=MetalMusicAddict]
I see a new xcompmgr mentioned. Im having trouble finding it to download. Is it a .deb or source?[/QUOTE]

Its compiled in a zip file as an attachment in the first post. Extract it somewhere, then cd into that folder when you use the commands.

---

### Post by fabs0028 on 2005-11-16
hello
well i build the new version easily with checkinstall for my ubuntu64.
It works pretty great.

I still got the log out problem as everybody.
As previously said, xcompmgr hangs my sessions start-up programs for about a minute.

Anyway it is pretty great :)

---

### Post by frodon on 2005-11-16
I have got the same problem, xcompmgr hangs my session start-up for about 3 minutes if i add it in the session start-up programs.
So i removed it from the sessions start-up programs to solve the problem.

Maybe it could be added in the bug list.

---

### Post by maxtreiber on 2005-11-16
If i would have a R100/R2XX ati card, i still could not use those new EXA acceleration thinks, because dapper is still using xorg 6.8.2, right ?
How long do we have to wait for 7.0 ?
or does someone have experimental cvs packages around ? Or just binaries ?
Does 7.0 help for >R300 cards, too ?

---

### Post by poofyhairguy on 2005-11-16
[QUOTE=maxtreiber]If i would have a R100/R2XX ati card, i still could not use those new EXA acceleration thinks, because dapper is still using xorg 6.8.2, right ?
How long do we have to wait for 7.0 ?
or does someone have experimental cvs packages around ? Or just binaries ?[/QUOTE]

Eventually it will be in Dapper I am sure. Till then we wait I guess.

> 
Does 7.0 help for >R300 cards, too ?

Kinda. No acceration though, just compatibility.

---

### Post by maxtreiber on 2005-11-17
just tried it out with x.org CVS.
Followed instructions from:
[http://wiki.x.org/wiki/CvsPage#head-f76fe9878bbeadc8b6541cf7e23bdb14ad876d2d](http://wiki.x.org/wiki/CvsPage#head-f76fe9878bbeadc8b6541cf7e23bdb14ad876d2d)
... very easy and straigtforward.
And with my ATI 9250 composite just works perfectly.
And not only that: Xv, TV-Overlay, everything, just perfect,
Thanks!

---

### Post by pxgray on 2005-11-17
This thread is ridiculously long, so I didn't parse the whole thing looking for it, but I thought I'd at least mention that for me, turning on xcompmgr broke Flash in Firefox and caused it to crash every time a page with Flash was loaded.  I have an NVidia card and was using the recommended command from the HOWTO.

That being said I had to turn xcompmgr off ultimately because it was so unstable on my system.  The system would crash or the Xserver would restart at the most random and inopportune times.  Having the drop shadow effect was cool, but not cool enough to risk me putting my fist through the monitor because the paper I was typing was completely lost.  I can't wait until this is more stable, but for now I'm going to have to leave it off.

---

### Post by maxtreiber on 2005-11-17
Me again :)
I was amazed of the idea to have only the current active window without opacity and all the others transparent because i use the "Select windows when mouse moves over them" option in the gnome Window Preferences.
Using this, i can work in one window and if i want to see whats behind in another, i just move the mouse over it and can look through it :)
anyways, i wrote a small C programm to do exactly this:

[http://81.169.175.95/transd.c](http://81.169.175.95/transd.c)

compile and run with:

gcc transd.c -o transd -lX11 && while true; do ./transd; done

its very badly programmed (most of the code is stolen) and needs a lot of values tweaked, but please try it out and tell me what you think!

---

### Post by Chrissss on 2005-11-17
@maxtreiber

Yes, indeed, that little programm is nice :)

It leads into the right direction!

---

### Post by 23meg on 2005-11-18
Does everyone experience Xorg using an average of twice / three times the CPU cycles it normally does when using composite? Does this mean composite is utilizing the GPU only marginally at the current state of things?

---

### Post by oobuntoo on 2005-11-19
Does anyone get "jiggling" artifacts on left and right edges of window when dragging it from side to side. This happens on my system with geforce 6600gt and 1.6ghz athlon xp using "nvidia" driver. It happens with or without shadow and transparency turned on. It's quite annoying. The strange thing is that it only  happen when dragging window horizontally, but not vertically.

---

### Post by 23meg on 2005-11-19
[QUOTE=oobuntoo]Does anyone get "jiggling" artifacts on left and right edges of window when dragging it from side to side. This happens on my system with geforce 6600gt and 1.6ghz athlon xp using "nvidia" driver. It happens with or without shadow and transparency turned on. It's quite annoying. The strange thing is that it only  happen when dragging window horizontally, but not vertically.[/QUOTE]
I have it on my laptop with a Geforce Go6200. It happens without xcompmgr as well, unfortunately. I can't pinpoint what it is; bad vertical refresh rates shouldn't matter much on LCDs but this is quite noticeable.

---

### Post by poofyhairguy on 2005-11-19
[QUOTE=pxgray]This thread is ridiculously long, so I didn't parse the whole thing looking for it, but I thought I'd at least mention that for me, turning on xcompmgr broke Flash in Firefox and caused it to crash every time a page with Flash was loaded.  I have an NVidia card and was using the recommended command from the HOWTO.

That being said I had to turn xcompmgr off ultimately because it was so unstable on my system.  The system would crash or the Xserver would restart at the most random and inopportune times.  Having the drop shadow effect was cool, but not cool enough to risk me putting my fist through the monitor because the paper I was typing was completely lost.  I can't wait until this is more stable, but for now I'm going to have to leave it off.[/QUOTE]

What's your hardware? It would help to know. Flash works fine for me, but I too have experianced crashes that has lost my work. 

I hope my warning to everyone early on was clear- xcompmgr is buggy. No way around it. I hope by this time next year any of the compositors are stable enough to use full time.

---

### Post by poofyhairguy on 2005-11-19
[QUOTE=23meg]Does everyone experience Xorg using an average of twice / three times the CPU cycles it normally does when using composite? Does this mean composite is utilizing the GPU only marginally at the current state of things?[/QUOTE]

That means the current acceration architexture sucks. Nvidia rushed out their competition to EXA- thats what we are all using. When EXA is fully developed (say 2007) these problems will be a memory.

---

### Post by poofyhairguy on 2005-11-19
[QUOTE=oobuntoo]Does anyone get "jiggling" artifacts on left and right edges of window when dragging it from side to side. This happens on my system with geforce 6600gt and 1.6ghz athlon xp using "nvidia" driver. It happens with or without shadow and transparency turned on. It's quite annoying. The strange thing is that it only  happen when dragging window horizontally, but not vertically.[/QUOTE]

Yep. Even without xcompgr it will do that. In fact, the only system I know that doesn't is OSX's system. Thats because they built in from the ground up to make it SEEM as responsive as possible.

That problem is part xdamage and part buffering problems. I honestly don't think it will be fixed till we moved to Xegl in two or three years.

---

### Post by varunus on 2005-11-19
For all who are having flash problems:

I found a trick on the gentoo forums (*gasp*) on how to fix these firefox crashes.  (All composite effects still work with firefox and flash if you do this, don't worry.)  Try this with any program you think may be having problems.

First, open up your firefox launcher file with the following:
```
sudo gedit /usr/bin/firefox
```

Find the part that looks like this:
```
##
## Variables
##
MOZ_DIST_BIN="/usr/lib/mozilla-firefox"
MOZ_PROGRAM="/usr/lib/mozilla-firefox/firefox-bin"
```

Add a line, making it look like this:
```
##
## Variables
##
##Added for composite extension to work
export XLIB_SKIP_ARGB_VISUALS=1
MOZ_DIST_BIN="/usr/lib/mozilla-firefox"
MOZ_PROGRAM="/usr/lib/mozilla-firefox/firefox-bin"

```

Flash will no longer have any issues.  This makes firefox ignore the extra alpha channel that xcompmgr gives it for color.  Because the application itself doesn't do anything with the alpha channel, all of the effects still work, and flash will no longer complain.

---

### Post by poofyhairguy on 2005-11-19
[QUOTE=varunus]For all who are having flash problems:

I found a trick on the gentoo forums (*gasp*) on how to fix these firefox crashes.  (All composite effects still work with firefox and flash if you do this, don't worry.)  Try this with any program you think may be having problems.

First, open up your firefox launcher file with the following:
```
sudo gedit /usr/bin/firefox
```

Find the part that looks like this:
```
##
## Variables
##
MOZ_DIST_BIN="/usr/lib/mozilla-firefox"
MOZ_PROGRAM="/usr/lib/mozilla-firefox/firefox-bin"
```

Add a line, making it look like this:
```
##
## Variables
##
##Added for composite extension to work
export XLIB_SKIP_ARGB_VISUALS=1
MOZ_DIST_BIN="/usr/lib/mozilla-firefox"
MOZ_PROGRAM="/usr/lib/mozilla-firefox/firefox-bin"

```

Flash will no longer have any issues.  This makes firefox ignore the extra alpha channel that xcompmgr gives it for color.  Because the application itself doesn't do anything with the alpha channel, all of the effects still work, and flash will no longer complain.[/QUOTE]


Cool, added to main guide. 

By the way, I have gotten a GUI for Xcompmgr to work in Ubuntu. I will make a NEW guide for that sometime next week.

---

### Post by seraphim on 2005-11-20
1.: thanks for all your great work phg! :)

2.: my hardware: athlon 1700+
                         geforce 6800

the cpu has got a lot of work...what exactly is generated by the gpu?
when i change transparency or a window is fading, the cpu is used. 
the nvidia-driver should be installed correctly, at least glxinfo returns nvidia and games are working ;) .

so is there something i can do to lower the cpu-usage?

---

### Post by fabs0028 on 2005-11-20
Hello everybody
Well it seems i have some problems with composite.

Since some days i noticed i had problemes with glx and composite ... glxinfo or a xscreensaver with opengl made my X server crash and restart so i disabled glx and now it works fine.
I noticed that it produced that line in /var/log/syslog. gdm_slave_xioerror_handler : erreur X fatale - Redémarrage de :0
I 'd like to know if i could find a X log to see what is the error of X but until now i didn't find anything interesting.

I also  have an other problem : after a long period of use of Xorg with xcompmgr, the server become really slow and take all the cpu and the memory and is slow as hell.
The speed come back to normal if i quit and relaunch xcompmgr but the memory use doesn't decrease.
For example now Xorg uses 427mo of RES memory as shown in top.

For the glx problem i'll try 7667 nvidia drivers instead of the 7676 maybe it will be better.

---

### Post by poofyhairguy on 2005-11-20
> **seraphim]
the cpu has got a lot of work...what exactly is generated by the gpu?
when i change transparency or a window is fading, the cpu is used. 
the nvidia-driver should be installed correctly, at least glxinfo returns nvidia and games are working  said:**
> 

If you want to see how much work the GPU is doing, take away the "renderaccel" line in the xorg.conf and try to use Xcompmgr. Even on the fastest machines I can't get the "fading trick" to be usuable. 

Of course, if it makes no difference then something is wrong with your set up beforehand.

[QUOTE]so is there something i can do to lower the cpu-usage?

Not really. We are really riding on the edge of the knife with this stuff. When EXA is mature (and when Nvidia switches over to EXA like they now say they will) then hopefully less CPU will be used. Till then (I say....6 months from now if we are lucky?) we have to deal with what we have. 

Personally I'm going to cheat. I'm buying an AMD 3800 x2 dual core processor so that one of the cores can handle the Xcompmgr CPU usage while the other handles my applications. I know this solution is not practical to all (and honestly I have been waiting for the processors to come out for the past couple years for an upgrade, so its not ALL about xcompmgr), but the other alternative is waiting.

As soon as I can find a way to benchmark the ATI cards I will see if their EXA is better when it comes to CPU usage then the Nvidia solution.

---

### Post by poofyhairguy on 2005-11-20
[QUOTE=fabs0028]Hello everybody
Well it seems i have some problems with composite.[/QUOTE]

Thats the state it in now.

> 
I also  have an other problem : after a long period of use of Xorg with xcompmgr, the server become really slow and take all the cpu and the memory and is slow as hell.
The speed come back to normal if i quit and relaunch xcompmgr but the memory use doesn't decrease.
For example now Xorg uses 427mo of RES memory as shown in top.


This has bugged me too. The best answer I have found comes from Rasterman ( maker of E17). He thinks that when the video card runs out of its own RAM is when the slowdown occurs and it starts to eat into system RAM. Apparently the "fading trick" causes RAM leekage, but since I am not a leet Xserver hacker I cannot fix the problem.

The good thing is that after a year of sitting on the shelf, Xcompmgr is getting love from those who actually can fix the thing. Now that EXA exists all of the awesome people hacking on that framework are using xcompmgr to do their testing. I hope this will drive them to kill the bugs in Xcompmgr as they kill the bugs in EXA/Xorg.

In the long run xcompmgr is not a solution. Its kinda just a "proof of concept" that people like me who are tired of waiting for Xorg to catch up to the other OSes in this matter are using WAY beyond what it was ever intended to do. I hate waiting. Based on my research, here is a timeline for when stuff will happen that is more than toys. Of course this is just my opinion/ prediction and I am not part of any xserver or distro development team so I could be way off. But here is my best shot:

December 2005 -Xorg 7 comes. With it comes nice EXA and almost stable composite for the ATI 92xx or less ATI cards. Also stimulates development of Xserver drivers.

Spring 2006 - (hopefully) EXA will be hammered on to the point where it is stable for ATI cards (up to 92xx) and Intel Graphics cards (after ATI). It seems thats what all of the EXA developers are using. I also hope (kinda for my own sake) that this is when the Nvidia Driver Team (who is AWESOME when it comes to drivers - they made something like EXA before EXA even had a name and we are all using it for xcompmgr) will release new Xorg drivers with EXA support or more stable whatever they call that copy of EXA they have made.

Summer/Fall 2006- KDE 4 will (hopefully) bring with it a STABLE Composite Manager built in when it is released. Hopefully the chips that are labled work in progress have some sort of EXA accerateion:

[http://xorg.freedesktop.org/wiki/ExaStatus](http://xorg.freedesktop.org/wiki/ExaStatus)

And by then the ATI 92xx's have what we can call "the first stable composite set up on the Linux desktop." Maybe also by this time ATI will release drivers for newer ATI cards with EXA, but I would not hold my breath. Also maybe XFCE will have a stable compsitor.....who knows about that one.

This is when the Cairo themes will come flooding in I hope.

Spring 2007 - Xegl gets to a medium usuable state where people like me are using it despite some crashing (aka the situation with Xcompmgr now). Xorg drivers for many cards have developed to the point where some distros (maybe even a major one.....maybe) turns on composite by default. I hope by this point the Linux desktop can at least SEEM LIKE its at the state of the OSX desktop today.

If we are lucky this will be when Gnome adds its Luminocity compositor to Metacity, but I would not hold my breath.

Summer/ Fall 2007 - If not in spring then this is when Gnome will add Luminocitiness I hope (or just give up the ghost to KDE because it will have compositer for years by then). ATI releases the specs for all the 9800 and below cards so that new stable drivers with EXA can be made for them (kinda a dream but possible). By this point the possibilites for composite will be mature (as in more than fading tricks and such- I want a stable Expose copy!)

Spring 2008 and beyond - Xegl is stable enough many can use it full time (this might be only a dream but please let me have it or I won't be able to hold off on buying a Mac till then). The Looking Glass Project emerges in a mature state and blows the OS using public away. The xserver reaches a point where its comparible to what MS offers by that point and begins to pull out in front.

Dancing in the streets.

---

### Post by Paulus on 2005-11-20
[quote=poofyhairguy]

Spring 2008 and beyond - Xegl is stable enough many can use it full time (this might be only a dream but please let me have it or I won't be able to hold off on buying a Mac till then). The Looking Glass Project emerges in a mature state and blows the OS using public away. The xserver reaches a point where its comparible to what MS offers by that point and begins to pull out in front.

Dancing in the streets.[/quote]

:KS  Thats what i'm talking about!  Looks like there's a great future ahead, just got to keep waiting i guess!  I can't see M$ releasing another version of windows before Xegl is stable, the time linux can step ahead (if not before(or already?- being free an' all)).

btw: respect ++ for all the research and hard work u have put in poofyhairguy!

---

### Post by poofyhairguy on 2005-11-20
[QUOTE=Paulus]:KS  Thats what i'm talking about!  Looks like there's a great future ahead, just got to keep waiting i guess! [/QUOTE]

I once read that "the Linux desktop is a side effect of the Linux server." The state of the xserver when the Xorg fork happened pretty much proves this point. At that time it could draw things on most screens- thats all a server needs to do (if that much). So it will take a while to move from that to a modern desktop. Drivers have to catch up. Window managers have to catch up. The concept that no modern (as in post 92xx) cards have open drivers that can do the job has to be dealt with (that will be a hard bridge to cross for many OSS fans). Opengl has to be evaluated for its effectiveness. Computer need to get more powerful to move up the baseline (Linux HAS to be able to run on older machines unlike MS where their "advances" force you to throw your old machine in the trash).

Yet despite the challenges its a bright future.

> 
btw: respect ++ for all the research and hard work u have put in poofyhairguy!

Thanks. I try my best.

---

### Post by TimmyJ on 2005-11-21
great little prediction timeline poofyhairguy :-) One thing I think should be at least mentioned is the Open Graphics card project though. They have been making some great progress lately (In fact they even mentioned that getting a card for sale out by the end of the year is a possiblity) and I'm real excited to see where it takes us!!

Read all about it here:
[http://kerneltrap.org/node/5743](http://kerneltrap.org/node/5743)

---

### Post by poofyhairguy on 2005-11-21
[QUOTE=TimmyJ]great little prediction timeline poofyhairguy :-) One thing I think should be at least mentioned is the Open Graphics card project though. They have been making some great progress lately (In fact they even mentioned that getting a card for sale out by the end of the year is a possiblity) and I'm real excited to see where it takes us!!
[/QUOTE]

I have kept up with it and I wish them luck, but until they can beat an ATI 92xx (the current high water mark for OSS graphics) I am a little skeptical.

---

### Post by flange on 2005-11-21
[QUOTE=poofyhairguy]I have kept up with it and I wish them luck, but until they can beat an ATI 92xx (the current high water mark for OSS graphics) I am a little skeptical.[/QUOTE]

This frustrates me.

Desktop Linux is a small market, no doubt, but here's what I see happening.  For a long time now, Nvidia has released closed source drivers for Linux users.  Maybe they are intended for graphics professionals, but whatever, Nvidia makes them available to all of us.  I personally chose an Nvidia-based video card for the sole reason that Nvidia provided good Linux drivers.  Many of us reward Nvidia with our business for their support of the platform we prefer to work on.

Now, because ATI has chosen not to provide an equal level of support for their customers, a growing demand for Linux drivers for ATI cards is left unfilled.  Open source developers are currently working hard to fill that void.  Nothing personal against an ATI video card owners (I'm one too, with my iBook G4), but I wish the OSS devs wouldn't do it.

If OSS devs succeed in making drivers that work with X.org in a way that is superior to what Nvidia is able to do, then I think demand among Linux users will shift away from Nvidia hardware, and towards ATI hardware.  I'm not a zealot for Nvidia, but I don't feel that ATI should be rewarded with more hardware sales (and likewise Nvidia punished), when they declined to support Linux users from the beginning.

---

### Post by ace2005 on 2005-11-21
> I also have an other problem : after a long period of use of Xorg with xcompmgr, the server become really slow and take all the cpu and the memory and is slow as hell.
The speed come back to normal if i quit and relaunch xcompmgr but the memory use doesn't decrease.
For example now Xorg uses 427mo of RES memory as shown in top.

Its caused by shadows, turn them off and it runs fine :)

---

### Post by poofyhairguy on 2005-11-21
[QUOTE=flange]This frustrates me.

Desktop Linux is a small market, no doubt, but here's what I see happening.  For a long time now, Nvidia has released closed source drivers for Linux users.  Maybe they are intended for graphics professionals, but whatever, Nvidia makes them available to all of us.  I personally chose an Nvidia-based video card for the sole reason that Nvidia provided good Linux drivers.  Many of us reward Nvidia with our business for their support of the platform we prefer to work on.

Now, because ATI has chosen not to provide an equal level of support for their customers, a growing demand for Linux drivers for ATI cards is left unfilled.  Open source developers are currently working hard to fill that void.  Nothing personal against an ATI video card owners (I'm one too, with my iBook G4), but I wish the OSS devs wouldn't do it.

If OSS devs succeed in making drivers that work with X.org in a way that is superior to what Nvidia is able to do, then I think demand among Linux users will shift away from Nvidia hardware, and towards ATI hardware.  I'm not a zealot for Nvidia, but I don't feel that ATI should be rewarded with more hardware sales (and likewise Nvidia punished), when they declined to support Linux users from the beginning.[/QUOTE]

A few comments on This:

1. ATI is not all evil in this respect. In fact, the reason I have mentioned the ATI 92xx cards so many times in this thread is because its an example of where ATI does not suck. ATI released the specs for all of their cards that are  of the 92xx series or lower. That means that for all these cards (including the medium powerful 8500) ATI gave the OSS community what they want the MOST from card makers- just the specs. In fact, without the 9200 it would be IMPOSSIBLE for the Xorg developers to make a mature framework (like XGL) because only with the 9200's drivers can they sufficiently bug test. The OSX developers get full access to the specs of the cards they ship and thats part of the reason that OS's GUI framework kicks ass - they can get to the bottom of problems. If we only had the Nvidia cards no one would ever know if some new bug was due to their closed drivers or due to the open code- there can be no process of elimination. The second most powerful set of cards with open drivers is the weak Intel intergrated cards- bleh. The entire framework is being built on the assumption that people have the 92xx card at first because otherwise NO progress could be made.

2. For many in the open source community Nvidia's closed drivers are almost worse than no drivers at all (because a lack of drivers would drive development to reverse engineer these cards to have open soruce drivers). Just from a pratical standpoint, its kinda is cool that with a 9200 Ubuntu gives you the best drivers possible out of the box while if you have Nvidia cards you have to drop to the command line to get them to work. Plus the Nvidia drivers introduce all kinds of hacks to the Xorg.conf file that makes it so that it would be almost impossible to make a decent GUI to configure that thing for all users (which is something that is really missing on the Linux desktop). For example- on my 6600 GT I added many things to my Xorg.conf to get Xinerama-ish dual screen support that are WAY different from how to get Xinerama on every other driver out there (including the closed source ATI one). For a lot of OSS people, just giving the community drivers is not enough. Xcompmgr has been accerated by the Nvidia drivers for almost a year, but development has not happened since JANUARY because those in charge did not want to(and could not) build a eye candy framework on top of these closed drivers. I might be wrong, but I'm sure there is at least one big Xserver developer that if he/she had to pick between a wonderful GUI framework built on closed drivers (Vista and OSX style) and the the current very ugly implementation build on barely working open drivers they would pick the second option. Some people have REALLY big hold ups about this open source thing.

3. Many people already have newer ATI cards when they get into open operating systems. Whats wrong with these people reverse engineering the cards to make hardware they have work? Thats how SOOOO many things in Linux get their drivers, but few people ever comment on why reverse engineering that promise controller card is bad. Whats the real difference there?

4. How good are Nvidia's PowerPC drivers for Linux? Or Nvidia's Itanium drivers for Linux? Open drivers are needed so that hardware support is availible on every supported Linux desktop system.

That said I have an Nvidia card now. But if next year the 92xx gives me the best eye candy I will buy one of them. My decision won't hurt Nvidia that much as their emphasis on the Linux side is to sell high end cards to Hollywood to make animated movies about small, cute animals, not to get the support of the average Linux desktop user. We are still too small of a market.

---

### Post by didit on 2005-11-26
hai poohfy, i have ati m9. Several days ago i upgraded XOrg.I can confirm that composite with exa enabled goes pretty well. Thanks for a nice howto :)

---

### Post by MetalMusicAddict on 2005-11-26
[QUOTE=poofyhairguy]If you want xcompgr to start when Gnome starts, the go to “System, Preferences, Sessions.” Click the last tab called “Startup Programs.” Click “Add.” Type in what command you liked best or worked best for you. Then for order pick “41” Then click “close,” log out and log back in.[/QUOTE]
For me this made it take *forever* for everything to start. 40 was perfect for the 3 PCs I use xcompmgr on. Everything started right up like xcompmgr wasnt running. 

I forgot exactly the GFX card chipset thats in my Dell Inspiron 2200 (945 I think) but Im using the i810 driver. If that helps anyone. My settings for that card: **-cC -t-2 -l-3 -r3 -o.35 -f -D3 **

---

### Post by poofyhairguy on 2005-11-27
[QUOTE=MetalMusicAddict]For me this made it take *forever* for everything to start. 40 was perfect for the 3 PCs I use xcompmgr on. Everything started right up like xcompmgr wasnt running. [/QUOTE]

I had troubles with 40. The number I picked as based on when other things began.

---

### Post by poofyhairguy on 2005-11-27
[QUOTE=didit]hai poohfy, i have ati m9. Several days ago i upgraded XOrg.I can confirm that composite with exa enabled goes pretty well. Thanks for a nice howto :)[/QUOTE]

You are welcome. Success stories are VERY much wanted!

---

### Post by fabs0028 on 2005-11-27
[QUOTE=MetalMusicAddict]For me this made it take *forever* for everything to start. 40 was perfect for the 3 PCs I use xcompmgr on. Everything started right up like xcompmgr wasnt running. 

I forgot exactly the GFX card chipset thats in my Dell Inspiron 2200 (945 I think) but Im using the i810 driver. If that helps anyone. My settings for that card: **-cC -t-2 -l-3 -r3 -o.35 -f -D3 **[/QUOTE]

Putting 40 as the number resolved my problem, now all starts at the same time :).
Thanx already one thing less to care about :)

---

### Post by garba on 2005-11-27
i gave it a try with my radeon 8500 and it works great, even if you are not going to use any composite feature the EXA acceleration is worth being enabled, it gives a smoother desktop to some degree... the composite thing is, well, nothing more than a hack at this stage of development but it's interesting nevertheless... of course XGL is the way to go, EXA won't cut in in the long run :D

---

### Post by seiflotfy on 2005-11-27
will it work for a ATI 9700 on breezy??

---

### Post by poofyhairguy on 2005-11-27
[QUOTE=garba]i gave it a try with my radeon 8500 and it works great, even if you are not going to use any composite feature the EXA acceleration is worth being enabled, it gives a smoother desktop to some degree... the composite thing is, well, nothing more than a hack at this stage of development but it's interesting nevertheless... of course XGL is the way to go, EXA won't cut in in the long run :D[/QUOTE]

Yeah, Xegl is the best way....but EXA is needed so the desktop does not stay primative for the years it takes to develop. Only one set of cards in existance (yours) have drivers ready for Xgl....the whole point of a modular Xorg is to catch everything else up in that respect. Luckly you (who have the correct card) will get EXA till then....nice Xorg people.

---

### Post by poofyhairguy on 2005-11-27
[QUOTE=seiflotfy]will it work for a ATI 9700 on breezy??[/QUOTE]

If you have a fast enough CPU (1.5+ GHZ) then the drop shadows will work fine. But it will be a while (I predict two Ubuntu releases) before your card accerates Xcompmgr.

---

### Post by IdolizingStewie on 2005-11-27
I'm experimenting with xcompmgr on my laptop with a pentium IV and NVidia GeForce FX 5700. I'm just running 
```
xcompmgr -a & killall gnome-panel
```
The acceleration works fine, but when I try to get the transparent windows with transset it spits out, for example
```
katherine@ubuntu:~$ transset .5
got arg .5
d is 0.5
opacity 0x7fffffff
Set Property to 0.5
```
but doesn't change the transparency of the window at all. Any ideas?

---

### Post by poofyhairguy on 2005-11-27
[QUOTE=IdolizingStewie]I'm experimenting with xcompmgr on my laptop with a pentium IV and NVidia GeForce FX 5700. I'm just running 
```
xcompmgr -a & killall gnome-panel
```
The acceleration works fine, but when I try to get the transparent windows with transset it spits out, for example
```
katherine@ubuntu:~$ transset .5
got arg .5
d is 0.5
opacity 0x7fffffff
Set Property to 0.5
```
but doesn't change the transparency of the window at all. Any ideas?[/QUOTE]

What Nvidia driver are you using? The repo one or one installed by hand?

---

### Post by IdolizingStewie on 2005-11-27
[QUOTE=poofyhairguy]What Nvidia driver are you using? The repo one or one installed by hand?[/QUOTE]

by hand

---

### Post by poofyhairguy on 2005-11-27
[QUOTE=IdolizingStewie]by hand[/QUOTE]

Hmmm....that might be it. All of my guides and all of my work is based on the driver in the repos- I have never messed with the pure Nvidia ones.

Lets see whats going on- I think your acceration is broken. Please run this xcompmgr command:

```
xcompmgr -fF -I-.002 -O-.003 -D6
```

Then minimize a few windows. Tell me if the fade is nice and smooth, or if the fade is jerking and CPU eating please.

---

### Post by IdolizingStewie on 2005-11-27
[QUOTE=poofyhairguy]Hmmm....that might be it. All of my guides and all of my work is based on the driver in the repos- I have never messed with the pure Nvidia ones.

Lets see whats going on- I think your acceration is broken. Please run this xcompmgr command:

```
xcompmgr -fF -I-.002 -O-.003 -D6
```

Then minimize a few windows. Tell me if the fade is nice and smooth, or if the fade is jerking and CPU eating please.[/QUOTE]

Fade is nice and smooth and transparency works too now. While the fades are very pretty, it makes things a bit slow when multitasking since I tend to bounce between windows and desktops a lot. I tried using the -n  option rather than the -a one (client-side compositing rather than server-side)  and transparency works then too.

---

### Post by poofyhairguy on 2005-11-27
[QUOTE=IdolizingStewie]Fade is nice and smooth and transparency works too now. While the fades are very pretty, it makes things a bit slow when multitasking since I tend to bounce between windows and desktops a lot. I tried using the -n  option rather than the -a one (client-side compositing rather than server-side)  and transparency works then too.[/QUOTE]


I slap my forehead. Of course- it was the xcompmgr command you were using. 

Try 23 meg's xcompmgr command- its nice for faster fading.

---

### Post by Kray on 2005-11-28
Very nice howto. Thx :-)

TBH I don't care too much about eye-candies... hmm, shadows with sane settings looks nice, other feratures... - ya know, its ATI Mobility U1... lol... But windows accelerating is nice. Before there were tonz-and-tonz artifacts while moving, resizing or minimazing/maximizing windows - now it looks much better, even when underlaying window is Opera or Eclipse (yep, it tend to be really ugly before). I'm still waiting for Beos-like GUI responsiveness and mutimedia performance, not sure if it ever become reality... hmm, time will show :]

---

### Post by ScreemingBlue on 2005-11-30
[QUOTE=ssam]it just about works for me on a 64 mb Radeon Mobility 9000 with the opensource drive, on a powerbook g4 1ghz. but i get funky yellow colours and a couple of games can crash the xserver (whether xcompmgr is running or not).

xorg 7 should make things work better[/QUOTE]

Sorry to be an idiot, when you say 'opensource driver' do you mean the one in the ubuntu repositories or the one from the ATI website. I have an ATI radeon 9200 and am trying to get xcompmgr working but all I get is lines across my screen:( . I have tried both the Ubuntu drivers and the ATI drivers. Can you post your xorg.conf so I can compare.

Does anyone know if xorg 7 is available in dapper yet? I went the whole hog and upgraded to Dapper only to find that xorg was on version 6.something and xcompmgr still didn't work. I have reverted back to the more stable Breezy although I found that Dapper seemed more responsive and was pretty much stable for the short time I used it. 

Please can anyone shed some light?


Cheers

---

### Post by ace2005 on 2005-11-30
[QUOTE=ScreemingBlue]Sorry to be an idiot, when you say 'opensource driver' do you mean the one in the ubuntu repositories or the one from the ATI website. I have an ATI radeon 9200 and am trying to get xcompmgr working but all I get is lines across my screen:( . I have tried both the Ubuntu drivers and the ATI drivers. Can you post your xorg.conf so I can compare.Cheers[/QUOTE]


He means the ones that are in use right after you install Ubuntu/Kubuntu, the one without 3D acceleration.

---

### Post by ScreemingBlue on 2005-11-30
I will give it a try, Thanks.

---

### Post by lucas on 2005-11-30
I tried adding thoose lines to my xorg.conf and restarted the xserver. XFCE's composite manager loaded and it worked fine, even though the transperancy of the panel is just irritating. But when I tried resizing a window the screen freezed (im not sure it actually did, couse i could move the cursor, but not click anything). Also, the keyboard was dead so i couldn't change to console or restart X. Anyway, i fast press on the power button made the system shut down nicely. 

Then i removed the changes, afterall, the windows looks fine without shadows. :)

---

### Post by poofyhairguy on 2005-11-30
[QUOTE=lucas]I tried adding thoose lines to my xorg.conf and restarted the xserver. XFCE's composite manager loaded and it worked fine, even though the transperancy of the panel is just irritating. But when I tried resizing a window the screen freezed (im not sure it actually did, couse i could move the cursor, but not click anything). Also, the keyboard was dead so i couldn't change to console or restart X. Anyway, i fast press on the power button made the system shut down nicely. 

Then i removed the changes, afterall, the windows looks fine without shadows. :)[/QUOTE]


Yeah, I never have luck with the built in KDE compositor.

---

### Post by jounihat on 2005-12-01
Xcompmgr is dead slow even with NVIDIA cards. I have a Geforce FX5700 with 256MB of RAM (AMD 2600+ 1GB RAM), and that should be more than enough for eyecandy, considering that OS X can do the same (and some more) with ATi Radeon 9200 with 32MB of RAM. But no, the effects are far from usable with a bit higher resolutions (1600x1200). Big windows just make the refresh rate suffer. If the developers can't dramatically speed things up, I'd say xcompmgr has been just waste of time.

---

### Post by poofyhairguy on 2005-12-01
[QUOTE=jounihat]Xcompmgr is dead slow even with NVIDIA cards. I have a Geforce FX5700 with 256MB of RAM (AMD 2600+ 1GB RAM), and that should be more than enough for eyecandy, considering that OS X can do the same (and some more) with ATi Radeon 9200 with 32MB of RAM[/QUOTE]

OSX has a real framework. Xcompmgr is just a single program. and I have Xcompmgr working well on a Geforce Go 420 16 mb cad- you just HAVE to enable renderaccel. Without that you lose any speed inprovement. So its not as bad as you claim- you must just have missed a step.

>  But no, the effects are far from usable with a bit higher resolutions (1600x1200). Big windows just make the refresh rate suffer. If the developers can't dramatically speed things up, I'd say xcompmgr has been just waste of time.

Xcompmgr was NEVER meant to do what I propose people do with it in this thread. It was NEVER to be a solution or a final framework. It is a program created to show off the composite extension of Xorg. A tech demo, to be used by those making EXA and the like to help understand what needs to be done in the future. It was NEVER intended for end users, for normal people.

But I can't wait till late 2007 or whenever Xegl is in a half stable state. I can't wait till the Linux desktop catches up to OSX's sometime in 2008/2009 (of course it will be ahead by then, I mean catch up to where it is now). So I use Xcompmgr and I leave the directions here for other users.

But its not a "waste of time." Me telling people how to use it is a waste of time if anything. It was never intended to be a solution. Look to Luminocity- there is a composite manager meant for actual use. It is also a year or so away from actual use by users (at least), but when its ready it will be better than Xcompmgr.

Also the speed thing is not Xcompmgr' fault. Its the fault of Nvidia's renderaccel or EXA being too slow. Xcompmgr does to determine the speed- the framework it uses does that. On Linux we have no mature framework- Nvidia's solution is a stop-gap and EXA is still in development. Don't blame Xcompmgr for problems Xorg and Nvidia have....

---

### Post by jounihat on 2005-12-01
[QUOTE=poofyhairguy]OSX has a real framework. Xcompmgr is just a single program. and I have Xcompmgr working well on a Geforce Go 420 16 mb cad- you just HAVE to enable renderaccel. Without that you lose any speed inprovement. So its not as bad as you claim- you must just have missed a step.[/QUOTE]

I've enabled renderaccel, and bazillion of other options people have kindly advised me in various forums, but nothing helps. With higher resolutions and bigger windows, xcompmgr is just pain in the butt (especially fade-in/out effects, shadows and transparency work with somewhat acceptable framerates). The effects are beautiful, though.

---

### Post by poofyhairguy on 2005-12-01
[QUOTE=jounihat]I've enabled renderaccel, and bazillion of other options people have kindly advised me in various forums, but nothing helps. With higher resolutions and bigger windows, xcompmgr is just pain in the butt (especially fade-in/out effects, shadows and transparency work with somewhat acceptable framerates). The effects are beautiful, though.[/QUOTE]

I run at 2560x1024 and it works fine for me but I have a faster video card. Honestly at this point no cards should have any acceration at all- EXA is the first real accerator and its not ready yet. Nvidia jumped the gun with whatever their renderaccel framework is called, but tests show it only works well with a few things (say, transparancies). It might be a while before the very high end get benefits from it all- the work now is focused on ATI 92xx cards and Intel cards and lower resolutions simply because that stuff is easier to get to work....

See you again at the eye candy party in a year?

---

### Post by Danielle on 2005-12-01
[QUOTE=poofyhairguy]These effects can not be given justice in a screenshot....I wish I had a camera because I would film it to show you. Anyone that gets this to work please consider doing this for me!
[/QUOTE]
hi, what does the program Istanbul Desktop Session Recorder do? i have used a program called Camstudio with windows that will record your desktop session maybe you can use that? then upload it to rapidshare.de
i haven't read the whole thread so sorry if you have already done it.

---

### Post by RAOF on 2005-12-01
[QUOTE=poofyhairguy]Yeah, I never have luck with the built in KDE compositor.[/QUOTE]
It **almost** works for me - it doesn't seem to crash X, but it does quite often fail to draw windows properly, especially when they resize themselves.  But apart from that, it looks *so good*.  Having background windows slightly transparent, making moving windows almost see-through, and with smooth transitions in between...

Sadly, the rest of KDE is maddeningly configurable :evil:

---

### Post by poofyhairguy on 2005-12-01
[QUOTE=Danielle]hi, what does the program Istanbul Desktop Session Recorder do? i have used a program called Camstudio with windows that will record your desktop session maybe you can use that? then upload it to rapidshare.de
i haven't read the whole thread so sorry if you have already done it.[/QUOTE]


I have not. I figured that the only way is to record a monitor. If I am wrong somewho show me the light please.

---

### Post by poofyhairguy on 2005-12-01
[QUOTE=RAOF]It **almost** works for me - it doesn't seem to crash X, but it does quite often fail to draw windows properly, especially when they resize themselves.  But apart from that, it looks *so good*.  Having background windows slightly transparent, making moving windows almost see-through, and with smooth transitions in between...[/QUOTE]

I've tried it and I like that it DOES things with its Kompmgr besides shadows and fading.

---

### Post by suoko on 2005-12-05
One silly question abour "renderaccel" option for nvidia drivers:
enabling this option freezes my PC as well as many others PCs. Is this due to an nvidia driver bug or a xorg bug? Or whatever?

---

### Post by RAOF on 2005-12-05
[QUOTE=suoko]One silly question abour "renderaccel" option for nvidia drivers:
enabling this option freezes my PC as well as many others PCs. Is this due to an nvidia driver bug or a xorg bug? Or whatever?[/QUOTE]
They're closed source drivers, so no-one really knows.  

But, given than the renderaccel option prints the warning "Enabling EXPERIMENTAL xrender support" to the xorg log, I'm guessing it's the nvidia drivers ;)

---

### Post by poofyhairguy on 2005-12-05
[QUOTE=suoko]One silly question abour "renderaccel" option for nvidia drivers:
enabling this option freezes my PC as well as many others PCs. Is this due to an nvidia driver bug or a xorg bug? Or whatever?[/QUOTE]


Its the Nvidia driver. One day Nvidia's renderaccel will be replaced by EXA. Till then we have to deal with its quirks.

---

### Post by oobuntoo on 2005-12-05
I used to have lockup problem when enabling renderaccel. Replacing my old nvidia card with 6600gt and the problem was gone. Shadow and transparency under KDE seem stable and fast enough for most part, but not stable enough for long term use. Other problems include screen artifacts when logging in, maximizing window to take up full screen, and playing video. Anyone know what is responsible for these artifacts? Is it Xorg, kde built-in xcompmgr, nvidia driver, or combinations of these? I don't recall seeing screen artifacts when using xcompmgr and trannset under gnome.

---

### Post by poofyhairguy on 2005-12-06
[QUOTE=oobuntoo]I used to have lockup problem when enabling renderaccel. Replacing my old nvidia card with 6600gt and the problem was gone. Shadow and transparency under KDE seem stable and fast enough for most part, but not stable enough for long term use. Other problems include screen artifacts when logging in, maximizing window to take up full screen, and playing video. Anyone know what is responsible for these artifacts? Is it Xorg, kde built-in xcompmgr, nvidia driver, or combinations of these? I don't recall seeing screen artifacts when using xcompmgr and trannset under gnome.[/QUOTE]

Its the composite extension within Xorg.

And yes, a faster card wil more RAM almost always does the job.

---

### Post by hectorC on 2005-12-06
Hello,

I followed your how-to and when I run xcompmgr I get the error "No composite extension". I have a nvidia 6600 and the only way I found to make it work was adding the "Extensions" section for unsupported cards. This is part of my xrog.conf:

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
	Option          "RenderAccel"           "true"
	Option          "AllowGLXWithComposite" "true" 
EndSection

Any idea why?

Thanks in advance!

Hector.

---

### Post by hectorC on 2005-12-06
[QUOTE=hectorC]Hello,

I followed your how-to and when I run xcompmgr I get the error "No composite extension". I have a nvidia 6600 and the only way I found to make it work was adding the "Extensions" section for unsupported cards. This is part of my xrog.conf:


Hector.[/QUOTE]


Forget it! My mistake.... I thought it said that the step where you add the "Extensions" section was only for unsopported cards.

Thanks anyway.

Hector.

---

### Post by poofyhairguy on 2005-12-08
[QUOTE=hectorC]Forget it! My mistake.... I thought it said that the step where you add the "Extensions" section was only for unsopported cards.

Thanks anyway.

Hector.[/QUOTE]

So everything is ok? Good.

---

### Post by poofyhairguy on 2005-12-08
Ok. Here is the GUI for Xcompmgr I promised. It was made for Mandrake, but after some fighting its an Ubuntu program now. Its attached to this post.

Enjoy!!!

---

### Post by phend-one on 2005-12-08
I read somewhere (can't remember) that the new nvidia driver (released very recently, but not 7667) allowed flawless use of compositing with xorg. Is this made possible through this guide? Is that what they were talking about?

I tried this about a month ago, and it was kinda glitchy (BUT SO NICE!).


**EDIT:** Did some more digging... I'm not sure if this is the new one though... [Linux Nvidia drivers 8174]("http://www.nvidia.com/object/linux_display_ia32_1.0-8174.html").

---

### Post by Knomefan on 2005-12-09
Yep, thats the new nvidia driver and it works very nicely here.

The big news concerning composite is that they seem to have fixed RenderAccel, that is, fixed it so that it doesn't freeze my computer anymore if it is enabled.

---

### Post by phend-one on 2005-12-09
So installing that driver from nvidia's site and following the steps in this guide should allow for composite effects without crashing? :D

---

### Post by Knomefan on 2005-12-09
All I can say is that it works for me here without crashing.

Of course, always keep in mind that installing the nvidia drivers directly can get you into trouble, so make sure that you know what you are doing.

Btw., there's a pretty good howto on how to do it in the howto section.

---

### Post by runlevel0 on 2005-12-09
I'm having a strange issue:

(Nvidia GeForce FX 5200)

When I set [color=#009900]Option "Composite" "Enable"[/color] the xserver crashes (no error message, no log entries)...

But, w/o this option (extmod, RenderAccel and the rest enabled) I am able to use xcompmgr and transset w/o any problem (even [color=#009900]AllowGLXWithComposite[/color] is on).

I'm not sure, but; Could it mean that the COMPOSITE extension is automatically loaded with extmod or any other X-server option?

---

### Post by Eversmann on 2005-12-09
I wanted to give my thanks for this thread, it made me my evening :-D

Now i have a desktop much quicker and much nicer!!! Those values you put for xcompmgr are AWESOME!!!

Thanks guys for giving such an useful information and all your work. That makes linux and ubuntu better everyday!!!

---

### Post by poofyhairguy on 2005-12-09
[QUOTE=phend-one]I read somewhere (can't remember) that the new nvidia driver (released very recently, but not 7667) allowed flawless use of compositing with xorg. Is this made possible through this guide? Is that what they were talking about?
[/QUOTE]

Well....now that EXA is starting to push renderaccel, this helps the Nvidia people make better drivers because they know exactly what the point of acceration will be.

But one thing to note is that many composite problems stem from Xorg itself. I hear people with ATI cards that work with the CVS xorg still have a few visual artifacts that are off. Of course, it might never be perfect. I was using a Mac the other day when the Panther I was using made a visual error that looked just like a familiar xcompmgr bug.

I can almost promise that by Dapper it will be much more stable.

---

### Post by poofyhairguy on 2005-12-09
[QUOTE=Eversmann]I wanted to give my thanks for this thread, it made me my evening :-D

Now i have a desktop much quicker and much nicer!!! Those values you put for xcompmgr are AWESOME!!!

Thanks guys for giving such an useful information and all your work. That makes linux and ubuntu better everyday!!![/QUOTE]


No problem. Just please be careful because if not one day xcompmgr will bring the hurt to you.

---

### Post by jannol on 2005-12-10
Awesome, all the tips and so on. Really cool with a modern look although I personally think the effects should be way faster as default.

Well I don't use xcompmgr more than for showoff for my friends since it tends to shutdown easily on my computer and that might not be very strange since I have overclocked my 6800LE in its bios so I get kinda bad artifacts sometimes with xcompmgr. I also use twinview which possibly affects.

Well, since I didn't find any screen recordings before I began messing with this I though I make one for those who wanna get a bit of a preview.

Now, it was not easy to sync the recording exactly to real time but I think I got close enough.

I am using setting -cfF -D 8 -O 0.02 -I 0.040

in this clip. I only recorded my left screen since I am guessing not everyone has dual screens.

get it [here](http://linux.jannol.com/ubuntu/demos/demo-0.mpg) 31.3 MB (no audio)

I will move the file to a slower server in a day or two since my highspeed server space is limited.

Thx all for your howto, guides, tips etc.

---

### Post by sethmahoney on 2005-12-10
Thanks a lot for the great howto!

I got everything working, except I can't update the xcompmgr.  This is the error I get when I run ./configure:

```
checking for XCOMPMGR... configure: error: Package requirements (xcomposite xfixes xdamage xrender) were not met.
```

Is the newer xcompmgr for Dapper only?  Any thoughts on what I might try to get it updated?

EDIT:
Nevermind, I got it working - I forgot to install all the development headers for those libraries.

---

### Post by poofyhairguy on 2005-12-10
[QUOTE=jannol]Awesome, all the tips and so on. Really cool with a modern look although I personally think the effects should be way faster as default.

Well I don't use xcompmgr more than for showoff for my friends since it tends to shutdown easily on my computer and that might not be very strange since I have overclocked my 6800LE in its bios so I get kinda bad artifacts sometimes with xcompmgr. I also use twinview which possibly affects.

Well, since I didn't find any screen recordings before I began messing with this I though I make one for those who wanna get a bit of a preview.

Now, it was not easy to sync the recording exactly to real time but I think I got close enough.

I am using setting -cfF -D 8 -O 0.02 -I 0.040

in this clip. I only recorded my left screen since I am guessing not everyone has dual screens.

get it [here](http://www.jannol.com/test/frm-0000.mpg) 31.3 MB (no audio)

I will move the file to a slower server in a day or two since my highspeed server space is limited.

Thx all for your howto, guides, tips etc.[/QUOTE]

Thanks for the video. Just so you know, I use Twinview with Xcompmgr fine and I posted in the first post the magical Xorg.conf that does it all.

And yes, it would be neat to be faster. But honestly this stuff is a while away from regular desktop use for most. We are all early adopters.

---

### Post by unkemptwolf on 2005-12-11
Just tried this after poofy reccomended it in another thread. 

[SIZE="3"]**Holy. Crap.**[/SIZE]

I dont think I've ever had effects this sweet on an OS. I cant get over it. Damn you poofyhairguy, for causing me to spend hours watching my menus and windows fade in and out, in and out, in... and... ou...

*drool*

---

### Post by Mastodront on 2005-12-11
I've recently decided to give Kubuntu another chance and so far I like it alot. I've enabled the drop shadows and transparency on moving and inactive windows and it looks really sweet, and it's not even especially crashy as I rembered it to be :)

But I've got one little problem;
It's a bit buggy, quite often active windows gets transparency and won't let it go even though they shouldn't have it :/  Moving windows always work as they should, as do the inactive ones. It's really nothing to cry about but when everything else works so fine it gets quite annoying :)  

I know compositing is unstable/buggy and so but I thought maybe there's a simple solution to the problem :)


Edit:  I've found that minimizing/maximizing the buggy windows a couple of time the transparency goes away, still quite annoying though :)

---

### Post by jannol on 2005-12-11
[QUOTE=poofyhairguy]Thanks for the video. Just so you know, I use Twinview with Xcompmgr fine and I posted in the first post the magical Xorg.conf that does it all.
[/QUOTE]

I tried that but I had to put two lines more in my xorg.conf to prevent xcompmgr from locking up my computer.

In the device section

 	Option	"NvAGP"       "2"
	VideoRam 131072

I guess it is not the twinview setup then...

---

### Post by Bloot on 2005-12-11
It's really nice for the eye to get delighted with all those effects, I like it very much, really.

But it still is too buggy for diary use, I just tried it and that's all, I'll wait 'till it gets more polished, if it ever gets.

Greetings.

---

### Post by Knomefan on 2005-12-11
You guys should really try out kde 3.5 with composite.

It's much better integrate than in gnome (well, that is, it is integrated) and mostly works like a charm (well, there are a few glitches, but nothing to serious here).

If you want nice drop shadows that you can tinker with with a nice gui, if you want to be able to for example make all windows automatically transperent when you move them, give it a try.

---

### Post by Mastodront on 2005-12-11
[QUOTE=Knomefan]You guys should really try out kde 3.5 with composite.

It's much better integrate than in gnome (well, that is, it is integrated) and mostly works like a charm (well, there are a few glitches, but nothing to serious here).

If you want nice drop shadows that you can tinker with with a nice gui, if you want to be able to for example make all windows automatically transperent when you move them, give it a try.[/QUOTE]

Have you had the same problems as I (3-4 posts up...)? I'm also using KDE 3.5...

---

### Post by Knomefan on 2005-12-11
[QUOTE=Mastodront]Have you had the same problems as I (3-4 posts up...)? I'm also using KDE 3.5...[/QUOTE]

Hm, strange, no I haven't had this probelm.

---

### Post by Eversmann on 2005-12-11
[QUOTE=poofyhairguy]No problem. Just please be careful because if not one day xcompmgr will bring the hurt to you.[/QUOTE]

Yeah, i have to deal with it, because sometimes when i bootup my laptop, i have to make a killal gnome-panel or disable it when i have to play a video. But it's worth the pay to have an accelerated and much nicer desktop to show to my friends :-D

I wish we could have another version reviewed and updated with all those bugs corrected. Maybe someday?

In this time,with vista and osx, i think all the linux users need a better desktop. It could gain more points for the people who want to start with the linux world.

---

### Post by poofyhairguy on 2005-12-11
[QUOTE=unkemptwolf]Just tried this after poofy reccomended it in another thread. 

[SIZE="3"]**Holy. Crap.**[/SIZE]

I dont think I've ever had effects this sweet on an OS. I cant get over it. Damn you poofyhairguy, for causing me to spend hours watching my menus and windows fade in and out, in and out, in... and... ou...

*drool*[/QUOTE]

Becareful. Once you are hooked then you are more than willing to throw stbility out the window. At least get the session saver extension for Firefox.

---

### Post by poofyhairguy on 2005-12-11
[QUOTE=Eversmann]Yeah, i have to deal with it, because sometimes when i bootup my laptop, i have to make a killal gnome-panel or disable it when i have to play a video. But it's worth the pay to have an accelerated and much nicer desktop to show to my friends :-D

I wish we could have another version reviewed and updated with all those bugs corrected. Maybe someday?[/QUOTE]

One day we won't need Xcompmgr. We will have something better.

For the record, Totem-xine is the best media player for Xcompmgr use.

---

### Post by poofyhairguy on 2005-12-11
[QUOTE=Knomefan]You guys should really try out kde 3.5 with composite.

It's much better integrate than in gnome (well, that is, it is integrated) and mostly works like a charm (well, there are a few glitches, but nothing to serious here).

If you want nice drop shadows that you can tinker with with a nice gui, if you want to be able to for example make all windows automatically transperent when you move them, give it a try.[/QUOTE]

I personally won't move till the entire composite extension is more stable- I can at least turn Xcompmgr off and on easily.

For the record, the gcompmgr I added to this thread adds a GREAT GUI for Gnome users.

---

### Post by sethmahoney on 2005-12-12
[QUOTE=poofyhairguy]For the record, the gcompmgr I added to this thread adds a GREAT GUI for Gnome users.[/QUOTE]

Yeah, the gcompmgr is AWESOME.  I just wish the controls were more intuitive.   "Blur radius", "top offset", and "fade-delta-time" just aren't very meaningful to most people.  Also, it doesn't seem to turn off the gnome-panel shadows (on my computer anyway), even when I fill in the checkbox.  Still, though, I'm very much glad its around!

Has anyone else had issues with nautilus and xcompmgr crashing when doing file transfers over a samba network, or when copying large files?  Seems to happen pretty regularly for me when I do either of those things.

---

### Post by RAOF on 2005-12-12
Hey, poofyhairguy, you wouldn't happen to have the deb-src of gcompmgr lying around for those of us with AMD64 machines, would you? ;)

And I suppose the PPC guys might want it too. :)

---

### Post by poofyhairguy on 2005-12-12
[QUOTE=RAOF]Hey, poofyhairguy, you wouldn't happen to have the deb-src of gcompmgr lying around for those of us with AMD64 machines, would you? ;)

And I suppose the PPC guys might want it too. :)[/QUOTE]

I hate to say it, but it doesn't exist. Gcompmgr was only released as a x86 Mandrake RPM. I would love to help....but I can't this time.

---

### Post by RAOF on 2005-12-12
[QUOTE=poofyhairguy]I hate to say it, but it doesn't exist. Gcompmgr was only released as a x86 Mandrake RPM. I would love to help....but I can't this time.[/QUOTE]
Oh, well.  It compiles & runs fine.  Maybe I'll learn how to package it, since checkinstall is broken in dapper atm :)

---

### Post by RAOF on 2005-12-13
And here they are.  And I hope they work :)

An AMD64 binary .deb, and the source package that you should be able to build with dpkg-buildpackage.

---

### Post by poofyhairguy on 2005-12-13
[QUOTE=RAOF]And here they are.  And I hope they work :)

An AMD64 binary .deb, and the source package that you should be able to build with dpkg-buildpackage.[/QUOTE]

Thank you very much!

---

### Post by codejunkie on 2005-12-13
[quote=poofyhairguy]One day we won't need Xcompmgr. We will have something better.

For the record, Totem-xine is the best media player for Xcompmgr use.[/quote] i've got quick question every thing except .mov files plays fine in totem-xine every time i open a .mov file in totem-xine it crashes. would you know any workaround to get totem-xine to play .mov files, i've got to all the codecs and such installed but right now, but in order to play them i have to disable the composite extension and play them in mplayer any help would be appreicated.

---

### Post by pizzach on 2005-12-13
Wow.  I just compiled and installed xcompmgr form cvs yesterday.  I left my computer on all night and it didn't freeze (only with the shadows on.)  In fact, It's been going most of today too.  I wonder if it's a fluke.  Still waiting for my first crash.  I also hasn't crashed with me using mplayer which usually happens after a few movies.

I just don't see the point in fading windows.  Mybe if I try to make the fade faster than default it'll grow on me.  I always get the feeling of waiting for my computer when the fades are on and I already feel like I have to wait enough.  :p

Man, your new avatar confused me hairpoofguy.  I didn't recognize you at first.  Very nice though.

---

### Post by poofyhairguy on 2005-12-13
[QUOTE=codejunkie]i've got quick question every thing except .mov files plays fine in totem-xine every time i open a .mov file in totem-xine it crashes. would you know any workaround to get totem-xine to play .mov files, i've got to all the codecs and such installed but right now, but in order to play them i have to disable the composite extension and play them in mplayer any help would be appreicated.[/QUOTE]

Hmmm.....I do not have that problem. But I will say as a suggestion that the only other media player that works well with Xcompmgr is VLC. You can try VLC for those files.

---

### Post by poofyhairguy on 2005-12-13
[QUOTE=pizzach]Wow.  I just compiled and installed xcompmgr form cvs yesterday.  I left my computer on all night and it didn't freeze (only with the shadows on.)  In fact, It's been going most of today too.  I wonder if it's a fluke.  Still waiting for my first crash.  I also hasn't crashed with me using mplayer which usually happens after a few movies.[/QUOTE]

I'm having same luck! Yay for near stable.

> 
I just don't see the point in fading windows.  

I think its pretty.

> 
Mybe if I try to make the fade faster than default it'll grow on me. 

I bet. Try gcompmgr.

> 
Man, your new avatar confused me hairpoofguy.  I didn't recognize you at first.  Very nice though.

Thanks.

---

### Post by scav on 2005-12-14
[QUOTE=maxtreiber]Me again :)
I was amazed of the idea to have only the current active window without opacity and all the others transparent because i use the "Select windows when mouse moves over them" option in the gnome Window Preferences.
Using this, i can work in one window and if i want to see whats behind in another, i just move the mouse over it and can look through it :)
anyways, i wrote a small C programm to do exactly this:

[http://81.169.175.95/transd.c](http://81.169.175.95/transd.c)

compile and run with:

gcc transd.c -o transd -lX11 && while true; do ./transd; done

its very badly programmed (most of the code is stolen) and needs a lot of values tweaked, but please try it out and tell me what you think![/QUOTE]


Have you been working more on this? The Idea is really good, only thing is the stability!

Would love a stable version,

Greetings

---

### Post by fannymites on 2005-12-16
Does anyone know if it's possible to change the transparency level when using the transd program?  It's a great little app but I have a dark wallpaper and the unfocused windows merge into it a little too much.

---

### Post by RAOF on 2005-12-16
Here's a quick hack to allow you to pass the opacity fraction on the command line.  Instead of running ```
while true; do ./transd; done
``` you would now run
```
while true; do ./transd 0.5; done
```

Warning: this hasn't actually been tested.  This computer doesn't have the composite extension.  But it should work. :)

---

### Post by fannymites on 2005-12-16
Unfortunately, the transparency level seems to be the same no matter what number I put there.
But on the subject of transd, is there anyway to make it automatically on boot?
I've tried various things but can't get anything to work so far.

I reckon this could have a lot of potential.

---

### Post by RAOF on 2005-12-16
Whoops!  My bounds checking is awesome.  Here's a version that **should** work :)

---

### Post by poofyhairguy on 2005-12-16
[QUOTE=fannymites]Unfortunately, the transparency level seems to be the same no matter what number I put there.
But on the subject of transd, is there anyway to make it automatically on boot?
I've tried various things but can't get anything to work so far.

I reckon this could have a lot of potential.[/QUOTE]

This is the best trick I know:

[http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency#transset-df](http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency#transset-df)

---

### Post by sethmahoney on 2005-12-16
[QUOTE=maxtreiber]Me again :)
I was amazed of the idea to have only the current active window without opacity and all the others transparent because i use the "Select windows when mouse moves over them" option in the gnome Window Preferences.
Using this, i can work in one window and if i want to see whats behind in another, i just move the mouse over it and can look through it :)
anyways, i wrote a small C programm to do exactly this:

[http://81.169.175.95/transd.c](http://81.169.175.95/transd.c)

compile and run with:

gcc transd.c -o transd -lX11 && while true; do ./transd; done

its very badly programmed (most of the code is stolen) and needs a lot of values tweaked, but please try it out and tell me what you think![/QUOTE]

I just installed the newer version of this, and it works like a charm.  Its so great I almost wet myself.

EDIT: Two problems: First, for some reason it makes my desktop "transparent" like any other window (which means when it loses focus, all my icons and my wallpaper get a little darker); second, like the poster above, it would be nice to be able to start it when Gnome starts.  Any ideas?

EDIT: There's a third problem: I can't stop flipping back and forth between windows just to see them go transparent!

---

### Post by fannymites on 2005-12-17
It's working nicely for me too.
I don't get the transparent desktop problem though.  Do you have nautilus set to show the desktop? I don't so that may be why.
Still haven't worked out how to make it work on start up yet.

I'm gonna have a go with that there transset-df, see what that's like.

So I got transset-df installed, it took me a while to work out what was what but I got there in the end.  Very nice.

---

### Post by poofyhairguy on 2005-12-18
[QUOTE=RAOF]Whoops!  My bounds checking is awesome.  Here's a version that **should** work :)[/QUOTE]

NICE!

---

### Post by fannymites on 2005-12-18
Anyone still trying to get it to start when gnome starts up - 
move to the directory containing the transd executable then do ```
sudo ln -s transd /usr/bin/transd
```
Next go to System>Preferences>Sessions>Startup Programs and add ```
/usr/bin/transd 0.6
```
and adjust the transparency level to suit.
Of course you will have to adjust the order number to make sure it starts after xcompmgr.  And to really show off, add xbindkeys and transset-df to startup also.

---

### Post by varunus on 2005-12-18
transd.  is.  AWESOME.  RAOF, you are the man.  However, there's another program out there with the same name (but not half as cool, all it does is watch for window creation and set a transparency) so you may want to change the name...

I need to go buy an NVIDIA card...or more accurately, a new computer, as my laptop's intel 855GM does not like composite.  I can see the theory, the trans switching isn't fast enough to be usable on this computer.  Also, dragging transparent windows is just bad news. (I tried it with the -F option on Xcompmgr for maximum awesomeness, as transparency switches fade in and out.)

Composite will hopefully be usable in dapper (with a little cvs compiling); the i810 EXA patch is almost complete (along with a few others). I just don't want to go to dapper and xorg 7 yet.

---

### Post by fannymites on 2005-12-18
I don't have an Nvidia card and I can tell you, using xcompmgr on dapper is vastly different to breezy.
On breezy I use the the xcompmgr settings for unsupported cards as suggested at the very start of this guide.
On dapper I'm using this setting from the the guide > 
```
xcompmgr -fF -I-.002 -O-.003 -D6 -cC -t-5 -l-6 -r5
```That one does fading in the best way and has drop shadows that look much better overall- especially with drop down lists such as the Applications menu. This could be called "The Perfect Setting." (I know its not for everyone)
along with transd (though I can't get it to run on startup on dapper for some reason)
Even with many windows open and fading into transparency it still runs at a very acceptable speed.  So much so I have xcompmgr running all the time on dapper whereas on breezy I only put it on if I'm not doing anything particularly important

---

### Post by ShiftyPowers on 2005-12-18
wow, using KDE 3.5 and translucency.  I have no converted from Gnome to KDE.  This thing is slick

---

### Post by poofyhairguy on 2005-12-19
[QUOTE=varunus](I tried it with the -F option on Xcompmgr for maximum awesomeness, as transparency switches fade in and out.).[/QUOTE]

I have read that Nvidia's driver has a few special hacks to make that effect so smooth. Until you see it on an Nvidia card.....

Lets just put it this way. This whole thing started because I saw the -Ff option on my girlfriend's Gefore 420 Go (16mb!) one day. I HAD to have Nvidia and Xcompmgr then.

---

### Post by RAOF on 2005-12-19
[QUOTE=ShiftyPowers]wow, using KDE 3.5 and translucency.  I have no converted from Gnome to KDE.  This thing is slick[/QUOTE]
Can't wait to try it on the new nVidia drivers, which apparently don't break when using composite quite so much ;)

---

### Post by RAOF on 2005-12-20
[QUOTE=varunus]transd.  is.  AWESOME.  RAOF, you are the man.  However, there's another program out there with the same name (but not half as cool, all it does is watch for window creation and set a transparency) so you may want to change the name...[/QUOTE]
Not actually my code, but thanks ;).  I just hacked on the "pass transparency fraction on commandline" bit.  Thank maxtreiber.

---

### Post by Jessehk on 2005-12-20
Worked perfectly. The only problems are the high memory usage and the fact that the screensavers have problems.

---

### Post by hectorC on 2005-12-21
[QUOTE=pizzach]Wow.  I just compiled and installed xcompmgr form cvs yesterday.  I left my computer on all night and it didn't freeze (only with the shadows on.)[/QUOTE]

I can't find how to access CVS of xcompmgr. I wonder if you could give me the CVS address.

thanks!


Hector

---

### Post by emerick7 on 2005-12-21
I followed through the instruction on [transparent terminals on the wiki]("https://wiki.ubuntu.com/TransparentTerminals?highlight=%28transparent%29%7C%28terminals%29"), and then when I got to the part to restart x with control-alt-backspace, everything when black and I got a command prompt-type screen.  I tried restarting it, and when it's finished going through the OKs (nothing errors out) during startup, I get a screen that says > Failed to start the X server (your graphical user interface.

I'm not able to get anywhere.  After that, it just goes into a command prompt again where it asks for login info, but I don't know where to go from there.  How do I go to a safe mode or something similar so I can revert back to what I had before?  At this point, I don't want transparent terminals anymore - I just need to get my desktop running.

I'd appreciate the help... I really need some this time.  Thanks!

---

### Post by Knomefan on 2005-12-21
First off and I hope you don't get me wrong, this is the reason why you should always make a backup before you edit an important file (belief me, I know what I'm talking about...)

About your problem.
I suspect that you just made a little mistake when you edited xorg.conf and finding this mistake will fix your problem.
So, simply log in (type your username, hit enter, type your password, hit enter) and then open xorg.conf as root with sudo /etc/X11/xorg.conf. Now look through the file and get rid of the changes you mad (a good way to do this is to simply comment the lines you want to get rid of out, that is put a # in front of them).

You should also take a look at your log file. It should tell you which error X encountered exactly.
less /etc/X11/xorg.conf (press > to get to the end of the file)

After you are done with the changes try to restart your login manager with:
sudo /etc/init.d/gdm restart (or /etc/init.d/kdm restart if you are using kde).

Hope this helps.

---

### Post by poofyhairguy on 2005-12-21
[QUOTE=Jessehk]Worked perfectly. The only problems are the high memory usage and the fact that the screensavers have problems.[/QUOTE]

Yeah....I have turned screensavers off a long time ago.

---

### Post by poofyhairguy on 2005-12-21
[QUOTE=emerick7]I followed through the instruction on [transparent terminals on the wiki]("https://wiki.ubuntu.com/TransparentTerminals?highlight=%28transparent%29%7C%28terminals%29"), and then when I got to the part to restart x with control-alt-backspace, everything when black and I got a command prompt-type screen.  I tried restarting it, and when it's finished going through the OKs (nothing errors out) during startup, I get a screen that says 

I'm not able to get anywhere.  After that, it just goes into a command prompt again where it asks for login info, but I don't know where to go from there.  How do I go to a safe mode or something similar so I can revert back to what I had before?  At this point, I don't want transparent terminals anymore - I just need to get my desktop running.

I'd appreciate the help... I really need some this time.  Thanks![/QUOTE]


What I would do is use this command:

> sudo nano /etc/X11/xorg.conf

To open your Xorg.conf file. Then when inside change the "nvidia" driver to "nv." Then hit control and "X" at the same time to save and exit. Then at the command prompt type

> startx

95% of the time for me that gets me back a display. Now you have to fix the problem. When Gnome starts use this command:

> sudo cp /etc/X11/xorg.conf /home/yourusername/Desktop/xorg.conf

To back up your xorg file that lets you in Gnome to your desktop. To restore use this command:

> sudo cp /home/yourusername/Desktop/xorg.conf /etc/X11/xorg.conf

Now fix the problem. Use this command:

> sudo gedit /etc/X11/xorg.conf

And undo EVERYTHING that other guide told you to do. Everything. Then change the "nv" in the driver part back to "nvidia." Then make sure you have the Nvidia drivers installed and the restricted modlules installed:

> sudo apt-get install nvidia-glx linux-686

with that command. Then once you are done, reboot. If you fixed the problem it will work like before. If not......well...put the "nv" driver back on and log back in here so I can try another idea.

In the first step does not help you (aka changing driver to "nv") your only hope is this command: 

```
sudo dpkg-reconfigure xserver-xorg
```

Good luck.

---

### Post by hectorC on 2005-12-21
poofyhairguy: do you know how to access CVS for xcompmgr?

thanks!

---

### Post by poofyhairguy on 2005-12-21
[QUOTE=hectorC]I can't find how to access CVS of xcompmgr. I wonder if you could give me the CVS address.

thanks!


Hector[/QUOTE]

I cannot find CVS. Best I can find is this tar file:

[http://xapps.freedesktop.org/release/](http://xapps.freedesktop.org/release/)

Thanks for making me find it, I want to compile a 64 bit version.

---

### Post by poofyhairguy on 2005-12-21
[QUOTE=poofyhairguy]I cannot find CVS. Best I can find is this tar file:

[http://xapps.freedesktop.org/release/](http://xapps.freedesktop.org/release/)

Thanks for making me find it, I want to compile a 64 bit version.[/QUOTE]

Scratch that. I found the CVS for Xcompmgr:

[http://cvs.freedesktop.org/xapps/xcompmgr/](http://cvs.freedesktop.org/xapps/xcompmgr/)

But nothing has happened since the last release. In fact, the CVS is kinda depressing because many of the files haven't been changed in months......

I guess there is no use for Xcompmgr soon. KDE's composite manager is pretty mature, and Metacity is finally getting one that kinda works. I bet that that release of Xcompmgr I linked above is the last one.

That of course sucks for Gnome people as the Metacity compositor is REALLY new...and maybe not as stable.

Later this week I plan to compile and try out Metacity's compositor. If its even medium stable I will make a guide.

Xcompmgr was a fun ride while it lasted.....but I knew we would have to move on one day!

My advice: If you really like the composite effects, you must accept a move to KDE for a while. Its now FAR ahead of Gnome in this area.

I will try to hack the Metacity compositor, but Metacity is VERY slow when it comes to effects so my original assumption (a few months ago) of KDE being a half year ahead of Gnome is probably correct (won't know for sure till I try that new compositor).

I will post the results of all my playing around in my eye candy blog. Look there in the future for information:

[http://doc.gwos.org/index.php/Poofyhairguy%27s_Eye_Candy_Report](http://doc.gwos.org/index.php/Poofyhairguy%27s_Eye_Candy_Report)

---

### Post by emerick7 on 2005-12-21
thanks for the help... got everything up and running now.

Before you replied, I saw somewhere else to try "sudo dpkg-reconfigure xserver-xorg."  That seemed to work, although I had to go through quite a few prompts.

---

### Post by emerick7 on 2005-12-21
As I am new to linux (but do enjoy some eye candy to decorate my desktop), I tried working with gcompmgr but had a few problems.  Right now, I'd like to get rid of it because I just want to revert to the way it was before.  Not that it was bad or anything, but I'd just like to eliminate it from my comp.  I uninstalled gcompmgr and xcompmgr from synaptic, but when I go to System > Logout, nothing appears.  I saw the thing about the most important rule, but I figured if I just uninstalled them then it wouldn't be a problem.

---

### Post by jannol on 2005-12-21
before you logout you could press ALT+F2 and type

killall xcompmgr

if you for some reason can't, press CTRL+ALT+F1 and log in and then type

killall xcompmgr

then press CTRL+ALT+F7 to get back to gnome

However, simply reboot and xcompmgr won't start if you have uninstalled it

---

### Post by emerick7 on 2005-12-21
I rebooted and it worked.  Before I was trying control-alt-backspace, but didn't think to do a full restart.

---

### Post by pixelnate on 2005-12-21
Poofy Hair Guy, you are the bomb. I don't miss OSX so much any more!
:smile: :smile: :smile:

---

### Post by ace2005 on 2005-12-22
Hey Look! Xorg 7.0/6.9.0 has been Released

Now how long until we can update to it?

---

### Post by poofyhairguy on 2005-12-22
[QUOTE=ace2005]Hey Look! Xorg 7.0/6.9.0 has been Released

Now how long until we can update to it?[/QUOTE]

Today if you do it yourself:

[http://xorg.freedesktop.org/wiki/CvsPage](http://xorg.freedesktop.org/wiki/CvsPage)

Tomorrow if you can stand unstable Dapper. 

Or in April if you wait to the next stable version.

This kinda of stuff is not backported usually.

---

### Post by ace2005 on 2005-12-22
Lets just say i totally screw up the xserver by trying it the cvs way, what do i have to do to reinstall the normal x server

[COLOR="Red"]**PLEASE DO AN EASY TO FOLLOW HOW-TO FOR GETTING AND INSTALLING THIS VIA CVS AND INSTALLING IT ON UBUNTU/KUBUNTU**[/COLOR]

That would be the best way, that guide is confusing me :(

---

### Post by poofyhairguy on 2005-12-22
[QUOTE=ace2005]Lets just say i totally screw up the xserver by trying it the cvs way, what do i have to do to reinstall the normal x server
[/QUOTE]

I think that page tells how to set up and extra one. So to go back you delete the file you installed it in? Its over my head too a little. Soon I will just install Dapper to get Xorg 7. I always try the new development release in January.

> 
[COLOR="Red"]**PLEASE DO AN EASY TO FOLLOW HOW-TO FOR GETTING AND INSTALLING THIS VIA CVS AND INSTALLING IT ON UBUNTU/KUBUNTU**[/COLOR]

That would be the best way, that guide is confusing me :(

There might not be an "easy way" to install Xorg. I mean....Mr. Stone who works for Ubuntu takes months to stablize the Xserver in each Ubuntu release.

Basically, I suggest that anyone who really wants it just try Dapper soon. The Xserver is not something that is really easy to replace!

---

### Post by muchmusic on 2005-12-22
Nice work senor Poof. I'm using a powerpc with a radeon 9800 with xorg 7 and xcompmgr/metacity

It looks awesome. unstable and I can't use a few options because they slow things down, but by and large it's awesome.

---

### Post by poofyhairguy on 2005-12-22
[QUOTE=muchmusic]Nice work senor Poof. I'm using a powerpc with a radeon 9800 with xorg 7 and xcompmgr/metacity

It looks awesome. unstable and I can't use a few options because they slow things down, but by and large it's awesome.[/QUOTE]


Glad you like.

---

### Post by poofyhairguy on 2005-12-22
[QUOTE=pixelnate]Poofy Hair Guy, you are the bomb. I don't miss OSX so much any more!
:smile: :smile: :smile:[/QUOTE]

Thanks. I feel same way- Xcompmgr is the reason I do not own a Mac Mini.

---

### Post by Evil Whisper on 2005-12-22
Hello!

What does this do:

Option "DAMAGE" "true"

Thanks,
- Evil Whisper

---

### Post by ace2005 on 2005-12-22
I have an insane idea, VMPLAYER!!!!!!!!!!!!

Try that first and then i can try it for real :D

What what change do i make to this  "define DefaultGcc2i386Opt -O2 -mcpu=pentium4" if i have an AMD Athlon XP 2000?

It also says that this will add debugging "#define DefaultGcc2i386Opt -O0 -g" so if i remove it will it make it faster

Should i include these options or not?

                  #define HasFreetype2 YES
                  #define HasFontconfig YES

Does enableing this mean that the one the one that is installed already will be used instead of a new one being used?

---

### Post by ace2005 on 2005-12-22
> Backup or move your /usr/X11R6 directory. Backup /etc/X11. This step is purely for caution's sake, since everything should be built in (and only in) the build directory you specify in host.def. 

Make /usr/X11R6 a symbolic link to your build directory. 

                  ln -s /opt/Xorg-6.7.99.1 /usr/X11R6

So i rename /usr/X11R6 to something like  /usr/X11R6_BACKUP and then keep going with the rest of the guide? won't just renaming it to create a symbolic link be a bit like pushing over the ladder you're standing on? won't these files be in use? won't everything crash if i do it?

> Backup /etc/X11

Do i make a copy only or make a copy and delete the original or rename the folder??

:confused: :confused: :confused: :confused: :confused: :confused: :confused: :confused:

---

### Post by Iandefor on 2005-12-22
>  Do i make a copy only or make a copy and delete the original or rename the folder?? 

make a copy of the folder /etc/X11 somewhere it'll be easy to keep track of.
My suggestion would be your home directory. DO NOT delete the original until you need to replace it with the backup (IE, X gets buggered up somehow). So: Make a copy only.

---

### Post by ace2005 on 2005-12-22
Ok i'm not trying VMplayer again with Ubuntu, its VERY SLOW, it took 5 mins to boot and i can't stand gnome, i think its something to do wih the splash screen

ok Thanks

---

### Post by poofyhairguy on 2005-12-22
[QUOTE=Evil Whisper]Hello!

What does this do:

Option "DAMAGE" "true"

Thanks,
- Evil Whisper[/QUOTE]


Good question. I honestly don't even want to try to sound smart and guess. I mean....I know what damage does:

[http://www.freedesktop.org/Software/XDamage](http://www.freedesktop.org/Software/XDamage)

I will say that that section I pulled straight from the Xorg mailing list....so its from a trusted source.

---

### Post by daveisadork on 2005-12-22
Hey, just wanted to drop in here and let you know about my experience with this. I have a P4 3.0GHz, 1GB of RAM and a GeForce PCX5750. Using xcompmgr with the official NVIDIA drivers is ridiculously fast. Having shadows enabled actually makes the computer feel *more* responsive than without. Anyway, thanks for the guide... it's been working great for me (very stable, too) ever since I moved to Breezy.

---

### Post by poofyhairguy on 2005-12-22
[QUOTE=daveisadork]Having shadows enabled actually makes the computer feel *more* responsive than without.[/QUOTE]

There is good reason for that. When you turn on xcompmgr you do more than get shadows- you begin to use the power of your computer in a new way to render your desktop.

Thats why I am jumping up and down about it!

---

### Post by Iandefor on 2005-12-22
[quote=poofyhairguy]There is good reason for that. When you turn on xcompmgr you do more than get shadows- you begin to use the power of your computer in a new way to render your desktop.

Thats why I am jumping up and down about it![/quote] I was wondering why you were so excited about it... :p

---

### Post by Evil Whisper on 2005-12-22
[QUOTE=poofyhairguy]Good question. I honestly don't even want to try to sound smart and guess. I mean....I know what damage does:

[http://www.freedesktop.org/Software/XDamage](http://www.freedesktop.org/Software/XDamage)

I will say that that section I pulled straight from the Xorg mailing list....so its from a trusted source.[/QUOTE]

Thanks for the info poofyhairguy.  When i first saw the name "Damage" I thought OMG why would I want to damage anything :-P its a very missleading name...

I've been playing around with the xcompmgr for a while I used it for about 3 - 5 hours it was great!  I liked it a lot except after a while weird things started to use 20%+ of CPU usage and the Side Candy CPU monitor was flashing red and saying 100% and my fans came on and started running at full RPM because of the high load so I removed it and restarted X and all returned to normal.

I do hope that this gains some more stability in the future.  The only problem now is its hard to go without the fade and transparency and shadows.  Very addicting (SP?)

Thanks,
- Evil Whisper

---

### Post by poofyhairguy on 2005-12-22
[QUOTE=Evil Whisper]Thanks for the info poofyhairguy.  When i first saw the name "Damage" I thought OMG why would I want to damage anything :-P its a very missleading name...[/QUOTE]

Kinda. Think about it in general terms: the screen is "damaged" when you move things around on it!

> 
I've been playing around with the xcompmgr for a while I used it for about 3 - 5 hours it was great!  I liked it a lot except after a while weird things started to use 20%+ of CPU usage and the Side Candy CPU monitor was flashing red and saying 100% and my fans came on and started running at full RPM because of the high load so I removed it and restarted X and all returned to normal.

You hit the memory wall. My 128 mb card hits that wall too. When you use drop shadows, Xcompmgr has a bad memory leak. When the leak runs over how much RAM for video card has....the CPU starts having to make up for it....and it all slows down. The only solution now is to have a 256mb or 512mb card, or avoid shadows. Thank Rasterman for this info.

> 
I do hope that this gains some more stability in the future.  The only problem now is its hard to go without the fade and transparency and shadows.  Very addicting (SP?)


Very addicting. If you find you can't do without, I suggest trying KDE. Its compositor is far more mature- I have not experianced the same memory problem with it.

---

### Post by jannol on 2005-12-22
This is really funny, I installed the latest nvidia drivers from today 22:th dec and I have no strange artifacts or pixelerrors as I did before.

This is my current setup workarounds...

**First Bug: Media Players Crash or Have Artifacts When in Full Screen Mode**

I use vlc and set output to X11 - No artifacts
MPlayer also works - No artifacts
Totem - Artifacts in fullscreen

**Second Bug: When you try to logout in Gnome, it seems to crash!**

modified toggle_xcompmgr.bash a little and put it as a Logout button in the panel

here is my toggle_xcompmgr.bash

```
#!/bin/bash
a=`ps -aef | grep -i xcompmgr | awk ' {if ($8 == "xcompmgr"){printf "2"}} '`
if  [[ x$a = x ]]
then
#xcompmgr -cCfF -D3 -r10 &
xcompmgr -cfF -D 2 -O -r8 &
#xcompmgr -c
killall gnome-panel
else
kill -9 `ps -aef | grep -i xcomp | awk ' {if ($8 == "xcompmgr"){printf $2}} '`
gnome-session-save --kill
fi
```

**Third and Fourth Bug:Games and screensavers**

As mentioned before by poofyhairguy

**Fifth Bug: Xcompmgr crashes when using Firefox!**

I don't use firefox, I use opera and it works great.

**Sixth Bug: Xcompmgr Crashing when you are doing important things.**

As mentioned before by poofyhairguy

**Seventh Bug: Problems with Flash in Firefox.**

I had issues with opera aswell so I

```
sudo gedit /usr/bin/opera
```

and changed it to look like this >

```
# Location of the Opera binaries
OPERA_BINARYDIR=/usr/lib/opera/8.50-20050916.1/
export OPERA_BINARYDIR
export XLIB_SKIP_ARGB_VISUALS=1
```

**Eighth Bug: You get addicted to using xcompmgr and can't go back.**

Well, at least I can share my excitement with my demos ;P

I also wonder if anyone have a good idea of how the transd opacity could be really useful. Only things that I can think of is if one wanna compare something or maybe just for a bit better overview of running apps. I don't use the mouse focus thingy but WIN-key to toggle opacity so I can check my server logging and gaim quickly but other than that I can't really find any big use of it.

I must say that I really have fun cause of ubuntuforums, all the ideas, thoughts and so on. Well I made a short demo again, let me know if you want me to stop with those. This time it should work with most media players, the first one I made does not work well with other than vlc.

Here's the [demo](http://linux.jannol.com/ubuntu/demos/demo-0.mpg) DIVX 19.2 MB 2:15 min 1280x1024

Unfortuneately my computer is a bit slow when recording so the effects does not appear exactly as IRL.

I don't know if this already exist but I made xcompmgr-1.1.3_1.1.3-1_i386.deb from xcompmgr-1.1.3.tar.gz  and it worked for me, but that xvidcap_1.1.3-p7_i386.deb from sourceforge did not.

Since I am trying to learn all kind of stuff, can someone experienced try my deb and let me know if it is any good?! [http://linux.jannol.com/ubuntu/debs/xcompmgr-1.1.3_1.1.3-1_i386.deb](http://linux.jannol.com/ubuntu/debs/xcompmgr-1.1.3_1.1.3-1_i386.deb)

BTW: How can I check if there is a memory leak and how big it is? Is it Xorg that grows and grows in memory usage?

---

### Post by poofyhairguy on 2005-12-22
> **jannol]This is really funny, I installed the latest nvidia drivers from today 22:th dec and I have no strange artifacts or pixelerrors as I did before.

This is my current setup workarounds...

**First Bug: Media Players Crash or Have Artifacts When in Full Screen Mode**

I use vlc and set output to X11 - No artifacts
MPlayer also works - No artifacts
Totem - Artifacts in fullscreen

**Second Bug: When you try to logout in Gnome, it seems to crash!**

modified toggle_xcompmgr.bash a little and put it as a Logout button in the panel

here is my toggle_xcompmgr.bash

```
#!/bin/bash
a=`ps -aef | grep -i xcompmgr | awk ' {if ($8 == "xcompmgr"){printf "2"}} '`
if  [[ x$a = x ]]
then
#xcompmgr -cCfF -D3 -r10 &
xcompmgr -cfF -D 2 -O -r8 &
#xcompmgr -c
killall gnome-panel
else
kill -9 `ps -aef | grep -i xcomp | awk ' {if ($8 == "xcompmgr"){printf $2}} '`
gnome-session-save --kill
fi
```

**Third and Fourth Bug:Games and screensavers**

As mentioned before by poofyhairguy

**Fifth Bug: Xcompmgr crashes when using Firefox!**

I don't use firefox, I use opera and it works great.

**Sixth Bug: Xcompmgr Crashing when you are doing important things.**

As mentioned before by poofyhairguy

**Seventh Bug: Problems with Flash in Firefox.**

I had issues with opera aswell so I

```
sudo gedit /usr/bin/opera
```

and changed it to look like this >

```
# Location of the Opera binaries
OPERA_BINARYDIR=/usr/lib/opera/8.50-20050916.1/
export OPERA_BINARYDIR
export XLIB_SKIP_ARGB_VISUALS=1
```

**Eighth Bug: You get addicted to using xcompmgr and can't go back.**

Well, at least I can share my excitement with my demos  said:**
> demo[/url] DIVX 19.2 MB 2:15 min 1280x1024

Unfortuneately my computer is a bit slow when recording so the effects does not appear exactly as IRL.

I don't know if this already exist but I made xcompmgr-1.1.3_1.1.3-1_i386.deb from xcompmgr-1.1.3.tar.gz  and it worked for me, but that xvidcap_1.1.3-p7_i386.deb from sourceforge did not.

Since I am trying to learn all kind of stuff, can someone experienced try my deb and let me know if it is any good?! [http://shr.jannol.com/ubuntu/debs/xcompmgr-1.1.3_1.1.3-1_i386.deb](http://shr.jannol.com/ubuntu/debs/xcompmgr-1.1.3_1.1.3-1_i386.deb)

BTW: How can I check if there is a memory leak and how big it is? Is it Xorg that grows and grows in memory usage?


First of all- great post! You just inspired me to try the new Nvidia driver. Mind If I put that deb in the initial post of the thread?

Second of all- the way to tell (memory leak) is if suddenly at some point you CPU rockets to 100% and stays there. Add the "system monitor" to the Gnome Panel to keep and eye on it.

Third of all, thanks for the movie. Can I put a link to it in the first post too?

Fourth: Can you give me pointers on how you made that deb? I want to make an AMD 64 one.

---

### Post by poofyhairguy on 2005-12-22
Fans of Xcompmgr! I talk about its fate today in my new Eye Candy blog entry. Look here to see:

[http://doc.gwos.org/index.php/Poofyhairguy%27s_Eye_Candy_Report](http://doc.gwos.org/index.php/Poofyhairguy%27s_Eye_Candy_Report)

Or if its down, look here:

[http://linuxeyecandy.blogspot.com/](http://linuxeyecandy.blogspot.com/)

---

### Post by jannol on 2005-12-22
[QUOTE=poofyhairguy]First of all- great post! You just inspired me to try the new Nvidia driver. Mind If I put that deb in the initial post of the thread?

Second of all- the way to tell (memory leak) is if suddenly at some point you CPU rockets to 100% and stays there. Add the "system monitor" to the Gnome Panel to keep and eye on it.

Third of all, thanks for the movie. Can I put a link to it in the first post too?

Fourth: Can you give me pointers on how you made that deb? I want to make an AMD 64 one.[/QUOTE]

Sure you can put the deb in the first post but please make sure it works first ;P

Link to the movie? Of course!!! Spread the fun ;P

How I made a deb?

```
sudo apt-get install checkinstall
```

then build as usual but instead of
```
sudo make install
```

you type
```
sudo checkinstall
```

---

### Post by poofyhairguy on 2005-12-22
[QUOTE=jannol]Sure you can put the deb in the first post but please make sure it works first ;P
[/QUOTE]

If I get my chroot working tonight I will. Can anyone else test? Please.

And thanks for the guide. I have a lot of debs to make now.

---

### Post by poofyhairguy on 2005-12-23
LARGEST EDIT EVER!!!!!!


Look at first post.

---

### Post by poofyhairguy on 2005-12-23
I could almost pee on myself!!!!!


With newest Nvidia driver the log-out bug is gone!!!!!

---

### Post by poofyhairguy on 2005-12-23
Thanks to Jannol I now have a 64 bit deb of the newest xcompmgr for everyone!

Please enjoy, and remember December 22, 2005- the day the Linux Desktop got modernized!

---

### Post by rosslaird on 2005-12-23
> I could almost pee on myself!!!!!

Well, I wouldn't go that far, but on my system the newest nvidia driver does indeed deliver a completely stable composite environment (I'm using xfwm in gnome and xfce).

Ross

---

### Post by poofyhairguy on 2005-12-23
Ok. I have found one way to make it crash. An old bug I found a while back does it.

What ever you do, do NOT cross a playing video file (or audio visualization) under the Gnome-Panel. A hard lock up awaits you if you do.

Otherwise it seems to be stable.

Thank you Nvidia for giving me what I really wanted for Xmas!

---

### Post by jannol on 2005-12-23
not for me :(

---

### Post by poofyhairguy on 2005-12-23
[QUOTE=jannol]not for me :([/QUOTE]


Explain more please!!! Reproduce the bug! I need to know so I can find a work around. 

I hear 3D desktop kills it (no surprise there). And there is the gnome-panel thing. What other bugs are going on?

---

### Post by rosslaird on 2005-12-23
[QUOTE=]I hear 3D desktop kills it (no surprise there).[/QUOTE]

Not on my system. 3ddesktop works perfectly.

---

### Post by poofyhairguy on 2005-12-23
[QUOTE=rosslaird]Not on my system. 3ddesktop works perfectly.[/QUOTE]

I must try. 

Skippy-xd works well.

---

### Post by jannol on 2005-12-23
I use XDMCP in gdm because I use my old laptop as a thin client, when I disabled XDMCP it works almost every time.

I get this error in /var/log/daemon.log when XDMCP is on

```
Dec 23 08:06:47 localhost gdm[8707]: gdm_slave_xioerror_handler: Ödesdigert X-fel - Startar om :0
```

Actually, if I wait for a while and do not press Esc it restarts gdm and I can simply log in. When this happens I never get any logout options, it kinda freeze like before except it restarts gdm.

I am not absolutely sure if it has to do with XDMCP, I'll have to dig into a bit more.

---

### Post by poofyhairguy on 2005-12-23
[QUOTE=jannol]I use XDMCP in gdm because I use my old laptop as a thin client, when I disabled XDMCP it works almost every time.

I get this error in /var/log/daemon.log when XDMCP is on

```
Dec 23 08:06:47 localhost gdm[8707]: gdm_slave_xioerror_handler: Ödesdigert X-fel - Startar om :0
```

Actually, if I wait for a while and do not press Esc it restarts gdm and I can simply log in. When this happens I never get any logout options, it kinda freeze like before except it restarts gdm.

I am not absolutely sure if it has to do with XDMCP, I'll have to dig into a bit more.[/QUOTE]

This is the stuff good bugreports are made off. Please get more info.

---

### Post by nocturn on 2005-12-23
I tried your guide, thanks for it, but my Nvidia driver locks up (Xid 13) :-(

---

### Post by jannol on 2005-12-23
Hmm, about the logout issue...

I take it back I guess, it is probably not XDMCP, it simply works from time to time but I do not have a clue, I checked a lot of settings, log files and so on but I can't tell why it does work occasionally. I also tried building xcompmgr the usual way but it is just the same.

If it does work for others please let me know if it is me that fu-ked up or not.

For now I can live with my logoout button so it is not really an issue for me but... you know... ;)

---

### Post by poofyhairguy on 2005-12-23
[QUOTE=nocturn]I tried your guide, thanks for it, but my Nvidia driver locks up (Xid 13) :-([/QUOTE]


What card you have? You should tell Nvidia about that. Really. I hear they are good with bug reports.

---

### Post by nocturn on 2005-12-23
[QUOTE=poofyhairguy]What card you have? You should tell Nvidia about that. Really. I hear they are good with bug reports.[/QUOTE]

I have Nvidia Geforce GO card, but I had the same issue with my old Geforce MX in my desktop.  I filed a bug report on the desktop card a while back, but they basicly tell you to turn RenderAccel off.

There is a Ubuntu Bug open for this too at: [https://bugzilla.ubuntu.com/show_bug.cgi?id=7183](https://bugzilla.ubuntu.com/show_bug.cgi?id=7183)

---

### Post by jannol on 2005-12-23
have you tried the nvidia-glx-legacy driver from ubuntu repos?

---

### Post by nocturn on 2005-12-23
[QUOTE=jannol]have you tried the nvidia-glx-legacy driver from ubuntu repos?[/QUOTE]

The legacy driver is for older types of cards, mine are included in the normal driver module.  They work fine, except for the lockups, for which the cause is unknown (many people report them, though only in specific combination of hardware, driver and kernels...

---

### Post by poofyhairguy on 2005-12-23
[QUOTE=nocturn]I have Nvidia Geforce GO card, but I had the same issue with my old Geforce MX in my desktop.  I filed a bug report on the desktop card a while back, but they basicly tell you to turn RenderAccel off.

There is a Ubuntu Bug open for this too at: [https://bugzilla.ubuntu.com/show_bug.cgi?id=7183](https://bugzilla.ubuntu.com/show_bug.cgi?id=7183)[/QUOTE]

Yeah, my girlfriends laptop has renderaccel problems too and its a Geforce Go card. I guess the Nvidia guys/gals are leaving the older ones out.

---

### Post by kleeman on 2005-12-23
This may be of relevance for nvidia users:

Description: NVIDIA Linux Display Driver (8178 )

Changelog:

    * Fixed a problem where certain precompiled kernel interfaces were not recognized.
    * Improved stability with the Composite X extension.
    * Fixed a corruption bug with RenderAccel and the Composite X extension when using wide desktops.
    * Fixed a problem validating HDTV modes on GeForce 6200.
    * Fixed detection of certain older TV encoders.
    * Fixed installation problems with Linux kernel source trees using separate KBUILD output directories.
    * Fixed installation problems on newer Debian systems.
    * Added support for NVIDIA SLI. Please see the README for details.
    * Added a new utility 'nvidia-xconfig', which is a commandline tool for updating X configuration files.

---

### Post by nocturn on 2005-12-23
[QUOTE=kleeman]This may be of relevance for nvidia users:

Description: NVIDIA Linux Display Driver (8178 )

Changelog:

    * Fixed a problem where certain precompiled kernel interfaces were not recognized.
    * Improved stability with the Composite X extension.
    * Fixed a corruption bug with RenderAccel and the Composite X extension when using wide desktops.
    * Fixed a problem validating HDTV modes on GeForce 6200.
    * Fixed detection of certain older TV encoders.
    * Fixed installation problems with Linux kernel source trees using separate KBUILD output directories.
    * Fixed installation problems on newer Debian systems.
    * Added support for NVIDIA SLI. Please see the README for details.
    * Added a new utility 'nvidia-xconfig', which is a commandline tool for updating X configuration files.[/QUOTE]


This makes me wanna update....

Anyone running these drivers on Breezy?  Did they cause much breakage?

---

### Post by jannol on 2005-12-23
using them in my demo and poofyhairguy also installed them and the work great.

I have a Nvidia 6800 LE unlocked all pipes and flashed to 400@900 which btw gave me artifacts in 2D and 3D in win XP.

---

### Post by Evil Whisper on 2005-12-23
Will these new drivers work with my GeForce FX5500?

Also does anyone have any ideas how I can fix the memory leak that suddenly occurs after 5 hours of use?

Edit: Does anyone have a how-to to update my drivers to the new ones?
Edit2: Could I just compile the drivers and install using check install?

Thanks,
- Evil Whisper

---

### Post by jannol on 2005-12-23
* The drivers will probably work for your card since it is not very old or unusual

* I think the memory leak or cpu load still is an issue even with Dapper, My comp gets sluggish after about approx. 6-8 hours, when it happens, I use my toggle button and turn off/on xcompmgr and then it runs for 6-8 hours again, still searching for a solution.

* Installation help can be found
[http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+driver](http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+driver)
and
[http://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/chapter-02.html#id2504480](http://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/chapter-02.html#id2504480)

* You could probably use checkinstall but if you build and compile you need a bunch if dev libs, I do not now which

---

### Post by Evil Whisper on 2005-12-23
Edit: Thanks!

I installed the kernel source extracted it and then installed the kernel headers and I'm running the new drivers now!

I'll give the xcompmgr another go.

I still have the log-out bug is there any way to fix that I'm running the latest nvidia drivers.

---

### Post by hectorC on 2005-12-23
[QUOTE=poofyhairguy]I could almost pee on myself!!!!!


With newest Nvidia driver the log-out bug is gone!!!!![/QUOTE]
 
Not for me. I updated the nvidia drivers to the latest and still can't see the log-out screen.

I have a nvidia 6600.

Hector

---

### Post by Evil Whisper on 2005-12-23
[QUOTE=poofyhairguy]
You hit the memory wall. My 128 mb card hits that wall too. When you use drop shadows, Xcompmgr has a bad memory leak. When the leak runs over how much RAM for video card has....the CPU starts having to make up for it....and it all slows down. The only solution now is to have a 256mb or 512mb card, or avoid shadows. Thank Rasterman for this info.
[/QUOTE]

My GeForce FX5500 is a 256mb card.
I guess I'll disable drop shadows then.
I do hope that in future releases they
fix this memory leak in drop shadows
as they are one of my favorite parts
about xcompmgr. :p

I'm also looking for a way to exclude gdesklets from xcompmgr's effects because of the larger semi transparent square around them.

Also is there a way to automatically set inactive windows to transset 0.5? And return them to 1 when they become active again?

Edit: I've heard there has been a release newer then the one in the ubuntu repositories.
Where could I find this?  And once I do find it if I make a deb using check install could I post
it here?

---

### Post by Iandefor on 2005-12-23
Oh my word... I'd been planning on running this on my next computer (Due around January) full-time, but I just couldn't wait, so I enabled compositing, got xcompmgr and transd... I have fallen in love with the visual effects, so much so I'm going to keep these effects as long as I can tolerate the horrible slowness it engenders on this computer. Thank you so much, Poofyhairguy! this is probably the greatest effect I've seen on computers, ever... one note, though: it doesn't seem like Enlightenment DR16 and xcompmgr play nicely together; upon logging in using E and xcompmgr, anything that E was taking care of (Window borders, the desktop background) simply turned black. Running xfdesktop and xfwm4 is a suitable replacement, though.

---

### Post by poofyhairguy on 2005-12-23
[QUOTE=nocturn]
Anyone running these drivers on Breezy?  Did they cause much breakage?[/QUOTE]

I am. No breakage for me.

---

### Post by poofyhairguy on 2005-12-23
[QUOTE=hectorC]Not for me. I updated the nvidia drivers to the latest and still can't see the log-out screen.

I have a nvidia 6600.

Hector[/QUOTE]


So close to my set up yet they are so different. 

Sometimes x86 land is frustrating.

Are you using newest Xcompmgr?

---

### Post by poofyhairguy on 2005-12-23
[QUOTE=Evil Whisper]My GeForce FX5500 is a 256mb card.
I guess I'll disable drop shadows then.
I do hope that in future releases they
fix this memory leak in drop shadows
as they are one of my favorite parts
about xcompmgr. :p

Also is there a way to automatically set inactive windows to transset 0.5? And return them to 1 when they become active again?[/QUOTE]

Sounds like you need to try KDE. Its compositor has better drop shadows support, and it does the "make non active windows translucent thing."

> 
I'm also looking for a way to exclude gdesklets from xcompmgr's effects because of the larger semi transparent square around them.

If you are talking about the shadows its impossible (well...not impossible...just damn close). If you are talking about transparancies I think the newest gdesklets actually supports Xcompmgr! Its an option somewhere (to checkmark).

> 
Edit: I've heard there has been a release newer then the one in the ubuntu repositories.
Where could I find this?  And once I do find it if I make a deb using check install could I post
it here?

deb in this post:

[http://ubuntuforums.org/showpost.php?p=597951&postcount=251](http://ubuntuforums.org/showpost.php?p=597951&postcount=251)

---

### Post by poofyhairguy on 2005-12-23
[QUOTE=Iandefor]Oh my word... I'd been planning on running this on my next computer (Due around January) full-time, but I just couldn't wait, so I enabled compositing, got xcompmgr and transd... I have fallen in love with the visual effects, so much so I'm going to keep these effects as long as I can tolerate the horrible slowness it engenders on this computer. Thank you so much, Poofyhairguy! this is probably the greatest effect I've seen on computers, ever... one note, though: it doesn't seem like Enlightenment DR16 and xcompmgr play nicely together; upon logging in using E and xcompmgr, anything that E was taking care of (Window borders, the desktop background) simply turned black. Running xfdesktop and xfwm4 is a suitable replacement, though.[/QUOTE]


Yeah...the Enlightenments don't play well with Xcompmgr. Hence the lack of an Enlightened Gnome Guide for Breezy from me.

---

### Post by jannol on 2005-12-23
Now it's xmas in gmt+1

[Merry Christmas](http://shr.jannol.com/ubuntu/xmas.mpg)

---

### Post by Evil Whisper on 2005-12-23
Thanks for the info poofyhairguy, I got gdesklets running perfect now.
The only thing left to fix is the logout bug. :-(

Would it be possible to script the make non active windows transparent thing,
maybe using a bash script or a perl script and then adding it either to your gnome session
or a cron job?

(It would have to check the window status and then run transset 0.5 on it).

---

### Post by varunus on 2005-12-23
transd, posted somewhere in this thread by RAOF, does exactly what you just said; it sets inactive windows to a different transparency.

---

### Post by Evil Whisper on 2005-12-23
Thanks for telling me about that heres the link:
[http://www.ubuntuforums.org/showpost.php?p=500959&postcount=112](http://www.ubuntuforums.org/showpost.php?p=500959&postcount=112)

Woo Hoo! Now I can stop wishing I had a mac because of the drop shadows and eye candy.

I'm using:
**xcompmgr -fF -I-.002 -O-.003 -D6 && ./transd &**

Everything is fast and responsive been using the above setting **without** transd for about 5 hours so far today using the latest nvidia drivers ( 8178 ) and no crashes or memory leaks so far.

---

### Post by poofyhairguy on 2005-12-23
[QUOTE=Evil Whisper]Thanks for the info poofyhairguy, I got gdesklets running perfect now.
The only thing left to fix is the logout bug. :-([/QUOTE]

For me the new drivers fixed it. That tells me its an Nvidia buy. Time for a good bug report so they will fix it:

[email]linux-bugs@nvidia.com[/email]

> 
Would it be possible to script the make non active windows transparent thing,
maybe using a bash script or a perl script and then adding it either to your gnome session
or a cron job?


Such a script exists in this thread.

---

### Post by Evil Whisper on 2005-12-23
Poofy what would I put in a bug report to nvidia?

Edit: Also one thing how would I make my gnome panel stay visible?
when I use any setting without drop shadows it makes the gnome panel
hide under the windows.

Edit2:

Transd crashes on me with the following:
```

X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  15 (X_QueryTree)
  Resource id in failed request:  0x2200376
  Serial number of failed request:  4921
  Current serial number in output stream:  4921

```

---

### Post by shodekiagari on 2005-12-24
Awesome guide, thank you! 

I remember using this way back when and it was slower than slow. But now it runs really smoothly, as nice as my old 500 mhz ibook :D (That's not an insult, it runs well on it...)

I'd just thought I'd add my specs to those who want to get an idea of what kind of hardware it works well with. 1.5 Ghz Pentium IV (I believe) and a NVIDIA Corporation NV11 [GeForce2 MX/MX 400] (from xorg.conf)

I'm using xcompmgr, I had to turn off kde's control as it didn't work and then crashed kde. Also, kcontrol seems to crash my computer now. I'm not sure why. System Settings still works fine.

Also, I changed the D6 in the "best" command to a D2 as the menus were taking too long to appear. I'm impatient... hehe. Just wanted to say thanks to everyone and detail what I went through to get it perfect.

shodekiagari

---

### Post by poofyhairguy on 2005-12-25
[QUOTE=Evil Whisper]Poofy what would I put in a bug report to nvidia?[/QUOTE]

What you have at the bottom of your post.

> 
Edit: Also one thing how would I make my gnome panel stay visible?
when I use any setting without drop shadows it makes the gnome panel
hide under the windows.

You have to kill it. Maybe even a few times. It ALWAYS comes back. This command till you see them:

killall gnome-panel

Edit2:

> 
Transd crashes on me with the following:
```

X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  15 (X_QueryTree)
  Resource id in failed request:  0x2200376
  Serial number of failed request:  4921
  Current serial number in output stream:  4921

```

Send that to Nvidia as it is. Let the response guide you. One bug at a time though. This one first for pratice.

---

### Post by poofyhairguy on 2005-12-25
[QUOTE=shodekiagari]Awesome guide, thank you! 

I remember using this way back when and it was slower than slow. But now it runs really smoothly, as nice as my old 500 mhz ibook :D (That's not an insult, it runs well on it...)

I'd just thought I'd add my specs to those who want to get an idea of what kind of hardware it works well with. 1.5 Ghz Pentium IV (I believe) and a NVIDIA Corporation NV11 [GeForce2 MX/MX 400] (from xorg.conf)

I'm using xcompmgr, I had to turn off kde's control as it didn't work and then crashed kde. Also, kcontrol seems to crash my computer now. I'm not sure why. System Settings still works fine.

Also, I changed the D6 in the "best" command to a D2 as the menus were taking too long to appear. I'm impatient... hehe. Just wanted to say thanks to everyone and detail what I went through to get it perfect.

shodekiagari[/QUOTE]


Thanks! I try my best!

---

### Post by Evil Whisper on 2005-12-25
So the **transd** crash is a nvidia bug?

```

X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  15 (X_QueryTree)
  Resource id in failed request:  0x2200376
  Serial number of failed request:  4921
  Current serial number in output stream:  4921

```

I'm just double checking and If so I'll file a bug report tonight.

---

### Post by poofyhairguy on 2005-12-25
[QUOTE=Evil Whisper]So the **transd** crash is a nvidia bug?

```

X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  15 (X_QueryTree)
  Resource id in failed request:  0x2200376
  Serial number of failed request:  4921
  Current serial number in output stream:  4921

```

I'm just double checking and If so I'll file a bug report tonight.[/QUOTE]

Thing about it is, with Nvidia and composite we don't know where the bugs come from. Do they come from Xcompmgr? From transd? From the composite extension? From the Nvidia driver?

Since the driver is closed we cannot know. So tell them whats going on and they will hopefully respond back with a certain answer. 

All composite bugs should be reported to Nvidia (if you use Nvidia card) because if it IS their fault, only then can they fix it.....

---

### Post by imranj on 2005-12-26
Ok, i have the new composition manager up and running , stable as of now, in KDE 3.4. 

AMD 3.2 Gig , with 512 MB mem and stuff, its ok with but of sluggishness, more optimization and improvements are need to make everything look natural and smooth.

All system are operational and well.

---

### Post by 23meg on 2005-12-26
Longer term report: I've found the combination of the new xcompmgr + Nvidia 7676 drivers + Breezy xorg build to be very stable with my Nvidia Go6200 chip; three or four crashes in about a month.

---

### Post by fannymites on 2005-12-27
WOW! I think I might change to Kubuntu.
I don't use kde on ubuntu but when I last did the kde composite manager seemed horribly slow in comparison to gnome.
Well I'm using kde 3.5 on suse and I've just been fiddling around with the composite manager there and it's fantastic.  Much faster in kde 3.5 and the new "window decorations only" transparency mode is great, very vista.
Couple of problems though, the settings seeme to reset themselves (shadow size etc) every so often though I'm not sure if this is something to do with suse.  The other thing I notice with the kde composite manager in kde is that the shadows seem sharper round the edges but if I run xcompmgr in a terminal they are the same as gnome (this is in ubuntu as well as suse).
Does anyone else notice this?  Also, can anyone recommend a really good setting for shadows using kde's composite manager?  I've got fading and transparency looking just right but I can't seem to get the shadows looking really good.

---

### Post by Cliff76 on 2005-12-27
Hi,

Kubuntu newbie here just migrated from Mepis. I tried the composite thing about six months ago on Mepis and it was horribly slow and buggy. I'm just getting back to a stable system after various twiddlings in Mepis caused me a whole ton of Windows-like-required reboots. I'm afraid to play with anything too cutting edge but after I saw the video I'm not sure I can resist. The one thing I'm afraid of is all of the manual steps in the howto that seem necessary for preventing bugs. I can easily see losing a week or two in time spent adjusting things. My question is what's the easiest way to get started for someone like me running KDE-3.5 on Breezy with the latest NVidia driver? Is is just a matter of putting the lines in my xorg.conf? Can I then play with the composite settings in KControl? Would I have to do the manual legwork required to keep Firefox healthy? I haven't yet installed it but I want to start using superkaramba too as I port my stuff from my Mepis partition. I heard the composite stuff doesn't work well with super-karamba. Is this still true as of current? Will the NVidia driver update help that as well? I'm just nervous to try bleeding edge stuff.

---

### Post by Heretic09 on 2005-12-27
I get "no composite extension" when I try to run xcompmgr. I have an nvidia 5200 with the official drivers from breezy.

This is my xorg.conf:

```

(skipped fonts stuff)
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
	Load	"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel" "true"
	Option		"AllowGLXWithComposite" "true"
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

Can any one see whats causing this?

---

### Post by reet on 2005-12-27
Heretic09, perhaps try to move Section Extensions above Section Device? That's all I can think of.

---

### Post by Heretic09 on 2005-12-27
> Heretic09, perhaps try to move Section Extensions above Section Device? That's all I can think of.

Tried that, same issue.

---

### Post by poofyhairguy on 2005-12-27
[QUOTE=Heretic09]I get "no composite extension" when I try to run xcompmgr. I have an nvidia 5200 with the official drivers from breezy.

This is my xorg.conf:

```

(skipped fonts stuff)
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
	Load	"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel" "true"
	Option		"AllowGLXWithComposite" "true"
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

Can any one see whats causing this?[/QUOTE]

My best advice would be to move the composite part to the end- after the dri part.

---

### Post by poofyhairguy on 2005-12-27
[QUOTE=Cliff76]Hi,

Kubuntu newbie here just migrated from Mepis. I tried the composite thing about six months ago on Mepis and it was horribly slow and buggy. I'm just getting back to a stable system after various twiddlings in Mepis caused me a whole ton of Windows-like-required reboots. I'm afraid to play with anything too cutting edge but after I saw the video I'm not sure I can resist. The one thing I'm afraid of is all of the manual steps in the howto that seem necessary for preventing bugs. I can easily see losing a week or two in time spent adjusting things. My question is what's the easiest way to get started for someone like me running KDE-3.5 on Breezy with the latest NVidia driver? Is is just a matter of putting the lines in my xorg.conf? [/QUOTE]

Install new Nvidia drivers. Fix up Xorg.conf. My advice section is mostly for Xcompmgr. Just know that it might crash on you one day....and you will be fine.

> 
Can I then play with the composite settings in KControl? Would I have to do the manual legwork required to keep Firefox healthy? I haven't yet installed it but I want to start using superkaramba too as I port my stuff from my Mepis partition. I heard the composite stuff doesn't work well with super-karamba. Is this still true as of current? Will the NVidia driver update help that as well? I'm just nervous to try bleeding edge stuff.

If you are scared, they maybe stay away. We are on the knife edge here. I say its stable, but thats my definition of stable. As in "unless I do one of the things I know will crash it, it only crashes once a week on its own."

The problem with superkaramba and gdesklets is that they have drop shadows. I have no solution to this problem.

Good luck.

---

### Post by Heretic09 on 2005-12-27
I'm a dumbass. I was doing it through an NX session with the moronic assumption that it should work. Note to self xcompmgr and/or transset  does not work through freenx.

---

### Post by Heretic09 on 2005-12-27
Does any one know how to apply transparancy just to one app? eg Yakuake or Konsole? As in when the app starts up its automatically semi transparent where as in transset you would have to manually select the app you want to be transparent every time.

---

### Post by imranj on 2005-12-28
I just upgraded to KDE 3.5 and i have noticed improved performance.

In the rendering of the effects, but i still feel that it doesn't use it or provides the smoothness like i get in OSX.

Is it due to fact that its still "Composite manager" is still a work in progress.

---

### Post by oobuntoo on 2005-12-28
Does anyone know of any way to make KDE panel uses REAL transparency (not the fake one you get thru configuring panel)? Seems like the KDE built-in composite manager only affect apps.

---

### Post by Cyfr on 2005-12-28
I have a ATI 9800pro that I used for gaming on windows.. now I really want these sexy effects on my  Ubuntu install..

Could anyone recommend a nvidia card ( i guess ) that will do what I want perfectly and not lag or whatever, but I dont want a gamers card since I havn't played games in ages and prolly won't ever on Linux

---

### Post by imranj on 2005-12-28
Yeah u can do that, its the same go to settings>desktop>window behaviour>Translucency Tab and the option active tabs.

Cool yeah, and yeah for best performance switch off shadows,as its for me a big drag, see if u can manage yeah dude.

---

### Post by imranj on 2005-12-28
[QUOTE=Cyfr]I have a ATI 9800pro that I used for gaming on windows.. now I really want these sexy effects on my  Ubuntu install..

Could anyone recommend a nvidia card ( i guess ) that will do what I want perfectly and not lag or whatever, but I dont want a gamers card since I havn't played games in ages and prolly won't ever on Linux[/QUOTE]

Get the best mid-class current card, i am not sure which one, but the newest one should do and yeah its damm stable with the latest drivers okie

---

### Post by Cyfr on 2005-12-28
Thats what im asking.. ive no idea what the best mid-class card is :p
I dont want to spend too much, but im not on a shoestring budget so want something that will do the task at hand (and future tasks that may appear!)

---

### Post by billputer on 2005-12-28
For a mid-range Nvidia graphics card, I'd recommend the 6600GT.  I'm running an XFX 6600GT and it works perfectly with the nvidia drivers from the repos.  Looking at the most recent price guide in Anandtech it'll probably cost you about $150 for one.

Further reading:  
[http://www.anandtech.com/guides/showdoc.aspx?i=2639&p=3](http://www.anandtech.com/guides/showdoc.aspx?i=2639&p=3)

---

### Post by jannol on 2005-12-28
I am using 6800 LE and it works great. I guess a standard 6600 will do just fine, those can be found for about $100

<edit>
billputer, haha I was to slow, well 6600GT is also great
</edit>

---

### Post by varunus on 2005-12-28
Heck, if you're not playing games, you could get away with an NVIDIA 5000 series card.

You could also buy an ATI 92XX for $25 and set up EXA for special effects like the first post shows...you may need dapper for this though, which is unstable.

---

### Post by piedamaro on 2005-12-28
I found that killing gnome-panel destroy the purpose of using -C because the panel still has drop shadows, and it probably crashes applications with a notification icon.
Killing metacity instead of gnome-panel solves both of these problems for me, what do you think?

---

### Post by Iandefor on 2005-12-28
[quote=poofyhairguy]Yeah...the Enlightenments don't play well with Xcompmgr.[/quote] They don't, eh? Do you know if Raster plans on working out how to get E to work with xcompmgr?

---

### Post by poofyhairguy on 2005-12-28
[QUOTE=Cyfr]
Could anyone recommend a nvidia card ( i guess ) that will do what I want perfectly and not lag or whatever, but I dont want a gamers card since I havn't played games in ages and prolly won't ever on Linux[/QUOTE]

A 6600 GT. Thats what I got for this stuff, works great.


A 6600 might work. Any less is wasting money. A 5xxx series one I have is MUCH slower and crashier than my 6600 GT.

---

### Post by poofyhairguy on 2005-12-28
[QUOTE=varunus]
You could also buy an ATI 92XX for $25 and set up EXA for special effects like the first post shows...you may need dapper for this though, which is unstable.[/QUOTE]

True. But get the 256mb one if you do that.

---

### Post by MistaED on 2005-12-28
Hey I was wondering (not sure if someone else has asked this) but is it possible to upgrade breezy's xorg to 7.0 or just 6.9 at least? I'd like to show off someone's slow pc that it can be fast and pretty again (it has a nice Ati 9200 in it) but I don't want them to run the unstable dapper drake for it.

Thanks
-MistaED

---

### Post by poofyhairguy on 2005-12-28
[QUOTE=Iandefor]They don't, eh? Do you know if Raster plans on working out how to get E to work with xcompmgr?[/QUOTE]

Not really. Rasterman wants eye candy everyone can use, and thats not composite for at least two years.

---

### Post by poofyhairguy on 2005-12-28
[QUOTE=imranj]
In the rendering of the effects, but i still feel that it doesn't use it or provides the smoothness like i get in OSX.

Is it due to fact that its still "Composite manager" is still a work in progress.[/QUOTE]

Its because in OSX the entire Xserver like thing is built from the ground up for this stuff. We are bolting it on.

OSX is three to five years ahead in this area.

---

### Post by piedamaro on 2005-12-29
I made a script: it fades unfocused windows and gives 100% opacity to the focused one. Pretty neat but somewhat resource hungry. Inspired by eutotrans.rb by Daniel Forchheimer.
It depends on bash and standard X tools only, and should work with other WMs too (tested with metacity).
```
#!/bin/sh
# This is a script that uses transset-df or any other transset-
# patch that can take an window id as argument to allow
# opacity to follow the focused window.
# The focused window get opacity 1.0 while all others
# have opacity set by the var 'FADING' in this script

# It is licensed under the GNU GPL license
# http://www.gnu.org/licenses/gpl.html
# This program is written by: Luca De Rugeriis
# inspired by the work of Daniel Forchheimer (eutotrans.rb)
# Last update: 2005-12-29

FADING=0.85
TRANSSET="/usr/bin/transset-df"

#fade all windows
WINDOWS_LIST=`xwininfo -root  -children | grep -v panel | sed '1,6d' | grep -v 0x1000021 | cut -d " " -f 6`
for i in $WINDOWS_LIST;do
        $TRANSSET --id $i $FADING
done

LAST_FOCUSED=0

while (true); do
        FOCUSED=`xdpyinfo | grep focus | cut -c 16-24`
        if [ $LAST_FOCUSED != $FOCUSED ]; then
                $TRANSSET --id $FOCUSED 1
                $TRANSSET --id $LAST_FOCUSED -t $FADING
                LAST_FOCUSED=$FOCUSED
        fi
        sleep .1
done

```

To launch and kill it I use modified version of frodon's script:
```
#!/bin/bash

if [ "$(pidof xcompmgr)" ]
then
        killall xcompmgr
	for i in `ps ax|grep eutotrans|grep -v grep |cut -d " " -f 1`;do
		kill $i
	done
	sleep .5
	killall metacity

else
        xcompmgr -fF -I.02 -O.02 -D6 -cC  -t-4 -l-8 -r5&
	~/bin/eutotrans-clean.sh&
	sleep .5
	killall metacity
fi

```

Have fun!

---

### Post by zenlunatic on 2005-12-29
Will this work on PowerPC?  Also how will it run on a 600mhz with 8 megs of video ram?

---

### Post by poofyhairguy on 2005-12-29
[QUOTE=zenlunatic]Will this work on PowerPC?  Also how will it run on a 600mhz with 8 megs of video ram?[/QUOTE]

I honestly have no idea. 

Try it and tell me.

You might have to compile your own xcompmgr though. Maybe not. Try installing it in synaptic.

---

### Post by jeffreyvergara.NET on 2005-12-30
how do you make gdesklet always on top when composite manager is on? the gdesklet will be always on top again if i turned of composite manager.

---

### Post by Footer on 2005-12-30
Cool stuff.  Just discovered this the other day.  Got it up and running and been playing with it for just a short time.  I have a quick question though.  My task bar and SuperKaramba apps on the desktop seem to be a bit more faded/washed out when I have translucency enabled.  They're bright and fine when not enabled.  Is there some way to make them bright yet still keep translucency enabled?

Thanks!

:)

---

### Post by fannymites on 2005-12-30
Has anyone here tried running kwin in dapper (gnome)?  Last time I tried kwin in gnome was in debian a while back and it was hopeless but in dapper it's running perfectly and not a single crash so far.  The kwin composite manager is so much better.
[[IMG]http://img424.imageshack.us/img424/8443/dapper8hc.th.png[/IMG]](http://img424.imageshack.us/my.php?image=dapper8hc.png)

---

### Post by poofyhairguy on 2005-12-30
[QUOTE=jeffreyvergara.NET]how do you make gdesklet always on top when composite manager is on? the gdesklet will be always on top again if i turned of composite manager.[/QUOTE]


Gdesklets kinda misbehave. I still haven't nailed this down yet.

---

### Post by greenwom on 2005-12-30
Well I'm not a gamer but I wanted a little more muscle in the DVD area so I picked up a FX 5500 and it works great.  I just went through this how to but I went went from 0 swap to  ```
mike1@ubuntu3:~$ free
             total       used       free     shared    buffers     cached
Mem:        644804     289200     355604          0      20980     104316
-/+ buffers/cache:     163904     480900
Swap:      1614492      99876    1514616
mike1@ubuntu3:~$

```
And that's after killing about 20 bash entries in the system monitor.  should compositing swamp the system this bad?  
Looks good anyway, I'm going without the drop shadows (I'll wait for more stability)

---

### Post by piedamaro on 2005-12-31
```
#!/bin/bash
a=`ps -aef | grep -i xcompmgr | awk ' {if ($8 == "xcompmgr"){printf "2"}} '`
if  [[ $a = "" ]]
then
	xcompmgr -fFcC &
	killall gnome-panel
else
	kill -9 `ps -aef | grep -i xcomp | awk ' {if ($8 == "xcompmgr"){printf $2}} '`
	killall gnome-panel
fi
```

-f parameters in ps is useless in this case: it yields an ascii forrest rapresentation, couldn't see why it's used here.
why -i in grep? xcompmgr exe is lower case
the awk doesn't return anything here beacuse /bin/sh is missing on command line: much more effective to grep form xcommgr then match the PID field with awk.
Last, it launches ps to find if xcomp is running, then it executes the very same command a second time to kill it: redundant.
My 2 cents.

---

### Post by jannol on 2005-12-31
could you write us the improved code?

---

### Post by piedamaro on 2005-12-31
I posted a script in the previous page, but ymmv.
Ah, no pun intended, just want to see if I missed something.

---

### Post by Paulus on 2006-01-02
[quote=fannymites]Has anyone here tried running kwin in dapper (gnome)?  Last time I tried kwin in gnome was in debian a while back and it was hopeless but in dapper it's running perfectly and not a single crash so far.  The kwin composite manager is so much better.
[[IMG]http://img424.imageshack.us/img424/8443/dapper8hc.th.png[/IMG]]("http://img424.imageshack.us/my.php?image=dapper8hc.png")[/quote] 
This is VERY interesting I must say!  How are you finding kompmgr btw, I'm finding it a little unstable with shadows, pretty bad for watching vid's with anything except totem (which we know anyway right?), I seem to get lots of random slowdown at times :(  ur using the l8st nv drivers?  what card? too many questions?  btw what windeco is tat your using?!

end of questions!  btw i'm using an fx5950, finding kompmgr not quite there yet :/  but v close!

---

### Post by fabs0028 on 2006-01-02
Hey everyone 
Take some minutes and read it so you can see that maybe in a short term we'll have a better x server ;)

[News of Xgl]("http://lists.freedesktop.org/archives/xorg/2006-January/011922.html")

Poofyhairguy i think it will please you :)
Cu everyone ;)

---

### Post by fannymites on 2006-01-02
Ok, some answers to Paulus' questions.
Remember this is on dapper with with kde 3.5.
The windeco is Suse2 (apt-get install kwin-style-suse2 if using dapper).
kompmgr has been very stable so far, still haven't had a single crash or any display problems.
I'm using an unsupported card and to my suprise it is running pretty snappy.
The only time I've had slowdown issues is when using fully transparent active and inactive windows with a lot of open windows but even then it is still usable.
Not had any problems with video in mplayer or totem, it gets a little jerky in kaffiene.
The only really notable problems I have had is that kde based apps weren't showing in the system tray which I solved by running adding kwin --replace as a startup program in System>Preferences>Sessions and setting the priority to 200 to make sure it is the last thing loaded.
The other problem is that the shadow settings keep changing by themselves but I'm also getting that in suse, in which I'm only using kde so it's nothing to do with running kwin in gnome.

I wasn't even expecting kwin's transparency/shadows to work in gnome, I only wanted to use kwin because of it's window placement settings.
I'm now using kwin in breezy gnome also, unfortunately I don't get the transparent window borders there cos it's kde 3.4.2.

---

### Post by curtis on 2006-01-02
> **fabs0028]Hey everyone 
Take some minutes and read it so you can see that maybe in a short term we'll have a better x server  said:**
> News of Xgl[/URL]

Poofyhairguy i think it will please you :)
Cu everyone ;)
Great, nice to see it is still being worked on.

---

### Post by poofyhairguy on 2006-01-03
> **fabs0028]Hey everyone 
Take some minutes and read it so you can see that maybe in a short term we'll have a better x server  said:**
> 

Well it exists, so yeah its here in the short term. As far as it being the default, I say two years.

[QUOTE]
Poofyhairguy i think it will please you :)


It does. Something to compile. I will make a guide if it will work on Breezy.

---

### Post by poofyhairguy on 2006-01-04
Here is a neat screenshot I took of xcompmgr and transset running in Xgl:

[IMG]http://img493.imageshack.us/img493/5184/xgl29xd.jpg[/IMG]

---

### Post by Footer on 2006-01-04
Is that the Nautilus file browser?

---

### Post by grendelkhan on 2006-01-04
how'd you get xgl to compile? I've had zero luck with this.

---

### Post by jannol on 2006-01-04
poofyhairguy very cool, but what is xgl really? is it some hack to xorg or is it standalone?

---

### Post by poofyhairguy on 2006-01-04
[QUOTE=Footer]Is that the Nautilus file browser?[/QUOTE]

Yes.

---

### Post by poofyhairguy on 2006-01-04
[QUOTE=grendelkhan]how'd you get xgl to compile? I've had zero luck with this.[/QUOTE]

Its the repo Xgl. I installed Dapper to mix it with the recently released glxcompmgr (which I got to compile but so far I can't control).

I'm going to wait till the newest code hits the cvs before I try to compile it again. Apparently it needs some immediate work.

---

### Post by poofyhairguy on 2006-01-04
[QUOTE=jannol]poofyhairguy very cool, but what is xgl really? is it some hack to xorg or is it standalone?[/QUOTE]

Hack to Xorg for now. Here is more info:

[http://linux.slashdot.org/comments.pl?sid=172800&threshold=1&commentsort=0&tid=104&mode=thread&cid=14382851](http://linux.slashdot.org/comments.pl?sid=172800&threshold=1&commentsort=0&tid=104&mode=thread&cid=14382851)

[http://linux.slashdot.org/comments.pl?sid=172800&threshold=1&commentsort=0&tid=104&mode=thread&cid=14383213](http://linux.slashdot.org/comments.pl?sid=172800&threshold=1&commentsort=0&tid=104&mode=thread&cid=14383213)

[http://linux.slashdot.org/comments.pl?sid=172800&threshold=1&commentsort=0&tid=104&mode=thread&cid=14383009](http://linux.slashdot.org/comments.pl?sid=172800&threshold=1&commentsort=0&tid=104&mode=thread&cid=14383009)

---

### Post by jannol on 2006-01-04
that was really interesting to read but I'll wait for a while more, maybe I try this when dapper becomes official, I got everything workin in breezy and I also got the memory leak to a minimum, I don't actully know if it was because of one small stuff I got from a novell linux dev but it seems to help

sudo chown <user> /usr/local/bin/xcompmgr

or maybe

sudo chown <user> /usr/bin/xcompmgr

for some

replace user with your own username

Since that I have run xcompmgr about 2 days before it shuts off and computer gets slow as hell but then in a few minutes I start xcompmgr again and all is good.

---

### Post by Gray. on 2006-01-05
I showed this to my friend today and he is now the proud owner of a new Ubuntu PC. I feel so happy :D

One problem though is that sometimes when I maximise windows, they overlap the top and bottom dock-bar-things (looks like fullscreen but still a window). Anyone know what to do?

---

### Post by jannol on 2006-01-05
it easily have that effect, one of my friends instantly said, "I WANT THAT" and even if I tried to explain all about not stable yet etc etc and also I know he has alot of other needs but now he has ubuntu and so far I have managed to help out with all of his comp. needs as eg. remote music server from an old DELLLLL laptop with vnc, video editing, music editing, tv-out on the remote comp. etc.
I told him to shutdown xcompmgr when using kino since then it crashes easily.

---

### Post by poofyhairguy on 2006-01-05
[QUOTE=Gray.]I showed this to my friend today and he is now the proud owner of a new Ubuntu PC. I feel so happy :D[/QUOTE]

Nice

> 
One problem though is that sometimes when I maximise windows, they overlap the top and bottom dock-bar-things (looks like fullscreen but still a window). Anyone know what to do?

Its easy to fix. Keep using one command till it works:

```
killall gnome-panel
```

---

### Post by Gray. on 2006-01-05
Thanks for that. :D

---

### Post by Squalor on 2006-01-05
[QUOTE=poofyhairguy]Here is a neat screenshot I took of xcompmgr and transset running in Xgl:[/IMG][/QUOTE]

May I ask how did you do that? When using this command:

```
Xglx :1 -ac -screen 640x480
```

the only thing I get is a pointer and black-white background. :confused:

---

### Post by fabs0028 on 2006-01-05
I 'm not sure but you should be able to launch programs in it by typing

> DISPLAY=:1 before any command.
So the graphical interface will launch in the xgl server not in your standard xorg

EDIT:
you must also do ```
export DISPLAY=:1
``` and then for example launch gnome-session all this in a terminal.

---

### Post by fabs0028 on 2006-01-05
Well all listening about xgl made me wanna compile it
As far i have a problem on the configure it seems to have some problems with the x prototypes :
> checking for XSERVER... configure: error: Package requirements (randrproto renderproto fixesproto damageproto xextproto xfont xproto xtrans xau compositeproto resourceproto recordproto xkbfile) were not met.


But i checked and in installed everything with apt. I 'm still on breezy so maybe it is not possible to compile it on but i really doubt that.

Maybe i miss something here.
An idea here?
Thanx a lot for your help.

By the way my configure command follows the one told by david r on the mailing list :

```
./configure --enable-xglserver --enable-glx --enable-xkb --with-mesa-source=/home/fab/compil/Mesa-6.4.1/src/

```

Thanx :)

---

### Post by fog on 2006-01-05
[QUOTE=Squalor]May I ask how did you do that? When using this command:

```
Xglx :1 -ac -screen 640x480
```

the only thing I get is a pointer and black-white background. :confused:[/QUOTE]
After this, open another terminal and give:
```
DISPLAY=":1"
```
then in the same terminal, give something...
```
nautilus
```
That's it.

[[IMG]http://img411.imageshack.us/img411/8815/screenshot2bf.th.jpg[/IMG]](http://img411.imageshack.us/my.php?image=screenshot2bf.jpg)

---

### Post by poofyhairguy on 2006-01-05
[QUOTE=fabs0028]
But i checked and in installed everything with apt. I 'm still on breezy so maybe it is not possible to compile it on but i really doubt that.
[/QUOTE]

Thats what I determined. It might be possible but so is Linux from scratch but I will never do that!

Basically I could not get it to run in Breezy. In fact, the only distro I know of with all the dependancies is Gentoo. 

So I installed Dapper to use the Xgl from its repos (that was added after I made Mr. Stone mad one day) so I could play with the glxcompmgr released recently.

Honestly the Xgl is not too exciting on its own. Its the compmgrs that make it fun.

I will try again to compile a new Xgl from the recent code when it actually enters the CVS. From what I read, many fixes will be added in the next couple of days.

---

### Post by Squalor on 2006-01-06
[QUOTE=fog]After this, open another terminal and give:
```
DISPLAY=":1"
```
then in the same terminal, give something...
```
nautilus
```
That's it.[/QUOTE]

Thank you for your help. 

Does anyone know where to get glxcompmgr? Does anyone have a DEB? :confused:

---

### Post by poofyhairguy on 2006-01-06
[QUOTE=Squalor]
Does anyone know where to get glxcompmgr? Does anyone have a DEB? :confused:[/QUOTE]

I have been trying, but it takes a lot to get it to work. I got it to compile into a deb with checkinstall, but I don't want to release it because it just doesn't work. As it is it's almost obsolete because there is plans to replace it by its creator. Maybe if Mr. Stone puts it in the repos we will play with it, otherwise I will keep trying.

---

### Post by Iandefor on 2006-01-06
Here's another testimonial: I got my new computer up and running. On an NVIDIA Geforce 6100 with the latest NVIDIA drivers, this works like a charm. I notice absolutely no difference in speed, at all. Only problem is, I lost my bottom panel, but I can live with that.

---

### Post by raggamuffin on 2006-01-06
thanks a lot poofyhairguy...worked like a charm right away for me (nvidia card)...

[[IMG]http://img497.imageshack.us/img497/5161/snapshot21yi.th.jpg[/IMG]](http://img497.imageshack.us/my.php?image=snapshot21yi.jpg)

---

### Post by poofyhairguy on 2006-01-06
[QUOTE=raggamuffin]thanks a lot poofyhairguy...worked like a charm right away for me (nvidia card)...[/QUOTE]

Welcome to modern times.

---

### Post by kiddo on 2006-01-07
Dear fellow ubuntuers,

this is just a testimonial to say that I am using the nvidia [1.0-8178]("http://www.nvidia.com/object/linux_display_ia32_1.0-8178.html") drivers (manually installed) on my breezy machine right now. The rumors were true: they are ultra stable. I've been running this for three days and xcompmgr has not crashed once. I got my dropshadows, I feel alive again!

For thou who has already used their installer, you know that you must **sudo apt-get remove nvidia-glx nvidia-settings**, especially nvidia-settings since it is integrated now.

Then, the only tricky part is that you must work around GCC. Because our kernel is compiled with GCC 3.4, but we have GCC 4.0 as default for compiling. What you need to do is this:
[B]sudo apt-get install gcc gcc-3.4

[/B]Then, each time, before you run the nvidia installer (make sure it's executable):
[B]CC=gcc-3.4
export CC[/B]

The driver should then work fine. And this time, the gnome logout dialog even works! ZOMG!



I'm amazed by the nvidia guys. Please please, someone, give me the email of [Jen-Hsun Huang]("http://nvidia.com/object/bio_huang.html") so I can tell the upper management how I love the fact that they support linux so actively. I'm dead serious. I know the developer knows I love him, so the ones I want to reach (I'm outside the US) are the "management" guys, they're the ones who need to have feedback.

---

### Post by Josef K. on 2006-01-07
[QUOTE=kiddo]
this is just a testimonial to say that I am using the nvidia [1.0-8178]("http://www.nvidia.com/object/linux_display_ia32_1.0-8178.html") drivers (manually installed) on my breezy machine right now. The rumors were true: they are ultra stable. I've been running this for three days and xcompmgr has not crashed once. I got my dropshadows, I feel alive again!
[/QUOTE]

is there a deb-package somewhere out there?! :D

---

### Post by Azriphale on 2006-01-07
I don't know of a .deb packaged nVidia driver, but installing the driver manually is really easy.

If I remember correctly, these are the steps I followed to install my previous drivers (I have not yet installed the 8178, I'm still on manually installed 7676)

I am not entirely certain of these steps, I did this a fair while ago. If it fails, you should be able to switch your xorg driver back to the "nv" driver to use X.

you need to have the linux-headers installed (and any specific to your kernel, i.e. i need linux-headers-686-smp)
you need gcc-3.4
you need to REMOVE nvidia-glx
REMOVE nvidia-settings
REMOVE linux-restricted-modules (whichever variation you have installed)

hit ctrl+alt+backspace
hit ctrl+alt+F1 to get to a virtual console and log in

change to the directory where the nvidia driver you downloaded from nvidia is on you drive

make sure the nvidia driver file downloaded from nvidia is executable


```
cd ~/Download
chmod +x NVIDIA-Linux-x86-1.0-8178-pkg1.run
sudo /etc/init.d/gdm stop
CC=gcc-3.4 sudo ./NVIDIA-Linux-x86-1.0-8178-pkg1.run
```

change the driver in your xorg.conf from "nv" to "nvidia"

I think that should do it.

[edit]
By the way, in the ATI vs nVidia thing going on:
I have had trouble with every ATI driver I have ever encountered, on every platform, incl Linux and Windows. I have found the ATI driver to be fairly unstable on both these platforms. On both these platforms, I have found nVidia to be very stable, easy to configure, and provide good performance.
[/edit]

---

### Post by Josef K. on 2006-01-07
meantime I've found them [here]("http://people.debian.org/~rdonald/index.php")
but seems to be for debian, so I guess I'll use them just this time, then remove links from sources.list... or perhaps I should just be patient and wait a bit :)
I was looking for deb file not to mess up the system with non packaged stuff (next time nvidia will release fresh driver (2 weeks? :rolleyes:) I wanna be able to upgrade again via apt as usual :))

---

### Post by Josef K. on 2006-01-07
[QUOTE=Josef K.]meantime I've found them [here]("http://www.khensu.org/index.php?itemid=135")
but seems to be for debian, so I guess I'll use them just this time, then remove links from sources.list... or perhaps I should just be patient and wait a bit :)
I was looking for deb file not to mess up the system with non packaged stuff (next time nvidia will release fresh driver (2 weeks? :rolleyes:) I wanna be able to upgrade again via apt as usual :))[/QUOTE]

PS.
TKS for the HOWTO :D
about ATI: don't know about linux, but on windows ATI driver for my old radeon 8500 used to be perfect

---

### Post by Azriphale on 2006-01-07
Maybe ATI just doesn't like me. I used to have problems. I don't know about their newer Windows drivers, but I do know that nVidia has far better Linux support.

Whatever, I am very happy with my nVidia GeForce 6200 TC, despite the fact that it is the lower of the 6xxx series. And I will continue to buy nVidia products, based on their Linux support alone. Along with outstanding products.

I believe that only nVidia cards are certified to work with 3d studio max. No ATI cards. Not that it bothers me, seeing as I dont use 3ds max. I use blender, for a few reasons. It seems a lot more simple (in the interface), it runs in Linux, and its Free and Open Source Software.

If you're more comfortable using a .deb for the drivers, then its better to do it that way. I don't mind killing X and reinstalling my nVidia drivers with every kernel update. I have to compile my ALSA audio drivers anyway. (They lied when they said that hda-intel ALSA support works out of the box in Breezy. It should, but it doesn't always)

---

### Post by oobuntoo on 2006-01-07
Poofyhairguy, when you had xgl running, is moving window around as smooth as on OSX? Are windows right and left edges still breaking up?

---

### Post by poofyhairguy on 2006-01-07
[QUOTE=oobuntoo]Poofyhairguy, when you had xgl running, is moving window around as smooth as on OSX? Are windows right and left edges still breaking up?[/QUOTE]

Lets just put it this way- the Xgl is not magic. It still needs a lot of work.

---

### Post by Cybolic on 2006-01-08
Thanks for the guide!
Although it's not that difficult a process, it's nice to have a step-by-step guide to check one haven't forgotten anything.

Since I used a bit different version of the toggle-script, I thought I'd post it here. Functionally they are equal, I just think my version is a bit cleaner:

```
#!/bin/sh

if [ -z "$(ps -A | grep -i xcompmgr)" ]; then
        xcompmgr -fF -I0.06 -O0.03 -D6 -cC -t-6 -l-7 -r6 -o.40 &
        killall gnome-panel
else
        kill -9 $(ps -A | grep -i xcomp | cut -d\  -f1)
        killall gnome-panel
fi
```
There, you also got my settings as a bonus ;)

Other than that, does anyone other than me have problems with Leafpad, Mousepad and GEdit when scrolling? ...it seems the GtkTextview isn't too happy about the Composite extension.... that's my guess anyhow....
Besides that problem (and occasional X-crashing when doing the "zoom"-trick (Ctrl+Alt+[-/+])) it works perfectly.... very nice, very smooth and very very fast. :D

---

### Post by garba on 2006-01-08
hello! forgive my ignorance, but do you need xcompmgr to be running to get accelerated windows rendering? this seems to be the case here, xcompmgr -a works fine and prevents windows from leaving a trail when moving them across the screen... still I would live to know what EXA is good for, enabling it by no means make things faster for me, even when using shadows and translucencies...

---

### Post by MistaED on 2006-01-08
Hello,

I've been using xcompmgr, it's quite awesome. I've tried the kwin compositor one back in 3.4 and it didn't work for me with shadows. I thought it was due to it being a WIP but 3.5 doesn't do it either. I am using the latest NVIDIA driver (8178) and it works fine wth transparencies and I have all the options enabled for it to allow renderaccel & glx with composite, very fast. Just none of those damn sexy shadows! :) My video card is a 6800GT 256mb btw.

The shadows work on my friend's PC with the CPU-driven mode (SLOW), and probably on mine that way but I haven't tried. I've tried searching around for anyone with the same problem but I can't seem to find any posts on the issue. Xcompmgr has no problems with shadows but I wanted to use kwin's compositor due to all the stability claims.

Thanks for your help.
-MistaED

---

### Post by Mr_J_ on 2006-01-08
This worked fine for me with my Dual monitor and Nvidia 6600GT

---

### Post by Ainvar on 2006-01-08
I have a Dell Precision Workstation M70 with the NVIDIA Quadro FX Go 1400 video card 256megs of ram.

I tried the stock nvidia drivers that are in the repos for Ubuntu 5.10 and then installed the latest and greatest using the NVIDIA installer that is a page or so back on this thread.

I am having great success as long as I dont reboot to many times. If so I get a normal bootup with a very very very brief glimpse of the NVIDIA logo screen going into xwindows and the the screen does a very shallow light up and then cuts off and repeats until I manually power off the laptop. I cant kill xwindows I cant switch to a diffrent console and I am not able to tell it to reboot with ctrl-alt-del. If I reinstall the drivers they work fine with the settings in this thread until I reboot a couple of more times.

My second issue is this, when I go to a diffrent page in mozilla 1.5 my mouse cursor flickers really really really bad and it does it on a few other applications also like evolution and thunderbird. gaim 2.0 is ok and has very little flickering.

here is my xorg.conf attached to this post and if you need any other info please let me know.


I do want to say that your howto is really really cool and makes me a sad panda knowing the my personal laptop a dell i6000d with an ati x300 128meg card cant do this hardly at all. What is ATI thinking when they make there drivers?? 

But I just wanted to thank you for this guide plus a few others I have seen on the forums and your blog, very informative and very easy to follow.

[http://www.smugglingyoyos.net/ubuntuforums/xorg.conf.gz]("http://www.smugglingyoyos.net/ubuntuforums/xorg.conf.gz")

---

### Post by piedamaro on 2006-01-09
Guys....don't know....read my posts.

---

### Post by RaptorRaider on 2006-01-09
Slightly offtopic perhaps, but is the movie in the startpost working at all?
I can't get it to work under Windows (I'm at work) with WMP, Quicktime and WinDVD?

Also do you have any idea when the newer ATI cards will work?

---

### Post by jannol on 2006-01-09
well, vlc is the player in win that can play it, it doesn't always work in wmp, I don't know why really but it probably has todo with many things. So you could just try installing vlc and play it if you want. I am zorry for the inconvenience.

---

### Post by poofyhairguy on 2006-01-09
> **Cybolic]Thanks for the guide!
Although it's not that difficult a process, it's nice to have a step-by-step guide to check one haven't forgotten anything.

Since I used a bit different version of the toggle-script, I thought I'd post it here. Functionally they are equal, I just think my version is a bit cleaner:

```
#!/bin/sh

if [ -z "$(ps -A | grep -i xcompmgr)" ] said:**
> 

Thanks for the code. It does seem a little more simple.

[QUOTE]
Other than that, does anyone other than me have problems with Leafpad, Mousepad and GEdit when scrolling? ...it seems the GtkTextview isn't too happy about the Composite extension.... that's my guess anyhow....
Besides that problem (and occasional X-crashing when doing the "zoom"-trick (Ctrl+Alt+[-/+])) it works perfectly.... very nice, very smooth and very very fast. :D

Yeah, scrolling plus a few other things lead to composite artifacts.  Those will just to be worked out over a few years. I was using OSX for four days and I noticed many composite artifacts in Tiger- its obviously a hard bunch of bugs to squash.

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=garba]hello! forgive my ignorance, but do you need xcompmgr to be running to get accelerated windows rendering? this seems to be the case here, xcompmgr -a works fine and prevents windows from leaving a trail when moving them across the screen... still I would live to know what EXA is good for, enabling it by no means make things faster for me, even when using shadows and translucencies...[/QUOTE]

EXA is the acceration needed to make Xcompmgr use your hardware effectively. 

If it does not speed things up for you no big deal, it was not ready in Breezy. Only Dapper has working EXA.

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=Ainvar]I have a Dell Precision Workstation M70 with the NVIDIA Quadro FX Go 1400 video card 256megs of ram.

I tried the stock nvidia drivers that are in the repos for Ubuntu 5.10 and then installed the latest and greatest using the NVIDIA installer that is a page or so back on this thread.

I am having great success as long as I dont reboot to many times. If so I get a normal bootup with a very very very brief glimpse of the NVIDIA logo screen going into xwindows and the the screen does a very shallow light up and then cuts off and repeats until I manually power off the laptop. I cant kill xwindows I cant switch to a diffrent console and I am not able to tell it to reboot with ctrl-alt-del. If I reinstall the drivers they work fine with the settings in this thread until I reboot a couple of more times.[/QUOTE]

That sounds like a bug with the Nvidia drivers. You might want to email them.

> 
My second issue is this, when I go to a diffrent page in mozilla 1.5 my mouse cursor flickers really really really bad and it does it on a few other applications also like evolution and thunderbird. gaim 2.0 is ok and has very little flickering.

Use a hardware accerated mouse.

Add this to the device part of your xorg.conf:

```
   Option     "HWcursor"
```

> 
I do want to say that your howto is really really cool and makes me a sad panda knowing the my personal laptop a dell i6000d with an ati x300 128meg card cant do this hardly at all. What is ATI thinking when they make there drivers?? 

But I just wanted to thank you for this guide plus a few others I have seen on the forums and your blog, very informative and very easy to follow.

ATI is thinking they don't care about the Linux desktop. They are more in bed with MS than Nvidia is (I think because their Directx performance is far better than their opengl performance).

And I'm glad my guides and blog helps. I just want to so what I can to give back to the community.

---

### Post by Azriphale on 2006-01-09
Woohoo!!!

I got xgl to compile. That was a good few hours of messing about. Mostly trying to look for one damn dep in the freedesktop cvs. Grrrrr.

Now, say I have Xgl running on display :1, how do I get Gnome to run in Xgl?

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=Azriphale]Woohoo!!!

I got xgl to compile. That was a good few hours of messing about. Mostly trying to look for one damn dep in the freedesktop cvs. Grrrrr.

Now, say I have Xgl running on display :1, how do I get Gnome to run in Xgl?[/QUOTE]

WOW! You got the newest code to compile? Care to share some secrets?

Here is my secret that you want:

[http://ubuntuforums.org/showpost.php?p=504974&postcount=6](http://ubuntuforums.org/showpost.php?p=504974&postcount=6)

Now yours please!

---

### Post by Onos on 2006-01-09
Quick question: I am using XFCE without any KDE/Gnome stuff.

How do I do I get into the XFCE composite manager? (and adjust my transparency, etc. ) ?

---

### Post by Azriphale on 2006-01-10
poofyhairguy:

I grabbed the latest from cvs. I think it is newer than that tarball that was released. At least, some of the xgl files were only 4 days old, the tarball is about 8 now.

I followed some instructions on freedesktop.org:

For glitz and glitzinfo, i went here:
[http://www.freedesktop.org/wiki/Software_2fXgl](http://www.freedesktop.org/wiki/Software_2fXgl)

then I followed these following instructions to compile everything needed to compile the xserver module

I followed these instructions to compile everything except the xserver package (which is what contains Xgl, as you undoubtedly know). Aside from the packages listed here, you also need xres:
```
cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xlibs co XRes
```
It can be compiled in the same way as the rest of them.

[http://www.freedesktop.org/wiki/Software_2fXserver_2fInstallGuide](http://www.freedesktop.org/wiki/Software_2fXserver_2fInstallGuide)

Then, for xserver, I went back here:

[http://www.freedesktop.org/wiki/Software_2fXgl](http://www.freedesktop.org/wiki/Software_2fXgl)

I ran autogen.sh like so:
```
./autogen.sh --prefix=/opt/fdo --enable-composite --enable-xglserver
```

I then ran it like so:
```
/opt/fdo/bin/Xgl :1 -ac -screen 1024x768 & xterm -display :1
```

Sorry about not going into much detail...  If that doesn't work for you, I'll have a look at mine when I get home. I did make a couple of notes about how I did it, but I think all that was in my notes was that XRes was needed.

I'm going to try to compile it without doing the rest of X with it when I get home too.

I feel stupid now, with not setting DISPLAY=:1 before running stuff. :) 
> ./Xglx :1 -ac -screen 640x480
DISPLAY=:1 nautilus
DISPLAY=:1 metacity
DISPLAY=:1 gnome-panel
DISPLAY=:1 xcompmgr -c
DISPLAY=:1 transset
DISPLAY=:1 gnome-settings-daemon

Can you perhaps tell me why I have Xgl instead of Xglx? I didn't think much about it until I saw that post....

and for the cvs glxcompmgr:
cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg co app/glxcompmgr

it looks like the mesa patch needed is with it there...

---

### Post by vayu on 2006-01-10
[QUOTE=Onos]Quick question: I am using XFCE without any KDE/Gnome stuff.

How do I do I get into the XFCE composite manager? (and adjust my transparency, etc. ) ?[/QUOTE]

I can't remember where I found this stuff, probably on the XFCE site but here's what I have and it works well:

play around with the values in this file:

~/.config/xfce4/xfwm4/xfwm4rc

move_opacity=72
resize_opacity=60
panel_opacity=80

I believe 100 is opaque and less is towards transparent

Looking around I found this file:

/usr/share/xfwm4/defaults

I haven't played with it at all.  There are some interesting shadow items, but based on the shadows I'm getting, these settings aren't making sense.  I would try putting values from there into the local file and then modifying them.

For me the KDE compositing is the nicest looking and the most tailorable.  I really like the transparent unfocused windows.  And the shadows are adjustable.  I haven't found these items in XFCE.  The KDE compositing (in 3.5) is just unstable enough to keep me away from it.  Xcompmgr and GNOME just aren't stable enough for me.  XFCE while the least flashy is very stable for me.

---

### Post by Azriphale on 2006-01-10
[quote=poofyhairguy]ATI is thinking they don't care about the Linux desktop. They are more in bed with MS than Nvidia is (I think because their Directx performance is far better than their opengl performance).[/quote]

I don't think nvidia is exactly in bed with MS at all. Sure, the nvidia linux drivers lag the windows drivers a little, but not by very much usually. Personally I think their linux driver is outstanding. 

Their current Linux driver is 8178, windows is 8198. This is a lot close than they were a little while ago. It looks to me like they actually do want to give proper support for linux.

There are a few little things I don't like, such as you can't have a DFP as the primary monitor over a CRT (well, in my case an analogue LCD) in TwinView (which made me run both monitors analogue...). But my DFP seems to not like 75Hz when running digital anyway, so I can live with it running from the analogue d-sub.

---

### Post by Cybolic on 2006-01-10
Just a quick tip:

If you really can't live with killing the gnome-panel and the trouble that brings (a pain if you have lots of apps in the tray) then another way to get maximising to work again is to kill Metacity instead.

In our little toggle script, replace the lines that read
```
killall gnome-panel
```
with
```
killall metacity
```

this way your windows may get re-arranged slighly, but you won't loose your tray apps - good news for users of Gaim, Amarok, Azureus and a lot of other programs ;).

---

### Post by poofyhairguy on 2006-01-10
[QUOTE=Cybolic]Just a quick tip:

If you really can't live with killing the gnome-panel and the trouble that brings (a pain if you have lots of apps in the tray) then another way to get maximising to work again is to kill Metacity instead.

In our little toggle script, replace the lines that read
```
killall gnome-panel
```
with
```
killall metacity
```

this way your windows may get re-arranged slighly, but you won't loose your tray apps - good news for users of Gaim, Amarok, Azureus and a lot of other programs ;).[/QUOTE]

Killing Metacity is always a good idea.

So is replacing it....hmm....

---

### Post by Azriphale on 2006-01-10
Have you started playing with Xgl yet :)

And on the subject of WMs, what would you suggest. When I was running Hoary, I tried replacing Metacity with E16, Openbox, xf4wm?, Fluxbox and various others. Can't remember if I tried E17 tho....

I eventualy went back to metacity because it it seemed a whole lot more stable than any of the others. The others crashed at some stage after installing them, but not Metacity.

What do you suggest I replace it with? As I said, I last tried with Hoary, so it was a fair while ago...

And while I'm at it, I'm going to look at KDE 3.5 and even see if KDE 4 will compile. Been reading some good stuff about KDE these days.

Can I use KDEs WM for Gnome?

---

### Post by Cybolic on 2006-01-10
It is quite possible to run KDEs window manager (kwin) while running Gnome, but there will be little graphical glitches. I don't the glitches are because of running it from Gnome, I think they are bugs in the kwin compositor.

If you want to try for yourself (and have your unfocused windows become transparent ;) ), you can run kwin like this
```
kwin --replace
``` but be aware that focusing the Gnome panels will be odd, there will be minor graphical bugs (missing parts of windows and graphics not updated some times), but it will look cool :cool:.

If you don't have kwin installed, type the following in a terminal:
```
sudo apt-get install kwin
```

When you want to go back (if you do), the way I do it is to add the "Run a program"-applet to your panel and first run [FONT="Courier New"]killall kwin[/FONT] and then [FONT="Courier New"]metacity[/FONT] (or xfwm4 or whatever you want ;) ) - that way you don't end up with running your wm from a terminal.

---

### Post by Azriphale on 2006-01-10
I probably have an updated method of getting Xglx up and running, using most of your existing Xorg packages. I'll start writing it up, its much easier and much quicker. Most of it is getting the xorg dev files from apt, then there are two things to compile - glitz (the one in the repos is too old) and xserver.

[EDIT] No.. No. I just got a compile error:
bigreq.c:41:38: X11/extensions/bigreqstr.h: No such file or directory

Lets have a look for it, then.
 
[EDIT] Got it. Trouble is, I'm busy using apt to fetch KDE 3.5 (Just to look! I swear!) Although, it can resume, so it will now die.
I'm sure synaptic isn't supposed to disappear when I press the cancel download button. Oh well. I hope my KDE progress remains intact.

[EDIT] erg. More missing deps :P

[EDIT] Ok. I am having problems getting the dep GL/internal/glcore.h

It is in the package mesa-swrast-source but it gets put in a funny place (/usr/share/mesa-source) and if you link the .h files to where they should be in /usr/include/GL it gives other errors like
```
g_render.c: In function `__glXDisp_TexCoord1sv':
g_render.c:599: error: dereferencing pointer to incomplete type

```

Can anybody help me with this?

[EDIT]
Solved by not configuring xserver with the --enable-glx command, but only using --enable-xglxserver

---

### Post by Azriphale on 2006-01-11
HOWTO (incomplete): Compile Xgl from the freedesktop.org CVS to run witg your current Xorg libraries.

I've never done the howto thing before, so please bear with me. Any comments are welcome.

Should I be starting a new thread for this....?

-------------------------------------------

As you may or may not be aware, I got Xgl to compile again last night, this time using the Xorg stuff that came with breezy rather than compiling all the xserver deps again.

I got the source from the freedesktop.org CVS server:

```
cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xserver co xserver
```

I will post all the deps and a bit of a howto when I get home (I don't have the list of deps at work). Right now, however, I can tell you how to find the deps if you want to try compiling before I post them (and when I do post them, I might not list them all cuz some were alerady installed on my machine, and I'm not sure which ones exactly).


Before you can compile xserver, you need to fetch and compile glitz (the version in the Breezy repos is too old):

```

$ cvs -d:pserver:anoncvs@cvs.freedesktop.org:/cvs/cairo co glitz glitzinfo

$ pushd glitz
$ ./autogen.sh
$ make
$ sudo make install
$ popd

$ pushd glitzinfo
$ make -f Makefile.glx
$ ./glitzinfo
$ popd

```

glitzinfo should report some info about available features, drawable formats and surface formats. The following set of features are important and if one of them is missing it is likely that it will give you performance problems.

```
texture rectangle
texture border clamp
multitexture
texture environment combine
```

Now you can start with xserver.....

```

$ pushd xserver
$ autogen.sh --enable-xglxserver
$ make

```

We don't want to install it (it could (will) break your current xserver from the repos).

When configure gives you the following message

```
randrproto renderproto fixesproto damageproto xextproto xfont xproto xtrans xau compositeproto resourceproto recordproto xkbfile
```

Search for packages that contain x11proto in the name (by using synaptic, for example), and install:
x11proto-randr-dev
etc.

Some of them are not the x11proto packages, so if you can't find one there, search for, say, xfont. This will come up with (i think) libxfont-dev.

You can check which are missing before you look for them all by running:
```
$ pkg-config --cflags randrproto renderproto fixesproto damageproto xextproto xfont xproto xtrans xau compositeproto resourceproto recordproto xkbfile
```

pkg-config will complain about the missing packages, then you can start looking for them in the repos.

Later on, configure will probably complain again in a similar fashion when looking for the packages required to build the xglserver component. You can search for those deps in the repos in a similar fashion to above.

Then we can start the build process. There are still a few missing deps that configure does not pick up, but they can be found using the packages.ubuntu.com resource. make will complain about a certain header file  that is missing, which you can search for on packages.ubuntu.com (search for files inside packages). Then just apt-get install the package it comes up with. You will probably have to do this a few times.

Once it is built, you should end up with an executable in the hw/xgl/glx called Xglx

cd to that directory (i.e. $ cd xserver/hw/xgl/glx) and run it with
```
$ ./Xglx :1 -ac -screen 1024x768
```
or whatever resolution you want.
If you leave off the -ac flag, it is likely that clients will not be able to connect to the xgl server. Or perhaps the server won't start. I can't remember..

Then you can:
```

$ export DISPLAY=:1
$ nautilus &
$ metacity &
$ xcompmgr -c &
$ transset &
$ gnome-panel &
$ gnome-settings-daemon &

```

I was haveing some warnings when starting some of those. I'll post them later. I don't know what to do about them. Maybe somebody can help me...

Can somebody point me in the direction of glxcompmgr? I got the source from the freedesktop.org cvs, but I can't compile it cuz I need glcore.h

I'll post what I think are the deps later whan I get home.

---

### Post by Azriphale on 2006-01-11
Something is wrong somewhere. Kwin's composite manager thingy is not playing nicely with Xgl.

I'm pretty sure all my problems are related to not being able to --enable-glx
Which means, i think, that it was not actually using hardware rendering.. perhaps..

Anyway, i'm through with this for now. Unless anybody has any suggestions.

---

### Post by limit223 on 2006-01-11
KDE 3.5, Dapper Flight 2, ATI Radeon X600 RV380 without xcompmgr part from the guide (in KDE is useless)...
That's the first time I see tranparency working on my video card ! Thanks Xorg !
Forget about ati driver!

---

### Post by poofyhairguy on 2006-01-11
[QUOTE=Azriphale]
pkg-config will complain about the missing packages, then you can start looking for them in the repos.
[/QUOTE]

Thats a wall I hit. I was resorting to alienizing RPMs to get all the dependancies.

---

### Post by poofyhairguy on 2006-01-11
[QUOTE=Azriphale]Something is wrong somewhere. Kwin's composite manager thingy is not playing nicely with Xgl.

I'm pretty sure all my problems are related to not being able to --enable-glx
Which means, i think, that it was not actually using hardware rendering.. perhaps..

Anyway, i'm through with this for now. Unless anybody has any suggestions.[/QUOTE]

Xgl is meant to work with either Luminocity, Glxcompmgr, or 'Compiz' which is due in Feburary.

But thanks for the direction so far. I think the best long term solution is to bug Mr. Stone to put it in the repos. I plan to start a campaign when Compiz is released (to get both of them).

Be ready.

---

### Post by poofyhairguy on 2006-01-11
> **Cybolic]It is quite possible to run KDEs window manager (kwin) while running Gnome, but there will be little graphical glitches. I don't the glitches are because of running it from Gnome, I think they are bugs in the kwin compositor.

If you want to try for yourself (and have your unfocused windows become transparent  said:**
> killall kwin[/FONT] and then [FONT="Courier New"]metacity[/FONT] (or xfwm4 or whatever you want ;) ) - that way you don't end up with running your wm from a terminal.

I find that solution is a good way to try it out...but not a good way to keep it as default.

There is a better way.

---

### Post by poofyhairguy on 2006-01-11
> **Cybolic]It is quite possible to run KDEs window manager (kwin) while running Gnome, but there will be little graphical glitches. I don't the glitches are because of running it from Gnome, I think they are bugs in the kwin compositor.

If you want to try for yourself (and have your unfocused windows become transparent  said:**
> killall kwin[/FONT] and then [FONT="Courier New"]metacity[/FONT] (or xfwm4 or whatever you want ;) ) - that way you don't end up with running your wm from a terminal.

Here is a full guide to make the changes stay that way:

[http://www.ubuntuforums.org/showthread.php?p=648604#post648604](http://www.ubuntuforums.org/showthread.php?p=648604#post648604)

---

### Post by Azriphale on 2006-01-12
[QUOTE=poofyhairguy]
[quote=Azriphale]
pkg-config will complain about the missing packages, then you can start looking for them in the repos.
[/quote]
Thats a wall I hit. I was resorting to alienizing RPMs to get all the dependancies.[/QUOTE]

[quote=Azriphale]
Search for packages that contain x11proto in the name (by using synaptic, for example), and install:
x11proto-randr-dev
etc.

Some of them are not the x11proto packages, so if you can't find one there, search for, say, xfont. This will come up with (i think) libxfont-dev.
[/quote]

Did that not work for you?
Ok, fine, I promise I'll post the deps later. Sorry I didn't do it earlier.

A couple of questions:
Is Luminocity in the Breezy repos? Or, better yet, can i get the latest source somewhere?
And how the hell do I compile glxcompmgr?
Its also complaining about the missing glcore.h

Otherwise, Kwin v3.5 actually works pretty well with gnome, I think. I haven't used any previos versions, but I have had no problems that I can think of now.

If you don't feel like compiling it, you can get Breezy repos from [www.kde.org](www.kde.org)
I lie. Information can be found at [http://kubuntu.org/announcements/kde-35.php](http://kubuntu.org/announcements/kde-35.php)
The repo is:
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main
which you can just add to the end of your sources.list

You can add the key that the packages have been signed with by doing this:
```
 wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
 sudo apt-key add kubuntu-packages-jriddell-key.gpg
```

I've not looked at kde4 yet because its probably not in a position to be looked at in much other than at source code level at the moment, which is no fun. But development goes on, and from what I have read, kde4 will be a whole lot better than kde has been before.

> We're trying stuff out in Luminocity and will be rolling them into Metacity
DAMN!
I want nothing more than to get rid of metacity with a (good looking) stable replacement.

---

### Post by Jeff250 on 2006-01-12
Great guide.  I was wondering:  How can I disable the default Metacity window maximize/minimize effects?  I know that I can using gconf-editor and toggling /apps/metacity/general/reduced_resources, but this also enables wireframe windows when you're moving them, which is pretty ugly looking.  The default metacity behavior when maximizing/minimizing windows is interfering with my effects. :-?

---

### Post by Azriphale on 2006-01-12
Unfortunately, one of the many, many shortcomings of Metacity is that, well, basically, you can't. You either have to use the reduced-resources mode thing that you mentioned, or get rid of metacity altogether. You may want to look at this guide to using enlightenment instead of metacity. I have not tested it lately, so I don't know how well it works... Here is the guide:
[http://www.ubuntuforums.org/showthread.php?t=54476&highlight=enlightened+gnome](http://www.ubuntuforums.org/showthread.php?t=54476&highlight=enlightened+gnome)

Or you can look at using kwin instead of metacity:
[http://www.ubuntuforums.org/showthread.php?p=648604#post648604](http://www.ubuntuforums.org/showthread.php?p=648604#post648604)

---

### Post by poofyhairguy on 2006-01-12
[QUOTE=Azriphale]
Is Luminocity in the Breezy repos? Or, better yet, can i get the latest source somewhere?
[/QUOTE]

I while ago I made a guide. I wonder if it still works:

[http://ubuntuforums.org/showthread.php?t=45202](http://ubuntuforums.org/showthread.php?t=45202)

---

### Post by poofyhairguy on 2006-01-12
[QUOTE=Azriphale]Did that not work for you?
Ok, fine, I promise I'll post the deps later. Sorry I didn't do it earlier.
[/QUOTE]

If you go that far, please take it all into a new guide.

Add to the series.

---

### Post by Azriphale on 2006-01-12
Thanks for the Luminocity guide, I'll give it a try later.

And in a few hours, you can expect to see a guide on getting Xgl set up in Breezy. I still don't have hw acceleration working, i dont think, and I need to iron out a couple of problems I was having yesterday first. And I only get home in about 4 hours.

---

### Post by tseliot on 2006-01-13
I have a question: Is it possible to have transparent menus (e.g. the "Applications" menu) in GNOME?
In KDE I can.

It's the only thing I miss from KDE.


Thanks in advance

P.S. This is a wonderful guide :)

---

### Post by poofyhairguy on 2006-01-13
[QUOTE=tseliot]I have a question: Is it possible to have transparent menus (e.g. the "Applications" menu) in GNOME?
In KDE I can.

It's the only thing I miss from KDE.


Thanks in advance

P.S. This is a wonderful guide :)[/QUOTE]

Thanks. That means a lot- I consider you to be the best guide maker on the forum.

Yet I know no way to make the Gnome Menu's transparent. Until Gnome does this stuff without hacks....it might not be able to.

---

### Post by tseliot on 2006-01-13
[QUOTE=poofyhairguy]Thanks. That means a lot- I consider you to be the best guide maker on the forum.

Yet I know no way to make the Gnome Menu's transparent. Until Gnome does this stuff without hacks....it might not be able to.[/QUOTE]
No, problem. If I find a way to do it I'll post it here. 
Thanks again

---

### Post by tseliot on 2006-01-13
Have a look at the image at the end of the webpage [http://freedesktop.org/~keithp/screenshots/]("http://freedesktop.org/~keithp/screenshots/")

---

### Post by Rob2687 on 2006-01-13
I compiled xgl succesfully with that guide but there is no Xglx in the folder mentioned. O_o

edit: Nevermind.

---

### Post by Azriphale on 2006-01-13
is Xgl working for you?
To have Xglx, you need to ./configure (or ./autogen.sh) with the --enable-xglxserver, not just --enable-xgl-server.
You can use either, or both options.

---

### Post by Rob2687 on 2006-01-13
I'm having a problem with the 'make' now...

```
Making all in .
make[4]: Entering directory `/home/robert/xserver/hw/xgl/glx'
if /bin/sh ../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../hw/xgl/glx  -I../../../hw/xgl  -I../../../miext/damage -I../../../miext/shadow -I../../../Xext -I../../../record -I../../../render -I../../../randr -I../../../xfixes -I../../../damageext -I../../../composite           -I../../../fb -I../../../mi -Wall -Wpointer-arith -Wstrict-prototypes   -Wmissing-prototypes -Wmissing-declarations     -Wnested-externs -fno-strict-aliasing -D_BSD_SOURCE -DHAS_FCHOWN -DHAS_STICKY_DIR_BIT -I/usr/include/freetype2   -D_BSD_SOURCE -I../../../include -I../../../Xext -I/usr/local/include -I/usr/local/include -I/usr/X11R6/include      -O2 -march=pentium3m -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions -MT xglx.lo -MD -MP -MF ".deps/xglx.Tpo" -c -o xglx.lo xglx.c; \
then mv -f ".deps/xglx.Tpo" ".deps/xglx.Plo"; else rm -f ".deps/xglx.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../hw/xgl/glx -I../../../hw/xgl -I../../../miext/damage -I../../../miext/shadow -I../../../Xext -I../../../record -I../../../render -I../../../randr -I../../../xfixes -I../../../damageext -I../../../composite -I../../../fb -I../../../mi -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -D_BSD_SOURCE -DHAS_FCHOWN -DHAS_STICKY_DIR_BIT -I/usr/include/freetype2 -D_BSD_SOURCE -I../../../include -I../../../Xext -I/usr/local/include -I/usr/local/include -I/usr/X11R6/include -O2 -march=pentium3m -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions -MT xglx.lo -MD -MP -MF .deps/xglx.Tpo -c xglx.c  -fPIC -DPIC -o .libs/xglx.o
In file included from ../../../include/dixfont.h:33,
                 from ../../../mi/mi.h:57,
                 from ../../../hw/xgl/xgl.h:43,
                 from xglx.h:29,
                 from xglx.c:26:
/usr/X11R6/include/X11/fonts/fontstruct.h:293:23: error: fontproto.h: No such file or directory
make[4]: *** [xglx.lo] Error 1
make[4]: Leaving directory `/home/robert/xserver/hw/xgl/glx'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/robert/xserver/hw/xgl/glx'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/robert/xserver/hw/xgl'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/robert/xserver/hw'
make: *** [all-recursive] Error 1
robert@linux:~/xserver$


```

---

### Post by Azriphale on 2006-01-13
> 
fontproto.h: No such file or directory


when I was having these, I looked on [http://packages.ubuntu.com](http://packages.ubuntu.com)
you can search for files inside a package.

This one, I believe is in x11proto-fonts-dev

I'll attach a file that contains a list of deps for --enable-xglserver
I made it on a clean install, but running inside VMware, so there was no glx. So you may need a couple more deps than those in the list...

---

### Post by Rob2687 on 2006-01-13
Yeah, I have all the x11proto* installed and the ones in the file you attached but it made no difference.

---

### Post by Azriphale on 2006-01-13
you definitely got all the x11proto* packages with -dev on the end?

output from packages.ubuntu.com
> 
FILE
usr/include/X11/fonts/fontproto.h		

PACKAGE
 x11/x11proto-fonts-dev


make sure you install the development packages.

also try installing libxfont-dev

edit:
Three more _possible_ deps, but they are not the ones giving you that error, I am sure.
x11proto-gl-dev
x11proto-trap-dev
x11proto-xinerama-dev

---

### Post by Rob2687 on 2006-01-13
Yeah, I have all that installed. I even tried the dapper x11proto-fonts-dev but it's still the same.

---

### Post by Azriphale on 2006-01-13
run this in the terminal:
```

$ sudo find / -name fontproto.h 

```
Does it come up with "/usr/include/X11/fonts/fontproto.h"?

also, have you got this installed?
libfreetype6-dev

---

### Post by Azriphale on 2006-01-13
I just removed a package and its refusing to install again.

All I can suggest trying now is the guide over here:
[http://www.ubuntuforums.org/showpost.php?p=643822&postcount=385](http://www.ubuntuforums.org/showpost.php?p=643822&postcount=385)
it takes a while tho, it recompiles a whole lot of the X components.

I need to get some sleep too, its almost 1 in the morning now...

---

### Post by Rob2687 on 2006-01-13
Yes and yes...

---

### Post by Azriphale on 2006-01-13
are you running configure with the flag --prefix=/some/path ?
If you are, you will need to compile and install xfont before xserver. If you are not, it should, I think, be working... the searching for missing files on packages.ubuntu.com worked for me....

---

### Post by Azriphale on 2006-01-13
try running configure with --prefix=/usr

I'll stick around for a few more minutes

Edit:
I hope that works for you, because now it is time for me to leave...

---

### Post by Rob2687 on 2006-01-13
Still couldn't get it to work. Thanks for you help but I think I'll this again some other time.

---

### Post by Jeff250 on 2006-01-14
[QUOTE=Azriphale]Unfortunately, one of the many, many shortcomings of Metacity is that, well, basically, you can't. You either have to use the reduced-resources mode thing that you mentioned, or get rid of metacity altogether. You may want to look at this guide to using enlightenment instead of metacity. I have not tested it lately, so I don't know how well it works... Here is the guide:
[http://www.ubuntuforums.org/showthread.php?t=54476&highlight=enlightened+gnome](http://www.ubuntuforums.org/showthread.php?t=54476&highlight=enlightened+gnome)

Or you can look at using kwin instead of metacity:
[http://www.ubuntuforums.org/showthread.php?p=648604#post648604](http://www.ubuntuforums.org/showthread.php?p=648604#post648604)[/QUOTE]

Thanks.  I went with kwin, since it seemed to be a more safe option.

Just for anyone interested, these effects great with my mobile Intel i915 graphics and Dapper (except for it can get a little slow when too many windows are opened).  All I had to go is enable exa and composite in my xorg.conf file and download and install the latest "common" and "i915" drivers from [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) .

---

### Post by Carrots171 on 2006-01-14
Hi, I have the latest Nvidia drivers (8178 ), and everything is working perfectly -BUT- the "logout bug" is still there; when I log out it crashes. Is there any way to correct this problem? Thanks for the help!

---

### Post by firehead on 2006-01-14
great howto, but somehow something doesnt' work the same as before... but first things first:
2 days ago, xcompmgr was running on my laptop and i had perfect transparent windows under fluxbox (running on kubuntu) by just typing 
```
xcompmgr -n
```
due to a little bit to much messing around with kernel configuration i decided to make a complete,neat reinstall of kubuntu, including the newest NVIDIA driver 8176 (used 7667 before) and the 2.6.12-10-686 kernel (...-386 before, and yes i'm using a 686 machine ;) ). and now i want transparency back. following poofyhairy's guide, i installed xcompmgr and transset-df (which i used before) and typed again xcompmgr -n and....nothing happened :(
now i can change opacity of single windows with transset, but every new window is totally opaque and all menues (incl. fluxbox menu) too. i'm totally sure, that i didn't have to write any script on my old system to get transparent consoles popping up, xcompmgr did it all by itself...
well maybe i forgot something:rolleyes: , but i have no idea what i could have done more before...please help me :D

---

### Post by firehead on 2006-01-14
*banging my head against the wall*
well 9 minutes later i solved the problem myself...sorry for bothering your thread poofy, but sometimes solving a problem is so simple, that i just don't see it...fluxbox has a menu for transparency, where everything can be set...which i just did ;)

a nice weekend to every1 who managed to get transparency working, and good luck to everybody else ;)

---

### Post by jpkotta on 2006-01-14
Has anyone tried using FVWM with xcompmgr?  I'm afraid it's still unstable for me.  

Steps to reproduce: 
Run FVWM with a null config.  Open an app, iconify it, and somehow remove the icon from view.  The apps I was able to reproduce the problem with were the GIMP, GQView, gnome-terminal, Firefox, and FrostWire.  I think the common trait is that all of them supply an icon pixmap.  It doesn't matter if a window is moved over the icon or if the window is already over where the icon appears (icons are automatically lowered).  It seems that the icon has to be completely covered.  It happens even if you move to a different page.  

Symptoms: 
Xorg and fvwm use a lot of CPU.  Sometimes X uses more, sometimes fvwm.  xcompmgr sometimes starts leaking memory at around 1 MB/sec.

Fixes: 
Kill xcompmgr, the iconified app, or uncover the icon.

I've tried using twm to reproduce the error, no go.

EDIT:
Tried again, fiddling with icon styles.  If I do "Style * NoIconTitle", it works great.

---

### Post by limit223 on 2006-01-15
I don't know if someone noticed KDE fake transparency does not require composite.
I address especially for people with ATI cards which have known issue in enabling it and  keeping installed ati driver full function at the same time.
 Make just Qt applications menus transparent is now the only eye-candy feature that I use on my desktop and it is not a giant eater of resource comparing composite.

If you wanna have it just do as simple as it is:
Kcontrol - Appearance & Themes - Style - Effects tab - Menu effect: select-Make Translucent
if want shadows: check - Menu drop shadow, choose a type and a percent of opacity.

Some shots are shown below:

---

### Post by poofyhairguy on 2006-01-16
[QUOTE=Carrots171]Hi, I have the latest Nvidia drivers (8178 ), and everything is working perfectly -BUT- the "logout bug" is still there; when I log out it crashes. Is there any way to correct this problem? Thanks for the help![/QUOTE]

Well...I think Ubuntu will have a new log out screen in Dapper, but for me the driver fixed the problem.

Best thing to remember is to his "esc" if you logout without remembering to 

killall xcompmgr

Its not frozen, I promise.

---

### Post by poofyhairguy on 2006-01-16
[QUOTE=firehead]*banging my head against the wall*
well 9 minutes later i solved the problem myself...sorry for bothering your thread poofy, but sometimes solving a problem is so simple, that i just don't see it...fluxbox has a menu for transparency, where everything can be set...which i just did ;)

a nice weekend to every1 who managed to get transparency working, and good luck to everybody else ;)[/QUOTE]

Using Kwin with Xcompmgr is a bad idea for the same reason- it has its own compositor.

---

### Post by firehead on 2006-01-16
> Using Kwin with Xcompmgr is a bad idea for the same reason- it has its own compositor.


well i can just set transparency options for different things like (un-)focused window alpha, or menu alpha in the fluxbox configuration menu, but transparency wouldn't work without xcompmgr...so it's mandatory to use xcompmgr to get transparency in fluxbox (imho).
now it's working flawless

---

### Post by poofyhairguy on 2006-01-16
[QUOTE=firehead]well i can just set transparency options for different things like (un-)focused window alpha, or menu alpha in the fluxbox configuration menu, but transparency wouldn't work without xcompmgr...so it's mandatory to use xcompmgr to get transparency in fluxbox (imho).
now it's working flawless[/QUOTE]


Sorry my mistake. Its XFCE with the built in compositor.

---

### Post by piedamaro on 2006-01-17
I'm not jelous. But think about me when you kill metacity. ;)

---

### Post by ember on 2006-01-17
Finally I tried this guide and I admit: Drop shadows and fading effects are just damn sexy, yet they keep crashing my OpenOffice (unofficial 2.0.1) and everytime I log out of gnome with more then just xcompmgr -a, my system crashes.
Anybody else with this problem?

---

### Post by commodore on 2006-01-19
I don't like that it changes the transparency of the whole titlebar or window. It would be great if it would change the background of those only. Not the text and buttons.

---

### Post by poofyhairguy on 2006-01-19
[QUOTE=commodore]I don't like that it changes the transparency of the whole titlebar or window. It would be great if it would change the background of those only. Not the text and buttons.[/QUOTE]

Send a bug report to KDE. If you get a response post it here. We would love to know.

---

### Post by poofyhairguy on 2006-01-19
[QUOTE=ember]Finally I tried this guide and I admit: Drop shadows and fading effects are just damn sexy, yet they keep crashing my OpenOffice (unofficial 2.0.1) and everytime I log out of gnome with more then just xcompmgr -a, my system crashes.
Anybody else with this problem?[/QUOTE]

it does not crash when you log out of Gnome, the log out screen is just too small to see.

hit "esc" to unfreeze the computer.

---

### Post by poofyhairguy on 2006-01-19
[QUOTE=piedamaro]I'm not jelous. But think about me when you kill metacity. ;)[/QUOTE]

I will....one day Metacity might rise again!

---

### Post by paul cooke on 2006-01-19
oohh this is just so neat... Thanks guys... that £60 I shelled out yesterday for a "new" nvidia card is well worth it, the previous one could only use legacy drivers...

Now things are just so much more snappier... but I did notice that if you left ordinary menu drop shadows enabled in the KDE settings things were slightly weird

---

### Post by ember on 2006-01-19
[QUOTE=poofyhairguy]it does not crash when you log out of Gnome, the log out screen is just too small to see.

hit "esc" to unfreeze the computer.[/QUOTE]

Ah - thanks. Actually you are right, but it still leaves the question: How do I log out with xcompmgr enabled. Is there any way other than changing WMs?

Best regards,
ember

---

### Post by veritas366 on 2006-01-19
Oh the IRONY.  I clicked on the mpg at the beginning...and got a black screen inside my browser which has video controls but won't actually play.  This is the current way my Firefox "plays" embedded mpegs.  Worked before the breezy update. I know this is way off topic but since the number one issue I have with Ubuntu is multimedia (and this isn't even using a nonfree codec or anything) I thought I'd share the irony.  

I know...there are ways to fix it.  I spent so much time last time...trying mozplugger.  Trying mplayer...deleting mplayer and trying totem.  Right now...I simply right click and save all videos.  Real media player works for those files...and that's nonfree.

Sigh.

Sorry for the OT comment.  Couldn't stop myself.

---

### Post by poofyhairguy on 2006-01-20
[QUOTE=ember]Ah - thanks. Actually you are right, but it still leaves the question: How do I log out with xcompmgr enabled. Is there any way other than changing WMs?

Best regards,
ember[/QUOTE]

Getting the newest drivers fixed it for me. I seem to be a rarity. The only other solution for Xcompmgr is to make it easy to turn on and off (from the trick on the first page) and turn it off.

---

### Post by piedamaro on 2006-01-21
[QUOTE=poofyhairguy]Getting the newest drivers fixed it for me. I seem to be a rarity. The only other solution for Xcompmgr is to make it easy to turn on and off (from the trick on the first page) and turn it off.[/QUOTE]
If you disable the logout prompt with gconf-editor (apps/gnome-session/options) it works, but it just ends the session and starts gdm.

---

### Post by Jucato on 2006-01-24
I've tried out this guide and updated my NVIDIA driver as well, but ran into some problems. Just like to ask 2 questions:

1. Do I need to install xcompmgr, if I'm using Kubuntu?
2. When using shadows/transparencies, I monitored my Xorg's VmSize performance. It starts out around 100,000, but shoots up to 800,000. Even while I only have 2 windows open! Is this a normal behavior when using composites? I mean I can understand if xorg w/ composites would use around 200,000+ VmSize, but for it to gradually grow to the limit of my RAM? It's like xorg is trying to eat up any and all remaining free space.

Here are my specs, btw:
AMD Sempron 2200 (1.5 GHz)
256 RAM
NVIDIA GeForce4 MX 4000 128 MB

If I turn composite off, My xorg stays around at 60,000+ VmSize.

---

### Post by fannymites on 2006-01-25
If you use smeg/alacarte it's pretty easy to make a shutdown/reboot menu which you can also add to the panel in place of the logout applet (if you use it).

---

### Post by ember on 2006-01-25
Good idea. I will try it tomorrow. Yet now it's time to sleep - for my computer as well as for me ;)

---

### Post by SilvioTO on 2006-01-26
I have nvidia GeForce4 MX 440 and when activate composite work well. The problem come when I open twice windows, close and open another, for example, it place in foreground and hide all gnome panels.
If I start composite at boot, the bottom panel of gnome don't appear.
Is a know problem? thanks for your help.

Silvio.

---

### Post by scrooch on 2006-01-26
I haven't read all this in here;

Running Dapper: I think the new kernel is compiled with gcc 4.0 so perhaps CC should be adjusted too. (But on the other hand, somehow method2 is failling for me although nvidia-installer doesn't give errors, modprobing doesnt give errors but starting X states module nvidia can't be loaded/found) 

Anyways...

How to get the menus  Applications, PLaces and System transparant? Just transset and clicking the panel doesnt make the menus themselves transparant unfortunately!:confused:

---

### Post by fannymites on 2006-01-26
Right-click on panel and select properties (or preferences, can't remember) and change the background to solid colour then adjust the transparency that way.

---

### Post by RAOF on 2006-01-26
[QUOTE=scrooch]I haven't read all this in here;

Running Dapper: I think the new kernel is compiled with gcc 4.0 so perhaps CC should be adjusted too. (But on the other hand, somehow method2 is failling for me although nvidia-installer doesn't give errors, modprobing doesnt give errors but starting X states module nvidia can't be loaded/found) 

Anyways...

How to get the menus  Applications, PLaces and System transparant? Just transset and clicking the panel doesnt make the menus themselves transparant unfortunately!:confused:[/QUOTE]
Dapper has (I think) the latest nVidia drivers in the repositories.  It's 81.78.  Just install the nvidia-glx package.  The kernel is being replaced too often in Dapper to manually install the nvidia drivers - you'd need to install them again every couple of days ;)

---

### Post by Jucato on 2006-01-26
does xorg have a leak when using composites in KDE (kompmgr)? I'm using the latest nvidia driver (8178). Does anyone have any idea?

---

### Post by poofyhairguy on 2006-01-26
[QUOTE=Fenyx]does xorg have a leak when using composites in KDE (kompmgr)? I'm using the latest nvidia driver (8178). Does anyone have any idea?[/QUOTE]

Yeah....there seems to be no compositor that does not leak when shadows are turned on. That is the one thing we don't get yet.

Without shadows I never get leakage.

---

### Post by Jucato on 2006-01-26
oh, so is it possible to use transparency without the shadows and not have leaks? Thanks for your answer poofyhairguy, at least now I can rest my mind that I haven't done something wrong (yet). :D

---

### Post by scrooch on 2006-01-27
> Right-click on panel and select properties (or preferences, can't remember) and change the background to solid colour then adjust the transparency that way.


Hehe yeah, but what I exaclty mean is, if you click on Applications. How to get the menu which you will get then (accessories, gaphics, internet etc) transparant?

---

### Post by poofyhairguy on 2006-01-27
[QUOTE=Fenyx]oh, so is it possible to use transparency without the shadows and not have leaks? Thanks for your answer poofyhairguy, at least now I can rest my mind that I haven't done something wrong (yet). :D[/QUOTE]

Yeah without shadows it seems to be fine. And honestly the Kwin compositor does not leak THAT bad....I use it.

---

### Post by poofyhairguy on 2006-01-27
[QUOTE=scrooch]How to get the menu which you will get then (accessories, gaphics, internet etc) transparant?[/QUOTE]

You can't. I tried for hours. There is no way that I have found. If you really want such things try using XFCE's or KDE's panels in Gnome (Kicker works pretty good in Gnome).

The menus won't get transparent until Gnome has a native/full featured compositor....and they are REALLY dragging their feet on that. So it might be a while. I am starting to believe that if compositing did not have usability benefits (aka allows for blinder people to have a neat zoom in feature) Gnome would have waited till the last possible second to start making a compositor (and they almost have). I have never seen a group in Linuxland that cares out eye candy less outside of the "CLI for everything, Linux is for servers!" crowd.

With that said, maybe KDE's compositor will make the Gnome menus translucent soon. As you can tell from me attached screenshot, using my Knome Guide you can make the Gnome Panels become translucent easily. Also notice how well the Kwin theme I use (aka the title bar theme) matches the Clearlooks Cairo scroll bars very well. 

Its better to give up on Metacity and native Gnome compositing for at least a few months.

---

### Post by veritas366 on 2006-01-31
sorry if this has been answered. I like the way things look...but too much weirdness.  I haven't read all of this thread...please point if I need to see something already posted.

First, the window behavior isn't working quite right...often, when a window is opened in front of another window, only the top left corner shows until I actually move the window.  clicking on it wont' work.  This happens a vast majority of the time.  I thought it was the shadows..but turning them off didn't help.

It's too annoying to keep...but I love how things look.  Suggestions?

Second, I've run into this with other themes I've downloaded that go beyond simply changing window borders etc.  At the moment, it seems kcontrol is what set my Firefox colors.  The main window decorations are fine and in keeping with the them I chose with kcontrol.  However, somehow I changed the color of certain areas (don't know what they are called) to a lavender color I'd like to change.  For example, right now, my sidepanels have this background color, as does the place where i enter the title above this post.  However, the background of the box  I currently type in is the normal cream color.

I tried changing colors within the firefox preferences, but choosing "use system colors" or use my colors seems not to change things at all.  Something is overriding it.  Changing colorschemes manually in kcontrol (very cool) also doesn't affect anything but the window itself.  

I like the dark blue theme in kcontrol but it doesn't carry over.  I don't mind if firefox doesn't match....but I'd like to dump the lavender background of the sidepanels and certain text boxes.

So...weird partial windows popping up and unwanted lavender tones. Thanks for the guide overall...and if anyone can help with these odd bits...I'd be grateful.

---

### Post by veritas366 on 2006-01-31
Investigating further...I see that it is the transparency effect that's doing it.  I turned off everything else...but only after I unchecked transparency did the partial windows appearances stop.  You've seen the kind of thing before...even just passing the cursor over the "invisible" parts will make some of it appear.

I did download the most recent nvidia drivers...and enabled compositing, etc...I think I followed all the directions correctly.  And all the compositing effects WORK...it's just that the windows don't materialize fully when I open a new program.  I'd love to make this work...so any help would be nice.

---

### Post by funkyou on 2006-01-31
Hello there, I have a question:

I use composite under KDE with the kompmgr since a few days, and it
works very good...
But there is one problem i cannot fix, and this applies to Konqueror and
amaroK only...

When i start one of these programs and move them around, they get only
non-transparent when i move them... When i am not moving them, they
switch to transparent EVEN when they are on focus and activated, and
even when they are the only window on the Desktop too...

(I have kompmgr configured, that only the non-focused windows will be
transparent...)

I think this is very annoying...

Have played with the setting, but for me there is no way to fix this...
I have a nVidia GeForce FX5200 with the freshest NVidia-drivers...

Has anyone here experienced the same problem, and has fixed this in
any way? I would be glad if there is a way to get around this annoying behavior...

I have attached some screenshots with my settings... oh, and just as i made
the screenies i noticed that this behavior also applies to ksnapshot... :???: 

greeting and btw: this is a great thread :)


-EDIT- I have attached a screenie of the behavior, its the last one below...
As you can see, Konqueror stays transparent even when activated and in
the foreground... But when i move the window, he gets non-transparent...

---

### Post by poofyhairguy on 2006-02-01
[QUOTE=funkyou]Hello there, I have a question:

I use composite under KDE with the kompmgr since a few days, and it
works very good...
But there is one problem i cannot fix, and this applies to Konqueror and
amaroK only...

When i start one of these programs and move them around, they get only
non-transparent when i move them... When i am not moving them, they
switch to transparent EVEN when they are on focus and activated, and
even when they are the only window on the Desktop too...

(I have kompmgr configured, that only the non-focused windows will be
transparent...)

I think this is very annoying...

Have played with the setting, but for me there is no way to fix this...
I have a nVidia GeForce FX5200 with the freshest NVidia-drivers...

Has anyone here experienced the same problem, and has fixed this in
any way? I would be glad if there is a way to get around this annoying behavior...

I have attached some screenshots with my settings... oh, and just as i made
the screenies i noticed that this behavior also applies to ksnapshot... :???: 

greeting and btw: this is a great thread :)


-EDIT- I have attached a screenie of the behavior, its the last one below...
As you can see, Konqueror stays transparent even when activated and in
the foreground... But when i move the window, he gets non-transparent...[/QUOTE]


I have the same problem with Firefox every now and then. Its a definate bug and I'm trying to figure out how to report it.

---

### Post by onesojourner on 2006-02-01
this is awesome. makes me want to build a faster system so it runs smoother but its still awesome. this is the stuff dreams are made of..(at least in the realm of a desktop)

P4 1.8
512 RAM
asus NVIDIA 5200 (64 MB) with latest drivers.

---

### Post by Jeff250 on 2006-02-01
[QUOTE=Jeff250]Great guide.  I was wondering:  How can I disable the default Metacity window maximize/minimize effects?  I know that I can using gconf-editor and toggling /apps/metacity/general/reduced_resources, but this also enables wireframe windows when you're moving them, which is pretty ugly looking.  The default metacity behavior when maximizing/minimizing windows is interfering with my effects. :-?[/QUOTE]

I've since discovered a way to disable the cheezy Metacity minimize effects without causing wireframe windows upon move:
First enable:
/apps/metacity/general/reduced_resources
Then enable:
/desktop/gnome/interface/accessibility
I haven't exactly noticed any other effects yet of enabling the accessibility, but it does disable the wireframe windows when you move them.
EDIT:  See [this post]("http://www.ubuntuforums.org/showthread.php?p=702089#post702089") for a potential problem!

Instead of xcompmgr, I'm also now using Metacity with kompmgr, KDE's compositor.  With Cairo effects and a Clearlooks theme on top of this all, Metacity is definitely looking great!

---

### Post by poofyhairguy on 2006-02-01
[QUOTE=Jeff250]
Instead of xcompmgr, I'm also now using Metacity with kompmgr, KDE's compositor.  With Cairo effects and a Clearlooks theme on top of this all, Metacity is definitely looking great![/QUOTE]

Good call. I just tried it an it kinda works well. I now officially suggest using this to get ones drop shadow fix.

How to do it? First of all go to my Knome guide and install Kwin like I tell you to there. But don't do the parts that replace Metacity. Instead start kcontrol with the command "kcontrol" and set up the settings just like you want (be sure to turn on "translucency/shadows" with the checkbox. When you have the drop shadow and fading as you want them, use this trick in metacity with this command:

kompmgr

I do not recommend this for anyone that does not REALLY need Metacity as it offers almost no features that xcompmgr does not also offer. You don't get the cool translucent Gnome Panels this way (which really start to grow on you after a while), you don't get the window border translucency, you don't get the improvements of overall use (aka you still have to kill the gnome panel).

But if all you want out of compositing is drop shadows, then use kcompmgr over Xcompmgr. I might ever gut that part out of my guide....

---

### Post by Jeff250 on 2006-02-01
Now that I've got Metacity's cheezy minimize effects disabled, the compositor fading on minimize works flawlessly as well.  Menus, tool-tips, and other various pop-ups like Amarok's OSD also fade nicely.  Closing a window doesn't fade though, probably because without the foresight of a window manager with built-in compositor (such as kwin) to keep the window open for the fading effect, it just closes immediately and this prevents the fade from being able to occur, but I don't really mind this.

Using kwin itself undoubtedly had better graphics effects options over Metacity.  But it was just really messy, having to use two different "control panels" and trying to guess which one had "sovereignty" (if not both of them, which was even messier) over a certain setting.  I also was never able to solve a bug where KDE apps like Amarok and Kopete would not put their icons in gnome's notification area on the panel.  They were probably trying to use KDE's panel (which I believe is called "kicker") which wasn't available, even though I was using kwin.

So I'm satisfied with my current Metacity solution, which compromises graphics and ease of use in a way that is suitable for my tastes.

I'm also running Dapper, so I don't know to what extent that affects my experience.

---

### Post by Paulus on 2006-02-02
I'm not sure if this is just specific to me...  I've noticed within this thread and outside of it that alot of people are complaining about e17 and xcompmgr/kompmgr.   Just letting you all know that the latest cvs of e17 and xcompgr/kompmgr is 100% stable for me... using it full time and it's bliss!

heres a screenshot with some gnome love:
[IMG]http://ubuntuforums.org/gallery/files/1/9/2/8/1/snapshot6.jpg[/IMG]

---

### Post by Jeff250 on 2006-02-02
[QUOTE=Jeff250]I've since discovered a way to disable the cheezy Metacity minimize effects without causing wireframe windows upon move:
First enable:
/apps/metacity/general/reduced_resources
Then enable:
/desktop/gnome/interface/accessibility
I haven't exactly noticed any other effects yet of enabling the accessibility, but it does disable the wireframe windows when you move them.[/QUOTE]

Gr, I've noticed one potential bug:  Hitting "Apply" in the "Apply the following changes" dialogue in Synaptic seems to cause Synaptic to crash.  This is with the latest version of Dapper.  Can anyone else confirm or deny this bug who might be using Dapper or Breezy?  It seems that by disabling /desktop/gnome/interface/accessibility (for me at least), logging out, and then back in resolves the issue.

---

### Post by Rizado on 2006-02-12
I just bought a nvidia 6600gt going from a R9500PRO, This is really cool and works great. Although I'm using KDE, No crashes so far. (Have only been running it for a couple of hours)

I read through the bugs at the end of the post, I did experience some artifacts when running kaffeine (I'm running it with xine because I want DVB support) however when I changed to xshm video driver in xine it disappeared. Transparacy affects the movie  too. The CPU usage went up a little but not much, From 13% to about 20% (This is while decoding a TS stream) Maybe this is just when using KDE but it could be worth a shot.

No openglscreensaver crash bug in KDE either, and Firefox works great. I don't now about games because I don't have any installed yet.

---

### Post by linkunderscore on 2006-02-12
I apologize if this has already been mentioned but I don't really have the patience to read through this entire thread to check and see if this has already been posted. 

But I believe I found a bug involving conky. 

If conky is running on the desktop the shadows that shoudl be on the desktop wallpaper go away when conky refreshes. The shadows remain on other windows , but if the shadow falls on the desktop it goes away when conky refreshes. If I close conky this goes away. I haven't found a work around, and I don't plan on trying to ;). I like shadows more than I like conky.

---

### Post by joehill on 2006-02-14
Thanks for the tip, Jeff 250.  I've got the Intel 955GM chipset (I believe virtually the same thing you have).  But when I try to install the latest cvs from freedesktop.org (the common DRI package and the i915 drivers package) I get errors:

> 
The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.


My first impression is to think, do these bleeding edge cvs builds only run on a bleeding edge kernel?

Does anyone have any more details on installing these, or general tips on getting it to work with Intel integrated chipsets?  The effects are really cool but they are slow enough that they're counterproductive for me.  I do a lot of window switching and waiting a second or two for the alt-tab dialog to come up or for my web pageto scroll is really annoying.

No crashes yet--my screen just gets a bit lazy.

---

### Post by bluebyt on 2006-02-15
[QUOTE=deception]Great job! Just would like to add if anyone experiences the "overlapping of the gnome-panel by applications".. just type "killall gnome-panel" in a terminal :KS 


Thanks poofyhairguy :D[/QUOTE]

Does anyone have this bug  "overlapping of the gnome-panel by applications"
When I do the "killall gnome-panel"  I lost the bottom panel, it is very annoying?
(I have the latest nvidia drivers)

When I used this command at startup "xcompmgr -fFcC" sometime the top and the bottom panel are not visible?

Is it because I am on breezy, does it work better on dapper?

I am little disappointed on the stability of this!

---

### Post by jannol on 2006-02-15
Did you install that xcompmgr file linked in the first message. I think there might be issues with others, also, there can be a few issues due to different kernels, graphiccards etc, I had similar issues on my other computer with its geforce mx card.

---

### Post by Parkotron on 2006-02-16
Wow, this thread has really died off since XGL and Compiz were released.

Anyway, for those of you using KDE's kompmgr I thought I'd share that I found a really easy way to enable/disable compositing. KWin has  dcop functions to turn kompmgr on and off. So I wrote a ridiculously simple bash script to toggle kompmgr on and off:
```

#! /bin/bash 

if [[ "`dcop kwin KWinInterface kompmgrIsRunning`" == "false" ]]; then
	dcop kwin KWinInterface startKompmgr 
else
	dcop kwin KWinInterface stopKompmgr 
fi

exit 0
```
I then used KHotkeys to assign this script to a global shortcut (win+`). Now I can turn compositing on and off really quickly, which can be really useful if it starts acting up.

Hope this helps someone.

---

### Post by nismoskys on 2006-02-17
when i try to run xcompmgr (or even the gui version) my comp crashes beyond control, no ctrl alt backspace or anything fixes it.. (however the mouse still moves, but doesnt click on anything) only solution is to restart from the tower..

---

### Post by poofyhairguy on 2006-02-17
[QUOTE=Parkotron]Wow, this thread has really died off since XGL and Compiz were released.

Anyway, for those of you using KDE's kompmgr I thought I'd share that I found a really easy way to enable/disable compositing. KWin has  dcop functions to turn kompmgr on and off. So I wrote a ridiculously simple bash script to toggle kompmgr on and off:
```

#! /bin/bash 

if [[ "`dcop kwin KWinInterface kompmgrIsRunning`" == "false" ]]; then
	dcop kwin KWinInterface startKompmgr 
else
	dcop kwin KWinInterface stopKompmgr 
fi

exit 0
```
I then used KHotkeys to assign this script to a global shortcut (win+`). Now I can turn compositing on and off really quickly, which can be really useful if it starts acting up.

Hope this helps someone.[/QUOTE]

Nice!

---

### Post by magomago on 2006-02-24
Ty VERRRY much.  I'm not one for all too nice of effects...but using this REALLY speeded things up.  My main linux complaint was the fact that the GUI was too unresponsive, and this REALLY put things in order!

---

### Post by vbmaster on 2006-02-24
Well, I'm having a bad experience with this tut.

I did everthing that was for me on this tut, and all run well. At the end, I tried some xcompmgr commands, and some crashed my desktop, while others resulted in beutiful things.

I don't know if this one was for me (i've a gForce4 mx 440) "xcompmgr -cC -t-3 -l-5 -r5", but after I run it my gnome pannel froze, and after the usual restart from the tower, my gdm just stop showing to me, after the loading screen of the ubuntu.

I received a black screen and after a some minutes I've an console version of the gdm that I don't want...

I want my gdm back... :P... :'(

P.S.: startx is not solution for me.... it works..but what I really want is my gdm.... :|

---

### Post by mcwtlg on 2006-02-24
It is still hanging during shutdown...nice effects, but a tad slow.  The shutdown bug sucks as well.

I am using the latest 32 bit driver from the Nvidia site, installed with the how to from tseliot.

Geforce 5600 FX w/256 megs video RAM, P4 3 ghz, 512 system RAM.

PoofyHariGuy, I had a question.  Your how to differs somewhat from the "newbie FAQ/Readme" included with the gCompMgr deb file.  Any comments?

(I am not criticizing at all!  Just curious.  Yours is MUCH clearer, but they have info listed that conflicts with yours.  I am pretty new to Linux generally and just got my dual boot working and am ery happy with Ubuntu Linux so far)

Here is the readme included:

################## IMPORTANT BUG NOTES ########################
Due to some kind of bug with Gnome and xcompmgr, if you have xcompmgr enabled 
and you click on Actions->Log Out, your window manager will freeze.
You can safely shutdown by opening a terminal, and entering
shutdown 0 -h

################### xcompmgr INSTALLATION #####################

If you haven't already, fetch xcompmgr from freedesktop.org

cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps login
[No password needed, just press return]
cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps co xcompmgr

cd xcompmgr
export PKG_CONFIG_PATH=/usr/X11R6/lib/pkgconfig/
./autogen.sh
./configure
make
su
[password]
make install

################### XORG CONFIGURATION #######################

The X configuration file is at /etc/X11/xorg.conf

You must be running either the ATI drivers from ati.com or the nvidia drivers from nvidia.com
The vesa video driver, with no hardware 3d acceleration will not cut it for running xorg compositing.
So if you haven't installed your cards commercial linux drivers, please do so before starting.

##############################################################
# NVIDIA VIDEO CARD GUIDE

Driver WILL be "nvidia", if you have a driver called "nv", that won't cut the mustard,
you must have the "nvidia" driver from nvidia.com to make this work in hardware mode.
"nv" only has 2d acceleration so it is not suitable.

su to root, then open /etc/X11/xorg.conf

##### make sure your module section looks like this

Section "Module"
	Load  "dbe"
	Load  "extmod"
	Load  "fbdevhw"

# CHECK FOR THIS ONE
	Load  "glx"
	Load  "record"
	Load  "freetype"
	Load  "type1"

# CHECK FOR BOTH OF THESE
	Load  "dri"
	Load  "GLcore"
EndSection

##### make sure your Device section looks like this

Section "Device"
	Identifier  "Videocard0"
	Driver      "nvidia"
	VendorName  "Videocard vendor"
	BoardName   "NVIDIA GeForce FX (generic)"

# CHECK FOR BOTH OF THESE
	Option     "RenderAccel" "true"
	Option  "AllowGLXWithComposite" "true"
EndSection

##### add these at the end of the file

Section "Extensions"
        Option "Composite" "Enable"
        Option "RENDER" "true"
        Option "DAMAGE" "true"
EndSection

##############################################################
# ATI VIDEO CARD GUIDE

Driver may be "ati" or "fglrx"

su to root, then open /etc/X11/xorg.conf

Find

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
        Driver          "ati"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "true"
EndSection


To

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
        Driver          "ati"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "true"

        Option          "backingstore"          "true"
        Option          "RenderAccel"           "true"
EndSection


and add

Section "Extensions"
        Option "Composite" "Enable"
        Option "RENDER" "true"
        Option "DAMAGE" "true"
EndSection

---

### Post by poofyhairguy on 2006-02-25
[QUOTE=vbmaster]Well, I'm having a bad experience with this tut.

I did everthing that was for me on this tut, and all run well. At the end, I tried some xcompmgr commands, and some crashed my desktop, while others resulted in beutiful things.

I don't know if this one was for me (i've a gForce4 mx 440) "xcompmgr -cC -t-3 -l-5 -r5", but after I run it my gnome pannel froze, and after the usual restart from the tower, my gdm just stop showing to me, after the loading screen of the ubuntu.

I received a black screen and after a some minutes I've an console version of the gdm that I don't want...

I want my gdm back... :P... :'(

P.S.: startx is not solution for me.... it works..but what I really want is my gdm.... :|[/QUOTE]

Resinstall GDM.

---

### Post by poofyhairguy on 2006-02-25
[QUOTE=mcwtlg]It is still hanging during shutdown...nice effects, but a tad slow.  The shutdown bug sucks as well.

I am using the latest 32 bit driver from the Nvidia site, installed with the how to from tseliot.

Geforce 5600 FX w/256 megs video RAM, P4 3 ghz, 512 system RAM.

PoofyHariGuy, I had a question.  Your how to differs somewhat from the "newbie FAQ/Readme" included with the gCompMgr deb file.  Any comments?

(I am not criticizing at all!  Just curious.  Yours is MUCH clearer, but they have info listed that conflicts with yours.  I am pretty new to Linux generally and just got my dual boot working and am ery happy with Ubuntu Linux so far)
[/QUOTE]

This is guide far more complete and up to date than the gcompmgr file.

Though honestly at this point I recommend that people really don't use any sort of xcompmgr anymore. 

Its better to use my Knome Guide:

[http://www.ubuntuforums.org/showthread.php?p=771053#post771053](http://www.ubuntuforums.org/showthread.php?p=771053#post771053)

---

### Post by jnk on 2006-02-28
I realy love this howto, great work.!!!!!
I got a AMD Athlon XP 2800+ (Barton Kernel) and a GeForce3 Ti400 gfxcard.
Using Ubuntu Brezzy, well well, thats a little info, now for the issue. ;)

If I use ONLY the fading effect, everything works like a charm, fast and stable.
But I want the shadow effect, the fading is just a pain in the *** ... =)
I have Firefox 1.5.0.1 running ( to see the guide) and the gnome-terminal to enter the shadow command.
I get shadows BUT if I try to minimize or resize (maybe close) the terminal everything freezes.
I cant event ctrl alt backspace, nothing happens... just hardreboot.
Is it my card thats the problemo or.? Have the latest repo nvidia drivers.
will updating drivers help.? updating xorg.? using opera instead of firefox.?
please help, I realy realy want the shodow thingy to work....!

---

### Post by poofyhairguy on 2006-02-28
[QUOTE=jnk]I realy love this howto, great work.!!!!!
I got a AMD Athlon XP 2800+ (Barton Kernel) and a GeForce3 Ti400 gfxcard.
Using Ubuntu Brezzy, well well, thats a little info, now for the issue. ;)

If I use ONLY the fading effect, everything works like a charm, fast and stable.
But I want the shadow effect, the fading is just a pain in the *** ... =)
I have Firefox 1.5.0.1 running ( to see the guide) and the gnome-terminal to enter the shadow command.
I get shadows BUT if I try to minimize or resize (maybe close) the terminal everything freezes.
I cant event ctrl alt backspace, nothing happens... just hardreboot.
Is it my card thats the problemo or.? Have the latest repo nvidia drivers.
will updating drivers help.? updating xorg.? using opera instead of firefox.?
please help, I realy realy want the shodow thingy to work....![/QUOTE]

The best bet is to use the Nvidia Guide to update your drivers to the newest version- only they are stable enough for use.

---

### Post by jnk on 2006-02-28
well, I downloaded the "NVIDIA-Linux-x86-1.0-8178-pkg1.run" from nvidia.com and tried to install it.
I have the K7 kernel and all extras to it, headers and so.
But when I trie to run the NVIDIA installer it just tells me that it cant find nvidia.ko or something like that and the installer ends. =(

---

### Post by mcwtlg on 2006-02-28
Wrong Thread ... reposting :( in the Nvidia thread.

---

### Post by kwaanens on 2006-02-28
[QUOTE=poofyhairguy]Who can use a Composite Manager? I hate to say it, but only people with Nvidia cards, an ATI 9250 card (or lower) and Dapper, or a fast enough computer. [/QUOTE]

What is ATI 9250 *and lower*?
I have an ATI x300 or whatever it's called on my Dell Inspiron 9300. Is that supported?
FWIW: I have 3d acceleration going fine.

- Ketil

---

### Post by RAOF on 2006-02-28
[QUOTE=kwaanens]What is ATI 9250 *and lower*?
I have an ATI x300 or whatever it's called on my Dell Inspiron 9300. Is that supported?
FWIW: I have 3d acceleration going fine.

- Ketil[/QUOTE]
Just what it says:  an ATI 9250 or older card.  Your card's newer, so is not supported (well) by the open-source drivers, and the binary ATI driver's composite support stinks.

---

### Post by poofyhairguy on 2006-02-28
[QUOTE=jnk]well, I downloaded the "NVIDIA-Linux-x86-1.0-8178-pkg1.run" from nvidia.com and tried to install it.
I have the K7 kernel and all extras to it, headers and so.
But when I trie to run the NVIDIA installer it just tells me that it cant find nvidia.ko or something like that and the installer ends. =([/QUOTE]

You have to follow (and write down some of) ALL of the red Method 2 here:

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

Its actually pretty darn hard to install the latest Nvidia drivers, but you have to do it if you want this stuff to be semi-stable. 

If you can't get it to work (and I don't blame you- its some command line time) I say think about upgrading to Dapper. No one who really cares about stability messes with this sort of stuff (even with the newest driver there are lock ups sometimes) so upgrading to Dapper will give you the new drivers. Heck, you can mess with XGL then (which is far beyond anything in this guide).

Or just install the new Nvidia drivers. Either way. But otherwise this is just not stable enough to mess with long term.

---

### Post by poofyhairguy on 2006-02-28
[QUOTE=kwaanens]What is ATI 9250 *and lower*?
I have an ATI x300 or whatever it's called on my Dell Inspiron 9300. Is that supported?
FWIW: I have 3d acceleration going fine.

- Ketil[/QUOTE]

No. Only older ATI cards work with this guide.

---

### Post by kwaanens on 2006-03-01
[QUOTE=RAOF]Just what it says:  an ATI 9250 or older card. [/QUOTE]

That's why I asked. I have no idea how ATI numbers its graphic cards, or how old 9250 is.

So, any hope for good ATI-support (soon), or should I find out how much it will cost to put in an Nvidia instead? (Any ideas anyone?)

- Ketil

---

### Post by Jucato on 2006-03-01
Just some quick questions I've been (almost) dying to ask. In Dapper, what Xorg version will be included? And how about composite managers? Can we expect a bit more stability in these coming release?

I've been able to successfully (after the nth try) install the NVIDIA driver (GeForce4 MX4000) and the kcompmgr works well, except for the annoying memory leak when it comes to shadows (which I would prefer to use over translucency...)

OT: More power to you poofy! :D

---

### Post by poofyhairguy on 2006-03-01
[QUOTE=kwaanens]That's why I asked. I have no idea how ATI numbers its graphic cards, or how old 9250 is.

So, any hope for good ATI-support (soon), or should I find out how much it will cost to put in an Nvidia instead? (Any ideas anyone?)

- Ketil[/QUOTE]

ATI seems to not want to change their ways. 

My official advice to anyone that asks is to move to an Nvidia card.

---

### Post by poofyhairguy on 2006-03-01
[QUOTE=Fenyx]Just some quick questions I've been (almost) dying to ask. In Dapper, what Xorg version will be included? [/QUOTE]

7.0

> 
And how about composite managers? Can we expect a bit more stability in these coming release?

Pretty much the same state of Breezy if you don't count compiz. Count that and its a whole new world.

---

### Post by Jucato on 2006-03-01
Oh I see. I hoped that maybe the composite managers would have improved. I guess I have to wait for the next update to kompmgr. Or try out this compiz thing, which I have absolutely no idea about. :D

---

### Post by poofyhairguy on 2006-03-01
[QUOTE=Fenyx]Oh I see. I hoped that maybe the composite managers would have improved. I guess I have to wait for the next update to kompmgr. [/QUOTE]

At this point most of the improvement will come from the composite extension getting better or drivers getting better. But neither has grown leaps and bounds since Breezy. KDE 3.5 has the most advanced "normal" compositor and you can get that now in Breezy. Big changes in this area will come from thing that are more than just a compositor, such as XGL + Compiz.


> Or try out this compiz thing, which I have absolutely no idea about. :D

Its worth looking into on Dapper.

---

### Post by Sutekh on 2006-03-02
Thanks so much for the effort you have poured into this guide poofyhairguy.

Also big thanks to tseliot for his excellent [NVIDIA HOWTO](http://ubuntuforums.org/showthread.php?t=75074).

I had no problems installing the 8178 Drivers, then was surprised at how easy it was to install xcompmgr.

Integrating with XFCE was a little harder, but the [Gentoo Wiki](http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency#Composite_manager_is_already_running_with_Xfce4) had a tip for turning XFCE's own composite manager off.

Cheers also to frodon for the toggle script.

Unfortunately pictures just don't do it justice.  I wanna get a video together but am scarce for time.  I absolutely love the desktop wrapping and auto-focussing ability of XFCE.  Combined with the composite manager it is mouth-watering.  
[ATTACH]6595[/ATTACH]
The first pic is the XFCE menu opening over Firefox.
  [ATTACH]6596[/ATTACH]
The second pic is me moving the mouse from one desktop to another, from Rhythmbox to Firefox.  This picture just can't hope to show how COOL that looks, sorry, but I hope you get the idea.

Now to create some space for Dapper and try Xgl/Compiz!

---

### Post by hitman012 on 2006-03-14
Regrettably, I can't seem to get everything to work properly here. Hardware acceleration of windows seems to be OK as well as the fading (which is nice), but using a command involving drop shadows results in a complete GUI lockup, needing a hard reset.

If it was maximising the CPU usage, I'd expect at least some responsiveness and the cursor does move smoothly but with no response from the windows at all. I understand that it's buggy, but surely this isn't simply a problem with the program?

I'm running it on a Duron 1.3GHz with 1GB of RAM and a GF4 MX440. My suspicion is the card, but I don't have an unused one to test it with (other rigs are PCI-E). 

Thanks in advance :)

---

### Post by John.Michael.Kane on 2006-03-14
@poofyhairguy I got this guide of yours to work minus the transparency, on laptop with a sis based gpu running dapper... how stable it is time will tell. good work on the guide ...

---

### Post by escape on 2006-03-14
Might want to add a note that this breaks fglrx on ATI cards, and gives you the Mesa stuff instead. Know any way to get around this (besides using xgl instead)? I'm pretty sure the exact cause is putting the Extensions/Composite Enabled part in xorg.conf.

---

### Post by pestypest on 2006-03-20
Hey poofhairguy, i was wondering if i could see ur xorg.conf file to see if mine looks the same? i tried to installing and  i killed X and i had to change evrything back to the way is was. I think i may have put a space or somthng in the wrong spot but im not sure so if maybe u could post it so i know what to look and how it should look that would be great. Also i was wondering if you could tell me if my specs meet the req's to run this?

Amd X2 4600+ smp kernal K8
Nvidia GO 7800 GTX 256mb
160 GB HD
2GB ram 
Ubuntu Breezy

Im trying this on my laptop.

---

### Post by RAOF on 2006-03-20
[QUOTE=escape]Might want to add a note that this breaks fglrx on ATI cards, and gives you the Mesa stuff instead. Know any way to get around this (besides using xgl instead)? I'm pretty sure the exact cause is putting the Extensions/Composite Enabled part in xorg.conf.[/QUOTE]
The ATI drivers are crap.  You can use **exactly** one of:
1) 3D acceleration
2) Composite

Your pick :(

Xgl gets around this problem by doing 2) with 1) :)

---

### Post by Sutekh on 2006-03-20
[QUOTE=pestypest]Also i was wondering if you could tell me if my specs meet the req's to run this?

Amd X2 4600+ smp kernal K8
Nvidia GO 7800 GTX 256mb
160 GB HD
2GB ram 
Ubuntu Breezy

Im trying this on my laptop.[/QUOTE]
I'm really no expert, but with hardware like *that* you really must be able to get it working.  You should keep track of *exactly* the commands you make, it may have been a erronous space that messed things up.  It was a really easy thing to setup for me.

Again, sweet hardware.

---

### Post by dartmusic on 2006-03-23
First off, I'd like to give a big thanks to Poofy for a great HOWTO.

Second, I'd like to know the best way to turn all of this off!  I've got it running and it's pretty damn breathtaking!  But (and there's always a but), it's SO unstable that I can't use it for long before Xorg starts using huge amounts of CPU and the screen redraws become extremely unstable to the point that clicking on anything in the kicker results in a big, fat nothing and I have to either do a ctrl-alt-backspace to restart the X server or sometimes it locks up the entire machine and I have to do a hard reboot.  This happens at least once a day.  

For now I'm going to wait a few more weeks for the stable Dapper release and try compiz, but for now I need to disable all of this stuff so as not to constantly be disrupted by lockups and such.  Do I simply remark out the two new lines that were added at the end of the xorg.conf file?   Is there something else?  I'm running this on an HP zd7000 series notebook with an Nvidia video card.

Thanks again.

---

### Post by RAOF on 2006-03-23
[QUOTE=dartmusic]...
For now I'm going to wait a few more weeks for the stable Dapper release and try compiz, but for now I need to disable all of this stuff so as not to constantly be disrupted by lockups and such.  Do I simply remark out the two new lines that were added at the end of the xorg.conf file?   Is there something else?  I'm running this on an HP zd7000 series notebook with an Nvidia video card.

Thanks again.[/QUOTE]
Yup.  Just comment out the "Composite" "Enable" bit, and don't try to load xcompmgr :)

---

### Post by dartmusic on 2006-03-23
Great...thanks!  (But, just to confirm: I'm running KDE, so there is no loading of xcompmgr, correct?  I just turn off all transparency in the settings?)

---

### Post by philcolbourn on 2006-03-25
Thanks for the procedure 'PHG'.
It works for me on a compaq evo n620c with ati radeon m7 7500.
I am running dapper if that makes any difference.
firefox doesn't seem to crash.

---

### Post by RAOF on 2006-03-25
[QUOTE=dartmusic]Great...thanks!  (But, just to confirm: I'm running KDE, so there is no loading of xcompmgr, correct?  I just turn off all transparency in the settings?)[/QUOTE]
Again, yes :)

---

### Post by StarQuake on 2006-04-18
I'm running the latest version of the NVIDIA drivers (8756) on an AMD64 but my logout window does not show up. Can It be fixed?

Also make sure you purged nvidia-glx or it might start complaining after a few reboots about something like fbmmx when starting Xorg.

---

### Post by glennric on 2006-04-21
I installed xcompmgr following the howto on a computer with the nvidia drivers installed from nvidia and a GeForce FX 5200.  It worked and looked great.  However, I didn't disable the xscreensaver and left my computer for a bit.  When I came back the xserver had crashed and I was back at a login screen.  I then uninstalled xcompmgr and set the xorg.conf file back to the way it was.  Now the xscreensaver still crashes the xserver, and so does any other software that uses GL.  For instance running glxgears crashes the xserver.  There are two possibilities here.  One is that something else was modified and not reset properly in the install/uninstall process.  The other possiblity is that running xcompmgr and GL software at the same time burned out the GL part of my video card.  Considering the smell of fried electronics that was coming from my computer I think the latter is the case.  I will do more testing and see exactly what the problem is.  Has anyone else experienced this?  In any case I think that there should be a warning in the howto that you may damage your video card using xcompmgr in combination with GL.

---

### Post by glennric on 2006-04-21
I reinstalled the nvidia drivers and now GL works again.  It seems that if GL software runs while xcompmgr is running that the nvidia drivers are corrupted.  Or something...

---

### Post by Iandefor on 2006-04-21
Wow, people are still using this guide? Must be popular. Or is it that Breezy is no friend of xgl and compiz :)?

---

### Post by dpm on 2006-04-28
Quoting the original post:

> **Second Bug: When you try to logout in Gnome, it seems to crash!**

THIS BUG IS GONE WITH NEWEST DRIVERS AND NVIDIA CARDS!!!!!  DANCING IN THE STREETS!!!!! 
Is this bug really gone? I'm using the latest driver from the dapper repos (8756) and everything seems to work fine except for the fact that every time I try to logout, the screen locks completely.

EDIT: I'm on Dapper and using a card with the GeForce2 MX/MX 400 chip.

---

### Post by djsroknrol on 2006-04-28
Thanks Poofyhairguy...

Gcompmgr makes playing with Xcompmgr alot more fun...

---

### Post by mannheim on 2006-05-03
> Is this bug really gone? I'm using the latest driver from the dapper repos (8756) and everything seems to work fine except for the fact that every time I try to logout, the screen locks completely.

If this is the bug where the logout window does not appear (because it's actually invisible), then I think this bug is **not** gone. At least, it happens to me.

But there's a workaround. You can disable the Ubuntu logout window and use the vanilla gnome logout dialogs  instead. (My experience here is with dapper -- might not apply to breezy.) To do this, open up gconf-editor and navigate to apps-->panel-->global. Then check "upstream-session". Restart the panel and you are all set.

The panel's System menu should now have two entries for "Log out ..." and "Shut down...", each of which puts up a simple dialog.

---

### Post by dpm on 2006-05-03
mannheim,

You are my hero.

Your workaround worked perfectly.

In case anyone is interested, this has already been reported as a bug for ubuntu:

[https://launchpad.net/distros/ubuntu/+source/gnome-session/+bug/24221]("https://launchpad.net/distros/ubuntu/+source/gnome-session/+bug/24221")

and also upstream in GNOME:

[http://bugzilla.gnome.org/show_bug.cgi?id=157822]("http://bugzilla.gnome.org/show_bug.cgi?id=157822")

although it still remains unconfirmed.

---

### Post by Aeon17x on 2006-05-05
I can also confirm that the logout bug is also present when using the 8756 drivers.

However, I can't use mannheim's workaround because the said option is not present in breezy. =|

---

### Post by ketsugi on 2006-05-11
Despite using the -C option, my gnome-panel still has a shadow. This is particularly disconcerting because I keep my panel at the top, which casts a largish shadow on even the active window's title bar.

Any idea what's wrong? Or is this the proper behaviour?

---

### Post by twiistedkaos on 2006-05-14
Is there any way to exclude certain programs? IE: Gdesklets, I don't want drop shadow on them since they are supposed to be transparent the shadow forms around the transparency.

---

### Post by slfd2525 on 2006-05-14
combine this with 3ddesktop... fading out to the selector makes it look amazing!!!

---

### Post by eokorie on 2006-05-15
How do I enable the composite manager in Metacity?  It does not show it listed in gconf.

---

### Post by ComplexNumber on 2006-05-15
didn't take me long to get the effects working. but when i configure it using gcompmgr, then save to gnome session, the next time i log in the panel isn't there. i have to go into gcompmgr, switch off xcompmgr, then start it again for the panel to show up and for the drop shadow effects etc to show. if i delete it from gnome session, i've noticed that the next time i log in,  xcompmgr is still running because the background of cairo-clock is transparent, but there are no effects such as drop shadows etc. i guess i'll work it out eventually.
using fedora core 5, i haven't had my system crash when using xcompmgr yet. mine seems to be really stable.

---

### Post by MichaëlVD on 2006-05-16
[QUOTE=ketsugi]Despite using the -C option, my gnome-panel still has a shadow. This is particularly disconcerting because I keep my panel at the top, which casts a largish shadow on even the active window's title bar.

Any idea what's wrong? Or is this the proper behaviour?[/QUOTE]

I have the same problem...

---

### Post by ComplexNumber on 2006-05-16
[quote=MichaëlVD]I have the same problem...[/quote]
it seems to be very temperamental. sometimes theres a shadow...sometimes not.

also, i have no problem using this in my root account(on fedora), but i can't for the life of me find out a way to have the effects enabled when i log into my root account. it just doesn't seem to want to. if, using gcompmgr, i stop xcompmgr, then start it again, i get the effects such as drop shadow etc. but that seems to be the only way. when i log into root, the effects are there, but the panel is gone. i've got round this by adding 'gnome-panel' to sessions so that the panel also shows up along with the drop shadow effects etc.

---

### Post by detyabozhye on 2006-05-23
With the new 8756 drivers, my compositing manager is now completely stable, video works correctly, OpenGL, whatever (I'm running XFCE, btw). But VLC still does funky stuff, I have to shade and unshade the window to make it show video, it won't show when it's maximized, and dragging or having something go by over the window messes the video up. MPlayer, Totem, XFMedia, Xine all work fine. What can I do to VLC to make it play correctly?

---

### Post by sal on 2006-05-23
set VLC video setting for "X11 video output"

thats what worked for me.

---

### Post by detyabozhye on 2006-05-23
Thanks. Works great! ^_^

---

### Post by horsefactory on 2006-05-23
Renderaccel stops Xmame working, at least on the nvidia drivers in the breezy repositories. :( Other than that, it's all great.

---

### Post by nami on 2006-05-29
Hi

How do you ONLY make the windows titlebar and the border transparent like windows vista?

nami

---

### Post by sal on 2006-05-31
[QUOTE=nami]Hi

How do you ONLY make the windows titlebar and the border transparent like windows vista?

nami[/QUOTE]

you click where it has the "apply translucency only to decorations"

---

### Post by Peepsalot on 2006-06-04
I am running xubuntu on a computer with onboard video (VIA S3 Unichrome Pro).  I set up compositing, but it runs very sluggishly.  Are there any tweaks I can do to improve performance of the xfce compositing manager with an unsupported card?  It just looks so crappy without it, with windows leaving trails everywhere they are dragged.

And how do I know if I have the best drivers set up for my card?

---

### Post by simianstyle on 2006-06-07
Haha, awesome - this even works on my old Riva TNT2 Nvidia card. Granted its insanely slow and the windows don't move smoothly, but it's nice to know that it possible!

---

### Post by galileon on 2006-06-09
SORRY, I just found the answer in this same thread, one page behind.....now i feel stupid....
hello all,
I'm running dapper on a pentium d 3ghz with an nvidia 6500,

the xcompmgr thing works great, and i even showed it to my friend who's testing vista - but one thing i omited to mention (and hoping to solve) was this: when I click on the button at the top right to log off, it just hangs my x server so i have to ctrl-alt-backspace into tty1 and kill xorg...i know it says we need newest driver and cards, but can anyone tell me if my card is too "old" or if my driver is old (8762)?? 

cheers,

Galileon.

---

### Post by galileon on 2006-06-09
but its slowing down my 3ddesktop now, any idea if it can be resolved?

i mean instead of a fluid 3ddesktop switch, it just throws the screen very abruptly ...

thanks.

---

### Post by Neo Ex on 2006-06-13
Hi. I have an ATI Radeon 9600XT graphic card. If I use the fglrx driver I can't get the Composite Manager working properly: instead of transparency and dropshadows, the background become grey and there are many artifacts.
How can I make it working? Theese instructions are for ATI Radeon 9200 or lower and for Breezy, not for Dapper.
Thanks

---

### Post by JcZndeR on 2006-07-03
this is awesome!!
worked perfectly 4 me after i played wit it a little bit..
altho my gdesklets look a little funny with the shadows :neutral: ; is there anyway to disable it 4 specific apps??
and also is there a way 2 make all windows semi-transparent at once (like with a script) on key-combination or by running a shell?
i can't do it of course...;)  not much of a programmer except html
it would b an interesting alternative 2 the normal "show desktop",<ctrl><alt>d
thx..

once again
good howto poofyhairguy

---

### Post by cowley on 2006-07-06
hi, is there any screenshots of this in action with transparent window borders etc?

simon

---

### Post by cajunaggie on 2006-07-16
I am confuse by the first part. There is already a section called "Device" in my conf file. Do I edit that one to exactly match the one posted? Or do I need to add an aditional section?

---

### Post by jannol on 2006-07-16
You edit your current section to look like that in the howto.

---

### Post by cajunaggie on 2006-07-16
> **jannol said:**
> You edit your current section to look like that in the howto.

Hokay, so, I edited it to match that section word for word. Restart and bam! no graphics. But after a quick restore with a live CD, I return to normal.

I have an ATI 9200SE, not an nVidia (as far as I know). So what do I need to edit in that section to make it work correctly?

---

### Post by jannol on 2006-07-16
zorry if I was unclear

I guess your section

Section "Device"
	Identifier	"ATI"
	Driver		"fglrx"
	BusID		"PCI:1:0:0" 
EndSection

looks something like that

and you just need to add whats not in it so it becomes

Section "Device"
	Identifier	"ATI"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
    	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
EndSection

so this line

Option 		"AllowGLXWithComposite" "true"

is the only line you need to add into your device section but the renderaccel is also nice for increasing rendering.

---

### Post by Amatsu Mikaboshi on 2006-07-18
*skips thread*

Anyways I can get all the stuff done up until the part where you type in

sudo apt-get install xcompmgr transset

At that point I get this error....
[quote=Terminal Error]clay@clay-linux:~$ sudo apt-get install xcompmgr transset
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xcompmgr
clay@clay-linux:~$
[/quote]

What can I do to resolve this error? You will have to excuse me as I'm a complete newbie to Linux. 

Thank you.

---

### Post by szadek on 2006-08-02
> *terminal*
[b]root@szadek-laptop:/usr/bin# xcompmgr -fF -I-.002 -O-.003 -D6 -cC -t-5 -l-6 -r5
No composite extension
[/b]
This is what I'm recieving when following the how-to.  I've followed the instructions and have the file, I must be doing something wrong.  Any ideas?

---

### Post by szadek on 2006-08-02
> *terminal*
[b]root@szadek-laptop:/usr/bin# xcompmgr -fF -I-.002 -O-.003 -D6 -cC -t-5 -l-6 -r5
No composite extension
[/b]
This is what I'm recieving when following the how-to.  I've followed the instructions and have the file, I must be doing something wrong.  Any ideas?

BAH repost.  Sorry

---

### Post by patrick295767 on 2006-08-04
Hi, 

By chance... 

this thread matters only xorg, but for xfree86 ?? :-( :-( 
  
Would someone knows whether there is something similar to composite for xfree86 or if it can be done ?
  
because 
```
Section "Extensions"
        Option  "Composite" "Enable"
EndSection
```
doesnt work :-( 

thx

---

### Post by jdunn on 2006-08-29
This worked well for me except for one problem.

I'm using the latest version of Dapper Kubuntu and drivers for my NVIDIA Geforce FX.  I made the changes in my xorg.conf file and enabled transparency in Kcontrol.  Then I ran Unreal Tournament 2004 and ran into problems:

* The startup animated movie sequence in the game is slow.
* I run the game once in a session and have no problems.  If I run the game again in a given session, there is no sound for the game.

Is there a solution for this other than turning off transparency in Kcontrol before playing the game?  Are there run parameters in Kcontrol that will toggle transparency...so I can add it to Kmenu and do this automatically whenever I run UT2004?

BTW, I love the drop shadows.  They are damn sexy.

---

### Post by flipkick on 2006-08-30
It's too slow for me. NVIDIA Geforce4 MX ( Well quite old I know ).

I'd had to spend a lot of money to get really accerlerated working, while most of the effects are enabled. So, nice to know this, still _far_ slow.

I switched from ATI to NVIDIA and had no single problem while installing....

---

### Post by jdunn on 2006-08-30
Well here we are...1 1/2 years after the original post by Poofy Hair Guy.  I have to say that there are much fewer bugs than there were back then.  I can run the KDE desktop with awesome looking drop-shadows and transparency on Dapper flawlessly for days...provided I don't play full-screen OpenGL games like Enemy Territory or UT2004.

Sorry but among my other hobbies on the computer, I'm a gamer...so as awesome as the drop-shadows look, I had to ditch composite mode.  Its just not ready for prime-time, yet.  [-(

---

### Post by jdunn on 2006-08-31
I followed the composite manager "How To" written by PHG and used KDE's built in manager to try out transparency and dropshadows.  Then, I played ut2004 and enemy-territory fullscreen at 1024x768 (my desktop res is 1280x1024).  Since then, I've had wierd X problems which have persisted even after I disabled composite mode.  Here are the problems:

* Sometimes I have no sound on ut2004 or enemy-territory
* Every time I exit enemy-territory, my desktop resolution comes up as 1024x768
* When I end a KDE session and return to the login manager, the login manager screen is 1024x768

How do I fix these problems?  They don't seem to be in xorg.conf.

---

### Post by BLTicklemonster on 2006-09-05
Eeek, hey poof, if this ever gets stable (you scared me off with your disclaimer) let me know! :)

---

### Post by Flaringo on 2006-09-26
I get some problems:

After I add the stuff to my xorg.conf-file (the "composite" or something at the start) and restart X, I am unable to move any window or anything. :(

---

### Post by HeyGabe on 2006-11-06
Just a note to let you know that this worked great for me, with little fuss. Those am some right sexy dropshadows. Neat!

---

### Post by HeyGabe on 2006-11-08
And **Now,** Not so much. 
I tried to install the gcompmgr, and it seems to have hosed my Package Manager. Errormessage (E: The package for gcompmgr needs to be reinstalled, but I can't find an archive for it.)

Any tips on how to make this error go away? I don't care if I don't get gcompmgr working, so long as I can unbreak my package manger.

---

### Post by ajm2005 on 2006-11-11
:)

---

### Post by TomasRossi on 2006-11-12
For me, composite manager effects works fine by for some X hours, then it starts to slow down KDE. Disabling and re-enabling it helps for another X hours. So, it is yet a little buggy. 

Tom;

---

### Post by ultranoize on 2006-11-26
I'm using Xfce version 4.3.99.1 (Xfce 4.4 BETA2). I have modified my xorg.conf file enabling the composite extension and adding the options in the device section. I restart the computer and try to enable the composting but dont get the tab in the Window Manager Tweaks window.  Any suggestions? Am I missing something?

---

### Post by detyabozhye on 2006-11-27
Try this: [https://lists.ubuntu.com/archives/xubuntu-devel/2006-October/002243.html](https://lists.ubuntu.com/archives/xubuntu-devel/2006-October/002243.html)

---

### Post by ultranoize on 2006-11-28
Thanks, it did help though i still can't make it  work. I give up for now i'll try again in a couple of months.

---

### Post by macewan on 2006-12-03
Thanks for this howto. Works well under Edgy.

---

### Post by blackmh on 2006-12-03
Works great on Edgy, thanks

---

### Post by blackmh on 2006-12-04
Oh, it seems I have logout/shutdown bug. I'm using lastest nvidia drivers 9629...

---

### Post by ajm2005 on 2006-12-09
:)

---

### Post by ahren37 on 2007-02-27
As a newbie to Ubuntu I appreciate the simplicity of the instructions. Thx for the info and for a fun way to strengthen my skills! :)

---

### Post by FuturePilot on 2007-03-03
This is cool, but why does it mess up my video playback when I'm running it? I have to turn it off to watch a video without all this breakage.

---

### Post by Skrypt on 2007-07-10
Hm... I've got an nVidia card with the latest drives but I ran the xcompmgr commands provided and each time, the screen would blank leaving only the shadows. I could mouse over and partially reveal text and the terminal had a long string of errors. anyone have luck with this on Ubuntu 7.04 AMD64 Desktop with Feisty?

---

### Post by saratchandra on 2008-05-20
Worked like magic on my unsupported SIS card. Compiz doesn't work on my computer, thankfully this one does. Downloaded the gcompmgr-amd64 version and it works great with the default setting without slowing down my computer at all.

---


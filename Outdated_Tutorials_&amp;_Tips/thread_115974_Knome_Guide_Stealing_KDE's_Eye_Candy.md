---
title: "Knome Guide: Stealing KDE's Eye Candy"
date: 2006-01-11
forum: Outdated Tutorials &amp; Tips
---

### Post by poofyhairguy on 2006-01-11
Now that Xcompmgr has run its course, its time to move on the greener pastures. Those who use KDE full time already can use the compositor built into their favorite desktop environment to enjoy a whole bunch of pretty effects. Gnome, on the other hand, is just starting to get these ducks in line. If you are like me and you prefer the Gnome Environment, you will be happy to know that its possible to "upgrade" its native window manager to one that is more fun so you don't have to wait.

This guide is very similiar to my old Enlightened Gnome guide, except that it does not advocate using a window manager from the turn of the century (which is why I never updated the other guide for Breezy). I hope someone likes this.

Lets get started. First step is to edit your Xorg file. Best way is follow the first part of my older guide here:

[http://www.ubuntuforums.org/showthread.php?t=75527](http://www.ubuntuforums.org/showthread.php?t=75527)

If you are using an Nvidia card (recommended) I also will suggest getting the newest drivers. The ones in the repos are crashtastic. Use this guide here to do that:

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

Now on to the specific parts of my guide.

Now save everything you are doing and close all other programs cept the ones I talk about.

First put this command into the terminal:

```
sudo gedit /etc/apt/sources.list
```

Copy and paste this line in the bottom of the file that comes up:

```
deb http://kubuntu.org/packages/kde35 breezy main
```

Now save and close the file.

Now put this command into terminal:

```
sudo apt-get update
```

Now put this command into terminal:

```
sudo apt-get install kwin kwin-baghira kdeartwork-theme-window
```

Tell apt-get yes when it asks something.

When its done, put this command into terminal:

```
sudo cp /usr/share/gnome/default.session ~/.gnome2/session
```

Write that command on a piece of paper somewhere too.

Now put this command into terminal:

```
sudo gedit ~/.gnome2/session
```

Look for this line:

```
0,RestartCommand=gnome-wm --sm-client-id default0
```

Delete that line. Yes. Delete it. Now save and close the file.

Now go to your menu. 

"System" -> "Preferences" -> "Sessions"

Click on the last tab "Startup Programs"

Click "Add"

In the place for "Startup Command" put 

```
kwin
```

For the order, make it "10"

Now hit "alt" + "control" + "backspace"

Login and notice the difference!

Ok. Now its time to control this darn thing. Put this in the terminal:

```
kcontrol
```

Under "Desktop" and "Window Behavior" click the "Translucency" tab.

Click the checkbox to turn it on. Now play with the other settings as you wish. Apply and close when you are done.

To change the look of the window borders, right click on any title and choose the "Configure Window Behavior" option.

The first thing that pops up is "Window Decoration." Choose the one you want and the option you want and apply and close. I like "Smooth Blend" best.

There you have it- you are using a window manager that was meant to do neat tricks. I hope someone enjoys.

**Undoing what you did.**

This section is in case you do not like the result or it does not work for you.

Hit "alt" + "control" + "backspace"
Change the "Sessions" to "Failsafe Terminal" and log in.

Now enter into the terminal the command I said to write down:

```
sudo cp /usr/share/gnome/default.session ~/.gnome2/session
```

When its done, put in this command:

```
exit
```

Now change the "Sessions" to "Failsafe Gnome" and log in. 

"System" -> "Preferences" -> "Sessions"

Click on the last tab "Startup Programs"

Choose the one that says "kwin" and delete it. 

Reboot and welcome back to normal.

Ok. That is it for now. I hope you all enjoy!

---

### Post by poofyhairguy on 2006-01-11
Any person with more KDE experiance than me know how to turn off "Edge Flipping?" Its driving me nuts and I want to add it to the guide.

---

### Post by Norm 2782 on 2006-01-11
wow cool... gonna try this tomorrow on Dapper ^^ thanks :D

---

### Post by derrick1985 on 2006-01-11
Anyone have a screenshot so I can see this before I actually try it?

Thanks

---

### Post by Bloot on 2006-01-11
[QUOTE=derrick1985]Anyone have a screenshot so I can see this before I actually try it?

Thanks[/QUOTE]

Yes I'd like to see some pictures too. But what I'd like most is to know that all those ugly bugs are really gone.

---

### Post by poofyhairguy on 2006-01-11
[QUOTE=derrick1985]Anyone have a screenshot so I can see this before I actually try it?

Thanks[/QUOTE]

Sure. I posted one here:

[http://www.ubuntuforums.org/gallery/showimage.php?i=1734&original=1&c=2](http://www.ubuntuforums.org/gallery/showimage.php?i=1734&original=1&c=2)

I made the titlebar a LITTLE more translucent than what I would normally use to show the "Aero" effect. You can set it to what you want.

Really...this this has MANY options. It would take a while to go through them all.

---

### Post by poofyhairguy on 2006-01-11
[QUOTE=Bloot]But what I'd like most is to know that all those ugly bugs are really gone.[/QUOTE]

Bugs still exist. Its not perfect. It won't be for years.

What is gone (for me with the newest Nvidia drivers) are the REALLY bad bugs- aka the ones that crash X and take everything with them. Its usuable now...where before it was "something you turn on to play with and turn right back off afterwards).

Yet I will admit some display artifacts exist. Yet I noticed after using my sister's Powerbook all week that even the mighty OSX still has MANY composite artifacts, so if you hold out until its perfected then you won't get to play with this fun stuff for a Windows release life cycle (aka six or so years).

---

### Post by Bloot on 2006-01-11
[QUOTE=poofyhairguy]Bugs still exist. Its not perfect. It won't be for years.

What is gone (for me with the newest Nvidia drivers) are the REALLY bad bugs- aka the ones that crash X and take everything with them. Its usuable now...where before it was "something you turn on to play with and turn right back off afterwards).

Yet I will admit some display artifacts exist. Yet I noticed after using my sister's Powerbook all week that even the mighty OSX still has MANY composite artifacts, so if you hold out until its perfected then you won't get to play with this fun stuff for a Windows release life cycle (aka six or so years).[/QUOTE]

Yes I meant the bad bugs such as crashing X. Thanks, I'll take a chance on it surely.

---

### Post by poofyhairguy on 2006-01-11
[QUOTE=Bloot]Yes I meant the bad bugs such as crashing X. Thanks, I'll take a chance on it surely.[/QUOTE]

There is one bug left that I find will crash X.

Don't drag playing video files under the Gnome panel. Even visualizations.

Thats it.

---

### Post by benplaut on 2006-01-11
by edge flipping, do you mean virtual desktops going 1, 2, 3, 4, 1, 2, ... i hate it, too. one of the only reasons i don't use kde...

---

### Post by poofyhairguy on 2006-01-11
[QUOTE=benplaut]by edge flipping, do you mean virtual desktops going 1, 2, 3, 4, 1, 2, ... i hate it, too. one of the only reasons i don't use kde...[/QUOTE]

Yep. I dislike it as well....wish I could turn it off...

---

### Post by benplaut on 2006-01-11
[QUOTE=poofyhairguy]Yep. I dislike it as well....wish I could turn it off...[/QUOTE]

worst thing ever invented! also, metacity is pretty much the only WM that doesn't do it :(

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-01-12
First off, nice guide!
Thanks a lot.

Some comments though:
I think there is an easier way to make kwin the default gnome window manager:
a. Open a terminal
b. Remove metacity from your gnome-session:
```
gnome-session-remove metacity
```
c. Start kwin:
```
kwin &
```
d. Save your new session:
```
gnome-session-save
```
Now log out and log back in and kwin should be your window manager.

I also don't understand, why you start kcontrol as root, that is, with gksudo kcontrol. There is no need for it as you just want to control how kwin behaves for your user, or am I missing something?

Also, there's one problem that seems quite trivial, but that I'm unable to solve. I'd like to have a run dialogue when I press Alt+F2. Now obviously, the gnome run dialogue doesn't work and I don't know how it is called anyway, so that I have no way to make a custom shortcut. And the kde run dialogue isn't installed and I can't figure out what package provides it. Any clues?

---

### Post by Iandefor on 2006-01-12
You never stop, do you, Poofy :)?

I'll probably give this a try sometime soon, but for now, I'm happy without compositing.

---

### Post by Azriphale on 2006-01-12
I'll have a look at what provides it, and how to do keyboard shortcuts when i get home later. I installed all of kde3.5 to have a look at it, so it may be easier for me to find.

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-01-12
[QUOTE=Azriphale]I'll have a look at what provides it, and how to do keyboard shortcuts when i get home later. I installed all of kde3.5 to have a look at it, so it may be easier for me to find.[/QUOTE]
Thanks. :D

---

### Post by woedend on 2006-01-12
poofy great writeup, everything went great but it kinda borked on me in dapper.  Maximized windows had their title bar hidden by the gnome top panel, and the tope panel wasn't at the top, there was about a half inch of space above it that behaved like a tiny second desktop.  But I did get a general feel for it and I think i'll stick with broken xcompmgr...gnome impresses me far more than kde windows.

---

### Post by Azriphale on 2006-01-12
I thought that it would probably be better to use the gnome run dialog than the kde one that you suggested.

After doing a bit of research on the gnome run dialog, it seems that a little while ago the "gnome-run" binary disappeard and the dialog was integrated into the gnome panel.

This means that without metacity you cannot directly assign Alt+F2 to open the  gnome run dialog.

This may sound like bad news, but 
A) The KDE "run command" dialog is, I believe, integrated into kdesktop so you don't want to use that (may as well start using KDE, which I guess you don't want to do)
B) I have come across a simple solution. I am not sure how well it will work for you, but try it and let me know. When I get home I'll give it a shot too.

The solution requires that you compile a simple C app that talks to the Gnome panel and asks it to start the run dialog. So first you need to do this:
```

apt-get install build-essential libx11-dev 

```
It may ask you to install some other dependencies, just answer yes.

a file called gnome-run.c.txt is attached to this post. Download it, and rename it to gnome-run.c

In the console, run this command to compile it:
```

gcc gnome-run.c -o gnome-run -L/usr/X11R6/lib -lX11

```

I'm not completely certain thet the -L flag to that is correct, tho.
Try to execute that and see if it works (just type "./gnome-run" in the console where you compiled it). If it does, create a new launcher on your desktop, and make it run that file (you'll need the full path here) to see if it works when not running in the console. If it doen't work, then I'll need to see what can be done later.


Oh, and in kcontrol, is there nothing anywhere in there to set keybindings?

Try looking here:
[http://docs.kde.org/development/en/kdebase/userguide/keys-for-scripts.html](http://docs.kde.org/development/en/kdebase/userguide/keys-for-scripts.html)
and here:
[http://docs.kde.org/development/en/kdebase/userguide/adding-extra-keys.html](http://docs.kde.org/development/en/kdebase/userguide/adding-extra-keys.html)

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-01-12
First off, thank you Azriphale. Great explanations of what is going on.
You are right I think, the kde run dialogue is integrated into kdesktop and if I understand it correctly, it uses some dcop call to start it, which didn't work for me with gnome. 

Thanks also for all your efforts with the gnome-run dialogue. I was aware that the menu entry for it had gone, but I didn't know that even the excecutable was gone.

I have however found an other workaround. While I'm now happily mixing Gnome and KDE anyway, I figured why not throw xfce into the mix? So now I installed xfce4-utils, which contains xfrun4 (may be a bit of an overkill, as there are also other run dialogues out there, but it works for me) and assigned a custom shortcut to it. And what can I say, I have a working run dialogue again.

Thanks again for all your efforts, greatly appreciated. :D

---

### Post by Azriphale on 2006-01-12
Sure, its not trouble. Glad you got something that works tho. I'm going to need to do something like this later anyway, if I continue to use kwin.

---

### Post by manicka on 2006-01-12
I had to import a key to use the kubuntu/kde3.5 repo

```
 wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
 sudo apt-key add kubuntu-packages-jriddell-key.gpg
```

---

### Post by adam.tropics on 2006-01-12
Thought I'd try it on a Toshiba laptop (ATI.....yes, I know! ) and didn't expect alot, which is good since the transparency didn't work. Not the end of the world, and to be fair, taking the transparency away, this is mighty mighty quick!! All in all, pretty impressive.

---

### Post by limit223 on 2006-01-12
[QUOTE=benplaut]by edge flipping, do you mean virtual desktops going 1, 2, 3, 4, 1, 2, ... i hate it, too. one of the only reasons i don't use kde...[/QUOTE]

That's the easiest part in KDE to get rid of them:
kcontrol
Desktop-MultipleDesktops-Number of Desktops:change it from 4 to 1 ...that's it!

I was looking in Gnome what means flipping edge ...anyway ...to understand exactly what was meant by it...:)

---

### Post by abrainlessdude on 2006-01-12
it looks like a nice thing, thanks man. I will try it.

---

### Post by chadwick359 on 2006-01-12
Hm, if i hadn't decided a while ago to swticth to KDE, i would totally try this. And, i admit, there are still things I likde better about Gnome. (resource use, a few of the panel applets) I was sucked in by The speed of KDE 3.5, the well integrated compositing, and my most used app ever, Katapult.

As always Phg, great howto.

---

### Post by Thirsteh on 2006-01-12
Screenshots! We want screenshots!

---

### Post by sethmahoney on 2006-01-12
Anyone know if its possible to make *just* the title bar translucent, but *only* for active windows, and have inactive windows and windows being dragged fully translucent?  KDE's configuration controls have always seemed confusing to me, but the only option I can seem to find is to make all windows fully translucent or to make all windows have only the title bar translucent.

---

### Post by makisupa123 on 2006-01-12
Can someone help me out here?

What types of eye candy are we talking about here?  I see the translucent title bars but i'm interested in drop shadows.  Anyone have any reports on stability?

And yes, we need more screenshots (kinda like cowbell).

Thanks for your work Poofy!

Mak.

---

### Post by fannymites on 2006-01-12
[QUOTE=sethmahoney]Anyone know if its possible to make *just* the title bar translucent, but *only* for active windows, and have inactive windows and windows being dragged fully translucent?  KDE's configuration controls have always seemed confusing to me, but the only option I can seem to find is to make all windows fully translucent or to make all windows have only the title bar translucent.[/QUOTE]
All of this is possible, as long as you are using kde 3.5.

For those wanting some secreenshots, there are some in this neowin thread, this page and the next one (mine's at the top of this page)
[http://www.neowin.net/forum/index.php?showtopic=414710&st=30](http://www.neowin.net/forum/index.php?showtopic=414710&st=30)

---

### Post by daedalusman on 2006-01-12
[QUOTE=poofyhairguy]Any person with more KDE experiance than me know how to turn off "Edge Flipping?" Its driving me nuts and I want to add it to the guide.[/QUOTE]


Don't know if this has been answered yet but here is how you can fix this. When in the configure dialog go to the advance tab and under the "active desktop borders" section you can set how you want the desktop borders to act. I personally like the "only when moving windows" option but you can disable it all together as well as set the delay time between the change. If any of this is confusing let me know.

---

### Post by sethmahoney on 2006-01-12
[QUOTE=fannymites]All of this is possible, as long as you are using kde 3.5.[/QUOTE]

Yeah, I've got KDE 3.5 working, but in the configuration dialog all I see is an option to either make transparency affect the whole window or only the title bar, for all windows.  What I'm hoping to find is a way to make only the titlebar transparent for the active window, and the entire window transparent for all inactive windows and windows being moved, or better yet to make those windows fully transparent, with an even more transparent titlebar.

---

### Post by sethmahoney on 2006-01-12
Oh, another question, too: I'm guessing the answer is no, but I don't suppose there is a way to make the titlebar transparent, but not make the titlebar text transparent (it gets hard to read at higher transparency levels!)?

---

### Post by poofyhairguy on 2006-01-12
[QUOTE=daedalusman]Don't know if this has been answered yet but here is how you can fix this. When in the configure dialog go to the advance tab and under the "active desktop borders" section you can set how you want the desktop borders to act. I personally like the "only when moving windows" option but you can disable it all together as well as set the delay time between the change. If any of this is confusing let me know.[/QUOTE]

Thanks a million.

---

### Post by poofyhairguy on 2006-01-12
[QUOTE=makisupa123]Can someone help me out here?

What types of eye candy are we talking about here?  I see the translucent title bars but i'm interested in drop shadows.  Anyone have any reports on stability?

And yes, we need more screenshots (kinda like cowbell).

Thanks for your work Poofy!

Mak.[/QUOTE]

Basically every type of cool translucency is availible with this trick. Drop shadows, fading, translucent titlebars, translucent windows, and many different combinations of each.

Its "will not crash my xserver" stable with the newest Nvidia drivers (the repo ones crash hard for me)....I can't comment on non-Nvidia cards.

And no problem.

---

### Post by benplaut on 2006-01-12
[QUOTE=daedalusman]Don't know if this has been answered yet but here is how you can fix this. When in the configure dialog go to the advance tab and under the "active desktop borders" section you can set how you want the desktop borders to act. I personally like the "only when moving windows" option but you can disable it all together as well as set the delay time between the change. If any of this is confusing let me know.[/QUOTE]

you may have just convinced me to use KDE

---

### Post by todavies on 2006-01-13
I've got this working fine, but it seems pretty slow.

---

### Post by benplaut on 2006-01-13
[QUOTE=todavies]I've got this working fine, but it seems pretty slow.[/QUOTE]

yes... it's running most gnome libs and most KDE libs... i'd expect it to be a bit sluggish, unfortunately...

---

### Post by poofyhairguy on 2006-01-13
[QUOTE=todavies]I've got this working fine, but it seems pretty slow.[/QUOTE]

Do you have an Nvidia card? Did you use my other guide to set it up right?

If the answer is no to either its slow because its not being accerated by your graphics card.

---

### Post by limit223 on 2006-01-13
[QUOTE=poofyhairguy]Any person with more KDE experiance than me know how to turn off "Edge Flipping?" Its driving me nuts and I want to add it to the guide.[/QUOTE]

Originally Posted by daedalusman
Don't know if this has been answered yet but here is how you can fix this. When in the configure dialog go to the advance tab and under the "active desktop borders" section you can set how you want the desktop borders to act. I personally like the "only when moving windows" option but you can disable it all together as well as set the delay time between the change. If any of this is confusing let me know.


This option is disabled by default in KDE...I really don't get what was annoying?

---

### Post by tronica on 2006-01-13
i got this working fine, and looks great. however i'm unable to install window decos, i'm not sure what to do? i'm stuck with plastik. can someone help me. Thanks

---

### Post by kennyhow on 2006-01-13
I have two issues

when I do the following:

```
sudo apt-get update
```

I get the following response.  It does the update to all the other respositories and then displays this:

```
Fetched 59.6kB in 7s (7907B/s)
Reading package lists... Done
W: GPG error: http://kubuntu.org breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: You may want to run apt-get update to correct these problems

```

Also, when I run xcompmgr with commands from the Vista-ish thread...I get the following:

```
xcompmgr -fF & killall gnome-panel
No composite extension
[1] 27290
[1]   Exit 1                  xcompmgr -fF

```

---

### Post by drizek on 2006-01-13
goto kubuntu.org and find the kde 3.5 announcement. the key will be there.

---

### Post by kennyhow on 2006-01-13
Ok, that worked for the kubuntu url thing.

---

### Post by Jeff250 on 2006-01-14
Another great guide!  I've got gnome and kwin playing nice together in every way but one regard:  KDE apps such as Amarok and Kopete don't put their icon in the gnome tray.  I presume that they're trying to in the KDE one, which doesn't exist on my desktop.  Gnome apps like RhythmBox work properly.

---

### Post by scpike on 2006-01-14
does anyone know if this will work with an ATI X600 card?

---

### Post by Rob2687 on 2006-01-14
Is anyone else having problems installing window decorations?
Whenever I try to configure make, I get errors. Although the ones that do install correctly only partially work. By that I mean none of the options for the theme work. i.e. The colour, window title, etc. can't be set.

---

### Post by limit223 on 2006-01-14
[QUOTE=scpike]does anyone know if this will work with an ATI X600 card?[/QUOTE]
Composite enable in xorg won't work with ati - fgrlx driver. I have the same card and I achieve to have this just only with new EXA feature from X.org 6.9 in Dapper and lately with VESA driver form X.org. 6.8 in Breezy (poor 2D acceleration).
 ATI still don't provide a driver that have composite feature...a lot of time behind Nvidia development...:(

---

### Post by art on 2006-01-15
Well I can say transparency doesn't work on ATI mobility radeon 7000(even with changes to xorg.conf). Also a very annoying thing was it wouldn't let me type in the deskbar-applet area, and I have become so dependant on it, that I had to remove kwin. The window decorations changed fine though...

---

### Post by Rob2687 on 2006-01-15
[QUOTE=art]Well I can say transparency doesn't work on ATI mobility radeon 7000(even with changes to xorg.conf). Also a very annoying thing was it wouldn't let me type in the deskbar-applet area, and I have become so dependant on it, that I had to remove kwin. The window decorations changed fine though...[/QUOTE]

Worked on my laptop but the 7000 is ancient so it's uber slow. Slow beyond any usability.

---

### Post by limit223 on 2006-01-15
If you still want this eye-candy but you don't want to use composite there is a very simple option:

sudo apt-get install kwin-deko-crystal

then in Windows Decoration choose Crystal theme...the effect is similar!!

---

### Post by poofyhairguy on 2006-01-16
[QUOTE=tronica]i got this working fine, and looks great. however i'm unable to install window decos, i'm not sure what to do? i'm stuck with plastik. can someone help me. Thanks[/QUOTE]


I installed all I wanted from the repos....I did not look past this.

Kwin themes are FAR harder to install than Metacity ones. Its the main downside.

---

### Post by poofyhairguy on 2006-01-16
[QUOTE=limit223]If you still want this eye-candy but you don't want to use composite there is a very simple option:

sudo apt-get install kwin-deko-crystal

then in Windows Decoration choose Crystal theme...the effect is similar!![/QUOTE]

E16 can also do the same fake transparancy. In fact, thats Rasterman's invention.

---

### Post by poofyhairguy on 2006-01-16
[QUOTE=kennyhow]
Also, when I run xcompmgr with commands from the Vista-ish thread...I get the following:

```
xcompmgr -fF & killall gnome-panel
No composite extension
[1] 27290
[1]   Exit 1                  xcompmgr -fF

```[/QUOTE]

You have to do the first part of that guide. The part involving your xorg.conf.

---

### Post by andrewsawyer on 2006-01-16
Great How-To, however I'm having problems with transparency.

I get a message that loads when I get into X that states:

> The Compostie Manager crashed twice within a minute and is therefore disabled for this session.

Followed straight after by:

> Composite extension not found
You must use XOrg &#8805; 6.8 for translucency and shadows to work.
Additionally, you need to add a new section to your X config file:
Section "Extensions"
Option "Composite" "Enable"
EndSection

I am using Xorg 6.8.2-77, and when I try to put the mentioned section into my xorg.conf, the GUI fails to load at all.

My xorg.conf is shown below:

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	VendorName 	"Videocard vendor"
	BoardName 	"NVIDIA GeForce 6600 GT"
	Option		"ConnectedMonitor" "CRT, DFP"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	Modeline	"1280x768@60" 83.91 1280 1312 1624 1656 800 816 824 841
	Option		"TwinView" "true"
	Option		"TwinViewOrientation" "RightOf"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Option		"MetaModes" "1280x768,1280x1024;1280x1024,1280x1024;1280x768,1024x768;1280x768,NULL;1024x768,NULL;NULL,1280x1024"
		Option     	"SecondMonitorHorizSync"   "30-82"
    		Option     	"SecondMonitorVertRefresh" "56-76"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

Section "ServerFlags"
    Option      "Xinerama"      "false"
EndSection

# Section "Extensions"
#	Option		"Composite"	"Enable"
# EndSection

```

I have hashed out the offending item so I can load the GUI.  Please note that this is a twin display system, and is using an nVidia graphics card.

If anyone has any advice for me on how to get this working, it would be very much appreciated.

Andy

---

### Post by poofyhairguy on 2006-01-16
[QUOTE=andrewsawyer]

My xorg.conf is shown below:

Andy[/QUOTE]

Great you added that. The problem is the driver section lacks "renderaccel." Look here for more info:

[http://ubuntuforums.org/showthread.php?t=75527](http://ubuntuforums.org/showthread.php?t=75527)

---

### Post by andrewsawyer on 2006-01-16
Thank you Poofy.  That now works great.  Unfortunately my entire left screen (title bar et al.) and about 1/3 of my right screen (on the left side) messes up on boot.  Not sure why, however if I load an app and just expand it out over the 'error' it cleans it up.  The screen just kinda goes green and blocky - I'll have to do a screen grab I guess unless you have experienced it yourself in which case you would know what I was on about!

Anyway, I'll do it next time I reboot.

---

### Post by andrewsawyer on 2006-01-16
Just did a CTRL + ALT +Del

Image attached.

The pic on the left screen is stretched - this isn't an error due to this thread - it's because I have two monitors running in different resolutions.  One 16:9, the other 4:3.

Can I just ignore this and move stuff over it to clear it out of the way, or may this be damaging my monitor in some way?

Andy

---

### Post by benplaut on 2006-01-16
[QUOTE=daedalusman]Don't know if this has been answered yet but here is how you can fix this. When in the configure dialog go to the advance tab and under the "active desktop borders" section you can set how you want the desktop borders to act. I personally like the "only when moving windows" option but you can disable it all together as well as set the delay time between the change. If any of this is confusing let me know.[/QUOTE]

arrrgggg... that's not it :(

---

### Post by lysis on 2006-01-16
the tranlucency is NOT changing my window borders and titles.  what gives?

---

### Post by Jeff250 on 2006-01-17
I had to reboot before any of the effects started to work.  After that, they were applied correctly in realtime.

---

### Post by tzy on 2006-01-17
hello

wonderful tweak, but I have a little problem with my firefox 1.0.7. I have attached a screenshot so you can see my problem.
maybe someone with the same problem?

I have a 6800GT, a pentium 3.2 HT, and 1G RAM but the performance is a to bad to work properly. But it was great to try it out. I have turned all of the eye candy on. Is there a way or settings to make it run better? without losing to muth eye candy?

thx and grtz

---

### Post by andrewsawyer on 2006-01-17
Can anyone else confrm that Xorg is now hogging CPU usage?  I've had my computer going all night (screensaver: blank), and now this morning, Xorg status is Running, with 229.2MiB Virtual Memory and 97% CPU.

Does anyone know how to fix this?

Andy

---

### Post by poofyhairguy on 2006-01-18
[QUOTE=tzy]hello

wonderful tweak, but I have a little problem with my firefox 1.0.7. I have attached a screenshot so you can see my problem.
maybe someone with the same problem?[/QUOTE]

I don't have that problem, but I have other visual artifacts. 

Visual artifacts cannot be avoided....they will exist for at least two years...so its either ignore them or lose the effects.

Even OSX has a few of those.

> 
I have a 6800GT, a pentium 3.2 HT, and 1G RAM but the performance is a to bad to work properly. But it was great to try it out. I have turned all of the eye candy on. Is there a way or settings to make it run better? without losing to muth eye candy?


You MUST install the new Nvidia drivers. And fancy up your Xorg.conf like I tell how in the other guide linked to in the first post.

---

### Post by poofyhairguy on 2006-01-18
[QUOTE=andrewsawyer]Can anyone else confrm that Xorg is now hogging CPU usage?  I've had my computer going all night (screensaver: blank), and now this morning, Xorg status is Running, with 229.2MiB Virtual Memory and 97% CPU.

Does anyone know how to fix this?

Andy[/QUOTE]

Be sure to use renderaccel.

---

### Post by poofyhairguy on 2006-01-18
Ok....this guide is VERY stable for me. I have a few visual artifacts, but no major crashing for a while.

This means there is no reason to use Xcompmgr ever again. Say goodbye to our old friend....time to step into 2006.

---

### Post by chadwick359 on 2006-01-18
Now, please don't flame the bejeezus out of me here, but I have to ask, at this point, isn't it almost getting to the point where it makes more sense to use Kde? Using kwin's compositor was a great idea, PHG, and I agree that each manager has it's strengths, but what is keeping you guys from becoming Kubuntu users? I stuck with Gnome for years as I watched the eyecandy available to Kde users grow, and have just recently switched full time. I found myself looking back and wondering why I had stuck with gnome for so long. Just some musings, I would like to hear your thoughts.

---

### Post by poofyhairguy on 2006-01-18
[QUOTE=chadwick359]Now, please don't flame the bejeezus out of me here, but I have to ask, at this point, isn't it almost getting to the point where it makes more sense to use Kde? Using kwin's compositor was a great idea, PHG, and I agree that each manager has it's strengths, but what is keeping you guys from becoming Kubuntu users? I stuck with Gnome for years as I watched the eyecandy available to Kde users grow, and have just recently switched full time. I found myself looking back and wondering why I had stuck with gnome for so long. Just some musings, I would like to hear your thoughts.[/QUOTE]

Here is why I prefer this over a full switch to KDE:

1. I like Gnome Applications more. Firefox. Gaim. Nautilus. Gimp. etc. I hate for them to look like crap in KDE. Running gnome-settings-daemon in KDE would do the trick, but they do not play well together always.

2. I dislike the kicker (KDE panel). I prefer the Gnome panels.

3. I like for Naultilus to draw my desktop. I prefer Gnome's automounting. 

4. The Industrial theme is better than any KDE theme I have tried. In fact...I have never found a KDE theme I like (compared to GTK themes- even Clearlooks is better). Plus its easier to install themes in Gnome.

5. Ubuntu is the primary distro of all the buntu's so it gets the most work done on it.

I just want KDE's window manager, so I took it. Now there is no need to switch to KDE for me and others. Its the best of both worlds.

---

### Post by chadwick359 on 2006-01-19
Hm, makes sense to me.

1. In 3.5, I have no problem with the look and feel of Gtk apps, I did have to swtich the 'Use my KDE style in GTK applications' option on and off, but afterwords, all was fine

2. Cool, it is possible to make kicker look and act like the gnome-panels, and as a matter of fact, I used to do this.

3. Totally got me there, Gnome's automounting is superior.

4. Industrial never actually did that much for me, and i find myself enchanted by things like scrolling pogress bars and user tweakable styles for those who don't know how to code.

5. Hm, again, you got me. Especialy in the art department, I have though that Kubuntu has been getting the short end of the stick.

---

### Post by andrewsawyer on 2006-01-19
[QUOTE=poofyhairguy]Be sure to use renderaccel.[/QUOTE]

I am.  Still no joy :-(  I'm sure it's something that I've forgotten, or maybe it doesn't mix well with twinview or something.

Here is my xorg.conf:

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	VendorName 	"Videocard vendor"
	BoardName 	"NVIDIA GeForce 6600 GT"
	Option		"ConnectedMonitor" "CRT, DFP"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true" 
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	Modeline	"1440x900@65" 83.91 1280 1312 1624 1656 800 816 824 841
	Option		"TwinView" "true"
	Option		"TwinViewOrientation" "RightOf"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Option		"MetaModes" "1440x900,1280x1024;1280x1024,1280x1024;1280x768,1024x768;1280x768,NULL;1024x768,NULL;NULL,1280x1024"
		Option     	"SecondMonitorHorizSync"   "30-82"
    		Option     	"SecondMonitorVertRefresh" "56-76"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

Section "ServerFlags"
    Option      "Xinerama"      "false"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

If you can see anything that is missing (or anything I don't need), please let me know.

Andy

---

### Post by poofyhairguy on 2006-01-19
[QUOTE=chadwick359]Hm, makes sense to me.

1. In 3.5, I have no problem with the look and feel of Gtk apps, I did have to swtich the 'Use my KDE style in GTK applications' option on and off, but afterwords, all was fine
[/QUOTE]

That works if you want everything to have a KDE look.  Not my style.

With that said, each to their own. This guide is proof of the power of free software.

---

### Post by RAOF on 2006-01-20
Does anyone else have the problem where (sometimes) the upper gnome-panel is displaced from the top of the screen & sits over the top of maximized window titlebars?

Changing the startup order for kwin to 45 seems to make it sometimes work, sometimes not.  Anyone seen this before, or even better, fixed this before?

This is in Dapper, so maybe something's different in more recent KDE/Gnome stuff.

---

### Post by poofyhairguy on 2006-01-20
[QUOTE=RAOF]Does anyone else have the problem where (sometimes) the upper gnome-panel is displaced from the top of the screen & sits over the top of maximized window titlebars?
[/QUOTE]

Kill the gnome panel to fix that:

killall gnome-panel

It will replace itself with a sane version!

---

### Post by Tryke on 2006-01-20
I'm really liking this so far, there's just a couple things nagging me...

First off, I can't seem to get the session changes to stick. When I re-load Xorg after ctrl+alt+bksp, I have to start kwin manually with a terminal. I didn't notice any "save" button or anything in the session dialog, so I assumed my changes would save automatically?

The other one bothering me is that Nautilus now only draws it's icons on Desktop 1. Anybody else get this? Any idea how to fix it?

p.s. If I'm thinking of the same thing you are when you say "edge flipping", open kcontrol and go to Desktop -> Window Behavior. Go to the "Advanced" tab and disable "Active Desktop Borders". This will let you mouse to the edge of the screen without changing desktops.

I forgot how kwin will actually let me close maximized windows by clicking in the very top corner of the screen, like in Windows. Something I wish metacity did.

---

### Post by scrillamaan on 2006-01-20
[QUOTE=Tryke]The other one bothering me is that Nautilus now only draws it's icons on Desktop 1. Anybody else get this? Any idea how to fix it?[/QUOTE]

I'm having the same problem and a solution would be nice, but I'm trying not to let it bother me too much because this is great otherwise. I've had a couple X lockups, but I'm still trying to pinpoint the problem and this is really cool.

---

### Post by abrainlessdude on 2006-01-21
I just got around to trying this. Omfg i fell in love :P 

great guide man. Thanks.

---

### Post by poofyhairguy on 2006-01-21
[QUOTE=Tryke]
The other one bothering me is that Nautilus now only draws it's icons on Desktop 1. Anybody else get this? Any idea how to fix it?
[/QUOTE]

I noticed this. I guess thats the big side effect.

---

### Post by RAOF on 2006-01-24
[QUOTE=poofyhairguy]Kill the gnome panel to fix that:

killall gnome-panel

It will replace itself with a sane version![/QUOTE]
Hmmm.  It doesn't fix it, but it does manage to crash many of the panel applets :(

I suppose this might be the price of running the unstable/testing version ;)

---

### Post by poofyhairguy on 2006-01-27
New Screenshot of Gnome Panel Transparancy

---

### Post by poofyhairguy on 2006-01-30
I talk all about this guide in my blog entry:

[http://linuxeyecandy.blogspot.com/](http://linuxeyecandy.blogspot.com/)


Screenshots included.

---

### Post by potrick on 2006-01-30
Poofy, I can't believe how well this works. I'm really happy, I think this may actually look better than my roommates iMac.

---

### Post by poofyhairguy on 2006-01-30
[QUOTE=potrick]Poofy, I can't believe how well this works. I'm really happy, I think this may actually look better than my roommates iMac.[/QUOTE]

I'm glad you are happy. That is the whole point.

---

### Post by RaptorRaider on 2006-01-30
[QUOTE=poofyhairguy]I talk all about this guide in my blog entry:

[http://linuxeyecandy.blogspot.com/](http://linuxeyecandy.blogspot.com/)


Screenshots included.[/QUOTE]
You should change the links in your signature.

This project is definitely looking nice. Hope to try this one day when ATI releases decent drivers.

For me though, "the whole point" would probably be to just show off to Windows fanboys.

---

### Post by poofyhairguy on 2006-01-30
[QUOTE=RaptorRaider]You should change the links in your signature.[/QUOTE]

Done.

> 
This project is definitely looking nice. Hope to try this one day when ATI releases decent drivers.

Yeah...many can't wait for that day.

> 
For me though, "the whole point" would probably be to just show off to Windows fanboys.

Thats what 3ddesktop is for.....

---

### Post by veritas366 on 2006-01-31
Well, it LOOKS great, but I'm having issues (which I accidentally posted in the xcomp thread, so ignore that.)  Here's a cut and past of what I wrote:

sorry if this has been answered. I like the way things look...but too much weirdness. I haven't read all of this thread...please point if I need to see something already posted.

First, the window behavior isn't working quite right...often, when a window is opened in front of another window, only the top left corner shows until I actually move the window. clicking on it wont' work. This happens a vast majority of the time. I thought it was the shadows..but turning them off didn't help.

It's too annoying to keep...but I love how things look. Suggestions?

Second, I've run into this with other themes I've downloaded that go beyond simply changing window borders etc. At the moment, it seems kcontrol is what set my Firefox colors. The main window decorations are fine and in keeping with the them I chose with kcontrol. However, somehow I changed the color of certain areas (don't know what they are called) to a lavender color I'd like to change. For example, right now, my sidepanels have this background color, as does the place where i enter the title above this post. However, the background of the box I currently type in is the normal cream color.

I tried changing colors within the firefox preferences, but choosing "use system colors" or use my colors seems not to change things at all. Something is overriding it. Changing colorschemes manually in kcontrol (very cool) also doesn't affect anything but the window itself.

I like the dark blue theme in kcontrol but it doesn't carry over. I don't mind if firefox doesn't match....but I'd like to dump the lavender background of the sidepanels and certain text boxes.

So...weird partial windows popping up and unwanted lavender tones. Thanks for the guide overall...and if anyone can help with these odd bits...I'd be grateful.

 

	
(Second post)

Investigating further...I see that it is the transparency effect that's doing it. I turned off everything else...but only after I unchecked transparency did the partial windows appearances stop. You've seen the kind of thing before...even just passing the cursor over the "invisible" parts will make some of it appear.

I did download the most recent nvidia drivers...and enabled compositing, etc...I think I followed all the directions correctly. And all the compositing effects WORK...it's just that the windows don't materialize fully when I open a new program. I'd love to make this work...so any help would be nice.

And finally, booting today I got a black screen of death!  Lots of error messages ending with a "kernel panic".  Booting again made the bad things go away, but could it be related?  I sure hope not.  It happened to be time for the 30 boot file system check so I'm hoping it was just something funky with that.

Anyway, I'd love for the transparency to work.  I have a gforce4 which is only 64 meg.  Maybe that's the problem?

---

### Post by Jedeye on 2006-02-01
Nice guide, it was very easy to follow, and almost worked perfectly... I am having a slight problem with my windows when I maximize them they are going behind the top gnome panel(but not the bottom one) They are snaping to it, so it seems they detect it. I have included a screen shot to just show the problem.

You can also see in the screenshot that the background runs up beyond the gnome panel... on my screen I dont see that, but there is a black bar running on the bottom of my monitor... just dead space.

Thanks for the guide I really like the shadows, and will certainly stick with it I can work out this one bug!

---

### Post by RAOF on 2006-02-02
[QUOTE=Jedeye]Nice guide, it was very easy to follow, and almost worked perfectly... I am having a slight problem with my windows when I maximize them they are going behind the top gnome panel(but not the bottom one) They are snaping to it, so it seems they detect it. I have included a screen shot to just show the problem.

You can also see in the screenshot that the background runs up beyond the gnome panel... on my screen I dont see that, but there is a black bar running on the bottom of my monitor... just dead space.

Thanks for the guide I really like the shadows, and will certainly stick with it I can work out this one bug![/QUOTE]
That's exactly what was happening for me.  killall gnome-panel didn't fix it.  I fiddled around with the start-order of kwin (it's on 45 at the moment), and that didn't seem to fix it.  But it's now working  - I'm running Dapper, and there have been some kwin updates, so I think that might be it.

---

### Post by poofyhairguy on 2006-02-02
[QUOTE=Jedeye]Nice guide, it was very easy to follow, and almost worked perfectly... I am having a slight problem with my windows when I maximize them they are going behind the top gnome panel(but not the bottom one) They are snaping to it, so it seems they detect it. I have included a screen shot to just show the problem.
[/QUOTE]

Same thing happens to me so you are correct about the effect. Yet I have been taking advantage of it- I drag my windows underneith the translucent gnome panel just to see the effect. If it bugs you then turn up the snapping settings a little so that its harder to push the windows under the panel.

---

### Post by andrewsawyer on 2006-02-02
[QUOTE=Jedeye]Nice guide, it was very easy to follow, and almost worked perfectly... I am having a slight problem with my windows when I maximize them they are going behind the top gnome panel(but not the bottom one) They are snaping to it, so it seems they detect it. I have included a screen shot to just show the problem.

You can also see in the screenshot that the background runs up beyond the gnome panel... on my screen I dont see that, but there is a black bar running on the bottom of my monitor... just dead space.

Thanks for the guide I really like the shadows, and will certainly stick with it I can work out this one bug![/QUOTE]

Found the same thing on Dapper also.  It seemed to fix by deleting the panel (not just refreshing), and then adding a new one at the top and manually then adding the stuff that you want into it.

Let me know if this solves the problem on your machines.

---

### Post by poofyhairguy on 2006-02-02
[QUOTE=andrewsawyer]Found the same thing on Dapper also.  It seemed to fix by deleting the panel (not just refreshing), and then adding a new one at the top and manually then adding the stuff that you want into it.

Let me know if this solves the problem on your machines.[/QUOTE]

If one more person confirms that I'll stick it on the first page.

---

### Post by Jedeye on 2006-02-02
Well the last thing I did before I went to bed was turn the transparency off... but I kept the drop shadows. When I started up this morning no problems. Thanks again for the guide :)

---

### Post by Jedeye on 2006-02-02
I was able to recreat the effect by messing with the theme boarders, so I tried andrewsawyer sugestion and it did the trick.

Thanks guys!

---

### Post by Jedeye on 2006-02-02
Ok... one more solution. This is based off of andrewsawyer idea, but instead of deleating and adding it back, try right clicking on it, properties, then change its orientation to bottom. Then set it back to the top.

Let me know if this helps any of you.

---

### Post by andrewsawyer on 2006-02-02
[QUOTE=Jedeye]Ok... one more solution. This is based off of andrewsawyer idea, but instead of deleating and adding it back, try right clicking on it, properties, then change its orientation to bottom. Then set it back to the top.

Let me know if this helps any of you.[/QUOTE]

I can confirm this also works - probably easier too!  I just run with one bar anyway being the reason I went the 'long-way-around'.

Andy

---

### Post by Maelgwyn on 2006-02-02
I tried this out - thanks so much phg!

Unfortunately, it kwin didn't run so well on my 866Mhz comp, so I've ended up going back to Metacity..

Are there any other **light** wm's that I could use instead of Metacity?

---

### Post by mstlyevil on 2006-02-02
Works great! There are a few bugs and annoyances but overall it runs beautifull. One thing that happens to me is when I am running transparancies if I try to log out or reboot using the gui the whole desktop freezes. Then when I hit CTRL-ALT- Backspace the x server does not like to start back up so I have to hit the reboot button on my tower to get x to start up. The other annoyance I found is that when you choose to show hidden files as soon as you close the window and reopen it those files are hidden again. According to system monitor I am not having a problem with excessive CPU or memory usage so my graphics card seems to be doing it's job. I would love to see how a Athlon X2 processor handles this.

A few annoyances are worth the eye candy.

---

### Post by poofyhairguy on 2006-02-02
[QUOTE=Maelgwyn]

Are there any other **light** wm's that I could use instead of Metacity?[/QUOTE]


[http://ubuntuforums.org/showthread.php?t=88393](http://ubuntuforums.org/showthread.php?t=88393)

[http://ubuntuforums.org/showthread.php?t=75471](http://ubuntuforums.org/showthread.php?t=75471)

---

### Post by darkmatter on 2006-02-02
[QUOTE=mstlyevil]Works great! There are a few bugs and annoyances but overall it runs beautifull. One thing that happens to me is when I am running transparancies if I try to log out or reboot using the gui the whole desktop freezes. Then when I hit CTRL-ALT- Backspace the x server does not like to start back up so I have to hit the reboot button on my tower to get x to start up. The other annoyance I found is that when you choose to show hidden files as soon as you close the window and reopen it those files are hidden again. According to system monitor I am not having a problem with excessive CPU or memory usage so my graphics card seems to be doing it's job. I would love to see how a Athlon X2 processor handles this.

A few annoyances are worth the eye candy.[/QUOTE]

The desktop doesn't actually freeze... the dialog is just rendered transparent... likely because it doesn't register as top level with the composite manager.

If you click on the desktop in the area... you can hear the 'click'... its just you need to remember the position of the dialog elements... or shut off compositing before logout

---

### Post by poofyhairguy on 2006-02-02
[QUOTE=mstlyevil]Works great! There are a few bugs and annoyances but overall it runs beautifull. One thing that happens to me is when I am running transparancies if I try to log out or reboot using the gui the whole desktop freezes. [/QUOTE]

Its not frozen. Hit the ESC key.


> 
I would love to see how a Athlon X2 processor handles this.

It does Ok, but a good Nvidia card is where the real solution lies.

[QUOTE]
A few annoyances are worth the eye candy.

True dat.

---

### Post by chanders on 2006-02-04
Great Guide!

One thing though... is there a way for kwin to avoid certain applications wrt shadows and transparency? 

I ask this because my gdesklets all have shadows now and it aint too pretty ;-)

thanks in advance
chanders

---

### Post by d3x7r0 on 2006-02-05
Ok everything's ok except for the fact that kopete and amarok don't place their tray icons in the gnome tray :-?

---

### Post by louis_nichols on 2006-02-09
well, it works quite nicely. the only thing I've noticed is that mouse cursors don't obey any rule. I mean, I can see the one set under gnome cursors over firefox and the ones set in kcontrol over... well... kcontrol and kde apps (I set the same one, so it's ok). But over window decorations and the empty desktop and gnome panel I only see the default "human" theme. doesn't that happen to anyone else? is there  a workaround?

---

### Post by louis_nichols on 2006-02-09
aaaa.... strike that! things are kinda weird. what I wrote above happened for a while. then at one point I noticed the cursor was ok everywhere, without knowing why. Then I logged out and when I logged back in... the cursor is the one I set over some applications both from gnome and from kde (gaim-but only over the conversations window-not the buddy list, krusader, firefox).

So I guess themes are messed up somewhere, but I have no clue where or how to solve it.

---

### Post by escape on 2006-02-11
Wait... so how much faster does this run than xcompmgr? transset-df with xcompmgr makes windows so slow that it isn't even worth using (I have an ATI Mobility X300 = 64mb = not too much graphics power); is this worth installing over xcompmgr? Does anyone know about xgl, being released by Novell? Would that work better, since it's not rendering things through software?

---

### Post by mips on 2006-02-11
Nice one poofyhairguy !!!

If I didn't switch to KDE a short while back I would be using this guide.

I miss some things from Gnome but prefer KDE a bit more. Suppose it is a case of the lesser of two evils for me :twisted:

---

### Post by veritas366 on 2006-02-11
With a better video card it was working for awhile but then went back to weirdness.  For example, a couple of times I tried to close a window and parts of it stayed on the desktop.  You can make them go away by passing the mouse over them but it's just bits and pieces.  A couple more times only a partial window would appear, the top left corner.  It's all the shadows and transparency stuff that does it...but that's the stuff I wanted!

I may go back to the beginning and start over or try one of the other ways people are doing it.  I really liked the looks this had but it is too unreliable on my system.  I can't figure why sometimes it works and sometimes it doesn't.

---

### Post by Jormundgand on 2006-02-14
EDIT: To force Nautilus to display icons on all desktops, you have to add application-specific settings. Rightclick a window titlebar, click "Configure Window Behaviour", "Window-Specific Settings", "New", "Detect", click on an icon on the desktop, go to "Preferences" and check the option with the choice box labelled "Desktop 1". Change that to "Force" and "All Desktops", then "Apply" and close. You might need to restart kwin.

---

### Post by fannymites on 2006-02-14
Doesn't anyone else have problems with shadow offsets when using kompmgr?
If I set the shadows equal around the windows then the inactive window shadows are affset to the right and if I change the settings so that the inactive shadows are equal then the active shadows are offset to the left.
Also, kwin just won't save my shadow settings.
I've been fighting this for weeks.

---

### Post by Clark Nova on 2006-02-14
Well, I followed these instructions to the letter and installed kcontrol ok but when I check the translucency box nothing happens at all. Is this because I have an ATI card (9800 pro) ?

Thanks :)

---

### Post by fannymites on 2006-02-14
Ok, you may have already done this but did you restart X?

---

### Post by Clark Nova on 2006-02-14
[QUOTE=fannymites]Ok, you may have already done this but did you restart X?[/QUOTE]


I've got to be completely honest, I don't actually know how to do that. This is still my first week of using Linux and I'm still trying to get my head around it all. 

How do I restart X?:-k

---

### Post by poofyhairguy on 2006-02-14
[QUOTE=Jormundgand]EDIT: To force Nautilus to display icons on all desktops, you have to add application-specific settings. Rightclick a window titlebar, click "Configure Window Behaviour", "Window-Specific Settings", "New", "Detect", click on an icon on the desktop, go to "Preferences" and check the option with the choice box labelled "Desktop 1". Change that to "Force" and "All Desktops", then "Apply" and close. You might need to restart kwin.[/QUOTE]

Can I add that to the main guide?

---

### Post by poofyhairguy on 2006-02-14
[QUOTE=veritas366]With a better video card it was working for awhile but then went back to weirdness.  For example, a couple of times I tried to close a window and parts of it stayed on the desktop.  You can make them go away by passing the mouse over them but it's just bits and pieces.  A couple more times only a partial window would appear, the top left corner.  It's all the shadows and transparency stuff that does it...but that's the stuff I wanted!

I may go back to the beginning and start over or try one of the other ways people are doing it.  I really liked the looks this had but it is too unreliable on my system.  I can't figure why sometimes it works and sometimes it doesn't.[/QUOTE]

Its a theme problems. Some Kwin themes do that . Others don't.

---

### Post by poofyhairguy on 2006-02-14
[QUOTE=SiBuntu]I've got to be completely honest, I don't actually know how to do that. This is still my first week of using Linux and I'm still trying to get my head around it all. 

How do I restart X?:-k[/QUOTE]

I'm going to be honest.  For ATI cards after the 9250 this sort of composite is not worth using honestly.

I can tell you from experaince it will work but it will eat 100% on a 2.6 GHZ CPU. Yes really. Without acceration (which the ATI drivers lack) its almost to slow to use.

If you have a dual core or something and still want to try, use my other guide to get it all set up:

[http://www.ubuntuforums.org/showthread.php?t=75527](http://www.ubuntuforums.org/showthread.php?t=75527)

Be careful though. I will say that some of this stuff MIGHT mess up your machine. Swapping window manager is an intermediate level task. 

I wish we had a way to say how hard a guide is on the forum. Maybe I need to make one.

Out of 5 stars (5 being the most difficult) this is a three.

---

### Post by fannymites on 2006-02-15
I like that idea.  I was reading a linux magazine when I fisrt started out which had something like "101 cool hacks" and each one had a difficulty rating (beginner, intermediate, expert) and following it gradually got me into more advanced stuff without outdong myself and getting into trouble.  Reckon it could be made into a rule for all howtos or something?

---

### Post by mstlyevil on 2006-02-16
Just to let every one know. Kwin works well with XFCE also. Poofy showed me the file to edit to execute it upon startup. I decided to share it with the rest of you who have XFCE installed on top of your Gnome install.

```
sudo gedit /etc/xdg/xfce4-session/xfce4-session.rc
```

Then make the file look like this.

```
[Failsafe Session]
Count=4
Client0_Command=kwin
Client0_PerScreen=False
Client1_Command=xfce4-panel
Client1_PerScreen=True
Client2_Command=xftaskbar4
Client2_PerScreen=True
Client3_Command=xfdesktop
Client3_PerScreen=False
```

Just a word of warning. If you installed XFCE on top of a Ubuntu server install this will not work. This only works when you install XFCE on top of your default Ubuntu install and only after you followed this guide to set up kwin in Gnome.

I want to thank poofy for letting me know how to try this out. He posted it here in this thread on XFCE.

[XFCE Rocks!]("http://www.ubuntuforums.org/showthread.php?t=120148&page=8")

---

### Post by Riggs on 2006-02-16
Question for poofyhairguy,

In your blog, you mention the clearlooks industrial theme.  I tried installing the controls for that.  It installed, but when I select it, it makes the controls look dull.  Nothing like what's in the screenshot...it says that I need to install the latest clearlooks engine and cairo...I have no clue on these...do you have a guide that explains to users how to install the latest clearlooks from CVS and how to install cairo?

[EDIT] - Nevermind.  It helps to search I guess.  But, I looked through this thread, and I don't know where to get more window decorations, or how to install them once I do get them.[/EDIT]

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=Riggs]  But, I looked through this thread, and I don't know where to get more window decorations, or how to install them once I do get them.[/QUOTE]

Thats my biggest problem with Kwin. I told everyone how to install every window decoration availible in synaptic. Beyond those, I have no clue how to install the ones off of KDE look.

Its sure not drag and drop like Gnome is.....

---

### Post by cetol on 2006-02-16
I may have missed it somewhere in the thread but when ever I boot I get a message that tells me my X needs to be v6.8 or greater. So for the stupid question of the day.... how do I upgrade X?

I looked through synaptic but couldnt find it?:-k

---

### Post by Gandalf on 2006-02-16
It worked for me too Thx, Arch with Xorg 7, Gnome 2.13...

but i hate the ugly shadow behind bmp... look at the below screenshot
[[img]http://wael.nasreddine.com/gallery/albums/userpics/10062/normal_Composing.png[/img]](http://wael.nasreddine.com/index.php?option=com_copperminevis&Itemid=24&place=displayimage&pos=-3)

is there a way to define "specific-window" option ?

---

### Post by andrewsawyer on 2006-02-16
[QUOTE=cetol]I may have missed it somewhere in the thread but when ever I boot I get a message that tells me my X needs to be v6.8 or greater. So for the stupid question of the day.... how do I upgrade X?

I looked through synaptic but couldnt find it?:-k[/QUOTE]
v6.8 should be available in the repos.  I know that Dapper is upto v7 now, so I can't see why Breezy wouldn't be able to get v6.8.

---

### Post by andrewsawyer on 2006-02-16
[QUOTE=Gandalf]It worked for me too Thx, Arch with Xorg 7, Gnome 2.13...

but i hate the ugly shadow behind bmp... look at the below screenshot
[[img]http://wael.nasreddine.com/gallery/albums/userpics/10062/normal_Composing.png[/img]](http://wael.nasreddine.com/index.php?option=com_copperminevis&Itemid=24&place=displayimage&pos=-3)

is there a way to define "specific-window" option ?[/QUOTE]
Clicking on the image to see a bigger screenshot gives the message:
> You are not authorized to view this resource.
You need to login.

---

### Post by Gandalf on 2006-02-16
yes i knew about that right after i posted the pic i just installed the gallery, anyway it has been fixed, thx :)

---

### Post by Jormundgand on 2006-02-19
Has anyone else had trouble with key combos no longer working after switching Kwin for Metacity? How do I fix this?

---

### Post by poofyhairguy on 2006-02-20
[QUOTE=Jormundgand]Has anyone else had trouble with key combos no longer working after switching Kwin for Metacity? How do I fix this?[/QUOTE]


Early in the thread there is a fix for the ALT-F2 combo.

---

### Post by Jormundgand on 2006-02-20
I couldn't find anything which helped - I installed kcontrol and poked about with that and couldn't get Print Screen to work.

---

### Post by Ubuntuud on 2006-02-20
When I run "sudo kcontrol" I get the following mesage:

Could not find mime type
application/octet-stream

And it isn't working with gdesklets, it makes a window of them. Should I try Superkaramba?

---

### Post by poofyhairguy on 2006-02-21
[QUOTE=Ubuntuud]Should I try Superkaramba?[/QUOTE]

Yes. And right click on any window title bar to get a shot at the settings.

---

### Post by souled on 2006-02-23
The icon for amaroK doesn't show up for me either. Is there any fix for this?

---

### Post by Dargo on 2006-02-23
Hi,

Thanks for the info, my desktop now looks great! 

The only problem that I have is probably one that's associated with the nvidia drivers, but I thought I'd ask anyway and see if somebody has some insight.

With shadowing and translucency enabled, and only when they're enabled pressing the shutdown applet (by default it's the one that looks like a door on the upper right taskbar) crashes my system.  I have no other problems like this elsewhere that I've discovered, and it also doesn't happen without effects enabled.  

Has anybody seen anything like this before?

 Thanks.

---

### Post by m.musashi on 2006-02-23
[QUOTE=andrewsawyer]Clicking on the image to see a bigger screenshot gives the message:[/QUOTE]
Cool desktop. What is the icon theme? The trash can is really cool.

---

### Post by souteneur3190 on 2006-02-25
After I install do this tutorial I cant change the window border in gonome themes, any idea how i can get it back?

---

### Post by poofyhairguy on 2006-02-25
[QUOTE=souteneur3190]After I install do this tutorial I cant change the window border in gonome themes, any idea how i can get it back?[/QUOTE]

This guide changes Gnome's window manager. That means the GUI tool to change window border themes no longer will work.

The only way to "get it back" is to use my directions to undue the guide. You have to pick- its one or the other.

When it comes to eye candy, you ALWAYS have to make sacrifices.

---

### Post by Haegin on 2006-03-05
I doubt it hasnt been solved by now but to turn off edge flipping:

1. right click the titlebar and select configure window behaviour
2. Select advanced on the right
3. Disable active desktop borders

ya done!

---

### Post by poofyhairguy on 2006-03-06
[QUOTE=Human Prototype]I doubt it hasnt been solved by now but to turn off edge flipping:

1. right click the titlebar and select configure window behaviour
2. Select advanced on the right
3. Disable active desktop borders

ya done![/QUOTE]

thanks.

---

### Post by sYs^ on 2006-03-28
Hi, nice howto , I'm just going to try it, but before _the action_, does it support borderless windows? because I have problems with them on metacity. Thanks

---

### Post by Skarjoko on 2006-03-28
Help!

I followed the guide and installed everything, but decided to take it away since I didn't like it that much, and uninstalled it. But I have a problem now....my Fn key on my laptop is not functioning properly. All the keys, by default, do their secondary action, rather than their primary, so I have to keep pressing Fn to make it normal. 

Whats wrong.... :(

EDIT: My borders are gone! I can't close or do anything now, and the themes in preferences do nothing!

---

### Post by domino on 2006-04-02
Thanks for the tut. Is it possible to accomplish this and Composite Manager on a 9800Pro card?

---

### Post by poofyhairguy on 2006-04-02
[QUOTE=domino]Thanks for the tut. Is it possible to accomplish this and Composite Manager on a 9800Pro card?[/QUOTE]

 I don't think the fglrx drivers support this....

---

### Post by Pjukern on 2006-04-30
I followed this guide, and my desktop is really nice now.
Is there a way to make it faster?
I have a P4 3,2 ghz cpu. And 2gigs of RAM.
It is really laggy when i open new windows, i can see it slowly fades in, and out when i close them.

My display adapter is the motherboards standard. Intel graphics 810i. It is not the best, but do you think this is why its laggy?

---

### Post by jazzgossen on 2006-05-12
[QUOTE=darkmatter]The desktop doesn't actually freeze... the dialog is just rendered transparent... likely because it doesn't register as top level with the composite manager.

If you click on the desktop in the area... you can hear the 'click'... its just you need to remember the position of the dialog elements... or shut off compositing before logout[/QUOTE]
Is there no better way of doing this? Manually shutting off transparency before logging off is a bit of a pain. Is that what all of you who are using kwin are doing?

---

### Post by jazzgossen on 2006-05-12
Well, I guess learning the keyboard shortcuts (Alt+L to logout, etc) works OK.

I just found another strange little thing when using kwin: the keyboard shortcuts to change desktops (workspaces). In gnome/metacity, its ctrl+alt+left/right, but when I use kwin under gnome, there seems to be no default keyboard shortcut available. I assigned ctrl+alt+left/right to "switch desktop left/right", but now when I press that key combination, I move *two* desktops at a time instead on one. 

Has anyone else noticed this?

Edit:
Sorrry, I fixed it. Assigning the keyboard shortcut to "Change to next/previous desktop" instead works as expected.

---

### Post by jazzgossen on 2006-05-18
Another problem with kwin:

"Auto-save session" doesn't work as it used to. I have installed kwin and done "kwin --replace", so now my WM is kwin each time I log in. Excellent. The problem is the placement of my saved windows. 

I have the "automatically save changes" ticked under Preferences/Sessions. Then, if I have for example three terminal windows open when I log out, they should start again on the same positions the next time I log in. But instead, they are stacked on top of each other in the upper left corner, and have their windows titles hidden under the upper gnome panel, so that I have to right click on the entry in the lower gnome panel and choose "move" there in order to move them.

I couldn't find any other posts about this in this thread. Does it work for the rest of you?

---

### Post by louis_nichols on 2006-05-18
[QUOTE=jazzgossen]Another problem with kwin:

"Auto-save session" doesn't work as it used to. I have installed kwin and done "kwin --replace", so now my WM is kwin each time I log in. Excellent. The problem is the placement of my saved windows. 

I have the "automatically save changes" ticked under Preferences/Sessions. Then, if I have for example three terminal windows open when I log out, they should start again on the same positions the next time I log in. But instead, they are stacked on top of each other in the upper left corner, and have their windows titles hidden under the upper gnome panel, so that I have to right click on the entry in the lower gnome panel and choose "move" there in order to move them.

I couldn't find any other posts about this in this thread. Does it work for the rest of you?[/QUOTE]

Kwin uses a diffrerent way to store settings, that's why they are not remembered. What you need to do is right click on the window border and select either advanced application settings or advanced window settings and configure there each app how you want it. It's quite versatile, actually. And works great. I used to make transparent terminals like that, configuring them to start without the window border and what not.

---

### Post by skyhopper88 on 2006-08-20
I really like these effects! Something odd has happened though. I do not want to use the KDE themes (window borders and controls) under Kcontrol, and I can no longer use the Ubuntu themer. I downloaded a KDE varient of the theme, but after I applied it, the theme did not change. Is there any way to give the theme control back to Ubuntu's default themer?

---

### Post by saracen on 2006-09-22
Does anyone know of a way to change themes for kwin without installing all that kde stuff?  The packages given by the OP want to pull down a ton of KDE stuff that I know I don't need.  I just want to be able to change away from the default theme.

On another note, why is metacity so damn slow compared to kwin?

---

### Post by 5ER on 2007-08-08
Why not just use kde?
It's better.

---

### Post by melenor on 2008-12-05
I was honestly just wondering if this thread would still be updated or if metacity has gained any of those effects. I have tried Kubuntu but i really like gnome better then KDE but i am looking for either a smoother metacity or to look for making tranpancey for background of windows, i have been told kwin could do this thanks

---


---
title: "Lost window bar on top of applications"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by jukingeo on 2008-07-12
Hello all,

I clicked on something wrong and I don't remember what, but when I open applications such as Firefox and Open Office, the top bar that allows you minimize, maximize, exit and resize the windows is gone.  The screen is open full at all times.  I have to go into File-Exit to get out.  This is a pain bacause I can't switch applications like this.

Anyone have an idea on how to get my window bars back?

EDIT:

Having the screen in this mode it also flashes when I hover the mouse over certain items.  I can't switch to Terminal either because the taskbar on the bottom is gone.  I have to completely exit out of Firefox or Open Office and then go into Terminal.

I did also try a reboot but it is doing the same thing.  It looks like it is trying run these applications maximized without taskbars, but I tried to back track to see what it is that I mis-clicked on, but I can't find anything.

I hope I can get this fixed soon because it is annoying.

EDIT:

Ok, I found a way to get Firefox operating again.  I went over to the little Ubuntu logo on the left next to the APPLICATIONS tab and RIGHT clicked on it.  I then clicked on Edit Menus and then the REVERT button on the bottom.  That got gave me my top window bar again.  However, Open Office is still doing it. So I am still going to need help there.



Thanx,

Geo

---

### Post by ugm6hr on 2008-07-12
I suspect your Window Manager (or Decorator) is misbehaving.

Do you use Compiz?

If so - easiest way I know is to install "fusion-icon" and use that to reload the window manager.

---

### Post by WinterMadness on 2008-07-12
> **jukingeo said:**
> Hello all,

I clicked on something wrong and I don't remember what, but when I open applications such as Firefox and Open Office, the top bar that allows you minimize, maximize, exit and resize the windows is gone.  The screen is open full at all times.  I have to go into File-Exit to get out.  This is a pain bacause I can't switch applications like this.

Anyone have an idea on how to get my window bars back?

EDIT:

Having the screen in this mode it also flashes when I hover the mouse over certain items.  I can't switch to Terminal either because the taskbar on the bottom is gone.  I have to completely exit out of Firefox or Open Office and then go into Terminal.

I did also try a reboot but it is doing the same thing.  It looks like it is trying run these applications maximized without taskbars, but I tried to back track to see what it is that I mis-clicked on, but I can't find anything.

I hope I can get this fixed soon because it is annoying.

EDIT:

Ok, I found a way to get Firefox operating again.  I went over to the little Ubuntu logo on the left next to the APPLICATIONS tab and RIGHT clicked on it.  I then clicked on Edit Menus and then the REVERT button on the bottom.  That got gave me my top window bar again.  However, Open Office is still doing it. So I am still going to need help there.



Thanx,

Geo



I think if you went to system>prefrences>emerald theme manager you could restore them.
Dont quote me on it, but thats the program people use to edit the title bars anyway, so if you click on one of them (or maybe your own) it should reset them.

---

### Post by nothingspecial on 2008-07-12
If you`ve installed compiz, make sure the windows decorator plugin is enabled.
system > preferences > advanced desktop settings -scroll down and you will see it.
If you have installed emerald, make sure you are using a theme -
system > preferences > emerald theme manager - double click on a theme.
If none of that works try opening a terminal and typing
```
metacity --replace 
```
If you still dont see windows borders goto system > preferences > appearence and click on a theme in there.

The beauty of ubuntu is that it`s totally customizable. Problem is, if you don`t know what you`ve done it`s hard to undo it. Do it myself at least once a fortnight.:)

---

### Post by LeoSolaris on 2008-07-12
I've had this problem intermittently with FF3 and 8.04, but never with Open Office...   I found that to get rid of it in FF3, all I have to do is go to the home folder, hit CTRL+h to unhide all of the hidden folders, then scroll down till I find .mozilla

In that file there is a folder called 'firefox', open it and it will have a few folders and a file called profiles.ini

Rename the profiles.ini folder to something like profiles.ini~ FF3 will automatically recreate the file and a new folder for it to point towards.

It will restore FF3 to defualt, which means no extentions and no bookmarks. You can import the bookmarks by opening the "organize bookmarks" and clicking on the "Import and backup" buttion. The last choice will let you choose a file, and you can navigate back to the old settings that the orginal profiles.ini pointed towards. In that randomly named folder, there is a folder called 'bookmarkbackups' Just pick the most recent.

To get rid of the effect in openoffice...    no idea...   this may be a windows virus attacking java, which FF3 and OO.o have in common, or adobe acrobat reader, if you use it in both...   always a possiblity. I have noticed that I do not get that wierd effect unless I visit some rather shade corners of the net.

Leo

---

### Post by jukingeo on 2008-07-12
> **ugm6hr said:**
> I suspect your Window Manager (or Decorator) is misbehaving.

Do you use Compiz?

If so - easiest way I know is to install "fusion-icon" and use that to reload the window manager.

Sorry no Compiz.

It was a wierd click of the mouse that did it.  At least I was aware of it when it happened to Firefox and as I said, I right clicked on that little Ubuntu logo on the taskbar and went into edit menus and clicked on the REVERT button.  That fixed Firefox, but now I don't know what to do with Open Office.  Incidentially in open office it is only happening on the word processor.  The other Open Office applications are OK

---

### Post by jukingeo on 2008-07-12
> **WinterMadness said:**
> I think if you went to system>prefrences>emerald theme manager you could restore them.
Dont quote me on it, but thats the program people use to edit the title bars anyway, so if you click on one of them (or maybe your own) it should reset them.

In SYSTEM==>PREFERENCES, there isn't an emerald theme manager listing.

---

### Post by jukingeo on 2008-07-12
> **nothingspecial said:**
> If you`ve installed compiz, make sure the windows decorator plugin is enabled.
system > preferences > advanced desktop settings -scroll down and you will see it.
If you have installed emerald, make sure you are using a theme -
system > preferences > emerald theme manager - double click on a theme.
If none of that works try opening a terminal and typing
```
metacity --replace 
```
If you still dont see windows borders goto system > preferences > appearence and click on a theme in there.

The beauty of ubuntu is that it`s totally customizable. Problem is, if you don`t know what you`ve done it`s hard to undo it. Do it myself at least once a fortnight.:)

Nope I don't have compiz and metacity --replace didn't work either.

As of now the problem seems to be isolated ONLY to Open Office Word Processor.  Another way to describe it (in MS Windows parlance) is that the word processor is opening on top of everything else in the fully maximized mode.  No taskbars are shown at all.  Apparently this weird mode Ubuntu doesn't like either because certain mouse movements cause the screen to flicker.  So because of THAT fact, I want it back the way it was.  With the taskbars, I don't get the flicker.

Geo

---

### Post by jukingeo on 2008-07-12
> **LeoSolaris said:**
> 

To get rid of the effect in openoffice...    no idea...   this may be a windows virus attacking java, which FF3 and OO.o have in common, or adobe acrobat reader, if you use it in both...   always a possiblity. I have noticed that I do not get that wierd effect unless I visit some rather shade corners of the net.

Leo

I did mention that it happened because of a weird click of the mouse.  I do admit my left mouse button is getting a bit twitchy lately.  I also did re-edit my first post and did fix the problem in Firefox...but the word processor I can't seem to fix.

My guess is that it has something to do with an "always on top" issue or something like that. But it is hard to fix when I can't see the properties because it launches that way all the time.

Anyway....Virus?  I thought that wasn't something you have to worry about here with Linux.  One of my reasons for switching from Windows.  No more viruses, no more spyware.

---

### Post by jukingeo on 2008-07-13
The problem in Firefox came back tonight, but this time the right click on the Ubuntu Icon===> Menu Edit ====> Revert didn't do anything.

Coincidentally this problem started happening when I updated the drivers on my Nvidia card to accept open GL.  Still I don't see why it would cause the menu bars to disappear.

I am beginning to think this is another Hardy bug.

I am VERY close to switching distributions because this version of Ubuntu is really really really bad.

EDIT:

Ok, I have a couple of things to add in regards to this problem.  I did what Leo said to do and it worked, but the problem is that in getting rid of the problem, I also got rid of all my settings and all my saved bookmarks and shortcuts.

So I did a bit of poking around.  I did notice that since I updated the video driver that the organbar goes pale and comes back again when I hover my mouse over it.  Another thing I noticed...and this is the biggie, if you hover your mouse over the bar for a while it automatically "unmaximized" the window and you are left with just a bar.  I never liked this feature.  But I also found out that if you are maximized and you grab the orange bar and PUSH UP on the mouse the bar disappears.

Since I don't like any of these extra "effects" I decided to turn them off.  Low and behold right within Preferences==>Appearance==>  There is a tab labeled "Visual Effects".  I opened it up and selected NONE.  So now hovering the mouse over the orange window bar has no effect on it....GOOD!

Next problem.  Open Office Word Processor.

While poking around in Preferences, I noticed a tab for Keyboard Shortcuts.  I looked through to see what the popular shortcuts were for minimizing and maximizing.  There were a few that interested me:

1) Activate Window Menu    Alt-Space
2) Toggle Full Screen      Disabled
3) Toggle Maximize State   Shift-Cntrl-Tab
4) Move Window             Alt-F7


Well there are a bunch of settings here, but the first one revealed something interesting with the Word processor.   Clicking the key combination DID reveal the window menu.  But here is the kicker, only minimize was able to be selected.  Unmaximize, Move, and Resize were all greyed out (disabled).

So I tried to add some key combinations to #2 & #3 above.  It worked for other windows but had NO effect on Word Processor.  The ALT-F7 Move option didn't work either.

So now comes the questions.

Why would these options be greyed out?  What am I missing here?

I am hoping someone could shed some light on what is happening.

I am going to poke around with the shortcuts some more, but I am a bit ticked that this problem happened in the first place.

The big problem is that I cant bounce back and forth between Word Processor or anything else, UNLESS I push it over to the other side of the expanded desktop (virtual screen 2 (right)).

Another thing I noticed is this.  Only on the Word Processor title bar menu I see the option "Move Titlebar Onscreen".

So Ubuntu KNOWS that the titlebar isn't there.  But clicking on the command will not produce the titlebar. 

So now I am wondering if Open Office Word Processor may have some "open in full screen" mode stuck on all the time.

Anyway this is as far as I got for tonight.

Geo

---

### Post by jukingeo on 2008-07-13
> **LeoSolaris said:**
> I've had this problem intermittently with FF3 and 8.04, but never with Open Office...   I found that to get rid of it in FF3, all I have to do is go to the home folder, hit CTRL+h to unhide all of the hidden folders, then scroll down till I find .mozilla

In that file there is a folder called 'firefox', open it and it will have a few folders and a file called profiles.ini

Rename the profiles.ini folder to something like profiles.ini~ FF3 will automatically recreate the file and a new folder for it to point towards.

It will restore FF3 to defualt, which means no extentions and no bookmarks. You can import the bookmarks by opening the "organize bookmarks" and clicking on the "Import and backup" buttion. The last choice will let you choose a file, and you can navigate back to the old settings that the orginal profiles.ini pointed towards. In that randomly named folder, there is a folder called 'bookmarkbackups' Just pick the most recent.

To get rid of the effect in openoffice...    no idea...   this may be a windows virus attacking java, which FF3 and OO.o have in common, or adobe acrobat reader, if you use it in both...   always a possiblity. I have noticed that I do not get that wierd effect unless I visit some rather shade corners of the net.

Leo

Hello Leo,

The problem happened to me again today.  I think it has something to do with the video driver and when you maximize certain screens.

One thing I noticed was that sometimes the top menu bar (the orange one where you minimize, maximize, etc...well, it looses it's color and takes the background color.  When hovering the mouse over it, it goes back the way it supposed to.

At any rate, I just wanted to let you know that I did try to delete the profile just as you said and it worked!

Unfortunately now with this finding, I am very worried about leaving my windows maximized...for in fear the same thing will happen again.  Another unfortunate thing is that because I deleted my profile, all my favorites and my settings are gone and I have to redo everything.  So that is a royal pain in the butt.

As for it happening in office, well, at the first time it happened to me with firefox, I had both firefox AND open office word processor opened and maximized.  It blew both settings off.

So you say that it happened to you several times?  Also you say that it happened only in Ubuntu 8.04?

In my last response here before I reread your suggestion I did say that I am seriously thinking about switching distributions.  While Ubuntu may be supported very well, it has been one problem after another with this version.

Geo

---

### Post by faintscrawl on 2008-10-26
> **jukingeo said:**
> Sorry no Compiz.

 Incidentially in open office it is only happening on the word processor.  The other Open Office applications are OK

I have the exact same problem.

---

### Post by ricky08 on 2008-10-26
OK guys, I think I've sussed a quick-fix, but NOT the reason why it happened in the first place: - 

Quick Fix: - 

System > Preferences > Keyboard Shortcuts

Scroll down to "Window Management" , then "Toggle Fullscreen Mode"

Click on the line to light-up the "new accelerator"

press F11 key (or one of your choice)

Now run ANY of the applications giving you problems, i.e. Open office Writer, spreadsheet, Firefox etc.

Pressing the F11 key once or twice will miraculously re-instate the windows bars you lost.

This was driving me batty, so I did a bit of poking around and came across these shortcuts. I've only been usung UBUNTU for around 3 days, and, like others, have pressed some key combination or other to mess things up. Not sure what, but this seems to fix it for me.

I suspect there must be a master setting somewhere which dictates how application windows are launched, but for now, this works a treat.

ps, I'm very much a noob, but enjoying the tinkering. Was a bit of a wizz with XP, but fancied a change - not sure if I chose the best distro for 1st attempt at Linux, but any suggestions are welcome.

Cheers - Ricky08

---

### Post by jukingeo on 2008-10-27
> **ricky08 said:**
> OK guys, I think I've sussed a quick-fix, but NOT the reason why it happened in the first place: - 

Quick Fix: - 

System > Preferences > Keyboard Shortcuts

Scroll down to "Window Management" , then "Toggle Fullscreen Mode"

Click on the line to light-up the "new accelerator"

press F11 key (or one of your choice)

Now run ANY of the applications giving you problems, i.e. Open office Writer, spreadsheet, Firefox etc.

Pressing the F11 key once or twice will miraculously re-instate the windows bars you lost.

This was driving me batty, so I did a bit of poking around and came across these shortcuts. I've only been usung UBUNTU for around 3 days, and, like others, have pressed some key combination or other to mess things up. Not sure what, but this seems to fix it for me.

I suspect there must be a master setting somewhere which dictates how application windows are launched, but for now, this works a treat.

ps, I'm very much a noob, but enjoying the tinkering. Was a bit of a wizz with XP, but fancied a change - not sure if I chose the best distro for 1st attempt at Linux, but any suggestions are welcome.

Cheers - Ricky08

Hello Ricky...

Thanx for the tidbit of info.  The same thing happened to me a while back. I accidentally pressed some weird key configuration and that is when it happened.  At first I blamed Open Office, but then it happened in Firefox.  There is a way to fix it in Firefox (outlined above), but I couldn't find a way to fix Open Office.  The Open Office people couldn't help me either...although they HAVE heard of the problem.

At any rate a few things happened in the interim and I ended up blasting Ubuntu off my hard drive and started over.  

What I did find out was the CAUSE of the problem and it is the "visual effects" in Ubuntu (in the appearances section).  This part of Ubuntu is VERY buggy and causes a lot of trouble, so I have to advise everyone that when you do a fresh install of Ubuntu...TURN VISUAL EFFECTS OFF!!!!! I can't stress that enough.  I have done that and God knows how many times I had weird key combos since then, but never again did I have the lost Window bar problem.  However, I will keep in mind what you wrote, just in case :).

Thanx,

Geo

---

### Post by robgr85 on 2008-10-27
Got similar problem on my kubuntu, and removing package called **xserver-xgl** bring my window bars back :)

I would suggest trying

```

sudo apt-get remove xserver-xgl

```

Cheers,

---

### Post by jukingeo on 2008-10-28
> **robgr85 said:**
> Got similar problem on my kubuntu, and removing package called **xserver-xgl** bring my window bars back :)

I would suggest trying

```

sudo apt-get remove xserver-xgl

```

Cheers,


Kubuntu is KDE, right?  I think the rules would be different there as compared to Gnome.  

I had a horrid time of trying to fix the problem in Open Office, but Firefox did have a quick fix.  At any rate, I found out what caused the problem and I conveniently had another major problem in Ubuntu (something with my video driver) and I just decided to blast the whole Ubuntu partition and start over.

Now that I have the "Visual Effects" turned off, I no longer have a problem with the window bars.

Geo

---

### Post by Neodudeman on 2008-12-08
I hate to rebump this thread, but I have a solution.

```

1. Go to System->Preferences->Appearance; Visual Effects. 
2. From the menu, select Extra.
3. Open OpenOffice Word Processor
4. Alt-ClickDrag to move the window down.
5. Re-maximize the window, and close.
6. In Visual Effects, select None.

And when you reload OpenOffice, it should be fine.

```

I installed the fusion-icon package as per one of the previous posts. The problem Is that OpenOffice is being fullscreened, and for some reason the shortcut key isn't undoing it. According to fusion-icon, this is the problem:

```

Window manager warning: Treating resize request of legacy application 0x3a00051 (Untitled1 ) as a fullscreen request

```

So aparently, OpenOffice word processor is asking for a resize request that metacity can't handle, so it just assumes that it's a fullscreen request. Well, as it turns out, I switch a lot between Extra Visual Effects and No Visual Effects; aka, switching between Compiz and Metacity. So, I thought "Maybe Compiz left a resize request attached to the window that Metacity can't interpret." So I switched back to Compiz, and lo-and-behold, when I attempted to Alt-ClickDrag the window to move it, I found the window bar higher than the screen! So what I did was drag it down, re-maximize it so it maximized properly Under the top bar, and closed Openoffice. I then switched back to No Effects, and my title bar was back! Yay!

---

### Post by brainac0cult on 2008-12-09
WARNING!!! before you do this let me just tell you if anything goes wrong just type in: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
___________________________________________________________________________
ok I believe I have had the same problem as you and this is how I fixed it:

1. press alt+f2 and type in:  gksudo gedit /etc/X11/xorg.conf 

and when your text editor comes up delete all the text you see and put this in this in:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Thu Jun  5 09:26:53 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "PHILIPS 107E"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce2 MX/MX 400"
    Option "AddARGBGLXVisuals" "True"
    Option "RenderAccel" "True"
    Option "AllowGLXWithComposite" "True"
    Option "backingstore" "True"
    Option "TripleBuffer" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1152x864 +0+0"
EndSection
```

---

### Post by jukingeo on 2008-12-09
Hello all,

I am surprised to see new activity here.  However, I will say that since this incident had happened to me, it was one of many things that went wrong with that Ubuntu installation.  I have since obliterated that partition and reinstalled with a fresh Ubuntu Studio distribution.

Of course the first thing I did was turn off the video effects and since then the problem with the window bar has not reared it's ugly head.

Neodude: It sounds like you came up with a solution.  I do follow the first part, but everything you wrote in that last paragraph went over my head like a supersonic jet at mach 2.  In fact I am still spinning in my office chair.  

One thing though.  Everyone talks about Compiz.  Isn't that a KDE thing?  I am using Gnome.

Brainac:  Nice little script you put together there.  I would download it for future use, but when I have written this post, I have since replaced my Nvidia 5200FX with an ATI 9600XT.  I needed more "stooch" for when I play RCT3 in Windows XP.   

The good news is that I have delegated Windows XP mostly for playing newer games or specific games that I cannot run/find a substitute for here in Ubuntu. 

I will say that initially I didn't have an easy time getting Ubuntu set up on my system.  Hardy had many problems back then.  However, after all the turmoil I been going through with Hardy, it is finally now somewhat stable.  I guess the massive updates that the developers have been working on for Hardy have been finally paying off.  Hardy now very rarely crashes.  Most of the programs that I download are from the repositories and they are proven stable versions and that is where I usually look for programs first (before going elsewhere).  I finally have a good sound card that works with Linux, I have Wine set up for some of my Windows programs I am trying to get to run in Linux.

Overall I really do hope that problem never shows up again.  But it does seem it was connected to the video effects and as I said, I have not been using them since I reinstalled with Ubuntu Studio.  Thankfully this problem hasn't showed up again.  Hopefully it stays that way.

Happy Holidays!

Geo

---

### Post by MonkeyPaw on 2008-12-09
Well, I had the same issue, but it was actually in Nautilus. It would always open maximized, but the title bar was gone. I'm running a 701 Eee, so it may not be all driver related. I didn't figure out a fix, as I was trying different distros and did a rebuild with Ubuntu-eee. No problems so far, but it certainly is/was an odd issue...

---

### Post by lojacc on 2008-12-10
New Linux convert, here. Running as far and fast from Microsoft as I can and so far I have just two comments:

1 - I have no argument (that can hold water) as to why i have not switched to Linux sooner! it's GREAT!!!
2- I can't remember one nasty thing I've heard about the OS that has been true. Probably because those are the same devotees that want me to keep paying for Windows

Anyway, back on subject. I am having the same issue with Ubuntu 8.10. I recently destroyed windows and installed Intrepid on a fresh partition, discovered Compiz Fusion, then discovered Emerald. I found a cool theme, but everytime i enable it [via the Emerald theme manager] the menu bars disappear as soon as i close the manager. I read about using "emerald --r" in the terminal and that seems to repair the issue....BUT only if i leave the terminal open. As soon as i close it, the menu bars disappear again.

I will try the above resolutions (as i am currently @ work) and see if that works. Hopefully I can report success and in turn help everyone else who is having this issue going forward.

Again, LOVE Linux so far. windows....what was i thinking....

---

### Post by jukingeo on 2008-12-10
> **MonkeyPaw said:**
> Well, I had the same issue, but it was actually in Nautilus. It would always open maximized, but the title bar was gone. I'm running a 701 Eee, so it may not be all driver related. I didn't figure out a fix, as I was trying different distros and did a rebuild with Ubuntu-eee. No problems so far, but it certainly is/was an odd issue...

Oh! Yes, I did notice that the problem "moved around" too.  I never happened to nautilus, but it did happen to Firefox and also Evolution. With Firefox I was able to fix it within Firefox.  Evolution required some more hoop jumping.  But I could NOT fix the problem with write.  As I said, at that point I had so many things going wrong with my Ubuntu installation and I decided to wipe it.  BUT, prior to that I did gain the knowledge about the video effects as being the culprit of the problem.  So when I reinstalled with Ubuntu Studio, I made sure the first thing I did was turn the video effects off.  Thusfar I have no problems.

What I would like to do though is permanently delete that stuff as I will never use it.  My goal for the use of any operating system is to streamline it.  I like enough features as for it to remain intuitive, but yet I like to keep it small and running as fast as possible.   Do I don't dump all these extra visual effects.

I was surprised that when I applied the streamlining info I learned when I began Ubuntu to Windows XP, you wouldn't believe how much faster XP runs now!  I just got rid of so much JUNK in XP.

I do intend to keep Windows for a long while because there are still many things I need to run over there that I can't run over here in Ubuntu (yet). I am learning how to use Wine, so that will be a big help.

Geo

---

### Post by jukingeo on 2008-12-10
> **lojacc said:**
> New Linux convert, here. Running as far and fast from Microsoft as I can and so far I have just two comments:

1 - I have no argument (that can hold water) as to why i have not switched to Linux sooner! it's GREAT!!!
2- I can't remember one nasty thing I've heard about the OS that has been true. Probably because those are the same devotees that want me to keep paying for Windows

On the surface and for a first impression, Linux does have a pretty good "Wow" factor.  But you will find that not everything is in butter.  Going behind the scenes is a little more complex and a whole different learning curve from what you know about Windows.  In the beginning I kept comparing Ubuntu to Windows and that is primarily because of what I saw on the surface.  But how everything else is structured "under the hood" is completely different.  For example, you probably have noticed by now Linux doesn't use drive letters.  It directly maps the drive to a path, which can be confusing because within a folder structure a drive will appear as a folder.  So what I did was give the folder an icon so I KNOW that it is a drive.  For example, in Windows XP, my second hard drive starts with the letter "D".  In Linux, this same drive I have labeled "File Storage".  I did it that way because I wanted to have direct access to this drive in both Windows AND Linux.

Another thing is the terminal.  That takes some getting used to as well.

You will find you will be going "behind the scenes" sooner than you think.
I remember when I first started with Linux, I right away had trouble with my sound card.  It took me a while to correct the situation, but I wizened up and decided to install an audio card that I knew was fully compliant with Linux.

So you have to watch things like that, not all hardware that is supported in Windows will be automatically supported (or recognized) in Linux.  You may have to do quite a bit of fudging around.

There definitely is a learning curve.

> Anyway, back on subject. I am having the same issue with Ubuntu 8.10. I recently destroyed windows and installed Intrepid on a fresh partition, discovered Compiz Fusion, then discovered Emerald.

 I found a cool theme, but everytime i enable it [via the Emerald theme manager] the menu bars disappear as soon as i close the manager. I read about using "emerald --r" in the terminal and that seems to repair the issue....BUT only if i leave the terminal open. As soon as i close it, the menu bars disappear again.

I hate to boist your bubble on using themes in Ubuntu, but I have been reading that Compiz IS a source of the problem.

> I will try the above resolutions (as i am currently @ work) and see if that works. Hopefully I can report success and in turn help everyone else who is having this issue going forward.

Again, LOVE Linux so far. windows....what was i thinking....

Get rid of Compiz and turn off video effects for starters.

Geo

---

### Post by hongleong on 2008-12-19
I'm using Compiz and had the same problem for OpenOffice. I noticed that in my config for System > Preferences > Appearance > Visual Effects, none of the 3 options was selected, which is weird because normally one of it is selected.

I did the following to fix my problem:

1. Selected "Extra" for "Visual Effects".

2. Opened OpenOffice Writer. It opened without the window title bar.

3. Goto menu : View > Full Screen. It changed to "Full Screen" mode and showed the "Full Screen" button.

4. Clicked on the "Full Screen" button and the window title bar appeared.

5. Restarted Writer. The window title bar did not disappear. :)

This fixed the problem but the Compiz "Desktop Cube", "Rotate Cube" and "Cube Caps" were disabled. I re-enabled them and so far so good.

I checked the config for System > Preferences > Appearance > Visual Effects, and again, none of the 3 options was selected. Looks like that's how it is when Compiz has been customised.

I checked OpenOffice Writer again. It is still showing the window title bar. So I guess the fix works.

---

### Post by zika on 2008-12-26
You might try a remedy binbash suggested in [http://ubuntuforums.org/showthread.php?t=986482&highlight=ff+window+top+disappear](http://ubuntuforums.org/showthread.php?t=986482&highlight=ff+window+top+disappear)
I did and (for now) it is working.

It looks like a permanent solution to the contrary to hitting F11 twice or similar (resizing window after unmaximizing it).

Thank You again binbash.

---

### Post by brainac0cult on 2009-01-29
im glad to be of help :))

---

### Post by DonaldJ on 2009-02-14
Happened to me too, just after a fresh install of U-810, and added 184        peripheral gnome add-ons... The top tool-bar with the header, the slash, the box, and X, is gone..  and I can't drag windows on the screen, only resize them...
I must go to Close in File to click a window off the screen...  It seems it happened after I installed a bunch of interesting Gnome items.. but no Emerald nor Compiz, just a lot of  Gnome stuff...  The top bar is gone for all windows... 
There's a setting for it somewhere, I hope..  But I just can't find it, and I thinks I've been through every preference in the system, but the one I can't find...  I thinks it's a conflict between extra softwares and the OS...

I see that the tool-bar icon that drops the windows from the desktop isn't in the tool-bar... Maybe that's where the glitch is..?

Also, when I click File>New, the pop-up closes...  

And Right-click is gone too..?

It looks like I must dump the install, and reinstall.. and this time not install so many strange Gnome extras..?

Maybe it's a just glitch in Ubuntu 810, and not in 804..?  Is there a way to prevent Ubuntu from updating to 810..?

Plus, after I finished installing everything in this new install, I downloaded the Ubuntu-810 image CD, to make updated copies in friends PC's in changing them over to Linux, but I can't find the download anywhere in the OS, to put to a CD..?   Um.. on second thought, I thinks I'm just gonna drop in the old 804 image CD, and reinstall...  This is all just too-big of a mess...

I'll wait a couple hours, and strive to repair it, to learn a little more about Ubuntu, then reinstall...

---

### Post by ugm6hr on 2009-02-14
> **DonaldJ said:**
> Maybe it's a just glitch in Ubuntu 810, and not in 804..?  Is there a way to prevent Ubuntu from updating to 810..?

Yes. It won't upgrade as default.

It will *offer* to upgrade when 10.04 comes out, but you don't even have to agree at that stage.

System -> Administration -> Software Sources
Updates tab
Release Upgrade - Show new distribution releases: pick whichever option you want.

---

### Post by DonaldJ on 2009-02-14
Update to this mess...  Solved...

Silly me! I installed "Gnome Apt Software Manager" unaware that it came with a serious Warning...   It sure does damage an Ubuntu OS...  I uninstalled "Gnome Apt Software Manager", and rebooted, and everything is back to normal...  oh yay...

---


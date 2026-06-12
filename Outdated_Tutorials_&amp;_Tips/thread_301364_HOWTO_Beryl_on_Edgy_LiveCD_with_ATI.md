---
title: "HOWTO: Beryl on Edgy LiveCD with ATI"
date: 2006-11-17
forum: Outdated Tutorials &amp; Tips
---

### Post by kvonb on 2006-11-17
Want to see if Beryl will work with your video card?  Want to make your friends/colleagues jealous?

=============================================================
** EDIT #01:**  Don't be scared at the length of these instructions, there is actually VERY little to do, it's just that I tend to explain every little detail and waffle on a bit :).
=============================================================
**  EDIT #02:** This should work with ANY video card as long as you have direct rendering working (see steps 01. and 02. below).  This howto is now fully up to date, I removed and re-installed Beryl using these instructions and all is working perfectly :mrgreen:.
=============================================================

Try this with the standard Edgy CD:

This works on my ATI9200se, it uses the standard opensource driver which actually works really well.  I'm running it now and Cedega works, 3d games like Wolfenstein and WolfET also work.

One cool side effect of doing this is that if you get your screen resolutions setup correctly in xorg.conf (monitor frequency and resolution settings etc'), if you then click on the "Install" icon, the installed version will have your resolutions setup and already working for you :).

Also if you copy all the downloaded .deb files from /var/cache/apt/archives (while still running the live CD, before rebooting) to (your fresh installed copy)/
var/cache/apt/archives/partial, they will be used when you re-do the Beryl install on your system, saving you from re-downloading them!

###################### **SECTION 1** ##############################

There should be no need to install any driver, try the following, the expected results are shown below the commands:

**[Step 1]** Boot the Ubuntu Edgy CD, open a terminal and copy and paste the following: (skip to Step2 if not using ATI)

```
glxinfo | grep vendor
```You should see something like:

```
 - libGL warning: 3D driver claims to not support visual 0x4b
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.
```[B]

[[/B]**Step ****2]** Type this in the same terminal:

```
glxinfo | grep "direct rendering"
```You should see something like:

```
 - libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
```..as long as you see  "direct rendering: Yes", you are in business :cool:.

** [****Step ****3]** Try the following, but they may crash your card, you can safely ignore this next section but it will improve performance.

```
sudo gedit /etc/X11/xorg.conf
```To the "Device" section add:

```
Option          "AGPMode"       "8"
        Option          "AccelMethod"   "EXA"
        Option          "ColorTiling"   "on"
```**!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!**
** WARNING!** The next parts are for my monitor only, Sony 21inch G500!
DO NOT USE THE FOLLOWING SETTINGS ON YOUR SCREEN, IT MAY DAMAGE IT!!!!!!!
If you want to know how high your screen will go, look in the manual that came with it,
or google the model.


To the "Monitor" section, comment out the original then add:

```
HorizSync    28.0 - 121.0
VertRefresh  43.0 - 160.0
```then to the front of each of the 'SubSection "Display"'s  lines add:

```
"1400x1050" 
```**!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!**

save and exit.

** [****Step ****4]** Logout, then log back again.  If unsuccessful, <ctrl> <alt> <backspace> to kill gdm, then switch to console1 <crtl> <alt> <F1> and simply type "startx".

###################### **SECTION 2** ##############################

(The next part is taken directly from [http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/AiGLX), you should always check there for updates before proceeding).


** [****Step ****5]** Add beryl to repos:

```
sudo gedit /etc/apt/sources.list
```add:

```
deb http://ubuntu.beryl-project.org edgy main
```[B]

[[/B]**Step ****6]** Import key:

```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```[B]

[[/B]**Step ****7]** Update repos:

```
sudo apt-get update
```**[****Step ****8]** Now download and install Berly stuff:

```
sudo aptitude install beryl
```**[****Step ****9]** Edit Xorg.conf, and add this: (THIS MAY BE FOR THE ATI CARD ONLY AND CAN BE SAFELY OMITTED)

```
sudo gedit /etc/X11/xorg.conf
```add this to the "Device" section:

```
     Option          "TripleBuffer" "true"
```** [****Step ****10]** On the menu go to System -> Preferences -> Sessions, select "Startup Programs" from the tabs along the top, click "Add" and type in: beryl-manager, save and close.

** [****Step ****11]** Now logout and log back in again (wait for it to autologin or type username "ubuntu" and press enter).  You should see the Beryl wobbly splash and once loaded you should get drop shadows on the desktop and strange effects on the menus!  If not, logout, press <ctrl> <alt> <F1>, (login as user "ubuntu" if it asks) and type: sudo /etc/init.d/gdm stop.  Now type "startx" and X should load with all the Beryl fab-ness!  If not, cry :D.

Regards, Kev :)

PS. Please let me know how you went and also if I made any typos.

---

### Post by finferflu on 2006-11-17
Well, I've already installed everything using howtos here and there, so thanks for your comprehensive howto!

---

### Post by fritzk3 on 2006-11-17
Let me get this straight:  will this work while exclusively running from the Live CD?  Or does this only work when you have installed Edgy to a partition on the hard drive?

I really like using Edgy on my laptop - but it's a company-owned laptop, so I can't go partitioning it and installing other OSes.

---

### Post by kvonb on 2006-11-17
```
fritzk3: 	Let me get this straight: will this work while exclusively running from the Live CD? Or does this only work when you have installed Edgy to a partition on the hard drive?
```

Yes it will run exclusively from the liveCD!

You DO NOT have to install anything to the hard disk, it will NOT touch your hard disk at all.

You will need an internet connection though (unless you can download all the needed packages beforehand and be able to copy them into /var/cache/apt/archives/partial once Edgy has loaded).  Sorry I can't remember what they were now, but I will try and find out if you need the names.

The other problem is that once you reboot/turn off it will be gone :(

Regards,  Kev :)

---

### Post by trogbot on 2006-11-17
Following your howto via livecd.  Added the repo to sources.list, but when trying to do sudo apt-get install ......., I get error stating:

"E: Couldn't find package beryl-core"

What's up with this?

Thanks for howto, everything worked so far, but can't get beryl to install.](*,)

---

### Post by kvonb on 2006-11-17
Maybe the repo is down, open a terminal and type this:

```
sudo gedit /etc/apt/sources.list
```

then at the end add:

```
 deb http://www.beerorkid.com/compiz edgy main-edgy
```

save and exit, then type:

```
 wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
``` (copy the whole string including the "-" on the end).

Now start again from item #7 in the instructions.

---

### Post by kvonb on 2006-11-17
Oh, and I figured out some cool things last night:

1) Press <ctrl> <alt> keys at the same time, hold them down and press the left mouse button.  Keep the button down and release the keys, you can now spin the cube by moving the mouse.

2) Hold the <alt> key down and move the mouse to a blank area of the screen and roll your mouse button down!  Roll up again to reverse.  EDIT: Also works on individual windows :).


3) <ctrl> <alt> any arrow key, will turn the cube.

---

### Post by pwk on 2006-11-18
Thanks. This worked well on my widescreen notebook with an ATI Mobility Radeon X300 (which has been giving me grief in Dapper for various reasons). I had no need to change any of the monitor sync settings for the LCD.

Now that's Edgy!

---

### Post by mikyor on 2006-11-18
I followed the instructions and everything worked out perfectly.  I am a little surprised it worked, since I have a IGP 320m

---

### Post by Anthem on 2006-11-19
> **mikyor said:**
> I followed the instructions and everything worked out perfectly.  I am a little surprised it worked, since I have a IGP 320m
Wait, really?  And it's responsive?

I've never gotten my 320m to work.

---

### Post by etrmedia on 2006-11-22
Pretty slick... now how about slipstreaming Beryl and the ATI drivers into a live cd?  :)

---

### Post by kvonb on 2006-11-22
> _etremedia:_
Pretty slick... now how about slipstreaming Beryl and the ATI drivers into a live cd?  :smile:
....my friend, if you know how to do that PLEASE let me know, I would be VERY interested in doing that :)

---

### Post by pwk on 2006-11-22
Is this of any use?


[https://lists.ubuntu.com/archives/ubuntu-devel/2006-November/022345.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-November/022345.html)
UCK is a tool that helps you customizing official Ubuntu Live CDs
(including Kubuntu/Xubuntu and Edubuntu) to your needs. You can add
any package to the live system, for example language packs, [B]or
applications[/B].

Please check the official announce here:
[http://sourceforge.net/forum/forum.php?forum_id=598852](http://sourceforge.net/forum/forum.php?forum_id=598852)
for further details and download links.

---

### Post by mrphd on 2006-11-25
Thanks for this. This is good. I got Beryl working on Edgy with my Radeon Mobility 9000.

I have two questions: first, is it normal that I get really ugly titlebar rescaling when I resize windows. I use a filled outline resize, but when I do resize I can see the text in the window titlebar being stretched first which looks really ugly (before drawing it normally).

Second, does anyone know if is it possible to get decent video playback under VLC whilst running Beryl? I have managed to get it running properly using mplayer, but so far I have had no luck with VLC.

Thanks!

---

### Post by pinworm on 2006-11-26
i got beryl installed, and aiglx is working.  but the beryl manager is unable to start the window manager.  im using xubuntu rather then ubuntu, but it shoudlnt be that much different?

this is what it says when you try to select the beryl window manager:

libGL warning: 3D driver claims to not support visual 0x4b
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: Another window manager is already running on screen: 0
beryl: No manageable screens found on display :0.0

any ideas?

---

### Post by kvonb on 2006-11-26
mrphd:

>  I have two questions: first, is it normal that I get really ugly titlebar rescaling when I resize windows. I use a filled outline resize, but when I do resize I can see the text in the window titlebar being stretched first which looks really ugly (before drawing it normally).


No, it's not normal, (well at least for me!) try changing the options in xorg.conf, especially the AGP speed.  Make sure you don't have 8x enabled!

>  Second, does anyone know if is it possible to get decent video playback under VLC whilst running Beryl? I have managed to get it running properly using mplayer, but so far I have had no luck with VLC.

Try changing the settings between opengl and X11 as in this screenshot:

[http://wamrfixit.homeip.net:8000/edgy/screenshots/snapshot24.png](http://wamrfixit.homeip.net:8000/edgy/screenshots/snapshot24.png)

===============================

pinworm:

> i got beryl installed, and aiglx is working. but the beryl manager is unable to start the window manager. im using xubuntu rather then ubuntu, but it shoudlnt be that much different?

this is what it says when you try to select the beryl window manager:

libGL warning: 3D driver claims to not support visual 0x4b
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: Another window manager is already running on screen: 0
beryl: No manageable screens found on display :0.0

any ideas?

It seems like a problem with the video driver, which one are you using?  How did you install it?

You might want to search the forum for "beryl nvidia".

Regards, Kev :)

---

### Post by pinworm on 2006-11-27
hey kev, im using the "ati" driver that comes with edgy.  im running a 9600 pro.  i dont think its  a driver problem because i can boot into xubuntu through safe terminal, then start up beryl-manager.  so i will have some effects on the terminal but no desktop environment.

---

### Post by kvonb on 2006-11-27
I have no idea, sorry :(.

The only thing I can think of is to make sure that you have direct rendering (as in the instructions above).

I'm no expert, I just managed to get it working on the liveCD so I thought I'd share it.

Check the beryl forums, I lost the bookmark unfortunately but google it.

Regards, Kev

---

### Post by jbus on 2006-12-13
This seems to work well with my Radeon 9800 pro. The only problem I notice on the live CD is that the video playback in totem doesn't seem to work well. The video plays but intermittently flashes between a black screen and the video. This is just the Live CD... I haven't installed anything other than beryl and I'm just playing the example ubuntu video. I didn't have this problem with XGL/Beryl Is there a way to fix this?

Edit: I fixed the issue with totem video playback by running gstreamer-properties and selecting &#8220;XWindow (NoXv)&#8221; as the default video playback. Now it works like a charm.

---

### Post by jbus on 2006-12-13
After installing to disk using this method I realized how slow AIGLX with the open source drivers is compared to XGL with the proprietary drivers. Also, windows with video can not wobble and tend to lag if you use AIGLX. While AIGLX/Beryl is slightly easier to set up, the speed XGL/Beryl offers is worth the extra couple of minutes it takes to set it up for Radeon users.

For those that want a live CD with 3d desktop, it should be possible to make a live CD that uses the proprietary ATI drivers and XGL/Beryl with Reconstructor [http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

---

### Post by kvonb on 2006-12-13
Hey jbus,

If you are going to use reconstructor to make a new liveCD, how about sharing it?  I would like a copy :mrgreen:.

Maybe I'll give it a go.

Which version of the drivers did you use?  For my 9200 the support stops at v8.28.8.

Could you let us know how you installed the drivers, it might help a lot of other people too.

Regards, Kev :)

---

### Post by trippinnik on 2006-12-14
What do you do if direct rendering is not turned on? I have a Radeon Mobility M6 LY in a Thinkpad X22, aka Mobility 9000.  I'd like to be using direct rendering even if I don't use Beryl.  Is it possible with this card?  Is it even worth trying Beryl?

---

### Post by kvonb on 2006-12-14
> **trippinnik said:**
> What do you do if direct rendering is not turned on? I have a Radeon Mobility M6 LY in a Thinkpad X22, aka Mobility 9000.  I'd like to be using direct rendering even if I don't use Beryl.  Is it possible with this card?  Is it even worth trying Beryl?

Go here:

[http://wiki.beryl-project.org/wiki/Install/Ubuntu](http://wiki.beryl-project.org/wiki/Install/Ubuntu)

Select the link "[Graphic Card Drivers]("http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/GCDrivers")" from either Dapper or Edgy (I don't know which one you are using), that will give you instructions.

But just be aware that support for older cards has been dropped by ATI in their "binary" drivers, you should check with [www.ati.com](www.ati.com) for info regarding your card and which version of the driver you can use.

As long as you try it on the liveCD first you won't mess up your system :mrgreen:.

Regards, Kev :)

---

### Post by trippinnik on 2006-12-14
My grfx card (Radeon Mobility 9000 or specifically Radeon Mobility M6 LY) is not supported by flgfx.  I can't find any Legacy drivers, but I have seen Beryl postings about using Open Source ATi or radeon drivers.

---

### Post by kvonb on 2006-12-14
> **trippinnik said:**
> My grfx card (Radeon Mobility 9000 or specifically Radeon Mobility M6 LY) is not supported by flgfx.  I can't find any Legacy drivers, but I have seen Beryl postings about using Open Source ATi or radeon drivers.


If you have (or get) the Edgy CD (Ubuntu 6.10) and boot from it, you will find that it is running the opensource driver.  The only change you can make is by changing the "device" line from "ati" to "radeon" in /etc/X11/xorg.conf, then logout, ctrl-alt-backspace to restart X and log back in (see the instructions at the top of this post).  Then do the direct rendering test (glxinfo | grep "direct rendering").  If it says "Yes" then you are in business, if not then unfortunately I can't help you, all I can suggest is to keep searching the forums for a possible answer.

---

### Post by jbus on 2006-12-14
> **kvonb said:**
> Hey jbus,

If you are going to use reconstructor to make a new liveCD, how about sharing it?  I would like a copy :mrgreen:.

Maybe I'll give it a go.

Which version of the drivers did you use?  For my 9200 the support stops at v8.28.8.

Could you let us know how you installed the drivers, it might help a lot of other people too.

Regards, Kev :)


Though I've never used Reconstructor, I'll give it a shot when I have time this weekend. I'm using ATI drivers v8.28.8, so I'm not sure if that will help you much Kev. 

Those of you having trouble  installing the ATI proprietary drivers should try using [Automatix Bleeder]("http://getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_Bleeder_.28only_on_Ubuntu_6.10_i386_as_of_now.29"). I have found this to be the easiest way. If you already have Automatix installed on Edgy just run "sudo apt-get install automatix2bleeder" to install Bleeder. Then just go to the system tools menu to run Bleeder. It installs v8.28.8 drivers with no need to make any further changes, just reboot.

---

### Post by Bobtheknight on 2006-12-14
Hey I've been tryingn to get Beryl set up for several days now, and this is the only method that worked.  So instead of installing it to the livecd, I decided to reformat the computer and install this.

Strangely enough, the default driver runs with this, but if I were to install fglrx driver it would not work :(  Nor would ati priperotry one I think.

Oh well, maybe I won't be playing any games on linux, but beryl is worth it!

(All I want to do now is spin the cube)

---

### Post by kvonb on 2006-12-14
> Though I've never used Reconstructor, I'll give it a shot when I have time this weekend. I'm using ATI drivers v8.28.8, so I'm not sure if that will help you much Kev.

Sounds good, please do :)  The 8.28.8 drivers work with my 9200SE (or so I'm led to believe :rolleyes:).

> Hey I've been tryingn to get Beryl set up for several days now, and this is the only method that worked. So instead of installing it to the livecd, I decided to reformat the computer and install this.

Strangely enough, the default driver runs with this, but if I were to install fglrx driver it would not work :sad:  Nor would ati priperotry one I think.

Oh well, maybe I won't be playing any games on linux, but beryl is worth it!

(All I want to do now is spin the cube)

Excellent, glad you got it working.  If you can get Beryl working then you CAN play games.  You **don't need** the fglrx driver to run games! I'm running the default (opensource) driver and I play: WolfET online (free), True Combat Elite online (free), Wolfenstein, QuakeII, Glest (free), Battlefield1942 (through Cedega), Half Life II (Cedega), Tribal Trouble (free), Soldier of Fortune, Unreal (WINE), tons of old DOS games with DOSbox, and all the free ones that I can find :mrgreen:.  You might have to turn the graphics quality down a bit, but it does work in full 3d very well.

If you need any more info or help getting games working let me know 8).

Regards, Kev :)

---

### Post by happy-and-lost on 2006-12-16
Works fine for me on the live CD, but it loses Direct Rendering on install, I copied my xorg.conf over from the liveCD, but it still doesn't work :confused:

---

### Post by mells on 2006-12-20
brilliant worked first time!

---

### Post by djlyx on 2006-12-22
Great write up, worked first time for me too.

I have a question, when I flip the cube (change work spaces).  It moves super fast, it kinda flickers.  I can tell its spinning, but it moves too fast.  Do you know how I can reduce the speed of the spin?  

I checked the forum, I couldn't find a post that addresses this issue.  I have the same ATI card as you BTW.

Cheers

---

### Post by kvonb on 2006-12-22
> **djlyx said:**
> Great write up, worked first time for me too.

I have a question, when I flip the cube (change work spaces).  It moves super fast, it kinda flickers.  I can tell its spinning, but it moves too fast.  Do you know how I can reduce the speed of the spin?  

I checked the forum, I couldn't find a post that addresses this issue.  I have the same ATI card as you BTW.

Cheers

Click on the Beryl icon in the taskbar, then select "Beryl Settings Manager", it is the topmost item.  On the left of the popped up window, choose "Rotate Cube", then from the tabs along the top click on "Numeric Values".  Have a play with those, I got mine so that it "bounces" after rotating, it is a bit annoying but it loks nice :).

I have attached 2 images and also my settings profile for reference.

One thing I also did is make the middle mouse button (when you press the wheel) initiate the cube rotation.  It messes up "open in new tab" in Firefox and also quick pasting in terminal, but it makes rotating so much easier and quicker.  You can set that in "Beryl Settings Manager" "Rotate cube" "Mouse", and set it to button 2.

Regards, Kev :)

---

### Post by djlyx on 2006-12-23
Thanks!

---

### Post by cos4 on 2006-12-25
I found something interesting in the reconstructor forum [Link]("http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&Itemid=44&func=view&id=4&catid=2"). I gave it a try late at night but I guess I mixed something up. Maybe I'll try again when I've got some free time or one of you gives it a try, working with the constructor is really easy you just have to know wich packages are needed and where to change a config file etc.

---

### Post by OMRebel on 2007-01-03
I booted up off of the Live CD to give this a try, but right at the first of this HowTo I got:

ubuntu@ubuntu:~$ glxinfo | grep vendor
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

I have a Radeon 9600SE.  Any suggestions?

---

### Post by kvonb on 2007-01-03
> **OMRebel said:**
> I booted up off of the Live CD to give this a try, but right at the first of this HowTo I got:

ubuntu@ubuntu:~$ glxinfo | grep vendor
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

I have a Radeon 9600SE.  Any suggestions?

I had that same type of error message while I was trying to setup an old nvidia legacy card, I believe it was because the BIOS was setup wrong.  Have a look in your BIOS (press DEL or F2 or whatever key it says at startup) and check the AGP settings, make sure that your AGP Aperture is 128 megs, turn on the video interrupt, and check the AGP speed, try 4x.  Also I would edit /etc/X11/xorg.conf and change the device from "ati" to "radeon", logout, restart gdm (sudo /etc/init.d/gdm restart), then try again.  That's all I can suggest right now.

---

### Post by mburgoon on 2007-01-05
kvonb

You are quite possibly my hero. I have screwed up my computer countless times trying to get the beryl effects installed... and your walkthrough works perfectly!!!!

I am using edgy, on a vaio s260, with an ati 9200 and the effects work awesome.  

THANK YOU!!!!!!!

---

### Post by kvonb on 2007-01-06
> **mburgoon said:**
> kvonb

You are quite possibly my hero. I have screwed up my computer countless times trying to get the beryl effects installed... and your walkthrough works perfectly!!!!

I am using edgy, on a vaio s260, with an ati 9200 and the effects work awesome.  

THANK YOU!!!!!!!

You're welcome, glad you got it working :cool:.

I got an nVidia 6600GT for Christmas so I'm probably going to do one for nVidia as well if anyone is interested.

---

### Post by finferflu on 2007-01-07
Unfortunately there is no way to get Beryl working with Radeon Mobility 9000, except installing XGL, which makes your wacom tablet unusable... Too bad Mobility 9000 is not supported by the open source driver (and that the official binary one does not support direct rendering..)...

Well, I guess we'll just have to wait...

---

### Post by kvonb on 2007-01-08
> **finferflu said:**
> Unfortunately there is no way to get Beryl working with Radeon Mobility 9000, except installing XGL, which makes your wacom tablet unusable... Too bad Mobility 9000 is not supported by the open source driver (and that the official binary one does not support direct rendering..)...

Well, I guess we'll just have to wait...

I read somewhere that on some notebooks there is a setting in BIOS relating to "sideband" memory or something for the graphics card, and that you have to enable it in order for it to work.  Maybe have a look and see.

---

### Post by ~LoKe on 2007-01-08
Interesting concept, but it seems like a bit much to do with a slow LiveCD.

---

### Post by mburgoon on 2007-01-08
Unfortunately once I rebooted my machine... it appears that Beryl is not working correctly anymore. 

I have a 13.3 widescreen laptop that normally displays at a resolution of 1280x800. However once the computer boots up and Beryl executes, about 1/4 of the screen on the right side is cut off (it's just white). 

I can change my resolution to 1024x768 and then I can see the entire screen. I would rather have a higher resolution then Beryl effects.... but ideally I would like both.... 

Has anyone ever experienced this problem....? or have a solution I might be able to try??

---

### Post by geekgirl74 on 2007-01-09
> **finferflu said:**
> Unfortunately there is no way to get Beryl working with Radeon Mobility 9000, except installing XGL, which makes your wacom tablet unusable... Too bad Mobility 9000 is not supported by the open source driver (and that the official binary one does not support direct rendering..)...

Well, I guess we'll just have to wait...

Hmm... that's not true... I've got Beryl+AIGLX running on a Radeon Mobility 9000 (rv250 with 64MB) on Feisty (I've also successfully tested it on Edgy) - using the opensource ati driver. The only thing is, that the performance drops at 24bit and makes scrolling unusable, so I'm using 1400x1050@16bit on my Samsung P30. 

I tuned the settings in xorg.conf and drirc. 
Glxgears gives ~3500fps in Gnome. On the other side I had to recompile libgtk2.0-0 (apt-get source -b libgtk2.0-0, compiled with CFLAGS=-O2 -march=pentium-m -pipe -fomit-frame-pointer, which i put as env variable in /etc/profile) to remove the lagging when opening programs like Gnome-Terminal etc... now beryl's running like a charm, but I still miss 24bit... it's a little bit exhausting to reconfigure several emerald themes for making them usable at 16bit :(

I would post my configs, if anybody is interested.

Cheers,
geekgirl74

---


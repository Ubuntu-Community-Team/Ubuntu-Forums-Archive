---
title: "HOWTO: ATI FGLRX 3D Acceleration"
date: 2004-11-07
forum: Outdated Tutorials &amp; Tips
---

### Post by mattyh on 2004-11-07
Ok, this HOWTO is more of a grouping together of the information found here on the forums, along with a little bit from my own experiences. In seeing how many different posts there are related to pretty much the same issues with the ATI drivers, I thought it would be helpful to stick all the information right here, in what seems to be the logical spot. Thanks to all the people who have posted on the various ATI threads, I really don't know who I got what from, so I thought I'd thank all of you.
    
    **NOTE:** These methods worked perfectly for my ATI 9600xt All in Wonder, and many other people, so hopefully it will work for the rest of the ATI cards supported by fglrx
    
    _**Steps:**_
    
   ** 1. **First off, follow the instructions provided in the Wiki ([http://wiki.ubuntulinux.org/BinaryDriverHowto]("http://wiki.ubuntulinux.org/BinaryDriverHowto")) under the ATI (fglrx) Graphics Card heading.
    
   ** 2. **Next, we are going to add a line to your /etc/X11/XF86Config-4 file. Before you edit that file, it is best to make a backup. To do so, use the following line:
    
    **sudo cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.bak**
    
    If at any point in the future it becomes necessary to restore the backup, you can do so by typing:
    
    [b]sudo cp /etc/X11/XF86Config-4.bak /etc/X11/XF86Config-4
    
    [/b]Now, I have found that by adding the following section in your XF86Config-4 file (via **sudo pico /etc/X11/XF86Config-4**) 3d acceleration will work after you restart your computer. It didn't seem to work by the Usual Ctrl+Alt+Backspace to restart X, but it does after a restart. The line in bold is the line to be added, and I included the surrounding text so that it is easy to find.
    
    Section "Device"
   Identifier      "ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
         Driver          "fglrx"
         BusID           "PCI:2:0:0"
   **Option          "UseInternalAGPGART" "no"**
                   EndSection
    
    Now, at this point, after a restart, you should be able to run **fglrxinfo **(type that command into a terminal), and it should output something like this (pay special attention to vendor string: if it says Mesa, 3d acceleration is not working):
    
    display: :0.0  screen: 0
    OpenGL vendor string: **ATI Technologies Inc.**
    OpenGL renderer string: RADEON 9600 XT Generic
    OpenGL version string: 1.3.4510 (X4.3.0-3.12.0)
    
    
   ** 3.** One thing the above method does not seem to enable is the Xv extension, which can be used by programs such as Mplayer, to speed up the acceleration of video playback. So. let's go ahead and run **fglrxconfig** (read below first), which seems to fix this issue.
    [b]
    BEFORE YOU RUN[/b] fglrxconfig make sure you have backed up your XF86Config-4 file as detailed in section 2.
    
    Now, take a look at your old XF86Config-4 file (via **sudo pico /etc/X11/XF86Config-4**), I usually open a new terminal to open this file so that I can look at my old config as needed. Just make sure to close it before you finish fglrxconfig. You need to take special note of the vertical and horizontal refresh rates ubuntu chose for you, or alternatively you can go ahead and get out your monitor manual which should have the ranges listed for you. (I know a lot of people probably don't have those handy) :D Below is where mine were listed:
    
    Section "Monitor"
        Identifier      "eView 17f2"
        [b]HorizSync       30-70
        VertRefresh     50-160[/b]
        Option          "DPMS"
    EndSection
    
    Now, go ahead and type **sudo fglrxconfig**.  For the most part the default values this program provides you with are fine, except where noted:
    
         a. Go ahead and choose whatever mouse you think is most similar to yours, it isn't to big of a deal.
    
         b. When it asks for which port your mouse is connected to, type: [b]/dev/input/mice
    
    [/b] c. Go ahead and except the default values and then when you get to where it asks for the Vertical Refresh rates, and then the Horizontal Refresh rates, go ahead and enter custom if you know them from above.
    
 d. Now, when it asks about resolutions, I generally choose custom, and enter 6321. (i.e. 1280x1024 1024x768 800x600 640x480) Go ahead and enter whatever resolutions you like.
    
         e. Here is one of the important entries: When it comes up to **Do you want to use an** **external AGPGART**, choose **Y**.
    
         f.  When it asks about Locked User Pages I chose No.
    
 g. On the next page I usually select 2 (WineX), even though I'm not sure if that is a big deal or not, but since I run WineX I play it safe.
    
    Go ahead and tell it to write the XF86Config-4 file, and you should be good to go.  
    
    **4. **Sometimes, after you restart you may notice that you don't have the scroll wheel on your mouse (if you have a scroll wheel) working, this is usually remedied by adding the following line (line in bold, the section mine was located in is given to help narrow down where to place it):
   
    Identifier  "Mouse1"
        Driver "mouse"
        Option "Protocol"   "ImPS/2"
    **    Option "ZAxisMapping"   "4 5"**
        Option "Device"     "/dev/input/mice"
    
 One last thing I noticed after checking the differences between the two XF86Config files is that some of the font paths are not listed anymore after running fglrxconfig. Here is a listing of the font paths after I edited them (these are the font paths *my* default XF86Config-4 file showed, yours might be different):
    
        FontPath   "unix/:7100"
        FontPath   "/usr/lib/X11/fonts/misc/"
        FontPath   "/usr/lib/X11/fonts/cyrillic"
        FontPath   "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath   "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath   "/usr/lib/X11/fonts/Type1/"
        FontPath   "/usr/lib/X11/fonts/CID"
        FontPath   "/usr/lib/X11/fonts/Speedo/"
        FontPath   "/usr/lib/X11/fonts/75dpi/"
        FontPath   "/usr/lib/X11/fonts/100dpi/"
        FontPath   "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath   "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
    
    
    I hope this HOWTO was helpful, and gets a lot of people up and running with their ATI cards.

---

### Post by wallijonn on 2004-11-07
Two very minor points:

> sudo cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.bak

Always look at your prompt to make sure where you're at. If you are in /etc/X11 then you issue a [COLOR=BLUE]sudo cp /etc/X11/XF86Config-4.bak /etc/X11/XF86Config-4[/COLOR] command to get back your original configuration.

You could also just issue another [COLOR=RED]fglrxconfig[/COLOR] command at the # prompt to redo it and [COLOR=RED]shutdown -r now[/COLOR] to do a clean reboot. 

You should add only the fonts listed in your [COLOR=DarkGreen]/usr/X11R6/lib/X11/fonts[/COLOR] directory (everybody's will probably be different)

Since I was getting speedo font errors (/var/log/XF86Config.0.log), I added 

[COLOR=RED]# This loads the Speedo font modules
    Load        "speedo"[/COLOR]

after this section:

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

.

---

### Post by nicklaz on 2004-11-09
I'm a linux noob that's in desperate need of help.  I applied all the fglrx driver changes but now I can no longer change my resolution with the screen resolution GUI tool.  

Does anyone know how to fix this?

---

### Post by fng on 2004-11-09
I had that problem too nicklaz
But i cant remember how i fixed it :(

sorry

possible solutions:
- wrong default resolution in config file
- wrong horizontal/vertical sync of monitor in config file

---

### Post by mattyh on 2004-11-09
It sounds like during the fglrxconfig you didn't select multiple resolutions. If you rerun fglrxconfig, at the resolution screen, hit 1 to change the possible resolutions. Keep in mind that for instance, if you want 1280x1024, 1024x768,800x600, and 640x480, you would enter 6321 I believe. In other words, you enter in the numbers for each resolution you want available. If this doesn't fix it you can edit the config yourself, which I don't recommend seeing as you categorize yourself as new. But, to do that you would search through the /etc/X11/XF86Config-4 file for the section that looks like this:
  ```

   	Subsection "Display"
   		Depth	   24
   		Modes	   "1280x1024" "1024x768" "800x600" "640x480"
 		ViewPort	0 0 # initial origin if mode is smaller than desktop
   #		Virtual	 1280 1024
   	EndSubsection
 
``` 
 If I wanted to add 1600x1200 to this above line, making sure of course my monitor can handle this. I would change the code to read:
 
  ```
   	Subsection "Display"
    		Depth	   24
    	    Modes	   "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
 		ViewPort	0 0 # initial origin if mode is smaller than desktop
    #		Virtual	 1280 1024
    	EndSubsection
 
``` 
    [color=Red]MAKE SURE that you backup your XF86Config-4 file as detailed in the posts above.[color=Black]  Hope this fixes your problem.[/color][/color]

---

### Post by nicklaz on 2004-11-10
Got it working!!  Thanks guys!!

---

### Post by HiddenWolf on 2004-11-11
Already had mine working by the time I saw this, but it's a good howto, and deserves some polish, then a sticky

---

### Post by mattyh on 2004-11-11
I added some "polish" any more suggestions.  I was hoping for some feedback on whether this is working for people or not.  Thanks.

---

### Post by allen on 2004-11-11
[QUOTE=mattyh]I added some "polish" any more suggestions.  I was hoping for some feedback on whether this is working for people or not.  Thanks.[/QUOTE]
 worked great for me but i stopped at step 3 as i don't plan on using MPlayer.

i had loads of trouble before reading this... thanks.

---

### Post by HiddenWolf on 2004-11-13
Ugh, the ati drivers are horrific, why would anyone bother...

I do not miss mine in the least.

---

### Post by HungSquirrel on 2004-11-13
> why would anyone bother...
Half-Life 2 comes out Tuesday.  If it can run on Cedega, me = :-D

---

### Post by mattyh on 2004-11-13
me, unless someone wants to buy my all in wonder :)

---

### Post by simmer on 2004-11-18
So this is version 3.12.0 of the ATi Radeon drivers? Let's say I wanted to install the latest once in order to play Doom3. How would one go about then?

Just out of curiosity: Which fps do you guys get with fgl_glxgears? I own a 9800 Pro and get the following:

2127 frames in 5.0 seconds = 425.400 FPS
2555 frames in 5.0 seconds = 511.000 FPS
2566 frames in 5.0 seconds = 513.200 FPS
2396 frames in 5.0 seconds = 479.200 FPS
2601 frames in 5.0 seconds = 520.200 FPS

-simmer

---

### Post by ohbahsan on 2004-11-18
followed this howto and got my 8500 LE running with dual monitor setup.  thanks a lot!

---

### Post by wallijonn on 2004-11-18
Simmer,

glxgears is a funny thing - I get about 900fps (9800Pro 128/256) but I've read that some others are getting >2000. It should be the only thing running (no other apps). Just let it run for 2 minutes without moving the mouse.

---

### Post by humina on 2004-11-24
I ran this howto and when I run tuxracer I notice that it runs faster than before, but there are a bunch of random polygons everywhere.  I get the same problem with tuxkart.  How do I fix that? :-(

Output of various commands:

lsmod | grep fglrx
----------------------------------
fglrx                 215044  7

dmesg | grep fglrx
----------------------------------
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[fglrx] module loaded - fglrx 3.12.0 [Jul 16 2004] on minor 0
[fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[fglrx] free  AGP = 54800384
[fglrx] max   AGP = 54800384
[fglrx] free  LFB = 116391936
[fglrx] max   LFB = 116391936
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 16384

fglrxinfo
---------------
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.4510 (X4.3.0-3.12.0)

My fgl_glxgears command works fine and I get over 500 FPS

---

### Post by IchaBOB on 2004-11-24
[QUOTE=mattyh]Ok, this HOWTO is more of a grouping together of the information found here on the forums, along with a little bit from my own experiences. In seeing how many different posts there are related to pretty much the same issues with the ATI drivers, I thought it would be helpful to stick all the information right here, in what seems to be the logical spot. Thanks to all the people who have posted on the various ATI threads, I really don't know who I got what from, so I thought I'd thank all of you.
    
    [/QUOTE]


 Well, each time I can go thru fglrxconfig, i specify my custom H and V settings and pick the resolutions I want.... Saves fine...

When I login thru GUI, it is clearly over 1000 (default was set to 1152), but when it loads up the desktop, it changes the resolution to 832x624... I cannot change the resolution thru GUI b/c the settings are (in the listed order):
1024x768
832x624
800x600
640x480
1024x768 <--- listed twice

I did specify in the config the following order:
1152, 1024, 800, 640 

Any ideas why I can't get this to work correctly?
Thx
ps - I've followed all the directions for ATI drivers and kernel etc successfully up to this point.

---

### Post by uliketu on 2004-11-24
Hey Icha, try removing all resolutions that you do not intend to use, ie. Just use the resolution you want and scrap the rest.  Just make sure your monitor supports it....
and back up your config file.

Simmer,  those fps are terrible for the card you have.  I have radeon 9000 pro
and these are my stats when using glxgears.  This is with other apps running...

9129 frames in 5.0 seconds = 1825.800 FPS
9323 frames in 5.0 seconds = 1864.600 FPS
9317 frames in 5.0 seconds = 1863.400 FPS
9269 frames in 5.0 seconds = 1853.800 FPS

It may be a driver issue, I'm not sure.  But if I were you, I would 
back up your config file and start tweaking...But, that's just me.

good luck

---

### Post by mattyh on 2004-11-24
[QUOTE=uliketu]

Simmer,  those fps are terrible for the card you have.  I have radeon 9000 pro
and these are my stats when using glxgears.  This is with other apps running...

9129 frames in 5.0 seconds = 1825.800 FPS
9323 frames in 5.0 seconds = 1864.600 FPS
9317 frames in 5.0 seconds = 1863.400 FPS
9269 frames in 5.0 seconds = 1853.800 FPS

It may be a driver issue, I'm not sure.  But if I were you, I would 
back up your config file and start tweaking...But, that's just me.

good luck[/QUOTE]

You're confusing fgl_glxgears and glxgears.  They give different framerates.  I've also been hearing around that glxgears isn't a good benchmarking tool at all.  Anyways, it seems quite logical that fgl_glxgears would give much lower FPS.

---

### Post by IchaBOB on 2004-11-24
[QUOTE=uliketu]Hey Icha, try removing all resolutions that you do not intend to use, ie. Just use the resolution you want and scrap the rest.  Just make sure your monitor supports it....
and back up your config file.

Simmer,  those fps are terrible for the card you have.  I have radeon 9000 pro
and these are my stats when using glxgears.  This is with other apps running...

9129 frames in 5.0 seconds = 1825.800 FPS
9323 frames in 5.0 seconds = 1864.600 FPS
9317 frames in 5.0 seconds = 1863.400 FPS
9269 frames in 5.0 seconds = 1853.800 FPS

It may be a driver issue, I'm not sure.  But if I were you, I would 
back up your config file and start tweaking...But, that's just me.

good luck[/QUOTE]
  Ok, well

I went into XF86Config and removed all the modes except for 1178......
When I rebooted, the login screen came in @ 1178, then desktop defaulted back to 832....

Went to change the res (GUI) and after removing them and a reboot ......
Now it lists:
1152x864
1152x768
1024x768
832x624
800x600
640x480

but hell, it Works!! I set 1152x846 as the default so hopefully it will reload it back to it

---

### Post by mdr on 2004-11-26
many thx for the how-to - finally got this working (though cannot change screen resolution in gnome yet though)

however - trivial point - you need to run the 386 kernel.
running the 686 kernel leads to mucho hair loss and gnashing of teeth.......well it has for me.

Moral of the story - do not try to be a smarty and upgrade to the 686 kernel first and hope fglrx will work too!!
:)

---

### Post by Jae686 on 2004-11-26
and Radeon MOBILE support?

---

### Post by wallijonn on 2004-11-27
[QUOTE=mdr]cannot change screen resolution in gnome yet 

however - trivial point - you need to run the 386 kernel.
running the 686 kernel leads to mucho hair loss and gnashing of teeth.......well it has for me.

[/QUOTE]
Once you create a fglrx XF86Config-4 file the Computer -> System Configuration -> Screen Resolution will no longer work; you will have to generate another XF86Config-4 file via fglrx.

You'll have to install the "correct" 686 kernel to be able to use DRI / fglrx (mentioned elsewhere).

---

### Post by mattyh on 2004-11-27
According to ATI's web site, they don't provide 3d drivers for their mobile solutions.  At least the information I found pointed to that.  Now, I used to have a Rage Mobility in my old laptop, and if I remember right GATOS ([http://gatos.sourceforge.net](http://gatos.sourceforge.net)) had some 3d accleration drivers for that chipset.  You might want to check that site to see, but I doubt it will be too helpful.

---

### Post by linny129 on 2004-11-27
[QUOTE=humina]I ran this howto and when I run tuxracer I notice that it runs faster than before, but there are a bunch of random polygons everywhere.  I get the same problem with tuxkart.  How do I fix that? :-(

Output of various commands:

lsmod | grep fglrx
----------------------------------
fglrx                 215044  7

dmesg | grep fglrx
----------------------------------
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[fglrx] module loaded - fglrx 3.12.0 [Jul 16 2004] on minor 0
[fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[fglrx] free  AGP = 54800384
[fglrx] max   AGP = 54800384
[fglrx] free  LFB = 116391936
[fglrx] max   LFB = 116391936
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 16384

fglrxinfo
---------------
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.4510 (X4.3.0-3.12.0)

My fgl_glxgears command works fine and I get over 500 FPS[/QUOTE]

 :sad:  Same problem - anyone have a solution?????

---

### Post by lagartija on 2004-12-01
[QUOTE=linny129]:sad:  Same problem - anyone have a solution?????[/QUOTE]

same problem for me with tuxracer
i've solved it upgrading to the last version of the ati drivers following this thread

[http://www.ubuntuforums.org/showthread.php?t=5461&highlight=ati](http://www.ubuntuforums.org/showthread.php?t=5461&highlight=ati)

hope it helps

---

### Post by humina on 2004-12-02
the posted deb source file works great.  Thanks for the post.

---

### Post by Murmex on 2004-12-02
[QUOTE=Jae686]and Radeon MOBILE support?[/QUOTE]
 Oy, oy, I've just started using Ubuntu and this is my first Linux distribution ^^

Anyway about ATI Mobility GPU, ATI released a few time ago some driver for them. I don't really know how it works, but you can find them in Linux -> FireGL -> Mobility FireGL T2 or 9000 (I personnally have a Mobility FireGL 9000 GPU)

About random polygons, there's a note on the ATI website about Doom 3 :
[http://www.ati.com/support/infobase/4688.html](http://www.ati.com/support/infobase/4688.html)

As lagartija said, you have to install the latest Drivers.

Me I'm gonna try for the third time to install those drivers. My prob is as I knw nearly nothing about Linux in general, I don't really know how to fix Ubuntu when I can't use it anymore with the Gnome interface (I feel a bit lost like that...) but I'm gonna try again ^^

Edit : Oy yeah, does that make a problem that ATI drivers are develloped for Kernel 2.4 as if I'm not wrong Ubuntu Kernel is the 2.6?

---

### Post by orestis82 on 2004-12-08
Is there any information about enabling 3d support on older ATI cards like Radeon 9200 ? I've read that they don't need fglrx as there is built-in support using the ati driver,  however, 3d support is not turned on, I have the Mesa system handling openGL.

---

### Post by robtotheb on 2004-12-16
Ive followed this HOWTO and its not worked  :sad: 

I wrote this in the 'XF86Config-4'

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9700 Pro (R300 ND)"
        Driver          "fglrx"
        BusID           "PCI:3:0:0"
       ** Option "UseInternalAGPGART" "no"**
XF86Config-4


I get this out with 'fglrxinfo'

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4


Any ideas what went wrong?

---

### Post by flibblesan on 2004-12-16
[QUOTE=robtotheb]Ive followed this HOWTO and its not worked  :sad: 

I wrote this in the 'XF86Config-4'

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9700 Pro (R300 ND)"
        Driver          "fglrx"
        BusID           "PCI:3:0:0"
       ** Option "UseInternalAGPGART" "no"**
XF86Config-4


I get this out with 'fglrxinfo'

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4


Any ideas what went wrong?[/QUOTE]
 I'm getting this too. When I was last running Ubuntu on this PC I didn't upgrade the kernel and fglrx worked fine. After a format I installed Ubuntu again and upgraded the Kernel to the latest K7 kernel.

I followed all guides I could find, and I've done everything to the letter exactly how I did first time around. But no matter what I still get the "Direct Rendering: NO" issue

Is the kernel the issue? If so what kernel should I be running for this to work?

---

### Post by flibblesan on 2004-12-16
this takes the piss now...

I've gone back to the original kernel and still can't get fglrx working.

It looks as if the Mesa libGL is getting loaded instead of the ATI one. Anyone know how to fix this?

---

### Post by flibblesan on 2004-12-17
someone in this "community" have any helpful advice of getting this working? Please?

---

### Post by flibblesan on 2004-12-17
Wow. After hours of tinkering I finally got it working. Here is what I did:

Install linux-restricted-modules that match your running kernel (in my case, 2.6.8.1-3-k7)
Installed fglrx-driver, fglrx-driver-dev and fglrx-control.
Ran "sudo fglrxconfig" as mentioned in the [guide](http://ubuntuforums.org/showthread.php?t=3567&page=1&pp=10) remembering to say no to UseInternalAGPGART.
quit the xserver and ran glxinfo. OpenGL is now listed as ATI.

Only issue now is the version installed is 3.12.0 I'm working on getting more recent drivers working and I'll post once I do.

---

### Post by flibblesan on 2004-12-17
Hmm

Tried upgrading to Daniels fglrx drivers which didn't work. Also tried the flavio drivers which again didn't work.

I don't understand how the normal warty drivers work but the newer ones don't :S

---

### Post by mattblack_uk on 2004-12-20
Xlib: extension "XFree86-DRI" missing on display ":0.0".

I'm also getting the above line when I run fglrxinfo. I have installed the k7 kernel. Could it be a problem with this kernel? People running the 686 kernel don't seem to be having the same problems. If I try to run fglrxconfig, it won't let me get back into X after a reboot. I have to restore my backup.

---

### Post by mattblack_uk on 2004-12-20
Would a 686 kernel be ok to use on an athlon? I remember when I used Yoper which is 686 optimised, and it seemed to run very quickly on my system.

---

### Post by nehalem on 2004-12-21
While I just asked and question and don't yet know if I'll get an answer if you want an athoritive forum on ATI linux drivers it appears that the following is the place:

[http://www.rage3d.com/board/forumdisplay.php?f=88](http://www.rage3d.com/board/forumdisplay.php?f=88)

I have been hunting for some time for people that can help me with getting external monitor support done right for my laptop and based on the comments and the tutorial found [here](http://www.rage3d.com/board/forumdisplay.php?f=89) I think this is the place.

Just another resouce!  (on another note that seem to have this same forum setup but their editor is much nicer (works like an actual word like editor in that I can press ctrl-u and it will underline and show it in real time), I'm guessing this is just disabled on this site?

---

### Post by wallijonn on 2004-12-31
These are all the **restricted** kernels (You will have to add the Restricted Repositories) listed in SPM which are compiled to use the ATI & nVidia fglrx drivers & their descriptions  ([COLOR=Red]r**ead the bottom pane. It should list ATI & nVidia.**[/COLOR]):

```

linux-restricted-modules-2.6.8.1-[COLOR=Red]3[/COLOR]-_386_
Non-free Linux 2.6.8.1 modules on 386

linux-restricted-modules-2.6.8.1-[COLOR=Blue]4[/COLOR]-_386_
Non-free Linux 2.6.8.1 modules on 386

linux-restricted-modules-2.6.8.1-[COLOR=Red]3[/COLOR]-_686_
Non-free Linux 2.6.8.1 modules on PPro/Celeron/PII/PIII/PIV

linux-restricted-modules-2.6.8.1-[COLOR=Blue]4[/COLOR]-_686_
Non-free Linux 2.6.8.1 modules on PPro/Celeron/PII/PIII/PIV

linux-restricted-modules-2.6.8.1-[COLOR=Red]3[/COLOR]-_686-[COLOR=Red]smp[/COLOR]_
Non-free Linux 2.6.8.1 modules on PPro/Celeron/PII/PIII/PIV SMP

linux-restricted-modules-2.6.8.1-[COLOR=Blue]4[/COLOR]-_686-[COLOR=Blue]smp[/COLOR]_
Non-free Linux 2.6.8.1 modules on PPro/Celeron/PII/PIII/PIV SMP

linux-restricted-modules-2.6.8.1-[COLOR=Red]3[/COLOR]-_k7_
Non-free Linux 2.6.8.1 modules on AMD K7

linux-restricted-modules-2.6.8.1-[COLOR=Blue]4[/COLOR]-_k7_
Non-free Linux 2.6.8.1 modules on AMD K7

linux-restricted-modules-2.6.8.1-[COLOR=Red]3[/COLOR]-_k7-[COLOR=Red]smp[/COLOR]_
Non-free Linux 2.6.8.1 modules on AMD K7 SMP

linux-restricted-modules-2.6.8.1-[COLOR=Blue]4[/COLOR]-_k7-[COLOR=Blue]smp[/COLOR]_
Non-free Linux 2.6.8.1 modules on AMD K7 SMP

```

Chances are that those of you who are having problems running fglrx probably have the wrong kernel installed. Or you did not installed the restricted modules. Install the one(s) I mentioned above and see if that doesn't take care of your problem.

For those who like the ATunnel screensaver: Go to [COLOR=Blue]Advanced[/COLOR] -> visual: [COLOR=Blue]GL[/COLOR].

---

### Post by Obi-Lan on 2005-01-07
Had to compile kernel and fglrx driver. Now works fine. fglrxinfo says:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.4641 (X4.3.0-3.14.6)

And fgl_glxgears gives:

2307 frames in 5.0 seconds = 461.400 FPS
2812 frames in 5.0 seconds = 562.400 FPS
2774 frames in 5.0 seconds = 554.800 FPS
2682 frames in 5.0 seconds = 536.400 FPS
2769 frames in 5.0 seconds = 553.800 FPS

---

### Post by Ron0909 on 2005-01-08
Hi everyone :)

I'm relatively new to Linux and have been messing around with quite a few distributions. To date I find that Ubuntu is brilliant and far more useable than any of the others. In my travels, I played around with Kanotix which is a derivative of Knoppix. Both are Debian based distros and designed as live distros with options to install to hd. Kano has a script that will install the latest drivers that actually works.
Glxgears was flying! I was wondering if anyone could adapt that script to function with Ubuntu? Ubuntu is far more to my personal liking and less likely to break under my clumsy hands. Here is a link to the script I am talking about
[http://kanotix.com/files/](http://kanotix.com/files/)

The file name is install-radeon-debian.sh

All my best and thank you to all the Ubuntu team for a great OS!

Ron
[http://www.cardmodels.net](http://www.cardmodels.net)

---

### Post by telmo on 2005-01-16
[QUOTE=flibblesan]Wow. After hours of tinkering I finally got it working. Here is what I did:

Install linux-restricted-modules that match your running kernel (in my case, 2.6.8.1-3-k7)
Installed fglrx-driver, fglrx-driver-dev and fglrx-control.
Ran "sudo fglrxconfig" as mentioned in the [guide](http://ubuntuforums.org/showthread.php?t=3567&page=1&pp=10) remembering to say no to UseInternalAGPGART.
quit the xserver and ran glxinfo. OpenGL is now listed as ATI.

Only issue now is the version installed is 3.12.0 I'm working on getting more recent drivers working and I'll post once I do.[/QUOTE]

I'm running 2.6.10-2.686 Kernel in a ATI Mobility Radeon 9600 (m10) and i get...

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4      :-& 

What can i do??? Any help pls?

---

### Post by .tekrox on 2005-01-16
OK, I followed the Tutorial, and got everything Running Fine on the older drivers in the warty reposotries; I then upgraded to the 3.14 drivers from the Hoary reposotries and I'm getting all the mesa3D stuff again ;_;

the X server config was untouched, and I checked to make sure nvidia.ko wasn't still in the current kernel's librarys!

any ideas?

---

### Post by xkcdmagic8 on 2005-01-16
Guys dont worry :!!!!!!: The new ATI FGLRX drivers which are supposed to be awsome are being released TOMMOROW!! so hang on and tomorrow everything should work!!

---

### Post by .tekrox on 2005-01-16
[QUOTE=nitinshantharam]Guys dont worry :!!!!!!: The new ATI FGLRX drivers which are supposed to be awsome are being released TOMMOROW!! so hang on and tomorrow everything should work!![/QUOTE]
 Just tried the script Ron linked to; no go either, so I'm back going back the 2.xx drivers until someone has ant idea of whats going on with these 3.14 drivers - or if what nitinshantharam says is true - then maybe new ATI drivers might work (we can always hope)

---

### Post by darkoptix on 2005-01-16
New drivers??? sounds like BULL! but, I'll wait/pray and see.  Hopefully they don't mess the XF86Config-4 file up, as bad as the last!

---

### Post by Mow on 2005-01-16
[QUOTE=darkoptix]New drivers??? sounds like BULL! but, I'll wait/pray and see.  Hopefully they don't mess the XF86Config-4 file up, as bad as the last![/QUOTE]

It's not bullshit. They say that the drivers will be released for X.ORG this week.

---

### Post by telmo on 2005-01-17
LOLOLOLOLOL I've just enabled 3D in my ATI card and NOW everyone is telling me the drivers are being released today!?!?!? I feel really dumb!  8-[

---

### Post by artnay on 2005-01-17
It's released. [Go check it out!](http://www.ati.com/support/drivers/linux/radeon-linux.html?type=linux&prodType=graphic&prod=productsLINUXdriver&submit.x=8&submit.y=7&submit=GO%21) Time for new HOW-TO? :mrgreen: 

/me goes updating.

---

### Post by Leaf on 2005-01-18
ok... I installed em (the new drivers) but I cant get em to work, sleep now.

---

### Post by mirtux on 2005-01-21
[QUOTE=Obi-Lan]Had to compile kernel and fglrx driver. Now works fine. fglrxinfo says:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.4641 (X4.3.0-3.14.6)

And fgl_glxgears gives:

2307 frames in 5.0 seconds = 461.400 FPS
2812 frames in 5.0 seconds = 562.400 FPS
2774 frames in 5.0 seconds = 554.800 FPS
2682 frames in 5.0 seconds = 536.400 FPS
2769 frames in 5.0 seconds = 553.800 FPS[/QUOTE]

Hi,
  i've installed Ubuntu after painful and stressing use of Fedora Core 3. I've finally installed ATI drivers. This is my [COLOR=Red]fglrxinfo[/COLOR]

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.4510 (X4.3.0-3.12.0)
``` 

My question is: i have some 220 FPS when i'm watching the scrreen with rotating wheels, but it peaks to 550 FPS when the windows is minimized! In which situation i have to benchmark my configuration?

Thanks,
MC

PS: i'm happy now to be in the Ubuntu community
  :-P

---

### Post by Michael on 2005-01-22
Thanks for the awesome guide man! First time that I was able to make X run only after 3 reboots :p

michael@ubuntu:~ $ glxgears
15231 frames in 5.0 seconds = 3046.200 FPS
15600 frames in 5.0 seconds = 3120.000 FPS
15611 frames in 5.0 seconds = 3122.200 FPS
15610 frames in 5.0 seconds = 3122.000 FPS
15607 frames in 5.0 seconds = 3121.400 FPS
15607 frames in 5.0 seconds = 3121.400 FPS

@ Radeon 9800 Pro

8)

I still have one question though. I have an LG F700P monitor which is able to run 1024x768 on 100Hz, and I set the right settings in XFConfig-4 (the vert/horz rates) but it shows it only on 85Hz, how can I make it run on 100Hz at this resolution?

---

### Post by J. S. Jackson on 2005-01-23
[QUOTE=Michael]
I still have one question though. I have an LG F700P monitor which is able to run 1024x768 on 100Hz, and I set the right settings in XFConfig-4 (the vert/horz rates) but it shows it only on 85Hz, how can I make it run on 100Hz at this resolution?[/QUOTE]

I have noticed this same thing, and I'm not sure how to correct it, however,I don't bother to run over 85Hz at any resolution, simply because it causes the image to blur more (most easily noticed looking at text obviously).  Generally you should always set the *minimum* refresh rate that is flicker-free for you.

A high end CRT can often do well over 100Hz at 1024x768, but that doesn't mean you should run it like that.  The reason that they use high end electronics/electron guns on those monitors is not so that you can do 160Hz @ 800x600, but rather so you can get acceptable refresh at high res.  For example 85Hz at 1600x1200 or 1280x1024/960.  It's unlikely anyone would read text at that res on a 17" monitor like yours, but for gaming, it's critical.

Most people are not able to detect any flicker at 75-80Hz at 640x480, but of course no one runs at that res.  Up to 1280x960 or even 1600x1200, you shouldn't detect any flicker whatsoever at 85hz.  Most people cannot see a difference between 85-100Hz, so running at 100+Hz only serves to throw the monitor slightly out of focus.

I don't mean this to sound like I'm "instructing" you, but rather to make you feel happier about "only" running at 85Hz until you get the problem sorted to your liking.  ;)

---

### Post by Gibbz on 2005-01-24
does anyone have a guide for getting new ati drivers and x.org working?

---

### Post by jensyt on 2005-01-24
[QUOTE=Gibbz]does anyone have a guide for getting new ati drivers and x.org working?[/QUOTE]
If you're running Hoary, all it takes is some apt-get install's. Warty, I'm not sure, though. If anyone wants me to, I can look into writing a howto for the new drivers.... Of course, this one could simply be adapted or added onto.

---

### Post by Gibbz on 2005-01-25
yeah im running array 3, i downloaded them via synaptic but got stuck editing xorg.conf

---

### Post by HBK on 2005-01-28
Hi,
I've got some questions about the options in fglrxconfig: What do
> Do you want to initialize xfree86-dga (y/n)? [n]
Do you want to export pseudo color visuals (y/n)? [n]
Do you want to synchronize buffer swaps
with the vertical sync signal (y/n)? [n]
Do you want to force multi sample visuals for every OpenGL application? (y/n)? [n]
Disable FSAA Gamma (y/n)? [n]

mean?

Thanks,
HBK

---

### Post by aToaster on 2005-02-02
[QUOTE=HBK]Hi,
I've got some questions about the options in fglrxconfig: What do

mean?

Thanks,
HBK[/QUOTE]
 New post started for the new ATI drivers, check it out.

[http://ubuntuforums.org/showthread.php?t=13226&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=13226&page=1&pp=10)

---

### Post by satyam on 2005-02-04
Ok

So I installed fglrx to use my Radeon 9600 XT in Ubuntu. I ran fglrxconfig, and followed instructions from another thread. However, when I run fglrxinfo it's returning a whole lot of stuff about Mesa, which, as I understand it, means that 3d acceleration isn't working.

How can I get the 3d acceleration working?

Thanks.

---

### Post by Shaggy on 2005-02-04
I was able to get mine working.  I actually found someone who had a working Xfreeconfig  file and used his.  Here it is as a reference or just drop it in place of yours.  Remember to back your old one up though.

# **********************************************************************
# DRI Section
# **********************************************************************
Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a

# This is for the touchpad
    Load        "synaptics"

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# If you don't have a floating point coprocessor and emacs, Mosaic or other
# programs take long to start up, try moving the Type1 and Speedo directory
# to the end of this list (or comment them out).
# 

    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"
    FontPath   "unix/:7100"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is 
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
# This allows clients to receive this key event.

#    Option "DontZap"

# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
# sequences.  This allows clients to receive these key events.

#    Option "Dont Zoom"

# Uncomment this to disable tuning with the xvidtune client. With
# it the client can still run and fetch card and monitor attributes,
# but it will not be allowed to change them. If it tries it will
# receive a protocol error.

#    Option "DisableVidModeExtension"

# Uncomment this to enable the use of a non-local xvidtune client. 

#    Option "AllowNonLocalXvidtune"

# Uncomment this to disable dynamically modifying the input device
# (mouse and keyboard) settings. 

#    Option "DisableModInDev"

# Uncomment this to enable the use of a non-local client to
# change the keyboard or mouse settings (currently only xset).

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"Keyboard"
# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option "Xleds"      "1 2 3"

#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"   "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"   "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"  "de"
# or:
#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions" "ctrl:swapcaps"

# These are the default XKB settings for XFree86
#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "us"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""

#    Option "XkbDisable"

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc101"
    Option "XkbLayout"	"us"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************
Section "InputDevice"
	Identifier "Mouse2"
  Option "Device"  "/dev/mouse"
  Option "Emulate3Buttons"
  Driver "synaptics"
  Option  "Protocol"  "auto-dev"
  Option  "LeftEdge"      "1700"
  Option  "RightEdge"     "5300"
  Option  "TopEdge"       "1700"
  Option  "BottomEdge"    "4200"
  Option  "FingerLow" "25"
  Option  "FingerHigh"  "30"
  Option  "MaxTapTime"  "180"
  Option  "MaxTapMove"  "220"
  Option  "VertScrollDelta" "100"
  Option  "MinSpeed"  "0.06"
  Option  "MaxSpeed"  "0.12"
  Option  "AccelFactor" "0.0010"
  Option  "SHMConfig" "on"
EndSection

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/input/mice"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"   "Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection


# **********************************************************************
# Other input device sections 
# this is optional and is required only if you
# are using extended input devices.  This is for example only.  Refer
# to the XF86Config man page for a description of the options.
# **********************************************************************
#
# Section "InputDevice" 
#    Identifier  "Mouse2"
#    Driver      "mouse"
#    Option      "Protocol"      "MouseMan"
#    Option      "Device"        "/dev/mouse2"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball"
#    Driver     "magellan"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "1412"
#    Option     "MaxX"           "15184"
#    Option     "MinY"           "15372"
#    Option     "MaxY"           "1230"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "231"
#    Option     "MaxX"           "3868"
#    Option     "MinY"           "3858"
#    Option     "MaxY"           "272"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonThreshold"    "17"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   31.5       
    VertRefresh 20 - 60
    Option "DPMS"

# === mode lines based on GTF ===
# VGA @ 100Hz
# Modeline "640x480@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync
# SVGA @ 100Hz
# Modeline "800x600@100" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
# XVGA @ 100Hz
# Modeline "1024x768@100" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
# 1152x864 @ 60Hz
# Modeline "1152x864@60" 81.642 1152 1216 1336 1520 864 865 868 895 +hsync +vsync
# 1152x864 @ 85Hz
# Modeline "1152x864@85" 119.651 1152 1224 1352 1552 864 865 868 907 +hsync +vsync
# 1152x864 @ 100Hz
# Modeline "1152x864@100" 143.472 1152 1232 1360 1568 864 865 868 915 +hsync +vsync
# 1280x960 @ 75Hz
# Modeline "1280x960@75" 129.859 1280 1368 1504 1728 960 961 964 1002 +hsync +vsync
# 1280x960 @ 100Hz
# Modeline "1280x960@100" 178.992 1280 1376 1520 1760 960 961 964 1017  +hsync +vsync
# SXGA @ 100Hz
# Modeline "1280x1024@100" 190.960 1280 1376 1520 1760 1024 1025 1028 1085 +hsync +vsync
# SPEA GDM-1950 (60Hz,64kHz,110MHz,-,-): 1280x1024 @ V-freq: 60.00 Hz, H-freq: 63.73 KHz
# Modeline "GDM-1950"  109.62  1280 1336 1472 1720  1024 1024 1026 1062 -hsync -vsync
# 1600x1000 @ 60Hz
# Modeline "1600x1000" 133.142 1600 1704 1872 2144 1000 1001 1004 1035 +hsync +vsync
# 1600x1000 @ 75Hz
# Modeline "1600x1000" 169.128 1600 1704 1880 2160 1000 1001 1004 1044 +hsync +vsync
# 1600x1000 @ 85Hz
# Modeline "1600x1000" 194.202 1600 1712 1888 2176 1000 1001 1004 1050 +hsync +vsync
# 1600x1000 @ 100Hz
# Modeline "1600x1000" 232.133 1600 1720 1896 2192 1000 1001 1004 1059 +hsync +vsync
# 1600x1024 @ 60Hz
# Modeline "1600x1024" 136.385 1600 1704 1872 2144 1024 1027 1030 1060 +hsync +vsync
# 1600x1024 @ 75Hz
# Modeline "1600x1024" 174.416 1600 1712 1888 2176 1024 1025 1028 1069 +hsync +vsync
# 1600x1024 @ 76Hz
# Modeline "1600x1024" 170.450 1600 1632 1792 2096 1024 1027 1030 1070 +hsync +vsync
# 1600x1024 @ 85Hz
# Modeline "1600x1024" 198.832 1600 1712 1888 2176 1024 1027 1030 1075 +hsync +vsync
# 1920x1080 @ 60Hz
# Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
# 1920x1080 @ 75Hz
# Modeline "1920x1080" 211.436 1920 2056 2264 2608 1080 1081 1084 1126 +hsync +vsync
# 1920x1200 @ 60Hz
# Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
# 1920x1200 @ 75Hz
# Modeline "1920x1200" 246.590 1920 2064 2272 2624 1200 1201 1203 1253 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 1400x1050 @ 60Hz M9 Laptop mode 
# ModeLine "1400x1050" 122.000 1400 1488 1640 1880 1050 1052 1064 1082 +hsync +vsync
# 1920x2400 @ 25Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@25" 124.620 1920 1928 1980 2048 2400 2401 2403 2434 +hsync +vsync
# 1920x2400 @ 30Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@30" 149.250 1920 1928 1982 2044 2400 2402 2404 2434 +hsync +vsync

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset     "generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver      "vga"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# installed.

#    BusID       "PCI:0:10:0"

#    VideoRam    256

#    Clocks      25.2 28.3

EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "yes"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=4e50
    Screen 0
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Server Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.

    Screen "Screen0"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "AlwaysCore"
    InputDevice "Mouse2" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

### EOF ###

---

### Post by StacyWebb on 2005-02-08
Here's something interesting. 
I have 3d acceleration by way of fglrxinfo (shows that all is oko) as root (sudo -s)
 but not as a user shows that MESA is still there.
So it says I don't have it any sugesstions?

---

### Post by Anezor on 2005-02-10
ooookey i am a real noob with this linux.. but i have now installed the drivers and want to conf my XF86Config but the file is read only and  idont know how i can edit it when the root account is disabled  :-|  so can some1 please help me  :-)

---

### Post by StacyWebb on 2005-02-10
sudo -s 
then your password
then vi XF86Config-4

---

### Post by amg on 2005-02-11
Hey, I'm following this guide, but get stuck anytime i have to type "fglrxinfo" into a terminal. Or, for that matter, anything graphics related.

It returns one line:

"Trace/breakpoint trap"

Any ideas?

---

### Post by wallijonn on 2005-02-18
[QUOTE=Obi-Lan]Had to compile kernel and fglrx driver. Now works fine. [/QUOTE]

Can you replicate here all the instructions you inserted? (For anyone else that wants to try).

---

### Post by mdr on 2005-02-21
for all those that successfully install and then cannot get Gnome to reset the screen resolution (the infamous xrandr error) then here is the fix as pointed out by 
pagefault. (ta very much btw).

[http://ubuntuforums.org/showthread.php?t=14928](http://ubuntuforums.org/showthread.php?t=14928)

In your XF86Config or Xorg.conf ensure this is included in the Modules section
rather than 
Load extmod
------------------------------
# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
SubSection "extmod"
Option "omit xfree86-dga" # don't initialise the DGA extension
EndSubSection
------------------------------

 :-)

---

### Post by psyko-lefse on 2005-02-23
I've followed the guide, but the mesa-drivers is still running  ](*,) 
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
        Option "UseInternalAGPGART" "no"
EndSection

```
```
morten@morten:~ $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4

```

Whats wrong?

---

### Post by StacyWebb on 2005-02-23
I ran into the same thing what I ended up doing is changing the permissons for my local user to the root group. 
This may be what your running into.
try su to root (or sudo fglrxinfo if you haven't got rid of sudo yet)

Post what comes back.

---

### Post by psyko-lefse on 2005-02-23
morten@morten:~ $ sudo fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4

Same response

---

### Post by StacyWebb on 2005-02-23
did you do 
modprobe fglrx
just  to make sure the module is loaded?

---

### Post by psyko-lefse on 2005-02-23
Still same response.....

---

### Post by Jezze on 2005-02-25
Lets say modprobe says: no such device and I have it installed... what do I do then?

---

### Post by StacyWebb on 2005-02-25
can you post your  XFree86-4 config file?
and also I am assuming you followed the posted instructions on installing it right,
(installing the restricted headers and all those other great things  :D 

also run as root  (or sudo)
cd /etc/
vi modules
(not modules.conf)
and see if fglrx is listed, if it is not add it

Let know if this works

---

### Post by starfarer on 2005-02-25
I have problem on make_install.sh as posted by me here [http://www.ubuntuforums.org/showthread.php?t=16853](http://www.ubuntuforums.org/showthread.php?t=16853).

 I've recreated the symlink using "ln sf /usr/src/linux-headers-2.6.8.1-3-386 /usr/src/linux" . But still no go.

On verge of uninstalling Ubuntu.

---

### Post by StacyWebb on 2005-02-25
should be ln **-s**  /usr/src/linux-headers-2.6.8.1-3-386 /usr/src/linux
 
after you do this the most common thing forgotton is to actually build the kernel
you will need to remove the earlier link and the run the above after you do that

then run as root (or sudo) 
make 
make install
(this will take a long time)
if it asks you to make a new grub config say no actually don't change your current setup
this should take care of any issues you may be having on any apps (such as vmware etc)

---

### Post by psyko-lefse on 2005-02-25
I've followed the guide, but the mesa-drivers is still running  ](*,) 
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
        Option "UseInternalAGPGART" "no"
EndSection

```
```
sudo@morten:~ $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4

```

Dosn't help if I log in as sudo, and fglrx is running.
Didn't have this problem when using the old kernel, 2.6.8, but when I upgraded it to 2.6.10, 3dsupport was gone ](*,) 
Have I missed something during the upgrade? Used synaptics to upgrade the kernel.

---

### Post by starfarer on 2005-02-28
I'm having very bad time. Ok now on make_install i don't get any error because i remove the radeon module using "/sbin/modprobe -r radeon". But after modprobe fglrx i can't start the X and i have to rmmod fglrx!!! to start X which basically means no mesa driver on fglrxinfo. Help!!!

---

### Post by StacyWebb on 2005-02-28
everything that I have stated above is for use with the 2.6.8 kernel, I know that the 2.6.10 kernel has issues with ATI, i wouldn't look for these to be resolved untill the new kernel release (unless you  add  patch)

---

### Post by psyko-lefse on 2005-02-28
Where can I find the nessesary patches?

---

### Post by StacyWebb on 2005-02-28
[http://www.stanchina.net/~flavio/debian/fglrx-archive/msg00180.html](http://www.stanchina.net/~flavio/debian/fglrx-archive/msg00180.html)
Try here.

---

### Post by Pablo928 on 2005-03-13
Just finished reinstalling Ubuntu on my other box. Followed the instructions to the best of my abilities. When I rebooted had no video signal. (Black screen). I'm not real happy. Lost all of my files and about a weeks work setting things up. You might warn people that they are taking a big risk for the sake of 3D harware acceleration. I guess I'll have to boot Windows if I want my video card to work right.

---

### Post by dillweed on 2005-03-16
[QUOTE=Pablo928]Just finished reinstalling Ubuntu on my other box. Followed the instructions to the best of my abilities. When I rebooted had no video signal. (Black screen). I'm not real happy. Lost all of my files and about a weeks work setting things up. You might warn people that they are taking a big risk for the sake of 3D harware acceleration. I guess I'll have to boot Windows if I want my video card to work right.[/QUOTE]
Did you make a copy of you xorg.conf or whatever config you were using?  The easiest way to go back to the way it was before is to restore that config file and it should work.  Always remember to make a backup of the config file before making changings.  I've learned that the hard way.  If anything goes wrong you can always restore.  I hate to be mean but there really is no reason to warn people here if they take the proper precautions.  I've been using linux for 3 years now with my fair share of mishaps and understand your frustations and found that with some searching on the internet, reading and perservance that anything can be fixed without having to reformat.  

Good luck

---

### Post by Drakx on 2005-03-16
Wohooo!!! at last a distro that ive got these ATI Drivers WORKING WITH MU X800 PRO

Thank YOU

drakx@BoX:~ $ glxgears
19525 frames in 5.0 seconds = 3905.000 FPS
14500 frames in 5.0 seconds = 2900.000 FPS
26916 frames in 5.0 seconds = 5383.200 FPS
27484 frames in 5.0 seconds = 5496.800 FPS
drakx@BoX:~ $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 PRO Generic
OpenGL version string: 1.3.4510 (X4.3.0-3.12.0)

drakx@BoX:~ $

drakx@BoX:~ $ fgl_glxgears
3946 frames in 5.0 seconds = 789.200 FPS
4304 frames in 5.0 seconds = 860.800 FPS
4800 frames in 5.0 seconds = 960.000 FPS
4797 frames in 5.0 seconds = 959.400 FPS
4804 frames in 5.0 seconds = 960.800 FPS
4804 frames in 5.0 seconds = 960.800 FPS
drakx@BoX:~ $


Now just to get the sound working on this nForce 2 motherboard

Once again THANK YOU  :grin:  :grin:  :grin:

---

### Post by motuvaa on 2005-03-18
I installed fglrx drivers just like in wiki node.. but I get only 360FPS in fgl_glxgears.. 
in SuSe my graphic card gave me fps ~550

---

### Post by Giblet on 2005-03-19
Do this.
Add the following line to the /etc/modprobe.conf file.
install fglrx /sbin/modprobe --ignore-install fglrx && { /sbin/modprobe nvidia_agp; /bin/true; }

and add the line '/sbin/modprobe fglrx'
to   '/etc/rc.d/rc.modules' 



Hi, alot of people have problems with mesa coming up after they do the install.

The lines above were posted by me about a year ago on linuxquestions.org

They still apply now, usually happens when someone is running an nforce chipset

Just a warning, on some installs under X.org, you need to mount the ram of the card or something strange.

---

### Post by rotorwash on 2005-03-19
Hope this isn't a FAQ... I searched with no resolution.

I have a nforce2 based machine. I looked at the binary drivers howto and it mentioned installing the xfree86-fglrx package. This package is not listed when doing a dpkg -l nor is it listed in synaptic. I have universe and multiverse enabled in my sources.list. There *is* a fglrx-driver package listed that I installed but I get a FATAL: module not found error when using modprobe after a depmod -a. I've searched the forums for fglrx but most of the posts are about successful installs or X config issues. Can someone either point me to the xfree86-fglrx package or give me some pointers on getting the module installed on a nforce2 box? I found some info [here](http://www.ubuntuforums.org/showthread.php?t=3009&page=1&pp=10&highlight=nforce2+fglrx). It mentioned a problem with i686 kernels but then others say they have it working :!:

Linux ubuntu 2.6.8.1-5-k7 #1 Mon Mar 14 22:06:28 UTC 2005 i686 GNU/Linux Warty

---

### Post by Drakx on 2005-03-21
> I have a nforce2 based machine. I looked at the binary drivers howto and it mentioned installing the xfree86-fglrx package. This package is not listed when doing a dpkg -l nor is it listed in synaptic 

Too true but if you open synaptic and search for fglrx it will come up with three options, use that binary

I also have nforce 2 based system and i have tohe x800 pro running with no problems

Hope this helps

---

### Post by Fediuld on 2005-03-21
Hi folks. 
I use hoary. 

I followed the information how to setup my ati from 4 different threads. 

I manage to run it and have 3d support. But when the system informed me that need to do an updateand put new Mesa drivers. Since then even if i tried 6 different kernels with plenty of different setups, Build the ati module (6.8.10) countless times and the xorg.conf too. I do not see something goes wrong. dmesg, lsmod produce the proper information, xorg.0.log the same. I attach them because i'm missing something!. 

As you can see at the end of Xorg.0.log is says that Acceleration is on. But nothing. 
All this time i was working with gentoo. Everything was working fine. First time i tried Ubuntu and i really like it (another friend propose it to me). I have the feeling that's faster than the custom made gentoo i had. 


I tried ck5 and nitro6 kernels just in case i can see any light with them. Nothing

I will really appreciate your help. 

Thank you a lot

Panos. 

PS I use nforce2 motheboard and 9500np Ati graphic card

DMESG

fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[fglrx] module loaded - fglrx 8.10.19 [Feb  9 2005] on minor 0
[fglrx] AGP detected, AgpState   = 0x1f00420a (hardware caps of chipset)
[fglrx] AGP enabled,  AgpCommand = 0x1f004302 (selected caps)
[fglrx] free  AGP = 121909248
[fglrx] max   AGP = 121909248
[fglrx] free  LFB = 122679296
[fglrx] max   LFB = 122679296
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 32768
[fglrx] AGP detected, AgpState   = 0x1f00420a (hardware caps of chipset)
[fglrx] AGP enabled,  AgpCommand = 0x1f004302 (selected caps)
[fglrx] free  AGP = 121909248
[fglrx] max   AGP = 121909248
[fglrx] free  LFB = 122679296
[fglrx] max   LFB = 122679296
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 32768
[fglrx] AGP detected, AgpState   = 0x1f00420a (hardware caps of chipset)
[fglrx] AGP enabled,  AgpCommand = 0x1f004302 (selected caps)
[fglrx] free  AGP = 121909248
[fglrx] max   AGP = 121909248
[fglrx] free  LFB = 122679296
[fglrx] max   LFB = 122679296
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 32768


lsmod


fglrx                 242428  7



xorg.conf - ati senction

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
......

# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
................
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:2:0:0"    # vendor=1002, device=4144
    Screen 0
EndSection




Xorg.0.log


(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 4.3.99.902, module version = 8.10.19
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
.............
(II) Primary Device is: PCI 02:00:0
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(--) Chipset RADEON 9500 (R300 4144) found
(II) resource ranges after xf86ClaimFixedResources() call:
......................
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 2 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "NoAccel" "no"
(**) fglrx(0): Option "NoDRI" "no"
(**) fglrx(0): Option "Capabilities" "0x00008000"
(**) fglrx(0): Option "GammaCorrectionI" "0x00000000"
(**) fglrx(0): Option "GammaCorrectionII" "0x00000000"
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DesktopSetup" "0x00000000"
(**) fglrx(0): Option "MonitorLayout" "AUTO, AUTO"
(**) fglrx(0): Option "HSync2" "unspecified"
(**) fglrx(0): Option "VRefresh2" "unspecified"
(**) fglrx(0): Option "ScreenOverlap" "0"
(**) fglrx(0): Option "IgnoreEDID" "off"
(**) fglrx(0): Option "UseInternalAGPGART" "no"
(**) fglrx(0): Option "Stereo" "off"
(**) fglrx(0): Option "StereoSyncEnable" "1"
(**) fglrx(0): Option "UseFastTLS" "0"
(**) fglrx(0): Option "BlockSignalsOnLock" "on"
(**) fglrx(0): Option "ForceGenericCPU" "no"
(**) fglrx(0): Option "CenterMode" "off"
(**) fglrx(0): Option "FSAAScale" "1"
(**) fglrx(0): Option "FSAAEnable" "no"
(**) fglrx(0): Option "FSAADisableGamma" "yes"
(**) fglrx(0): Option "FSAACustomizeMSPos" "no"
....
(**) fglrx(0): Qbs disabled
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x00000000
(**) fglrx(0): Gamma Correction for II is 0x00000000
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): initializing int10
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(**) fglrx(0): Option "mtrr" "off"
(--) fglrx(0): Chipset: "RADEON 9500 (R300 4144)" (Chipset = 0x4144)
(--) fglrx(0): (PciSubVendor = 0x148c, PciSubDevice = 0x2057)
(--) fglrx(0): board vendor info: third party grafics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd8000000
(--) fglrx(0): MMIO registers at 0xe9000000
(--) fglrx(0): ChipExtRevID = 0x00
(--) fglrx(0): ChipIntRevID = 0x02
(--) fglrx(0): VideoRAM: 131072 kByte (64-bit SDR SDRAM)
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): I2C bus "DDC" initialized.
(II) fglrx(0): Connector Layout from BIOS -------- 
(II) fglrx(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) fglrx(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(**) fglrx(0): MonitorLayout Option: 
	Monitor1--Type AUTO, Monitor2--Type AUTO

(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
..
(**) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(**) fglrx(0): FSAA Gamma disabled
(**) fglrx(0): FSAA Multisample Position is fix
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 4.3.99.902, module version = 8.10.19
	ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(**) fglrx(0): Capabilities: 0x00008000
(**) fglrx(0): cpuFlags: 0x4000000f
(**) fglrx(0): cpuSpeedMHz: 0x0000089d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): using built in AGPGART module: no
(**) fglrx(0): UseFastTLS=0
(**) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
...
(II) fglrx(0): UMM area:     0xd8501000 (size=0x07aff000)
(II) fglrx(0): driver needs XFree86 version: 4.3.x
(WW) fglrx(0): could not detect XFree86 version (query_status=-3)
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID PCI:2:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:2:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8bbc000
(II) fglrx(0): [drm] mapped SAREA 0xf8bbc000 to 0x4024a000
(II) fglrx(0): [drm] framebuffer handle = 0xd8000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.10.19
(II) fglrx(0):     Date: Feb  9 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.8.1-3-k7
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xe9000000
(II) fglrx(0): [agp] Mode=0x1f00420a bridge: 0x10de/0x01e0
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f00430a
(II) fglrx(0): [agp] AGP protocoll is enabled for grafics board. (cmd=0x1f004302)
(II) fglrx(0): [agp] grafics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 28672
(II) fglrx(0): [drm] texture shared area handle = 0xf8dbc000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xd8000000 FBMappedSize: 0x00501000
(II) fglrx(0): FBMM initialized for area (0,0)-(1024,1281)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1024,768) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 768)
(II) fglrx(0): Largest offscreen area available: 1024 x 505
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		24 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x00000001
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(**) fglrx(0): Video overlay enabled on CRTC1
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.
,,,,,
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8bbc000 at 0x4024a000
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) fglrx(0): UMM area:     0xd8501000 (size=0x07aff000)
(II) fglrx(0): driver needs XFree86 version: 4.3.x
(WW) fglrx(0): could not detect XFree86 version (query_status=-3)
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID PCI:2:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:2:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8bbc000
(II) fglrx(0): [drm] mapped SAREA 0xf8bbc000 to 0x4024a000
(II) fglrx(0): [drm] framebuffer handle = 0xd8000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.10.19
(II) fglrx(0):     Date: Feb  9 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.8.1-3-k7
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xe9000000
(II) fglrx(0): [agp] Mode=0x1f00420a bridge: 0x10de/0x01e0
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f00430a
(II) fglrx(0): [agp] AGP protocoll is enabled for grafics board. (cmd=0x1f004302)
(II) fglrx(0): [agp] grafics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 28672
(II) fglrx(0): [drm] texture shared area handle = 0xf8dbc000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xd8000000 FBMappedSize: 0x00501000
(II) fglrx(0): FBMM initialized for area (0,0)-(1024,1281)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1024,768) (front color buffer - assumption)
(II) fglrx(0): Using hardware cursor (scanline 768)
(II) fglrx(0): Largest offscreen area available: 1024 x 505
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x00000001
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(**) fglrx(0): Video overlay enabled on CRTC1
(==) RandR enabled
(II) Mouse1: ps2EnableDataReporting: succeeded
AUDIT: Mon Mar 21 23:22:19 2005: 3107 X: client 7 rejected from local host
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8bbc000 at 0x4024a000
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) fglrx(0): UMM area:     0xd8501000 (size=0x07aff000)
(II) fglrx(0): driver needs XFree86 version: 4.3.x
(WW) fglrx(0): could not detect XFree86 version (query_status=-3)
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID PCI:2:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:2:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8bbc000
(II) fglrx(0): [drm] mapped SAREA 0xf8bbc000 to 0x4024a000
(II) fglrx(0): [drm] framebuffer handle = 0xd8000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.10.19
(II) fglrx(0):     Date: Feb  9 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.8.1-3-k7
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xe9000000
(II) fglrx(0): [agp] Mode=0x1f00420a bridge: 0x10de/0x01e0
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f00430a
(II) fglrx(0): [agp] AGP protocoll is enabled for grafics board. (cmd=0x1f004302)
(II) fglrx(0): [agp] grafics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 28672
(II) fglrx(0): [drm] texture shared area handle = 0xf8dbc000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xd8000000 FBMappedSize: 0x00501000
(II) fglrx(0): FBMM initialized for area (0,0)-(1024,1281)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1024,768) (front color buffer - assumption)
(II) fglrx(0): Using hardware cursor (scanline 768)
(II) fglrx(0): Largest offscreen area available: 1024 x 505
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x00000001
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(**) fglrx(0): Video overlay enabled on CRTC1
(==) RandR enabled
(II) Mouse1: ps2EnableDataReporting: succeeded



fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

---

### Post by rotorwash on 2005-03-22
[QUOTE=Drakx]Too true but if you open synaptic and search for fglrx it will come up with three options, use that binary

I also have nforce 2 based system and i have tohe x800 pro running with no problems

Hope this helps[/QUOTE]
Nope, I installed the packages and get that FATAL: module not found error this is with an ATI AIW 9800 Pro.

---

### Post by Fediuld on 2005-03-22
I found something spooky. 

I install the fglrx drivers, as this and another HOW TO saying. I made a sim link to the ati libGL.so.1.2 for both libGL.so & libGL.so.1 and everything is working perfectly. 
But the spooky thing is that every time i boot the machine those 2 links seeing back the normal libGL from the MESA drivers and they link it!!!!! Is there any way to make the link stable and not force me everytime i boot the machine to change them?? Ok i know how to write a script and put it in the boot loader but i thing that isn't a solution. It should be a way around. 

Ta

Panos.

---

### Post by AvvY on 2005-04-25
I have an ATI 9800+ pro.

I installed the fglrx drivers acoriding to the instructions. then i tried to follow the rest of this guide, but ran into porblems. i couldn't find this: /etc/X11/XF86Config-4 - it doesn't exist.

i had just installed Wolfenstein Enemy Territory and tried to run it but got this error:

> ***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting... 

so i tried what it suggested and ran "et +set r_allowSoftwareGL 1" which loaded Enemy Territory, but it was running uber uber slow. Any ideas of what I should do?

Late,

---

### Post by william_nbg on 2005-05-06
I installed the fglrx drivers for my x600 ati and it seems to work fine. Good bench marks with the fx gears. But after installing a game I like "Descent3" and I after the intro video plays out I get this error message.

Failed to load library [libGL.so].

Descent 3 Message(Error: Failed to load library [libGL.so].
)

System Error


I have these files in my X11R6/lib dir

Any ideas how to fix this problem

thanks

---

### Post by william_nbg on 2005-05-09
Ok, I'm a linux newbie but I'm slowly getting there - thanks to forums and 'how to's like this. thanks to everybody taking part in this.

found the problem myself:

ran the game like this:

descent3 --gllibrary libGL.so.1

Just had to find out which library I was using.

---

### Post by Edgard on 2005-05-20
Does it work with the X800XL series too?  :neutral:  :neutral:  :neutral:

---

### Post by luigi.malago on 2005-06-04
[QUOTE=william_nbg]I installed the fglrx drivers for my x600 ati and it seems to work fine. Good bench marks with the fx gears. [/QUOTE]

Hi, i'm having problems configuring my ATI X600.
Can you post your xconf.org please?
Do you have a ATI X600 PCI express?

thanks,
hope you can help me.

Luigi

---

### Post by maaylix on 2005-08-04
I'm having problems with the very first step. 

After entering:

sudo cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.bak

I get this: 

cp: cannot stat `/etc/X11/XF86Config-4': No such file or directory

I already went through the driver install, and fglrxinfo displays the correct info:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

Am I missing something?

---

### Post by neothewastedone on 2006-02-28
To the op, THANKS MAN. You fricking rock.

---

### Post by mate84 on 2007-10-28
Hello,
I have a Dell vostro 1000 laptop with ATI 1150. In the restricted drivers manager I got this error: xorg-driver-fglrx is missing and after when I install it I get this information: fix broken packages first. And in the terminal:
mate@mate-laptop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed. You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: fglrxinfo: command not found
mate@mate-laptop:~$ sudo apt-get install xorg-driver-fglrx
[sudo] password for mate:
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
xorg-driver-fglrx: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
E: Broken packages
mate@mate-laptop:~$

At the moment I have large icons.....
Can anybody help me?

---


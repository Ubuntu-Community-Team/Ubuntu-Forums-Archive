---
title: "HOWTO: True or Pseudo-Transparent Borderless Pop-up Terminals"
date: 2005-10-25
forum: Outdated Tutorials &amp; Tips
---

### Post by 23meg on 2005-10-25
[SIZE="1"][COLOR="Red"]Last Updated: 08.12.2005[/COLOR][/SIZE]

Transparent terminals are not just sexy eye candy; they also make a lot of sense in terms of GUI usability. Having terminal text appear as if it were on your desktop, or as a transparent pop-up layer that shows other windows beneath it that can be stashed away and recalled with a single click is very handy in daily Gnome usage, where we need the terminal often, but we also want it to blend nicely into the graphical environment, and not take up any desktop space when not needed.

I had already written [a howto]("http://www.ubuntuforums.org/showthread.php?t=38938") on getting pseudo-transparent terminals for Hoary, so the first part of this guide will be essentially identical to that. The second part, however, is for getting true transparency, where you will actually see other windows beneath the terminal, and not just a replication of your underlying desktop as is the case with pseudo-transparency. This requires that you correctly set up the composite extension for X. [poofyhairguy]("http://www.ubuntuforums.org/member.php?u=2381") has written [a detailed guide]("http://www.ubuntuforums.org/showthread.php?t=75527") on setting it up, which I will also partially quote here in the second section. 

[SIZE=3]**Pseudo-Transparent Terminals with Alltray + gnome-terminal**[/SIZE]

Pseudo-transparency only replicates the part of the desktop that's directly underneath your window; as a result, if there's another window in between, it's ignored, and a true sense of depth is not attainable. However, by reserving a space for your window on your workspace, and having no desktop icons in that space, you can put pseudo-transparency to good use. Since our terminal will be a pop-up one that won't take permanent space, this is quite possible. Here's a screenshot:

[[IMG]http://img477.imageshack.us/img477/6602/term8ey.th.jpg[/IMG]]("http://img477.imageshack.us/my.php?image=term8ey.jpg")

[SIZE=3]**1.**[/SIZE] Download Alltray. An Ubuntu deb package is available [here]("http://prdownloads.sourceforge.net/alltray/alltray.ubuntu_0.60-1_i386.deb?download"). See the bottom of this post for an AMD64 build.

[SIZE=3]**2.**[/SIZE] Install the package with dpkg```
sudo dpkg -i /path/to/file/alltray.ubuntu_0.60-1_i386.deb
``` [SIZE=3]**3.**[/SIZE] Set up a new profile in gnome-terminal by hitting Edit / Profiles / New. I'll name it "tterm" here, you can name it whatever you like, but keep in mind that I'll refer to it as "tterm" in all commands in this howto. Edit the profile with the following options: uncheck the "Show menubar by default in new terminals" option in the "General" tab, in the "Effects" tab choose "Transparent Background" and set transparency level as you like, and in the "Scrolling" tab disable the scrollbar.

[SIZE=3]**4.**[/SIZE] Now we'll determine the exact coordinates where your terminal will appear. To do this, launch gnome-terminal with your newly created profile, drag it to where you want it to stay, and type ```
xwininfo
``` The mouse pointer will turn into a crosshair. Click the terminal window, and note first the value that appears in the "Corners:" line.

[SIZE=3]**5.**[/SIZE] Create a launcher with one of the following commands and place it on your desktop or on a menu, or if you want your terminal to be launched on Gnome startup, go to System / Preferences / Session / Startup Programs, click the add button and enter this command there and set the order to something higher than 49.

If you want your terminal to appear in all workspaces, use the following command. 
```
alltray -x -st -g [COLOR=Blue][geometry][/COLOR]"gnome-terminal --window-with-profile=tterm"
``` If you want it to appear fixed in a single workspace, exclude the -st option and use the following command. I recommend this mode, since it allows the terminal to stay anchored in one workspace, and yet you can still call it to your present workspace with a single click on the notification area icon. For short operations you can call it to your present workspace, and if you'll be working with the terminal longer, you can switch to a separate workspace that you've reserved for the terminal. Plus, the terminal will stick to as many workspaces as you want; just pop it up and leave the workspace and it stays there; do the same in another workspace and it stays there too. Once you adopt it, this can become an efficient working habit that will definitely boost usability.```
alltray -x -g [COLOR=Blue][geometry][/COLOR]"gnome-terminal --window-with-profile=tterm"
``` Replace [COLOR=Blue][geometry][/COLOR] with the value you found via xwininfo in the last step, excluding the brackets. If you want the terminal to be shown on startup instead of being hidden, add the -s parameter.

[SIZE=3]**6.**[/SIZE] Add a notification area to your Gnome panel if you don't have one. Now click your launcher or start your Gnome session if you added the command the startup, and you should see the gnome-terminal icon in the notification area. Click it and the terminal will pop up. Click it again, or hit the minimize button and it will be stashed.

That's it. Now on to the more sophisticated true transparent terminal.

[SIZE=3]**True Transparent Terminals with Alltray + gnome-terminal + Composite + transset-df **[/SIZE]

The only way to have true transparency in the X window system as of today is the Composite extension written by Keith Packard. It's in the standard x.org R6 distribution but since it's still experimental and buggy, it isn't enabled by default. As I've stated at the beginning, you can refer to [this howto]("http://www.ubuntuforums.org/showthread.php?t=75527") for detailed info on how to set it up to your liking, but for our purposes, simple client-side compositing with xcompmgr's -n option will be enough. However, if you want to run the extension with all its bells and whistles, without a noticeable performance hit, you'll need a recent NVIDIA card and a fast computer. ATI do not support compositing in their drivers at present, so expect inferior performance with most ATI cards.

Here's a screenshot:

[[IMG]http://img494.imageshack.us/img494/3953/tterm27ja.th.jpg[/IMG]]("http://img494.imageshack.us/my.php?image=tterm27ja.jpg")

[SIZE=3]**1.**[/SIZE] Download Alltray. An Ubuntu deb package is available [here]("http://prdownloads.sourceforge.net/alltray/alltray.ubuntu_0.60-1_i386.deb?download"). See the bottom of this post for an AMD64 build.

[SIZE=3]**2.**[/SIZE] Install the package with dpkg```
sudo dpkg -i /path/to/file/alltray.ubuntu_0.60-1_i386.deb
``` 
[SIZE=3]**3.**[/SIZE] Download and install the X composite manager and the packages required for compiling [transset-df]("http://forchheimer.se/transset-df/"), which is a modified version of the transset tool by Daniel Forchheimer for adjusting window transparency "the bash way" with parameters instead of clicking with the pointer as is the case with transset. Since you'll be compiling from source, make sure you have gcc, make etc. installed. The best way of making sure of this is installing the *build-essential* package, which will install all basic tools you'll need for compilation.```
sudo apt-get install xcompmgr libxcomposite1 libxcomposite-dev libxfixes3 libxfixes-dev libxdamage1 libxdamage-dev libxrender1 libxrender-dev

``` [SIZE=3]**4.**[/SIZE] Download and compile transset-df.```

wget http://forchheimer.se/transset-df/transset-df-4.tar.gz
tar zxf transset-df-4.tar.gz
cd transset-df-4/
make
sudo make install
``` [SIZE=2]*Tip: You can use [checkinstall]("http://asic-linux.com.mx/%7Eizto/checkinstall/") to add  any compiled package into the apt database so that you can see it in Synaptic and perform all apt commands on it. To use it, install it with "sudo apt-get install checkinstall", and replace the last step of the compilation process with "sudo checkinstall".*[/SIZE]

[SIZE=3]**5.**[/SIZE] Modify your xorg.conf file to enable compositing. Add the following lines after the "Modules" section in /etc/X11/xorg.conf```
Section "Extensions"
        Option  "Composite" "Enable"
EndSection
``` 
Add the following to the "Device" section```

        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true" 
``` 
[SIZE=3]**6.**[/SIZE] Add xcompmgr to your Gnome session startup in System / Preferences / Session / Startup Programs. "xcompmgr -n" should do the trick, but if you want more eye candy type "man xcompmgr" for more info on the other parameters. An order of 40 works best for me; if it doesn't, try 0. Again, refer to poofyhairguy's guide if you have any trouble. Now restart X with Ctrl+Alt+Backspace. If it works, go ahead. If something goes wrong and you lose the ability to start x, boot into recovery console and reverse the changes you made. 

[SIZE=3]**7.**[/SIZE] Set up a new profile in gnome-terminal by hitting Edit / Profiles / New. I'll name it "tterm" here, you can name it whatever you like, but keep in mind that I'll keep referring to it as "tterm". Edit the profile with the following options: uncheck the "Show menubar by default in new terminals" option in the "General" tab, set "Dynamically-set title" to "Isn't displayed" in the "Title and Command" tab, and in the "Scrolling" tab disable the scrollbar.

[SIZE=3]**8.**[/SIZE] Now we'll determine the exact coordinates where your terminal will appear. To do this, launch gnome-terminal with your newly created profile, drag it to where you want it to stay, and type ```
xwininfo
``` The mouse pointer will turn into a crosshair. Click the terminal window, and note first the value that appears in the "Corners:" line.

[SIZE=3]**9.**[/SIZE] Launch gedit and paste one of the following scripts into a blank document. ```
#!/bin/bash
alltray -x -st -g [COLOR=Blue][geometry][/COLOR] "gnome-terminal --window-with-profile=tterm" & sleep 1
transset-df -n "tterm (AllTray)"  [COLOR=Red][opacity][/COLOR]  
``` 
This will launch your terminal regardless of whether xcompmgr is running. If it's not running at the time you fire up the terminal, you'll get a pseudo-transparent one. If you want it to be launched only if xcompmgr is running, use the code below instead.```
#!/bin/bash
a=`ps -aef | grep -i xcompmgr | awk ' {if ($8 == "xcompmgr"){printf "2"}} '`
if  [[ $a = "" ]]
then
    exit
else
#!/bin/bash
alltray -x -st -g [COLOR=Blue][geometry][/COLOR] "gnome-terminal --window-with-profile=tterm" & sleep 1
transset-df -n "tterm (AllTray)"  [COLOR=Red][opacity][/COLOR]   

fi

``` You have the option of making your terminal appear in all workspaces, or stay anchored in one workspace and pop up to your present workspace when you click on the icon. If you want it in all workspaces, use the scripts above as they are. For the latter option, remove the -st parameter. Refer to step 5 of the first part of the guide for more info. 

Replace [COLOR=Blue][geometry][/COLOR] with the first "Corners:" value you got with xwininfo, and [COLOR=Red][opacity][/COLOR] with the level of opacity you want on a decimal scale from 0 to 1, excluding the brackets (Note: if for example 0.7 doesn't work, try 0.70; this seems to be a transset-df bug). Save the script with a .sh extension, and make it executable with "chmod +x".

If you want the terminal to be shown on startup instead of being hidden, add the -s parameter.

[SIZE=3]**10.**[/SIZE] Make sure you have a notification area on your Gnome panel. Create a launcher that points to the script or add it to your Gnome session startup in System / Preferences / Session / Startup Programs with an order value higher than 49. Click the launcher or start Gnome, and enjoy.

[SIZE=3]**Troubleshooting**[/SIZE] 

I'll update this part with solutions to problems people seem to be having with the above methods.

- In the second method, if the terminal occasionally pops up in the wrong position or does not have true transparency, try setting a value of 2 or 3 after the "sleep" command in the scripts in step 9.

- [fabs0028]("http://www.ubuntuforums.org/member.php?u=51827") pointed to me that there's no official AMD64 build of Alltray, so here's their build of it, made with checkinstall:

 [Link 1]("http://www.ubuntuforums.org/attachment.php?attachmentid=3793&d=1132670261") **|** [Link 2]("http://rapidshare.de/files/8048724/alltray.tar.gz.html")

- If you're having problems with Alltray 0.60, try 0.62, for which there's an autopackage on the download page.

---

### Post by frodon on 2005-10-25
Transset-df is awesome !

Thanks 23meg for your howto, i love it since i saw it fot the first time in hoary section.

---

### Post by Wolki on 2005-10-25
I get this error if I try to use alltray:

```
** ERROR **: file gnome_theme.c: line 194 (parse_theme): assertion failed: (theme_name)

```

Any ideas?

Also, you can use Devil's Pie to set the translucency of windows; while the setup can be a little more complicated, it doesn't need to be compiled since it's already in universe.

---

### Post by 23meg on 2005-10-25
frodon: Thanks for the feedback, appreciated. 

Wolki: Did you try using another metacity or gtk theme? I also thought about using devilspie, but since transset-df can do the same thing without running as a daemon and residing in memory, it's more logical if you don't already have some other use for devilspie.

---

### Post by Wolki on 2005-10-25
[QUOTE=23meg]Wolki: Did you try using another metacity or gtk theme? I also thought about using devilspie, but since transset-df can do the same thing without running as a daemon and residing in memory, it's more logical if you don't already have some other use for devilspie.[/QUOTE]

I just switched to clearlooks to try it out, and it didn't work either - same error. Also, I doubt I'd switch from Human to something else for Alltray (seems to be a useful app though). Thanks for the help anyway.
Hm yeah, probably. devilspie is rather lightweight, but still overfeatured if all you want is a transparent terminal.

---

### Post by 23meg on 2005-10-25
There's an autopackage of Alltray on the website which is a slightly newer version, maybe you should try that. Do you get that error whenever you launch Alltray, or just with gnome-panel? For me it outputs some error messages on terminal as well, but works nevertheless.

---

### Post by souled on 2005-10-25
Awesome HOWTO, will have to try the transparent stuff later. There is also a way to use Devil's Pie to get a transparent border plus you can make it not appear on the window list. However, I am still having problems with being able to dock it will AllTray and having it skip the window list.

---

### Post by sam hassell on 2005-10-25
Excellent HOW-TO, thanks a lot.

I was wondering if there is a way to force the terminal window to stay on the bottom of the window stack? so that nothing can be put behind it.

Thanks again.

---

### Post by souled on 2005-10-25
> ...stay on the bottom of the window stack?...

There is a way to do it using Devil's Pie. I could help you achieve this if you'd like, but I haven't discovered a way to make Devil's Pie work with All Tray. Meaning you wouldn't be able to dock the terminal. Although, I haven't really experimented that much to make the two work together.

---

### Post by 23meg on 2005-10-26
I've tried the same but the two don't seem to play well with each other; Devil's Pie just won't recognize an Alltray window with any of the matcher flurbs. If I figure out a way of doing that I'll update the howto, but frankly I don't see a great benefit there because this is meant as a pop-up terminal that will appear on your active workspace whenever you want and then disappear when you're done with it.

---

### Post by jr.gotti on 2005-10-26
Just to add on, if you want the size of the terminal to be larger than the default, add the "geometry=##x##"

Example:

```
alltray -x -st -g +554+62  "gnome-terminal --window-with-profile=tterm --geometry=79x38"
```

The previous cod will cause the terminal to be to the right of the screen, with a height to fill the desktop.

Excellent tutorial 23! Been looking for this for awhile!

---

### Post by short4lif2 on 2005-10-26
I had problems with the second tutorial.  I managed to get all the packages, but the following output came out when i tried compiling transset 

> danny@danny:~/transset-df-4$ make
cc -Wall `pkg-config --cflags xcomposite xfixes xdamage xrender` -c transSet.c
/bin/sh: cc: command not found
make: *** [transSet.o] Error 127
danny@danny:~/transset-df-4$ sudo make install
cp transset-df /usr/bin
cp: cannot stat `transset-df': No such file or directory
make: *** [install] Error 1


any ideas?

---

### Post by 23meg on 2005-10-26
make sure you have the package "gcc" installed.

---

### Post by 23meg on 2005-10-26
[QUOTE=pixelPOET]Just to add on, if you want the size of the terminal to be larger than the default, add the "geometry=##x##"

Example:

```
alltray -x -st -g +554+62  "gnome-terminal --window-with-profile=tterm --geometry=79x38"
```

The previous cod will cause the terminal to be to the right of the screen, with a height to fill the desktop.

Excellent tutorial 23! Been looking for this for awhile![/QUOTE]

Thanks for the props and the addition; let me further add that the exact gnome-terminal geometry to use will depend on your screen resolution, so your geometry may not work good on other systems. If you want a non-standard size, it's best to launch a bordered, normal gnome-terminal, resize it to your liking, note the size that's displayed in the middle of the window while you're resizing, and use that for the geometry option. Also, note that this will affect the value you get with xwininfo, so it's best done before probing for the window coordinates.

---

### Post by thestarslookdown on 2005-10-27
I don't know why, but the transparency isn't working.  I did everything in the second tutorial and the terminal will load (in alltray as well), but it won't be transparent.  Anyone know why, or is more infomation needed?

---

### Post by 23meg on 2005-10-28
thestarslookdown: Launch an xterm window and enter

```
transset-df -n "tterm (AllTray)"  0.70  
```

tell me what output this command gives you.

---

### Post by sam hassell on 2005-10-28
> 
Quote:
...stay on the bottom of the window stack?...

There is a way to do it using Devil's Pie. 

Thanks souled, I'll have a look into Devil's Pie when i get some time.

---

### Post by thestarslookdown on 2005-10-28
> No window matching tterm (AllTray) exists!

That's what it says in both a regular xterm and the one launched by the sh file.

---

### Post by 23meg on 2005-10-28
I've forgotten to mention that you have to set the "Dynamically-set title" option in the "Title and Command" tab of your gnome-terminal profile settings to "Isn't displayed". This causes the window to have a static title that doesn't change according to your prompt string. I've updated the guide to correct this mistake, thanks for reporting it.

**Note:** I have also updated step 9 of the second section to allow launching the terminal on the condition that xcompmgr is running.

---

### Post by thestarslookdown on 2005-10-28
I still can't get it to work.  However, if I start a terminal, switch to the tterm profile (which changes the title to tterm), and then do

> transset-df -n "tterm (AllTray)"  0.70

the terminal will become transparent.

---

### Post by 23meg on 2005-10-30
I think your gnome-terminal shortcut isn't launching the terminal with the tterm profile for some reason. Make sure it's started with that profile by checking the syntax of the "--window-with-profile" option. Also try using a higher value with the "sleep" command in the launcher script.

---

### Post by thestarslookdown on 2005-11-03
Raising the value of sleep to 5 made it work.  Thanks.

---

### Post by HJThis on 2005-11-03
Hey,To all

@23meg

I would just like to say thanks for this great thread
did as you & others had posted & wow i can't get over
how much better it makes the desktop look.

please keep up the great work oh by the way
i got this to work with right clicking well almost
just need to find a way to remove the sides of
the Terminal.

Thank you

---

### Post by HJThis on 2005-11-03
Hi,To all

Well just like to say sorry i word that all wrong i did not
find a way one of the members here posted an idea for
adding the Terminal as a right click option

so using part of his idea & your thread
i just about have it working.

Thank you

---

### Post by rjwood on 2005-11-05
I am trying to do this and I am having difficulty understanding one or two things. Just because I'm not yet sure of  proper scripting, but I'm learning.
does this look correct?

#!/bin/bash
alltray -x -st -g +10+46 "gnome-terminal --window-with-profile=tterm" & sleep 3
transset-df -n "tterm (AllTray)"  0.70 

I named the script tterm, is that ok??

I only put the FIRST value of the xwininfo in or should the complete line be there?
I've tried it both way's and can't get it working. 
Also, I don't have xcompmgr in sessions because I have a launcher for it instead. I doubt that makes a difference though.

---

### Post by frodon on 2005-11-05
Why not use a keyboard shortcut ?
You just need to create a shortcut which will run your alltray command, it's what i use to launch my alltray command.
See my [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=79560") if you don't know how create a custom keyboard shortcut.

---

### Post by rjwood on 2005-11-05
Now i am getting this:

rob@ubuntu:~$ cd transset-df-4/
rob@ubuntu:~/transset-df-4$ make
cc -Wall -o transset-df transSet.o dsimple.o `pkg-config --libs xcomposite xfixes xdamage xrender` -lm
Package xrender was not found in the pkg-config search path.
Perhaps you should add the directory containing `xrender.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xrender' found
transSet.o: In function `get_top_window':
transSet.c:.text+0x189): undefined reference to `XQueryTree'
transSet.c:.text+0x1d3): undefined reference to `XQueryTree'
transSet.o: In function `main':
transSet.c:.text+0x63e): undefined reference to `XFetchName'
transSet.c:.text+0x6d9): undefined reference to `XInternAtom'
transSet.c:.text+0x70e): undefined reference to `XGetWindowProperty'
transSet.c:.text+0x72e): undefined reference to `XFree'
transSet.c:.text+0x857): undefined reference to `XInternAtom'
transSet.c:.text+0x871): undefined reference to `XDeleteProperty'
transSet.c:.text+0x88e): undefined reference to `XInternAtom'
transSet.c:.text+0x8ae): undefined reference to `XChangeProperty'
transSet.c:.text+0x8c1): undefined reference to `XSync'
dsimple.o: In function `Open_Display':
dsimple.c:.text+0x1ea): undefined reference to `XOpenDisplay'
dsimple.c:.text+0x201): undefined reference to `XDisplayName'
dsimple.o: In function `Open_Font':
dsimple.c:.text+0x27b): undefined reference to `XLoadQueryFont'
dsimple.o: In function `Beep':
dsimple.c:.text+0x2b2): undefined reference to `XBell'
dsimple.o: In function `ReadBitmapFile':
dsimple.c:.text+0x342): undefined reference to `XReadBitmapFile'
dsimple.o: In function `WriteBitmapFile':
dsimple.c:.text+0x392): undefined reference to `XWriteBitmapFile'
dsimple.o: In function `Resolve_Color':
dsimple.c:.text+0x6ec): undefined reference to `XGetWindowAttributes'
dsimple.c:.text+0x70b): undefined reference to `XParseColor'
dsimple.c:.text+0x737): undefined reference to `XAllocColor'
dsimple.o: In function `Bitmap_To_Pixmap':
dsimple.c:.text+0x785): undefined reference to `XGetGeometry'
dsimple.c:.text+0x7af): undefined reference to `XCreatePixmap'
dsimple.c:.text+0x7db): undefined reference to `XCopyPlane'
dsimple.o: In function `Select_Window':
dsimple.c:.text+0x870): undefined reference to `XCreateFontCursor'
dsimple.c:.text+0x894): undefined reference to `XGrabPointer'
dsimple.c:.text+0x8bc): undefined reference to `XAllowEvents'
dsimple.c:.text+0x8d0): undefined reference to `XWindowEvent'
dsimple.c:.text+0x933): undefined reference to `XUngrabPointer'
dsimple.o: In function `Get_Window_Under_Cursor':
dsimple.c:.text+0x978): undefined reference to `XCreateFontCursor'
dsimple.c:.text+0x99c): undefined reference to `XGrabPointer'
dsimple.c:.text+0x9df): undefined reference to `XQueryPointer'
dsimple.c:.text+0x9ef): undefined reference to `XUngrabPointer'
dsimple.o: In function `Window_With_Name':
dsimple.c:.text+0xa16): undefined reference to `XFetchName'
dsimple.c:.text+0xa5c): undefined reference to `XQueryTree'
dsimple.c:.text+0xac2): undefined reference to `XFree'
dsimple.o: In function `Window_With_Name_Regex_Recurse':
dsimple.c:.text+0xaef): undefined reference to `XFetchName'
dsimple.c:.text+0xb3b): undefined reference to `XQueryTree'
dsimple.c:.text+0xba1): undefined reference to `XFree'
collect2: ld returned 1 exit status
make: *** [transset-df] Error 1
rob@ubuntu:~/transset-df-4$

probably easy for most of you
I know it's pretty much telling me what to do but, I'm not sure how to.
any help would be greatly appriciated.

---

### Post by rjwood on 2005-11-05
nobody has any idea's of how to fix this??

---

### Post by 23meg on 2005-11-05
HJThis: Thanks, glad it worked for you.

rjwood: Your script looks correct; you only need to put the first two numbers you see next to "Corners:" in xwininfo. And the compilation error you're getting seems to be because you haven't installed the required packages. Are you sure you've performed step 3?

(Edit: Oops, possible omission in the guide. I'm not on an Ubuntu machine now so I can't check this but see if there's a package called libxrender1-dev or libxrender-dev and install it if it's missing. Please report if it helped so that I can make the necessary correction.)

---

### Post by rjwood on 2005-11-06
[quote=23meg]HJThis: Thanks, glad it worked for you.

rjwood: Your script looks correct; you only need to put the first two numbers you see next to "Corners:" in xwininfo. And the compilation error you're getting seems to be because you haven't installed the required packages. Are you sure you've performed step 3?

(Edit: Oops, possible omission in the guide. I'm not on an Ubuntu machine now so I can't check this but see if there's a package called libxrender1-dev or libxrender-dev and install it if it's missing. Please report if it helped so that I can make the necessary correction.)[/quote]

Thank you 23meg, I finally got it working with your help. There are actuall 3 or 4 different libxrender selections in synaptic. I checked them all and got the link working. the only problem now, if it is a problem is that when I click the 'tterm' icon that i created it docks ttern a second time with alltray and i have to click the new docked tterm icon to get it working. So, I basically have to click two different icons to get it to show up. Is that normal??

Thanks again for the 'How To' and the attention.:KS

---

### Post by ArukiRei on 2005-11-06
Is there a way to get this running by the script where it doesn't automatically hide. Everytime I run this in the launcher is automatically hides and I have to click on it to show it so the transparency command is executed with it.

---

### Post by 23meg on 2005-11-07
> **rjwood]Thank you 23meg, I finally got it working with your help. There are actuall 3 or 4 different libxrender selections in synaptic. I checked them all and got the link working. the only problem now, if it is a problem is that when I click the 'tterm' icon that i created it docks ttern a second time with alltray and i have to click the new docked tterm icon to get it working. So, I basically have to click two different icons to get it to show up. Is that normal??

Thanks again for the 'How To' and the attention.:KS[/QUOTE]

You're welcome. No, the behavior you describe as I understand it is not normal said:**
> Is there a way to get this running by the script where it doesn't automatically hide. Everytime I run this in the launcher is automatically hides and I have to click on it to show it so the transparency command is executed with it.

I don't exactly follow you; the terminal is meant to launch hidden by default, and to pop up once you click the tray icon. Doesn't it work like this for you? Do you want the terminal to stay on the screen all the time? Please elaborate in clearer terms.

---

### Post by rjwood on 2005-11-07
I wanted to show you 3 different screenshots but, I don't know how to make them thumbnails or whatever they are called. 
When I log into my screen I have one 'terminal' icon set on my panel. When I hold the mouse over it, it say's 'tterm'. If I click it, Another terminal icon appears next to the time on my panel. When I hold the mouse over that one it reads 'tterm'. If I right click on it I get the small menu with alltray (greyed-out)- show/hide-exit-and-undock options. if I click it the terminal appears on the desktop properly, and a 3rd terminal icon appears on the panel labeled 'tterm (Alltray)'. When I type 'exit' in the terminal both the 2nd and 3rd icons disappear. If there is a better/easier way I would love to have it. I also have my ctrl+alt+t keys set for a terminal, perhaps I can link that command to the tterm..

BTW off subject. How do you have different sections of quotes in your reply. I only know how to do one quote.

---

### Post by 23meg on 2005-11-07
[QUOTE=rjwood]I wanted to show you 3 different screenshots but, I don't know how to make them thumbnails or whatever they are called. 
When I log into my screen I have one 'terminal' icon set on my panel. When I hold the mouse over it, it say's 'tterm'. If I chick it, Another terminal icon appears next to the time on my panel. When I hold the mouse over that one it reads 'tterm'. If I right click on it I get the small menu with alltray (greyed-out)- show/hide-exit-and-undock options. if I click it the terminal appears on the desktop properly, and a 3rd terminal icon appears on the panel labeled 'tterm (Alltray)'. When I type 'exit' in the terminal both the 2nd and 3rd icons disappear. If there is a better/easier way I would love to have it. I also have my ctrl+alt+t keys set for a terminal, perhaps I can link that command to the tterm..

[/QUOTE]

Is the script you're using identical to the one you pasted in your post on the previous page? Try removing it from startup and launching it manually and see if you get the same behavior.

[QUOTE=rjwood]
BTW off subject. How do you have different sections of quotes in your reply. I only know how to do one quote.
[/QUOTE]

I just manually wrap portions of the text between quote tags. Perhaps you can also do it by choosing some text and hitting the quote button on top.

---

### Post by ArukiRei on 2005-11-07
[QUOTE=23meg]I don't exactly follow you; the terminal is meant to launch hidden by default, and to pop up once you click the tray icon. Doesn't it work like this for you? Do you want the terminal to stay on the screen all the time? Please elaborate in clearer terms.[/QUOTE]

Sorry for not being so discriptive. I had a problem very similar to thestarlookdown, where I had to set the sleep time high. Mine is set to 3. But my problem is that if I leave the terminal window hidden it seems to not execute the transparancy command. But if I open it, then after 2-3 seconds it goes transparent. It's just and odd error. Thanks for any help :D

---

### Post by 23meg on 2005-11-08
Hmm, that's strange. Try using much shorter (0.x) and longer periods for sleep and also try not touching the tray icon during the sleep period and see if that helps.

---

### Post by ArukiRei on 2005-11-08
Doesn't seem to help. I can't get the terminal to appear borderless if I put it in the startup apps and still can't get it to go transparent unless I unhide it while it put the transparentcy command

---

### Post by 23meg on 2005-11-09
I see; try replacing the last line of the launcher script with this:

```
transset-df -n "AllTray"  [opacity]  
```

and this

```
transset-df -n "tterm"  [opacity]  
```

where tterm is the name of your gnome-terminal profile.

---

### Post by ArukiRei on 2005-11-09
Nope.. doesn't seem to work.

Oh and is there anyway to uninstall the transaparentcy program.. it seem to screw up my flash, crashes firefox anytime i go to a page with flash in it :(

---

### Post by 23meg on 2005-11-09
Of course. Remove the ```
Section "Extensions"
        Option  "Composite" "Enable"
EndSection
``` section from your xorg.conf, and then do```
sudo apt-get remove xcompmgr transset-df-4
```

---

### Post by guyomarj on 2005-11-09
Nice trick :) I used the pseudo-transparent way, and it worked well...

Is there a way not to have the terminal listed in the "window list panel"? And is there a way to bind the terminal to a key?

---

### Post by 23meg on 2005-11-09
[QUOTE=guyomarj]
Is there a way not to have the terminal listed in the "window list panel"? [/QUOTE]
You should be able to do that with [Devil's Pie]("http://www.burtonini.com/blog/computers/devilspie"), theoretically, but I haven't managed to, so I didn't include it in the guide. I don't think this is a significiant problem, since the terminal here is meant as a pop-up one that you'll only open when you need, and hide when you're done. You also have the option of making it appear on only one workspace by removing the -st parameter from the launcher line.

[QUOTE=guyomarj]And is there a way to bind the terminal to a key?[/QUOTE]

Do you mean pressing a key to make Alltray hide/show the window? I don't think this is possible but I'll look into it.

---

### Post by guyomarj on 2005-11-09
[QUOTE=23meg]Do you mean pressing a key to make Alltray hide/show the window? I don't think this is possible but I'll look into it.[/QUOTE]

Yes, I'm kind of lazy :D and thx for the reply, I'll look into Devil's Pie

---

### Post by 23meg on 2005-11-10
[Wolki's guide to Devil's Pie]("http://ubuntuforums.org/showthread.php?t=75749") will let you get started fast if you're interested.

---

### Post by twodogs on 2005-11-19
i'm following directions how to get trans. window. ([https://wiki.ubuntu.com/TransparentTerminals](https://wiki.ubuntu.com/TransparentTerminals))

at 'compile step 3' it does this....

100%[====================================>] 10,071        28.42K/s

18:05:34 (28.34 KB/s) - `transset-df-4.tar.gz' saved [10071/10071]

twodogs@ubuntu:~$  tar zxf transset-df-4.tar.gz cd transset-df-4/
tar: cd: Not found in archive
tar: Error exit delayed from previous errors
twodogs@ubuntu:~$  make
bash: make: command not found
twodogs@ubuntu:~$  sudo make install
sudo: make: command not found
twodogs@ubuntu:~$
twodogs@ubuntu:~$

it will not do the 'make' for some reason.  do you know why?  i'm a noob and still new to linux.  thanks for your help.

---

### Post by fabs0028 on 2005-11-20
Thanx a lot for this great tutorial
I just had to rebuild alltray cause i'm on an amd64 ubuntu but it was perfect.

Anyway really love that transparent terminal on my screen, it is really usefull.

Thanx one more time :)

---

### Post by 23meg on 2005-11-21
[QUOTE=twodogs]i'm following directions how to get trans. window. ([https://wiki.ubuntu.com/TransparentTerminals](https://wiki.ubuntu.com/TransparentTerminals))

at 'compile step 3' it does this....

100%[====================================>] 10,071        28.42K/s

18:05:34 (28.34 KB/s) - `transset-df-4.tar.gz' saved [10071/10071]

twodogs@ubuntu:~$  tar zxf transset-df-4.tar.gz cd transset-df-4/
tar: cd: Not found in archive
tar: Error exit delayed from previous errors
twodogs@ubuntu:~$  make
bash: make: command not found
twodogs@ubuntu:~$  sudo make install
sudo: make: command not found
twodogs@ubuntu:~$
twodogs@ubuntu:~$

it will not do the 'make' for some reason.  do you know why?  i'm a noob and still new to linux.  thanks for your help.[/QUOTE]
You need to enter the commands one by one; you need a space between the following two commands:```
 tar zxf transset-df-4.tar.gz 
cd transset-df-4

```

---

### Post by 23meg on 2005-11-21
[QUOTE=fabs0028]Thanx a lot for this great tutorial
I just had to rebuild alltray cause i'm on an amd64 ubuntu but it was perfect.

Anyway really love that transparent terminal on my screen, it is really usefull.

Thanx one more time :)[/QUOTE]
Happy that it's working for you; I hadn't noticed that there's no AMD64 build of alltray; can you make a deb file of your build with checkinstall? Since it doesn't have any dependencies it should be fine. I can also add a link to it in the guide.

---

### Post by fabs0028 on 2005-11-22
hey not a bad idea at all !
Anyway i allready built it with checkinstall so here is the deb for amd64

---

### Post by 23meg on 2005-11-23
Thanks for contributing, added to the guide.

---

### Post by PenguinZdravko on 2005-11-27
Does the truly transparent effect need nvidia X.Org drivers? And what about the pseudo-transparent? Does it need nvidia drivers?

---

### Post by 23meg on 2005-11-27
The true transparent one will slow down X a lot with most ATI hardware. Check out the composite howto thread linked in the guide for details on what the exceptions are. The pseudo transparent one should work well with all video hardware.

---

### Post by PenguinZdravko on 2005-11-27
I am using nvidia card. But does the truly transparent and pseudo-transparent effects need nvidia drivers, because i'm using nv?

---

### Post by 23meg on 2005-11-27
Yes it does.

---

### Post by nchase on 2005-11-28
I can get this effect to work by using the transset command manually but I cannot get the script I made to work during startup.  I tried making a launcher and that did not work either.

---

### Post by 23meg on 2005-11-28
Please post the exact contents of your script, the order number you used in startup, other apps you launch on startup, and your exact launcher command.

---

### Post by nchase on 2005-11-28
Here is my script:

```
#!/bin/bash
alltray -x -st -g [+5+71] "gnome-terminal --window-with-profile=tterm" & sleep 1
transset-df -n "tterm (AllTray)"  [0.65]

```

In startup I am using order number 48

Other apps lauched on startup:

```
nvidia-settings --load-config-only
order 40
```

```
xcompmgr -fF -I-.002 -O-.003 -D3 -cC -t-5 -l-6 -r5 
order 41
```

```
gdesklets
order 45
```

launcher command:```
/home/username/transscript.sh
```

Thanks in advance. This is really cool stuff.

---

### Post by 23meg on 2005-11-28
It seems your geometry option in the script is incorrect; remove the brackets and just use the bare values. Example script:
```
#!/bin/bash
alltray -x -st -g +907+700 "gnome-terminal --window-with-profile=tterm" & sleep 2
transset-df -n "tterm (AllTray)" 0.85  
```

---

### Post by nchase on 2005-11-28
Oh. Duh! Thank you very much

---

### Post by kozimodo on 2005-11-28
Hi 23meg,

Your guide says that one needs a "recent" nVidia card for true transparency to work.  How recent is recent?  I have a GeForce MX/MX400.

kozimodo

---

### Post by 23meg on 2005-11-28
[quote=kozimodo]Hi 23meg,

Your guide says that one needs a "recent" nVidia card for true transparency to work.  How recent is recent?  I have a GeForce MX/MX400.

kozimodo[/quote]If your card is recent enough to be supported by the closed source Nvidia driver, you should give it a try. You may not get top performance with an MX400 with shadows etc. , but if you just use the -n option it should cut it.

---

### Post by kozimodo on 2005-11-29
Thanks 23meg,

The installation of the nVidia drivers went fine but it crapped out on me once I installed xcompmgr.  Oh well...

kozimodo

---

### Post by nchase on 2005-11-30
Is it possible to drag the terminal window around and retain transparency?

---

### Post by 23meg on 2005-11-30
[QUOTE=nchase]Is it possible to drag the terminal window around and retain transparency?[/QUOTE]
Yes.

kozimodo: Weren't you able start X at all after activating composite?

---

### Post by daedalusman on 2005-12-02
I'm getting this error when I try the make command from step 4 of the true transparency guide.

```
make
cc -Wall `pkg-config --cflags xcomposite xfixes xdamage xrender` -c transSet.c
/bin/sh: cc: command not found
make: *** [transSet.o] Error 127

```

How do I fix this? Thanks

---

### Post by 23meg on 2005-12-02
Make sure you have at least one version of gcc installed. Better yet, install the build-essential package.

---

### Post by daedalusman on 2005-12-02
Well, I made it throught he HOWTO but the transparency doesn't work. Here is my script file...

```
#!/bin/bash
alltray -x -st -g +4+44 "gnome-terminal --window-with-profile=coolterm --geometry=159x58" & sleep 3
transset-df -n "coolterm (AllTray)"  0.10 
```

Also, when I restarted, after adding the "xcompmgr -n" command to startup with order 40, it wouldn't load up Gnome, it just hung on the ubuntu splash logo. Any thoughts on this?

---

### Post by 23meg on 2005-12-03
Why do you specify a --geometry option with your gnome-terminal? Alltray will take care of the window location; try removing that line.

[QUOTE=daedalusman] Also, when I restarted, after adding the "xcompmgr -n" command to startup with order 40, it wouldn't load up Gnome, it just hung on the ubuntu splash logo. Any thoughts on this?[/QUOTE]Did you try 0? If neither work, you'll have to experiment to find a value that works by trial and error.

---

### Post by daedalusman on 2005-12-03
Well I got the transparency to work, I read throught the vista-ish affects howto and that got it going. And I think I'm not going to have it start when the system starts, I got that working too, but since its so buggy and crashes a lot I'm going to set up a script file. That way I can start and stop it easily. Thanks for the help and a great howto, its some really cool stuff and I can't wait for this to get farther along in development. Its going to rock when its more stable.

---

### Post by 23meg on 2005-12-03
Happy to know you got it working. The toggle script is really useful for switching off composite when it's not needed.

Also check out the new build of xcompmgr in that thread which will probably help with stability.

---

### Post by 23meg on 2005-12-07
Guide updated, with options to make the terminal appear on all workspaces or keep it in one workspace and make it pop up to the present workspace on click, more troubleshooting info and minor corrections.

---

### Post by mentos on 2005-12-09
hi there... first post for me here :)

```
mentos@jason:~/transset-df-4/transset-df-4$ make
cc -Wall `pkg-config --cflags xcomposite xfixes xdamage xrender` -c transSet.c
transSet.c:14:19: error: stdio.h: No such file or directory
In file included from transSet.c:15:
/usr/include/X11/Xlib.h:52:23: error: sys/types.h: No such file or directory
In file included from transSet.c:17:
dsimple.h:42:19: error: regex.h: No such file or directory
In file included from transSet.c:17:
dsimple.h:99: error: syntax error before ‘regex_t’
transSet.c:18:20: error: stdlib.h: No such file or directory
transSet.c:19:20: error: getopt.h: No such file or directory
transSet.c:20:20: error: string.h: No such file or directory
transSet.c: In function ‘usage’:
transSet.c:30: warning: implicit declaration of function ‘fprintf’
transSet.c:30: warning: incompatible implicit declaration of built-in function ‘fprintf’
transSet.c:30: error: ‘stderr’ undeclared (first use in this function)
transSet.c:30: error: (Each undeclared identifier is reported only once
transSet.c:30: error: for each function it appears in.)
transSet.c:60: warning: implicit declaration of function ‘exit’
transSet.c:60: warning: incompatible implicit declaration of built-in function ‘exit’
transSet.c: In function ‘main’:
transSet.c:108: error: array type has incomplete element type
transSet.c:129: warning: implicit declaration of function ‘getopt_long’
transSet.c:145: warning: implicit declaration of function ‘malloc’
transSet.c:145: warning: incompatible implicit declaration of built-in function ‘malloc’
transSet.c:145: warning: implicit declaration of function ‘strlen’
transSet.c:145: warning: incompatible implicit declaration of built-in function ‘strlen’
transSet.c:145: error: ‘optarg’ undeclared (first use in this function)
transSet.c:167: warning: implicit declaration of function ‘atof’
transSet.c:173: warning: incompatible implicit declaration of built-in function ‘fprintf’
transSet.c:173: error: ‘stderr’ undeclared (first use in this function)
transSet.c:174: warning: incompatible implicit declaration of built-in function ‘exit’
transSet.c:181: error: ‘optind’ undeclared (first use in this function)
transSet.c:190: warning: implicit declaration of function ‘printf’
transSet.c:190: warning: incompatible implicit declaration of built-in function ‘printf’
transSet.c:194: warning: incompatible implicit declaration of built-in function ‘printf’
transSet.c:195: warning: implicit declaration of function ‘sscanf’
transSet.c:195: warning: incompatible implicit declaration of built-in function ‘sscanf’
transSet.c:199: warning: incompatible implicit declaration of built-in function ‘fprintf’
transSet.c:200: warning: incompatible implicit declaration of built-in function ‘exit’
transSet.c:208: warning: incompatible implicit declaration of built-in function ‘printf’
transSet.c:216: warning: incompatible implicit declaration of built-in function ‘fprintf’
transSet.c:217: warning: incompatible implicit declaration of built-in function ‘exit’
transSet.c:246: warning: implicit declaration of function ‘memcpy’
transSet.c:246: warning: incompatible implicit declaration of built-in function ‘memcpy’
transSet.c:248: warning: incompatible implicit declaration of built-in function ‘printf’
transSet.c:283: warning: incompatible implicit declaration of built-in function ‘printf’
transSet.c:108: warning: unused variable ‘long_options’
transSet.c:108: error: storage size of ‘long_options’ isn’t known
make: *** [transSet.o] Error 1
mentos@jason:~/transset-df-4/transset-df-4$ sudo make install
cp transset-df /usr/bin
cp: cannot stat `transset-df': No such file or directory
make: *** [install] Error 1
mentos@jason:~/transset-df-4/transset-df-4$

```

i'm new to linux but i followed everystep carrefully and that is what i get at step 4... what am i doing wrong?

tnx in advance :);)

---

### Post by 23meg on 2005-12-10
I think it's just that you've gone one directory too deep with the cd command. Make sure that you're in the transset-df-4/ folder where you've extracted all the necessary files. You can verify whether the files are there with the "ls" command.

If confused by the command line, you can just double click on the archive file you've downloaded, extract the files via drag and drop to a temporary folder, change your working directory in the command line to that folder (with "cd") and issue the make command there.

---

### Post by SpEcIeS on 2005-12-14
Whenever I use xcompmgr my screen locks up. Everything but the mouse. :confused: 

Does anyone have any idea why?

---

### Post by 23meg on 2005-12-14
[QUOTE=SpEcIeS]Whenever I use xcompmgr my screen locks up. Everything but the mouse. :confused: 

Does anyone have any idea why?[/QUOTE]
What's your video hardware? Which driver are you using? Which options are you using xcompmgr with?

---

### Post by SpEcIeS on 2005-12-14
[QUOTE=23meg]What's your video hardware? Which driver are you using? Which options are you using xcompmgr with?[/QUOTE]
I have a nVidia Geforce4 MX 4000 128MG and the nvidia drivers that come with Ubuntu. Now as far as the xcompmgr, loading straight. :)

Thanks for the help. :D

---

### Post by 23meg on 2005-12-14
Did you try the proprietary Nvidia drivers? Maybe you should; check that your card is supported though. 

For xcompmgr settings, refer to [this thread]("http://www.ubuntuforums.org/showthread.php?t=75527"). Try running it with the -n option first, and if you're not, try running it on Gnome startup; it works more reliably that way. If everything fails, try the new version of xcompmgr that you can find in the thread I linked to.

---

### Post by SpEcIeS on 2005-12-14
Thanks :) I will give it a go, but as far as the drivers are concerned..  they seem to work fine, the ones downloaded with apt.

When my system locks up, upon loading xcompmgr, the windows shadow, but screen lockup happens without gnome-panel visable. The mouse works, but the keyboard is dead, so I cannot exit. I have to manual reboot, however upon thinking, I should ssh into the box and see if I can terminate the X server.

---

### Post by 23meg on 2005-12-14
> the ones downloaded with apt.Do you mean nvidia-glx? If so you're already running the proprietary drivers, which will work better with composite anyway.

Maybe you should post your problems in the composite manager thread. And try the other xcompmgr options.

---

### Post by SpEcIeS on 2005-12-14
Actually it is the legacy drivers, however the fading portion of the xcompmgr works, aside from when I use log out which locks up the screen, but now I am using the -n option. This seems to help, but I will find out when I go to log out.

The fading menus look nice and the overall windowing performance has been increased. 

Also, using gcompmgr, fading a window is really nice. :)

_**Edit**_
Fading and tranparency works great, but when I log out the screen locks up. On another note, it just locks up my screen and not my keyboard; it would seem that my left Ctrl key is a little weak. :)

---

### Post by 23meg on 2005-12-14
Good to know it helped you. The logout bug is a known one. It's not a real lockup, if you press esc you can get back to gnome, it's just that the dialog box becomes invisible.

---

### Post by SpEcIeS on 2005-12-14
I found out why the screen locks up on log out:
[b]
################## IMPORTANT BUG NOTES ########################
Due to some kind of bug with Gnome and xcompmgr, if you have xcompmgr enabled 
and you click on Actions->Log Out, your window manager will freeze.
You can safely shutdown by opening a terminal, and entering
shutdown 0 -h
[/b]
This was included in the gcompmgr software.

If I use the shadowing features the system does lockup, but not the mouse. This IS including the keyboard. However, any problems playing with transparency only locks the screen.

The shadowing features look really nice, but it does not seem to want to work on my card, successfully. :) :confused:

---

### Post by 23meg on 2005-12-14
Some cards, especially older ones, are unlucky with composite. Perhaps the best you can do at the moment is experiment with the xcompmgr settings, and install the new xcompmgr version in place of the one shipped with Ubuntu.

---

### Post by TeeAhr1 on 2005-12-19
Well, I love it, it looks sexy as hell!  But...since I set it up, I've been having odd behavior from GNOME.  For instance, my logout screen has become invisible.  It's still there somewhere, because I can use the keys to select options within it, but I can't see it.

Also, GNOMEHelp is gone (not invisible, gone).  I don't see how this could possibly be related, but it all seemed to happen at the same time.

Granted, I don't know what's causing all this weirdity, but I think the only way to really figure out what's wrong is to revert my changes and reinstall GNOME.  If anyone could help me out with (sob) removing this, I'd be most grateful.  (I'm using true transparency, btw).  If anyone else has had the same problems and could share a little insight, I'd love to hear all about it.  Thx in advance, y'all!

---

### Post by 23meg on 2005-12-19
> Well, I love it, it looks sexy as hell! But...since I set it up, I've been having odd behavior from GNOME. For instance, my logout screen has become invisible. It's still there somewhere, because I can use the keys to select options within it, but I can't see it.
It's a known bug with the composite extension. You'll have to live with it. Check the composite thread I linked to for workarounds.

> Also, GNOMEHelp is gone (not invisible, gone). I don't see how this could possibly be related, but it all seemed to happen at the same time.Do you mean it's in the System menu, yet nothing happens when you click it? I can't see how it could be related either; it was probably caused by something else.

---

### Post by TeeAhr1 on 2005-12-20
> **23meg]It's a known bug with the composite extension. You'll have to live with it. Check the composite thread I linked to for workarounds.[/QUOTE]
:oops: That's what I get for not reading the whole thread.  Thx, sorry about that...
[QUOTE=23meg]Do you mean it's in the System menu, yet nothing happens when you click it? I can't see how it could be related either said:**
> 
Yeah, it's peculiar.  Depending on where I am when I try to access it, I either get this:
[QUOTE=error]There was an error displaying help: There was an error launching the default action command associated with this location.
or no response at all.  Yeah, like I said, I can't imagine the two things being related, I just found it odd that they both happened at the same time...:confused:

EDIT/ADD: Sorry if I'm getting off-topic, but if I reinstall GNOME without removing the changes I made for the transparent terminal, it should still work, correct??

---

### Post by 23meg on 2005-12-20
[QUOTE=TeeAhr1]EDIT/ADD: Sorry if I'm getting off-topic, but if I reinstall GNOME without removing the changes I made for the transparent terminal, it should still work, correct??
[/QUOTE]Yes, since they're X related. I suggest reinstalling the package "yelp" and doing a few searches and asking for help before attempting to reinstall Gnome.

---

### Post by fannymites on 2005-12-20
I've just got around to trying this and it's great but I'm just wondering if it's possible to launch the terminal unhidden?
I have it running on startup so it's already in the tray but I often need to use another terminal so I'd like it run hidden on startup but use a slightly different script when run from a launcher so it's unhidden.

---

### Post by 23meg on 2005-12-20
Pass the -s parameter to alltray to make it show the window on start.

---

### Post by TeeAhr1 on 2005-12-20
Another workaround for the 'invisible logout screen' bug: Ctrl-Alt-Bkspace (IIRC?) backs you out to the login, from which you can choose any option you wish.

---

### Post by 23meg on 2005-12-20
I prefer to create individual reboot and shutdown shortcuts in the panel or the desktop with the "shutdown" command. ```
man shutdown
```

---

### Post by Liquibyte on 2005-12-21
Just so you know.  I have almost gotten this working in KDE and Konsole.

---

### Post by 23meg on 2005-12-21
Cool; if you had to do something essentially different, how about posting it here, so that I can add it to the guide as well? And why "almost"; what's missing?

---

### Post by Liquibyte on 2005-12-21
Well, most of it works but I have a few questions about the script.  Actually I have one now and more later if now doesn't answer what I need to know.

can I take this:
```

#!/bin/bash
a=`ps -aef | grep -i xcompmgr | awk ' {if ($8 == "xcompmgr"){printf "2"}} '`
if  [[ $a = "" ]]
then
    exit
else
#!/bin/bash
alltray -x -st -g [geometry] "gnome-terminal --window-with-profile=tterm" & sleep 1
transset-df -n "tterm (AllTray)"  [opacity]   
fi
```

and do this:
```

#!/bin/bash
a=`ps -aef | grep -i xcompmgr | awk ' {if ($8 == "xcompmgr"){printf "2"}} '`
if  [[ $a = "" ]]
then
    xcompmgr -n
else
#!/bin/bash
alltray -x -st -g [geometry] "gnome-terminal --window-with-profile=tterm" & sleep 1
transset-df -n "tterm (AllTray)"  [opacity]   
fi

```

to start xcompmgr if it isn't running?

I have done this:

```

alltray -x -st -g [geometry] "gnome-terminal --window-with-profile=tterm" & sleep 1
xcompmgr -n
transset-df -n "tterm (AllTray)"  [opacity]

```

and if xcompmgr isn't running it will work.  Otherwise I have to
```
transset-df -n "tterm (AllTray)"  [opacity]
```
in the Konsole.

I also have a problem with the script actually starting AllTray altogether, it will only load when I manually start Konsole.  Another quirk is that all Konsole variations, regardless of title, will load in the specified position.  None will default to the true transparency unless it is the first initialized, with the exception of root which won't at all.  One more thing, the AllTray icon will only lower and raise the window once (I have the -s option enabled, but the reverse is also true).

---

### Post by 23meg on 2005-12-21
The second script will launch xcompmgr if it's not running, but will stop there and not run the terminal. If you wanted the terminal too, you'd have to do ```
#!/bin/bash
a=`ps -aef | grep -i xcompmgr | awk ' {if ($8 == "xcompmgr"){printf "2"}} '`
if  [[ $a = "" ]]
then
    xcompmgr -n
    alltray -x -st -g [geometry] "gnome-terminal --window-with-profile=tterm" & sleep 1
    transset-df -n "tterm (AllTray)"  [opacity]  
else
    alltray -x -st -g [geometry] "gnome-terminal --window-with-profile=tterm" & sleep 1
    transset-df -n "tterm (AllTray)"  [opacity]   
fi
```The third script you've pointed to is only meant to work with xcompmgr anyway; it's in the second (true transparency) part of the guide. If you wanted a pseudo-transparent one you don't need a script; you can just refer to one of the commands in step 5 of the first part of the guide.

I haven't used Konsole at all, but what I figure is that Alltray isn't able to place it with its geometry option to the correct place. Can you tell me the exact command line you use to do this?

---

### Post by Liquibyte on 2005-12-22
Basically this is what I started with to get true transparency:

```
#!/bin/bash

## --borderless --sticky --show --geometry 
alltray -x -st -s -g +714+0 "konsole --window-with-profile=Liquibyte - Konsole" & sleep 5
## --Normal client-side compositing with transparency support
xcompmgr -n
## --name
transset-df -n "Liquibyte - Konsole (AllTray)"  0.70
```

True transparency works with this the first time it's started thereafter I have to enter the transparency part again manually, i.e.

```
transset-df -n "Liquibyte - Konsole (AllTray)"  0.70
```

---

### Post by 23meg on 2005-12-25
It works only the first time you start Konsole and doesn't work in consequent attempts after you shut it down once? Or does it work in the first terminal you start and not in consequent ones you run simultaneously?

Try not using a space in your Konsole profile name; make it something simple like "tterm".

---

### Post by NightBlade40 on 2006-01-20
Good guide, using this in xfce 4.2.2 and it works and looks great. I have a slight problem though, it seems that I can only initiate the transparent terminal from an ordinary terminal. Trying to run the script from a launcher or placing it in ~/Desktop/Autostart doesn't do anything, and if I leave the transparent terminal open when logging out (saving the session) and logging back in I get an ordinary terminal on startup. Here is my tterm script in case it might help anything:

```
#!/bin/bash
alltray -x -st -g +457+387 "gnome-terminal --window-with-profile=tterm" & sleep 1
transset-df -n "tterm (AllTray)"  0.70
```

---

### Post by babygigi on 2006-01-23
Hum... everytime i try this no matter with what this happens

gigi@ubuntu:~$ xcompmgr -n
No composite extension

Any Help?

---

### Post by babygigi on 2006-01-23
Yes i did... where do i find what my video hardware is?

---

### Post by babygigi on 2006-01-23
Intel Corperation 82815 CGC [Chipset Graphics Controller] I think... do i need the NVIDIA Card?

---

### Post by 23meg on 2006-01-23
[QUOTE=NightBlade40]Good guide, using this in xfce 4.2.2 and it works and looks great. I have a slight problem though, it seems that I can only initiate the transparent terminal from an ordinary terminal. Trying to run the script from a launcher or placing it in ~/Desktop/Autostart doesn't do anything, and if I leave the transparent terminal open when logging out (saving the session) and logging back in I get an ordinary terminal on startup. Here is my tterm script in case it might help anything:

```
#!/bin/bash
alltray -x -st -g +457+387 "gnome-terminal --window-with-profile=tterm" & sleep 1
transset-df -n "tterm (AllTray)"  0.70
```[/QUOTE]
Nothing seems wrong with your script; did you make it executable?

---

### Post by 23meg on 2006-01-23
[QUOTE=babygigi]Hum... everytime i try this no matter with what this happens

gigi@ubuntu:~$ xcompmgr -n
No composite extension

Any Help?[/QUOTE]
Did you enable the composite extension the way I described in step 5? If so, what's your video hardware?

---

### Post by NightBlade40 on 2006-01-24
[QUOTE=23meg]Nothing seems wrong with your script; did you make it executable?[/QUOTE]

Yep, perhaps I should elaborate on my last post. I run my script from an already open ordinary terminal, it successfully runs and gives me a working terminal icon in the xfce icon tray. Running the same script using a launcher or putting a copy of it in ~/Desktop/Autostart doesn't give my any terminal tray icon or any indication that the program successfully executed at all. Maybe I have to do something special with xfce?

---

### Post by jerome bettis on 2006-02-03
THANK YOU .. BEST HOW TO EVER

alltray owns.  i'm looking into using wmctrl to hide the terminal on the taskbar, i think it can be done - i used it to do this with aterm in fluxbox.

\\:D/

---

### Post by jerome bettis on 2006-02-03
well it sorta works

wmctrl -i -r `wmctrl -l | grep "(AllTray)" | awk '{ print $1 }'` -b toggle,skip_taskbar

that works until you click the icon on the system tray to bring it back, then the taskbar thing comes with it.  i'm gonna look at the alltray source and see if i can make that command execute when the icon is clicked.  maybe i'll make a litte checkbox on the menu to show / hide the taskbar icon.

also this assumes there is only one window using all tray open.  i'll have to think of a way around that later, i think wmctrl suppors using PIDs.

---

### Post by jerome bettis on 2006-02-03
ok there is no need to do anything like that

i downloaded the source for alltray, made a few small changes and it no longer shows anything in the taskbar.

in src/utils.c, comment out the if statements on lines 1908 and 1919, so skip_tasklist() gets called no matter what.  also change FALSE to TRUE on line 1920.

do ./configure && make && make install and that's that \\:D/.  not the best solution but a quick and easy one that works just fine for me.  any questions post here or PM me and i'll explain better.

---

### Post by sYs^ on 2006-03-17
is it possible to stick the terminal to the background?
and is it possible to use alltray with option -s and hide the terminal from the tasklist?

btw, great howto, it's working almost perfectly

---

### Post by glowplug on 2006-03-27
thanks 23meg, great howto 

transparent terminal came in handy already...

...would have been really useful for reading/typing this..err...one...err...suppose that's illogical [img]http://ubuntuforums.org/images/smilies/eusa_think.gif[/img]

---

### Post by kh4nh on 2006-04-01
Hi guys,

I am not sure why, but it is not stable on my system. Sometimes i got a transparent terminal. And most of the time I got a white terminal as the thumbnail below. 

Could 23meg or anyone help me, thanks for your time


[[IMG]http://img152.imageshack.us/img152/2083/screenshot2pm.th.png[/IMG]]("[URL=http://img152.imageshack.us/my.php?image=screenshot2pm.png)"][[IMG]http://img152.imageshack.us/img152/2083/screenshot2pm.th.png[/IMG]](http://img152.imageshack.us/my.php?image=screenshot2pm.png)[/URL]


here is my script:
==============
#!/bin/bash
alltray -x -st -g +97+110 "gnome-terminal --window-with-profile=tterm" & sleep 2
transset-df -n "tterm (AllTray)" 0.35

---

### Post by zwiebug on 2006-04-04
call me stupid, but how do i build a launcher that automatically opens up two or more of these consoles? i tried to do a "gedit /home/me/tterm.sh" and putting in "alltray ......... for terminal one" , then next line "alltray ......for terminal two next to terminal one" and starting that script as a launcher in the panel. doesn't work. opens up only the first terminal.

---

### Post by hkspowers on 2006-04-11
Hello everyone, I am a noob at linux but not to computers.  Anyway I tried this script but I get this error.  

james@ubuntu:~$  tar zxf transset-df-4.tar.gz cd transset-df-4/
tar: cd: Not found in archive
tar: Error exit delayed from previous errors
james@ubuntu:~$  tar zxf transset-df-4.tar.gz
james@ubuntu:~$ cd transset-df-4/
james@ubuntu:~/transset-df-4$ make
cc -Wall `pkg-config --cflags xcomposite xfixes xdamage xrender` -c transSet.c
transSet.c:14:19: error: stdio.h: No such file or directory
In file included from transSet.c:15:
/usr/include/X11/Xlib.h:52:23: error: sys/types.h: No such file or directory
In file included from transSet.c:17:
dsimple.h:42:19: error: regex.h: No such file or directory
In file included from transSet.c:17:
dsimple.h:99: error: syntax error before ‘regex_t’
transSet.c:18:20: error: stdlib.h: No such file or directory
transSet.c:19:20: error: getopt.h: No such file or directory
transSet.c:20:20: error: string.h: No such file or directory
transSet.c: In function ‘usage’:
transSet.c:30: warning: implicit declaration of function ‘fprintf’
transSet.c:30: warning: incompatible implicit declaration of built-in function ‘fprintf’
transSet.c:30: error: ‘stderr’ undeclared (first use in this function)
transSet.c:30: error: (Each undeclared identifier is reported only once
transSet.c:30: error: for each function it appears in.)
transSet.c:60: warning: implicit declaration of function ‘exit’
transSet.c:60: warning: incompatible implicit declaration of built-in function ‘exit’
transSet.c: In function ‘main’:
transSet.c:108: error: array type has incomplete element type
transSet.c:129: warning: implicit declaration of function ‘getopt_long’
transSet.c:145: warning: implicit declaration of function ‘malloc’
transSet.c:145: warning: incompatible implicit declaration of built-in function ‘malloc’
transSet.c:145: warning: implicit declaration of function ‘strlen’
transSet.c:145: warning: incompatible implicit declaration of built-in function ‘strlen’
transSet.c:145: error: ‘optarg’ undeclared (first use in this function)
transSet.c:167: warning: implicit declaration of function ‘atof’
transSet.c:173: warning: incompatible implicit declaration of built-in function ‘fprintf’
transSet.c:173: error: ‘stderr’ undeclared (first use in this function)
transSet.c:174: warning: incompatible implicit declaration of built-in function ‘exit’
transSet.c:181: error: ‘optind’ undeclared (first use in this function)
transSet.c:190: warning: implicit declaration of function ‘printf’
transSet.c:190: warning: incompatible implicit declaration of built-in function ‘printf’
transSet.c:194: warning: incompatible implicit declaration of built-in function ‘printf’
transSet.c:195: warning: implicit declaration of function ‘sscanf’
transSet.c:195: warning: incompatible implicit declaration of built-in function ‘sscanf’
transSet.c:199: warning: incompatible implicit declaration of built-in function ‘fprintf’
transSet.c:200: warning: incompatible implicit declaration of built-in function ‘exit’
transSet.c:208: warning: incompatible implicit declaration of built-in function ‘printf’
transSet.c:216: warning: incompatible implicit declaration of built-in function ‘fprintf’
transSet.c:217: warning: incompatible implicit declaration of built-in function ‘exit’
transSet.c:246: warning: implicit declaration of function ‘memcpy’
transSet.c:246: warning: incompatible implicit declaration of built-in function ‘memcpy’
transSet.c:248: warning: incompatible implicit declaration of built-in function ‘printf’
transSet.c:283: warning: incompatible implicit declaration of built-in function ‘printf’
transSet.c:108: warning: unused variable ‘long_options’
transSet.c:108: error: storage size of ‘long_options’ isn’t known
make: *** [transSet.o] Error 1
james@ubuntu:~/transset-df-4$ sudo make install
cp transset-df /usr/bin
cp: cannot stat `transset-df': No such file or directory
make: *** [install] Error 1
james@ubuntu:~/transset-df-4$

my hardware is a dual xeon with ht, 32bit and I have a Nvidia Quadro FX 3000.  

can anybody tell me what i am doing wrong?

thanks in advance,
James

---

### Post by 23meg on 2006-04-14
[QUOTE=hkspowers]Hello everyone, I am a noob at linux but not to computers.  Anyway I tried this script but I get this error.  

james@ubuntu:~$  tar zxf transset-df-4.tar.gz cd transset-df-4/
tar: cd: Not found in archive[/quote]

You need to break that line up before the "cd" part; it's actually two separate lines of commands. First copy and paste the "tar zxf transset-df-4.tar.gz" part, hit enter, and then do the same for "cd transset-df-4/".

---

### Post by 23meg on 2006-04-14
[QUOTE=zwiebug]call me stupid, but how do i build a launcher that automatically opens up two or more of these consoles? i tried to do a "gedit /home/me/tterm.sh" and putting in "alltray ......... for terminal one" , then next line "alltray ......for terminal two next to terminal one" and starting that script as a launcher in the panel. doesn't work. opens up only the first terminal.[/QUOTE]

Simply inserting two separate lines of the alltray command should work. The following worked for me:
```

#!/bin/bash
alltray -x -st -g +907+700 "gnome-terminal --window-with-profile=tterm" & sleep 2
alltray -x -st -g +907+700 "gnome-terminal --window-with-profile=tterm" & sleep 2
transset-df -n "tterm (AllTray)" 0.85  

```

---

### Post by 23meg on 2006-04-14
[QUOTE=kh4nh]Hi guys,

I am not sure why, but it is not stable on my system. Sometimes i got a transparent terminal. And most of the time I got a white terminal as the thumbnail below. 

Could 23meg or anyone help me, thanks for your time
[/QUOTE]
Your script seems to work fine over here. Did you try playing with the "sleep" value? Start by trying 3 instead of 2 and experiment with other close values and see if that helps.

---

### Post by curiita on 2006-04-15
well, i get this error

> root@portatil:/home/curiita/Desktop/downloads# sudo dpkg -i alltray.ubuntu_0.60-1_i386.deb
(Reading database ... 61356 files and directories currently installed.)
Preparing to replace alltray 0.60-1 (using alltray.ubuntu_0.60-1_i386.deb) ...
Unpacking replacement alltray ...
Setting up alltray (0.60-1) ...
root@portatil:/home/curiita/Desktop/downloads# sudo apt-get install xcompmgr libxcomposite1 libxcomposite-dev libxfixes3 libxfixes-dev libxdamage1 libxdamage-dev libxrender1 libxrender-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xcompmgr

any help?

---

### Post by sYs^ on 2006-04-15
_Package **xcompmgr**_

    * hoary (x11): X composition manager [[COLOR="Red"]universe[/COLOR]]
      1.1.1+cvs.20041109-0ubuntu2: amd64 i386 powerpc
    * breezy (x11): X composition manager [[COLOR="Red"]universe[/COLOR]]
      1.1.1+cvs.20041109-0ubuntu2: amd64 i386 powerpc
    * dapper (x11): X composition manager [[COLOR="Red"]universe[/COLOR]]
      1.1.1+cvs.20041109-0ubuntu2: amd64 i386 powerpc

You will have to enable universe repository, follow this howto: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) and enable universe repository, then ```
sudo apt-get update
``` and ```
sudo apt-get install xcompmgr
```

---

### Post by 23meg on 2006-04-18
Anyone tried the transset-df method with XGL + Compiz? Worked straight away for me but I'm trying to iron some minor bugs; for example the terminal window sometimes gets decorated with a title bar after a while for no apparent reason.

---

### Post by Felipe_U on 2006-04-19
Hi, there.
 I'm having trouble compiling the transset-df-5. I already installed the build-essential package and the following libxrender libraries: libxrender1, libxrender1-dbg, libxrender-dev, libxcomposite1, libxcomposite1-dbg, libxcomposite-dev
After all that I'm still getting the following error:
```

cc -Wall -o transset-df transSet.o dsimple.o `pkg-config --libs xcomposite xfixes xdamage xrender` -lm
Package xcomposite was not found in the pkg-config search path.
Perhaps you should add the directory containing `xcomposite.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xcomposite' found
transSet.o: In function `get_top_window':
transSet.c:(.text+0x189): undefined reference to `XQueryTree'
transSet.c:(.text+0x1d3): undefined reference to `XQueryTree'
transSet.o: In function `main':
transSet.c:(.text+0x63e): undefined reference to `XFetchName'
transSet.c:(.text+0x6d9): undefined reference to `XInternAtom'
transSet.c:(.text+0x70e): undefined reference to `XGetWindowProperty'
transSet.c:(.text+0x72e): undefined reference to `XFree'
transSet.c:(.text+0x857): undefined reference to `XInternAtom'
transSet.c:(.text+0x871): undefined reference to `XDeleteProperty'
transSet.c:(.text+0x88e): undefined reference to `XInternAtom'
transSet.c:(.text+0x8ae): undefined reference to `XChangeProperty'
transSet.c:(.text+0x8c1): undefined reference to `XSync'
dsimple.o: In function `Open_Display':
dsimple.c:(.text+0x1ea): undefined reference to `XOpenDisplay'
dsimple.c:(.text+0x201): undefined reference to `XDisplayName'
dsimple.o: In function `Open_Font':
dsimple.c:(.text+0x27b): undefined reference to `XLoadQueryFont'
dsimple.o: In function `Beep':
dsimple.c:(.text+0x2b2): undefined reference to `XBell'
dsimple.o: In function `ReadBitmapFile':
dsimple.c:(.text+0x342): undefined reference to `XReadBitmapFile'
dsimple.o: In function `WriteBitmapFile':
dsimple.c:(.text+0x392): undefined reference to `XWriteBitmapFile'
dsimple.o: In function `Resolve_Color':
dsimple.c:(.text+0x6ec): undefined reference to `XGetWindowAttributes'
dsimple.c:(.text+0x70b): undefined reference to `XParseColor'
dsimple.c:(.text+0x737): undefined reference to `XAllocColor'
dsimple.o: In function `Bitmap_To_Pixmap':
dsimple.c:(.text+0x785): undefined reference to `XGetGeometry'
dsimple.c:(.text+0x7af): undefined reference to `XCreatePixmap'
dsimple.c:(.text+0x7db): undefined reference to `XCopyPlane'
dsimple.o: In function `Select_Window':
dsimple.c:(.text+0x870): undefined reference to `XCreateFontCursor'
dsimple.c:(.text+0x894): undefined reference to `XGrabPointer'
dsimple.c:(.text+0x8bc): undefined reference to `XAllowEvents'
dsimple.c:(.text+0x8d0): undefined reference to `XWindowEvent'
dsimple.c:(.text+0x933): undefined reference to `XUngrabPointer'
dsimple.o: In function `Get_Window_Under_Cursor':
dsimple.c:(.text+0x978): undefined reference to `XCreateFontCursor'
dsimple.c:(.text+0x99c): undefined reference to `XGrabPointer'
dsimple.c:(.text+0x9df): undefined reference to `XQueryPointer'
dsimple.c:(.text+0x9ef): undefined reference to `XUngrabPointer'
dsimple.o: In function `Window_With_Name':
dsimple.c:(.text+0xa16): undefined reference to `XFetchName'
dsimple.c:(.text+0xa5c): undefined reference to `XQueryTree'
dsimple.c:(.text+0xac2): undefined reference to `XFree'
dsimple.o: In function `Window_With_Name_Regex_Recurse':
dsimple.c:(.text+0xaef): undefined reference to `XFetchName'
dsimple.c:(.text+0xb3b): undefined reference to `XQueryTree'
dsimple.c:(.text+0xba1): undefined reference to `XFree'
collect2: ld returned 1 exit status
make: *** [transset-df] Error 1

``` 
Any Ideas on why this is happening?

Thanks in advance,
Felipe

---

### Post by 23meg on 2006-04-19
Did you by any chance install the required libs from some other source than the official Ubuntu repositories? And are you running Breezy?

---

### Post by Felipe_U on 2006-04-19
[quote=23meg]Did you by any chance install the required libs from some other source than the official Ubuntu repositories? And are you running Breezy?[/quote]

Yes, I'am running breezy, and I installed the libraries through synaptic. Maybe I'm missing some other libraries.....Thanks for your quick post.

Regards,
Felipe

---

### Post by 23meg on 2006-04-19
No problem; make sure you have all the required libs by issuing the command ```
sudo apt-get install xcompmgr libxcomposite1 libxcomposite-dev libxfixes3 libxfixes-dev libxdamage1 libxdamage-dev libxrender1 libxrender-dev
``` and try again.

---

### Post by Felipe_U on 2006-04-19
[quote=23meg]No problem; make sure you have all the required libs by issuing the command ```
sudo apt-get install xcompmgr libxcomposite1 libxcomposite-dev libxfixes3 libxfixes-dev libxdamage1 libxdamage-dev libxrender1 libxrender-dev
``` and try again.[/quote]

Thanks, it seems I was missing a couple of libraries.

Regards,
Felipe

---

### Post by OffHand on 2006-04-22
Im almost there. I followed all the steps but still the terminal uses a fake transparant (desktop picture). I don't see the folders under the terminal. 
My script looks like this: ```

#!/bin/bash
alltray -x -g +192+132 "gnome-terminal --window-with-profile=tterm" & sleep 2
transset-df -n "tterm (AllTray)" 0.85
```
It also opens at the upper left corner which is wrong.

It looks like everything is installed: ```
 admin@linux:~$ sudo apt-get install xcompmgr libxcomposite1 libxcomposite-dev libxfixes3 libxfixes-dev libxdamage1 libxdamage-dev libxrender1 libxrender-dev
Password:
Reading package lists... Done
Building dependency tree... Done
xcompmgr is already the newest version.
libxcomposite1 is already the newest version.
libxcomposite-dev is already the newest version.
libxfixes3 is already the newest version.
libxfixes-dev is already the newest version.
libxdamage1 is already the newest version.
libxdamage-dev is already the newest version.
libxrender1 is already the newest version.
libxrender-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
admin@linux:~$

```

---

### Post by babygigi on 2006-04-22
when i open my terminal from the icon i get a normal transparent one, but when i execute the file i made with the .sh ending with the script> #!/bin/bash
alltray -x -st -g +1+28 "gnome-terminal --window-with-profile=Default" & sleep 3
transset-df -n "tterm (AllTray)" 0.85 
 i get this msg in the terminal that opens and the terminal qickly closes it's self:
> (gnome-terminal:8864): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion 'gtk_accel_group_from_accel_closure (accel_closure) !=NULL' failed 

is there any way to fix this? thanks in advanced

---

### Post by 23meg on 2006-04-29
[QUOTE=babygigi]when i open my terminal from the icon i get a normal transparent one, but when i execute the file i made with the .sh ending with the script i get this msg in the terminal that opens and the terminal qickly closes it's self:


is there any way to fix this? thanks in advanced[/QUOTE]
The profile names you specify in the last two lines of the script are different; change your Gnome Terminal profile name to "tterm" and it should be fixed.

---

### Post by 23meg on 2006-04-29
[QUOTE=subsonic_shadow]Im almost there. I followed all the steps but still the terminal uses a fake transparant (desktop picture). I don't see the folders under the terminal. 
My script looks like this: ```

#!/bin/bash
alltray -x -g +192+132 "gnome-terminal --window-with-profile=tterm" & sleep 2
transset-df -n "tterm (AllTray)" 0.85
```
It also opens at the upper left corner which is wrong.

It looks like everything is installed: ```
 admin@linux:~$ sudo apt-get install xcompmgr libxcomposite1 libxcomposite-dev libxfixes3 libxfixes-dev libxdamage1 libxdamage-dev libxrender1 libxrender-dev
Password:
Reading package lists... Done
Building dependency tree... Done
xcompmgr is already the newest version.
libxcomposite1 is already the newest version.
libxcomposite-dev is already the newest version.
libxfixes3 is already the newest version.
libxfixes-dev is already the newest version.
libxdamage1 is already the newest version.
libxdamage-dev is already the newest version.
libxrender1 is already the newest version.
libxrender-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
admin@linux:~$

```[/QUOTE]
Make sure the composite extension is working correctly. When you type ```
transset 0.5
``` and click on a window does it become transparent? (make sure you have the package transset installed)

---

### Post by BjoeHrn on 2006-05-26
Hey dudes!

I need some help with xcompmgr. When it starts I can move my windows (terminals, firefox and so on) over my panels. If I max. a window it also get over the panels :(.
What shall I do?

Please help.

Thank you very much :-).

---

### Post by 23meg on 2006-05-27
[QUOTE=BjoeHrn]Hey dudes!

I need some help with xcompmgr. When it starts I can move my windows (terminals, firefox and so on) over my panels. If I max. a window it also get over the panels :(.
What shall I do?

Please help.

Thank you very much :-).[/QUOTE]
This is a known bug and AFAIK it wasn't fixed. Still, check out the new version of xcompmgr from poofyhairguy's thread (linked in the original post), maybe it's fixed there. I never maximize windows so it hasn't been an issue for me.

---

### Post by ZylGadis on 2006-05-28
It is not fixed, I just tried it. Not too important, but still annoying.

---

### Post by 23meg on 2006-05-28
[QUOTE=ZylGadis]It is not fixed, I just tried it. Not too important, but still annoying.[/QUOTE]
Alright, just remembered this, but it's entirely from memory and I haven't tested it recently:  try launching xcompmgr at startup rather than manually later on, and experiment with the order number. This may make the problem go away.

---

### Post by robio376 on 2006-06-09
Anybody have any success with 6.06 LTS? I have tried and failed.  video card is a Ati X300 using fglrx driver.

---

### Post by 23meg on 2006-06-09
Which of the two methods are you using? How exactly does it fail? Are you getting any error messages?

---

### Post by benplaut on 2006-06-09
sudo apt-get install yakuake

---

### Post by robio376 on 2006-06-10
[QUOTE=23meg]Which of the two methods are you using? How exactly does it fail? Are you getting any error messages?[/QUOTE]
Thanks for the help... There's no errors that I can find. I'm thinking that I have a problem with a failing video card. I dual boot this system with Fedora 5 and now it's showing artifacts also. I've been wanting to replace my Ati X300 card with a Nvidia card anyways. So now's a good time. Anybody know of a really good nvidia card for LTS? My system is as follows 3.2P4HT 1GB Ram and PCIx16 slot. 
Any ideas would be greatly appreciated!!
Thanks again! Sorry 23meg for asking the same questions in another thread!

---

### Post by JMO707 on 2006-06-10
Two questions:

Is there anyway to just make that every normal gnome-terminal I launch have a predefined transparency?

Is there anyway that the fonts doesnt get transparent too?

---

### Post by CameronCalver on 2006-06-13
Ahhhh i did the transparent thing from the first post and i set transparency to maximimum and set it default and now i cant change back i tryed reinsalling gnome-terminal but  didntwork what command will i do to change profiles or boot up in default so i can change it

---

### Post by jeff-- on 2006-06-15
Well I tried to do true transparency, and the only problem is that when I run xcompmgr -n in the terminal, it waits a long time, then I got some messages ```
error 9 request 154 minot 1 serial 53201
error 3 request 20 minor 0 serial 53202
error 3 request 20 minor 0 serial 53203
error 3 request 15 minor 0 serial 53204
```And so far it hasn't finished I guess because I don't have my "jeff@ubuntu:~$" displayed after that yet.  Could it be my video card is too old?  I have a GeForce TI 4200, and I had some x server issues earlier so I selected vesa for my drivers.  I can't think of any other things that could be causing this.

---

### Post by mistab1034 on 2006-06-21
I had this working in Breezy and loved it. Now I'm trying to get it in Dapper and everything is working except for the geometry. It just ignores it and puts it in the top right corner, but with the correct size.

this is the command I'm using, and used in Breezy:
```
alltray -x -s -st -g 1082x1010+1+28 "gnome-terminal --window-with-profile=Default"
```

any idea why it won't put it where i want?

---

### Post by toorima on 2006-06-22
I finally got it the way I wanted it with this line
alltray -s -x -st -stask "gnome-terminal --window-with-profile=tterm --geometry=95x40+0+420"
anything else would make it start in top left corner
the -stask is for skip taskbar

---

### Post by mistab1034 on 2006-06-22
thanks, that got it to work. I hate tiny little command line quirks like that.

---

### Post by iggykoopa on 2006-06-27
easiest way i've found to get this to work is just run XFWM for the window manager...works great

---

### Post by -Chi.0 on 2006-06-27
Does any one know if you can do this on Kubuntu Dapper 6.06?

---

### Post by JaymzJulian on 2006-07-08
> **-Chi.0 said:**
> Does any one know if you can do this on Kubuntu Dapper 6.06?

I got true transparent konsole with just a small patch and recompile of the deb that's in dapper.  Aparently it causes some problems, and is disabled in the source - but it works for me, so YMMV.  What I did:

```

  apt-get source konsole
  cd kdebase-3.5.2
  (edit konsole/konsole/main,cpp and change if0 to if1 :))
  ./configure
  cd konsole/konsole
  make && make install

```

This is, of course, stupid, and so I built a deb and threw it at [http://dspaudio.com/~jaymz/transparent-konsole_3.5.2-0ubuntu27_i386.deb](http://dspaudio.com/~jaymz/transparent-konsole_3.5.2-0ubuntu27_i386.deb)

---

### Post by Adrian_b on 2006-08-01
sagara@sousuke:~$ sudo dpkg -i transparent-konsole_3.5.2-0ubuntu27_i386.deb
(Reading database ... 140486 files and directories currently installed.)
Preparing to replace konsole 4:3.5.2-0ubuntu27 (using transparent-konsole_3.5.2-0ubuntu27_i386.deb) ...
Unpacking replacement konsole ...
dpkg: dependency problems prevent configuration of konsole:
 konsole depends on kdelibs4c2a (>= 4:3.5.3-1); however:
  Version of kdelibs4c2a on system is 4:3.5.2-0ubuntu18.1.
 konsole depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 konsole depends on libgcc1 (>= 1:4.1.0); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 konsole depends on libstdc++6 (>= 4.1.0); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
dpkg: error processing konsole (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 konsole



System is updated..
Using Edgy Eft maybe?

---

### Post by Anonii on 2006-10-12
Greetings,

my bash script to execute tterm (terminal) in the startup is:

```
#!/bin/bash
alltray -s -x -g 730x600+100+100 "gnome-terminal --window-with-profile=tterm -e folding"

```

This opens tterm with the **folding** command from the start. folding is another bash script. But that doesnt matter. Anyway, I want, now, to open a second tab with _rtorrent_ on it from the start. Can I do that? And how?

This means, that from startup I'll have tterm with **folding** in the one tab and _rtorrent_ in the other.
Any ideas?

*gnome-terminal --help | grep tab* will give you the commands.

Thanks!

---

### Post by Anonii on 2006-10-18
Can someone help me create a "tterm" but not with the default window size?

For example open a gnome-terminal, resize it to 93x7. Then execute "xwininfo"
Which to me gave:
```
$ xwininfo

xwininfo: Please select the window about which you
          would like information by clicking the
          mouse in that window.

xwininfo: Window id: 0x320fb47 "habeeb@4far: ~"

  Absolute upper-left X:  82
  Absolute upper-left Y:  98
  Relative upper-left X:  2
  Relative upper-left Y:  24
  Width: 761
  Height: 142
  Depth: 24
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +82+98  -309+98  -309-624  +82-624
  -geometry 93x7+80+74

```
 
Then I "note the value that appears in the "Corners:" line.".
So I note: +82+98, am i right?
And I use the command, **alltray -s -x -g +82+98 "gnome-terminal --window-with-profile=tterm"**

(Lets not take it as far as creating a bash script, a command is fine, for the example.)

What I would get from that command, would be a "tterm" in the default size and near the given spot. (see the screenshot attached for better understanding.)

(The screenshot is kinda ****** up, but I tried to represent it my best. I stroked the outline of the terminal window in which I executed the command, and used the geometry from. The rest brushes, are for privacy ^_^ )

Thanks!

---

### Post by aknapp on 2007-04-07
Is there a way to make it so that it doesn't hide when you do "Ctrl+Alt+D" (show desktop)?

---

### Post by Gerry_W on 2007-07-06
I really like the idea of a transparent terminal. However, when I try to 'make' transset-df-5.tar. gz I get this:

```
:~/transset-df-5$ make
cc -Wall -o transset-df transSet.o dsimple.o `pkg-config --libs xcomposite xfixes xdamage xrender` -lm
Package xext was not found in the pkg-config search path.
Perhaps you should add the directory containing `xext.pc'
to the PKG_CONFIG_PATH environment variable
Package 'xext', required by 'Xcomposite', not found
transSet.o: In function `get_top_window':
transSet.c:(.text+0x26d): undefined reference to `XQueryTree'
transSet.c:(.text+0x2c3): undefined reference to `XQueryTree'
transSet.o: In function `main':
transSet.c:(.text+0x755): undefined reference to `XFetchName'
transSet.c:(.text+0x7e7): undefined reference to `XInternAtom'
transSet.c:(.text+0x848): undefined reference to `XGetWindowProperty'
transSet.c:(.text+0x864): undefined reference to `XFree'
transSet.c:(.text+0x987): undefined reference to `XInternAtom'
transSet.c:(.text+0x9a3): undefined reference to `XDeleteProperty'
transSet.c:(.text+0x9c5): undefined reference to `XInternAtom'
transSet.c:(.text+0xa05): undefined reference to `XChangeProperty'
transSet.c:(.text+0xa1a): undefined reference to `XSync'
dsimple.o: In function `Open_Display':
dsimple.c:(.text+0x1da): undefined reference to `XOpenDisplay'
dsimple.c:(.text+0x1ee): undefined reference to `XDisplayName'
dsimple.o: In function `Open_Font':
dsimple.c:(.text+0x26d): undefined reference to `XLoadQueryFont'
dsimple.o: In function `Beep':
dsimple.c:(.text+0x2a9): undefined reference to `XBell'
dsimple.o: In function `ReadBitmapFile':
dsimple.c:(.text+0x355): undefined reference to `XReadBitmapFile'
dsimple.o: In function `WriteBitmapFile':
dsimple.c:(.text+0x3b9): undefined reference to `XWriteBitmapFile'
dsimple.o: In function `Resolve_Color':
dsimple.c:(.text+0x710): undefined reference to `XGetWindowAttributes'
dsimple.c:(.text+0x739): undefined reference to `XParseColor'
dsimple.c:(.text+0x76c): undefined reference to `XAllocColor'
dsimple.o: In function `Bitmap_To_Pixmap':
dsimple.c:(.text+0x7d2): undefined reference to `XGetGeometry'
dsimple.c:(.text+0x809): undefined reference to `XCreatePixmap'
dsimple.c:(.text+0x862): undefined reference to `XCopyPlane'
dsimple.o: In function `Select_Window':
dsimple.c:(.text+0x91b): undefined reference to `XCreateFontCursor'
dsimple.c:(.text+0x969): undefined reference to `XGrabPointer'
dsimple.c:(.text+0x9a0): undefined reference to `XAllowEvents'
dsimple.c:(.text+0x9c4): undefined reference to `XWindowEvent'
dsimple.c:(.text+0xa33): undefined reference to `XUngrabPointer'
dsimple.o: In function `Get_Window_Under_Cursor':
dsimple.c:(.text+0xa8c): undefined reference to `XCreateFontCursor'
dsimple.c:(.text+0xad7): undefined reference to `XGrabPointer'
dsimple.c:(.text+0xb2f): undefined reference to `XQueryPointer'
dsimple.c:(.text+0xb42): undefined reference to `XUngrabPointer'
dsimple.o: In function `Window_With_Name':
dsimple.c:(.text+0xb6d): undefined reference to `XFetchName'
dsimple.c:(.text+0xbc0): undefined reference to `XQueryTree'
dsimple.c:(.text+0xc25): undefined reference to `XFree'
dsimple.o: In function `Window_With_Name_Regex_Recurse':
dsimple.c:(.text+0xc56): undefined reference to `XFetchName'
dsimple.c:(.text+0xcc1): undefined reference to `XQueryTree'
dsimple.c:(.text+0xd26): undefined reference to `XFree'
collect2: ld returned 1 exit status
make: *** [transset-df] Error 1

```

I have not been able to figure out what exactly this "xext" package that it mentions in the beginning is. Can anyone help me out?

Thanks.

---

### Post by malachias on 2007-08-09
I have the identical problem. I can't install xext because it's "missing but referenced". Damn I really hate that error. =(

Any ideas?

---

### Post by frodon on 2007-08-10
this is an old guide so transset is in the repositories now ;)

---

### Post by Chymera on 2007-08-26
any updates on this guide? i'm looking for something similar to [http://www.lynucs.org/index.php?screen_id=10737077394089d877b3812&p=screen](http://www.lynucs.org/index.php?screen_id=10737077394089d877b3812&p=screen)
but i cant even get the first .tar.gz to install itself (i click the "install" button and it just closes)... plus i cant find half of the references in it?

has this been implemented as an out-of-the-box option in feisty?

---

### Post by fedex1993 on 2007-09-27
Yeah i got my transparent terminal working ever since i edited my xorg.conf beryl emerald is not loading i click reload window manager and it not working now please help

---

### Post by 23meg on 2007-09-28
I'll update this guide as soon as I find the time, perhaps within a week or so.

---

### Post by darkstr2o4 on 2007-12-10
is there a command that will start the terminal without the menu bar? right now my command is:

alltray -x -g 765x450+16+35 
 "gnome-terminal --window-with-profile=tterm"

The terminal comes up in the correct location but it always shows the menu bar for the terminal options.

---

### Post by 23meg on 2007-12-15
You can disable the menu bar in the "General" tab of the profile options.

---

### Post by mesocal on 2008-05-11
One thing I was having some issues with was the fact that every time I launched alltray, it would pop up in a different location; dispite the fact that I used 

   alltray --borderless --sticky -g 80x46x+3-47 "gnome-terminal --window-with-profile=transparent"

No matter what I did, it would pop up in the most random places. Finally, I tried it another way - which make since:

alltray --borderless --sticky "gnome-terminal --geometry 80x46+1+97 --window-with-profile=transparent"

obviously, substitute 'transparent' with the name of your profile.  I hope this helps someone out.

---

### Post by pingpongboss on 2008-05-11
> **Chymera said:**
> any updates on this guide? i'm looking for something similar to [http://www.lynucs.org/index.php?screen_id=10737077394089d877b3812&p=screen](http://www.lynucs.org/index.php?screen_id=10737077394089d877b3812&p=screen)
but i cant even get the first .tar.gz to install itself (i click the "install" button and it just closes)... plus i cant find half of the references in it?

has this been implemented as an out-of-the-box option in feisty?

[COLOR="Red"]This can now be done easily with Compiz on Hardy.[/COLOR]

Create a new profile for gnome-terminal called noborders.
Uncheck **Show menubar by default**, change **transparency** to what you like, change** Scrollbar is** to *Disabled*.

_[COLOR="DarkRed"]Remove borders: [/COLOR]_Now in ccsm, go to the **Window Decoration** plugin. Under **Decoration windows** change *any* to *(any) & !(title=noborders & class=Gnome-terminal)*.
[COLOR="DarkRed"]Fixed (user-specified) starting placement:[/COLOR]In ccsm, go to the **Place Windows** plugin. Make a New setting for **Positioned windows**. The match should be *(title=noborders & class=Gnome-terminal)*. My x-position is 400 and y-position is 300. Change those to suite you. Next time you start a new terminal it will be placed at (400,300).

[COLOR="DarkRed"]Start a new terminal with ```
gnome-terminal --window-with-profile=noborders
```[/COLOR]

Put *gnome-terminal --window-with-profile=noborders* under Sessions under gnome's System/Preferences to start it whenever you log in.

If you more options with its behavior, then use the **Window Rules** plugin in Compiz. Eg: to make it non movable, add *(title=noborders & class=Gnome-terminal)* to **Non movable windows**. Use the **Widget Windows** plugin and add *(title=noborders & class=Gnome-terminal)* to **Widget Windows** if you would like it to act like a widget (like a Screenlet).

etc, etc. so much you can do with compiz.

---

### Post by alexxxm on 2008-05-28
I was searching the web on how to get a borderless transparent Konsole, when I found this thread.

I dunno if it's in some old post (frankly the thread is too long!), but I wanted to say I'm pretty happy with Eterm - easily installable by yum.

Once you have Eterm, it's simply the matter of calling it by 

Eterm -O --buttonBar no --scrollBar no -x -f yellow -g 120x50+0+110 

alessandro

---

### Post by Vladimir Hidalgo on 2008-09-16
I installed **xcompmgr** with apt-get, then started it as "**xcompmgr -n**". Then I used xfce4-terminal with no border, no menu bar and in Style (or Appereance maybe, mine says "Estilo" in Spanish) I set the background color to transparent. You can choose the opacity.

Oh yes, you can use "**xcompmgr -fc &**" and close the terminal. That way you get even nicer effects in every window. Works great here with an Intel i810, so I must assume that performance on nVidia cards could not be less than excellent.

---

### Post by c-m on 2009-02-08
Any update on this for 8.10? It would be very useful on my Netbook

---

### Post by jerremy-tamlin on 2009-11-19
Thanks so much for this!

---

### Post by TheProphetJonah on 2011-06-05
OK. First, the application I chose to run, I have a text reader that flashes one word or a short chunk of text at a time, programmable up to a freakin' blur, called "dictator" which also works in Winblows but I ain't going there.
So I run that, and Orca screenreader, AND put a transparent hypnotic spiral image playing in Eye of Gnome at a transparency of 0.2

So I can script it with a command to execute dictator, orca and anim.gif which is just the name of the file.

and transset-df -c 0.2 and it does the target-sign, I click on the hypno wheel and drag it over the running speed-reading program.
For a really cool effect you can edit the output from Orca to play alternating words, alternately in the left and right earphones.

What makes it all sweeter than candy, ALL the programs originally referenced in 2005  in the original post, are available as .deb archives.
Install all of them with apt-get.

---

### Post by TheProphetJonah on 2011-06-05
> **TheProphetJonah said:**
>  cool effect you can edit the output from Orca to play alternating words, alternately in the left and right earphones.
...using wavplay or similar apps.

There's also an echo effect in wavplay for which I have exactly no other use.

man orca and man wavplay for details.

---


---
title: "Install Google Earth"
date: 2006-06-12
forum: Outdated Tutorials &amp; Tips
---

### Post by lastrite on 2006-06-12
The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

The rest of the install is self explanatory, have fun!

---

### Post by Praxidike on 2006-06-13
Wow, thanks. :)

I've been trying to get it working, new to Linux, was trying for ages with Wine, running the Windows version with no luck, this is much easier to install!! Although it's a little slow, maybe that's my drivers...

---

### Post by salomao on 2006-06-13
Simple and efficient, works fine.
 Thank you!

---

### Post by george_apan on 2006-06-13
Now that it is installed how do you uninstall it?

---

### Post by ubunturules on 2006-06-13
To uninstall Google Earth go to your home directory or wherever you installed Google Earth at.  There should be a folder there called google-earth.  Click on that folder and in it you should find a uninstall script.

---

### Post by David Valentine on 2006-06-13
THANK YOU for posting this--this is great!!!

---

### Post by ishtvan222 on 2006-06-13
Wow, thank you Google. Just a week ago I was thinking about how cool it would be to have a Google Earth in Linux, now its a dream come true. Thanks for the howto.

---

### Post by MadL on 2006-06-13
I can get Google Earth to start, but it always quits in the middle of setup, with this error message in the Terminal:


>  
Installing desktop menu entries...
Error: Rage 128 timed out... exiting


Suggestions?

---

### Post by user1397 on 2006-06-14
sounds like a video card problem, what video card do you hav?

---

### Post by Praxidike on 2006-06-14
Think I've got my drivers sorted out - it now runs smoothly (I said it ran slow in my post earlier)... but it crashes randomly, with no warnings.  Any idea what the problem there is?  Not a big deal, no problem to restart, just wondering what could cause it...

---

### Post by the_c on 2006-06-14
Nice howto. Thank's! :-)

---

### Post by george_apan on 2006-06-14
[QUOTE=ubunturules]To uninstall Google Earth go to your home directory or wherever you installed Google Earth at.  There should be a folder there called google-earth.  Click on that folder and in it you should find a uninstall script.[/QUOTE]
The thing is I don't know where it is installed or the name of the script. I installed it using sudo and it probably went somewhere in my /usr directory but I don't know where...

edit: nevermind, I got it. It's in /usr/local/google-earth. Thanks!

---

### Post by Rizado on 2006-06-14
[QUOTE=Praxidike]Think I've got my drivers sorted out - it now runs smoothly (I said it ran slow in my post earlier)... but it crashes randomly, with no warnings.  Any idea what the problem there is?  Not a big deal, no problem to restart, just wondering what could cause it...[/QUOTE]If you run through a console you might see that a crash report is generated and where, then it'll be sent to google the next time you start google earth. It's still beta and is the first linux release so expect some crashes.

---

### Post by nickm on 2006-06-14
is there a way to get it to show up in the menu?

---

### Post by simplyw00x on 2006-06-14
> is there a way to get it to show up in the menu?
Yes, yes there is.

```
sudo cp /usr/local/google-earth/googleearth.desktop /usr/share/applications/
```

---

### Post by nickm on 2006-06-14
Thanks!

---

### Post by Hobitus on 2006-06-14
Excellent, now i can see my city in Linux too :D

---

### Post by MadL on 2006-06-14
[QUOTE=erik1397]sounds like a video card problem, what video card do you hav?[/QUOTE]

Looks like an ATI Rage 128 Pro Ultra TF

---

### Post by weijie90 on 2006-06-14
i have the same problem. Rage 128 timed out.
please help...

---

### Post by Shish on 2006-06-16
Same here; and an opengl app I wrote myself no longer works either -- the kernel says

[drm:r128_cce_depth] *ERROR* r128_cce_depth called without lock held
[drm:r128_cce_idle] *ERROR* r128_cce_idle called without lock held

so it looks like one of opengl, X, or the kernel broke the r128 driver recently...

---

### Post by raduc on 2006-06-19
Same problem here with an ATI Rage 128 (Fury Pro) card...

---

### Post by kreso on 2006-06-19
I've got a stupid problem:

when i run googlearth it reports symlink: Permission denied??? running it as root works great, but still.

I debugged for a while and it seems that/usr/local/google-earth/googleearth-bin causes this fault?

---

### Post by UbuntuniX on 2006-06-19
Thanks,
it can be useful at times :)

---

### Post by dsoria on 2006-06-19
i've this error:

error code 29

"not connected to server"
"chek is your conection"

mm.. my connection is god! i can see the web pages, no problem!

help!

---

### Post by ripplez on 2006-06-20
Fantastic double thank you

---

### Post by MetaMorfoziS on 2006-06-20
[QUOTE=kreso]I've got a stupid problem:

when i run googlearth it reports symlink: Permission denied??? running it as root works great, but still.

I debugged for a while and it seems that/usr/local/google-earth/googleearth-bin causes this fault?[/QUOTE]


sudo chmod 777 -R [or whatever] ~/.googleearth/

(Because you installed it with root rights, and after isntall you started it, and it creates the .googleearth directory with root rights, and the next start it can'T open it with normal user)

---

### Post by James_M on 2006-06-20
I've got a little problem.  I was able to download it just fine from terminal (Xubuntu), and it says it installs just fine (also in terminal), but then there's nothing for me to launch!  How exactly do you turn it on, and how can I make Xubuntu stop opening the .bin file in the archive manager?

---

### Post by norv on 2006-06-20
I get start-up crash using Dapper.
I tried running
**export LD_ASSUME_KERNEL=2.4.10**
as described in the GoogleEarth README but that didn't help.
Problem may be Nvidia driver related as I have this video card
**nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev a4)**
I don't have any special Nvidia drivers installed just vanilla Dapper install.

---

### Post by Neo40 on 2006-06-20
I can't figure out how to increase fonts in menu. They are too small and hard to read. Is there a way to fix it?

Thanks!

---

### Post by James_M on 2006-06-20
now I got it to get to installing menu entries and it's been hanging there for about 30 mins.  My powerbook won't even get that far...

---

### Post by dragonflyFZX on 2006-06-21
hi, thanks for this,

however, i have a question (i have never used google earth).  is it normal that i have a black space at the botom of the main window?

what is it for???

---

### Post by wog on 2006-06-21
[QUOTE=dragonflyFZX]hi, thanks for this,

however, i have a question (i have never used google earth).  is it normal that i have a black space at the botom of the main window?

what is it for???[/QUOTE]

I had to open the program to see what you were talking about.

If the black strip along the bottom of the window is what you're talking about, it's for information about the pointer location and altitude, and about how busy it is regarding streaming data.

If you're talking about the black area above that in the opening screen below the Earth, that's the blackness of space. :)

---

### Post by That Other Guy on 2006-06-21
Any suggestions on getting it to print?  I can print to a PostScript file fine, but I'd like to print directly from GE.  The GE print window comes up, but there aren't any printers to choose from.  I'm running CUPS on Kubuntu 5.10; all other apps print just fine.

Same for emailing: I followed the GE email readme, and Firefox opens a new tab, but Thunderbird doesn't do anything (i.e. no compose window).

Many thanks,

mike

---

### Post by VictorE on 2006-06-22
Thanks for putting this together.  I've been wanting to install GE for a while, but was put off by what I thought would be a complicated process.  I'm glad that it was so easy and it worked w/o a hitch.

---

### Post by domino on 2006-06-22
Anyone know how to make google earth play nice with compiz? It's too choppy under compiz? Otherwise, under gnome is as smooth as the windows and os x versions.

---

### Post by maol62 on 2006-06-22
Any one who knows how to associate kmz with Google Earth so that the file is opened with an already existing, or if there is no existing a new, Google Earth window? As it is now I have just managed to associate kmz so that everytime I open a kmz-file a new Google Earth window is launched but I want them to be opened in the same window, not a new one.

---

### Post by kreso on 2006-06-23
[QUOTE=MetaMorfoziS]sudo chmod 777 -R [or whatever] ~/.googleearth/

(Because you installed it with root rights, and after isntall you started it, and it creates the .googleearth directory with root rights, and the next start it can'T open it with normal user)[/QUOTE]

Yeah, I tried that, doesn't work. I also tried it installing as regular user, same shit.

---

### Post by Sam on 2006-06-23
[QUOTE=domino]Anyone know how to make google earth play nice with compiz? It's too choppy under compiz? Otherwise, under gnome is as smooth as the windows and os x versions.[/QUOTE]

I'm using Xgl with compiz and run Google Earth with [this trick](http://www.ubuntuforums.org/showthread.php?t=176636). You should use it for every application that uses 3D.

But I experienced some (rare) random crashes while moving the view. I don't know if it's due to Xgl or the beta state.

---

### Post by pgmario on 2006-06-23
Fonts are not displayed on the map. The menus and tooltips work, but instead of city names, etc. on the map, there are only white squares.
Does anyone know how to fix this problem?

**Edit:** Works after restart.

---

### Post by McDuff on 2006-06-24
i've successfully installed google earth on my laptop.
but when I start the prog, it doesn't load the image of the earth and I get the following:
```
libGL warning: 3D driver claims to not support visual 0x46
libGL warning: 3D driver claims to not support visual 0x22
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d

```

I have a via k8m800 unichrome pro video card.
does anybody know how to solve this problem?

---

### Post by qazwsx on 2006-06-24
My problem
[[IMG]http://img45.imageshack.us/img45/656/kuvakaappaus6to.th.png[/IMG]](http://img45.imageshack.us/my.php?image=kuvakaappaus6to.png)
Runs pretty smoothly otherwise.

---

### Post by hawko on 2006-06-24
[QUOTE=Sam]But I experienced some (rare) random crashes while moving the view. I don't know if it's due to Xgl or the beta state.[/QUOTE]

I am using a normal install of Ubunutu (no compiz) and I also get crashes.  I'm thinking GE is still just a little unstable.  Much better than nothing though!

---

### Post by easy_target on 2006-06-24
[QUOTE=Neo40]I can't figure out how to increase fonts in menu. They are too small and hard to read. Is there a way to fix it?

Thanks![/QUOTE]

Yes there is! I found this on a Gentoo forum:

Edit the following files:

-Font Size:

```
~/.googleearth/Registry/google/googleearthplus/User/render/guifontsize
```

-Font Family:

```
~/.googleearth/Registry/google/googleearthplus/User/render/guifontfamily
```


If you don't see these files, you can create them. I had the best results using  "12" under guifontsize and "Sans" under guifontfamily, but you can virtually use anything you want.

Happy earth browsing!

---

### Post by dcstar on 2006-06-25
[QUOTE=McDuff]i've successfully installed google earth on my laptop.
but when I start the prog, it doesn't load the image of the earth and I get the following:
```
libGL warning: 3D driver claims to not support visual 0x46
libGL warning: 3D driver claims to not support visual 0x22
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d

```

I have a via k8m800 unichrome pro video card.
does anybody know how to solve this problem?[/QUOTE]
You should run "glxinfo" (in a terminal) to check if your Direct Rendering is actually installed correctly.

You may need to re-run:
```
sudo dpkg-reconfigure xserver-xorg
```
and select your video hardware again.

---

### Post by groove on 2006-06-25
It seems to use wine

---

### Post by Neo40 on 2006-06-27
Thanks for the info! I'll try it tonite :)

---

### Post by Davidios on 2006-06-28
This is my problem. Any help?

---

### Post by Tourmaline on 2006-06-28
Installed on a notebook with Radeon Mobility 9000 and ATI driver 8.24.8 (direct rendering enabled) when launched from shell I get a "Segmentation Fault" error message. Problem seems to come from ATI driver. The program starts when using software-rendering but, of course, it's unusable. 

The program works well on Radeon 9550 and FGLRX 8.16.20 on Ubuntu 5.10.

---

### Post by domino on 2006-06-28
I have a problem with it just crashing. If you need more info on crashes, run googleearth in the terminal. Once it crashes it should produce the error message. For example:

```

domino@dapper:~$ googleearth
Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin(__gxx_personality_v0+0x212) [0x804ab32]
  ./googleearth-bin [0x804b133]
  [0xffffe420]
  /usr/local/google-earth/libevll.so(_ZN5earth4evll9CacheNode8populateEPNS0_5CacheEPNS_10HeapBufferEPNS0_13CacheNodeTypeE+0x33) [0xb38a9893]
  /usr/local/google-earth/libevll.so(_ZN5earth4evll5Cache18loaderNodePopulateEPNS0_9CacheNodeEPNS_10HeapBufferE+0x50) [0xb38a9950]
  /usr/local/google-earth/libevll.so(_ZN5earth4evll9NetLoader17finishHttpRequestEPNS0_11NLQueueElemEmPNS_10HeapBufferE+0x1a2) [0xb39742e2]
  /usr/local/google-earth/libevll.so(_ZN5earth4evll9NetLoader12asyncHandlerEv+0x2ef) [0xb397b4df]
  ./libbase.so(_ZN5earth11AsyncThread12asyncHandlerEPNS0_10ThreadInfoE+0x53) [0xb793ef13]
  ./libbase.so(_ZN5earth11AsyncThread9asyncFuncEPv+0x28) [0xb793efd8]
  /lib/tls/i686/cmov/libpthread.so.0 [0xb625f341]
  /lib/tls/i686/cmov/libc.so.6(__clone+0x5e) [0xb63354ee]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/domino/.googleearth/crashlogs/crashlog-C69BC757.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

```

---

### Post by simplyw00x on 2006-06-29
[QUOTE=Davidios]This is my problem. Any help?[/QUOTE]
Same problem here.

---

### Post by barmaley on 2006-06-30
Hello, people
Thanks for the how-to, worked great.
When I run the program it shows a warning:
'You are currently running Google Earth in OpenGL with sofware emulation.In this mode, Google Earth will work but it will run very slowly. If you want to run Google Earth more quickly we suggest that you upgrade your graphics card driver. ...'
And indeed it runs, but very slowly as they promised.
Can anybody help with that?

---

### Post by mtpadilla on 2006-06-30
[QUOTE=kreso]Yeah, I tried that, doesn't work. I also tried it installing as regular user, same shit.[/QUOTE]


Yep, same exact problem here. Tried the same sort of thing w/o any luck...hmmm.

---

### Post by woopud on 2006-06-30
Installation went fine, then I started it, Window opened and 5 seconds later :

woopud@ubuntu:~$ wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin--12:43:14--](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin--12:43:14--)  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 72.14.203.93, 72.14.203.91
Connecting to dl.google.com|72.14.203.93|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16,984,110 (16M) [application/octet-stream]

100%[====================================>] 16,984,110   163.87K/s    ETA 00:00
12:44:57 (160.81 KB/s) - `GoogleEarthLinux.bin' saved [16984110/16984110]
woopud@ubuntu:~$ sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.1563..................................................................
Installing mimetypes...
Running /usr/bin/update-mime-database /home/woopud/.local/share/mime***
* Updating MIME database in /home/woopud/.local/share/mime...
Wrote 2 strings at 20 - 6c
Wrote aliases at 6c - 70
Wrote parents at 70 - 74
Wrote literal globs at 74 - 78
Wrote suffix globs at 78 - d0
Wrote full globs at d0 - d4
Wrote magic at d4 - e0
Wrote namespace list at e0 - e4
***
Installing desktop menu entries...
Error: Rage 128 timed out... exiting
woopud@ubuntu:~$

---

### Post by lastrite on 2006-06-30
> Installing desktop menu entries...
Error: **Rage 128** timed out... exiting
woopud@ubuntu:~$

That looks like a video card driver issue, for those having issues running this or with sluggish performance i'd install the latest drivers available for your graphics cards, theres plenty of information on how to do that in this forum :D

---

### Post by NZ-Wanderer on 2006-07-01
Yup, I get that message as well, just a complete crash when running google earth..
I used synaptic and made sure the nvidia drivers were installed, and also re-did xserver.xorg to make sure it was all setup properly..

Update: solved the crash problem, it seems my internet connection wasn't working...

Now all I got to do is solved why I not get earth (got the menu etc on left, but just black space where the earth should be..

[QUOTE=domino]I have a problem with it just crashing. If you need more info on crashes, run googleearth in the terminal. Once it crashes it should produce the error message. For example:
[/QUOTE]

---

### Post by rskovacs on 2006-07-02
As far as uninstalling Google Earth...

It should work like this, right?

```
cd /usr/local/google-earth
sudo sh uninstall
```

When I try to run the uninstall script, I get the error: "Could not find a usable uninstall program. Aborting."  What is going wrong?

---

### Post by hajk on 2006-07-03
Graphics cards based on nVidia GeForce 6200SE TurboCache show GoogleEarth as a totally unusable patchwork of differently sized and scaled rectangles. I gather from the nVidia forums that the next issue of the nVidia driver will fix this. I hope that Backports will make that version available in due course... made a request through LaunchPad today.

---

### Post by motionsiren on 2006-07-03
A fresh installl with a ATI Radeon 9550 to Apple Cinema Display worked flawlessly (using video card drivers that came with Ubuntu 6 itself).

Now... for Sketchup, so I can waste my days modeling buildings ;)

thanks for the note. nice and simple too. finally.

---

### Post by Danyl on 2006-07-04
Hi yall

It seems I am having similar problems to another poster back in the thread. 

When I initially attempted to start the program I got this error:

```
Installing desktop menu entries...
Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin(__gxx_personality_v0+0x212) [0x804ab32]
  ./googleearth-bin [0x804b133]
  [0xffffe500]
  /usr/lib32/libX11.so.6(XQueryExtension+0x17) [0x57342fc7]
  /usr/lib32/libX11.so.6(XInitExtension+0x3b) [0x5733754b]
  /usr/lib32/libXext.so.6(XextAddDisplay+0x49) [0x5731151c]
  /usr/lib32/libGL.so.1 [0x5744f394]
  /usr/lib32/libGL.so.1(__glXInitialize+0x1f) [0x5744fa5b]
  /usr/lib32/libGL.so.1(__glXSetupForCommand+0x47) [0x57450a11]
  /usr/lib32/libGL.so.1(glXSwapIntervalSGI+0x9d) [0x5744df57]
  ./libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext15setSwapIntervalEi+0x100) [0x56adbf60]
  ./libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext4openEv+0x568) [0x56b17378]
  /home/dan/google-earth/libevll.so(_ZN5earth4evll13VisualContext11openContextEN3Gap3Gfx25igRenderDestinationFormatERKNS0_8InitInfoE+0xff) [0x59a388bf]
  /home/dan/google-earth/libevll.so(_ZN5earth4evll13VisualContext4initERKNS0_8InitInfoE+0xdf) [0x59a3a2af]
  /home/dan/google-earth/libevll.so(_ZN5earth4evll17RenderContextImpl4initERKNS0_8InitInfoE+0x3f) [0x599eae8f]
  ./librender.so(_ZN12RenderWidget6setApiEPN5earth4evll3APIE+0x4b) [0x56fb87bb]
  ./librender.so(_ZN5earth6render12RenderWindow12createWidgetEv+0x8a) [0x56fa06ba]
  ./libgoogleearth.so(_ZN5earth6client12ModuleWidget9showEventEP10QShowEvent+0x7d) [0x55c6180d]
  ./libqt-mt.so.3(_ZN7QWidget5eventEP6QEvent+0x277) [0x56266db7]
  ./libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0x561ba731]
  ./libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xc9) [0x561bb219]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x266) [0x56265d16]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56265a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x56265cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56265a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x56265cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56265a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x56265cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56265a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x56265cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56265a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x56265cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56265a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x56265cb7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56265a6b]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x56265cb7]
  ./libqt-mt.so.3(_ZN11QMainWindow4showEv+0x93) [0x56338513]
  ./libqt-mt.so.3(_ZN7QWidget10showNormalEv+0x33) [0x5625f383]
  ./libgoogleearth.so(_ZN10MainWindow18readScreensizeInfoEv+0x621) [0x55c26e61]
  ./libgoogleearth.so(_ZN5earth6client11Application3runEiPPc+0x1569) [0x55c4e2d9]
  ./libgoogleearth.so(_ZN5earth6client11ApplicationC1EiPPcb+0x923) [0x55c502c3]
  ./googleearth-bin [0x804c73d]
  /lib32/libc.so.6(__libc_start_main+0xd2) [0x5711aea2]
  ./googleearth-bin(__gxx_personality_v0+0x41) [0x804a961]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/dan/.googleearth/crashlogs/crashlog-F7639991.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

```

And when I try and open it now from the applications menu, it just crashes immediately (after the Google Earth splash screen comes up).

Is there a work around with this or do I have to wait until Google decide to upgrade the app to something better than Beta???

---

### Post by Matt Houston on 2006-07-04
Noobie question here: where do I install Google Earth to if I don't want it in my home directory, is there a 'program files' kind of place?

---

### Post by hajk on 2006-07-04
Standard places for software outside the control of apt:

1. The /usr/local/ tree (this is one of the defaults of GoogleEarth); requires you to
     run the install with root privileges ("sudo").

2. The user tree, like /home/matt/... .

The point is that any future update/upgrade of Ubuntu leaves those directory trees alone.

---

### Post by pjnewman on 2006-07-04
[QUOTE=kreso]Yeah, I tried that, doesn't work. I also tried it installing as regular user, same shit.[/QUOTE]

Because googleearth auto runs after install (and installation is done as root) your user preference files in ~/.googleearth are owned by root.  So:
chown -R <you>:<you> ~/.googleearth

That did the trick for me.

---

### Post by russbuss on 2006-07-05
[QUOTE=hajk]Graphics cards based on nVidia GeForce 6200SE TurboCache show GoogleEarth as a totally unusable patchwork of differently sized and scaled rectangles. I gather from the nVidia forums that the next issue of the nVidia driver will fix this. I hope that Backports will make that version available in due course... made a request through LaunchPad today.[/QUOTE]

I have similar troubles, although the patchwork is sort of usable.  I can usually get a square in the lower left corner that is usable, although the controls in the upper right get all screwed up and are useless (save the zoom which I can usually fnd via trial and error).

I am using an Intel integrated video card (82915G/GV/910GL Express Chipset) so maybe this is the problem?

Anyone else have this problem?  Anyone else certain that my problem is caused by my video card?

---

### Post by Mishal on 2006-07-05
Google Earth on my PC is not working properly at all. I know it is meant to be unstable at the moment, but for me it has been quite unusable:

- The program shuts down by itself after a few minutes will all unsaved down deleted

- It won't close when I try to exit. It disappears from the taskbar but it can be seen to be running if I go to System Monitor. The problem with this is that I cannot restart Google Earth unless I manually 'End Process' in the System Monitor. But if I 'end process' like that, I lose all my unsaved data. Thus, I have simply failed to keep my placemarks.

- I get overlaying squares which prevent me from seeing things. I think this is a problem for others in this thread too.

- The program often gets stuck. In other words, I move my mouse pointer and I see the effect after 20 seconds.

All in all, I have just given up using my favorite software on PC because it is unusable. I have tried installing the Windows version using wine but it won't run.

By the way, my machine is a Athlon XP 2000+ with 512GB RAM which isn't exactly bad, is it? I guess I just have to wait for the stable release.

---

### Post by duartemolha on 2006-07-05
Great... My was not running in normal user mode... know it runs fine 

Thanks :)

duarte

---

### Post by casfindad on 2006-07-07
> **hajk said:**
> Standard places for software outside the control of apt:

1. The /usr/local/ tree (this is one of the defaults of GoogleEarth); requires you to
     run the install with root privileges ("sudo").

2. The user tree, like /home/matt/... .

The point is that any future update/upgrade of Ubuntu leaves those directory trees alone.

So, if I want to install GoogleEarth 4 and make it available to other users on my computer, should I install as sudo and chmod -R user:user ~/.googleearth for each user? Or do I install with my regular user account in my home tree?

Also, has anyone else gotten the uninstall script to work? I had to remove my copy manually.

---

### Post by DarkDancer on 2006-07-08
Hmmm, it would work great for about 5 minutes and then lock Ubuntu up tight as a drum. The uninstall worked well though. I'll try it again after they makea few improvements.

---

### Post by fululian on 2006-07-09
> Graphics cards based on nVidia GeForce 6200SE TurboCache show GoogleEarth as a totally unusable patchwork of differently sized and scaled rectangles. I gather from the nVidia forums that the next issue of the nVidia driver will fix this. I hope that Backports will make that version available in due course... made a request through LaunchPad today.

i run an nvidia GeForce Go 6200 TurboCache on my sony vaio vgn-fs115z notebook, i installed google-earth as told above and it turns out exactly as in the quote above.

---

### Post by casfindad on 2006-07-09
> **casfindad said:**
> So, if I want to install GoogleEarth 4 and make it available to other users on my computer, should I install as sudo and chown -R user:user ~/.googleearth for each user? Or do I install with my regular user account in my home tree?

Also, has anyone else gotten the uninstall script to work? I had to remove my copy manually.

Bump.

Also, do you think I should wait until Google Earth is more stable? It seems like people are having some problems with the latest beta affecting their system.

---

### Post by wog on 2006-07-09
> **casfindad said:**
> Bump.

Also, do you think I should wait until Google Earth is more stable? It seems like people are having some problems with the latest beta affecting their system.

I didn't have a problem with the beta, but then I have an nVidia 5200 card, nice and stable. :)

---

### Post by nosam on 2006-07-10
I installed it with no problems, but after starting Google Earth it freezes right at "Google Earth Intialization".  And boy does it _freeze_.  I have to shut down my system by cycling the power.  Any ideas as to a fix, or is it not worth fooling with?

---

### Post by fululian on 2006-07-11
got a new automatic update today and it sure enough installed a brand new NVIDIA DRIVER. the one we was looking for (hajk?), however, nothing changed, tried it a few times after one reboot, and it's the same thing. so we keep on waiting...damn such a premiere program and i can't run it.

---

### Post by Master Shake on 2006-07-12
When I open GoogleEarth, the earth section displays in the top 1/6th of the screen.  The other 5/6th is a big black area.  Any ideas?

6.06 Dapper, most recent updates, a crappy Intel 82845G/GL

---

### Post by Tuzo on 2006-07-13
I'm running Linux on an iMac.  I can't seem to follow these simple instructions.  Is it possible to run Google Earth on a Mac running Ubuntu Linux?  After I run "sh GoogleEarthLinux.bin", I get the following:

Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.1660..................................................................
myprompt% 

Then, nothing...

Any ideas?

Thanks!


> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

The rest of the install is self explanatory, have fun!

---

### Post by domino on 2006-07-13
re-download the file. Maybe a corrupt download? Also make sure you have read/write permission on the file. I prefer running google earth on OS X rather than Linux/xgl/compiz. It's just more responsive on a Mac.

---

### Post by jaka on 2006-07-21
How to remove/unistall google earth?

---

### Post by flixer on 2006-07-21
Another alternative is to try and install Google Earth with [Automatix]("http://www.ubuntuforums.org/showthread.php?t=80295").

---

### Post by JMO707 on 2006-07-22
Does somebody suffer of unexpected crashs (the program closes) because of a bug?

---

### Post by irober02 on 2006-07-23
I installed Google Earth last night and it worked (is working well) EXCEPT that after I logged out and logged in again I find that my keyboard is frozen.

The problem only seesm to happen in KDE -I can run gnome. I haven't solved the problem yet. :-( 

This might be a coincidence but BE WARNED.

My .xsession-errors file is showing a lot of GDK errors:

I'm running Dapper on a Dell laptop with an ATI graphics card and using the fglrx drivers.

ian

---

### Post by NZ-Wanderer on 2006-07-23
Well, I can now report that all my problems with getting Google Earth to run have now disappeared, and I can now see it just fine :) :) 

I used Automatix to install it, and everything went without a hitch..

---

### Post by Jesterday on 2006-07-24
I use Google Earth all the time and it is working great for me in linux. Has anyone tried upgrading to Google Earth Plus and downloading waypoints with a GPS in Linux?

---

### Post by greg m on 2006-07-26
> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

The rest of the install is self explanatory, have fun!

self explanatory?? not to me,:confused:

---

### Post by NZ-Wanderer on 2006-07-26
Go here

[http://ubuntuforums.org/showthread.php?t=177646&highlight=automatrix](http://ubuntuforums.org/showthread.php?t=177646&highlight=automatrix)

And install Automatrix, apart from containg all sorts of goodies it now also contains Google Earth (you can pick and choose what to install)

[CENTER][IMG]http://folding.extremeoverclocking.com/sigs/sigimage.php?u=188671&c1=FFFFFF&c2=000000&c3=000000&c4=0000CC&c5=FFFFFF[/IMG][/CENTER]

> **greg m said:**
> self explanatory?? not to me,:confused:

---

### Post by dweez on 2006-07-31
I tried installing GoogleEarth using Automatix (running it on Dapper btw) and my system freezes up when Google is attempting to initiate.  Any ideas?  Any needed info I might have left out?

AMD Athlon 1800+
1GB (2x512MB) OCZ EL PC 3500
ATI Radeon 9700 Pro

---

### Post by NZ-Wanderer on 2006-07-31
Hmmm I think you might find it has something to do with your ATI, although I could be totally wrong.. - I needed Nvidia drivers installed on Dapper before Google Earth worked properly for me..
Maybe there is someone here that's installed it on an ATI and can help you..

[CENTER][IMG]http://folding.extremeoverclocking.com/sigs/sigimage.php?u=188671&c1=FFFFFF&c2=000000&c3=000000&c4=0000CC&c5=FFFFFF[/IMG][/CENTER]

> **dweez said:**
> I tried installing GoogleEarth using Automatix (running it on Dapper btw) and my system freezes up when Google is attempting to initiate.  Any ideas?  Any needed info I might have left out?
AMD Athlon 1800+
1GB (2x512MB) OCZ EL PC 3500
ATI Radeon 9700 Pro

---

### Post by a-musing amazon on 2006-07-31
Well it used to work for me, however I just tried loading it again and it broke. I tried it again and it then told me there was an update. Downloaded and installed that and if I run it in console I get the splash screen and then it fails with messages: 

Google Earth has caught signal 11.

  (no debug data available.)

I'm running the AMD64 kernels (I've checked and it breaks on both the -generic and -k8 AMD64 kernels).

---

### Post by a-musing amazon on 2006-07-31
Well seems caught signal 11 is a seg. fault.

Tried the fix export LD_ASSUME_KERNEL=2.4.10 before running googleearth as suggested in the README.Linux

but now I get 
/bin/sh: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory

which is strange since I have this lib in both /lib/ and in /lib32/.

---

### Post by dweez on 2006-08-01
Thanks for the replies.  I thought the ATI card might be part of the problem, just wanted to run it by people here.  I'll keep looking into it or get tired and just swap out an older nVidia card I have.

---

### Post by kloy1334 on 2006-08-01
Uninstalling Google Earth does not work correctly for me. My system says "Could not find a usable uninstall program. Aborting." What do I need to do?

---

### Post by bobt on 2006-08-01
I had a problem with rendering. Large pixilated area right through the middle and the control overlays acting funky. Went to "View-->View Size-->Computer playback" and selected one of the entries there. Works great now!

Bob

---

### Post by Metroid48 on 2006-08-02
It works great, but it's REALLY slow. Not sure if it's a graphic card problem, but it works fine in Windows.

Intel G915 Mobile Chipset.

Btw, is there a terminal command to update Intel drivers, like there is for Nvidia and ATI cards?

---

### Post by mostwanted on 2006-08-03
An even simpler way is to get Google Earth is by using the Klik package:

[http://googleearth.klik.atekon.de/](http://googleearth.klik.atekon.de/)

---

### Post by angrykeyboarder on 2006-11-07
Another alternative is to add the [PLF repository]("http://doc.ubuntu-fr.org/doc/plf") to your sources.list file.

Or just:

```
$ wget [http://packages.freecontrib.org/ubuntu/plf/pool/edgy-plf/non-free/googleearth_4.0.2091-1plf6.10_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/edgy-plf/non-free/googleearth_4.0.2091-1plf6.10_i386.deb)
$ sudo dpkg -i googleearth_4.0.2091-1plf6.10_i386.deb 
```

---

### Post by leetrefz on 2006-11-16
So I did like the first post said, after putting in 
wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin) 
 I wait for it to download, and when i do 
sh GoogleEarthLinux.bin
it says the checksums don't match. 
wa?

---

### Post by angrykeyboarder on 2006-11-18
I'd suggest [this method]("http://ubuntuforums.org/showpost.php?p=1726307&postcount=1").

---

### Post by 56phil on 2006-11-18
The download went well. I thought the install was ok. However, when I started googleearth All I got was a splash screen. Top told me it was using all available CPU cycles so I waited 5 minutes then killed the process. Does anyone have any ideas how I can resolve this problem? ](*,) Thanks.

---

### Post by gammyhand on 2006-11-18
I have installed earth but running it just gets to the splash screen and nothing else.

---

### Post by romg on 2006-11-21
Hi all,

When trying to install GoogleEarth, I can see these lines in my shell :

> Gdk-WARNING **: locale not supported by C library

Gdk-WARNING **: locale not supported by Xlib, locale set to C

Gdk-WARNING **: can not set locale modifiers


Then the installation work normally, execept that I can't run GoogleEarth...

I run it on ubuntu (Linux pcromg 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux)

Any idea ?

Thanks !

Jérôme

---

### Post by gammyhand on 2006-11-22
> **gammyhand said:**
> I have installed earth but running it just gets to the splash screen and nothing else.

Anyone?

---

### Post by Paul_M on 2006-11-22
I have installed Google Earth on my laptop (IBM ThinPad T21), however on running the applicatio it gets only as far as the splash screen, on running it via a terminal window however I get the following message as well as the splash screen:```
libGL warning: 3D driver claims to not support visual 0x42
```Any ideas what may be wrong there? I'm at a loss at the moment

---

### Post by JohnnyVW on 2006-11-24
> **gammyhand said:**
> I have installed earth but running it just gets to the splash screen and nothing else.

I'm having the same problem.  It worked fine on Dapper.  I'm running Edgy now and GE just sticks on the splash screen.

---

### Post by k1001001 on 2006-11-24
When I run Google Earth, it runs very painfully slow. Any suggestions?

---

### Post by otwr on 2006-12-03
Partial success with:

$ DISPLAY=:0 googleearth

with XGl this ends up creating a weird window that doesn't interact with the rest of the desktop... but at least it's there.

---

### Post by Chris11 on 2006-12-04
> **JohnnyVW said:**
> I'm having the same problem.  It worked fine on Dapper.  I'm running Edgy now and GE just sticks on the splash screen.

Me too, but on Dapper...

Atlon 2000+
512Mb ram
ATI Radeon 9000 Pro

---

### Post by wool on 2006-12-07
Ubuntu 6.10 AMD64
running on Inspiron 1501
Turion 64 X2 TL-50

> dave@dave-laptop:~$ sudo sh GoogleEarthLinux.bin
Password:
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.2414..................................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!

can anyone help?

---

### Post by misha680 on 2006-12-08
Download and save this attachment (it is from fglrx 8.27.10), and put libGL.so.1 into the /usr/lib/googleearth directory.

Misha

> **Chris11 said:**
> Me too, but on Dapper...

Atlon 2000+
512Mb ram
ATI Radeon 9000 Pro

---

### Post by peacekpr on 2006-12-21
> **misha680 said:**
> Download and save this attachment (it is from fglrx 8.27.10), and put libGL.so.1 into the /usr/lib/googleearth directory.

Misha

I placed this in ~/google-earth and it at least got Google Earth initialized.  However, Google Earth will only run in a software 3d emulation mode (meaning, it's not utilizing the 3d capabilities of my ATI Xpress 200M card).  I have a healthy installation of xorg-driver-fglrx.  Any idea as to how to get the 3d working correctly?

Thanks,
Jason

---

### Post by Chris11 on 2006-12-21
Meanwhile I upgrades to Edgy, I'v got 3D with the ATI driver, I couldn't get to work the fgrlx driver and it looks like that the fgrlx driver does not work, at least no with a ATI Radeon 9000 Pro. Then I installed Google earth and everything went smooth... I even see my pizza oven in the backyard.. 

Chris

---

### Post by Tibor60 on 2006-12-28
I think googleearth is not ready for linux, only in some special cases... or linux is not ready for googleearth. On the windows boot on my system googleearth is working fast and shiny, in Dapper Drake, with 3D and direct renderin on, is functioning without error messages, but for any changes of the screen I must wait 20-25 minutes. So the best solution to trash googleearth from the linux boot and boot to XP...

---

### Post by angrykeyboarder on 2006-12-28
> **Tibor60 said:**
> I think googleearth is not ready for linux, only in some special cases... or linux is not ready for googleearth. On the windows boot on my system googleearth is working fast and shiny, in Dapper Drake, with 3D and direct renderin on, is functioning without error messages, but for any changes of the screen I must wait 20-25 minutes. So the best solution to trash googleearth from the linux boot and boot to XP...

I've got it running under Windows XP and Ubuntu Edgy on [this box]("http://ubuntuforums.org/showthread.php?p=541266#post541266").  It runs just fine in both Operating Systems. It might be *slightly* slower in Ubuntu but not much.

---

### Post by Tahi_Kiwi on 2006-12-29
I installed the Linux version of Google Earth last night. Google Earth did not seem to recognize my video at all, so it ran super slow in software emulation mode. Awful!

I just ran the uninstall script, and I thought I would check back later on fine tuning my Ubuntu hardware settings. 

Has anyone gotten Google Earth for Linux to run well--fast and stable? I'm running Ubuntu 6.06 as a guest OS under VWware Workstation. Host is Windows XP running on a new computer (two weeks old).

Thank you.

---

### Post by Tibor60 on 2006-12-30
I see. But I have only a 1 GHz Intel Celeron and 512 MB RAM. And still GoogleEarth running smoothly on XP and very poorly in Ubuntu. I still hope that the problem is not in the hardware resources because if it is so, linux is loosing the main advantage: functioning well with less resources then Windows. I hope that we will not have to buy for linux systems "supercomputers" to have the same results as we can have with XP on cheap old PC-s...

---

### Post by petermck on 2007-01-01
I've got google earth running perfectly on Ubuntu 6.10 but there was a bit of a process to it. 
I had to update the drivers for my ATI video card with the proprietry ATI drivers instead of the open source ATI driver since this seems to not support direct rendering (yet). 
You can see if direct rendering is working with glxinfo from the command line.
You should see
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes

at the top.
You may find [http://www.ubuntuforums.org/showthread.php?t=321766&highlight=howto+ati](http://www.ubuntuforums.org/showthread.php?t=321766&highlight=howto+ati) helpful.
Also, I found some advice somewhere on the forum to put the attached library in your google-earth folder, but if things are running real slow (i.e running at all) it's more likely a problem with direct rendering.:cool:

---

### Post by n2j3 on 2007-01-02
> **misha680 said:**
> Download and save this attachment (it is from fglrx 8.27.10), and put libGL.so.1 into the /usr/lib/googleearth directory.

Misha

Worked wonders. Thanks. Only problem is gray areas when i try to add pins or generally when there are menus overlapping the main window. Basic functionality is there though, so I consider it a success. 

ATI 9250 (binary ati drivers)
xubuntu dapper
latest googlearth (downloaded today)

---

### Post by lingenfr on 2007-05-04
> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

The rest of the install is self explanatory, have fun!

Yeah uh, not so much. I ran the bin file with sudo and it crashed X. It would be helpful if someone with a working install would start a new thread with some better instructions. 13 pages of random issues is really not helpful. Thanks.

---

### Post by lingenfr on 2007-05-12
bump

---

### Post by treblesix on 2007-05-13
Installed and works great!

---

### Post by kschelde on 2007-05-14
Thanks for getting google earth working for me. *S*

---

### Post by lingenfr on 2007-05-14
> **lingenfr said:**
> Yeah uh, not so much. I ran the bin file with sudo and it crashed X. It would be helpful if someone with a working install would start a new thread with some better instructions. 13 pages of random issues is really not helpful. Thanks.

Has anyone had a similar experience? Were you able to fix it? How?

---

### Post by treblesix on 2007-05-15
I just did the following in a terminal, and it installed fine.........

wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
sh GoogleEarthLinux.bin

---

### Post by bchymist on 2007-05-29
I ended up with this problem on 7.04

> Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.2414.......................................... ........................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all! 


---

### Post by idahogie on 2007-05-31
> **bchymist said:**
> I ended up with this problem on 7.04

I have the same problem.  Plus I'm new to Linux.  Double-whammy.

Any help?

---

### Post by BenjaminGTF on 2007-06-04
It is also under the medibuntu repository now!

---

### Post by ukripper on 2007-06-09
Add medibuntu repostories - [http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)  and then type following in terminal:

```
sudo apt-get install googleearth
```

Job done.

---

### Post by hrz195 on 2007-06-15
> **lingenfr said:**
> Has anyone had a similar experience? Were you able to fix it? How?

The same problem happened to me. The cause was the fact that I wasn't able to use direct rendering (run glxinfo to see if you're using direct rendering). Using the restricted drivers manager I installed the required NVIDIA driver which enables  direct rendering. After this Google Earth ran fine.

---

### Post by LookTJ on 2007-06-19
I tried to run the uninstall script as root

the output was

```
Could not find a usable uninstall program. Aborting.
```

---

### Post by jtek on 2007-07-01
> **gammyhand said:**
> I have installed earth but running it just gets to the splash screen and nothing else.

I had this exact same problem, running Feisty on a Dell laptop with (I think) ATI video card. All it needed was a reboot. ;-) Now it's working great!

---

### Post by GoneWithTheWind on 2007-07-10
> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

The rest of the install is self explanatory, have fun!

Thanks!  That worked well and it's up.  :)

---

### Post by firmwire on 2007-07-10
I have been all over the forums and have found some very good info for possibly solving my issue.  I am not sure if it will work or not since I am not at home at the moment. I wanted to run some things by you all to make it easier when I do get home.

Issue: 
Running Compiz Fusion ( perfectly) in xgl w/ gnome.  I have fglrx as the driver I am using. I have Composite set to "0"  and have even changed it to "false".
When I run glxinfo I get direct rendering  is NO. 
glxgears works fine in any session I do.
From what I can find, in order for compiz fusion to run it has to be in xgl mode.  But google earth NEEDS direct rendering ( I think).
I think if I just go into a non xgl session the same glxinfo gives me YES for direct rendering. I don't remember though at the moment.
Even so...when I run google earth in any session I get 100% CPU usage from it. It just hangs at the initialization splash screen. I can still kill the process, so it doesn't lock my system up completely. 
I have read that people have been able to get it to work with Beryl and ATI cards running together. I am just trying to figure out how to get it to run with my setup.

In case the question comes up, I have installed it two different ways. I had installed it through Automatix. Then uninstalled it. Then I installed it from the download from the google earth linux download site. Both installs went fine. Both hang and produce 100% cpu usage when activated and hangs on the splash screen.

I found this post [COLOR="Red"][http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636).[/COLOR] Do you think this will solve my problem?

Also I have seen posts about libGL.so.1.bz2 and libGL.so.1.tar.bz2, and I do you think this may fix my issue?

Oh yeah... and I even tried this earlier today: DISPLAY=:0 /usr/local/google-earth/googleearth. It just loads the splash screen and hangs.

I know people have had the issue with 100% cpu usage, but I couldn't find anything saying what they did to fix it or if they were even able to.
I have seen in one place that one person actually installed an extra stick of RAM and that helped. But I don't think I should have to. Everything else works great. I only have 1GB on this system currently.

I am running Feisty 64 and it runs completely stable. I love it!

Any suggestions/solutions are greatly appreciated. Thanks in advance.

---

### Post by firmwire on 2007-07-11
/bump

---

### Post by zutronius on 2007-08-16
It freezes up as soon as I attempt to start the program and always have to end up force quitting it.

---

### Post by soeten on 2007-08-17
Thanks.. Now I just got to get this damn VIA-driver to work. xD

---

### Post by bereanone on 2007-09-07
Install was easy, running it caused Ubuntu to crash.  Black screen, a lot of writting with [OK]'s on the right side, next screen sign in and password.  Wheww what happened?
Newbie (for now)

---

### Post by bob365 on 2007-09-13
When I try the to open google earth i get a black screen and i get kicked back to the login screen. I need help. thanks, bob

---

### Post by frogitts on 2007-09-16
This same problem happens to me a lot, actually. I have an Intel 915GM graphics card on my Inspiron B130 laptop, and I can't run applications that require full screen/ decent graphics. I figured out that this is linked to Beryl. I can run Beryl fine, but when I try to to run (for example) Open Arena, it crashes, restarting the operating system (I think), running my startup file (which is part of the black screen), and finally landing me on the login page (even though I have it set to automatic login. Simply changing to the Metacity window manager has solved this problem for me, but it's still sad, because I want to use both! If anyone knows how to use programs like this under Beryl with the 915GM (with, of course, all of the drivers installed, etc), I would like to know, because I've been scouring forums for months to no avail.

---

### Post by geneb711 on 2007-09-17
Have same problem as many of the other posts.  Click on icon for Google Earth, screen goes black and have to restore session.  Anyone find out how to correct this problem???

---

### Post by 2wanderers on 2007-09-20
This seems to be a problem with display drivers.

I found two fixes - [this one]("http://blog.mypapit.net/2006/06/google-earth-on-ubuntu-dapper-video.html"), which made it work, but very slowly.

The ultimate solution was to install the proprietary graphics drivers, in my case nVidia drivers.  Works great now.

---

### Post by madds007 on 2007-10-09
Hi all

I Typed sudo apt-get install google earth to install from the medibuntu repos it downloaded and i got the configuring google earth screen in the terminal window, but cannot select the 'ok' on the license agreement what am i doing wrong?

---

### Post by rakesh_bhalla81 on 2007-11-21
got this problem whle installing google earth kindly help

[I]poseidon@poseidon-desktop:~$ wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
--12:16:27--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 72.14.203.91
Connecting to dl.google.com|72.14.203.91|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
12:16:32 ERROR 404: Not Found.[/I]

---

### Post by subpar on 2007-11-25
> **rakesh_bhalla81 said:**
> got this problem whle installing google earth kindly help

[I]poseidon@poseidon-desktop:~$ wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
--12:16:27--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 72.14.203.91
Connecting to dl.google.com|72.14.203.91|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
12:16:32 ERROR 404: Not Found.[/I]


You can always download the bin file from earth.google.com website. It'll give you the linux version. I tried to wget the new location of the file (wget [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)), but it gave me this:

```
subpar@lolputer:/home/guests$ wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
--19:04:36--  http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 72.14.203.91
Connecting to dl.google.com|72.14.203.91|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 23,042,785 (22M) [application/octet-stream]
GoogleEarthLinux.bin: Permission denied

Cannot write to `GoogleEarthLinux.bin' (Permission denied).

```

Here's a link: [http://earth.google.com/tour/thanks-linux4.html](http://earth.google.com/tour/thanks-linux4.html)

---

### Post by EriCr on 2007-11-28
> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

The rest of the install is self explanatory, have fun!
I tried this but I get an error telling me the file cant be found.
I also tried downloadind through Mozilla but the graphical installer wont open the .bin file.

See screenshot

Any ideas?

EriCr

---

### Post by kd5ob on 2007-11-30
root@roam:~/googleearth# sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
root@roam:~/googleearth# 

///  AND BOOM!!!!

---

### Post by subs on 2007-11-30
thnx.... works gr8!!

---

### Post by Steve.Chevalier on 2007-11-30
For some reason I got a 404 on this link.  I just went to here, [http://earth.google.com/](http://earth.google.com/), and followed the download links. Works great!!!! Thank you!

---

### Post by RevolutionMaster on 2007-12-02
that didn't work. 
I changed it and got the following to work:

> wget [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)
sh GoogleEarthLinux.bin

---

### Post by Roasted on 2007-12-14
I tried using

wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
sh GoogleEarthLinux.bin

I also tried sudo apt-get install googleearth.

Both yield google earth freezing upon starting it up. It'll pop up with it's typical Google Earth screen and eventually fade to gray. Then it just sits there.....

---

### Post by aypnoia on 2007-12-15
Try un-installing anything you have (there is an uninstall icon in google earth directory) and re-install with sh GoogleEarthLinux.bin
If you have compiz turn it off (no visual effects) and restart X before installation. Google earth and compiz don't like each other, in fact compiz doesn't like any 3d stuff

---

### Post by omega_user on 2007-12-16
thank you very much. Works great, don't think I'll bother uninstalling this!

---

### Post by The Spy on 2007-12-16
Okay, It´s not working. When I type in the command to download Google Earth (wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)) in the Terminal I get a 404 Error. Any idea what the problem might be?
I´m running Gutsy Gibbon 7.10

I did download the file straight from Google.com, but when I try to install it in the Terminal using the command: sh GoogleEarthLInux.bin, it says it can´t find the file.
Thanx

---

### Post by Frankly Francois on 2007-12-16
> **The Spy said:**
> Okay, It´s not working. When I type in the command to download Google Earth (wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)) in the Terminal I get a 404 Error. Any idea what the problem might be?
I´m running Gutsy Gibbon 7.10

Yeah, the code on the first post didn't work for me either. But, I followed RevolutionMaster's post and it worked.

> 
wget [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)
sh GoogleEarthLinux.bin

But careful on how you copy the code into terminal. This forum automatically shortens url length, so if you copy the text above with the old "crtl+c" method it's just going to copy as "http://dl.google.com/earth/client/cu...EarthLinux.bin" 
Right click and copy link location to get the full url.

---

### Post by The Spy on 2007-12-18
Hey, thanks Frankly Francois. It downloaded and installed fine, and runs great!:guitar:

---

### Post by justinclark on 2007-12-20
Help! It seems to have installed fine but when I try to launch the google earth screen comes on and then just closes.

---

### Post by tollboy on 2007-12-23
```
]Quote:
Originally Posted by The Spy View Post
Okay, It´s not working. When I type in the command to download Google Earth (wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)) in the Terminal I get a 404 Error. Any idea what the problem might be?
I´m running Gutsy Gibbon 7.10
Yeah, the code on the first post didn't work for me either. But, I followed RevolutionMaster's post and it worked.

Quote:
wget [http://dl.google.com/earth/client/cu...EarthLinux.bin](http://dl.google.com/earth/client/cu...EarthLinux.bin)
sh GoogleEarthLinux.bin
But careful on how you copy the code into terminal. This forum automatically shortens url length, so if you copy the text above with the old "crtl+c" method it's just going to copy as "http://dl.google.com/earth/client/cu...EarthLinux .bin"
Right click and copy link location to get the full url.
```

sry i dont know hw to do refrence thats why using this CODE for the post
I TRIED EVERY THINGH 
bt it is saying that not found

---

### Post by NoPoChris on 2007-12-29
the url has apparently changed:

[http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)

---

### Post by dixopr on 2007-12-30
Googleearth installs fine then locks on the initializing start page????

---

### Post by mugg326 on 2007-12-31
I'm running Gutsy and followed the terminal install instructions at the beginning of the howto, but I just get the following message:
[FONT="Times New Roman"]
sh: Can't open GoogleEarthLinux.bin[/FONT]

Any ideas?

---

### Post by Tristam Green on 2007-12-31
[quote=Google Earth]We understand. The first time you launch Google Earth, you'll check out your house, your school, and your office. Got that out of your system? Good. Now let's talk about what Google Earth can really do.[/quote]
That sounds a mite pretentious, or is it just me?

Here's where mine freezes from the terminal:

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
```

---

### Post by charlescarroll1 on 2008-01-01
I followed the above instructions, and have installed google earth, but does not load up when I try to run it.  All I get is the google earth splash screen, and does nothing...

HELP ME!!!!

---

### Post by VidiotGeek on 2008-01-05
> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

The rest of the install is self explanatory, have fun!

Ok...I feel like an idiot for this somehow not working for me, but I don't know what else to do. The file is saved on my desktop so I cd in terminal to home/Desktop before I try to execute the command. This is my result each time I try to install.

```
sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................

```

Then it stops & gives me a new prompt. No results, no further installation instructions...nothing. Someone tell me the ridiculously stupid thing I'm overlooking here. Help a total newcomer to Ubuntu from a Mac/Win background. :)

---

### Post by Ryo964 on 2008-01-07
Thanks Misha, 
   Worked great to get past splash screen for: 

Gutsy 7.10 64 AMD
Dell Inspiron 1501

Thanks again

---

### Post by Ryo964 on 2008-01-07
Thanks Misha!
   Worked great (not even all that slow) to get past splash screen for GE on: 

Gutsy 7.10 AMD 64 
Dell Inspiron 1501

---

### Post by tabris37 on 2008-01-11
I am running the latest download of googleearthlinux.bin and it dosnt work at all! I had an older version that worked great but It is gone now.
the new version restarts ubuntu right after the splash screen. please help me fix it! i tried this  $sudo vi /etc/X11/xorg.conf and i got a whole bunch of junk and supposedly if I change the defaltdepth from 24 to 16 it just might work, but i cant seem to figure out how to edit the file. does anyone know how that works? I need a hand.

---

### Post by dcstar on 2008-01-11
There is a package in the repositories (Multiverse) called** googleearth-package** that downloads the latest .bin file (when you modify the file path config that Google changed) and creates a .deb package that you install.

This sets up all the Ubuntu menu items and seems to be more reliable than using the generic Linux .bin file.

I have used it to create an installable GoogleEarth .deb for my AMD-64 system, and it works perfectly:

[http://ubuntuforums.org/showthread.php?t=601272](http://ubuntuforums.org/showthread.php?t=601272)

---

### Post by eabadham on 2008-01-15
OPS! Just realized the answer is on the post above :)

---

### Post by whoscheesemine on 2008-03-04
Yeah, so I'm trying to install Google Earth and I found this debian package:

[http://packages.debian.org/googleearth-package](http://packages.debian.org/googleearth-package)

After I installed it, in the upper right hand corner (I'm using Xubuntu by the way, I guess you'd call it the task manager in Winblows) it showed that there was an update to create a package called "googleearth-package" well I installed it but when I search for this file I can't find it. I thought that perhaps if I saw past things that have happened in the terminal I might be able to figure it out.

---

### Post by RhynoWoody on 2008-03-08
Fabulous.  This worked swimmingly.  Thanks Everybody!

---

### Post by breaking on 2008-03-08
The googleearth-package deal installed fine for me, but it's unbearably slow and jerky:(. 
I've tried running without compiz and LIBGL_ALWAYS_INDIRECT=true, but all with barely noticeable improvements. I'm on Gutsy, with the restricted nvidia driver on my geforce FX go5600 (128mb) and a P4 2.8ghz. 1gb ram.
EDIT: oops, it turns out I wasn't using the correct restricted driver after all. With the right driver it works much better, though still has its uncomfortable moments. For example, I can't get the flight simulator mode to do anything but freeze.

---

### Post by kiisu on 2008-03-12
I was up late last night and then again this morning working on getting Google Earth to work.

Installing from both sudo-apt and from Synaptic didn't work (I'm using Mint by the way). In both cases it was there and installed but nothing would happen when I tried to run it.

Eventually I tried this, from earlier in the thread:
> wget [http://dl.google.com/earth/client/cu...EarthLinux.bin](http://dl.google.com/earth/client/cu...EarthLinux.bin)
sh GoogleEarthLinux.bin 
Which worked but I had to delete the old files before it would launch from the icon. Oh and be sure to right click and select save the full link, rather than just copying the code posted above - the link is shortened here in the forums I think>?

Now all is good. Hopefully this might help someone else in my position.

---

### Post by luvit on 2008-03-15
I just installed Google Earth with ease in just a few steps.
Please [see my blog ]("http://www.yay4u.com/2008/03/install-google-earth.html")for simple intructions that worked for me ;)

---

### Post by CD27 on 2008-03-17
```
eric@eric-laptop:~$ wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
--19:08:00--  http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 209.85.133.176
Connecting to dl.google.com|209.85.133.176|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:08:01 ERROR 404: Not Found.

eric@eric-laptop:~$ sh GoogleEarthLinux.bin

```

---

### Post by martin saint martin on 2008-03-22
i ran this :   wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
--15:17:05--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)

and i got this:           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 209.85.133.176
Connecting to dl.google.com|209.85.133.176|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:17:07 ERROR 404: Not Found.

what does this mean?

---

### Post by luvit on 2008-03-22
Visit [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)
type: sudo sh ./GoogleEarthLinux.bin

see my [[COLOR="Blue"]_blog_[/COLOR]]("http://http://www.yay4u.com/2008/03/install-google-earth.html") for finer details
it's really easy... i don't know where you found instructions, but i have used my method on four different distros: [[COLOR="Blue"]_two easy steps_[/COLOR]]("http://http://www.yay4u.com/2008/03/install-google-earth.html")

---

### Post by martin saint martin on 2008-03-30
i'm sorry but it is still not working right.  i did what your blog had said and this is what i got:
martin@martin-desktop:~$ cd Desktop
martin@martin-desktop:~/Desktop$ sudo sh ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................

(setup.gtk2:7325): Gtk-WARNING **: Error loading theme icon 'gtk-cancel' for stock: Unable to load image-loading module: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: cannot open shared object file: No such file or directory
Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...
googleearth

then it will go to the "initializing" screen and stay there.  using ubuntu 64bit if that makes a difference.

---

### Post by luvit on 2008-03-30
64 bit does make a difference. I am not aware of 64bit for google earth.

I struggled for a long time trying to be a 64 bit user and more than half of the apps I wanted did not exist for 64 bit... like Adobe Flash Player.  Using 32bit I felt less stress... I really wanted 64 bit since I have Dual Core,,, but I'm not disappointed at 32bit.

Have you been using 64 bit for long? :)

---

### Post by martin saint martin on 2008-03-31
64bit ubuntu has been the only ubuntu i've used, since i have a athlon X2.  i thought why not take advantage of what my hardware can do?  do you know how to run 32bit stuff on a 64bit OS or can you show me a thread that talks about this?  one more thing i'm just using the onboard graphics, could that be what is keeping the program from working right?

---

### Post by luvit on 2008-03-31
I do not know how to run 32bit packages on a 64bit OS install.
I downgraded to 32bit OS install for this reason.

I don't believe the Video Hardware or driver would cause the package to fail installation... 


I will tell you that Google Earth on both of my Linux boxes is flaky on the graphics side... dialog boxes fight for foreground focus. My windows version is flawless.

I have yet to determine if I can fix the boxes fighting for foreground focus.

---

### Post by dsplabs on 2008-04-03
What I did first was:
```
sudo apt-get install googleearth*
```

But that only installs a utility for making a Debian package of Google Earth, so then I downloaded GoogleEarthLinux.bin and run

```
sh GoogleEarthLinux.bin
```

And that worked fine.

```

Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
Installing mimetypes...
Installing desktop menu entries...
mkdir: `/home/kamil/.config/menus/applications-merged': Permission denied
touch: cannot touch `/home/kamil/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu': Permission denied
Installing desktop icon...

```

---

### Post by quasar277 on 2008-04-10
> **luvit said:**
> 
I will tell you that Google Earth on both of my Linux boxes is flaky on the graphics side... dialog boxes fight for foreground focus. My windows version is flawless.

I have yet to determine if I can fix the boxes fighting for foreground focus.

What graphic card drivers are you using? The only way google earth is not giving me that problem is if I'm running ATI proprietary drivers... which is a pity.

---

### Post by luvit on 2008-04-10
> **quasar277 said:**
> What graphic card drivers are you using? The only way google earth is not giving me that problem is if I'm running ATI proprietary drivers... which is a pity.

it is a pity... i get the same foreground focus-fighting problem with flash menus on some websites... like nav-bar pull-down menus hide behind "flash rotating billboard" pics....

I've never looked at my driver info before... I've not had time to troubleshoot it since it only bites me once a week.

I have:
Mobile PM965/GM965/GL960
intel - experimental modesetting driver for I...
vesa - Generic VESA-compliant video cards

---

### Post by quasar277 on 2008-04-21
> I've never looked at my driver info before... I've not had time to troubleshoot it since it only bites me once a week.


Then you should be 'fine' :)

I have no idea about Intel Mobile chipsets. There are some tutorials on ubuntu documentation but they're for ati and I think nvidia too.
If you do a search on the forums I'm pretty sure you'll find something. But try the Docs as well.

C.

---

### Post by evil_urna on 2008-05-12
Does it take a real long damm time to install for anyone else?

---

### Post by finalcut on 2008-05-12
u can find some pretty sweet stuff on google earth

---

### Post by evil_urna on 2008-05-13
> **finalcut said:**
> u can find some pretty sweet stuff on google earth

REALLY? I never knew.

---

### Post by KhanTG on 2008-05-18
> **evil_urna said:**
> Does it take a real long damm time to install for anyone else?

installing wasn't an issue for me... went right in (i just had to get the right path for the *.bin)  I am not getting the maps after the interface loads.  Anybody have suggestions?

---

### Post by hanzahar on 2008-05-19
>  wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
--20:04:36--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 209.85.133.91
Connecting to dl.google.com|209.85.133.91|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:04:36 ERROR 404: Not Found.This came out...why? :(

---

### Post by pasargad on 2008-05-19
> **hanzahar said:**
> This came out...why? :(

i have the same problem,where is the problem:confused:

---

### Post by Raccoon1400 on 2008-05-19
I had the same issue. Just download it manually.

---

### Post by Krypttt on 2008-05-27
EDIT:
Ever mind this.

---

### Post by BLTicklemonster on 2008-05-29
[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

Save it to your /home/yourname directory, then in terminal, type

cd /home/yourname

then

sh GoogleEarthLinux.bin

and follow the directions.

Pretty easy?

---

### Post by gonella on 2008-05-29
> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

The rest of the install is self explanatory, have fun!

I have installed Google Earth in my Kubuntu 8.04, but when I try to run it my kubuntu logs off by it self. What should be the problem?

---

### Post by fuzzyl0g1c on 2008-05-29
oops!

---

### Post by stmcc on 2008-05-29
I have been trying to install googleearth for some time. I am dual booted with Win XP and it works fine on Xp. When I try to install it on ubuntu 8.4 ,the screen is black and there is no info on the left pane. I get this:
googleearth-bin: main/renderbuffer.c:2153: _mesa_reference_renderbuffer: Assertion `oldRb->Magic == 0xaabbccdd' failed.
Google Earth has caught signal 6.

Stacktrace from glibc:
  ./googleearth-bin [0x804f403]
  ./googleearth-bin [0x804f916]
  [0xb7f6b420]
  /lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7118a01]
  /lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb711010e]
  /usr/lib/dri/unichrome_dri.so(_mesa_reference_renderbuffer+0x14e) [0xb079e32e]
  /usr/lib/dri/unichrome_dri.so(_mesa_free_framebuffer_data+0x67) [0xb0779537]
  /usr/lib/dri/unichrome_dri.so(_mesa_destroy_framebuffer+0x26) [0xb0779626]
  /usr/lib/dri/unichrome_dri.so(_mesa_unreference_framebuffer+0x6b) [0xb07793ab]
  /usr/lib/dri/unichrome_dri.so [0xb0735e40]
  /usr/lib/dri/unichrome_dri.so [0xb072b6f0]
  /usr/lib/dri/unichrome_dri.so [0xb072b0be]
  /usr/lib/dri/unichrome_dri.so [0xb072b2f5]
  /usr/lib/libGL.so.1 [0xb6686113]
  /home/mac/google-earth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext22internalDestroyContextEv+0x41) [0xb3e34fa1]
  /home/mac/google-earth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext12userDestructEv+0x7b) [0xb3e6ddbb]
  ./libIGCore.so(_ZNK3Gap4Core8igObject15internalReleaseEv+0x8b) [0xb69ee44b]
  /home/mac/google-earth/libevll.so(_ZN5earth4evll13VisualContextD2Ev+0xff) [0xb3a3efdf]
  /home/mac/google-earth/libevll.so(_ZN5earth4evll17VisualContextUnixD0Ev+0x2d) [0xb3c9707d]
  /home/mac/google-earth/libevll.so(_ZN5earth4evll17RenderContextImplD0Ev+0x1cf) [0xb3be951f]
  /home/mac/google-earth/libevll.so(_ZN5earth4evll17RenderContextImpl15DeleteSingletonEv+0x2e) [0xb3bc6e2e]
  /home/mac/google-earth/libevll.so(_ZN5earth4evll7APIImpl19deleteRenderContextEv+0x17) [0xb3b3f757]
  /home/mac/google-earth/libevll.so(_ZN5earth4evll7APIImpl8shutdownEv+0x36) [0xb3b3f8f6]
  /home/mac/google-earth/libevll.so(_ZN5earth4evll7APIImplD0Ev+0x2d) [0xb3b4747d]
  /home/mac/google-earth/libevll.so(_ZN5earth4evll7APIImpl15DeleteSingletonEv+0x2b) [0xb3b3f59b]
  /home/mac/google-earth/libevll.so(releaseApi+0x17) [0xb3b3f977]
  ./libapiloader.so(_ZN5earth4evll9ApiLoader10releaseApiEv+0x19) [0xb69655f9]
  ./libmoduleframework.so(_ZN5earth6module13ModuleManagerD0Ev+0x8a) [0xb681d47a]
  ./libmoduleframework.so(_ZN5earth6module13ModuleContextD0Ev+0x31) [0xb681ccd1]
  ./libmoduleframework.so(_ZN5earth6module13ModuleContext15DeleteSingletonEv+0x26) [0xb681ac86]
  ./libgoogleearth_lib.so(_ZN5earth6client11ApplicationD1Ev+0x24c) [0xb72cfb5c]
  ./googleearth-bin(main+0x2c4) [0x8050bf4]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7102450]
  ./googleearth-bin [0x804f231]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/mac/.googleearth/crashlogs/crashlog-F8642F8

---

### Post by keanu_reeves on 2008-06-25
404 error coming has google changed the path?

---

### Post by Orfintain on 2008-06-26
I got the same 404 error , google's site allowed me to download a bin file for it for linux so it should be possible , I guess the real question is how did I use linux for 6 month's and still not know how to install from a bin file....

---

### Post by VTshredder on 2008-06-26
also getting the 404 error....

vtshredder@Slip:~$ wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
--20:41:17--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 209.85.133.136, 209.85.133.93, 209.85.133.190, ...
Connecting to dl.google.com|209.85.133.136|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:41:17 ERROR 404: Not Found.

vtshredder@Slip:~$ sh GoogleEarthLinux.bin
sh: Can't open GoogleEarthLinux.bin
vtshredder@Slip:~$

---

### Post by NuxIT on 2008-06-29
Hi, I installed google earth 4.3 just recently. I had 4.2 and it worked fine with my default user. I downloaded the 4.3 bin file and used that install method following this guide:
[http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/]("http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/")

However, whenever I run it with my default user everything is "greyed out" and their is no earth. I have to run it as sudo from terminal to get it to come up correctly. I tried changing the ownership of two files. Google-googleearth.desktop and using the chown command. It added styles user to the ownership. 
```
-rw-rwx--- 1 styles styles  620 2008-06-29 20:33 Google-googleearth.desktop
styles@t60:/home/apps/google-earth$ ls -l G*.*
-rw-r--r-- 1 root root 426 2008-06-29 01:12 Google-googleearth.desktop

```

Even with styles added it still has everything greyed out and no earth unless launched with sudo. Any ideas? Thanks

EDIT:
I didn't realize the answer is on the same page from the install link I listed above. 
I did this:

Here&#8217;s how to fix the &#8220;only works with sudo&#8221; problem
in your homedir, cd .config/Google, then do &#8217;sudo chown [you user name] GoogleEarthPlus.conf&#8217;

Next time you run googleearth, it&#8217;ll show you an error message about not being able to write to /root/.googleearth, and that it will use your homedir instead&#8230;

Hope this helps others!

---

### Post by nikolaos on 2008-06-30
For those like me, to who google earth is ridiculously slow, just go to View and disable the Atmosphere feature. It worked for me, hope it does for you to.

---

### Post by booleanB on 2008-07-02
error 404 with the first command

but download it separately and thengo through 

'sh GoogleEarthLinux.bin' this

---

### Post by lu.victor2008 on 2008-07-04
> **nikolaos said:**
> For those like me, to who google earth is ridiculously slow, just go to View and disable the Atmosphere feature. It worked for me, hope it does for you to.

HAHHA! Thank You so much. I reinstalled Google Earth several times for its slowness. Now it runs pretty well.

---

### Post by Fatfool on 2008-07-05
> **NuxIT said:**
> Hi, I installed google earth 4.3 just recently. I had 4.2 and it worked fine with my default user. I downloaded the 4.3 bin file and used that install method following this guide:
[http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/]("http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/")

However, whenever I run it with my default user everything is "greyed out" and their is no earth. I have to run it as sudo from terminal to get it to come up correctly. I tried changing the ownership of two files. Google-googleearth.desktop and using the chown command. It added styles user to the ownership. 
```
-rw-rwx--- 1 styles styles  620 2008-06-29 20:33 Google-googleearth.desktop
styles@t60:/home/apps/google-earth$ ls -l G*.*
-rw-r--r-- 1 root root 426 2008-06-29 01:12 Google-googleearth.desktop

```

Even with styles added it still has everything greyed out and no earth unless launched with sudo. Any ideas? Thanks

EDIT:
I didn't realize the answer is on the same page from the install link I listed above. 
I did this:

Here&#8217;s how to fix the &#8220;only works with sudo&#8221; problem
in your homedir, cd .config/Google, then do &#8217;sudo chown [you user name] GoogleEarthPlus.conf&#8217;

Next time you run googleearth, it&#8217;ll show you an error message about not being able to write to /root/.googleearth, and that it will use your homedir instead&#8230;

Hope this helps others!
yep that helped a lot. been searching for a solution to the sudo problem for weeks now. that fixed it. thanks!!

---

### Post by NuxIT on 2008-07-05
> **Fatfool said:**
> yep that helped a lot. been searching for a solution to the sudo problem for weeks now. that fixed it. thanks!!

Sure, glad that worked for you!:guitar:

---

### Post by SusieSA on 2008-07-23
> **booleanB said:**
> error 404 with the first command

but download it separately and thengo through 

'sh GoogleEarthLinux.bin' this
Hi,
I used the quote you suggested relating to the 404 ERROR, and got this reply :

sally@sally-desktop:~$ sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.3.7204.836..............................................................
loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...

Still unable to read the script, and the world blacked out.  Can you help further?
Ta.
Suzie SA

---

### Post by SusieSA on 2008-07-23
Hi,
I used the quote you suggested relating to the 404 ERROR, and got this reply :

sally@sally-desktop:~$ sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.3.7204.836...................................... ........................
loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...

Still unable to read the script, and the world blacked out. Can you help further?
Ta.
Suzie SA

---

### Post by astroorion on 2008-07-26
I was able to get google earth to run
Thank's to the post by BLTicklemonster on post # 189

---

### Post by dunbrokin on 2008-07-31
I got Google Earth to run....but it is so sllloooowwww....

I have 2G and am on 8.04.

---

### Post by gjoellee on 2008-07-31
I woul say installing GooogleEarth +much more other software i easies to istall with ULTAMATIX! Download: [http://linux.softpedia.com/progDownload/Ultamatix-Download-24551.html](http://linux.softpedia.com/progDownload/Ultamatix-Download-24551.html)

---

### Post by gjoellee on 2008-07-31
by the way....Google Earth works VERY good in Intrepid Ibex, but not in hardy (this is what I am experiencing)

---

### Post by Claudestephane on 2008-08-03
I was delighted to find your post on Google Earth installation, but please find a screen scrape of my terminal session. Help clearly still needed, as installation never took place. 

claude@claude-laptop:~$ wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
--01:02:08--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 209.85.133.190, 209.85.133.93, 209.85.133.136, ...
Connecting to dl.google.com|209.85.133.190|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
01:02:08 ERROR 404: Not Found.

claude@claude-laptop:~$ sh GoogleEarthLinux.bin


Claudestephane

---

### Post by jetta on 2008-08-04
> **dsplabs said:**
> What I did first was:
```
sudo apt-get install googleearth*
```

But that only installs a utility for making a Debian package of Google Earth, so then I downloaded GoogleEarthLinux.bin and run

```
sh GoogleEarthLinux.bin
```

And that worked fine.

```

Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
Installing mimetypes...
Installing desktop menu entries...
mkdir: `/home/kamil/.config/menus/applications-merged': Permission denied
touch: cannot touch `/home/kamil/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu': Permission denied
Installing desktop icon...

```

thx to dsplabs, this post work fine with me..
i'm currently running Hardy with Centrino Core 2 Duo, Intel Graphics Media Accelerator X3100, 1G DDR2.

---

### Post by jeffegg2 on 2008-08-04
I installed google earth. what a mistake!! everytime I run it it disables my wireless...then I have to do a resore of a backup...

bye google earth.

---

### Post by heinlich on 2008-08-06
I also downloaded it and it worked fine on my laptop, the only problem is every time I click on the map or drag the map, the area blinks, and also for clicking on the photo people shared. So goodbye google earth for me too, at least right now

---

### Post by geezerone on 2008-08-07
Installed version 4.3 but won't load as unable to identify the graphics card? 

I am using Nvidia 6600 which isn't the kindest as when trying to use accelerated driver I had to reboot into recovery mode and fix X-Server to stop the black screen appearing.

---

### Post by zenithdave on 2008-08-10
'Here&#8217;s how to fix the &#8220;only works with sudo&#8221; problem
in your homedir, cd .config/Google, then do &#8217;sudo chown [you user name] GoogleEarthPlus.conf&#8217;

Next time you run googleearth, it&#8217;ll show you an error message about not being able to write to /root/.googleearth, and that it will use your homedir instead&#8230;'

That worked here thanks a lot :D

running fine in full screen now :mrgreen:

---

### Post by grouchyolddude on 2008-08-16
[http://ubuntuforums.org/search.php?searchid=46412312](http://ubuntuforums.org/search.php?searchid=46412312)

I managed to find the "fix" for my font issue, but recieve a slightly different read out from the config, google command..
can someone tell me exactly whoich seetting I need to change??
[General]
AnimSpeed=1
CachePath=/root/.googleearth/Cache
ClampBegin=false
ControllerEnabled=false
ControllerMode=2
DisableNavCheckbox=false
InvertMouseWheel=false
KMLPath=/root/.googleearth
Key="KF2vnIDUh1c="
LogoutClean=true
NavMode=0
NavigatorShow=0
PolyEditXPos=69
PolyEditXSize=422
PolyEditYPos=74
PolyEditYSize=552
RepeatMode=1
ReverseControls=false
SMode=true
SwoopEnabled=true
TimeFolderRestrict=false
TimeShow=1
TimeZoneHours=-6
TimeZoneMinutes=0
TimeZoneMode=1
TimeZoneName=Local
UID="0TsuRF0Wp27Uw6ss7bWoaQ=="
VID="AAAADTQuMy43MjA0LjA4MzY="
currentVersion=4.3.7204.0836
defaultBrowser=true
enableTips=true
hiddenWindows-4_3=@Invalid()
lastHeight=693
lastLeft=0
lastTip=7
lastTop=0
lastWidth=1024
layersOpen=true
mouseWheelSpeed=1
osName=Linux
placesOpen=true
renderWarning-OGLsoftwareEmulated=false
searchOpen=true
shown_GPS=false
shown_LeftPanel=true
shown_RenderFrame=true
shown_Ruler=false
visibleWindows-4_3=RenderWindow, ServerWindow
wasFullScreen=false
wasMaximized=true

[Render]
CompassVisible=true

[UsageStatistics]
firstRun\day=13
firstRun\hour=21
firstRun\minute=1
firstRun\month=8
firstRun\second=55
firstRun\year=2008

[COLOR="Blue"]I don't find any font size under "render" as the others have.. ???[/COLOR]

---

### Post by McTek on 2008-08-17
This URL no longer valid

---

### Post by alek01 on 2008-08-21
Hi,
Thank you for the HowTo. However, I am getting this error message:
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.3.7284.3916..............................................................
No protocol specified

I'm using 8.04 and an NVidia card on Asus S96S. I've left the Google Earth file on the Desktop. Any idea what is happening and solutions?

Thanks a lot.

Alek

WHat protocal do I need to specify and how/where?

---

### Post by linuxguymarshall on 2008-08-21
I know a lot of people are going to yell at me for this but..... I think Automatix installs Google Earth

---

### Post by simuflite on 2008-08-22
Trying to install I get the following error:

cweyer@cweyer-laptop:~/Desktop$ sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.3.7284.3916..............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
cweyer@cweyer-laptop:~/Desktop$

Ideas?

---

### Post by hopkinsjeni on 2008-08-24
I've tried to install GoogleEarth using the info on this forum but my terminal keeps saying this:

--15:29:37--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 66.102.9.136, 66.102.9.190, 66.102.9.93, ...
Connecting to dl.google.com|66.102.9.136|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:29:38 ERROR 404: Not Found.

Can anyone help?
I also tried to install using the instructions on google and that was no help either, the program would download onto my desktop but wouldn't install or do anything. Any help would be greatly appreciated!

---

### Post by hopkinsjeni on 2008-08-24
> **Frankly Francois said:**
> Yeah, the code on the first post didn't work for me either. But, I followed RevolutionMaster's post and it worked.



But careful on how you copy the code into terminal. This forum automatically shortens url length, so if you copy the text above with the old "crtl+c" method it's just going to copy as "http://dl.google.com/earth/client/cu...EarthLinux.bin" 
Right click and copy link location to get the full url.


This worked beautifully for me! Thank you!

---

### Post by ft566 on 2008-08-27
> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

The rest of the install is self explanatory, have fun!

I tried this but an error came up saying that it wasn't found.

---

### Post by hopkinsjeni on 2008-08-28
Check my post #220 (I think) that definitely worked for me after my terminal kept saying the same thing as yours.

---

### Post by hopkinsjeni on 2008-08-28
> **ft566 said:**
> I tried this but an error came up saying that it wasn't found.
Check out my post #220 that definitely worked for me after I had the same error as you.

---

### Post by fragimar on 2008-09-01
I was having problems so I went to earth.google.com to see where the download location was on their site. It seems they updated the software and the url is different. This terminal code worked for me.


wget [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)
sh GoogleEarthLinux.bin

---

### Post by Scrotnig on 2008-09-01
vBulletin curtails the URL....use this:
```
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

---

### Post by ExWindowsDude on 2008-09-01
> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

The rest of the install is self explanatory, have fun!

******************************************
Wanted to give everyone an Updated URL path that worked for me.
(the above path is out of date---404).
Google Earth Install
```

wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin

```
After you have downloaded it run:
```

sh GoogleEarthLinux.bin

```

******************************************

Have Fun!:)

---

### Post by Kooothor on 2008-09-02
Hey I don't know about you but I keep having white screens each time I zoom or move. It's just blank for like a microsecond, but very annoying. Does anyone happen to have this bug also ?

I'm running Ubuntu Hardy on latest Macbook.

---

### Post by ExWindowsDude on 2008-09-02
> **Kooothor said:**
> Hey I don't know about you but I keep having white screens each time I zoom or move. It's just blank for like a microsecond, but very annoying. Does anyone happen to have this bug also ?

I'm running Ubuntu Hardy on latest Macbook.

Me too, my Google Earth is PAINFULLY slow (at least for my expectations for Linux/Xubuntu).

It can take "minutes" (2-3) to load and move around,etc.
I monitored my CPU usage and it spikes pretty high (60%+)....

Google Earth is PAINFULLY slow on Windows Too....so I'm assuming it's just a "Product" issue.....

---

### Post by mauris on 2008-09-04
I have downloaded the "GoogleEarthLinux.bin" (both: website and command line), but when when I use the command: "sh GoogleEarthLinux.bin", I get the following error: "sh: Can't open GoogleEartLinux.bin"
What am I doing wrong? :)

EDITED
I just repeated the same command and finally started the installation. 
But ... ;) now I have a different problem. Google does not like my graphic card :(
(Presario v3000, NVIDIA, turion 64x2).

---

### Post by Dead Angel on 2008-09-06
Delete this post. I'm a chicken little.

---

### Post by madsmaddad on 2008-09-07
I have same problem as message 190. I get a central splash logo for google earth, and then the computer logs off. 

It did install in my desktop/googleearth however. 

should I uninstall and make it install in usr/local/googleearth?

---

### Post by Milambar on 2008-09-14
The download location has changed yet again.

It is now: 

[http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)

But you can't seem to access it via wget, only via a web browser as you need to click on an "I accept" link, and accept a cookie.

Of course, you can't actually install it once you manage to get it...

```

root@newcore:~# sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.3.7284.3916..............................................................
You don't seem to be running an X server (no DISPLAY set).
Google Earth and its installer both require X11.
Aborting...

```

---

### Post by DManX04 on 2008-09-15
So I've gotten the program installed. The splash screen comes up and the window opens showing the stars and the menu bar on the right. However, then I get an "error:29" message saying that it can't connect to the website. I've tried this on several different networks, and they all say the same thing. Any advice?

---

### Post by adamogardner on 2008-09-16
I didn't get mine :

adamogardner@CRONUS:~$ wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
--20:56:11--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 209.85.133.91, 209.85.133.93, 209.85.133.136, ...
Connecting to dl.google.com|209.85.133.91|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:56:12 ERROR 404: Not Found.

adamogardner@CRONUS:~$ sh GoogleEarthLinux.bin

---

### Post by flyboy917 on 2008-11-09
Just installed it on the 64bit version of 8.04. Works just fine.
:)

---

### Post by artist on 2008-12-01
> **charlescarroll1 said:**
> I followed the above instructions, and have installed google earth, but does not load up when I try to run it.  All I get is the google earth splash screen, and does nothing...

HELP ME!!!!
I can not run it correctly as a common user, maybe just like what you got. But I can run it as the supper user. I don't know why.

---

### Post by AlexPozz26 on 2008-12-04
I tried typing that initial command in, and this is the error message I get:

alex@gretchen:~$ wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
--13:13:03--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 72.14.207.93, 72.14.207.136, 72.14.207.190, ...
Connecting to dl.google.com|72.14.207.93|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
13:13:03 ERROR 404: Not Found.

---

### Post by phantom3113 on 2008-12-04
I get the same issue. Upon putting the initial command from the first post, I get this:

```
laptop:~$ wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin sh GoogleEarthLinux.bin
--17:23:32--  http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 209.85.173.136
Connecting to dl.google.com|209.85.173.136|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:23:32 ERROR 404: Not Found.

--17:23:32--  http://sh/
           => `index.html'
Resolving sh... failed: Name or service not known.
--17:23:36--  http://googleearthlinux.bin/
           => `index.html'
Resolving googleearthlinux.bin... failed: Name or service not known.

FINISHED --17:23:50--
Downloaded: 0 bytes in 0 files
```

Why can't it find it?

---

### Post by montevjl on 2008-12-06
> **Scrotnig said:**
> vBulletin curtails the URL....use this:
```
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

Great info. You got the right link. Mny tks. /jl

---

### Post by montevjl on 2008-12-06
ok

---

### Post by Beastboy26 on 2008-12-09
google earth crashes every time i try to open it.  This is the message I get

```
Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin [0x804f403]
  ./googleearth-bin [0x804f916]
  [0xb8073400]
  /usr/lib/libX11.so.6(XInitExtension+0x41) [0xb6b36771]
  /usr/lib/libXext.so.6(XextAddDisplay+0x52) [0xb6c0e692]
  /usr/lib/libGL.so.1 [0xb674c58b]
  /usr/lib/libGL.so.1 [0xb674ce0f]
  /usr/lib/libGL.so.1 [0xb6749fcf]
  /home/bryan/google-earth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext15setSwapIntervalEi+0x8a) [0xb47035fa]
  /home/bryan/google-earth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext4openEv+0x4b5) [0xb473a345]
  /home/bryan/google-earth/libevll.so(_ZN5earth4evll13VisualContext11openContextEN3Gap3Gfx25igRenderDestinationFormatERKNS0_8InitInfoE+0xff) [0xb3ad2a4f]
  /home/bryan/google-earth/libevll.so(_ZN5earth4evll13VisualContext4initERKNS0_8InitInfoE+0x1fb) [0xb3ad431b]
  /home/bryan/google-earth/libevll.so(_ZN5earth4evll17RenderContextImpl4initERKNS0_8InitInfoE+0x8f) [0xb3c9502f]
  ./librender.so(_ZN12RenderWidget6setApiEPN5earth4evll3APIE+0x4f) [0xb68b0fef]
  ./librender.so(_ZN5earth6render12RenderWindow12createWidgetEv+0xb2) [0xb68bbc82]
  ./libgoogleearth_lib.so(_ZN5earth6client12ModuleWidget9showEventEP10QShowEvent+0x90) [0xb742c350]
  ./libQtGui.so.4(_ZN7QWidget5eventEP6QEvent+0xa86) [0xb78ca132]
  ./libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0x1d3) [0xb788e4ab]
  ./libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x132) [0xb789509e]
  ./libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x62) [0xb7e87eda]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0xf9) [0xb78cc809]
  ./libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x83) [0xb78cc567]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x15c) [0xb78cc704]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb78cc770]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb78cedcb]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb78cc6ee]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb78cc770]
  ./libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x83) [0xb78cc567]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x15c) [0xb78cc704]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb78cc770]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb78cedcb]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb78cc6ee]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb78cc770]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb78cedcb]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb78cc6ee]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb78cc770]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb78cedcb]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb78cc6ee]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb78cc770]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb78cedcb]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb78cc6ee]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb78cc770]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb78cedcb]
  ./libQtGui.so.4(_ZN7QWidget10showNormalEv+0x68) [0xb78c5150]
  ./libgoogleearth_lib.so(_ZN10MainWindow18readScreensizeInfoEv+0xc0f) [0xb740cfef]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application12setupMainWinERK7QStringb+0x2c0) [0xb73bca30]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application3runEv+0x2f1) [0xb73c04e1]
  ./googleearth-bin(main+0x2ba) [0x8050bea]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb71dc685]
  ./googleearth-bin [0x804f231]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/bryan/.googleearth/crashlogs/crashlog-E33380DC.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

```

any ideas

---

### Post by insert_name_here on 2008-12-24
fwiw, Beastboy, I get the same error message.  So you have my sympathies, but sympathies don't really fix things...

---

### Post by dspisak on 2008-12-25
I followed the script in Scrotnig's previous response and received this error message:

root@djs-pc:/home/spisaks# sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.3.7284.3916..............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!

Now what do i do?  TIA.

---

### Post by lightspeed500oard on 2008-12-27
I went through Terminal but got the following Msg,,pixel@ubuntu:~$ wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
--2008-12-27 02:54:43--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
Resolving dl.google.com... 74.125.19.93, 74.125.19.136, 74.125.19.190, ...
Connecting to dl.google.com|74.125.19.93|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2008-12-27 02:54:43 ERROR 404: Not Found.

pixel@ubuntu:~$ sh GoogleEarthLinux.bin
sh: Can't open GoogleEarthLinux.bin
pixel@ubuntu:~$ 
pixel@ubuntu:~$ 
Any Ideas? Thanks.

---

### Post by puppe on 2009-01-03
Well, the first line simply tells you that google earth does not exist anymore in that specific location you tried to download from.

The second error tells you that you can't install/run anything which you don't have.

You have to find another download location for G-Earth.

update: the current link to google earth is:

```
http://dl.google.com/earth/client/GE4/release_4_3/GoogleEarthLinux.bin
```

You can use the same commands as earlier with this link, or just paste it in to your browser and then download.

---

### Post by lightspeed500oard on 2009-01-03
Thanks for the desipher on line code, and i'll loke for another download site.

---

### Post by phobikore on 2009-01-09
!

---

### Post by phobikore on 2009-01-09
i typed:  

[I]wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
sh GoogleEarthLinux.bin
[/I]
and got an error:

[I]--03:11:57--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
&#917;&#973;&#961;&#949;&#963;&#951; &#964;&#959;&#965; dl.google.com... 66.249.93.93, 66.249.93.190, 66.249.93.91, ...
Connecting to dl.google.com|66.249.93.93|:80... &#963;&#965;&#957;&#948;&#941;&#952;&#951;&#954;&#949;.
&#919; &#945;&#943;&#964;&#951;&#963;&#951; &#947;&#953;&#945; HTTP &#963;&#964;&#940;&#955;&#952;&#951;&#954;&#949;, &#945;&#957;&#945;&#956;&#959;&#957;&#942; &#945;&#960;&#940;&#957;&#964;&#951;&#963;&#951;&#962;... 404 Not Found
03:11:57 &#931;&#934;&#913;&#923;&#924;&#913; 404: Not Found.[/I]

any suggestions? :)

((last line means:request for HTTP sent, waiting for response...))

---

### Post by Skripka on 2009-01-09
> **phobikore said:**
> i typed:  

[I]wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
sh GoogleEarthLinux.bin
[/I]
and got an error:

[I]--03:11:57--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
&#917;&#973;&#961;&#949;&#963;&#951; &#964;&#959;&#965; dl.google.com... 66.249.93.93, 66.249.93.190, 66.249.93.91, ...
Connecting to dl.google.com|66.249.93.93|:80... &#963;&#965;&#957;&#948;&#941;&#952;&#951;&#954;&#949;.
&#919; &#945;&#943;&#964;&#951;&#963;&#951; &#947;&#953;&#945; HTTP &#963;&#964;&#940;&#955;&#952;&#951;&#954;&#949;, &#945;&#957;&#945;&#956;&#959;&#957;&#942; &#945;&#960;&#940;&#957;&#964;&#951;&#963;&#951;&#962;... 404 Not Found
03:11:57 &#931;&#934;&#913;&#923;&#924;&#913; 404: Not Found.[/I]

any suggestions? :)

((last line means:request for HTTP sent, waiting for response...))

You can either install Google Earth the OBNOXIOUS way which leaves crap all over your HDD...or you can do it the Debian way.

[http://blog.irwan.name/?p=103](http://blog.irwan.name/?p=103)

---

### Post by ithanium on 2009-01-10
thanks for the post... it helped :D

---

### Post by Eyke on 2009-01-10
Hola!

I did wast Skripka's link suggested. I ran the make and got a lot of error messages about path problems. It did create the dep package. I ran the package and ubuntu said it installed correctly.

I have an entry in the apps menu, but with a generic icon. When I click the icon nothing happens. :(

Any suggestions? Un-smeggin-fortunately the laptop shutdown and I lost the terminal output. :(

Thanks

---

### Post by etlpkby on 2009-01-12
> **dspisak said:**
> I followed the script in Scrotnig's previous response and received this error message:

root@djs-pc:/home/spisaks# sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.3.7284.3916..............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!

Now what do i do?  TIA.

Ok, for reference I had this problem with latest (4.3) googleearth. I am running 8.10 Ibex on amd64. Video card in nvidia GeForce 9600 GT. (drivers installed via synaptic)

```
Linux serverwuss 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux
```

Firstly, I removed my $HOME/.goggleearth directory as I had previous version in my /home partition and I re-installed (don't ask *sigh*) 8.10 in '/' area. It may have nothing to do with fix, but I'd thought I'd mention it. Ok - onward...

I tried to fix it by following this blog:-
[http://blog.irwan.name/?p=283]("http://blog.irwan.name/?p=283")

But the 'make' gave errors
```
dpkg-shlibdeps: failure: couldn't find library libstdc++.so.6 needed by ../usr/lib/googleearth/libbasicIngest.so (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
```
<a lot of these seen>

When I tried to install the package created with the 'make' it gave me warning about 'ia32-libs' - so I fired up Synaptic and removed 'ia32-libs' which also removed the googleearth-package.

Then re-installed 'ia32-libs' via synaptic. Re-ran the download from Google-earth site (not..repeat **not** the googleearth-package, which is 4.2.x)
```

$ sudo sh ./GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.3.7284.3916..............................................................
loki_setup: Suspect size value for option option

/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon.

```

Despite the above 'failures' **it installs OK and starts fine!**

So basically check 'ia32-libs' pkg ;)

---

### Post by wiilliiss on 2009-01-28
have google earth ,exe.tar.gz google says for linux,mac,pc on desktop feisty says cannot open this file.  same with vuze. any ideas how to?

---

### Post by Lunx on 2009-01-31
> **Skripka said:**
> You can either install Google Earth the OBNOXIOUS way which leaves crap all over your HDD...or you can do it the Debian way.

[http://blog.irwan.name/?p=103](http://blog.irwan.name/?p=103)

Great stuff, been doin' my head in working out how to get GE up and running, had same problem with others trying to install the "hard way". Followed commands in that blog (don't forget sudo at first), now it's got it all together and is compiling package as I type. Now it should be a breeze to install :D

---

### Post by Lunx on 2009-01-31
Had no worries compiling deb package, but when I went to run install I see there were a heap of Not Found errors. I could see it installed into the correct directory, and was able to execute it, but it barely ran. I did apt-get autoremove straight away and it shows a list of what's missing
```

Do you want to continue [Y/n]? y
(Reading database ... 181572 files and directories currently installed.)
Removing googleearth ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'


```

So what would be my next plan of attack? I'm brand new to this installing from command line, and installing GE is the first thing I've tried as an experiment. Would love to get it up and running properly now I've got so close.

---

### Post by Phædrus2401 on 2009-02-02
Having some trouble. When I try the script found in the first post, I get the following error:

wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
Resolving dl.google.com... 72.14.207.136, 72.14.207.190, 72.14.207.91, ...
Connection to dl.google.com|72.14.207.136|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-02-02 21:13:38 ERROR 404: Not Found.


Did Google take the Linux version down or something? I hope not, I was looking forward to it.

---

### Post by kyleabaker on 2009-02-02
The file has moved since a newer version is now offered. If you still want to go with Google Earth 4 then you can try the following..

```
wget [http://dl.google.com/earth/client/ge4/release_4_3/googleearth-linux-plus-4.3.7284.3916.bin](http://dl.google.com/earth/client/ge4/release_4_3/googleearth-linux-plus-4.3.7284.3916.bin)
```

> **Phædrus2401 said:**
> Having some trouble. When I try the script found in the first post, I get the following error:

wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
Resolving dl.google.com... 72.14.207.136, 72.14.207.190, 72.14.207.91, ...
Connection to dl.google.com|72.14.207.136|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-02-02 21:13:38 ERROR 404: Not Found.


Did Google take the Linux version down or something? I hope not, I was looking forward to it.

--Problems with Google Earth 5.0 (beta)
Getting the following error in the terminal when attempting to run Google Earth 5.0 (beta). Anyone have it working and know how to fix this?

```
Warning: Unable to create prefs directory '/home/kyleabaker/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

```

---

### Post by cretox on 2009-02-03
> **kyleabaker said:**
> 

--Problems with Google Earth 5.0 (beta)
Getting the following error in the terminal when attempting to run Google Earth 5.0 (beta). Anyone have it working and know how to fix this?

```
Warning: Unable to create prefs directory '/home/kyleabaker/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

```

[:arrow: **External LINK**]("http://skoroneos.blogspot.com/2009/02/googleearth-5-on-ubuntu-810.html")

```
$ mv libcrypto.so.0.9.8 bkp_libcrypto.so.0.9.8
```

Note: googleearth's libcrypto.so.0.9.8 is:
· in ~/google-earth/ if you have installed it with the .bin package
· in /usr/lib/googleearth/ if you have installed it with the .deb package (in this case you'll need root permissions)

hope it works
cheers

---

### Post by nickthecook on 2009-02-03
> **cretox said:**
> [:arrow: **External LINK**]("http://skoroneos.blogspot.com/2009/02/googleearth-5-on-ubuntu-810.html")

```
$ mv libcrypto.so.0.9.8 bkp_libcrypto.so.0.9.8
```

Note: googleearth's libcrypto.so.0.9.8 is:
· in ~/google-earth/ if you have installed it with the .bin package
· in /usr/lib/googleearth/ if you have installed it with the .deb package (in this case you'll need root permissions)

hope it works
cheers

Worked perfectly for me! Thanks!

Just a note: I installed from the .bin downloaded from Google, and the path was "/usr/local/google-earth/" for me.

---

### Post by lcaljouw on 2009-02-03
Worked like a charm for me to resolve the libcrypto message;

sudo su
./googleearth.bin
cd /usr/local/googleearth
mv libcrypto.so.0.9.8 bkp_libcrypto.so.0.9.8
exit

googleearth

and... voila!

Thanks!

---

### Post by stormtrooprdave on 2009-02-03
> **lcaljouw said:**
> Worked like a charm for me to resolve the libcrypto message;

sudo su
./googleearth.bin
cd /usr/local/googleearth
mv libcrypto.so.0.9.8 bkp_libcrypto.so.0.9.8
exit

googleearth

and... voila!

Thanks!

Will this upgrade my existing google earth installation from the repos or will I have 2 versions?

---

### Post by kyleabaker on 2009-02-03
> **lcaljouw said:**
> sudo su
./googleearth.bin
cd /usr/local/googleearth
mv libcrypto.so.0.9.8 bkp_libcrypto.so.0.9.8
exit

I used the following that worked with cretox's solution:

```

wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
mv google-earth/libcrypto.so.0.9.8 google-earth/bkp_libcrypto.so.0.9.8

```

---

### Post by stormtrooprdave on 2009-02-03
> **kyleabaker said:**
> I used the following that worked with cretox's solution:

```

wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
mv google-earth/libcrypto.so.0.9.8 google-earth/bkp_libcrypto.so.0.9.8

```
I followed these instructions and ended up with 2 versions - my original one from the repos and the new version on my desktop.  When I launched it however it just brought up a black screen and nothing worked.

---

### Post by jmcgovern on 2009-02-03
I'm having trouble with the new version (5.0)  I ended up removing 4.3 completely, then running the script.   It appears to install, but when i tried to select the option to launch after install it appeared to launch, but crashed/closed immediately,  i got the following error. 
```

Warning: Unable to create prefs directory '/home/mcgoverns/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference


```

Everytime i try to click the icon to start the program, it loads, then immediately crashes/closes.  if i run the command 'googleearth', as instructed by the installer, in terminal i get.'command not found'.

---

### Post by feisty on 2009-02-05
> **jmcgovern said:**
> I'm having trouble with the new version (5.0)  I ended up removing 4.3 completely, then running the script.   It appears to install, but when i tried to select the option to launch after install it appeared to launch, but crashed/closed immediately,  i got the following error. 
```

Warning: Unable to create prefs directory '/home/mcgoverns/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference


```

Everytime i try to click the icon to start the program, it loads, then immediately crashes/closes.  if i run the command 'googleearth', as instructed by the installer, in terminal i get.'command not found'.


just rename the libcrypto in something else.

---

### Post by kyleabaker on 2009-02-05
> **jmcgovern said:**
> I'm having trouble with the new version (5.0)  I ended up removing 4.3 completely, then running the script.   It appears to install, but when i tried to select the option to launch after install it appeared to launch, but crashed/closed immediately,  i got the following error. 
```

Warning: Unable to create prefs directory '/home/mcgoverns/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference


```

Everytime i try to click the icon to start the program, it loads, then immediately crashes/closes.  if i run the command 'googleearth', as instructed by the installer, in terminal i get.'command not found'.

Read a couple posts up. It's already been answered. Check my previous post. it's the "mv..." part.

---

### Post by kornykyano on 2009-02-07
I need help, not what the problem is that when you get errors in the use graphics. I leave you a picture:[ATTACH]102505[/ATTACH]
I use Ubuntu 8.04.2, I have 3D acceleration and Compiz off.

The version of Google Earth is:

Google Earth 5.0.11337.1968 (beta)
Build Date Jan 28, 2009
Build Time 3:39:00 pm
Renderer OpenGL
Operating System Linux (2.6.24.0)
Video Driver NVIDIA Corporation
Max Texture Size 4096x4096
Server kh.google.com

sorry for my English, I did it with a translator.

Thanks!

---

### Post by EnsignR on 2009-02-08
> **kyleabaker said:**
> I used the following that worked with cretox's solution:

```

wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
mv google-earth/libcrypto.so.0.9.8 google-earth/bkp_libcrypto.so.0.9.8

```

I just tried the above... worked when I cd'ed to /usr/local/ prior to running mv. Therefore I the last statement should probably be as follows

```

mv /usr/local/google-earth/libcrypto.so.0.9.8 /usr/local/google-earth/bkp_libcrypto.so.0.9.8
 

```

Thanks to whom ever figured this out.

---

### Post by joeboe on 2009-02-09
So I changed libcrypto.so.0.9.8 with this code:

```
mv /usr/local/google-earth/libcrypto.so.0.9.8 /usr/local/google-earth/bkp_libcrypto.so.0.9.8
```

but now google earth won't open - if I navigate to the GE folder and try to open it, nothing happens.

When I type googleearth into terminal I get this:

```
/usr/bin/googleearth: line 3: cd: /usr/lib/googleearth: No such file or directory
/usr/bin/googleearth: line 4: /usr/lib/googleearth/googleearth-bin: No such file or directory
/usr/bin/googleearth: line 4: exec: /usr/lib/googleearth/googleearth-bin: cannot execute: No such file or directory

```

which I think is due to a previous botched install... not really sure

Any help is appreciated, I'm brand new to Ubuntu - installed it yesterday :D

---

### Post by antony_css on 2009-02-09
It does not work for me - it crashes during initiation

This is the error message:
> 
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference


---

### Post by janicejan on 2009-02-09
Thanks for sharing this one, I installed it and works pretty fine, on how to install tutorials, just read everything in it :D

---

### Post by lundish on 2009-02-09
> **kyleabaker said:**
> I used the following that worked with cretox's solution:

```

wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
mv google-earth/libcrypto.so.0.9.8 google-earth/bkp_libcrypto.so.0.9.8

```

it works for me
thank you

---

### Post by jhahoneyk on 2009-02-15
@joeboe
maybe you've messed up with the command to be run-
```
mv google-earth/libcrypto.so.0.9.8 google-earth/bkp_libcrypto.so.0.9.8
```
I think you moved some of ur googleearth files from ~/googleearth to /usr/lib/googleearth
Reinstalling and running the above command again should fix the problem.

---

### Post by fbugnon on 2009-02-16
> **jhahoneyk said:**
> Reinstalling and running the above command again should fix the problem.

Maybe is not necessary to reinstall.  I was having the same problem (crash right after the splash screen, during initialization of googleearth) and it was solved by simply renaming the file "libcrypto.so.0.9.8" (located, in my case, on /opt/googleearth/), without further steps.

Here the error message I received before:

[INDENT]./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference[/INDENT]

PS: I've followed the very short instructions found on [this]("http://www.google.com/support/forum/p/earth/thread?tid=7b1b524777b9b982&hl=en") site (Nakkel and gerdk answers).

---

### Post by jhahoneyk on 2009-02-16
Yes, in general there is no need to reinstall, even I didn't need to reinstall, just rename the file. Reinstall was meant for joeboe

---

### Post by 2fast4uspartan on 2009-02-16
Thanks! I dont know when Ubuntu Linux will stop impressing me. Ive got everything I need from a computer and more from Ubuntu. Im sticking with Hardy Heron though because I just love it more than any other update. If you are a serious C# programmer like me, use MonoDevelop. type Mono in your Add/Remove apps search bar for ubuntu and find it. it is great! thanks ubuntu and to the rest of the ubuntu community

---

### Post by thered on 2009-02-17
I've just  done a clean install of Intrepid.

Installed googleearth 5 but it starts to load then fails.

I've tried ```
sudo mv google-earth/libcrypto.so.0.9.8 google-earth/bkp_libcrypto.so.0.9.8
```

But get the following

**mv: cannot stat `google-earth/libcrypto.so.0.9.8': No such file or directory**

Even though file is present.  Am I missing something?

---

### Post by thered on 2009-02-17
OK new problem.

I re-installed Ver4.3 this opened but flicker badly.

Re-installed GE5 and now runs but still flickering, unusable.

Terminal reports:

[I]We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /root/.googleearth/crashlogs/crashlog-1A46D44F.txt[/I]

Event though it hasn't actually'crashed'

---

### Post by thered on 2009-02-17
OK I'm cool now.  Forgot to use openGL had to do that before:oops:

I took the libGL.so.1.2.xlibmesa file from /usr/lib/fglrx and popped it into the Google Earth folder, renamed as "libGL.so.1"

---

### Post by Buzzingxx on 2009-02-17
--01:48:04--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 66.102.9.190, 66.102.9.91, 66.102.9.93, ...
Connecting to dl.google.com|66.102.9.190|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
01:48:04 ERROR 404: Not Found.

Problem !!! :(
Please Help

---

### Post by RunningBear on 2009-02-22
I managed to install Google Earth, but when I start it, it starts, flips through several screens of somtheing -- too fast to se what, and the quits with no error message.  The machine is dual boot and Google Earth runs fine on the same machine under Windows XP, so I doubt that it is the hardware.

Thanks

_DAVID

---

### Post by kiisu on 2009-02-23
Renaming the libcrypto file managed to get GE to start, but now it is agonizingly slow - anyone experience this, or have a suggestion?

---

### Post by CapnGimp on 2009-02-23
Installed googleearth after installing the package builder from Synaptic
 I used the  --force switch detailed here...
[http://blog.irwan.name/?p=103](http://blog.irwan.name/?p=103)
substituting the correct pkg numbers
it starts runs and then dissappears in a second.
read THIS
[http://blog.irwan.name/?p=283](http://blog.irwan.name/?p=283)
 which says you don't NEED the --force switch now...happy happy joy 

so I forget to UNINSTALL all this before following the directions to install in last link

 OK, I've tried to rename it by all the recommended ways correcting my PATH names to fit my machine.
 I get nada

 Here is last try  

" john@SLICKnix:~$ #googleearth
john@SLICKnix:~$ googleearth
Warning: Unable to create prefs directory '/home/john/.googleearth'. File exists.
/usr/lib/googleearth/googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
john@SLICKnix:~$ sudo mv google-earth/libcrypto.so.0.9.8 google-earth/bkp_libcrypto.so.0.9.8
[sudo] password for john: 
mv: cannot stat `google-earth/libcrypto.so.0.9.8': No such file or directory
john@SLICKnix:~$ cd /usr/lib/googleearth
john@SLICKnix:/usr/lib/googleearth$ /google-earth$ mv libcrypto.so.0.9.8 orig-libcrypto.so.0.9.8
bash: /google-earth$: No such file or directory
john@SLICKnix:/usr/lib/googleearth$ /googleearth$ mv libcrypto.so.0.9.8 orig-libcrypto.so.0.9.8
bash: /googleearth$: No such file or directory
john@SLICKnix:/usr/lib/googleearth$ /googleearth$ mv libcrypto.so.0.9.8 orig-libcrypto.so.0.9.8
bash: /googleearth$: No such file or directory
john@SLICKnix:/usr/lib/googleearth$ ls
drivers.ini                 libgdal.so             liblayout.so
googleearth-bin             libge_net.so           libmath.so
gpl.txt                     libgeobase.so          libmeasure.so
gpsbabel                    libgeobaseutils.so     libminizip.so
ImporterGlobalSettings.ini  libGLU.so.1            libmoduleframework.so
ImporterUISettings.ini      libgoogleearth_lib.so  libnavigate.so
kh20                        libgooglesearch.so     libport.so
kvw                         libgps.so              libproj.so.0
lang                        libicudata.so.38       libQtCore.so.4
libalchemyext.so            libicuuc.so.38         libQtGui.so.4
libapiloader.so             libIGAttrs.so          libQtNetwork.so.4
libauth.so                  libIGCollision.so      libQtWebKit.so.4
libbase.so                  libIGCore.so           librender.so
libbasicingest.so           libIGDisplay.so        libstdc++.so.6
libcollada.so               libIGExportCommon.so   libwmsbase.so
libcommon.so                libIGGfx.so            libz.so.1
libcomponentframework.so    libIGGui.so            PCOptimizations.ini
libcrypto.so.0.9.8          libIGMath.so           plugins
libcurl.so.4                libIGOpt.so            qt.conf
libevll.so                  libIGSg.so             resources
libflightsim.so             libIGUtils.so          shaders
libfusioncommon.so          libinput_plugin.so     xml
libgcc_s.so.1               liblayer.so
john@SLICKnix:/usr/lib/googleearth$ mv libcrypto.so.0.9.8 orig-libcrypto.so.0.9.8
mv: cannot move `libcrypto.so.0.9.8' to `orig-libcrypto.so.0.9.8': Permission denied
john@SLICKnix:/usr/lib/googleearth$ su mv libcrypto.so.0.9.8 orig-libcrypto.so.0.9.8
Unknown id: mv
john@SLICKnix:/usr/lib/googleearth$ googleearth
Warning: Unable to create prefs directory '/home/john/.googleearth'. File exists.
/usr/lib/googleearth/googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
john@SLICKnix:/usr/lib/googleearth$ 
"


john@SLICKnix:/usr/lib/googleearth$ googleearth
Warning: Unable to create prefs directory '/home/john/.googleearth'. File exists.
/usr/lib/googleearth/googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
john@SLICKnix:/usr/lib/googleearth$

 not the sharpest knife in linux

 I could use a little help  please
 .....

---

### Post by CapnGimp on 2009-02-23
john@SLICKnix:~$ gksu #googleearth
Warning: Unable to create prefs directory '/home/john/.googleearth'. File exists.
/usr/lib/googleearth/googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
john@SLICKnix:~$ 



that's what I get when I try to run it.
it starts, goes thru a couple of opening windows motions and then POOF.... it closes

---

### Post by Lunx on 2009-02-25
> **CapnGimp said:**
> 
that's what I get when I try to run it.
it starts, goes thru a couple of opening windows motions and then POOF.... it closes

I'm having same problem here, but think I may be onto a solution now. Apparently GE doesn't play nicely with Compiz running, so if you disable Compiz it should work (well that's what I'm hoping, about to reinstall and see how I go).

Will post later as to whether I was successful or not in case it helps others

---

### Post by combatwombat_nz on 2009-02-26
No compiz running here...same errors...

Running as normal user:
Google Earth has caught signal 11.



Another crash happened while handling crash!

Running as su:
./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

Opens, closes.

That was version 5 downloaded. v 4.3 from Medibuntu goes fine.

Ubu 8.10, AMD64. Nvidia 8500GT.

---

### Post by kalyp on 2009-02-26
I had the exact same problem and it turned out it was because my computer is 64-bit. The solution in that case is here: [http://ph.ubuntuforums.com/showthread.php?t=962937&highlight=google+earth+intrepid](http://ph.ubuntuforums.com/showthread.php?t=962937&highlight=google+earth+intrepid)
Hope this helps!

If you're 32-bit then I guess it's a different issue... I had no problem on another computer which is 32-bit.
(intrepid in both cases)

---

### Post by Lunx on 2009-02-27
> **Lunx said:**
> I'm having same problem here, but think I may be onto a solution now. Apparently GE doesn't play nicely with Compiz running, so if you disable Compiz it should work (well that's what I'm hoping, about to reinstall and see how I go).

Will post later as to whether I was successful or not in case it helps others

I installed GE 4.2 and switched from Compiz to Metacity and had mixed results. At first I had problem with it failing to initialise and immediately crashing, was getting really annoyed and was almost going to uninstall, gave it another go and got it to run, but everything looked really screwed up. Closed it down and opened it again and it started behaving itself and running properly (although there's a problem with displaying fonts correctly). I switched back to Compiz, was eventually able to get it to run without crashing, but looked shocking (unusable). So perhaps turning off Compiz may be solution worth trying for some 

Easy way to switch between Compiz and Metacity (and other windows decorators) is to install fusion-icon from synaptic or use the terminal

```
sudo apt-get install fusion-icon
```

Once installed go to **Applications --> System Tools** and you'll see it there. Click on it and it will put a launcher on the panel which you can right-click on and choose Select **Window Manager --> Metacity**

Note: Metacity should be installed by default and on your system already

---

### Post by chip616 on 2009-02-27
Followed the instructions earlier up in this thread as follows:

```
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
mv google-earth/libcrypto.so.0.9.8 google-earth/bkp_libcrypto.so.0.9.8
```

Everything worked fine, and the splashscreen loads, and then the tips screen loads, but then I get an error message as follows:

> Google Earth is unable to identify your graphics card.  This is most likely because the driver for your graphics card has not been installed.  You may continue but the Google Earth is unlikely to work until you upgrade your driver.  For detailed driver download and install instructions please see our Google Earth Online Help Center using the link below:

[http://earth.google.com/support/bin/answer.py?answer=21482hl=en](http://earth.google.com/support/bin/answer.py?answer=21482hl=en)

The link, when followed, says that the information I have requested cannot be found.

Now, this is an nVidia e-GeForce 7300GT and I have the nVidia driver loaded and working.  It runs compiz, but at the moment, I am not using compiz on this machine.  I am using Kubuntu 8.04.

There is no problem with my video driver.  Anyone know what's up?

This is Google Earth 5.0.11337.1968 which I just downloaded and set up.

Thanks for any help anyone can offer.

Frank.

[COLOR="Red"]PS:  I have since successfully installed Google Earth on two Dell laptops with nVidia 8800 video cards[/COLOR], so the issue seems to be this 7300 GT.  However, it cannot be the driver, as the card is working.  It has to be something that Google Earth does not like about the driver.

-FB

[COLOR="Red"]OK, this is fixed.  While I have the nvidia driver installed, seems that it was not activated.  Once I had enabled the nvidia driver for this card, Google Earth now works properly.[/COLOR]

-FB

---

### Post by Yfrwlf on 2009-03-02
Same prob here, on 64-bit, even with all the 32-bit libs that are installed after installing Flash (so maybe some 32-bit libs are missing?), I get the same error when I try to run GE5:
```
./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
```as well as the unable to create prefs dir, file exists error.  It's not a 3D acceleration issue as that works fine.

---

### Post by CalderCoalson on 2009-03-02
Same problem as either normal user or root:

```
./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

```

---

### Post by kalyp on 2009-03-02
> **Yfrwlf said:**
> Same prob here, on 64-bit, even with all the 32-bit libs that are installed after installing Flash (so maybe some 32-bit libs are missing?), I get the same error when I try to run GE5:
```
./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
```

did you try to hide libcrypto.so.0.9.8 by moving it to a different name? cf the link I posted earlier and I think someone else mentioned it too. That's what solved the problem for me.

edit: I meant libssl.so.0.9.8 actually (I think). I'm sorry it looks like the link I posted earlier doesn't work anymore and I cannot find it again... basically the command was just mv libssl.so.0.9.8 libssl.so.0.9.8.bak and it solved the problem (on a 64-bit)

---

### Post by smoqer on 2009-03-04
> **CalderCoalson said:**
> Same problem as either normal user or root:

```
./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

```

this is what I did on debian lenny stable amd64

```
sudo mv /usr/lib32/i686/cmov/libssl.so.0.9.8 /usr/lib32/i686/cmov/libssl.so.0.9.8_backup
```

```
 sudo mv -v /emul/ia32-linux/usr/lib/libssl.so.0.9.8 /emul/ia32-linux/usr/lib/libssl.so.0.9.8_backup

```

I hope it can works fine for ubuntu, too.

enjoy:popcorn:

---

### Post by kvarley on 2009-03-04
Thanks! Was looking for a download location, and .bin file format makes it really easy to install.

---

### Post by CalderCoalson on 2009-03-04
Smoqer, after following your advice GE will stay open until I actually click something, at which point it dies with the following error:
```
./googleearth-bin: relocation error: /usr/lib32/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
```

---

### Post by smoqer on 2009-03-05
> **CalderCoalson said:**
> Smoqer, after following your advice GE will stay open until I actually click something, at which point it dies with the following error:
```
./googleearth-bin: relocation error: /usr/lib32/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
```
probably something is different between debian and ubuntu. however, try to rename that library (if you have a 64 bit system, of course)

```
sudo mv -v /usr/lib32/libssl.so.0.9.8 /usr/lib32/libssl.so.0.9.8_backup
```
if you experience any problem with other 32 bit softwares, just rename the library with the old name (without "_backup")

otherwise, you can thing that some bug affects ubuntu.


edit: it seems that /usr/lib32/libssl.so.0.9.8 is created every boot. at this moment the only solution I found is renaming it every time. If you previously renamed the library, you probably need to delete the backup, then rename the library. or you can make an easy script

```

#! /bin/bash
sudo rm -vf /usr/lib32/libssl.so.0.9.8_backup
sudo mv -v /usr/lib32/libssl.so.0.9.8 /usr/lib32/libssl.so.0.9.8_backup
googleearth
exit 0
```
it's not "elegant", but it should work ;)

---

### Post by fwyzard on 2009-03-08
Hi guys,
I just found a simpler way: remove the libcrypto that comes with Google Earth and let it use the system one.

Assumy google earth is installed under /opt/google-earth, this works for me:

```
sudo rm /opt/google-earth/libcrypto.so.0.9.8
```

To be on the safe side, you may want to move/rename it instead:

```
sudo mv /opt/google-earth/libcrypto.so.0.9.8 /opt/google-earth/libcrypto.so.0.9.8-backup
```

Hope this helps,
.Andrea

---

### Post by smoqer on 2009-03-10
> **fwyzard said:**
> Hi guys,
I just found a simpler way: remove the libcrypto that comes with Google Earth and let it use the system one.

Assumy google earth is installed under /opt/google-earth, this works for me:

```
sudo rm /opt/google-earth/libcrypto.so.0.9.8
```

To be on the safe side, you may want to move/rename it instead:

```
sudo mv /opt/google-earth/libcrypto.so.0.9.8 /opt/google-earth/libcrypto.so.0.9.8-backup
```

Hope this helps,
.Andrea

I haven't /opt/google-earth on my system, maybe cause I used goolgeearth-package to build the deb package. So, this solution is not good for me :(

---

### Post by SyberKowboy on 2009-03-11
That worked perfectly for me. I just downloaded version 5 from Google and installed it to my /home/user/ directory. If you remove or rename the libcrypto file like fwyzard recommends it works fine.

---

### Post by swaroopdutta on 2009-03-25
> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

The rest of the install is self explanatory, have fun!

THE LINK NOT FOUND ... Message says :-

--2009-03-25 12:23:16--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
Resolving dl.google.com... 72.14.203.93, 72.14.203.136, 72.14.203.190, ...
Connecting to dl.google.com|72.14.203.93|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-03-25 12:23:17 ERROR 404: Not Found.

---

### Post by Ottawajoe on 2009-03-27
Hi 
 I'm really new to Linux. I am trying to install Google earth. I went to Applications-accessories-terminal and I pasted 

wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
sh GoogleEarthLinux.bin

It wouldn't install it saying "Can't open google earth bin"

Now what do I do?

Thanks 
Ottawajoe

---

### Post by Ottawajoe on 2009-03-28
Hi
I'm really new to Linux. I am trying to install Google earth. I went to Applications-accessories-terminal and I pasted

wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
sh GoogleEarthLinux.bin

It wouldn't install it saying "Can't open google earth bin"

Now what do I do?

Thanks
Ottawajoe

---

### Post by 3rdalbum on 2009-03-28
Google seems to have changed the location of the Google Earth binary. Is there any reason why you're not installing it from the Medibuntu repository? ([www.medibuntu.org](www.medibuntu.org)).

---

### Post by jjroper on 2009-03-28
Well, I almost got Google Earth up and running, but, I get this error during installation.

wrong ELF class.

Apparently, GE is 32bit and my laptop is 64bit.  I saw somewhere, and now can't find it, that it is possible to tell Ubuntu to run GE in 32bit mode, or something like that.  Anybody know how to do that?

I already renamed the file that causes problems too (libcrypto) and of course, that did not solve the entire problem.  It helped, because before GE shut down.  Now it stays open, but the graphics are all bad.

Thanks,

Jim

---

### Post by jjroper on 2009-04-01
After some confusion,  have google earth 5 up and running.

The first thing that helped, apparently, was removing the libcrypto* file from the google-earth directory.  The second thing that helped, was setting the screen to "no effects" in linux.

But now, the text within the google earth window (not the menu bar) are bad.  Some letters only show a sort of blurred area, others look fine.  But, that means that text is unreadable.  So, still have a problem!

Cheers.

---

### Post by adamgram on 2009-04-25
> **Ottawajoe said:**
> Hi
I'm really new to Linux. I am trying to install Google earth. I went to Applications-accessories-terminal and I pasted

wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
sh GoogleEarthLinux.bin

It wouldn't install it saying "Can't open google earth bin"

Now what do I do?

Thanks
Ottawajoe

[http://ubuntu.igameilive.com/2009/02/google-earth-on-ubuntu-810.html](http://ubuntu.igameilive.com/2009/02/google-earth-on-ubuntu-810.html)

---

### Post by stewacide on 2009-04-25
Google Earth looks pretty psychedelic on my system since it seems to apply textures at random (although this could be an issue with the latest Intel drivers)

---

### Post by Arup on 2009-04-26
Jaunty includes latest vesion 5 of GE so there is no need to install it via the script. Also for Intel cards, just set effects to none in appearance and turn of atmosphere in view setting of GE and it works out fine, I have tested it with G31 on Jaunty x64 and its smooth and fast.

---

### Post by alkatron on 2009-05-04
On the same computer i have both hardy 32 bit and hardy 64 bit.
While on hardy 32 bit GE functions regulary on 64 bit if gives me a Segmentation fault....

I tried to install from
Google
medibuntu
googleearth-package

always segmentation fault at very start.

Any idea on how to trace this error?
Has GE some log file?

Thanks
Alkatron

---

### Post by hopugop on 2009-05-08
Works for me... I used the following commands:

```
wget http://dl.google.com/earth/client/ge4/release_4_3/googleearth-linux-plus-4.3.7284.3916.bin

sh googleearth-linux-plus-4.3.7284.3916.bin
```

:P

---

### Post by zurih on 2009-05-09
I'm getting this error (9.04 64bit):

```
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.3.7284.3916..............................................................
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
loki_setup: Suspect size value for option option

/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
```

Any suggestion?

---

### Post by blarney on 2009-05-09
Okay, my terminal screen popped up and it went through the install process and finished.  Now I can't find it or anything.  Is it supposed to run automatically?  Am I supposed to click on it or do another intall? 

I'm having a headache trying to figure out ubuntu, I think

---

### Post by kbowgren on 2009-05-09
> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```The rest of the install is self explanatory, have fun!

When I type the command in the terminal I get the following. I also did a Google download for Linux but it wants an application to open it. I am new to Linux and would appreciate any help.

Ken


kbowgren@kbowgren-laptop:~$ wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
--2009-05-10 08:38:30--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
Resolving dl.google.com... 209.85.153.91, 209.85.153.93, 209.85.153.136, ...
Connecting to dl.google.com|209.85.153.91|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-05-10 08:38:30 ERROR 404: Not Found.

kbowgren@kbowgren-laptop:~$ sh GoogleEarthLinux.bin

---

### Post by collinp on 2009-05-10
I'm thinking that this tutorial is too out of date to be relevant now. It was made in 2006 and the link is non-functioning.

---

### Post by alwayshere on 2009-05-10
sudo apt-get install googleearth
 
works for me

---

### Post by Dalle85 on 2009-05-11
You can install it from Synaptics... You might have to enable restricted sources in your repositories.

If you have it installed but don't know how to run it, just type "googleearth" in terminal (you have to create a shortcut manually)

If you can start it but it just displays a night sky with stars, you might have the same bug as me... Try running it as root ("sudo googleearth"in terminal)... It works for me, but it really isn't the optimal solution!

---

### Post by Arup on 2009-05-13
Whats surprising to see is that GE installed via repos in Jaunty won't run with latest nvidia driver from nvidia's site installed via the .sh. It would segfault on launch. You have to install the nvidia driver via repository to get it to work.

---

### Post by klesha on 2009-05-16
thank you hopugop!


wget [http://dl.google.com/earth/client/ge4/release_4_3/googleearth-linux-plus-4.3.7284.3916.bin](http://dl.google.com/earth/client/ge4/release_4_3/googleearth-linux-plus-4.3.7284.3916.bin)

sh googleearth-linux-plus-4.3.7284.3916.bin

worked for me too!

---

### Post by Bruce S on 2009-05-17
I got Google Earth downloaded and it is sitting on Desktop.

Do not know how to install it, nothing I have tried does anything useful.

I have 64 bit OS.
Will this be the cause of the problem?:o

---

### Post by davar on 2009-05-19
i dowload all the terminal information to install and as  for my response i get the message:

                            There is no window program configured to open this type of File

Please help and thanks very much

---

### Post by ipayne on 2009-05-19
Here is how I got it to work. Not much here is new but it does pull together some stuff from various other places...

Note: If you've installed Google Earth already and are getting errors/crashes try to uninstall it.  To do this, find the directory where it is installed. Open a terminal and try:

```
sudo find / -name google-earth -type d
```


This may take a little while since it is going to search your entire drive partition (starting from / )looking for a directory (-type d) named google-earth.  I use sudo here to avoid the onslaught of "Permission denied" messages that would result from trying to read directories for which I don't have permissions.

If you do have Google Earth installed, this command will eventually spit out a path like, /home/yourUserName/google-earth, so cd into that directory.

Now run:

```
./uninstall
```

That should clean up earlier installs.

Now download the installer here -> [(http://earth.google.com)]("http://earth.google.com").  Navigate to the directory containing the downloaded file (it should be called something like GoogleEarthLinux.bin, and run that script like this:

```
./GoogleEarthLinux.bin
```

This will launch a graphical installer that allows you to choose some things like where to install, etc.  If you're not sure what this stuff is about, just use the defaults.

When the installer completes, don't launch yet.

By default, this script creates a directory in your home directory (called google-earth) where it installs the app.  It also creates a link in your home directory (called googleearth) that you can use to launch.

So, as posted many times above, go to the install directory and rename the following file:

```
mv libcrypto.so.0.9.8 bak_libcrypto.so.0.9.8
```

This fix seems to work for lots of people, but when I tried it out:

```
~/googleearth
```

The app tries to start and then crashes and I get the following output in my terminal:

> 
Warning: Unable to create prefs directory '/home/myUserName/.googleearth'. File exists.
Google Earth has caught signal 11.



Another crash happened while handling crash!

 
The warning about the existing file is normal, but obviously the crash isn't. The solution for me was to run as root:

```
sudo ~/googleearth
```

which works fine.

I haven't yet discovered why this works but I'll update if I figure it out.

---

### Post by anchorschmidt on 2009-05-31
Thanks a lot

---

### Post by geoffree on 2009-05-31
> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

The rest of the install is self explanatory, have fun!

NOT EXACTLY FOR ME....

Could you please detail running a .bin file? Not a newbie, but am puzzled as to how to do this.

TIA

geoffree

---

### Post by freeediver on 2009-06-11
> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

The rest of the install is self explanatory, have fun!
I just tried this and got no where, what has changed ? Version 5 will not work for me, I was hoping to get 4.3 at least I will be grateful for any help. 
Thanks

---

### Post by arch0njw on 2009-06-29
> **dsoria said:**
> i've this error:

error code 29

"not connected to server"
"chek is your conection"

mm.. my connection is god! i can see the web pages, no problem!

help!

[https://help.ubuntu.com/community/GoogleEarth#Troubleshooting](https://help.ubuntu.com/community/GoogleEarth#Troubleshooting)

"**Google Earth on Ubuntu x64**

 If you get a "error 29", you may miss "lib32nss-mdns". Install this library like this: 
sudo aptitude install lib32nss-mdns 
You may also install other 32bit libraries. Note that google does not provide a 64 bit version of Google Earth. Thus installation on x64 system will take some extra efforts. 
"

Answer to a post from a long time ago.  I just found this answer in one place -- doesn't hurt to put it in another.

---

### Post by circut1 on 2009-07-04
Thanks so much for the straight forward and precise, I might add, info to get me up to speed. Had to install Google with my new ubuntu network  OS installations.  Did what you said and all works well. Have not rebooted yet but reset my drivers for nvidea proprietary drivers ,  after reading the notes and pop up in google about slow performance etc etc.

---

### Post by fbugnon on 2009-07-21
> **arch0njw said:**
> 
"**Google Earth on Ubuntu x64**

 If you get a "error 29", you may miss "lib32nss-mdns". Install this library like this: 
sudo aptitude install lib32nss-mdns 

Answer to a post from a long time ago.  I just found this answer in one place -- doesn't hurt to put it in another.

Thank you very much for this info, just saved my day.

For a bit more of speed (no card drive installed) I disable atmosphere effects.

Cheers,

f.

---

### Post by 1915flyer on 2009-10-15
Has anyone figured out how to **UNINSTALL** Google Earth? This seems to have been a problem for several years as evidenced by this thread.

GE is installed in /opt/google-earth. There is a file named 'uninstall', but when I run it all I get is 
"Could not find a usable uninstall program. Aborting."

Ubuntu 9.04

```
#! /bin/sh
#### UNINSTALL SCRIPT - Generated by SetupDB 1.6 #####
DetectARCH()
{
        status=1
        case `uname -m` in
           amd64 | x86_64)  echo "amd64"
                  status=0;;
           i?86 | i86*)  echo "x86"
                  status=0;;
           90*/*)
		   echo "hppa"
		   status=0;;
	    *)
		case `uname -s` in
		    IRIX*)
			echo "mips"
			status=0;;
           AIX*)
           echo "ppc"
           status=0;;
		    *)
			arch=`uname -p 2>/dev/null || uname -m`
                       if test "$arch" = powerpc; then
                          echo "ppc"
                       else
                          echo $arch
                       fi
			status=0;;
		esac
        esac
        return $status
}

DetectOS()
{
  os=`uname -s`
  if test "$os" = OpenUNIX; then
     echo SCO_SV
  else
     echo $os
  fi
  return 0
}

FindBinary()
{
  arch=$1
  if which loki-uninstall 2> /dev/null > /dev/null || type -p loki-uninstall 2> /dev/null > /dev/null; then
    if loki-uninstall -v > /dev/null 2> /dev/null; then
        echo `exec 2>&-; which loki-uninstall || type loki-uninstall`
    else
        echo "$HOME/.loki/installed/bin/`DetectOS`/$arch/uninstall"
    fi
  else
    echo "$HOME/.loki/installed/bin/`DetectOS`/$arch/uninstall"
  fi
}

arch=`DetectARCH`
UNINSTALL=`FindBinary $arch`

# Special case: if amd64 and binary is missing, try to run x86 build...
if test ! -x "$UNINSTALL" ; then
  if test "$arch" = amd64 ; then
    UNINSTALL=`FindBinary x86`
  fi
fi

if test ! -x "$UNINSTALL" ; then
    echo Could not find a usable uninstall program. Aborting.
    exit 1
fi

exec "$UNINSTALL" -L google-earth "/opt/google-earth/.manifest/google-earth.xml" "$1"


```

Thanks for any help.

Tyler

---

### Post by 1915flyer on 2009-10-15
I finally came across a message with instructions on how to uninstall Google Earth!

[http://ubuntuforums.org/showthread.php?t=208254](http://ubuntuforums.org/showthread.php?t=208254)

Basically, navigate to the GE directory (/opt/google-earth). Then

```
sudo su -
./uninstall
```

Now it runs the uninstall script and indicates GE is uninstalled.

---

### Post by makkirot on 2009-10-15
Awesome..Thanks :popcorn::popcorn:

---

### Post by ShizzlePDX503 on 2009-10-16
any ideas why I get this in the terminal... I saw that someone else had this issue in this thread but didn't see any responses to it:

```
shizzle@shizzle-laptop:~/Desktop$ sh GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.1.3509.4636..............................................................
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
loki_setup: Suspect size value for option option

/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
loki_setup: Suspect size value for option option
```

---

### Post by THE MIXER on 2009-12-16
_***[FONT=Arial][SIZE=5][COLOR=Red]Thank's ..[/COLOR][/SIZE][/FONT]***_


[SIZE=2][B]Its OK And every thing goes fine , But when i wanna change setting or i wanna go to tools or program's setting , Some thing look wrong ...
see the pictures in Attachments .. [/B][/SIZE]


>>>

---

### Post by LewisDre4m on 2010-01-05
PLEASE NOTE, for some very very very strange reason the Google Earth download will not work if you are using Google Chrome. Download it using firefox or something else. I follow the instructions on this site as they are perfect. 

[http://sunnybiologia.blogspot.com/2009/09/how-to-install-goggle-earth-in-ubuntu.html](http://sunnybiologia.blogspot.com/2009/09/how-to-install-goggle-earth-in-ubuntu.html)

Which basically tells you this . . .

download the Linux installer in the google earth page.
Open a terminal and change to the directory where the installer downloaded to. If it’s on your desktop you can use this command:

cd ~/Desktop
Change the permissions on the installer so you can run it:

chmod +x GoogleEarthLinux.bin
Run the installer as the root user:

sudo ./GoogleEarthLinux.bin

The installer dialog will open. The default install paths work fine. Click Begin Install.
Once the installation is finished you can click Start to launch Google Earth.

---

### Post by jhahoneyk on 2010-01-05
> **LewisDre4m said:**
> 

sudo ./GoogleEarthLinux.bin



IMO, sudo is not required. You can just run the bin file and install in your home directory if required

---

### Post by MonicaR on 2010-01-05
I tried to use the terminal info that you gave, but it didnt work...i got an error 404 message!

---

### Post by MonicaR on 2010-01-05
I'm such a newbie so please be patient with me.  I opened the terminal and tried typing in:

cd ~/Desktop
Change the permissions on the installer so you can run it:

and this one
chmod +x GoogleEarthLinux.bin
Run the installer as the root user:

and this one: need a password for it
sudo ./GoogleEarthLinux.bin

but I still cannot get it to work.  It is in my downloads in some type of page form and not the icon.  What am I doing wrong???

---

### Post by heavyrain2408 on 2010-01-23
What errors did you receive?

---

### Post by Francewhoa on 2010-03-21
Same here. Default fonts are too small in Google Earth 5. **The following worked for me.** [http://ubuntuforums.org/showthread.php?p=9004685#post9004685](http://ubuntuforums.org/showthread.php?p=9004685#post9004685)

---

### Post by MissouriNewb on 2010-06-21
> **LewisDre4m said:**
> PLEASE NOTE, for some very very very strange reason the Google Earth download will not work if you are using Google Chrome. Download it using firefox or something else. I follow the instructions on this site as they are perfect. 

[http://sunnybiologia.blogspot.com/2009/09/how-to-install-goggle-earth-in-ubuntu.html](http://sunnybiologia.blogspot.com/2009/09/how-to-install-goggle-earth-in-ubuntu.html)

Which basically tells you this . . .

download the Linux installer in the google earth page.
Open a terminal and change to the directory where the installer downloaded to. If it’s on your desktop you can use this command:

cd ~/Desktop
Change the permissions on the installer so you can run it:

chmod +x GoogleEarthLinux.bin
Run the installer as the root user:

sudo ./GoogleEarthLinux.bin

The installer dialog will open. The default install paths work fine. Click Begin Install.
Once the installation is finished you can click Start to launch Google Earth.++++ Thanks so much.

Could not install at all and actually see the globe.

Now all works well!!

Thanks a ton!!

Respectfully Submitted

MN

Romans 6.23

---

### Post by Hovik on 2010-06-29
> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```The rest of the install is self explanatory, have fun!

Thanks for the info, I got it to work but only by changing the code to accommodate a new download link - as follows:

```
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```Cheers!

---

### Post by thelazyc on 2010-07-14
p, li { white-space: pre-wrap; }  I am having this problem, how do I fix it?



Google Earth could not write to the current cache or My Places file location. The values will be set as follows:
 My Places Path: "/home/thelazyc/.googleearth"
Cache Path: "/home/thelazyc/.googleearth/Cache"

---

### Post by 4hp007 on 2010-08-01
> wget [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin) 
sh GoogleEarthLinux.binI installed using this in terminal. But when i tried to start i just got a splash screen of google earth and then gone. But it dint start. Can some one help. I m new to ubuntu so pls help step wise. Pls. I even tried opening from terminal but got this error.
> 
sudo ~/google-earth//googleearth
Fatal error in __driConfigOptions line 1, column 0: unknown encoding.
Google Earth has caught signal 6.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /root/.googleearth/crashlogs/crashlog-4c556f1a.txt

Please include this file if you submit a bug report to Google.



---

### Post by freeediver on 2010-08-02
I have had so many issues with GE that I no longer update it.
I have a version that works,  GE 4.5 I think and it is stable so I'm not going to rock the boat.

---

### Post by tahir.salfi on 2010-08-08
> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```

The rest of the install is self explanatory, have fun!

Dear its not Working. I had Copy it and Paste it in Terminal but didn't work. :(

---

### Post by coredatarecovery.com on 2010-08-09
Google Earth could not write to the current cache or My Places file location. The values will be set as follows:
My Places Path: "/home/chuck/.googleearth"
Cache Path: "/home/chuck/.googleearth/Cache"

I've chmod both of them to 777 but I still get the error.

any suggestions?

---

### Post by riopiedra on 2010-08-09
> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```The rest of the install is self explanatory, have fun!

Just to correct a little bit this:

[LIST=1]
[*]I downloaded the last version for linux of google earth from their official site.
[*]Then in a terminal I went to the place the file GoogleEarthLinux.bin was downloaded.
[*]then I made: sudo sh GoogleEarthLinux.bin
[*]The program was installed in /proc/google-earth , a symbolic link was put in /usr/local/bin , and a hide directory .googleearth was created at /home/myuser
[*]Then I went to /home/myuser and made: sudo chown -hR myuser .googleearth
[*]Then I followed the next instructions I found in [http://www.google.com/support/forum/p/earth/thread?tid=467f457376d88888&hl=en](http://www.google.com/support/forum/p/earth/thread?tid=467f457376d88888&hl=en)
[/LIST]
cd /opt/google-earth/

(assuming you installed it under /opt/google-earth/)

wget [http://librarian.launchpad.net/7037027/libGL.so.1](http://librarian.launchpad.net/7037027/libGL.so.1) -O libGL.so.1

That's all!

---

### Post by chiafunkito on 2010-09-11
used this command to download and install:wget [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin) && chmod +x GoogleEarthLinux.bin && ./GoogleEarthLinux.bin 
but always crashes after opening briefly with a note on known bug causing this. Any ideas?

---

### Post by smile4yourself on 2010-09-18
I tried this on Kubuntu 10.04.1 LTS (Lucid Lynx) and got the splash screen after which the application dies. I looked for a log file but could not find one. Anyone have any ideas?

---

### Post by mx32 on 2010-09-25
I have successfully installed Google Earth from the Medibuntu repository using Synaptic (I have Ubuntu 10.04 and genome) 

Installation was as easy as:
Go to System>Administration>Synaptic

Search for Google earth and then select
googleearth and googleearth-data packages.
Click install.
You will be warned of not verified software, click accept and that's it.

It runs flawlessly

This is how to add medibuntu to the reporsitory:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by waltclay on 2010-09-28
[http://www.google.com/support/forum/p/earth/thread?tid=522e9e6586ef2cc2&hl=en]("http://www.google.com/support/forum/p/earth/thread?tid=522e9e6586ef2cc2&hl=en")

---

### Post by waltclay on 2010-09-28
Also [http://code.google.com/p/earth-issues/issues/detail?id=913#c3]("http://code.google.com/p/earth-issues/issues/detail?id=913#c3")

---

### Post by waltclay on 2010-09-28
I have now successfully used the Medibuntu method of #349 to upgrade, but it is a version 5.1. The most recent (Sept 2010) is a 5.2. 

5.2 in xp allows me to save paths, but I'll stay with 5.1 until Medibuntu has upgrade - my thanks to them for their good work.

---

### Post by pbenerjee on 2010-09-28
> **waltclay said:**
> I have now successfully used the Medibuntu method of #349 to upgrade, but it is a version 5.1. The most recent (Sept 2010) is a 5.2. 

5.2 in xp allows me to save paths, but I'll stay with 5.1 until Medibuntu has upgrade - my thanks to them for their good work.

Yes, I am staying with 5.1 too, for the same reason

---

### Post by b3rylord on 2010-11-03
In site [http://tutorial.*****************/how-to-install-google-earth-to-ubuntu-10-10.html](http://tutorial.*****************/how-to-install-google-earth-to-ubuntu-10-10.html)  (downloadatoz dot com)

there is the method:-

1. Install **googleearth-package** from the repositories:
sudo apt-get install googleearth-package 
 Related Tutorials  : 
 
[LIST]
[*][Google Earth: How to Install it on Ubuntu 10.04]("http://tutorial.*****************/google-earth-how-to-install-it-on-ubuntu-10-04.html")
[*][How to Install Google Earth to Ubuntu 10.10]("http://tutorial.*****************/how-to-install-google-earth-to-ubuntu-10-10.html")
[*][How to Install KDE Desktop on Ubuntu 10.04]("http://tutorial.*****************/how-to-install-kde-desktop-on-ubuntu-10-04.html")
[*][How to Upgrade to Ubuntu 10.10 from Ubuntu 10.04 ]("http://tutorial.*****************/how-to-upgrade-to-ubuntu-10-10-from-ubuntu-10-04.html")
[*][How to Open Start Menu in Ubuntu 10.04 and Ubuntu 10.10 by the Windows Key]("http://tutorial.*****************/how-to-open-start-menu-in-ubuntu-10-04-and-ubuntu-10-10-by-the-windows-key.html")
[/LIST]
 
 
2. Make the **package** force
make-googleearth-package &#65533;Cforce 

3. Double clicking on the **.deb** it has generated to install it. 

4. Go to Applications > Internet > Google Earth to Run [Google Earth]("http://www.*****************/home-education_directory/google-earth/")                                  


I do not understand the ?Cforce after makegoogleearth-package in step 2 so cannot go forward.

Any help appreciated by newbie.....

Paul

---

### Post by fbugnon on 2010-11-03
It seems like all the links (URL) of your post have errors, so I could not check specifically the tutorial you mentioned.

But the "force" option (usually **-f** or **-force**) in this case its something to help the package to be installed even if the installer detects something strange (like missing dependencies, pre-existant files where new files are to be placed, different architecture, etc.) and, although should be used with caution, is somehow normal in tutorials that tries to debug errors. 

Hope it helps you.
More info on -force option could be found in **man make**.
Cheers

---

### Post by MarsbarloveR on 2010-11-06
Does anybody knows how to install Google Earth on Lubuntu? For some reason it just wont work :( 

And being the noob that i am, i just cant figure out how to fix this.

Thanks sofar. Any hints or tips are much apreciated!

---

### Post by jimmyxu on 2010-11-09
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.2.1.1588..............................................................
setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
Couldn't load 'setup.data/setup.xml'
--------------------------------------------------------------

How can I install in 10.10?

---

### Post by b3rylord on 2010-11-09
Thanks fbugnon,
I did another sudo apt-get install googleearth-package
and the result was as follows:-

[sudo] password for deltaman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
googleearth-package is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Trouble is I cannot find anything to do with google earth on the PC, and have to admit that I do not really know where to look[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG] This is Ubuntu 10.10 by the way.

---

### Post by irpsit on 2010-12-24
[B]With this I hope to finish the problem for everyone.
[/B]
To Install Google Earth run these commands:

> sudo apt-get install googleearth-package
(this alone does not install the program!)

> sudo make-googleearth-package --force
(this step takes big time, but it's necessary)

> sudo dpkg -i ./googleearth_5.1.3535.3218+0.5.7-1_i386.deb
(the file name may be different, just browse in /home, or in the last line of the output of last command)

Go to Applications - Internet - Google Earth

If it does not launch, then do

> sudo apt-get install lsb-core

Or you might have to install the following packages:
> sudo aptitude install ttf-dejavu
sudo aptitude install ttf-bitstream-vera
sudo aptitude install msttcorefonts
sudo aptitude install lib32nss-mdns

After this, it should run. But sometimes start-up tips make the software crash
 
So, follow this fix, if Google Earth crashes:  
(applies to Maverick or Lucid)

> gedit ~/.config/Google/GoogleEarthPlus.conf

Now, search for "enableTips" inside the conf file and if it exists, change its value from "true" to "false". If it does not exist, you need to add the following under "[General]" category.

> enableTips=false

Save and Exit. Done. Now try launching Google Earth in Ubuntu, all's going to be fine.

---

### Post by Circlotron on 2010-12-26
Wow! That worked first shot! Thanks. :KS:KS:KS:KS:KS:KS:KS

---

### Post by NuxIT on 2011-01-20
Holy crap. I can't believe I spent hours trying to install GE on xubuntu 10.10 by following all these crazy installation instructions that did not work for me!! 

Turns out all I had to do was VERY simple (DOH):

> Google Earth now has pre-compiled .deb packages (32 & 64-bit) directly available for Ubuntu:

[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

Just double-click the file name where you have saved it and the package installer will run. 

---

### Post by DeviantGuy on 2011-01-21
When I tried to install Google Earth via the Terminal, the command was found. But I got a 404 error. So I'm just going to install the .DEB file ;)

---

### Post by NuxIT on 2011-01-23
> **DeviantGuy said:**
> When I tried to install Google Earth via the Terminal, the command was found. But I got a 404 error. So I'm just going to install the .DEB file ;)

Yep, directly from googles site. Also, on my xubuntu I had to install lsb-core for it to work. Forgot to mention that. 

sudo apt-get lsb-core

---

### Post by trinitydan on 2011-01-23
> **NuxIT said:**
> Yep, directly from googles site. Also, on my xubuntu I had to install lsb-core for it to work. Forgot to mention that. 

sudo apt-get lsb-core
Good tip!  lsb-core got it to run on my machine running Ubuntu 10.10 too.  I think you meant to type "install" in there, but the meaning was there and got it working for me so thanks!

```
sudo apt-get install lsb-core
```

---

### Post by NuxIT on 2011-01-28
> **trinitydan said:**
> Good tip!  lsb-core got it to run on my machine running Ubuntu 10.10 too.  I think you meant to type "install" in there, but the meaning was there and got it working for me so thanks!

```
sudo apt-get install lsb-core
```

Yep, meant to have install in their. Thanks for clarifying.

---

### Post by nhtrader on 2011-02-21
Also note that if you previously installed the google earth package and then subsequently installed lsb-core, you'll need to reinstall the google earth package. This is what you do...
1. find the location of the downloadedgoogle earth package
2. double click it
3. select reinstall
4. try google earth now - it should work.


SUMMARY for new installation of google earth version 6 
(these instructions must be completed in order)

1. use synaptic package manager| search for lsb-core
2. if not installed, mark for installation and install/apply.
3. fetch google earth *.deb package (i386 or x86_64) from google's download URL
[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

4. double click downloaded file (your webbrowser's default download folder)
5. select install
6. finished

-------
I use xubuntu 10.10 with xfce 4.8.0 google earth now works.

---

### Post by COMPUTIAC on 2011-02-23
Hello , Works great !  Very easy to install.  I did it another way though, first downloaded Google earth, did not work. Read the post from nhtrader, downloaded  lsb-core .   Now all is fine.     Flying away !!

                 Thank's All,     COMPUTIAC

---

### Post by MacHeath on 2011-02-23
Excellent post works like a dream:-)

I installed  Google Earth first then lsb-core and it did not appear to be a problem

---

### Post by COMPUTIAC on 2011-02-23
Thank's,  a lot of weird stuff to explore,  ehhhh !



COMPUTIAC

---

### Post by befana on 2011-07-19
I've installed Google Earth following nhtrader's instructions, and it looks awfully bad! Look at this font - I can't read nothing!

---

### Post by Illuminati Hater 1 on 2011-08-06
> **lastrite said:**
> The linux version of google earth has just been released so heres how to get it!

1. Open up a terminal (Applications > Accessories > Terminal) 
2. Type in the following:

```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```The rest of the install is self explanatory, have fun!

Man this is out-dated the say 404 not found...............
Please provide the latest installation method thanks in advance
:(

---

### Post by Elfy on 2011-08-06
A post from _2006_ about software is likely to be out of date. In addition the person who started the thread has not been here for 2 years. 

Further this thread is actually in the _Outdated Tutorials_ forum. 

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---


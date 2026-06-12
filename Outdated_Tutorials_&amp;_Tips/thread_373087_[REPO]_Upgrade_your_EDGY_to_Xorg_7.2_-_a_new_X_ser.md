---
title: "[REPO] Upgrade your EDGY to Xorg 7.2 - a new X server for &quot;stable&quot; version"
date: 2007-02-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Treviño on 2007-02-28
[CENTER][B]_THIS GUIDE IS FOR ADVANCED USERS ONLY_

[/B][/CENTER]
Well, I've been much *unsettled* about posting those informations and data but seen that all went well for me I decided, finally to share all I created. 

I did all this work, at the beginning, just for me packaging the pure xorg7.2, then, when all the related the packages come to feisty I downloaded  and recompiled them all to my machine changing a little the version data... All this has been easy and fast for me using some scripts I wrote to do it (in just 5 hours I got all)... 

I start to say that [I]**I suggest** to **update** to those _advanced users_ that use AiGLX and free drivers from freedesktop community.
[/I]I use the open-source radeon drivers and I'm happy with this... Intel people maybe will be more.

[SIZE=3]**What you'll get** (more...)[/SIZE][LIST]
[*]Ehnannced AiGLX support
[*]Better Compiz/Beryl use
[*]Improved 3d performances (mostly using open-sources drivers)
[*]Working resuming from hibernation and VT switching
[*]mhmhm... Any other thing related to Xorg 7.2 and Mesa 6.5.2 :D[/LIST][SIZE=3][B]
HOW To upgrade to Xorg7.2 and Mesa3D 6.5.2[/B] with *(virtually)* _no riscks_[/SIZE][LIST]
[*]Edit your sources.list with your favorite text editor (i.e. [FONT=Courier New]sudo gedit /etc/apt/sources.list[/FONT]) and add my new repo[/LIST][INDENT]```
# Treviño's Ubuntu edgy Xorg-7.2 Repository (GPG key: 81836EBF - DD800CD9)
deb http://download.tuxfamily.org/3v1deb edgy xorg-7.2
```[/INDENT][LIST]
[*]Update your apt database list with[/LIST][INDENT]```
sudo apt-get update
```[/INDENT][LIST]
[*]Then you're ready for updating your system, I think the better way is that of using tools like synaptic to check what you're doing (instead of [FONT=Courier New]sudo apt-get upgrade[/FONT])
[*]I don't think you need to update the /etc/X11/xorg.conf file, but I've to notify you that the EXA acceleration is currently buggy (slow text rendering), so if you use it simply switch to XAA until a bugfix is released
[*]When update has ended, simpy restart your X closing your gnome/kde session or simply with [FONT=Courier New]Ctrl+Alt+Backspace[/FONT]
[*]If you're using closed ATi or nVidia drivers, and after this upgrade you'll get a *white screen of the death* on Beryl or Compiz, simply reinstall (rebuilding) your video drivers and all should work again...[/LIST]*Good Luck!* :D

You'll _**find more about my repo**_ (checking also its packages) at **[this page]("http://3v1n0.tuxfamily.org/dists/edgy/xorg-7.2/index.html")**.


[B][SIZE=3]Why _future upgrades_ will be *_safe_*![/SIZE]
[/B]To avoid problems on updates to next ubuntu versions (feisty first of all), I've "re-versioned" all the files from *VERSION-XubuntuY* to *VERSION-XedgyY~3v1ubuntuZ* or from *VERSION-XubuntuY* to *VERSION~3v1ubuntu*X, and as you can easily check using [FONT=Courier New]dpkg --compare-versions[/FONT], the versions I've used are ALWAYS (in my tests) lower than official ones of edgy+1 release.

So, I can say with a reasonable certitude that ***this* update won't create problems** with future versions!


[SIZE=3]HOW To _**dowgrade to default edgy configuration**_ (Xorg 7.1 and Mesa3D 6.5.1+cvs)[/SIZE][LIST]
[*]Remove the xorg-7.2 repository (listed above) from your sources.list and run[/LIST][INDENT]```
sudo apt-get update
```[/INDENT][LIST]
[*]Then, go back using synaptic or commands like the below:[/LIST][INDENT]```
sudo apt-get install -f libdrm2/edgy libdrm-dev/edgy libgl1-mesa-dev/edgy libgl1-mesa-dri/edgy libgl1-mesa-glx/edgy libgl1-mesa-swx11/edgy libgl1-mesa-swx11-dbg/edgy libgl1-mesa-swx11-dev/edgy libglu1-mesa/edgy libglu1-mesa-dev/edgy libosmesa6/edgy libosmesa6-dev/edgy mesa-common-dev/edgy mesa-swx11-source/edgy mesa-utils/edgy x11-common/edgy x11proto-damage-dev/edgy x11proto-gl-dev/edgy x11proto-input-dev/edgy x11proto-randr-dev/edgy xbase-clients/edgy xdmx/edgy xdmx-tools/edgy xkb-data/edgy xkeyboard-config/edgy xlibmesa-dri/edgy xlibmesa-gl/edgy xlibmesa-glu/edgy xlibs-dev/edgy xlibs-static-dev/edgy xnest/edgy xorg/edgy xserver-xephyr/edgy xserver-xorg/edgy xserver-xorg-core/edgy xserver-xorg-dev/edgy xserver-xorg-input-acecad/edgy xserver-xorg-input-aiptek/edgy xserver-xorg-input-all/edgy xserver-xorg-input-digitaledge/edgy xserver-xorg-input-elographics/edgy xserver-xorg-input-fpit/edgy xserver-xorg-input-hyperpen/edgy xserver-xorg-input-kbd/edgy xserver-xorg-input-magellan/edgy xserver-xorg-input-mouse/edgy xserver-xorg-input-mutouch/edgy xserver-xorg-input-palmax/edgy xserver-xorg-input-spaceorb/edgy xserver-xorg-input-summa/edgy xserver-xorg-input-synaptics/edgy xserver-xorg-input-tek4957/edgy xserver-xorg-input-void/edgy xserver-xorg-input-wacom/edgy xserver-xorg-video-all/edgy xserver-xorg-video-apm/edgy xserver-xorg-video-ark/edgy xserver-xorg-video-ati/edgy xserver-xorg-video-ati/edgy xserver-xorg-video-chips/edgy xserver-xorg-video-cirrus/edgy xserver-xorg-video-cyrix/edgy xserver-xorg-video-dummy/edgy xserver-xorg-video-fbdev/edgy xserver-xorg-video-glint/edgy xserver-xorg-video-i128/edgy xserver-xorg-video-i740/edgy xserver-xorg-video-i810/edgy xserver-xorg-video-imstt/edgy xserver-xorg-video-mga/edgy xserver-xorg-video-neomagic/edgy xserver-xorg-video-newport/edgy xserver-xorg-video-nv/edgy xserver-xorg-video-rendition/edgy xserver-xorg-video-s3/edgy xserver-xorg-video-s3virge/edgy xserver-xorg-video-savage/edgy xserver-xorg-video-siliconmotion/edgy xserver-xorg-video-sis/edgy xserver-xorg-video-sisusb/edgy xserver-xorg-video-tdfx/edgy xserver-xorg-video-tga/edgy xserver-xorg-video-trident/edgy xserver-xorg-video-tseng/edgy xserver-xorg-video-v4l/edgy xserver-xorg-video-vesa/edgy xserver-xorg-video-vga/edgy xserver-xorg-video-vmware/edgy xserver-xorg-video-voodoo/edgy xutils/edgy xvfb/edgy x-window-system/edgy x-window-system-core/edgy
```[/INDENT]Again, what I've done _***should* be completely safe**_, but **use it at your own risk**!


**[SIZE=3]How did I do this?[/SIZE]**
I've wrote _[**a post**]("http://ubuntuforums.org/showpost.php?p=2320957&postcount=81")_ where there's a small guide to get the same for your machine (fo getting optimized builds or for other archs)


Bye! :KS

---

### Post by quake74 on 2007-03-01
Hi, I just tried your repo but I have issues with the DRI module. The error is

/usr/X11R6/bin/X: symbol lookup error: /usr/lib/xorg/modules/extensions//libdri.
so: undefined symbol: drmSetServerInfo

If I disable the dri module, it works fine.

Edit: and trying to start ppracer gives

ppracer: symbol lookup error: /usr/lib/libGL.so.1: undefined symbol: drmCloseOnce

Edit2: I guess I need libdrm at least 2.3.0

---

### Post by hornett on 2007-03-01
Thanks a lot for packaging these up. I have them installed and they are working a treat. 

Not much visible difference from 7.1 if I'm completely honest, but I did notice that my beryl genie animation suddenly got smooth :D

---

### Post by Twiggy794 on 2007-03-01
> Hi, I just tried your repo but I have issues with the DRI module. The error is

/usr/X11R6/bin/X: symbol lookup error: /usr/lib/xorg/modules/extensions//libdri.
so: undefined symbol: drmSetServerInfo

If I disable the dri module, it works fine.
Same here.

Edit: Building libdrm 2.3 just results in insanely slow and buggy performance

---

### Post by BOBSONATOR on 2007-03-01
This totally jacked my Xorg, even though it sucessfully upgraded, it did alot of other stuff, and now i cant even get into x, or see a log on screen

so i go into safe mode and

dpkg-reconfigure xserver-xorg, and every option i pick still wont work.


Please help.
Thanks in advance,

---

### Post by Treviño on 2007-03-01
Sorry about libdrm... I had compiled it months ago, but I forgot to include it on repo... Wait few minutes and update again, it will be there! ;)

**BOBSONATOR**, could you pastebin your Xorg.log ?

---

### Post by nonameruler on 2007-03-01
hi, 

I had the same problem, and backported libdrm2 from feisty to dapper.

Look at the attachement

---

### Post by Treviño on 2007-03-01
Thanks, but now these files are on repo :)

---

### Post by quake74 on 2007-03-01
> **Treviño said:**
> Thanks, but now these files are on repo :)

Yep, reinstalled (I reverted back to 7.1 in the meantime) and it works. On my laptop ATI X600SE using "ati" driver, I get a good performance improvement, will test the stability in the future. So, what else is new and cool about 7.2?

---

### Post by pwk on 2007-03-01
> **BOBSONATOR said:**
> This totally jacked my Xorg, even though it sucessfully upgraded, it did a lot of other stuff, and now i cant even get into x, or see a log on screen

This upgrade also broke my system and I couldn't repair it. The downgrade method suggested failed with dependency problems. 

I was hoping to fix the Beryl white screen of death but I got the GDM screen of death instead.

Never mind, I just upgraded the whole system to feisty as an easy fix.

---

### Post by Treviño on 2007-03-01
> **quake74 said:**
> Yep, reinstalled (I reverted back to 7.1 in the meantime) and it works. On my laptop ATI X600SE using "ati" driver, I get a good performance improvement, will test the stability in the future. So, what else is new and cool about 7.2?Mh, you can have water with beryl/compiz? :D

You can read more on [Xorg 7.2 Release Notes]("http://xorg.freedesktop.org/wiki/PressReleases/X11R72Released")

---

### Post by nfm on 2007-03-01
How can white screen of death be fixed? I can see login screen, I don't want to reinstall edgy again.

:sad: edit: nevermind, it's beryl issue and I got around it :)

---

### Post by Treviño on 2007-03-01
Are you using AiGLX isn'it it?

In this case, do a:
```
ldd /usr/bin/beryl|grep libGL
```
It should give you something like:
> libGL.so.1 => /usr/lib/libGL.so.1 (0xb7e4c000)
If it points to any other file (like ones located on /usr/X11R6/lib/), try to run:
```
LD_PRELOAD=/usr/lib/libGL.so.1.2 beryl --replace
```
If this works (and it *should* work), simply (re)move the file you found using the "ldd" command before.

Bye

PS: I've uploaded a new server with newer ubuntu patches ;)

---

### Post by BOBSONATOR on 2007-03-01
> **Treviño said:**
> Sorry about libdrm... I had compiled it months ago, but I forgot to include it on repo... Wait few minutes and update again, it will be there! ;)

**BOBSONATOR**, could you pastebin your Xorg.log ?

I cant even see a graphical interface, nor can i use the internet, i think i will just upgrade to feisty anyways.

---

### Post by Treviño on 2007-03-01
Mhmmhm maybe you could move your log to an external partition (or usb memory) to attach it later...

Or simply try to understand what's wrong using:
```
grep EE /var/log/Xorg.0.log|less
```

---

### Post by BOBSONATOR on 2007-03-02
Well, the Xorg.0.log says something like

```

/usr/bin/X: symbol lookup error:
/user/lib/xorg/modules/extensions//libdri.so: undefined symbol:drmSetServerInfo
```

---

### Post by spockrock on 2007-03-02
I am thinking of trying this out, but I use the nvidia proprietary driver any improvements? oh well I guess there is only one way to find out...

---

### Post by quake74 on 2007-03-02
> **BOBSONATOR said:**
> Well, the Xorg.0.log says something like

```

/usr/bin/X: symbol lookup error:
/user/lib/xorg/modules/extensions//libdri.so: undefined symbol:drmSetServerInfo
```

I had the same problem, but it went away as soon as trevino added libdrm2 to his packages. Did you install that too? (sudo apt-get install libdrm2) You should have 2.3.0+git20070118~3v1ubuntu0

---

### Post by BOBSONATOR on 2007-03-02
i cant do that because i cant get into the internet.......................................

---

### Post by 23meg on 2007-03-02
[QUOTE=Treviño]Edit your sources.list with your favorite text editor (i.e. sudo gedit /etc/apt/sources.list) and add my new repo[/QUOTE]

A small correction: you should change the "sudo gedit" bit to "gksudo gedit".

---

### Post by 23meg on 2007-03-02
After the update, Compiz stopped working here.

```
compiz.real: No GLXFBConfig for default depth, this isn't going to work.
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0

```

A problem with Mesa, do you think? This is on an NVidia Geforce Go6200.

---

### Post by Treviño on 2007-03-02
> **23meg said:**
> A small correction: you should change the "sudo gedit" bit to "gksudo gedit".Well, I leaved it so to make it work also with kubuntu (and I think) xubuntu that have a symbolic link to gedit, but don't use gksudo.

Then, about your Nvidia problem, I've read (in beryl-forum) that it works for some users, maybe you should regenerate your nvidia drivers? :o

---

### Post by lazyd2 on 2007-03-02
It's working just perfect. Thanks!

---

### Post by spockrock on 2007-03-02
ok installed, then re-installed nvidia drivers, and holy crap way faster, kudos trevino!!!

---

### Post by venkatu on 2007-03-02
> Hi, I just tried your repo but I have issues with the DRI module. The error is

/usr/X11R6/bin/X: symbol lookup error: /usr/lib/xorg/modules/extensions//libdri.
so: undefined symbol: drmSetServerInfo

If I disable the dri module, it works fine.


this situation persists for me even with the updated libdrm2 (2.3.0+git20070118~3v1ubuntu0) on a mach64 chipset. disabling dri in xorg.conf get's X going, albeit with no acceleration. anybody know how to get a dev snapshot of libdrm2 for compiling?

thanks.

---

### Post by sabrebutt on 2007-03-02
Great job! Works perfect. Much smoother animations and better stability.

---

### Post by BOBSONATOR on 2007-03-02
> **BOBSONATOR said:**
> i cant do that because i cant get into the internet.......................................

K i fixed it with the libdrm2, now everything is artifactling like, what to do from then?

---

### Post by Treviño on 2007-03-02
> **venkatu said:**
> this situation persists for me even with the updated libdrm2 (2.3.0+git20070118~3v1ubuntu0) on a mach64 chipset. disabling dri in xorg.conf get's X going, albeit with no acceleration. anybody know how to get a dev snapshot of libdrm2 for compiling?

thanks.[http://packages.ubuntu.com/feisty/source/libdrm](http://packages.ubuntu.com/feisty/source/libdrm)
If you want a more updated package you can download it from freedesktop's git ;)

**BOBSONATOR**, what's the problem now exactly :o

---

### Post by 23meg on 2007-03-02
[QUOTE=Treviño]Well, I leaved it so to make it work also with kubuntu (and I think) xubuntu that have a symbolic link to gedit, but don't use gksudo.[/QUOTE]

It's [not a good idea]("http://www.psychocats.net/ubuntu/graphicalsudo") to encourage its use. 

[QUOTE=Treviño]Then, about your Nvidia problem, I've read (in beryl-forum) that it works for some users, maybe you should regenerate your nvidia drivers? [/QUOTE]

I'll try that, thanks.

---

### Post by 23meg on 2007-03-03
For the record, reinstalling the driver fixed it and Compiz is running noticeably better on Xorg 7.2.

---

### Post by hornett on 2007-03-03
Oh dear, had this all running perfectly the other day, but I installed an update for something Xorgish* today and since then wine won't run. Instead my X server crashes.

In my /var/log/Xorg.0.log.old I get this:

```
...
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80bfb81]
1: [0xffffe420]

Fatal server error:
Caught signal 11.  Server aborting

```


Any ideas ? :confused:

Not sure what package I need to install to get debug info for that backtrace...

*I think the new packages were xserver-xorg-core_2%3a1.2.0~3v1ubuntu1_i386.deb and xserver-xorg-dev_2%3a1.2.0~3v1ubuntu1_i386.deb

---

### Post by spockrock on 2007-03-03
have you tried rebooting, I got the signal eleven crash in xorg 7.1 but the problem was I do not think the nvidia-glx package completely removed it self.

---

### Post by hornett on 2007-03-03
Thanks, spockrock. I, rebooted and reinstalled the nvidia driver, still no go. :(

Going to try purging and reinstalling everything related to Xorg, in case some random library has been corrupted or something.

---

### Post by Faytz on 2007-03-03
If your having a gpg key error when typing in sudo apt-get update
 try upgrade instead of update.It works

---

### Post by hornett on 2007-03-03
Right, got it sorted. Not sure what it was but a full reinstall of the xorg packages solved it. 

Perhaps something didn't get upgraded properly the first time..?

Anyway, thanks again for posting these.

---

### Post by iam_foo on 2007-03-03
ha!

yeah..this is great.

thanks.

---

### Post by adam.tropics on 2007-03-03
Magic Lamp effects in Beryl seem a bit better, though it is a bit hard to tell. However, and it's a BIG HOWEVER, USB hotplugging (my MX1000 mouse) now works. That's worth it on its own, so thank you.

---

### Post by GoBieN on 2007-03-04
A big thank you, because it seems that you have just solved my problem with X hanging on me in Edgy with an ATI Rage on a SMP-server.  see here: [http://www.ubuntuforums.org/showthread.php?t=339954](http://www.ubuntuforums.org/showthread.php?t=339954)

---

### Post by sorcererx84 on 2007-03-05
With latest updates (xserver-xorg-video-i810 v 1.7.4, i915gm card) I get:
> libGL warning: 3D driver claims to not support visual 0x5b
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.

When trying to run a 3d app. No performance increase also.

---

### Post by DarkN00b on 2007-03-05
Hmm. Not noticing any difference except that My Beryl-ized window drop shadows become transparent cutting through all windows clean down to the desktop. Maybe something to do with the Intel chipset I have in this laptop?

---

### Post by Treviño on 2007-03-05
Well, the libGL waring is a normal thing, the rest is unknown to me, I've just synced my packages to newer ones available on feisty...
Maybe you can bug-report on launchpad about feisty packages (since mine are the same, but compiled under edgy).

Any other problem (I mean, something really not working, more than messages...)?

Anyway the xorg intel module has few importance on 3d performances, it simply makes Xorg manage the card, so for getting a performance enhancement must be updated Mesa (mostly).

---

### Post by benobi on 2007-03-05
Yeah.. Great upgrade. Now my beryl is damn slow.
I have an intel i915 chip using i810 driver. Before the update to xorg 7.2, my beryl was working great, now since the upgrade to xorg 7.2 everything is sluggish (simply unusable, had to go back to Kwin).

I've tried the i810-modesetting driver, no improvement.
xorg.conf is fine, composite enable, etc... tried pretty much every possible trick in my xorg.conf and I crashed X a couple of times. The good part is that I refreshed my vi skills....

Anyway, read tons of post on the forums about xorg 7.2, intel and beryl over the last couple of days and can't find a solution to that sudden beryl slugginesssssssssss. And, no, I'm not the only unlucky folk here, it seems to be a global intel problem.

If you have an intel chip, do not upgrade, for now, you're better off without xorg 7.2.

---

### Post by Treviño on 2007-03-05
Have you set the acceleration mode to XAA instead of EXA (it's bugged on xorg 7.2, see on launchpad), or try to downgrade the intel video driver (use synaptic and select the previous I had released).

No others that have updated found what you did...

---

### Post by olskar on 2007-03-06
Thanks Treviño! I did the upgrade and I think that beryl got smoother..Maybe I am just imaging but that doesnt matter..no problems anyway.. :)

---

### Post by c0nv1ct on 2007-03-07
The upgrade went fine, didn't break anything. But 'Xorg -version' says 7.1.1, so i'm not sure if it even upgraded.

After the upgrade, adept manager tells me theres 2 more updates, one is libgl1-mesa-dev, which says it can't install, gives a 'BREAK (upgrade)' error.  The other is mesa-common-dev, which when i select it, wants to remove a ton of dev packages, including kde-devel, kdebase-dev, and about 10 others.

---

### Post by Treviño on 2007-03-07
> **c0nv1ct said:**
> The upgrade went fine, didn't break anything. But 'Xorg -version' says 7.1.1, so i'm not sure if it even upgraded.

After the upgrade, adept manager tells me theres 2 more updates, one is libgl1-mesa-dev, which says it can't install, gives a 'BREAK (upgrade)' error.  The other is mesa-common-dev, which when i select it, wants to remove a ton of dev packages, including kde-devel, kdebase-dev, and about 10 others.Maybe you tried to upgrade when I haven't finished to upload all the files... Retry please.
Latest mesa update I uploaded has [fixes]("https://launchpad.net/ubuntu/+source/mesa/+bug/90169") for radeon r300 users.

If [FONT=Courier New]X -version[/FONT] gives you a bad version, try to see to which file it points... I mean
[FONT=Courier New]which X[/FONT] should give you[FONT=Courier New] /usr/bin/X[/FONT]

---

### Post by c0nv1ct on 2007-03-07
'which X' gives '/usr/bin/X' and here is what 'X -version' gives:

```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 x86_64
Current Operating System: Linux RA-XPC 2.6.17-11-generic #2 SMP Thu Feb 1 18:03:05 UTC 2007 x86_64
Build Date: 07 July 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present

```

---

### Post by ykpaiha on 2007-03-07
sorry tried just now and I got:

libberylsettings: dlopen: /usr/lib/beryl/libbench.so: cannot open shared object file: No such file or directory
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libwallpaper.so' plugin
beryl: No GLXFBConfig for default depth, falling back on visinfo.
beryl: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
beryl: Plugin 'dbus':initDisplay failed
beryl: Couldn't activate plugin 'dbus'
Couldn't initialize dbus. This should not happen!
Erreur de segmentation (core dumped)

so no more beryl sniff where do I look now ?
thanks

---

### Post by Treviño on 2007-03-07
Strange, from latest beryl update there are some problems, because some plugins should be updated, but I can run it well... Are you using Xgl or AiGLX?

**c0nv1ct**, simply check you've installed well my packages... And xserver-xorg-core first of all

---

### Post by ykpaiha on 2007-03-07
all seems ok as far as I can see but i just checked the beyl forum it seems a bit the same
[http://forum.beryl-project.org/viewtopic.php?f=36&t=4633&p=26095&hilit=libbench#p26095](http://forum.beryl-project.org/viewtopic.php?f=36&t=4633&p=26095&hilit=libbench#p26095)
[http://forum.beryl-project.org/viewtopic.php?f=36&t=4626&p=26077&hilit=libbench#p26077](http://forum.beryl-project.org/viewtopic.php?f=36&t=4626&p=26077&hilit=libbench#p26077)

I keep looking forward with standar metacity for now
Unless you got an idea
thanks

---

### Post by gatiba on 2007-03-07
> **nfm said:**
> How can white screen of death be fixed? I can see login screen, I don't want to reinstall edgy again.

:sad: edit: nevermind, it's beryl issue and I got around it :)

How do you solved the white screen's problem?

---

### Post by c0nv1ct on 2007-03-07
> **gatiba said:**
> How do you solved the white screen's problem?

The only fix for the white screen problem so far is to run beryl with this command:

```
beryl --use-copy
```

> **Treviño said:**
> 
**c0nv1ct**, simply check you've installed well my packages... And xserver-xorg-core first of all

I've checked my xserver-xorg package, and it is installed, and says its 7.2.  But a package just called 'xorg' is shown to be installed as well and states its version 7.1.  So should I remove 'xorg' and then reinstall xserver-xorg?

---

### Post by Treviño on 2007-03-07
Mh, no... It is only a Metapackage... Your situation is so strange :o

---

### Post by wax4213 on 2007-03-08
It works perfectly for me, except on every update I get the white screen (I'm using Beryl).  I can fix it by using envy to reinstall my nvidia drivers.  I have the Go 440 card, which uses the old 1.6.xx drivers, and envy is the most convenient way to install those.  I just make sure to not let it configure my xorg file, because then it turns compositing off.  Fixing it afterwards is an easy fix, but I'm lazy.

---

### Post by gatiba on 2007-03-08
White screen's problem resolved for me too reinstalling Nvidia drivers ;)

---

### Post by moptop on 2007-03-09
> **hornett said:**
> Oh dear, had this all running perfectly the other day, but I installed an update for something Xorgish* today and since then wine won't run. Instead my X server crashes.

In my /var/log/Xorg.0.log.old I get this:

```
...
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80bfb81]
1: [0xffffe420]

Fatal server error:
Caught signal 11.  Server aborting

```


Any ideas ? :confused:

Not sure what package I need to install to get debug info for that backtrace...

*I think the new packages were xserver-xorg-core_2%3a1.2.0~3v1ubuntu1_i386.deb and xserver-xorg-dev_2%3a1.2.0~3v1ubuntu1_i386.deb
lots of reasons to suggest this is an upstream bug, believed fixed in ubuntu, but probably still persistent.  some links:

[https://bugs.freedesktop.org/show_bug.cgi?id=8537](https://bugs.freedesktop.org/show_bug.cgi?id=8537) (the upstream bug)
[https://bugs.freedesktop.org/show_bug.cgi?id=1753](https://bugs.freedesktop.org/show_bug.cgi?id=1753) (or maybe this is really the upstream bug?)
[http://ubuntuforums.org/newreply.php?do=postreply&t=354697](http://ubuntuforums.org/newreply.php?do=postreply&t=354697) (a recent forum thread with reports from edgy and feisty users)
[http://linuxfud.wordpress.com/2006/09/29/ubuntu-crashes-on-start-and-returns-to-the-login-screen/](http://linuxfud.wordpress.com/2006/09/29/ubuntu-crashes-on-start-and-returns-to-the-login-screen/) (a similar issue )
[http://gnomesupport.org/forums/viewtopic.php?t=12299](http://gnomesupport.org/forums/viewtopic.php?t=12299) (another indication this is a gnome-specific issue, even if the bug is really in xorg)
[http://bugs.beryl-project.org/ticket/684](http://bugs.beryl-project.org/ticket/684) (beryl discussion of this bug)

matt

---

### Post by berserker on 2007-03-10
I upgraded to Xorg 7.2 and then downgraded to 7.1.1 after two days because of a huge memory leak in 7.2.  It appears this is a common [problem]("http://forums.gentoo.org/viewtopic-t-537634-postdays-0-postorder-asc-start-0.html?sid=a9ae18e8b365575c7a8e46108d0ff8d6").

---

### Post by LookTJ on 2007-03-10
[LIST]
[*]added repo
[*]updated repo
[*]upgraded xorg
[*]restarted xorg/gdm
[*]had a problem, ctrl+alt+f1, login and ran dpkg-reconfigure xserver-xorg
[*]ran /etc/init.d/gdm restart
[*]had same white screen of death so i reran the scripts and chose ati instead of fglrx
[*]gdm shows up[/LIST]I noticed my touchpad mouse works better.

dumb ATi!
go nVidia!

---

### Post by Oen386 on 2007-03-11
This fixed a lot of my issues with Beryl. :)

---

### Post by AlexTheMad on 2007-03-12
it worked fine for me... except one thing, now my font login sceen font is huuuuge, and it is the same in amsn. It's really horrid to use now. Somebody with a clue as to what I should do?

edit:

also the water effect works now :D

---

### Post by Treviño on 2007-03-12
Did you read the EXA thing on main post?

---

### Post by ZenYoga on 2007-03-14
I'm having the same problem with big fonts on login screen.
Isn't XAA rendering on by default, /etc/X11/xorg.conf file isn't edited.

---

### Post by Treviño on 2007-03-14
Maybe you should set the default dpi to run with your X server...
On gnome gnome-system-daemon manages them..

---

### Post by Rizado on 2007-03-16
It seems to work pretty fine, I haven't noticed any differences yet. Although I had to reinstall the nvidia drivers and it complained that /usr/lib/xorg/modules/extensions/libglx.so is not a symbolic link. I'm pretty sure it was before this update. Actually I just checked it out and it IS a symbolic link. Strange...

Another thing I've noticed is that "glxgears -printfps" isn't working anymore...

---

### Post by berserker on 2007-03-16
Does the package "xserver-xorg-core" contain the patch mentioned in the bug report [here]("https://bugs.freedesktop.org/show_bug.cgi?id=10009")?

---

### Post by Treviño on 2007-03-16
**Rizado**, yes actually glxgears doesn't need anymore the printfs parameter...

**berserker**, I don't think, I use the standard feisty version actually and it doesn't seem to include it, so please post an issue on launchpad to make that patch to be included on upstream, from my part I'll try to add it on my builds...

---

### Post by berserker on 2007-03-16
> **Treviño said:**
> **berserker**, I don't think, I use the standard feisty version actually and it doesn't seem to include it, so please post an issue on launchpad to make that patch to be included on upstream, from my part I'll try to add it on my builds...

I posted a comment and the patch [here]("https://launchpad.net/ubuntu/+source/xorg/+bug/77606").

---

### Post by Treviño on 2007-03-16
> **berserker said:**
> I posted a comment and the patch [here]("https://launchpad.net/ubuntu/+source/xorg/+bug/77606").
Good, but the right source package is xserver-xorg, so I've integred the bug I've found at [https://beta.launchpad.net/ubuntu/+source/xorg-server/+bug/92882](https://beta.launchpad.net/ubuntu/+source/xorg-server/+bug/92882) (posted by someone today too) and marked yours as duplicate of it.

Anyway I'll apply the patch to my package, so wait for it ;)

---

### Post by Rizado on 2007-03-16
> **Treviño said:**
> **Rizado**, yes actually glxgears doesn't need anymore the printfs parameter...What the... What's the reason for that? I used it all the time to check that my drivers were installed correctly.

---

### Post by berserker on 2007-03-16
> **Rizado said:**
> What the... What's the reason for that? I used it all the time to check that my drivers were installed correctly.

The command ```
glxgears
``` used to output the frames per second.  Then some time ago it was changed to ```
glxgears -printfps
``` (among others).  Someone wisely decided that's the whole reason anyone runs it in the first place so now we're back to ```
glxgears
``` with no parameters required for fps.

Another way to check if your video driver is correctly installed is to use ```
glxinfo
```

---

### Post by Treviño on 2007-03-16
Exactly that... :)

BTW, I've updated the xorg packages, you should have downloaded them yet from my repo... They include now the patch to fix the memory leak of bug [92882]("https://beta.launchpad.net/ubuntu/+source/xorg-server/+bug/92882")

Let me know if you see a performance increasement ;)

---

### Post by berserker on 2007-03-16
> **Treviño said:**
> Exactly that... :)

BTW, I've updated the xorg packages, you should have downloaded them yet from my repo... They include now the patch to fix the memory leak of bug [92882]("https://beta.launchpad.net/ubuntu/+source/xorg-server/+bug/92882")

Let me know if you see a performance increasement ;)

I'm not sure about the performance increase just yet but it appears the memory leak is gone.

Thank you, Treviño!

---

### Post by Rizado on 2007-03-17
> **berserker said:**
> The command ```
glxgears
``` used to output the frames per second.  Then some time ago it was changed to ```
glxgears -printfps
``` (among others).  Someone wisely decided that's the whole reason anyone runs it in the first place so now we're back to ```
glxgears
``` with no parameters required for fps.Oh, that's kinda stupid of me. Should have let it run for more than 5 seconds :) Actually I had just memorized -printfps. When I first started using linux it wasn't necessary (As you say)

---

### Post by edmondt on 2007-03-17
Works good for me, on Edgy... Beryl 0.2 works too. But I had to recompile the nvidia driver again for some reason tho. 

I used Envy to do that and it works great.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Oen386 on 2007-03-17
I just had Update Manager update my Xorg files. What can I do to reinstall these files? Whenever I try to run the commands again I get errors (because I think it is already installed of course).

:(

---

### Post by spockrock on 2007-03-17
never mind all is working well now

---

### Post by aluminum87 on 2007-03-17
Hi Treviño!...thanks for putting in the effort with the Edgy Xorg 7.2 repository. I'd really appreciate it if you could compile the same tweaked version for Edgy PPC; after I discovered that the ATI drivers work on the LiveCD of Feisty Herd 5, on 7.2, I realized this is going to be my last hope to use Beryl on a fully-supported version of Ubuntu for my architecture! Would you be willing to do this?

Thanks!
-JW

---

### Post by Treviño on 2007-03-17
I've no ppc hardware so I can't do it... Is there a way to compile for another arch?

---

### Post by berserker on 2007-03-17
Perhaps I spoke too soon.  Xorg is up to over 300 MB after 24 hours.  Will keep an eye on it.

EDIT:  Reinstalled the "xserver-xorg" and "xserver-xorg-core" packages and 24 hours later Xorg usage is 78 MB and holding.

---

### Post by aluminum87 on 2007-03-19
I'll have to look into that, but is there any way for you to host the modified source files, or to go into any detail about how you managed to edit the versions to avoid conflict? I could compile it myself and try it out if you were able to do that.

---

### Post by Treviño on 2007-03-19
> **aluminum87 said:**
> I'll have to look into that, but is there any way for you to host the modified source files, or to go into any detail about how you managed to edit the versions to avoid conflict? I could compile it myself and try it out if you were able to do that.

This is how I did this...

First of all you should edit your [FONT=Courier New]/etc/sources.list[/FONT] file adding this source repository:[INDENT]```
# Ubuntu feisty main and universe sources repository
deb-src http://archive.ubuntu.com/ubuntu feisty main universe
```[/INDENT]Then do a sudo [FONT=Courier New]sudo apt-get update[/FONT] and make a working dir and save and [FONT=Courier New]chmod +x[/FONT] this script into it (I called it "repackage") editing the optional fields:[INDENT]```
#!/bin/bash

packager="YourName"
packager_email="name@company.net"
version_sufix="~YourSufix0"

distro="$(cat "/etc/lsb-release"|grep "DISTRIB_CODENAME" | cut -d'=' -f2)"; #edgy

for i in ./*; do 
    if ( [ -d "$i" ] && [ -d "$i/debian" ] && [ ! -f "$i/.done" ] ); then 
        cd $i; 
        old_version=$(dpkg-parsechangelog|grep --max-count=1 -F "Version:" |cut -d" " -f2);
        source_package=$(dpkg-parsechangelog|grep --max-count=1 -F "Source:" |cut -d" " -f2);
        package=$(grep -F -m1 "Package:" "./debian/control" | cut -d" " -f2)
        #version=$(expr "$version" : "\([^-]\+\).*"); # edit version as you want
        #version=$(expr "$old_version" : "\([0-9:.-]\+\).*"); # edit version as you want
        version=$(echo $old_version | sed "s/ubuntu/$distro/")
        #version=$old_version
        #if TODO check installed version and autoselect version type
        #echo -e "$old_version -> $version";
        mv "./debian/changelog" /tmp;
        echo -e "$source_package (${version}${version_sufix}) $distro; urgency=low\n\n  * Repackaged under $distro by  $packager\n\n -- $packager <$packager_email>  $(LANG=en_US date +"%a, %d %b %Y %T %z")\n" > "./debian/changelog"
        cat "/tmp/changelog" >> "./debian/changelog"
        if debuild binary; then
            debuild clean
            mv "/tmp/changelog" "./debian/changelog" -v
            echo "" > "./.done"
        else
            mv "/tmp/changelog" "./debian/changelog" -v
        fi
        cd ..;
    fi;
done

rm -f /tmp/changelog

```[/INDENT]So you can run these commands:[INDENT] ```
apt-get source libdrm x11proto-damage x11proto-gl x11proto-randr x11proto-input xkeyboard-config
sudo chown $USER:$USER ./ -R #maybe not needed; I won't repeat it.
./repackage
```[/INDENT]Install the *.deb files you've just made; then[INDENT]```
apt-get source mesa
./repackage
```[/INDENT]Again, install the mesa .debs you've done (or just the *-dev ones); consider that you could have problems installing both the libosmesa* files an the glx ones; most important is mesa-swx11-source[INDENT]```
apt-get source xorg-server
./repackage
```[/INDENT]Install the debs file you've made (the *-dev ones are mostly important too):[INDENT]```
apt-get source wacom-tools xorg xserver-xorg-input-acecad xserver-xorg-input-aiptek xserver-xorg-input-calcomp xserver-xorg-input-citron xserver-xorg-input-digitaledge xserver-xorg-input-dmc xserver-xorg-input-dynapro xserver-xorg-input-elo2300 xserver-xorg-input-elographics xserver-xorg-input-evdev xserver-xorg-input-fpit xserver-xorg-input-hyperpen xserver-xorg-input-jamstudio xserver-xorg-input-joystick xserver-xorg-input-keyboard xserver-xorg-input-magellan xserver-xorg-input-magictouch xserver-xorg-input-microtouch xserver-xorg-input-mouse xserver-xorg-input-mutouch xserver-xorg-input-palmax xserver-xorg-input-penmount xserver-xorg-input-spaceorb xserver-xorg-input-summa xserver-xorg-input-synaptics xserver-xorg-input-tek4957 xserver-xorg-input-ur98 xserver-xorg-input-vmmouse xserver-xorg-input-void xserver-xorg-video-amd xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-cyrix xserver-xorg-video-dummy xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-i810 xserver-xorg-video-i810-modesetting xserver-xorg-video-imstt xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-newport xserver-xorg-video-nsc xserver-xorg-video-nv xserver-xorg-video-rendition xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-unichrome xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-vga xserver-xorg-video-via xserver-xorg-video-via xserver-xorg-video-vmware xserver-xorg-video-voodoo
./repackage
```[/INDENT]Install the needed packages you've made and that's all :)

---

### Post by Shibby73 on 2007-03-19
Well... I guess a newb shouldn't try to hang with the big boys - advanced users.

I followed instructions for beryl and xorg 7.2  now my edgy 6.10 and beryl don't work.
I can't even get into a working desktop, at best I seem to hang with the beryl splash page.
Prior to this event, beryl was making my windows (ie. beryl manager settings, opera favorites, any new window) not load the contents in a visible manner, sometimes I could get it back by minimizing and maximizing the window.  It is very glitchy.

I have a laptop by acer travel mate 800LCi 1.3ghz with an ATI radeon 9000 3d graphic card/64mb

Well I don't know what I am doing well enough to get back into my ubuntu.
I fortunately can get online with my evdo card, but that is by starting up in win xp, I have no clue how to get the evdo working (I am travelling) for a new ubuntu install, but even before that step I am worried I may overwrite the wrong partition with the live cd just to get back to a functioning ubuntu edgy 6.10 (I think it should overwrite the /et3? partition and not the fat32).  Any help would be great, I don't think I am ready to try beryl just to have a cool cube flipping animation (it was cool while it worked).  I strongly suspect some kind of memory leak was happening, but don't know how to prove that now.  The thing worked well at first and kept getting slower and buggy until now it doesn't work at all.

What do you guys recommend me to do?
Can I fix this from a safe mode with some command lines or something, I probably won't have internet access in linux however.

Best regards, this is a major learning experience.

-Steve (shibby73)
[email]smorrea-nospam-@stansgnosticus.net[/email]

---

### Post by spockrock on 2007-03-20
hmm on the the recent updates cause X to hardlock, its kinda frustrating... >_<

when I try to go back, I get, this;
```

  libgl1-mesa-dev: Conflicts: libgl-dev
  libgl1-mesa-glx: Conflicts: libgl1
  libgl1-mesa-swx11: Conflicts: libgl1
  libgl1-mesa-swx11-dev: Conflicts: libgl-dev

```

breakage, lol....

---

### Post by aluminum87 on 2007-03-20
Wow, that's really thorough, thanks for the effort, Treviño. :) If I could just ask you for one clarification, though - which are the strings I should edit, and what version information should I replace them with?

Also, I noticed that on your repository website, some of the files are versioned with ~3v1ubuntu0 and others with ~3v1ubuntu2, how should I compensate for this?

Again, thanks.

---

### Post by aluminum87 on 2007-03-20
also, one more thing - is there a way to resolve dependency issues for the script you provided? I think I managed to track down all the development-related packages it references, but just in case there's something less obvious...

---

### Post by Incie83 on 2007-03-20
Upgrade to Xorg 7.2 went smoothly, or so it seemed. There is, however, one problem: I can only use Metacity at the moment since Beryl acts strange (windows/menus show just the borders, but no content).

I tried disabling DRI but that just gives me the white screen (which I can't resolve by running beryl --use-copy).

I use Beryl 0.1.1 from the beerorkid repos and my xorg.conf looks like this (I left out alll the keyboard/tablet stuff):

```

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
	Load 	"dri"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option          "AGPMode"       "8"
        Option          "AccelMethod"   "XAA"
        Option          "ColorTiling"   "on"
	Option          "TripleBuffer" 	"true"
	Option		"UseFBDev"	"true"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	DisplaySize	338	270	# 1280x1024 96dpi
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Monitor		"SyncMaster"
	DefaultDepth	24
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
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "on"
EndSection


```

Any help is greatly appreciated!

---

### Post by Waappu on 2007-03-20
Hi

Some problems to get latest update
> W: Failed to fetch [http://download.tuxfamily.org/3v1deb/pool/edgy/xorg-7.2/libgl1-mesa-glx_6.5.2~3v1ubuntu3_i386.deb]("http://download.tuxfamily.org/3v1deb/pool/edgy/xorg-7.2/libgl1-mesa-glx_6.5.2%7E3v1ubuntu3_i386.deb")
  404 Not Found


W: Failed to fetch [http://download.tuxfamily.org/3v1deb/pool/edgy/xorg-7.2/libglu1-mesa_6.5.2~3v1ubuntu3_i386.deb]("http://download.tuxfamily.org/3v1deb/pool/edgy/xorg-7.2/libglu1-mesa_6.5.2%7E3v1ubuntu3_i386.deb")
  404 Not Found


W: Failed to fetch [http://download.tuxfamily.org/3v1deb/pool/edgy/xorg-7.2/mesa-utils_6.5.2~3v1ubuntu3_i386.deb]("http://download.tuxfamily.org/3v1deb/pool/edgy/xorg-7.2/mesa-utils_6.5.2%7E3v1ubuntu3_i386.deb")
  404 Not FoundAnd if you are intrested I get attached message always visiting your page.
[http://3v1n0.tuxfamily.org/dists/edgy/xorg-7.2/index.html](http://3v1n0.tuxfamily.org/dists/edgy/xorg-7.2/index.html)

---

### Post by Treviño on 2007-03-20
First of all I fixed all the problems related to the latest mesa update, my upload-script had some problems :P

Then, **aluminium87**: you should edit the first three lines of the script with your values (the ones you want), I haven't manage a build dependency management but you can do it manually with few problems I think. The different version tag like ~3v1ubuntu0 or ~3v1ubuntu2 means a rebuild against newer sources or with my own patches...

**Incie83**, try to upgrade to beryl 0.2 or 0.3svn from my beryl-svn repo ;)

---

### Post by shizeon on 2007-03-20
Hi Trevino,   Curious, did the latest Mesa update address the EXA  bugs some of us have been seeing or is that specific to x.org?

---

### Post by Treviño on 2007-03-20
I've no tested about EXA, but I don't think that latest update fixes the bugs related to it (checking changelog and patches); there are no news nor in launchpad and in freedesktop's bugzilla about it...
Just waiting :/

---

### Post by Docter on 2007-03-21
This has made a massive difference on my i810. I'm using a third less RAM to run ubuntu too.


thx

---

### Post by karlhm76 on 2007-03-22
worked great for me, no problems whatsoever. However I can't see any obvious improvements either to the general running of my system.

Beryl runs the same on my Nvidia GF 7600. I was hoping for something a little more dramatic considering some of the posts here.

I was also kind of hoping that it would solve my bluetooth issues that have plagued me ever since I made the switch from Windows to Linux, but nothing new there.

Thanks for the update though, it worked great.

---

### Post by Ehol on 2007-03-22
> **Incie83 said:**
> Upgrade to Xorg 7.2 went smoothly, or so it seemed. There is, however, one problem: I can only use Metacity at the moment since Beryl acts strange (windows/menus show just the borders, but no content).

...

Any help is greatly appreciated!

Same problem here, but I use your repo for Beryl (0.2.0svn)
Now I can only Metacity.
It Seems with Beryl, Xorg isn't able to display contents

Ah, performance doesn't seem to be improved : splash-page of Beryl (to say one) is choppy and slow.

I have a P4 2500 and a ATI 9600Pro
I explicitly told to xorg.conf to use XAA instead of EXA (there was written nowhere, but just in case ...)

---

### Post by timfelgentreff on 2007-03-22
Hi,
works great, stability has greatly improved. However, there are some graphical bugs with the i810 1.7.4 driver you provide. Would it be possible for you, to provide the latest intel driver (version 1.9.92) as a package as well, since it seems to have merged with the i810 now (git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel) ?

In any case, thanks for your great work on your repository, I really appreciate it!
Regards, T.

---

### Post by sc00ter on 2007-03-22
Borked my system.

Upgrade ran OK without any errors. Then after reboot, got GDM login screen OK, then after entering the login credentials the desktop loads, but that's as far as it gets.

Nautilus loads OK but gnome-panel is just a blank bar. No apps. can be launched. ALT-F1, ALT-F2 fails.

Attempted to disable DRI etc. in xorg.conf but still same results, no go.

I'm running Edgy 6.10 with AiGLX on OSS ATI drivers  (as packaged with Edgy) on my Dell C640 with M7 Radeon 7500. Using Beryl 0.2.

Tried all suggestions in this thread, with no success.

Attempted to roll back (downgrade) to 7.1.1, also got the dependency issues as mentioned earlier on in this thread. So no joy there.

No errors reported in Xorg.0.log

Last resort - re-installing ...

MY ADVICE: IF IT AINT BROKE, DON'T FIX IT.

---

### Post by Ehol on 2007-03-23
The dependency issue (or at least what i understand from it ... that is, by far, a real clue to know if i understood it well :D ) is relatively (maybe) easy to solve :
when synaptic tells you that is impossible to downgrade due to dependency issue, just work on the libgl-mesa-dri e libgl-mesa-glx, don't touch the devel ones.
If you let the system downgrade that one and downgrade mesa-common, xorg and xserver (that is a HARD WORK, cause you have first to remove xorg, ubuntu-desktop and some other that i don't remember ... my fault, sorry ... and then reinstall the version you need BEFORE rebotting, otherwise you're stuck with reinstall completely), then, after rebooting, you should be able to remove the devel version and reinstall the current devel ones.
I said you should, cause it worked for me, but I am not sure it could work for everyone.

---

### Post by Treviño on 2007-03-23
> **timfelgentreff said:**
> Hi,
works great, stability has greatly improved. However, there are some graphical bugs with the i810 1.7.4 driver you provide. Would it be possible for you, to provide the latest intel driver (version 1.9.92) as a package as well, since it seems to have merged with the i810 now (git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel) ?

In any case, thanks for your great work on your repository, I really appreciate it!
Regards, T.
I've tried to package that, but it requires Xorg 7.3 that it's actually in GIT, so it's not easy to provide it... Maybe I could upgrade the existent intel packages but I'd prefer to put on repo the same version of the stanard ubuntu feisty...

I'll release when xorg-7.3 will be out and I'll package it for feisty :P

---

### Post by barlaso on 2007-03-27
I'm using ATI radeon 9550 & AIGLX with open drivers.
Upgrading to xorg 7.2 slowed my system down (even metacity) beyond usability.  Downgrading didnt work due to dependency problems.
Thankfully, i had done an extensive backup, and was able to restore my system.
Beryl is quite usable under 7.1
I STRONGLY SUGGEST A SYSTEM BACKUP BEFORE TRYING

note: damn these ati cards, i'll switch to nvidia as soon as i get the chance

---

### Post by Treviño on 2007-03-28
Did you read the warning about EXA? :o

---

### Post by Treviño on 2007-03-28
PLEASE MOD... Remove this duplicate...

---

### Post by wax4213 on 2007-04-04
The newest update is not downloading correctly for me, it give me this error:

```
95% [11 Packages bzip2 0] [9 Release 38789/50.9kB 76%] [Connecting to debs.mich
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://download.tuxfamily.org edgy/xorg-7.2 Packages                       
  Sub-process bzip2 returned an error code (2)

```

and this:

```
Failed to fetch http://download.tuxfamily.org/3v1deb/dists/edgy/xorg-7.2/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

```

---

### Post by berserker on 2007-04-04
> **wax4213 said:**
> The newest update is not downloading correctly for me, it give me this error:

I'm getting the same error.

---

### Post by king_growler on 2007-04-04
> **berserker said:**
> I'm getting the same error.Me too. :(

---

### Post by Treviño on 2007-04-04
Sorry for this... Unfortunately I had finished my 2Gb of space on my repository, but after some cleaning I found about 400MBs... So now all is working again with some updates (there should be improvements for itel users..)

---

### Post by MrZeroo00 on 2007-04-05
> (there should be improvements for itel users..)
For Intel user ?

---

### Post by DnasTheGreat on 2007-04-05
Thanks for the repository! I have an intel i945 and this new Xorg improves things (especially Beryl) considerably for me. (Also, I was beginning to get bored with the lack of bleeding-edge software in Ubuntu. ;))

Anyway, I am getting one error when running any OpenGL app.

```

do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.

```

Any idea what this means?

OpenGL runs perfectly find here, so I'm not worrying about it much. But it would be nice to know what is going on. (For the record the two variables are not set anyway.)

---

### Post by Treviño on 2007-04-05
I don't really know these warnings, but it happens often that devs put some messages on mesa-lib loading for debugging purposes...

---

### Post by ShinjiLeery on 2007-04-05
> **spockrock said:**
> hmm on the the recent updates cause X to hardlock, its kinda frustrating... >_<

when I try to go back, I get, this;
```

  libgl1-mesa-dev: Conflicts: libgl-dev
  libgl1-mesa-glx: Conflicts: libgl1
  libgl1-mesa-swx11: Conflicts: libgl1
  libgl1-mesa-swx11-dev: Conflicts: libgl-dev

```

breakage, lol....

Same problem here... I can't go back to edgy version...

Ah trevino... Dacce na mano :lolflag:

---

### Post by king_growler on 2007-04-06
> **ShinjiLeery said:**
> Same problem here... I can't go back to edgy version...

Ah trevino... Dacce na mano :lolflag:I can't go back either, and the updated 7.2 xorg broke hibernate for me, which I need on my laptop, so I'll need to reinstall this weekend looks like. :(

---

### Post by DizzyTech on 2007-04-08
Here's a slower tip, but it can get you back to XOrg from Edgy without reinstall (7.2 will be in Feisty anyway):

[LIST]
[*]Remove the xorg-7.2 entry from your /etc/apt/sources.list
[*]Reload your repositories, using Synaptic or sudo aptitude update
[*]Open Synaptic
[*]Using the bottom, left-hand corner filters, click on "Status".
[*]Look up.  Click on the filter for "Installed (local or obsolete)".
[*]What comes up in the right is all of the drivers updated to 7.2, as part of the repo in this topic.
[*]Click on each entry in the right, and use Control+E to force the version.  In the dialog box, choose the one that has "edgy" at the end.  If there are multiple ones (edgy-security, edgy-proposed, etc...) choose the latest version that is not in the xorg-7.2 repo.
[*]You will encounter some problems in the Xorg large package.  If you get any errors about a certain version having to be used, skip it and come back.  Once you get to a certain package (I can't remember), you can downgrade them.
[*]Make sure everything in the list pertaining to Xorg, or X, is being downgraded (it'll be a pretty shade of purple).  DO NOT CONTINUE UNTIL THEY ARE ALL GOING TO BE DOWNGRADED!
[*]Press 'Apply'.  Wait for Synaptic to reinstall all of the lower-version packages.
[*]Use Control+Alt+Backspace to restart X.  Problem solved.
[*]Cry tears of joy.
[/LIST]

---

### Post by ShinjiLeery on 2007-04-09
> **DizzyTech said:**
> Here's a slower tip, but it can get you back to XOrg from Edgy without reinstall (7.2 will be in Feisty anyway):

[LIST]
[*]Remove the xorg-7.2 entry from your /etc/apt/sources.list
[*]Reload your repositories, using Synaptic or sudo aptitude update
[*]Open Synaptic
[*]Using the bottom, left-hand corner filters, click on "Status".
[*]Look up.  Click on the filter for "Installed (local or obsolete)".
[*]What comes up in the right is all of the drivers updated to 7.2, as part of the repo in this topic.
[*]Click on each entry in the right, and use Control+E to force the version.  In the dialog box, choose the one that has "edgy" at the end.  If there are multiple ones (edgy-security, edgy-proposed, etc...) choose the latest version that is not in the xorg-7.2 repo.
[*]You will encounter some problems in the Xorg large package.  If you get any errors about a certain version having to be used, skip it and come back.  Once you get to a certain package (I can't remember), you can downgrade them.
[*]Make sure everything in the list pertaining to Xorg, or X, is being downgraded (it'll be a pretty shade of purple).  DO NOT CONTINUE UNTIL THEY ARE ALL GOING TO BE DOWNGRADED!
[*]Press 'Apply'.  Wait for Synaptic to reinstall all of the lower-version packages.
[*]Use Control+Alt+Backspace to restart X.  Problem solved.
[*]Cry tears of joy.
[/LIST]

I can't do this beacuse i can load Xorg. I have to do the operation only with the command shell ;)

---

### Post by Treviño on 2007-04-09
libgl1 and libgl-dev are only meta-packages remove them before with 

sudo apt-get remove -f libgl1 libgl-dev

Then follow my command...

---

### Post by king_growler on 2007-04-11
> **king_growler said:**
> I can't go back either, and the updated 7.2 xorg broke hibernate for me, which I need on my laptop, so I'll need to reinstall this weekend looks like. :(Well, I just wanted to say that it was NOT Treviño's 7.2 xorg packages that broke hibernate. After pounding my head against the table for days, and doing a complete reinstall, I still can't figure out what broke hibernate -- it used to work fine on my Acer Travelmate 4500, but now it just hangs the system (and I simply cannot come-up with any combination of options that will get it work again).

But the one thing I did learn was it wasn't Treviño's packages, so I wanted to correct my mis-statement and say that I think they work great, and offer some nice improvements to the default packages. Thanks! :D

---

### Post by Excentrik on 2007-04-11
Hi all

I upgraded to Xorg 7.2 a few weeks ago, and I was having some problems.
I've posted them here:
[http://ubuntuforums.org/showpost.php?p=2357100&postcount=210](http://ubuntuforums.org/showpost.php?p=2357100&postcount=210)

I've downgraded back to Xorg 7.1.1 after posting the problems and that solved the multiscreen problem, but not the slowness of applications and the Xorg itself. Usually, after a few hours, X starts to become very sluggish and by dragging, for instance, a console window, it stutters and gets the CPU to 100%.

Any hints about any of these problems are most welcome.
Regards,
Excentrik

---

### Post by Treviño on 2007-04-13
Both the problems? I mean the scrolling thing and the multiscreen problem?

For first one did you put XAA as engine?

---

### Post by ShinjiLeery on 2007-04-13
> **Treviño said:**
> libgl1 and libgl-dev are only meta-packages remove them before with 

sudo apt-get remove -f libgl1 libgl-dev

Then follow my command...

I have this error: 

```
xxxxx@xxxxxxx:~/Desktop$ sudo apt-get remove -f libgl1 libgl-dev
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Reading state information... Fatto               
Il pacchetto libgl1 non è installato, quindi non è stato rimosso
Il pacchetto libgl-dev non è installato, quindi non è stato rimosso

```

---

### Post by Excentrik on 2007-04-13
> **Treviño said:**
> Both the problems? I mean the scrolling thing and the multiscreen problem?

For first one did you put XAA as engine?

You mean if I still have both problems?
Then, the answer is no.

Simplifying:
Xorg 7.1.1 - scrolling and slowness problem, multiscreen working
Xorg 7.2    - scrolling and slowness problem, multiscreen NOT working

And I've always used XAA (I never liked EXA that much :p)

---

### Post by nubutu on 2007-04-18
Hi

I succesfully upgraded to Xorg 7.2 a couple of weeks ago, finding a better 3D performance, as well as the possibility to tweak the R300 driver more than I could and so being able to play GoogleEarth alongside AIGLX, for instance.

I notice, though, that 2D tasks are less responsive, and that my laptop's fun starts working more often and louder than before. I'm not entirely sure whether it's related, but I recently saw somebody reporting a R300 bug about 2D performance being somewhat impaired. Could somebody let me know if this happened after upgrading, and what could be done to fix it?

Thanks

Radeon 9700
Xorg 7.2 and all the packages provided by Trevinos's repository.

---

### Post by Treviño on 2007-04-18
I've the same card (mobility) but it seems to work well here... I didn't noticed this fun problem, but maybe it's me... :P

---

### Post by nubutu on 2007-04-18
Uhm...most likely it's me.

Besides, could you tell me whether you're able to fire up GoogleEarth in Metacity? I myself and others experience a system hang when doing so, whereas under Beryl almost everything looks OK. I say almost because there is some flickering and overlying problems anyway, only that I consider those to be minor annoyances given the great improvement that is to have it working.

---

### Post by Treviño on 2007-04-18
Radeon users with problems with google earth can improve their experience using this driconf config (put it into your ~/.driconf file):
```
<driconf>
    <device screen="0" driver="r300">
        <!-- here there could be some "Default" settings -->
        <application name="Google Earth" executable="googleearth-bin">
            <option name="disable_lowimpact_fallback" value="true" />
        </application>
    </device>
</driconf>
```

---

### Post by nubutu on 2007-04-19
Or they can install DRIconf to do this stuff in a nice graphical way and see what other options their drivers have available

[http://dri.freedesktop.org/wiki/DriConf](http://dri.freedesktop.org/wiki/DriConf)

---

### Post by Treviño on 2007-04-19
Sure, in fact I've generated that xml code using driconf...

However driconf is also on ubuntu repos ;)

---

### Post by Treviño on 2007-04-24
Since I've upgraded to feisty it's now harder for me maitain this repo, however it will work for edgy users...

BTW, it's not all ended... **Feisty** users will be happy to know that soon I'll open a repo with *mesa-6.5.3* (actually is a RC and available in git) and then if all goes in the right way, Ladies and Gentleman... Xorg 7.3! ^_^

So, stay tuned!! :)

---

### Post by Docter on 2007-04-24
You sir are a king among men.

---

### Post by D!mon on 2007-05-15
are there any feisty repos already avaliable?

---

### Post by scottDkoDer on 2007-07-06
I upgraded xorg on edgy and had beryl and googleearth running on same session, but it was very buggy.  Beryl was fine but googleearth was so graphically challenged with artifacts and such I had to revert. Barely recovered!  Ironically enough, I had to downgrade xorg from 7.2 to 7.1 to get xgl to work on feisty.  Interesting stuff though.

---

### Post by phaidros on 2007-07-21
> **Treviño said:**
> .

BTW, it's not all ended... **Feisty** users will be happy to know that soon I'll open a repo with *mesa-6.5.3* (actually is a RC and available in git) and then if all goes in the right way, Ladies and Gentleman... Xorg 7.3! ^_^



some news on this front? would be rockin :)

---


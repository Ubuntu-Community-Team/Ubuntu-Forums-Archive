---
title: "Script: ATI driver installer"
date: 2006-08-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Kilz on 2006-08-12
I have stoped developing this script, but tworkemon has writtewn one and made it avialable [on post 91 of this thread.]("http://www.ubuntuforums.org/showthread.php?t=235145&page=10") for the 8.28.8 drivers.


[B][COLOR="Red"]For some people the 8.27.10 script works fine. For some people this script doesn't. I have no idea why it works for some people but not others. I am leaving it up in case you want to try. But I can no longer support it. Use it at your own risk. 
[Please go here if you need help]("http://http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually") [/COLOR][/B]


This script only works with Dapper Drake.
Due to requests for help I created an installer for the ATI 8.27.10 propriteary drivers. 
You may want to [look at the Release notes]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.27.10.html") to see exactly [what cards are supported]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.27.10.html#179398") by this driver release. Installing this driver on a non supported card may stop the x server from starting.

**[COLOR="Red"]You need to make sure the [Universe and Multiverse are enabled]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories").[/COLOR]** **[COLOR="Red"]Before running the script.[/COLOR]**

[COLOR="Blue"][SIZE="5"]**Instructions**[/SIZE][/COLOR]
Download the script
[AMD64 version]("http://home.comcast.net/~ubuntu64user/ATI-8.27.10-install-amd64-3.tar.gz")
[i386 version]("http://home.comcast.net/~ubuntu64user/ATI-8.27.10-install-i386-5.tar.gz") - Do not use this script for ATI 200M, All In One cards, or IGP models.. I cant guarantee graphics will work afterwords. Use at your own risk.

Extract the .tar.gz to your Desktop by right clicking on the file and selecting Extract Here. Please leave the script in the ATI folder.
Open a terminal and type or copy/paste in these 2 commands
cd ~/Desktop/ATI
sudo ./ATI

The installer will create everything and install it. It will remove the ATI folder and reboot when done. To test the installation type in glxgears into a terminal. You should see 3 revolving gears.
[IMG]http://i9.photobucket.com/albums/a74/tghc/ubuntu/glxthumb.png[/IMG]

If the kernel is updated. You will need to open a terminal and paste in the next 3 commands and reboot. That or just run the script again.
```
sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx 
sudo depmod
```

---

### Post by cstudent on 2006-08-15
Three questions?

1. Will this do me any good with an old ATI All-in-Wonder?
2. Will it have to be redone when the kernel is updated?
3. Will it break if the kernel is updated?

---

### Post by Kilz on 2006-08-15
> **cstudent said:**
> Three questions?

1. Will this do me any good with an old ATI All-in-Wonder?
2. Will it have to be redone when the kernel is updated?
3. Will it break if the kernel is updated?

1. This script will always install the newest drivers as they are released. You may want to [look at the Release notes]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.27.10.html") to see exactly what cards are supported. There is a note on that page
" Note:ATI All-in-Wonder® variants based on the above are also supported. Video capture however is not supported." 
So if the card is supported it will work for what ATI has enabled.
2. Yes but that can be done by opening a terminal and typing in
```
sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx 
sudo depmod
```
Or rerunning the script.
3.  There is always the chance that something may not work after an upgrade. As we all know sometimes upgrades break things sometimes. From my experience most of the time its just acceleration may not work if the kernel is updated.

Thanks for the questions, it has pointed out one way to enhance the howto. I will be adding a link to the release notes so people can check if their card is supported.

---

### Post by lime4x4 on 2006-08-15
here is the error i'm getting when trying to run your script

/usr/bin/make  -f debian/rules clean
make[1]: Entering directory `/usr/src/modules/fglrx-kernel'
# select which makefile to use.
rm -f /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/Makefile || true
cd /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x ; \
	ln -s Makefile.kbuild Makefile ; \
	cd .. ; \

if [ -e patch-stamp ]; then \
	   dpatch deapply-all ; \
	   rm -rf patch-stamp debian/patched ; \
	fi   
if [ -f /usr/src/modules/fglrx-kernel/debian/control.template ]; then \
		cp  /usr/src/modules/fglrx-kernel/debian/control.template /usr/src/modules/fglrx-kernel/debian/control; \
	fi
dh_testroot
rm -f build-stamp configure-stamp
/usr/bin/make clean SYSSRC=/usr/src/linux -C /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x -f Makefile "KDIR=/usr/src/linux-headers-$i"
make[2]: Entering directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[2]: Leaving directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
echo "ROOT_CMD = "
ROOT_CMD = 
/usr/bin/make  -f debian/rules binary_modules
make[1]: Entering directory `/usr/src/modules/fglrx-kernel'
# select which makefile to use.
rm -f /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/Makefile || true
cd /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x ; \
	ln -s Makefile.kbuild Makefile ; \
	cd .. ; \

#nothing here anymore
touch configure-stamp
if [ -f /usr/src/modules/fglrx-kernel/debian/control.template ]; then \
		cp  /usr/src/modules/fglrx-kernel/debian/control.template /usr/src/modules/fglrx-kernel/debian/control; \
	fi
dh_testdir
dh_testroot
PATCHLEVEL = 6 
Kernel compiler version : 4.0.3
Detected compiler version : 4.0.3
Using compiler gcc-4.0 version 4.0.3
touch /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/gcc-check
touch /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/cc-sanity-check
## Main Make ##
IGNORE_CC_MISMATCH=1 CC="gcc-4.0"  /usr/bin/make -C /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x -f Makefile SYSSRC=/usr/src/linux  "KDIR=/usr/src/linux-headers-$i" KBUILD_PARAMS="-C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x"
make[2]: Entering directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[2]: Makefile: No such file or directory
make[2]: *** No rule to make target `Makefile'.  Stop.
make[2]: Leaving directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
make: *** [kdist_image] Error 2

---

### Post by Kilz on 2006-08-15
> **lime4x4 said:**
> here is the error i'm getting when trying to run your script


Please give me some more information. Are you running Ubuntu, Kubuntu, or Xubuntu? Also what version of Ubuntu are you running? Also please copy the entire terminal session from the begining into a text file and attach it.

---

### Post by SonicvanaJr on 2006-08-15
Hi. I'm running Ubuntu 64-bit version with a 2.6.15-26-amd64-generic kernel. I ran your script and everything seem to have completed fine. The machine rebooted, but when I open terminal and try to type in fglrx there is no such command. There is however fgl_glxgears, fglrxinfo, and fglrx_xgamma. I had a feeling fgl_glxgears may be my equivalent of your fglrx command. However when I run fgl_glxgears it quickly opens and closes and the following appears in terminal. 

Using GLX_SGIX_pbuffer
Floating point exception

---

### Post by Kilz on 2006-08-15
double post, see below

---

### Post by Kilz on 2006-08-15
> **SonicvanaJr said:**
> Hi. I'm running Ubuntu 64-bit version with a 2.6.15-26-amd64-generic kernel. I ran your script and everything seem to have completed fine. The machine rebooted, but when I open terminal and try to type in fglrx there is no such command. There is however fgl_glxgears, fglrxinfo, and fglrx_xgamma. I had a feeling fgl_glxgears may be my equivalent of your fglrx command. However when I run fgl_glxgears it quickly opens and closes and the following appears in terminal. 

Using GLX_SGIX_pbuffer
Floating point exception

Sorry typo in the howto, I just fixed it. Try glxgears or also try fgl_glxgears -fbo If you want to know why you have to use -fbo [take a look here.]("http://www2.ati.com/drivers/linux/linux_8.19.10.html#176759") This is an older release. It looks like ATI disabled something and made the -fbo required a few versions back.

---

### Post by ramasdf123 on 2006-08-15
will direct rendering work when I install this?  I am trying to get XGL. I have Radeon® Xpress 200M video chip in my laptop which is V2405US, FYI.

---

### Post by lime4x4 on 2006-08-15
running ubuntu dapper with all updates
also running the latest 686 kernel from ubuntu

---

### Post by Kilz on 2006-08-15
> **lime4x4 said:**
> running ubuntu dapper with all updates
also running the latest 686 kernel from ubuntu

Please run the script again, if you get an error, copy the entire terminal session and paste it into a text file. Then attach the file to a post here.

---

### Post by lime4x4 on 2006-08-15
I'd like to but every time i run the script it reboots my computer...
From what i can c it's having issues with the deb packagae it just downloaded

---

### Post by Kilz on 2006-08-15
> **lime4x4 said:**
> I'd like to but every time i run the script it reboots my computer...
From what i can c it's having issues with the deb packagae it just downloaded

If it rebooted your computer , it may have installed. From my First post
[quote=Kilz]The installer will create everything and install it. It will remove the ATI folder **and reboot when done.** To test the installation type in glxgears into a terminal. You should see 3 revolving gears.[/quote]
It dosnt download a .deb file. It downloads the ati-driver-installer from ATI. please open a terminal and type in glxgears to test it.

---

### Post by lime4x4 on 2006-08-15
nope but it broke my install of the older ati drivers

john@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

---

### Post by lime4x4 on 2006-08-15
here is the error

.ATI-installer.sh:156: syntax error:bad substitution removing temp directory:fglrx_8.27.10-1_i386deb  (--install)
dpkg: error processing xorg-driver-fglrx_8.27.10-1
cannot access archive

---

### Post by lime4x4 on 2006-08-15
here is a screen shot i hope it works[IMG][IMG]http://img293.imageshack.us/img293/2020/screenshot1sg4.png[/IMG][/IMG]

---

### Post by scxtt on 2006-08-15
Kilz,

not that it matters, but there's a few typos in your echo:
[indent]echo "your system will now reboot, if it [color=red]dose[/color] not [color=red]automaticly[/color] please reboot"[/indent]i'm sure you mean does and automatically ...

also, what's the significance of the -h in "sudo shutdown -h -r now"? shouldn't it just be **sudo shutdown -r now**?, since you're rebooting and not halting ...

---

### Post by lime4x4 on 2006-08-15
well that didn't work to well...
I uploaded a snapshot of my desktop to my personal web space

[http://lime4x4.pointclark.net:8888/cpg148/displayimage.php?album=random&cat=10001&pos=-11](http://lime4x4.pointclark.net:8888/cpg148/displayimage.php?album=random&cat=10001&pos=-11)

---

### Post by kelboy on 2006-08-15
I ran your script and when i rebooted, When it came to the session logon screen..my screen went black (as in the signal was lost)...absolutly no signal out of the vid card...
I had to reconfigure xserver-xorg to get my display back...and login etc...
my hardware:
386 build
UBUNTU 6.06 (fresh install 3 days old)
radeon 9000 pro AIW

---

### Post by Kilz on 2006-08-16
> **ramasdf123 said:**
> will direct rendering work when I install this?  I am trying to get XGL. I have Radeon® Xpress 200M video chip in my laptop which is V2405US, FYI.

There are problems with the 200m, ATI admits it, so I'm not sure. You can try but I don't guarantee anything.

---

### Post by Kilz on 2006-08-16
> **lime4x4 said:**
> well that didn't work to well...
I uploaded a snapshot of my desktop to my personal web space

[http://lime4x4.pointclark.net:8888/cpg148/displayimage.php?album=random&cat=10001&pos=-11](http://lime4x4.pointclark.net:8888/cpg148/displayimage.php?album=random&cat=10001&pos=-11)

The [latest script]("http://home.comcast.net/~ubuntu64user/ATI-8.27.10-install-i386-3.tar.gz"), version 3, should work for you.

[quote=scxtt]  	Kilz,

not that it matters, but there's a few typos in your echo:

    echo "your system will now reboot, if it dose not automaticly please reboot"

i'm sure you mean does and automatically ...

also, what's the significance of the -h in "sudo shutdown -h -r now"? shouldn't it just be sudo shutdown -r now?, since you're rebooting and not halting ...[/quote]
Thanks, I fixed the typo's for version 3.

---

### Post by lime4x4 on 2006-08-16
the script ran without errors but when the computer rebooted i was greeted with a black screen.. Had to reboot into recovery mode and change the driver from fglrx to ati...
Any ideas?

---

### Post by Kilz on 2006-08-16
> **lime4x4 said:**
> the script ran without errors but when the computer rebooted i was greeted with a black screen.. Had to reboot into recovery mode and change the driver from fglrx to ati...
Any ideas?

What version of Ubuntu are you running, the fix that was put in and the error you had were issues with Edgy.

---

### Post by Kilz on 2006-08-18
Version 5 or the i386 script has been released. Do not use this script for Edgy installs, 200M or All In One cards. The script could leave you without graphics. Use at your own risk.

If anyone installs the script on i386 Ubuntu please tell me of your experences. I would like to know if the script works or not for you.

---

### Post by marcus12 on 2006-08-18
thanks! script v5 worked fine on xubuntu with a radeon 9200

---

### Post by evil_elman on 2006-08-18
What happens if I already have an ATi driver installed? Will it simply overwrite it, remove it first and the install or something between?

---

### Post by Kilz on 2006-08-18
> **evil_elman said:**
> What happens if I already have an ATi driver installed? Will it simply overwrite it, remove it first and the install or something between?

The script removes the old driver firest because there can be problems overwriting. Then it installs the new one.

---

### Post by evil_elman on 2006-08-18
Works flawlessly!

Good work, mate!

EDIT: Just saw that ATi released the 8.28.8 driver... Could we hope for support on this driver anytime soon in the script? :-)

---

### Post by Kilz on 2006-08-18
> **evil_elman said:**
> Works flawlessly!

Good work, mate!

EDIT: Just saw that ATi released the 8.28.8 driver... Could we hope for support on this driver anytime soon in the script? :-)

Im going to do some testing, but it wont be long if I dont run into anything to bad.

---

### Post by jinx099 on 2006-08-19
neither script 1, nor script 5 worked with my laptop's radeon 9000 IGP :(

---

### Post by AKA248 on 2006-08-19
GREAT! I works !!!

THANK YOU VERY MUCH !!!

100 :KS 

:-)

cya, AKA248

---

### Post by Dropknee on 2006-08-19
Pls make the script for the latest ATI driver 8.28.8

---

### Post by Kilz on 2006-08-19
> **Dropknee said:**
> Pls make the script for the latest ATI driver 8.28.8

I have come across a huge problem installing the 8.28.8 drivers. Acceleration is no longet working on my system. I will have to figure out how to solve that before making any scripts for that driver.

---

### Post by mjpatey on 2006-08-20
I haven't installed the script yet, but am trying to decide whether I need to.

When I run glxgears, I already get the gears animation, but graphics on my system are a little sluggish.  Windows XP's graphics are running significantly faster than Ubuntu's at this point.

To give a direct comparison, I use Picasa (photo management / editing software) in both OSes.  In XP, slideshow dissolves are silky-smooth, and manually arrowing back and forth from one pic to the next is almost instantaneous.  In Ubuntu, slideshows are very choppy, and shuttling manually is slow as molasses.

Screen savers also bog down quite a bit in Ubuntu for me.

Will your script speed these things up in my case?

I'm running Ubuntu with Gnome desktop, using an ATI Radeon 9200, 3.2GHz Pentium IV, 1.5GB RAM, 7200 RPM HD.

Thanks for any help you may have!

-Mark

---

### Post by mjpatey on 2006-08-20
Well, I guess I got impatient :rolleyes:   I'm thinking I should have waited for a response to my previous post before installing, but I went ahead and did it anyway.

I installed the latest version of the script (#5)... My video card is the ATI 9200 (RV280 5961).

Right now, my results are a mixed bag.  My experience in Picasa's slideshow feature seems about the same as before-- for some reason the images refuse to display in full resolution even though I've set it to do so in Options.

However, Google Earth runs great!!!

But-- my screen savers are running at a snail's pace now.  Lava Lite runs at about 3 frames per second... "Skyrocket" barely moves at about 1 frame every 2 seconds... and "GLBlur" displays only 1 frame every 8 seconds.  All these ran acceptably fast before the script, though not nearly as fast as I wanted.

Do you have any pointers for me?  I'm open to any tweaks you may suggest.

Thanks!

-Mark

---

### Post by scxtt on 2006-08-20
what's your output for fglrxinfo?

---

### Post by mjpatey on 2006-08-20
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.27.6)

-Mark

---

### Post by scxtt on 2006-08-20
that looks good, but doesn't explain the SS problem ... very odd, and i had the opposite result {great FPS on the SS, but i don't use them} ...

---

### Post by mjpatey on 2006-08-20
I did install Automatix some time ago... any chance something is conflicting?

---

### Post by scxtt on 2006-08-20
couldn't tell you, i don't use automatix (and won't), don't even use a script to install fglrx {tho perusing Kilz's script, it looks like his script does basically what i do :p} ...

---

### Post by Dropknee on 2006-08-20
> **Kilz said:**
> I have come across a huge problem installing the 8.28.8 drivers. Acceleration is no longet working on my system. I will have to figure out how to solve that before making any scripts for that driver.

I got the exact same problem, I open a thread [here]("http://www.ubuntuforums.org/showthread.php?t=239229") about this but no solucion yet :( sorry

---

### Post by Kilz on 2006-08-20
Sometimes the newest driver is nothing but a headache. Im kicking myself for not doing a partmage backup before installing it. Becuse reverting to the previous driver doesnt work. I did have a 1 month old backup, but it was corupted.

---

### Post by mjpatey on 2006-08-20
Kilz,

I was wondering if you could give my issue a quick read, beginning with the fourth post on Page 4 of this thread (my final post is the last one on the page).

I can't figure out why some things (Google Earth) are running smoothly, while others (Picasa and screen savers) are either slow as molasses or don't work at all.  They all worked *OK* before the script, and I was hoping to improve on that, but while Google Earth has improved, the rest has become much worse.

Thanks in advance for any suggestions you may have!  I guess I'd be open to the suggestion of "just revert to the old configuration" if it's my only option, and if you could tell me how.  Is it just a matter of changing from fglrx to ati in xorg.conf?

Thanks,

-Mark

---

### Post by Dropknee on 2006-08-20
> **Kilz said:**
> Sometimes the newest driver is nothing but a headache. Im kicking myself for not doing a partmage backup before installing it. Becuse reverting to the previous driver doesnt work. I did have a 1 month old backup, but it was corupted.

Installing the previous driver dont work :(....... Oh well.... :( Im going to.....c...r..y......:(   lol.... I lost my Compiz, XGL until someone find a solution and .... my games too... :(

---

### Post by Kilz on 2006-08-20
> **scxtt said:**
> couldn't tell you, i don't use automatix (and won't), don't even use a script to install fglrx {tho perusing Kilz's script, it looks like his script does basically what i do :p} ...

Ya, the script basicly dose what I do myself. I wrote it to save myself typing in things. I made it available to avoid errors. Being human errors happen. But the longer I look at it the more I believe there are some real problems with ATI on Ubuntu.

---

### Post by Kilz on 2006-08-20
> **mjpatey said:**
> Kilz,

I was wondering if you could give my issue a quick read, beginning with the fourth post on Page 4 of this thread (my final post is the last one on the page).

I can't figure out why some things (Google Earth) are running smoothly, while others (Picasa and screen savers) are either slow as molasses or don't work at all.  They all worked *OK* before the script, and I was hoping to improve on that, but while Google Earth has improved, the rest has become much worse.

Thanks in advance for any suggestions you may have!  I guess I'd be open to the suggestion of "just revert to the old configuration" if it's my only option, and if you could tell me how.  Is it just a matter of changing from fglrx to ati in xorg.conf?

Thanks,

-Mark

Open a terminal and type in ```
glxgears -printfps
``` Then paste the results in a reply.

---

### Post by scxtt on 2006-08-20
> **Kilz said:**
> Ya, the script basicly dose what I do myself. I wrote it to save myself typing in things. I made it available to avoid errors. Being human errors happen. But the longer I look at it the more I believe there are some real problems with ATI on Ubuntu.i meant that more as a compliment [convoluted as i wrote it :p] - good work man, it's a great idea - i was thinking about doing it myself, but i've been lazy about it ...

---

### Post by mjpatey on 2006-08-20
Thanks, Kilz... here's what I got:

glxgears -printfps
8555 frames in 5.0 seconds = 1710.975 FPS
8095 frames in 5.0 seconds = 1618.920 FPS
8623 frames in 5.0 seconds = 1724.462 FPS
8621 frames in 5.0 seconds = 1723.732 FPS
8630 frames in 5.0 seconds = 1725.906 FPS
8625 frames in 5.0 seconds = 1724.856 FPS
7563 frames in 5.1 seconds = 1496.043 FPS
7642 frames in 5.0 seconds = 1528.328 FPS
8625 frames in 5.0 seconds = 1724.184 FPS
8619 frames in 5.0 seconds = 1723.416 FPS
8618 frames in 5.0 seconds = 1723.554 FPS
7885 frames in 5.0 seconds = 1576.865 FPS
8571 frames in 5.0 seconds = 1712.053 FPS
8580 frames in 5.0 seconds = 1715.948 FPS
8583 frames in 5.0 seconds = 1716.497 FPS
8583 frames in 5.0 seconds = 1716.525 FPS
8584 frames in 5.0 seconds = 1716.651 FPS
8575 frames in 5.0 seconds = 1714.983 FPS
8581 frames in 5.0 seconds = 1716.069 FPS
7542 frames in 5.0 seconds = 1508.197 FPS
8585 frames in 5.0 seconds = 1716.872 FPS
8579 frames in 5.0 seconds = 1715.752 FPS
8567 frames in 5.0 seconds = 1713.309 FPS
8477 frames in 5.0 seconds = 1695.385 FPS
7779 frames in 5.0 seconds = 1555.640 FPS

I assume it would have gone on indefinitely every 5 seconds.  The gears look fine, it's just the screen savers.  I know it sounds stupid to even care about the screen savers (I never used them in Windows), but I like showing Ubuntu off to family and friends, and the screen savers are a good graphical showcase.

Is there a way to get FPS from the screen savers?

---

### Post by lime4x4 on 2006-08-20
kilz sorry for the delay i was out of town for awhile...
I'm running the latest dapper version of ubuntu but i'm using the 686 kernel from the repository

---

### Post by mjpatey on 2006-08-20
Regarding the issue I've been having with acceleration working, but not on the screen savers...

I found [THIS LINK]("http://www.ubuntuforums.org/showthread.php?t=216154"), which explains that several of the Gnome screen savers aren't accelerated.  The solution is using "xscreensaver" which can be downloaded in Synaptic.

I installed xscreensaver (and 3 other files that contained xscreensaver extras), used the command: ```
xscreensaver-command -prefs
``` to bring up the control panel, then

```
xscreensaver-command -activate
``` to manually activate it.

I added custom app launchers to the panel for each of these, and it has effectively replaced the default Gnome screensaver for me.  It even has several of the original screensavers from Gnome built-in, but with 2 bonuses:  the ones that require acceleration are accelerated, and you can tweak them all individually.

By the way, there are LOTS of screensavers in the package.

I hope this helps someone like it did me!

---

### Post by Kilz on 2006-08-20
> **mjpatey said:**
> Thanks, Kilz... here's what I got:

glxgears -printfps
8555 frames in 5.0 seconds = 1710.975 FPS
8095 frames in 5.0 seconds = 1618.920 FPS
8623 frames in 5.0 seconds = 1724.462 FPS
8621 frames in 5.0 seconds = 1723.732 FPS


I assume it would have gone on indefinitely every 5 seconds. The gears look fine, it's just the screen savers. I know it sounds stupid to even care about the screen savers (I never used them in Windows), but I like showing Ubuntu off to family and friends, and the screen savers are a good graphical showcase.

Is there a way to get FPS from the screen savers?
Reply With Quote

I took a look at your postting and it looks like you have acceleration working. I'm not sure why the screen savers are not fast, they should work ok with those fraims per second.

---

### Post by pollock.tar.gz on 2006-08-20
GREAT tool. this solved all of my 3D acceleration problems for my ATi 9550 after hours of trying other things. thanks a lot for the script.

---

### Post by mjpatey on 2006-08-20
Kilz,

Yeah, after the script, for some reason glxgears still gives a nice framerate, but most of the Gnome screensavers bog way down to 1 or 2 FPS.

I normally wouldn't care about screen savers, it's just that their performance might be indicative of a larger problem... and I just want it to work because it should work.

Thank you for the script!!!  It certainly straightened out pretty much everything else (except for Picasa's slideshow!?), and with xscreensaver added into the mix, it's the best my system has run yet.

Now on to Wine and 3D gaming...  :-)

---

### Post by lime4x4 on 2006-08-21
Well my problem appears to be the newer driver doesn't work on my system..I even tried manually installing it with no luck.. I ended up going back to the 8.26.18 drivers..Atleast now i have the ati drivers installed again

---

### Post by eightballrj on 2006-08-23
First,
Thanks a bunch for your work at easing the 64 bit transition! But, I tried to use the script on a fresh install and upgrade of dapper 64. With the repositories enabled as directed I get a non-gui screen with hundred and thousands of iterations of something like "Timing while atomic". I didn't know if this was some function of your script but I let it run while I was asleep and it had gotten up to 14000 something with probably 100 iterations between each noted number change... needless to say it ran for a while. Any clues before I blast and reinstall??

Thanks,
Richard

---

### Post by Kilz on 2006-08-23
> **eightballrj said:**
> First,
Thanks a bunch for your work at easing the 64 bit transition! But, I tried to use the script on a fresh install and upgrade of dapper 64. With the repositories enabled as directed I get a non-gui screen with hundred and thousands of iterations of something like "Timing while atomic". I didn't know if this was some function of your script but I let it run while I was asleep and it had gotten up to 14000 something with probably 100 iterations between each noted number change... needless to say it ran for a while. Any clues before I blast and reinstall??

Thanks,
Richard
Not a clue. But be aware there are problems with the xserver update. You may want to uncheck that box if you update after the reinstall

---

### Post by eightballrj on 2006-08-23
Ok thanks I will try that and see how it works!

---

### Post by MilesTEG1 on 2006-08-24
Hello,
I have installed successfully on Dapper Ubuntu, with i686 kernel.
My video card is an ATI Technologies Inc RV350 [Mobility Radeon 9600 M10], on a laptop PackardBell EasyNote R7320 with Intel Celeron M 1,3 GHz.

Here you have the FPS I have with this card :
```
pierrick@TERMINUS:~$ glxgears -printfps
627 frames in 5.0 seconds = 125.307 FPS
626 frames in 5.0 seconds = 125.192 FPS
625 frames in 5.0 seconds = 124.991 FPS
625 frames in 5.0 seconds = 124.993 FPS
625 frames in 5.0 seconds = 124.992 FPS
625 frames in 5.0 seconds = 124.991 FPS
625 frames in 5.0 seconds = 124.994 FPS

``` 
Why FPS are so bad ??
The wheels run good, but FPS aren't so good.

Another question : does the last driver from ATI will work ?
[ATI Proprietary Linux x86 Display Drivers for XFREE86 / X. Org  Version 8.28.8]("https://support.ati.com/ics/support/KBAnswer.asp?questionID=1176")

Thanks
Miles

---

### Post by Kilz on 2006-08-24
> **MilesTEG1 said:**
> Hello,
I have installed successfully on Dapper Ubuntu, with i686 kernel.
My video card is an ATI Technologies Inc RV350 [Mobility Radeon 9600 M10], on a laptop PackardBell EasyNote R7320 with Intel Celeron M 1,3 GHz.

Here you have the FPS I have with this card :
```
pierrick@TERMINUS:~$ glxgears -printfps
627 frames in 5.0 seconds = 125.307 FPS
626 frames in 5.0 seconds = 125.192 FPS
625 frames in 5.0 seconds = 124.991 FPS
625 frames in 5.0 seconds = 124.993 FPS
625 frames in 5.0 seconds = 124.992 FPS
625 frames in 5.0 seconds = 124.991 FPS
625 frames in 5.0 seconds = 124.994 FPS

``` 
Why FPS are so bad ??
The wheels run good, but FPS aren't so good.

Another question : does the last driver from ATI will work ?
[ATI Proprietary Linux x86 Display Drivers for XFREE86 / X. Org  Version 8.28.8]("https://support.ati.com/ics/support/KBAnswer.asp?questionID=1176")

Thanks
Miles

I noticed this problem myself when I installed the 8.28.8 drivers and they were slow. I ended up having to do a complete reinstall because nothing could fix it I thought. When I tried to install the 8.27.10 drivers after the reinstall they were also slow like this. 
I had to go back to the [8.26.18 drivers]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.26.18-x86_64.run") to get a decient fps and cedega to work. In seriously concidering making an install script for it. The only problem with them is that screen savers run slow. Something I can live with.

---

### Post by theratster on 2006-08-24
Hey, I tried your script on my laptop (V.5 I believe) running Ubuntu 6.06 with an ATI Mobility Radion 9000. It seemed to install fine, rebooted, but the glxgears are running very very slowly. I ran fglrxinfo and I'm not sure if its using the drivers correctly:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Help plz? :)

---

### Post by tomski on 2006-08-24
Thanks for the script, it works for me, so far no problems!!
& i dont really use screensavers i just turn off the monitor when i walk away, so im not bothered if they are slow but i hope to play some 3d games, so i am hoping they will perform ok.

I had tried to install my own this way before as seperate commands...obviously i had done it wrong!!

one problem out of the way thanks Kilz

---

### Post by helmut0 on 2006-08-24
Hi the script worked great for me and I got the gears to work,but now when I run a mpeg or avi with one of my players my desktop reboots and I have to sign in again.I have a ms1039 with a mt40 and ati x1600 running the latest dapper..Thank you in advance...I can not see the error,it's too fast..

---

### Post by nbx909 on 2006-08-24
how do i uninstall this?

---

### Post by Kilz on 2006-08-24
> **nbx909 said:**
> how do i uninstall this?

The answer depends on what you had before.

---

### Post by blay on 2006-08-24
Install seems to have worked fine here as well, but I too get :

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Ubuntu 6.06
Radeon Mobility 9100

Any help would be appreciated.

---

### Post by Kilz on 2006-08-25
> **blay said:**
> Install seems to have worked fine here as well, but I too get :

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Ubuntu 6.06
Radeon Mobility 9100

Any help would be appreciated.

It didnt install. Did you enable the multiverse and universe repositories?

---

### Post by blay on 2006-08-25
Yes, using the "guide" posted in your 1st post.
[http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

I did notice one thing though. In the guide for Synaptic, the "Channel" shows as Ubuntu 6.06 'Dapper Drake'. Mine shows as Ubuntu 6.06 LTS. Not sure if this has anything to do w/ it, but thought it may be worth mentioning. thanks again for the help.

---

### Post by Kilz on 2006-08-25
> **blay said:**
> Yes, using the "guide" posted in your 1st post.
[http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

I did notice one thing though. In the guide for Synaptic, the "Channel" shows as Ubuntu 6.06 'Dapper Drake'. Mine shows as Ubuntu 6.06 LTS. Not sure if this has anything to do w/ it, but thought it may be worth mentioning. thanks again for the help.

Your right , that doesnt matter. Ok, type in 
```
gksudo gedit /etc/X11/xorg.conf
```

When it opens look for a section that looks like this

```
Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection
```

It may have a diffrent Identifier

Dise the driver say "fglrx" in yours?

---

### Post by blay on 2006-08-25
Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

---

### Post by theratster on 2006-08-25
I am having the same problem as blay (I posted @ the end of pg 6), and so far my stuff is matching with him:

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

I also have all repositories active

---

### Post by blay on 2006-08-25
I was doing a little reading [here]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Troubleshooting_for_Method_1") and was wondering if this might have anything to do w/ this.

Unfortunately OpenGL seems to be broken for R200 cards (everything below Radeon 9500) in this driver version. This may be fixed by replacing /usr/lib/libGL.so.1.2 with libGL.so.1.2 from the previous driver version (8.24.8). To do so download this file: libGL.so.1.2 and then copy it to the /usr/lib/ directory.

It would seem I have one of these cards. This is taken from xorg.conf fresh install:```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
```

Mainly note the R200. So am I basically "screwed"?

---

### Post by kvonb on 2006-08-26
==========================================================================
EDIT:

PLEASE DISREGARD THIS POST! IT WAS MEANT FOR KILZ ONLY. MY APOLOGIES.

Kilz, if you would like a copy of my script, which includes stuff to setup the old libgl.so.1.2 file, pm me and I will send it to you for testing and updating.

==========================================================================

I wrote my ATI installation script a few months ago (nobody seemed interested though!), it solves the MESA problems.  You are welcome to incorporate it into your script if you like.

I wrote it with an UNDO or RECOVERY function in mind but didn't finish it.

I would like to suggest a few things though:

1) warn the user at the beginning of the script (before doing anything) about the possible consequences and especially about the reboot, and give the option to quit.

2) maybe make the MESA solution an option after installing the drivers as ATI might fix this in a future driver release, making it redundant and a possible problem.

Regards,

Kev :)

---

### Post by Spready on 2006-08-26
Thanks - 
I am new to Linux and used the original script on page to download and install the drivers for my Saphire ATI Radeon 9550.
It worked a treat and I can now use my widescreen to its full potential.

Nice one!

---

### Post by smashkins on 2006-08-26
My videocard ATI Radeon 9550SE works fine but xgl don't started ... :(

---

### Post by theratster on 2006-08-26
kvonb, I tried your script, but alas after I followed through (no errors as far as I could see) and a reboot, it still gives the MESA GL stuff for fglrxinfo.

---

### Post by blay on 2006-08-26
> **theratster said:**
> kvonb, I tried your script, but alas after I followed through (no errors as far as I could see) and a reboot, it still gives the MESA GL stuff for fglrxinfo.

Same here. ](*,)

---

### Post by djcuuna on 2006-08-26
hello i installed the drivers fine no probs but when it rebooted everything seemed ok but when i started mozilla and loaded a web page and scrolled up and down the picture started going all choppy and break up my cards a radeon 1600 so i put the vesa display back on any ideas what it was and is there a fix for it thank you for any help

---

### Post by kvonb on 2006-08-27
Erm....sorry, maybe I didn't make myself clear, the script was for KILZ to see if there was anything in it that he could use, I didn't mean for everyone to try it!

My script installs the official Ubuntu drivers, NOT the ATI drivers, however it works on 3 of my machines with ATI 9200se cards, it might be because my script doesn't try to remove any ATI driver, just installs the Ubuntu driver over the top.

To undo the changes my script made, (IF YOU DIDN'T REMOVE ati-install FOLDER!) do the following:

cd ~/ati-install
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.notworking
sudo cp ./xorg.conf.before-script /etc/X11/xorg.conf
sudo cp /etc/apt/sources.list /etc/apt/sources.list.modified
sudo cp ./sources.list.before-script /etc/apt/sources.list

The links to lib.gl.so.1.2 should be fine, you can safely leave them as they are.

Now use KILZ's script to download and install the official ATI drivers.

I do apologise, I didn't mean to hijack this thread or push my script on anyone.

ALWAYS read through any script before running it, it could do some nasty things to your system!

Regards,  Kev

---

### Post by Kilz on 2006-08-27
> **kvonb said:**
> Erm....sorry, maybe I didn't make myself clear, the script was for KILZ to see if there was anything in it that he could use, I didn't mean for everyone to try it!

My script installs the official Ubuntu drivers, NOT the ATI drivers, however it works on 3 of my machines with ATI 9200se cards, it might be because my script doesn't try to remove any ATI driver, just installs the Ubuntu driver over the top.

To undo the changes my script made, (IF YOU DIDN'T REMOVE ati-install FOLDER!) do the following:

cd ~/ati-install
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.notworking
sudo cp ./xorg.conf.before-script /etc/X11/xorg.conf
sudo cp /etc/apt/sources.list /etc/apt/sources.list.modified
sudo cp ./sources.list.before-script /etc/apt/sources.list

The links to lib.gl.so.1.2 should be fine, you can safely leave them as they are.

Now use KILZ's script to download and install the official ATI drivers.

I do apologise, I didn't mean to hijack this thread or push my script on anyone.

ALWAYS read through any script before running it, it could do some nasty things to your system!

Regards,  Kev

I have been doing a lot and really havent had time for this thread. Im going to try and look at the script you posted and see if there is anything that can be incorperated. But the high failure rate my script has isnt improving. Im wondering if its possible to make a script to do this sucessfully.

---

### Post by jcscar on 2006-08-27
Thanks!! You have made installing the ATI card so easy witht his script.  THANK YOU THANK YOU THANK YOU

---

### Post by sidechem on 2006-08-28
Hi, I could use help from anyone who's seen anything like this before, or can understand some of my problems....
I've been trying to install the ATI proprietary driver for some time to no avail using many differnt methods on a fresh 64bit install of Ubuntu dapper.

Short description of my system.
AMD 64bit 3500+
MSI radeon 9800pro graphics card

I've just did a fresh install of dapper 2min ago, DLd the linux headers, the ATI driver 8.27.10 and used the ATI driver wiki.

here are my errors... and these are persistent no matter what I try, driver 8.28.8 or using kilz script...
(it looks like I'm getting a DRI error... but I don't know why)

fglrxinfo
```
Error: couldn't find RGB GLX visual!
```

glxgears
```
Error: couldn't get an RGB, Double-buffered visual
```

cat /var/log/Xorg.0.log | grep -i fglrx
```
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(II) fglrx(0): pEnt->device->identifier=0x6cfc00
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 9800 PRO (R350 4E48)" (Chipset = 0x4e48)
(--) fglrx(0): (PciSubVendor = 0x1462, PciSubDevice = 0x9562)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe8000000
(--) fglrx(0): MMIO registers at 0xfbe00000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI R360
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: R360
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: VSC  Model: 4c4a  Serial#: 39179
(II) fglrx(0): Year: 1998  Week: 6
(II) fglrx(0): EDID Version: 1.0
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate  Composite  SyncOnGreenSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) fglrx(0): Gamma: 2.38
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): redX: 0.635 redY: 0.333   greenX: 0.280 greenY: 0.595
(II) fglrx(0): blueX: 0.152 blueY: 0.063   whiteX: 0.283 whiteY: 0.298
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 720x400@88Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@87Hz (interlaced)
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 70  vid: 19041
(II) fglrx(0): #3: hsize: 832  vsize 624  refresh: 75  vid: 20297
(II) fglrx(0): #4: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #5: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #6: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) fglrx(0): #7: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  286 x 229 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 80.0 MHz   Image Size:  300 x 225 mm
(II) fglrx(0): h_active: 1024  h_sync: 1056  h_sync_end 1152 h_blank_end 1328 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 774 v_blanking: 804 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 78.8 MHz   Image Size:  300 x 225 mm
(II) fglrx(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 75.0 MHz   Image Size:  300 x 225 mm
(II) fglrx(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1328 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled
(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 32 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.68  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.29  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 80.0 MHz (scaled from 0.0 MHz), 60.2 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   80.00  1024 1056 1152 1328  768 771 774 804 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.61  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.68  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.29  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 80.0 MHz (scaled from 0.0 MHz), 60.2 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   80.00  1024 1056 1152 1328  768 771 774 804 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.61  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (320, 240) mm
(--) fglrx(0): DPI set to (101, 108)
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): cpuSpeedMHz: 0x00000906
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xe8701000 (size=0x078ff000)
(II) fglrx(0): UMM area:     0xe8701000 (size=0x078ff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe8000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(II) Loading extension FGLRXEXTENSION

```

My xorg.conf is here
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
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
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection
```

Any help from anyone would be much appreciated...
I've been trying to get this working for over 3 weeks.
Thanx!

---

### Post by Kilz on 2006-08-29
> **sidechem said:**
> Hi, I could use help from anyone who's seen anything like this before, or can understand some of my problems....
I've been trying to install the ATI proprietary driver for some time to no avail using many differnt methods on a fresh 64bit install of Ubuntu dapper.

Short description of my system.
AMD 64bit 3500+
MSI radeon 9800pro graphics card

I've just did a fresh install of dapper 2min ago, DLd the linux headers, the ATI driver 8.27.10 and used the ATI driver wiki.

here are my errors... and these are persistent no matter what I try, driver 8.28.8 or using kilz script...
(it looks like I'm getting a DRI error... but I don't know why)

fglrxinfo
```
Error: couldn't find RGB GLX visual!
```

glxgears
```
Error: couldn't get an RGB, Double-buffered visual
```

cat /var/log/Xorg.0.log | grep -i fglrx
```
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(II) fglrx(0): pEnt->device->identifier=0x6cfc00
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 9800 PRO (R350 4E48)" (Chipset = 0x4e48)
(--) fglrx(0): (PciSubVendor = 0x1462, PciSubDevice = 0x9562)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe8000000
(--) fglrx(0): MMIO registers at 0xfbe00000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI R360
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: R360
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: VSC  Model: 4c4a  Serial#: 39179
(II) fglrx(0): Year: 1998  Week: 6
(II) fglrx(0): EDID Version: 1.0
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate  Composite  SyncOnGreenSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) fglrx(0): Gamma: 2.38
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): redX: 0.635 redY: 0.333   greenX: 0.280 greenY: 0.595
(II) fglrx(0): blueX: 0.152 blueY: 0.063   whiteX: 0.283 whiteY: 0.298
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 720x400@88Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@87Hz (interlaced)
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 70  vid: 19041
(II) fglrx(0): #3: hsize: 832  vsize 624  refresh: 75  vid: 20297
(II) fglrx(0): #4: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #5: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #6: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) fglrx(0): #7: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  286 x 229 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 80.0 MHz   Image Size:  300 x 225 mm
(II) fglrx(0): h_active: 1024  h_sync: 1056  h_sync_end 1152 h_blank_end 1328 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 774 v_blanking: 804 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 78.8 MHz   Image Size:  300 x 225 mm
(II) fglrx(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 75.0 MHz   Image Size:  300 x 225 mm
(II) fglrx(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1328 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled
(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 32 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.68  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.29  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 80.0 MHz (scaled from 0.0 MHz), 60.2 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   80.00  1024 1056 1152 1328  768 771 774 804 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.61  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.68  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.29  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 80.0 MHz (scaled from 0.0 MHz), 60.2 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   80.00  1024 1056 1152 1328  768 771 774 804 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.61  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (320, 240) mm
(--) fglrx(0): DPI set to (101, 108)
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): cpuSpeedMHz: 0x00000906
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xe8701000 (size=0x078ff000)
(II) fglrx(0): UMM area:     0xe8701000 (size=0x078ff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe8000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(II) Loading extension FGLRXEXTENSION

```

My xorg.conf is here
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
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
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection
```

Any help from anyone would be much appreciated...
I've been trying to get this working for over 3 weeks.
Thanx!


I have had a few people have trouble with the 8.27.10 and up drivers. Try the 8.26.18 [x86]("https://support.ati.com/ics/support/KBList.asp?folderID=619")  or [x86_64 ]("https://support.ati.com/ics/support/KBList.asp?folderID=1017")drivers and see if they work, it worked for 2 other people.

---

### Post by kvonb on 2006-08-30
sidechem:

a few questions:

1) is your video card built onto the mainboard (ie not a seperate card)?

   * if so, check the ATI website for a different driver

2) are you using Ubuntu 386 or Ubuntu 64?

   * if it is 64, check the ATI website for a different driver

3) did you enable "universe" and "multiverse" in /etc/apt/sources.list?

   * if not, then do: sudo gedit /etc/apt/sources.list
   * read through that file, there is a message about how to do it

4) is your AGP aperture size set to at least 128 megs in the BIOS?

   * if not, then change it

Hope this helps, regards, Kev :)

---

### Post by bartman on 2006-08-30
Kilz: Thank you very much for this wonderfull script! I'm using a laptop and I was afraid the fglrx drivers would break my hibernation as they did on my previous laptop but this works perfectly!

I can now play 3D games, video playback is smooth in fullscreen... excellent!

I only have one question: When running glxgears my CPU usage ramps up to 100%. Do you also notice this?

---

### Post by sjust on 2006-08-30
HI I used your script. Everything went fine, but when I check flgrxinfo it said that I still had
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5879 (8.26.18)
It did not update the drivers to 8.27 I have tried to install the 8.28 drivers myself but I get a syntax error and the install just quits. I can live with 8.26, they work just fine xgl and compize work great. I just wanted to let you know what happened.

---

### Post by HellTriX on 2006-08-31
I've run this script on my Ubuntu dapper install with 64 bit verson, I have a AMD 3800+ with Radeon X800 pro 256mb.
When I run glxgears -printfps i think was the command, I was only getting 150 fps for each one.

Running World of Warcraft in wine with graphics settings turned all the way down, I was getting 5-19 fps. Which is low, my friend just installed it but he uses an X700 slower video card and is averaging over 30.

using this forum I did all the checks to make sure opengl was enabled an all that stuff, but its still just slow.

Im kinda lost for what to do, people are talking about installing the older drivers, but there are so many steps and I have read so many different ways to do it that I'm just to confused as to what todo. I just basicly started learning linux this week, and the install I did was custom setup with raid since it wouldn't take my inital partitions. So I learning pretty quickly, but can anyone point me to a good howto that I can follow to install older drivers and maybe tell me what I need to do to downgrade to them incase the howto doesn't tell me that?

TY

---

### Post by VCSkier on 2006-08-31
no luck for me.  i'm running xubuntu 6.06.1 on an ati radeon mobility (9000, i think) card in a 2-3 year old IBM Thinkpad T41 laptop (i386).  i tried the script, and x wouldn't start.  so i replaced my xorg.conf with xorg.conf.original-0, and its running again.  i've tried several time to get the proper drivers running with several different methods, and never had any luck; everytime x has gotten broken.  any suggestions?  how can i troubleshoot this...  i'm still a noob.:oops:

---

### Post by herrdoktor330 on 2006-08-31
Kilz,

I'm having a problem installing this driver that I don't understand. To explain what I've done to this point:

1) I did a custom compile of the 2.6.17.7 kernel.
2) I have a radeon 9800 pro

When I try running the command "sudo module-assistant build,install fglrx" it stops at "Building fglrx-kernel-source, step 1". It stops with the error " ile.cpu:132 warning: overriding commands for target 'archclean' " and never finishes the install.

What did I do wrong?

---

### Post by quickwitt on 2006-09-03
Worked like a charm!

eMachines M6805

---

### Post by kingofsnakes2111 on 2006-09-06
I've just solved the screen saver problem.
There is something wrong with the path of Xscrensaver not looking for dri in the right place (/usr/lib/dri/fglrx_dri), instead Xscreensaver looks in /usr/X11R6/lib/modules/dri which is non-existent.

The way to solve:

sudo mkdir /usr/X11R6/lib/modules
sudo ln -s /usr/lib/dri /usr/X11R6/lib/modules/dri

glxgears still display the wrong FPS...

---

### Post by tworkemon on 2006-09-14
Here is an updated version of the script. It uses the latest ATI drivers 8.28.8. My suggestion would be this... Remove any fglrx packages from adept, apt-get, or what ever you use first prior to running this. Examples would be... fglrx-control, fglrx-kernel-"your kernel", fglrx-kernel-source, xorg-driver-fglrx. Also remove the /etc/ati directory if apt-get remove or whatever you use has not done so. The script should remove the necessary packages but better be save to do them yourself incase. This script is not 100% guarenteed but works most of the time. I did not change the readme so read it but ignore the ati driver part since this does use the latest 8.28.8 but do follow the rest as far as repository etc..

Let me know if you have any problems.

---

### Post by Kilz on 2006-09-14
I added a link to your post on the first post so people can find it barried back this far. Im no longet developing the script, so thanks for posting this one.

---

### Post by lassegs on 2006-09-14
Hi,

Nice script, but ive got a problem. I manage to install it and fgl_glxgears -fbo seems to be running fine, with about 105 fps. But in cedega 3d acceleration fails, and all the screensavers with 3dacceleration lags big time.
My card is a Radeon Mobility x700, and my fglrx_info shows this
lasse@cylinder:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.6011 (8.28.8)

What is happening here? Help would be very much apriciated!

EDIT: THE 8) is actually just an 8 with a ) behind.

---

### Post by kingofsnakes2111 on 2006-09-15
> **lassegs said:**
> Hi,

Nice script, but ive got a problem. I manage to install it and fgl_glxgears -fbo seems to be running fine, with about 105 fps. But in cedega 3d acceleration fails, and all the screensavers with 3dacceleration lags big time.
My card is a Radeon Mobility x700, and my fglrx_info shows this
lasse@cylinder:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.6011 (8.28.8)

What is happening here? Help would be very much apriciated!

EDIT: THE 8) is actually just an 8 with a ) behind.

Did you try within a terminal:

sudo mkdir /usr/X11R6/lib/modules
sudo ln -s /usr/lib/dri /usr/X11R6/lib/modules/dri

---

### Post by kvonb on 2006-09-21
I just used tworkemon's script and it worked flawlessly for me.  I followed his advice on removing all the modules manually, then ran his script.  I modified his script so that it didn't download the driver as I had it already and didn't want to re-download it, and also remmed out the reboot line for safety.

Rebooted and all is perfect, thanks tworkemon and killz.

Also I started having problems with opengl screensavers slowing down and followed kingofsnakes2111's advice to a letter, and it now works perfectly.

I play Battlefield 1942 through Cedega, and with this latest driver that silly box in the middle of the screen is back! (see attached screenshot).

I do believe this is a driver problem, as nothing has changed in Cedega or BF1942.  If anyone has managed to fix this, please let me know how.

Regards,

Kev :)

---

### Post by fummo on 2006-10-10
Thank you very much :wink: =D> :biggrin:

---

### Post by Kobalts on 2006-10-17
> **kingofsnakes2111 said:**
> I've just solved the screen saver problem.
There is something wrong with the path of Xscrensaver not looking for dri in the right place (/usr/lib/dri/fglrx_dri), instead Xscreensaver looks in /usr/X11R6/lib/modules/dri which is non-existent.

The way to solve:

sudo mkdir /usr/X11R6/lib/modules
sudo ln -s /usr/lib/dri /usr/X11R6/lib/modules/dri

glxgears still display the wrong FPS...


Hey thanks!  This works great.  Now my screen savers run much faster.

How did you find this fix anyway?   I didn't see any error messages or anything being printed anyplace?

From what I understand, the ln command just creates a link, so that the programs looking for  /usr/lib/dri is then pointed to /usr/X11R6/lib/modules/dri right?  (Sorry, I am still a n00b in this stuff)

---

### Post by Nio on 2006-10-17
I have a M6 LY, will this script bring me 3D Support or stop my X from working? Thanks in advance!

---

### Post by kingofsnakes2111 on 2006-10-18
> **Kobalts said:**
> 
How did you find this fix anyway?   I didn't see any error messages or anything being printed anyplace?

From what I understand, the ln command just creates a link, so that the programs looking for  /usr/lib/dri is then pointed to /usr/X11R6/lib/modules/dri right?  (Sorry, I am still a n00b in this stuff)

Hello,

Effectively, screen saver doesn't report any errors. It just doesn't find the right dri files (accelerated one).
So to find which files are missing, you can use the command "strace" which trace all system call of a command, you can use it like:
strace -o /tmp/log.txt /usr/lib/xscreensaver/glplanet

Beware that decoding the resulting log file is not easy, it uses C function, hexadecimal, ... 

I regulary use this command to find out what's wrong...

Best regards

---

### Post by prosonik on 2006-10-24
I have a sapphire 9600.. Worked fantastic.. Using Stock Dapper /with Automatrix etc.. 

prosonik



Let me know if you have any problems.[/QUOTE]

---

### Post by ilushkin on 2006-10-24
please update the script for 6.10 edgy version !

---

### Post by Placenta Juan on 2006-10-24
Worked like a charm on my ati 9600xt,
thanks tworkemon!
Just curious if I'll need to do anything special when I upgrade to edgy

---

### Post by Miraaz on 2006-10-25
TO NOT try it in Edgy! Not working! Tested.

---

### Post by TVMA on 2006-10-25
The script worked beautifully for me, I tried the ATI driver from the aTI site first, and it didn't work, but this worked like a charm. Thanks again.

---

### Post by mitjab on 2006-10-29
it works for me too in edgy. I use fglrx drivers not ati and works fine for me!

---

### Post by Kobra on 2006-10-29
I used the script last night, and everything went alright, but my zorg.conf was borked.  I had to set it back to ati to be able to boot.  But when I booted this morning, the Update Manager said that I had 4 updates, and two of them were the fglrx-kernel-source and the fglrx-control.  Should I try running fglrx in my xorg now?

The bottom line is, go ahead and try the Dapper ATI Driver's script in Edgy.  BUT, it is kinda hit-or-miss.  For me, it was a miss, but I'm working around that

---

### Post by mitjab on 2006-10-29
why i have this

```

mitjab@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


```

and not ATI RAdeon 9800

---

### Post by Finsta on 2006-11-04
> **mitjab said:**
> why i have this

```

mitjab@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


```

and not ATI RAdeon 9800
I've been getting that too and I have an ATI Radeon 9800XT, weird...

---

### Post by Placenta Juan on 2006-11-05
If it says mesa, then you're not using the proprietary ATI drivers. The only way I could get ATI's drivers to work in edgy was by following Method 2 at the guide found here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

That said, I updated the script to reflect these changes and install the new 8.30.3 drivers in Ubuntu Edgy. If you would like to use it you **must** follow a few steps before you run the script.
1. Make sure your card is supported! Anything older than a 9500+ is unsupported, so check the list at [ATI's site]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300")
2. Fglrx does not support compositing, which is enabled by default in Edgy. This must be disabled in your xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```
then add these lines at the bottom (if they're not already there)
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```
save and exit.
3. You have to blacklist the old fglrx module from linux-restricted-modules
```
sudo gedit /etc/default/linux-restricted-modules-common
```
Find the line DISABLED_MODULES and add "fglrx" (should look something like this)
```
DISABLED_MODULES="fglrx"
```
4. Download attached file and unpack to desktop
5. Run file with this command:
```
cd ~/Desktop/ATI
sudo ./ATI
```

After rebooting, check that everything installed OK
```
fglrxinfo
```
should output something like:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6119 (8.30.3)

Hope this helps some of you.

---

### Post by darrenrxm on 2006-11-05
It worked! Thanks a lot for making this script.

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6119 (8.30.3)

---

### Post by sjust on 2006-11-05
I have done all the steps before. I just had to run the script and it worked great. Nice work keep it up.

---

### Post by nbhaskar on 2006-11-06
> **Placenta Juan said:**
> If it says mesa, then you're not using the proprietary ATI drivers. The only way I could get ATI's drivers to work in edgy was by following Method 2 at the guide found here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

That said, I updated the script to reflect these changes and install the new 8.30.3 drivers in Ubuntu Edgy. If you would like to use it you **must** follow a few steps before you run the script.
1. Make sure your card is supported! Anything older than a 9500+ is unsupported, so check the list at [ATI's site]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300")
2. Fglrx does not support compositing, which is enabled by default in Edgy. This must be disabled in your xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```
then add these lines at the bottom (if they're not already there)
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```
save and exit.
3. You have to blacklist the old fglrx module from linux-restricted-modules
```
sudo gedit /etc/default/linux-restricted-modules-common
```
Find the line DISABLED_MODULES and add "fglrx" (should look something like this)
```
DISABLED_MODULES="fglrx"
```
4. Download attached file and unpack to desktop
5. Run file with this command:
```
cd ~/Desktop/ATI
sudo ./ATI
```

After rebooting, check that everything installed OK
```
fglrxinfo
```
should output something like:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6119 (8.30.3)

Hope this helps some of you.

when I type in fglrx, the following error is displayed. Can you please tell me why? Am I missing any thing?

```
babu@babu-desktop:~$ fglrxinfo
bash: fglrxinfo: command not found
```

Update:

Never mind i just installed fglrx driver (i had 'radeon' driver before) and restarted the machine now I get the following message.

```
babu@babu-desktop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

---


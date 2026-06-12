---
title: "[SOLVED] No letters appear in OpenOffice programs."
date: 2008-11-22
forum: New to Ubuntu
---

### Post by ikisham on 2008-11-22
I'm using Ubuntu 8.10 for about a week now and yesterday I opened Writer and saw that no text appeared:

[[IMG]http://img171.imageshack.us/img171/3101/writervl8.th.png[/IMG]](http://img171.imageshack.us/my.php?image=writervl8.png)
[[IMG]http://img530.imageshack.us/img530/5505/presentationfd5.th.png[/IMG]](http://img530.imageshack.us/my.php?image=presentationfd5.png)
[[IMG]http://img171.imageshack.us/img171/2663/impressjp3.th.png[/IMG]](http://img171.imageshack.us/my.php?image=impressjp3.png)
[[IMG]http://img81.imageshack.us/img81/6751/help2cu3.th.png[/IMG]](http://img81.imageshack.us/my.php?image=help2cu3.png)
[[IMG]http://img386.imageshack.us/img386/5439/helpif0.th.png[/IMG]](http://img386.imageshack.us/my.php?image=helpif0.png)
[[IMG]http://img81.imageshack.us/img81/8186/drawev5.th.png[/IMG]](http://img81.imageshack.us/my.php?image=drawev5.png)
[[IMG]http://img142.imageshack.us/img142/6013/calcnv8.th.png[/IMG]](http://img142.imageshack.us/my.php?image=calcnv8.png)

As you can see it happens with all OO programs. Also I didn't notice before as it was the first time I was gonna use it.I thought it could be because I was using Portuguese as system language so I turned to English and it didn't alter. Since I need these programs I decided to reinstall Ubuntu, now in English. After reinstall it showed the text normally (btw just like with the live-cd). Then I used update-manager and downloaded and installed those circa 72 MB of first-update files, restarted and, when opened OO, there it was the problem again.
**Afterwards** I installed java packages to see if it would help (you see I'm really a guesser), but no. Then I update to OO 3.0 (by adding this link deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main to third-party software sources; it updates java and OO perfectly) but the problems, as you see, persists.
If necessary I can reinstall Ubuntu again to try to catch more exactly when the problem appears (if it appears) but I would rather not do that.
Maybe some source code fiddling can resolve?
Well, as a last information, there's a kind of a bug when Ubuntu opens the cd tray at the end of install or live-cd, it opens and closes immediately so once it scratched the cd when I tried to pull it out and since everything else in the os is working perfect I would think this isn't the cause for the problem.
Obs: actually the text flashes quickly when you point to a button for ex.

---

### Post by jenkinbr on 2008-11-22
The CD issue was a udev bug that can be solved by doing an upgrade on all your packages.  To get your CD back, just wait for the restart and then eject the drive while the bios is doing it's business.

As for OO.o, wtf?  My first guess was some gtk settings with the theme you are using, but if it is only an OO.o issue, then I don't know....

That CD drive thing annoyed the heck out of me, though.

---

### Post by ikisham on 2008-11-22
Found this at the OpenOffice forum:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=10183](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=10183)
Thank you anyway. Now I'll only go back to Windows when/if it becomes open source software!=D>
Details: actually the only box to disable is 'screen font anti-aliasing'. Since if one has the same problem wont see anything that's written, it is the second of the five checked squares in the first column of the tools>options>view box. Actually the letters are now jagged.
Found the cause: I have a GF4 MX-460-VTP gpu with NVIDIA accelerated graphics driver (version 96), I disable it, restarted and now anti-aliasing is working. Could that be fixed someway?

---

### Post by ikisham on 2008-11-22
Just one last point. I've opted to keep NVIDIA driver enabled, this makes all OpenOffice.org programs unable to apply anti-aliasing to the fonts so being somewhat with a jagged appearance. I would really want to know if that can be fixed. Maybe some command line settings (for example: where do I find the README for the driver?). The driver I use (version 96) is for kinda old gpus so I don't know if much ppl are interested unless it affects other versions too. Should I post somewhere else in the forum? Is this a problem to be reported as a bug?
Thanx for your kind help.

---

### Post by ikisham on 2008-11-23
I deactivated nVidia driver and reactivated it some times to make some tests and now OpenOffice 'screen font anti-aliasing' is working perfectly well.
To put short, the solution could have been: uncheck 'screen font antialiasing' in OO tools>options>view; deactivate nVidia driver: restart; activate nVidia driver; restart; check 'screen font antialiasing' and it's done.

---

### Post by ikisham on 2008-11-28
I'm reopening here since I've reinstalled ubuntu 8.10 and can't make 'screen font antialiasing' work in OO with visual effects set to 'normal'.
I found a solution here:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/294076](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/294076)
The last post said this:
"I have been looking at several forums and doing a lot of Google-ing about this bug these last few days and it seems to me that:

1. Many people have been affected by this with their legacy cards.
2. It manifests itself with many different applications..OOv3, Opera, K3b, GoogleEarth....
3. There are several proposed "fixes" such as anti-aliasing, turn off compositing, the one above from TexasRanger.
4. Some work for some and not for others.
5. For me (Geforce4 MX440 card with 96beta driver on Intrepid) I changed my xorg.conf file to

Option "RenderAccel" "False"
or
Option "RenderAccel" "0"

in the Section "Device"."

So I came here since I think it's the most adequate forum to ask a simple question: how do I change my xorg.conf file?
Btw, I'm using Geforce4 MX460-VTP.

---

### Post by ikisham on 2008-11-28
I put sudo gedit /etc/X11/xorg.conf and got this:

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

So or the command should be other or I don't have this Option "RenderAccel"

Well I'm trying to google this but if anybody sees it, pls help.

---

### Post by ikisham on 2008-11-28
Well, I have this basic question here. I'm trying to fix the nVidia 96 driver problem with 'screen font anti-aliasing' in OpenOffice.
The original post is here:
[http://ubuntuforums.org/showthread.php?p=6230724#post6230724](http://ubuntuforums.org/showthread.php?p=6230724#post6230724)
Thank you very much.

---

### Post by overdrank on 2008-11-28
> **ikisham said:**
> Well, I have this basic question here. I'm trying to fix the nVidia 96 driver problem with 'screen font anti-aliasing' in OpenOffice.
The original post is here:
[http://ubuntuforums.org/showthread.php?p=6230724#post6230724](http://ubuntuforums.org/showthread.php?p=6230724#post6230724)
Thank you very much.

Please do not make duplicate threads on the same issue. Threads merged. :)

---

### Post by ikisham on 2008-11-28
I opened another thread because it's a separate issue and one would never guess seeing the title of this thread. Also I didn't close this one cos when I get this fixed I can post how I did it. And could you pls tell me if what I did is correct to change the xorg.conf file? If yes ,I'll have to search another solution ..

---

### Post by geear on 2008-11-28
I don't know about correctly editing xorg.conf file. Here's a temporary fix though, might help.

I'm using a Dell 8200 with the GeForce 440 and having the same problem with OOo 2.4 and Ubuntu 8.10. I didn't find a fix, but here's something that helped a bit until a real solution is found:

On the Tools>Options>View under "Screen font antialising" you can adjust the "from 1 Pixels". Change this to 14/15 (maybe more/less for you).

With that the text in the document looks right (as long as you don't zoom too far out), and the menus are readable, though NOT antialised. Also, de-activate "Preview of fonts" otherwise that menu remains unreadable. I also noticed that some of the numbers in the fight-size menu are rotated 90 degrees... odd! I think the only number rotated is the "4"


Gaelan :)

---

### Post by geear on 2008-11-28
Well, turning off desktop effects solved the problem too. It also solved another problem I was having: scrolling in FireFox or any moderate size document was very slooooow. I guess I'll have to mess around with the nvidia drivers... ah well, another day. I can live without the desktop effects for now.

G.

---

### Post by ikisham on 2008-12-01
I typed 'sudo gedit /etc/X11/xorg.conf' in Terminal and got this:
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
 Identifier "Configured Monitor"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
 DefaultDepth 24
 Option "AddARGBGLXVisuals" "True"
EndSection

Section "Module"
 Load "glx"
EndSection

Section "Device"
 Identifier "Configured Video Device"
 Driver "nvidia"
 Option "NoLogo" "True"
EndSection

Then I added <tab>Option<tab>"RenderAccel"<tab>"False"
in the "Device" section, restarted (rebooted) and now the problem is solved, at least in OpenOffice.

---

### Post by RobHK on 2009-04-06
> **ikisham said:**
> I put sudo gedit /etc/X11/xorg.conf and got this:

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

So or the command should be other or I don't have this Option "RenderAccel"

Well I'm trying to google this but if anybody sees it, pls help.

I didn't find *Option "RenderAccel" *either, so I just added it and it worked

---


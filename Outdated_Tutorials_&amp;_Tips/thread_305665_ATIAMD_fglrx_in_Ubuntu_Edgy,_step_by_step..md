---
title: "ATI/AMD fglrx in Ubuntu Edgy, step by step."
date: 2006-11-23
forum: Outdated Tutorials &amp; Tips
---

### Post by slavik on 2006-11-23
written by Vyacheslav Goltser

This HOWTO is to get ATI's (now AMD's) fglrx module working under edgy. Reason for this HOWTO is that the wiki page has all the info thrown about and weird to follow. This HOWTO attempts to streamline the instruction already available on the wiki page.

Step 0: Let's create a working environment so that we can clean up afterwords
```
cd ~/Desktop; mkdir atitemp; cd atitemp
```

Step 1: Download the proper packages we will need.
```
sudo apt-get install fakeroot gcc-3.4 module-assistant build-essential debhelper
```

Step 2: Download the latest driver from the ATI/AMD site, as of 11/23/2006, it is 8.31.5
```
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.31.5-x86.x86_64.run
```

Step 3: Make the driver executable
```
chmod +x ati-driver-installer-8.31.5-x86.x86_64.run
```

Step 4: We need to generate the packages, but because the default shell is not bash (which we need) we need to make it default and then generate packages (this piece of code, also undoes it)
```
sudo mv /bin/sh /bin/sh.old
sudo ln -s /bin/bash /bin/sh
fakeroot sh ./ati-driver-installer-8.31.5-x86.x86_64.run --buildpkg Ubuntu/edgy
sudo rm /bin/sh
sudo mv /bin/sh.old /bin/sh
```

Step 5: We need to install the generated packages and build the kernel module (this is the actual driver)
```
sudo dpkg -i *.deb
sudo module-assistant prepare,update
sudo module-assistant build,install fglrx-kernel
sudo depmod
```

Step 6: Package linux-restricted-modules has it's own fglrx module which we need to blacklist.
```
sudo gedit /etc/default/linux-restricted-modules-common
```
put fglrx between the quotes, save and exist

Step 7: Let's make sure that the driver is actually loadable. If you get an error here (output about it not being found) then read Troubleshooting Step 1.
```
sudo modprobe fglrx
```

Step 8: Edit /etc/X11/xorg.conf to load fglrx instead of whatever is there.
```
sudo gedit /etc/X11/xorg.conf
```
Scroll down to the Section "Device" that reffers to your video card and on the line that starts with Driver, change whatever is in quotes to fglrx (it is most likely that ati or radeon is there).

Step 9: We need to restart X.
```
sudo /etc/init.d/gdm restart
```

At this point you should have the drivers working confirm with the following code:
```
glxinfo | grep direct
```

You should receive output that looks like this:
```
Direct Rendering: yes
```

If you don't get that line, then try rebooting, if that doesn't help, come to the IRC channel #ubuntu on irc.freenode.net network.

Troubleshooting step 1: modprobe can tell you that it can't find the module, if it is so, execute the followin g piece of code:
```
sudo cp /lib/modules/2.6.17-10-generic/misc/fglrx.ko /lib/modules/2.6.17-10-generic/volatile/fglrx.ko
```

---

### Post by seijling on 2006-11-29
Well as smooth as that walk through went, it didn't seem to completely work.  I sill cannot get "direct Rendering".  Is there something I can do?  I asked in irc but no one seemed to know/care.

Thanks either way - graphics are working much better.

---

### Post by ericsonp on 2006-12-07
These instructions worked up to: 

  sudo modprobe fglrx

which returns:

  FATAL: Error running install command for fglrx

It appears I have the right sources:

root# apt-cache showpkg fglrx-kernel-source
Package: fglrx-kernel-source
Versions: 
8.31.5-1 (/var/lib/dpkg/status)

root# apt-cache showpkg xorg-driver-fglrx-dev
Package: xorg-driver-fglrx-dev
Versions: 
8.31.5-1 (/var/lib/dpkg/status)

Any suggestions on troubleshooting this problem?

Thanks,

Paul

---

### Post by ericsonp on 2006-12-07
Here's more info...


paule@paule2:~$ sudo modprobe -vf fglrx
install /sbin/lrm-video fglrx 
insmod /lib/modules/2.6.17-10-generic/misc/fglrx.ko 
FATAL: Error running install command for fglrx


paule@paule2:~$ sudo install /sbin/lrm-video fglrx 

returns nothing and

paule@paule2:~$ sudo insmod /lib/modules/2.6.17-10-generic/misc/fglrx.ko 

returns:
insmod: error inserting '/lib/modules/2.6.17-10-generic/misc/fglrx.ko': -1 Invalid module format

What does "Invalid module format" mean?

Cheers,

Paul

---

### Post by kthakore on 2006-12-07
Try my script for ATI drivers it works for edgy

[fglrxinstaller]("http://kartikhacked.blogspot.com")

---

### Post by ericsonp on 2006-12-07
Thanks!

FYI it doesn't work with the current version of the ATI driver (8.31.5-x86.x86_64) due to ATI's deviation from their previous naming convention.

I should still be able to get it working though. Any idea which version of the driver will work with Edgy?

Cheers,

Paul

---

### Post by ericsonp on 2006-12-07
So I modified your script and it runs without errors, but still no direct rendering, still using Mesa driver!

```

version=8.31.5-x86.x86_64
#wget http://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-$version.run
sudo ln -sf bash /bin/sh
sudo apt-get remove fglrx-kernel-2.6.17-10-generic
bash ati-driver-installer-$version.run --buildpkg Ubuntu/edgy
version=8.31.5
sudo ln -sf dash /bin/sh
sudo dpkg -i xorg-driver-fglrx_$version-1*.deb
sudo dpkg -i fglrx-kernel-source_$version-1*.deb
sudo dpkg -i fglrx-control_$version-1*.deb
sudo rm /usr/src/fglrx-kernel*.deb
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo cp libGL.so.1.2 /usr/lib/

```

I commented out the wget since I already had the .run file. Been working on this on and off for days. Worst time I've ever had with a video driver.

---

### Post by ericsonp on 2006-12-08
More clues:

dmesg says:

> [17179610.272000] fglrx: version magic '2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-3.4' should be '2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1'

It appears that:

```
apt-get install build-essential 
```

requires gcc-4.1:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  g++ g++-4.1 gcc gcc-4.1 libstdc++6-4.1-dev
Suggested packages:
  gcc-4.1-doc lib64stdc++6 manpages-dev autoconf automake1.9 libtool flex
  bison gcc-doc gcc-4.1-locales libc6-dev-amd64 lib64gcc1 libstdc++6-4.1-doc


One solution is to leave gcc-4.1 installed and compile a new kernel and all the kernel modules. But this seems like a lot of work just to get one driver working.

Is gcc-4.1 required to compile the fglrx module?

Was the Edgy distro was compiled with gcc-3.4?

Opinions?

---

### Post by kcallis on 2006-12-08
The closest that I can to actually working was I was able to boot, but as soon as GDM started, there were problems with the screen. From there, the system would eventually lock up. 

I am running under 2.6.19 and the card in question is a X200m. The battle continues!!! ](*,)

---

### Post by kcallis on 2006-12-09
> **kcallis said:**
> The closest that I can to actually working was I was able to boot, but as soon as GDM started, there were problems with the screen. From there, the system would eventually lock up. 

I am running under 2.6.19 and the card in question is a X200m. The battle continues!!! ](*,)
Well, I am back to back screen of death, and I it would look like I am never going to get away with using fglrx as my driver... Nevertheless, I will keep battling, until I come up with some different!

---

### Post by PatsM on 2006-12-09
I followed steps described. Now I can't startup ubuntu anymore.
At startup i keep getting /bin/sh not found.
HELP; i don't wont to reinstall ubuntu from scratch (again).

---

### Post by trevis on 2006-12-10
> **slavik said:**
> 
Troubleshooting step 1: modprobe can tell you that it can't find the module, if it is so, execute the followin g piece of code:
```
sudo cp /lib/modules/2.6.17-10-generic/misc/fglrx.ko /lib/modules/2.6.17-10-generic/volatile/fglrx.ko
```

I have to run this every time i restart my laptop, is there a way around this?

---

### Post by deethree on 2006-12-10
AWESOME!

Finally I can play Q1!

Thanks dude!

d3.

---

### Post by bodhi.zazen on 2006-12-15
Nice How-to

This thread has been added to the UDSF wiki.

[ATI_AMD_fglrx_Edgy](http://doc.gwos.org/index.php/ATI_AMD_fglrx_Edgy)

---

### Post by arron on 2006-12-16
I have followed both the howto, and the script to install the drivers.

All seems to go well, but i still cant get 3d rendering.  I have a ATI 200m on a compaq r4000 laptop.  When i try to run anything 3d i get:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".

Everything seemed to go ok installing it with no errors, i just get this error now when running something.....argggggg maybe linux users should boycott ati until they get their stuff together.

PLEASE HELP!!!! anyone get this working on a 200m card?

---

### Post by themikeflynn on 2006-12-16
I followed this guide completely, and get "Direct Rendering: yes" at the end. So I thought it completed correctly. However, my 3D rendering is **very slow**. I tested out a few screensavers and they all crawl. I'm using a 9800pro that went through them with ease in my older drivers.

This is the Device section of my xorg.conf. Shouldn't there be mention of 9800 pro? I'm pretty sure this is where the fault is. I added fglrx to the blacklist, but I'm not sure if it went right... help? ](*,) 
> Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

---

### Post by kesman on 2006-12-17
Whoa man, thanks so much! I know that glxgears shouldn't be used for this, but anyways, fps from around 300 jumped up to 4000 after this update :) Next stop, Beryl :P

Edit:

Well, I just noticed that every 3d application now causes me 100% cpu usage... What's causing this?

Here's some configs:

from /etc/X11/xorg.conf
```

Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection

```
```

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
        Driver          "fglrx"
        Option          "VideoOverlay" "on"
        Option          "OpenGLOverlay" "off"
#       Option          "DesktopSetup" "single"
        BusID           "PCI:1:0:0"
        Option          "XaaNoOffscreenPixmaps"
EndSection

```
```

Section "Extensions"
        Option      "Composite" "disable"
EndSection

```

---

### Post by slavik on 2006-12-21
> **arron said:**
> I have followed both the howto, and the script to install the drivers.

All seems to go well, but i still cant get 3d rendering.  I have a ATI 200m on a compaq r4000 laptop.  When i try to run anything 3d i get:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".

Everything seemed to go ok installing it with no errors, i just get this error now when running something.....argggggg maybe linux users should boycott ati until they get their stuff together.

PLEASE HELP!!!! anyone get this working on a 200m card?
my next upgrade involves an nvidia card :P

as for the DRI missing piece, I think you have to load the dri module ...

---

### Post by s1zzk3r on 2006-12-26
Oh please help. Everything is workin prefectly but I get this:

direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

How do I change it to Yes?

Here are my xorg.conf sections:

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "XAANoOffscreenPixmaps"
        BusID       "PCI:1:5:0"
EndSection

Section "Extensions"
        Option      "Composite" "disable"
EndSection


I need it to be Yes please :(

---

### Post by InterNut on 2006-12-29
when i try this "step by step" install i get to the :
"**sudo modprobe fglrx**"
and all i get is:
[B]FATAL: Error running install command for fglrx.

[/B]no errors during the previous commands, im using the **ati-driver-installer-8.32.5-x86.x86_64, **instead of the ati-driver-installer-8.31.5-x86.x86_64 in this guide.

any suggestions?

i have a 9800pro crd

---

### Post by Extrapolation on 2007-01-18
I followed all the instructions, until restarting X.  Now when I boot up, it starts up Ubuntu, then takes me to a black screen where even my monitor says it has no input.  How can I even roll back the driver to the working one I had before?  I can't even access the desktop now!

---

### Post by Jose Catre-Vandis on 2007-02-05
All goes well until:
```
 sudo modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.17-10-generic/misc/fglrx.ko): Operation not permitted
```

I have checked, it is there!

SOLVED: Sorted this out by going back to the wiki and the repos to get fglrx and then everything installed fine and I have direct rendering and 3D, and mplayer works :-)

---

### Post by stucky on 2007-02-11
> **arron said:**
> I have followed both the howto, and the script to install the drivers.

All seems to go well, but i still cant get 3d rendering.  I have a ATI 200m on a compaq r4000 laptop.  When i try to run anything 3d i get:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".

Everything seemed to go ok installing it with no errors, i just get this error now when running something.....argggggg maybe linux users should boycott ati until they get their stuff together.

PLEASE HELP!!!! anyone get this working on a 200m card?


Same issue here on a Radeon 9250. I was very careful to make sure I pointed it to the 8.28 drivers as I know those are the last to support my card. At lease X isn't broken, but what's with the XFree86 error?

---

### Post by stucky on 2007-02-11
On a lark, just searched XFree86-DRI in Synaptic and it came back with x11proto-xf86dri-dev. 

Installed it restarted X  and ran a quick
```
 glxinfo | grep direct
```

and FINALLY received this back

direct rendering: Yes


:guitar: :guitar: Halle-frickin-lujah!!!!:guitar: :guitar:

---

### Post by ericsonp on 2007-02-14
Glad to hear of your success; however, this solution still does not get direct rendering working for me. 

It would be great if someone on the dev team would come up with a better solution as the current one appears to be unreliable and overly complicated.

---

### Post by stucky on 2007-02-14
Working - yes
Improvement - no

Completely underwhelmed. I'm thinking that a 128 MB video card should be able to blow my non-gaming mind and provide for smooth scrolling and reasonable 3D capabilities. I'm getting 7.5 fps on gears. :(  The preview says 118 fps. I'm really hating the whole video card world right now.

---

### Post by slavik on 2007-03-07
> **ericsonp said:**
> These instructions worked up to: 

  sudo modprobe fglrx

which returns:

  FATAL: Error running install command for fglrx

It appears I have the right sources:

root# apt-cache showpkg fglrx-kernel-source
Package: fglrx-kernel-source
Versions: 
8.31.5-1 (/var/lib/dpkg/status)

root# apt-cache showpkg xorg-driver-fglrx-dev
Package: xorg-driver-fglrx-dev
Versions: 
8.31.5-1 (/var/lib/dpkg/status)

Any suggestions on troubleshooting this problem?

Thanks,

Paul

Ran into the same problem, rebooted and everything loaded up fine :)

---

### Post by maqi on 2007-03-19
Hey slavik,

Great post! Couldn't get the ubuntu restricted drivers working, but followed your instructions for the latest drivers (ati-driver-installer-8.34.8-x86.x86_64.run) and it worked perfectly. Thanks heaps :)

Cheers,
maqi

---

### Post by dgg222 on 2007-03-29
> **Extrapolation said:**
> I followed all the instructions, until restarting X.  Now when I boot up, it starts up Ubuntu, then takes me to a black screen where even my monitor says it has no input.  How can I even roll back the driver to the working one I had before?  I can't even access the desktop now!

Same thing happened to me. I had to boot off the Ubuntu CD, mount the hard drive with:

sudo mkdir /media/temp
sudo mount /dev/sda1 /media/temp

then edit the xorg.conf file:

sudo gedit /media/temp/etc/X11/xorg.conf

In the device section I changed the driver back to "ati" then saved and rebooted without the CD in.

That allowed me to log back in to the desktop but I doubt it's fixed the problem completely. I probably have no video driver at all now :(

---

### Post by dmeans08 on 2007-03-30
If anyone is still getting an XFree86-DRI on device error, I fixed it by following the directions in this link [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)  I followed the guide the ubuntu way, then did the configure directions and everything works perfectly now.

---

### Post by wysinwyg on 2008-02-19
Edit: I had a thought.  This guide it geared towards Ubutnu Edgy.  Is the problem possibly that I'm installing this on Ubuntu/gutsy? I'm not sure if the commands or steps are somehow different, but this guide shows more promise than most of the rest that a google search found.

Here's what I've gotten using the 9800 Pro and the drivers from ATI/AMD that are supposed to support it.  (Please, bear with me, my expertise level is.... well it's almost nil.)

Using this guide, I've gotten up to the point where you use fakeroot and, after all of a bunch of code that I personally don't understand, I get the following

```
nick@nofear:~/Desktop/atitemp$ chmod +x ati-driver-installer-8-02-x86.x86_64.run
nick@nofear:~/Desktop/atitemp$ sudo mv /bin/sh /bin/sh.old
nick@nofear:~/Desktop/atitemp$ sudo ln -s /bin/bash /bin/sh
nick@nofear:~/Desktop/atitemp$ fakeroot sh ./ati-driver-installer-8-02-x86.x86_64.run --buildpkg Ubuntu/gutsy
Created directory fglrx-install.J16459
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.455.2....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.455.2-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 8.455.2-0ubuntu1
 debian/rules build
echo "Using architecture: i386"
Using architecture: i386
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.C16545/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.C16545/debian/driver.$i > \
              /tmp/fglrx.C16545/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.C16545/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.C16545/debian/10fglrx.template > /tmp/fglrx.C16545/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.C16545/debian/fglrx.default ]; then \
          mv /tmp/fglrx.C16545/debian/fglrx.default /tmp/fglrx.C16545/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib64: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
dh_testdir
 fakeroot debian/rules binary
fakeroot: FAKEROOTKEY set to 1567221223
fakeroot: nested operation not yet supported
Removing temporary directory: fglrx-install.J16459

```
Not sure why it mentions debian but it's obviously not part of the plan here when it says "nested operation not supported."  This may have to do with changes on the ATI/AMD end?  I only speculate.   Please keep in mind that I've tried several of the ATI driver installation guides, including the one through aptitude which causes failure to boot.  The Automatic installation feature of this .run doesn't perform any of the setup tasks either, and you really have to scan each line of the help received when you simply type 'aticonfig'.

I've been at this for three days, and have bounced ideas around with a friend of mine whose knowledge has kept me sane so far.  Any help would be appreciated, as I haven't seen anyone post a working solution for the Radeon 9800 Pro (or I just haven't found it).

---

### Post by wysinwyg on 2008-02-25
/friendly bump

Anyone know what this jargon is telling me?  I'm sure it means something to someone out there, and it might just help me get to the end if it turns out to be the only hangup in the set-up process.

---

### Post by miker999 on 2008-03-24
Hi,

Take a look at:
[http://jeffrasmussen.wordpress.com/2007/01/12/ati-radeon-x1300-works/](http://jeffrasmussen.wordpress.com/2007/01/12/ati-radeon-x1300-works/)
which indicates that using sudo would solve the fakeroot error.

Regards

Michael

---

### Post by miker999 on 2008-03-24
Plus, this looks handy:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

M.

---


---
title: "How to Install fglrx 8.35.5 (feisty/edgy)"
date: 2007-04-14
forum: Outdated Tutorials &amp; Tips
---

### Post by bizarrosephiroth on 2007-04-14
HOW TO INSTALL:  fglrx Driver for ATI cards (edgy/feisty)
My name is safer (a.k.a bizarrosephiroth) and I am fairly new to linux.  The installation of fglrx was very painful for me because a lot of guides are 'incomplete' and/or 'erroneous'.  This guide is 100% working, but as our world is subject to change, feel free to list plausable changes that should be made.  
PEOPLE/SOURCES TO THANK.
From jinx.com: sakuramboo
From irc Ubuntu Servers: crdlb (#ubuntu-effects) and xtknight (#ubuntu) and others.
From ubuntuforums.org ----- Freebird54 and bdogg64
And the writers and editors of: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C)
PLEASE NOTE:
All command to be entered in terminal(shell/konsole) will be in dark red and italicized.  Also, while this guide is fairly short, please read carefully to ensure no section is skipped.
Enable "restricted" Repository 
To do this in GNOME, go to your System Menu > Administration > Software Sources. Place a check next to "Proprietary drivers for devices (restricted)," click Close, click Reload, and let the application update the package list. 
To do this in XFCE, go to your Applications > System > Software Sources. Place a check next to "Proprietary drivers for devices (restricted)," click Close, click Reload, and let the application update the package list. 
If you use KDE, go to K > System > Adept Manager Manage Packages. Enter your password. Go to Adept > Manage Repositories. Right Click everything that starts with deb or deb-src and select enable. Select fetch updates and you are good to go! 

*You need to enable the universe repository before updating
sudo apt-get update
sudo apt-get install -y --force-yes module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-$(uname -r) wget
Download ati proprietary driver
cd ~/  (Note that ~/ here means, whatever directory you want to put the file in: for instance, if you wanted to put the file in your home folder, you would type: cd /home/)
sudo wget [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.35.5-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.35.5-x86.x86_64.run)

Build .deb packages
sudo sh ./ati-driver-installer-8.35.5-x86.x86_64.run --buildpkg Ubuntu/edgy

Blacklist old fglrx module from linux-restricted-modules: 
Note: You only need to do this if you've installed the driver from Method 1 above. 
As ubuntu's linux-restricted-modules package includes the fglrx module from an old driver version (8.28.8), we have to blacklist this module to make sure the new kernel module which is needed by the new driver will be used instead. 
sudo gedit /etc/default/linux-restricted-modules-common
Add "fglrx" to the line "DISABLED_MODULES" 
File: /etc/default/linux-restricted-modules-common 
DISABLED_MODULES="fglrx"

Remove any old fglrx debs from /usr/src/: 
sudo rm /usr/src/fglrx-kernel*.deb
Fix broken dependencies 
Note: You only need to do this if you have installed previous versions of these drivers using this method before. 
sudo apt-get -f install
Needed for 8.35.5
sudo mkdir -p /usr/src/modules/fglrx/linux
sudo touch /usr/src/modules/fglrx/linux/config.h

Download Patch for 2.6.20.* kernels
cd ~/   (Note that ~/ here means, whatever directory you want to put the file in: for instance, if you wanted to put the file in your home folder, you would type: cd /home/)
sudo wget [http://darcs.frugalware.org/repos/frugalware-current/source/x11-extra/fglrx/fglrx-2.6.20.patch](http://darcs.frugalware.org/repos/frugalware-current/source/x11-extra/fglrx/fglrx-2.6.20.patch)

Apply Patch for 2.6.20.* kernels
cd /usr/src
sudo cp fglrx.tar.bz2 fglrx.tar.bz2-original
sudo tar -xvjf fglrx.tar.bz2
cd /usr/src/modules/fglrx
sudo patch -p0 < ~/fglrx-2.6.20.patch  (Note: ~/ means go to directory where the patch is located, so if it was in your home folder you would do ' sudo patch -p0 < /home/fglrx-2.6.20.patch'.  Also, note that if -p0 fails to work, you should use -p6) 
cd /usr/src
sudo tar -cvjf fglrx.tar.bz2 modules/fglrx

Compile the kernel module: 
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -ae
You are essentially done, but you need to disable AIGLX and Composite by making the following changes in your xorg.conf file:

sudo gedit /etc/X11/xorg.conf  (for Kubuntu: kdesu kate /etc/X11/xorg.conf)

Make sure the following are in the file and not inside a pre-existing Section.


Section "Extensions"
        Option      "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection

Also make sure that “ati” or “vesa” in your video card Driver section is changed to “fglrx” and the following three Option lines are also located in that same Section so it looks like this section below:

Section "Device"
        Identifier "ATI RADEON 9600XT"
        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection

YOU ARE DONE!!!!!!!!!!
All you need to do is the following ----- Restart you computer first.
IMPORTANT!!!!! ---- GO BACK TO GNOME!!!!! (OR KDE FOR KUBUNTU!!!)
I know most people are only going to do this in order to use beryl with Xgl.
I just want to make sure that no reader of this tutorial go directly to Xgl to test because Xgl does not function with glx, so some tests will come back negative.  Note: this doesn't affect 3D acceleration in Xgl.  And now for Testing --- read below:

Go to Terminal (Shell) and type the following three test codes:
fglrxinfo   
fgl_glxgears
glxinfo | grep rendering

The first code should yeild something like this:
display: :0.0  screen: 0

OpenGL vendor string: ATI Technologies Inc.

OpenGL renderer string: RADEON 9800 XT

OpenGL version string: 2.0.6400 (8.35.5)


The second code should display a cube(s) with gears rotating in 3D.

The third code should say something like this:
Direct rendering: yes  (Note: make sure this says “Yes” no matter what)

---

### Post by pay on 2007-04-14
I ended up just compilling the 2.6.19 kernel because I didn't realise that there was a patch for the 2.6.20 kernel that I  needed. Thanks for the guide but can I recommened that you put the people/sources to think section at the end so then the guide flows better?

---

### Post by tehquickness on 2007-04-17
I am having problems getting this to work. I have followed the directions however, fglrxinfo is still saying that I am still using the mesa driver:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

How can I start trying to trouble shoot this? Let me know what information I can give you to help figure this out.

---

### Post by nak on 2007-04-19
ATI has released a new version (8.36.5) that, supposely, fix the issue with the 2.6.20 kernels. I'm going to probe it and I'll post the results later. Bye

---

### Post by derrekito on 2007-04-21
> **nak said:**
> ATI has released a new version (8.36.5) that, supposely, fix the issue with the 2.6.20 kernels. I'm going to probe it and I'll post the results later. Bye

Yes I have the new drivers up and running.

---

### Post by wyth on 2007-04-21
derrekito, what card are you running?  If this is working now, off goes desktop effects and on go the drivers that actually work well on my old card.

---

### Post by hagar_am on 2007-04-21
Gigabyte Radeon X1300Pro

After upgrade to feisty:
fglrxinfo -> mesa..
glxinfo | grep direct -> NO

tried this howto & similar one, tried envy - finished with X working but:
fglrxinfo -> mesa..
glxinfo | grep direct -> NO
tried guide with 8.36.5 Xserver died when is going to show login screen there is just black screen.
I can press alt+ctrl+del/bacspace no respond..
Any idea here?

---

### Post by wyth on 2007-04-21
There was an issue with the ATI X-based cards.  Check out [this page]("http://www.mikesplanet.net/2007/04/installing-ubuntu-704-ati-x-cards/") for a possible fix.

---

### Post by hagar_am on 2007-04-21
Done similar things. I`ve just remove ati card and workin on my mainboard buil-in chipset.
I`m done with ati.):P ):P ):P

---

### Post by wyth on 2007-04-21
Y'see, there's where I'm envious -- I'm on a laptop.  Can't easily replace my card.  I'm even looking into trading up my old laptop for something that works with oss; it's that important.

---

### Post by hagar_am on 2007-04-22
That`s why I don`t like laptops;).. but if I will be thinking about buing one I`m going to stay away of ATI.

---

### Post by sadako1 on 2007-05-28
Dude, you saved my life! I owe you a debt of gratitude.

I drew a poltry 2041.2 FPS with that crazy fgl_glxgears command! That was a trip for the eyes!

Thanks again. Now I can get Beryl working on this thing!

Andrew

---


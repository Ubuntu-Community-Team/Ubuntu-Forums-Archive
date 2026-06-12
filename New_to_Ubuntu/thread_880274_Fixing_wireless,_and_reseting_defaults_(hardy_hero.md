---
title: "Fixing wireless, and reseting defaults (hardy heron)"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Chalks on 2008-08-04
I installed Gutsy on my computer from a live CD, and used the upgrade manager to upgrade it to Hardy Heron.  When I did so, my wireless card stopped working (it's a linksys card).  When I click on the networking icon in the top left, there's only an option for wired network... not wireless.  I tried to follow the instructions [here](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy) but even though I got the b43 and then the b43 legacy drivers installed, it still wasn't working.  What should I do?

Also, I have a radeon 3870.  After the initial installation of HH, my screen displayed at a resolution of 1024x768.  Then, I downloaded the 8.6 linux driver from ATI, and ran it.  After installing Catalyst Control Center, I could boot normally and get to the login screen with 1680x1050 resolution, but once I logged in, the screen would turn white and the system would hang.  If I changed the session to failsafe, it would login just fine.  Eventually I figured out that I needed to rerun "sudo aticonfig --initial -f"  then I ran it several more times with "--config=/path/I/can't/remember/xorg.conf", "--resolution=1680x1050" and a few of the other options from the example given by running just "aticonfig".  SO.  It works.  kind of.  When I drag a window around it lags considerably and slows the system way down... so it doesn't really actually work.

How can I reset the display drivers to default, and remove the drivers I installed?  I'm sure I installed them incorrectly.  Finally, I know I saw a guide for how to properly install them on this site, but I can't find it anywhere.  Can you point me to it?


Thank you.

---

### Post by phidia on 2008-08-04
Not the same card as yours but I've noticed a few posts about white screens with the ATI driver. This one [here]("http://ubuntuforums.org/showthread.php?t=871131&highlight=white+screen+ati") shows a possible source of the problem-but without a lot of bug reports I'm afraid it won't get addressed.
You should be able to run > sudo dpkg-reconfigure -phigh xserver-xorg in a terminal and get a working xorg.conf from that _but_ be sure to read the guide [here ]("https://help.ubuntu.com/community/Video")too.

---

### Post by Chalks on 2008-08-04
Yay!  using the .inf file from [[COLOR="Blue"]here[/COLOR]](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/) and the instructions [[COLOR="Blue"]here[/COLOR]](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy), I got my wireless working flawlessly.


The ati driver is still screwed though.  When I used that command, phidia, the white screen came back.  How can I remove the driver _completely_ (not just the conf file) and replace it with the default Hardy Heron installation drivers?

---

### Post by phidia on 2008-08-04
You can just edit /etc/X11/xorg.conf and replace the driver in the device section of that file with the stock/open source driver.

Take a look at the wiki [here]("https://help.ubuntu.com/community/RadeonDriver") on the specifics for your card.

Also pay close attention to section 3 **Removing the proprietary fglrx driver** 
and section 4 **Configuring X.org**

---

### Post by Chalks on 2008-08-05
Thanks very much for your help so far, Phidia.

I'm still having issues.  I followed the instructions for completely removing fglrx to the letter.  Then, I configured xorg.conf file as instructed.  Unfortunately I still got the white screen.  When I ran "glxinfo | grep "direct rendering"", I got 'No direct rendering'.  This apparently means I won't be able to use the open source driver.  So, I tried to do that yet again.  I think I got a little farther (though I'm still getting the white screen):


I _think_ that my problem is twofold.  First, in restricted manager, it says I don't have any proprietary drivers installed, also when I try to start catalyst control center, it says "no ATI driver installed".  However, Synaptic Package Manager says I have the following installed:
fglrx-control
radeontool
xorg-driver-fglrx
xserver-xorg-video-ati

Second, I think that maybe the xserver-xorg-video-ati package is conflicting with the xorg-driver-fglrx package?  I'm really not sure.  Any tips/pointers?


if this makes a difference, I can load ubuntu just fine in failsafe GNOME (with proper resolution and everything), but if I have the default session, I get the white screen.


EDIT:  WOOO!   ok, I got it working with the 8.7 driver too.  These [old instructions](http://wiki.cchtml.com/index.php/Category:Installation_Documentation) got me started on the right track.  Here's how to get it working in Hardy Heron:

1. download the proper linux driver from ati.com ([here's the one I used](http://ati.amd.com/support/drivers/linux/linux-radeon.html)).
2. open terminal and type "sudo bash path/to/ati-driver-installer-8-7-x86.x86_64.run"
2.b. just do the default options on the installer that pops up.
3. go back to terminal and type "sudo aticonfig --initial -f"
4. type "sudo vi /usr/bin/compiz"
4.b. find the line that says "WHITELIST="nvidia intel ati radeon i810""
4.c. change it to "WHITELIST="fglrx nvidia intel ati radeon i810""  (I think the order mattered?)
4.d. save it
5. reboot.

---


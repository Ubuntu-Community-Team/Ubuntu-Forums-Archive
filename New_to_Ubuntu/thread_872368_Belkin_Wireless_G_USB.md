---
title: "Belkin Wireless G USB"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by black04cert on 2008-07-27
I need some help with this thing.

I plug the usb adapter in and no light comes on. Ubuntu doesn't even recognize it. I've got a buddy that has the exact same adapter on his ubuntu laptop and he plugged it in and it worked just fine.

I have v8.04 Ubuntu. F5D7050 is the model # of the adapter. I've tried to follow some of these how to's and none have worked for me.

---

### Post by wdaniels on 2008-07-27
I think the module for this chipset is rt73usb which hasn't always worked by default in Ubuntu. First question, which Ubuntu version are you using?

Edit: You already said didn't you :D

OK, so can you post the output of this command:

```
sudo lsmod | grep rt
```

---

### Post by ptn107 on 2008-07-27
I have the exact same adapter and it works fine.  Make sure you have *linux-ubuntu-modules-2.6.24-19-generic* installed, as it contains the module [zd1211] you need for the adapter to work.

---

### Post by james_vanb on 2008-07-30
If you haven't already got it working, I've used the Belkin Wireless USB in both Gutsy and Hardy. Install has been the same using ndiswrapper and the Belkin install CD.

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands:

```
sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb
```

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

```
sudo gedit /etc/modprobe.d/blacklist
```

add "blacklist rt2500usb" and "blacklist rt73usb" (Without the quotes) to end of list, save and close.

REBOOT

Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin". Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following (If the .inf file you copied is not the rt73, replace as appropriate below) :

```
sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf
```

Insert the wireless adapter.

Now issue the following commands:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows (If you are using Xubuntu, replace gedit with mousepad):

```
sudo gedit /etc/modules
```

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

```
sudo ndiswrapper -m
```

Reboot

---

### Post by black04cert on 2008-07-31
Alright. Thanks for the help guys...it's installed but now I have a new problem...I have a linksys router...I have dhcp disabled on the router for lack of confidence in the dhcp and also assigning different ip's with different privelages. When i goto setup the wireless connection with roaming turned off and set it up with static ip's it doesn't work.

here's a few screenshots of what it looks like with roaming off...

---

### Post by james_vanb on 2008-08-01
You might want to try eliminating possible problem points to isolate what issue you really have to deal with.  For example, WEP is sometimes a challenge to correctly configure.  So, Try turning off WEP at your router and setting for automatic DHCP.  Set your computer to "Roaming" (and/or Manually Configure) and see if you can connect (you may have to reboot).  This will tell you if the Wireless USB is really working.  If it is not, your problem is with configuring the wireless connection.  

If you can connect, set WEP at your router - reboot - and try to connect (If still in roaming, you should get a pop up box asking for the password).  If you can not connect, try manually configuring - set WEP key and keep DHCP automatic - see if you can connect. If you can not connect, the problem is with setting security.  See this tutorial for possible solution:

[http://ubuntuforums.org/showthread.php?t=202834&highlight=wep](http://ubuntuforums.org/showthread.php?t=202834&highlight=wep)

If you can connect with WEP set, the problem is configuring the static IP.  I don't use a static IP, however, a quick Google found the following:

[http://ubuntuforums.org/showthread.php?t=17575](http://ubuntuforums.org/showthread.php?t=17575)
[http://ubuntuforums.org/archive/index.php/t-15774.html](http://ubuntuforums.org/archive/index.php/t-15774.html)

The following is for setting a static IP for a printer, but might point you in the right direction:

[http://www.watchingthenet.com/linksys-tip-assign-static-ip-address-to-printer-while-using-dhcp-on-your-wireless-network.html](http://www.watchingthenet.com/linksys-tip-assign-static-ip-address-to-printer-while-using-dhcp-on-your-wireless-network.html)

Hope it helps - Good luck!

---

### Post by Emjay111 on 2009-08-29
> **james_vanb said:**
> 

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin". Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following (If the .inf file you copied is not the rt73, replace as appropriate below) :

```
sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf
```Insert the wireless adapter.

Many thanks for the tutorial James, worked a treat on Intrepid.

One small ammendment for Intrepid though...

You'll find there isn't a shortcut to the Home folder on the desktop, so I just created a new folder anywhere on my desktop - I called it "Belkin" too (no quotes) -  and copied all the Belkin files to this folder instead.

The command for Intrepid should therefore include "Desktop" in the string - see example below.

```
sudo ndiswrapper -i /home/(your user name)/Desktop/Belkin/rt73.inf
```Note that it seems to be case sensitive as well.

The files I copied for my Belkin FSD7050 v4000 series USB stick were 

BLKWGU.inf
BLKWGUXP.sys
BLKWGU2K.sys 
BLKWGU9X.sys

(The last two were "just in case" they were needed.)

Thanks once again for writing this procedure up - much appreciated.  :P

Marcus

---

### Post by james_vanb on 2009-08-29
Marcus,

Glad it worked for you.  Thanks for keeping things current.

James

---


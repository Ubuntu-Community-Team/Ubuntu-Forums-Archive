---
title: "Broadcom wireless..."
date: 2008-05-02
forum: New to Ubuntu
---

### Post by tentel on 2008-05-02
I've been trying like mad to get this thing running.

here is the output from lspic -v

03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 1374
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at b6000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>



I found this guide [here]("http://ubuntuforums.org/showthread.php?t=575750") and i followed it exactly.

I installed ndiswrapper like it said.  
downloaded the bcmwl5.inf file.
I went to go blacklist BCM43xx, but it is already blacklisted in Hardy, so instead I blacklisted B43, and ssb.

I put ndiswrapper in modprobe.

I know it all worked because I also downloaded the ndiswrapper gui, and it showed me that the drivers were installed.

But I could never get it to work.

So I unblacklisted B43 and ssb, and took ndiswrapper off of the modprobe list, and then went to synaptics and downloaded the b43 fwcutter.  when it installed, it asked me if it wanted me to find and extract the files.  i said yes, but it never did anything.


and when i go to system>administration>hardware drivers, my Broadcom card doesn't even show up in the list of restricted drivers.


I'm really stumped.




-Tim

---

### Post by bilal.17 on 2008-05-02
Broadcom always has troubles in working with linux, try this guide [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

---

### Post by tentel on 2008-05-02
It worked....

I'm sitting here in shock...

I'm just worried that it won't stick.


it said that this wouldn't last past a reboot
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy #this step added Apr 27 2008
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44 #this step added May 1 2008



it said to add this to make it stick:
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper



I dunno if it worked.

when I enter that last command, the sudo tee one, nothing happens.
it is just letting me add something to the file, but i don't know what i'm supposed to put.
ndiswrapper?
then how to I close the file afterwards?


i'm scared to reboot...

---

### Post by tentel on 2008-05-02
darn, it didn't stick.

I had to retype in that temorary fix again.

anyone have any ideas?

---

### Post by tentel on 2008-05-02
the only way I canuse my wireless is to type in 
sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper



I used sudo gedit /etc/modules and added ndiswrapper, but it didn't do anything.

---

### Post by tentel on 2008-05-02
the only way I can use my wireless is to type in 
sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper



I used sudo gedit /etc/modules and added ndiswrapper, but it didn't do anything.

---

### Post by dndrich on 2008-05-02
There is something in this post that will probably work.  It has to do with editing a file and adding some lines to make it stick.  It worked for me.  There is a wirelessfix file that you modify.  Try this:

[http://ubuntuforums.org/showthread.php?t=766560&highlight=hardy+ndiswrapper](http://ubuntuforums.org/showthread.php?t=766560&highlight=hardy+ndiswrapper)

Run from step 5 on.  It looks like you did everything else before it.

---

### Post by tentel on 2008-05-02
It worked!


Many thanks.

I have been trying on and off since last november to get that card to work.

I'm in shock.
I'm delerious.


Thanks Everyone
-Tim

---


---
title: "Load module on bootup"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by nathansoz on 2008-11-02
Hi all. I need to load the ath_pci module on startup on my 8.10 box. I tried adding ath_pci to the /etc/modules list but that was a no go. But if I manually run 'modprobe ath_pci' after startup, everything is peachy. Is there something I am missing here?

---

### Post by igknighted on 2008-11-02
Are there any other modules that must be loaded first?  Maybe once everything is loaded, ath_pci can load, but in /etc/modprobe it tries to load too early?  I would try putting it in /etc/modprobe.2 through /etc/modprobe.5 so it loads for those runlevels, rather than universally.  That way perhaps it will load later.

---

### Post by nathansoz on 2008-11-02
Wait... I don't have an /etc/modprobe.5

Should I have one... or should I make a file called that. Or should I make a file called /etc/modules.5
?

---

### Post by igknighted on 2008-11-02
Oops, my bad.  I was thinking of /etc/rc*, not modprobe.  Still could be an order thing, but i'm not sure how to make it load later.

What is the file/command you used to try to make it load in /etc/modprobe?

---

### Post by nathansoz on 2008-11-03
Well I just threw ath_pci at the bottom of the list of my /etc/modules file. I dont think a command is needed as none of the other ones there had a command.

---

### Post by nathansoz on 2008-11-03
Yes, no command is needed. But it still doesn't WORK unless I type manually ```
sudo modprobe ath_pci
``` 
after login.

---

### Post by igknighted on 2008-11-03
As a workaround, you could create a script (just a file with the sudo modprobe ath_pci command) and place in /etc/rc.2 - /etc/rc.4.  This way when the system goes to the default runlevels, that module should get loaded.  I imagine this is a horribly bass-ackwards way of doing this, but it just might work for you.  Don't forget to chmod +x the file so it is executable.

---

### Post by theToolman on 2009-01-29
I have the same problem;

My Acer 3680, running Kubuntu 8.10 Intrepid has:

0a:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

And it happily works **after** I issue the "sudo modprobe ath_pci" command.  

I have also added "ath_pci" to the bottom of /etc/modules so that the module loads on boot, but it does not load on boot.

I am assuming it is attempting to load too early, but I can't confirm this or find any logging of the module barfing.  my dmesg /syslog has no errors :(

Anyone got any ideas?

---

### Post by theToolman on 2009-01-29
After spending all afternoon chasing this I finally found the solution!

It turns out that the script "/etc/init.d/module-init-tools" is the script that parses and "modprobe"s each line of "/etc/modules".  That script was configured to only be run on runlevel 5.  My Kubuntu boots into runlevel 2, so that script is never run on start!.

I have submitted a [bug report]("https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/322669") , but for those who have the same problem, you can simply move the file:

/etc/rc5.d/S20modules-init-tools

to

/etc/rc2.d/S20modules-init-tools

You can check your current runlevel with the "runlevel" command. 

At last I get **ath_pci** on boot!

---


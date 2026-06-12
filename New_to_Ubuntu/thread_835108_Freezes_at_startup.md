---
title: "Freezes at startup"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by bhitte on 2008-06-20
(specs)I'm running Ubuntu 8.04 with an unsupported wireless card, Liteon WN5301A wireless card. Uses the Atheros AR2416 chipset. Used ndiswrapper to install the driver. 

I recently switched to wireless internet. After I configured the wireless interface, my computer froze. I couldn't use the mouse or keyboard so I had to do a hard reboot. I can login and start up the gui. But after a few seconds everything will freeze, leaving me to hard reboot again. It appears that it would be a problem with the wireless startup process. Any ideas on how to fix this?

---

### Post by dark_harmonics on 2008-06-20
> **bhitte said:**
> (specs)I'm running Ubuntu 8.04 with an unsupported wireless card, Liteon WN5301A wireless card. Uses the Atheros AR2416 chipset. Used ndiswrapper to install the driver. 

I recently switched to wireless internet. After I configured the wireless interface, my computer froze. I couldn't use the mouse or keyboard so I had to do a hard reboot. I can login and start up the gui. But after a few seconds everything will freeze, leaving me to hard reboot again. It appears that it would be a problem with the wireless startup process. Any ideas on how to fix this?

This sounds like ndiswrapper may be crashing your computer. If you added ndiswrapper to your /etc/modules you should boot to the recovery kernel (at the grub bootloader screen hit escape and select the recovery option) and remove it from that file. See if your computer will boot after that. You might have to get a pcmcia wireless card that is compatible with linux to use it. Wireless support is getting better, but in a lot of cases is still a bit hacky. Not sure about the exact cause here but would suggest the above steps to troubleshoot at least.

---

### Post by ukripper on 2008-06-20
> **bhitte said:**
> (specs)I'm running Ubuntu 8.04 with an unsupported wireless card, Liteon WN5301A wireless card. Uses the Atheros AR2416 chipset. Used ndiswrapper to install the driver. 

I recently switched to wireless internet. After I configured the wireless interface, my computer froze. I couldn't use the mouse or keyboard so I had to do a hard reboot. I can login and start up the gui. But after a few seconds everything will freeze, leaving me to hard reboot again. It appears that it would be a problem with the wireless startup process. Any ideas on how to fix this?

How i have fixed this problem is completely different of what others may suggest.

I have blacklisted ndiswrapper during modules loading at bootup.

Code:

```
sudo gedit /etc/modprobe.d/blacklist
```

add  this to the file - **blacklist ndiswrapper**
save and exit.

Then open rc.local file as following, this will load ndiwrapper after boot has finished and during before login:



```
sudo gedit /etc/rc.local
```

add these two lines before **exit 0** - 
> modprobe ndiswrapper
/etc/init.d/networking restart

save and exit then reboot. see if it still freezes

 Not sure if this will fix for you too.

---

### Post by Chris Kupka on 2008-07-08
Mine was freezing on startup, as well.  After booting in recovery mode, turns out it was cos my madwifi driver hadn't compiled correctly.  After I reinstalled, the wireless worked fine and the computer starts like a charm.

If you have a 32bit, might I suggest trying the madwifi driver instead of ndiswrapper?  Many of the posts suggest that madwifi is superior - however, only ndiswrapper works for 64bit systems.

Hope this helps.

-Chris

---

### Post by tjwoosta on 2008-07-08
i had the same exact troubles the other day with ndiswrapper, here is the thread

(**dont worry about the thread name, i misdiagnosed the problem at first**, but i did solve everything)

[http://ubuntuforums.org/showthread.php?t=848641]("http://ubuntuforums.org/showthread.php?t=848641")

---


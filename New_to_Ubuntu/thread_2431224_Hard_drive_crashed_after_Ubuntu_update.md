---
title: "Hard drive crashed after Ubuntu update?"
date: 2019-11-13
forum: New to Ubuntu
---

### Post by stacey-bean on 2019-11-13
Hi there,

I recently ran an automatic update for Ubuntu and was prompted to reboot my computer to complete the update. It rebooted to a blank, black screen and has shown no signs of life since. 
I've tried rebooting in safe mode, with nomodeset, and the command "sudo apt update && sudo apt upgrade --fix-missing" -- none of it has made any difference.
I got a bootable USB of ubuntu thinking I would simply re-install the OS, but when I try to boot from the USB I get an Ubuntu loading page for about 30 seconds and then the device shuts down. I'm now running a test version of Ubuntu off of the USB, but the hard drive from the laptop itself seems to have disappeared. When I try to install the OS, it only sees the USB and says that I don't have enough space to install. I don't care if I have to wipe my computer and start over, but I don't see how I can do that if the hard drive is out. Also, I would prefer to access and back up the files on my hard dive first.

I don't understand how a regular update would render my hard drive inaccessible or what to do about it. Any help would be much appreciated. Thanks in advance!

---

### Post by TheFu on 2019-11-13
> **stacey-bean said:**
>  
I don't understand how a regular update would render my hard drive inaccessible or what to do about it. Any help would be much appreciated. Thanks in advance!

If the HDD was already dying, then writing lots of new data to it could have exceeded the limits of allowed failed sectors.

Or if the HDD controller was failing.

Or if the cable was failing .... 

The cable and disk parts can be checked by using smartctl.  Boot off a Try Ubuntu flash drive, install smartmontools, run a short test, then about 5 min later, after the test finishes, ask smartctl for a report and post the output back here if you need help interpreting the results.  I need to see the raw data column.

There are a few other smartctl threads in these forums, if you want to learn more about interpreting failures.

Sometimes bad things happen at inconvenient times. Hopefully, you have a backup from last week and those files are new enough.  Weekly backups are the minimal needed.

---

### Post by Autodave on 2019-11-13
Check cabling.  Can you feel or hear the HD spinning?  Is this an SSD or conventional spinning drive?

---

### Post by oldrocker99 on 2019-11-13
The cable is the **first** thing to check. A lot of electronic problems are caused by cables failing. In other words, blame the connectors ***FIRST!***

Even cables which have been in one position and not moved at all can suddenly fail. I had one fail during a long disk write. Changed the cable, and it came right back.

Go figure. I keep a couple of USB3 cables handy; I realize now that they're handy to have around.

---


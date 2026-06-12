---
title: "Power Cut Rescue"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Andavane on 2008-07-05
Despite all the sage advice about shutting down gracefully, powercuts and spikes do occur.
What is the best thing to do after a power cut and reboot to check whether things are reasonably all right?
Regards
John

---

### Post by Canis familiaris on 2008-07-05
Make periodic backups.
Also buy a spike guard and a UPS.

Sorry for not answering the exact question.

---

### Post by stumac on 2008-07-05
> **Anurag_panda said:**
> Make periodic backups.
Also buy a spike guard and a UPS.

Sorry for not answering the exact question.

Good advice but no need for a spike guard if a UPS is used.

When system boots after a power fail it will find it's file systems "dirty" and will automatically fsck them.  This will greatly slow the boot up so don't think it's a hang and switch it off again.

Stuart

---

### Post by Canis familiaris on 2008-07-05
> **stumac said:**
> Good advice but no need for a spike guard if a UPS is used.

I connect the UPS to Spike Guard to "Protect" the UPS. :lolflag:
One thing I forgot is also a good SMPS/PSU is needed. Lots of people buy cheap SMPS/PSU and later see their hardware in smoke.

---

### Post by sharks on 2008-07-05
using a UPS may solve ur problem.

---

### Post by Herman on 2008-07-06
> What is the best thing to do after a power cut and reboot to check whether things are reasonably all right?:) The best thing to do is refrain from rebooting right away.
Instead, boot your Ubuntu Live CD, open a terminal and run a file system check on your Ubuntu partition in your hard drive.
Here's a link explaining what commands you should run, [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem").
After the file system has been checked and repaired if needed, then you can reboot into your hard installed operating system again.

I use a UPS for all my computers, we don't have a very reliable electricity supply where I live.

---

### Post by Andavane on 2008-07-07
> **Herman said:**
> :) The best thing to do is refrain from rebooting right away.
Instead, boot your Ubuntu Live CD, open a terminal and run a file system check on your Ubuntu partition in your hard drive.
Here's a link explaining what commands you should run, [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem").
After the file system has been checked and repaired if needed, then you can reboot into your hard installed operating system again.

I use a UPS for all my computers, we don't have a very reliable electricity supply where I live.
Thank you friend - very useful!
I'm afraid I didn't do this at the time, but presume it would be Ok to do it now.
Another point: I ordered a UPS from Amazon. It is an APC. It has a CD for a program which "gracefully shuts down windows" and a USB link to enable it to do that. Hope it can be done without all that jazz? haven't booted into Windows for over a month now. When in India I used one, but I never bothered with any of the software that came with it. I just used it as a reserve power supply.
Kind regards
John

---

### Post by Herman on 2008-07-07
:) With file systems, the old saying 'a stitch in time saves nine' applies.
You can run e2fsck any time and it is quite safe and beneficial to your ext2 or ext3 file system.
I think the ext2 and ext3 file systems are good reliable file systems, I haven't had very many problems with them at all. 
Even if you do have a power failure or a sudden shut down, it doesn't always damage the file system, especially if the computer happens to be idle at the time. 
If a power failure or a sudden shutdown occurs right in the middle of an update, or while you are downloading files or otherwise writing to the hard disk, then the chances of file system damage are high.

I don't bother with the UPS programs either, if I am near my computer when there is a power failure (blackout) or out of spec power (brownout)  the UPS starts beeping and flashing an alarm, I normally just wait a minute or so to see if normal power will resume. If it doesn't then I start shutting down computers. 
I haven't even bothered until now to look and see if there's any UPS program available in Ubuntu.  
Now that you have brought the matter to my attention, I searched in Synaptic Package Manager and found [APC UPS Daemon]("http://www.apcupsd.com/"), which is installable in Ubuntu. That might be worth a try. 
> It controls and monitors the status of UPS and allows your computer to run for
a specified length of time on UPS power, and then executes a controlled
shutdown in the case of an extended power failure.Another associated program is gapcmon which is a program for apcupsd which gives you a GUI for monitoring your UPS unit(s). If you use gkrellm, there's gkrellmapcupsd which is a pluggin for displaying information about your UPS in gkrellm I think. :)
> Another point: I ordered a UPS from Amazon. [COLOR=Sienna]**It is an APC**[/COLOR]Good work! I have a different brand of UPS unit. Now I wish I had an APC! I don't see any support for my brand of UPS here in Synaptic.  :(

If you have time and you like your new APC UPS and the [APC UPS Daemon]("http://www.apcupsd.com/") works well for you, you might like to help other Ubuntu users by writing a review recommending APC USB units in [UbuntuHCL.org]("http://www.ubuntuhcl.org/") ,that's a hardware website for Ubuntu users. :)
Here are links to two reviews on APC UPSs already, 
[APC Back-**UPS** ES 525]("http://www.ubuntuhcl.org/browse/product+APC_BackbUPSb_ES_525?id=696")
[COLOR=#009900][/COLOR]
[APC Back-**UPS** RS 800]("http://www.ubuntuhcl.org/browse/product+APC_BackbUPSb_RS_800?id=706")

Regards, Herman :)

---


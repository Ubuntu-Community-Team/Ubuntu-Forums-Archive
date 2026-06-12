---
title: "Auto update caused &quot;signal lost&quot; on my screen?"
date: 2014-09-03
forum: New to Ubuntu
---

### Post by furioususer on 2014-09-03
Hey, I'm brand new to ubuntu.[B]


Specifications[/B]: 
Ubuntu 14,4 LTS (I've had it installed for about 3 weeks)
Intel® Core™ i5-3450 CPU @ 3.10GHz × 4 
Intel® Ivybridge Desktop 
64-bit

Software & updates > additional drives > no additional drives available

I have 2 harddrives:
1) SSD - Ubuntu is installed on this. The disk is used only for Ubuntu.
2) HD mechanical disk - 2 partitions: one consisting of Windows XP and the other partition is for saving personal data (I access this partition regularly through Ubuntu).


**Description of problem**
Today (wednesday) I got a notification about some new updates (among them was a kernel upgrade I believe) consisting of about 120 MB. I installed it and kept on working without any issues. A few hours later I felt the need to reboot my computer and that was when I ran in to some trouble...
My screen suddenly did not respond. It acted like it was in hibernation. I got the error msg from the screen "no signal detected" - I use a Philips LCD TV as screen. It seemed to indicate that information was not sent to the TV so I naturally suspected that there was some physical error. 

Firstly, I swiched over to my computer monitor and changed cables, but I still got the same error "no signal". I plugged in my bootable Ubuntu14 USB and rebooted but still no change. I couldn't even access the BIOS. The only thing showing up was the first screen revealing that it has detected my two drives and then it goes black "no signal".  

Secondly, I opened the computer box (or what it's called in eng), disconnected all the harddrives and rebooted, all of a sudden I got access to the BIOS. With that improvement I started to plug in only the USB-Ubuntu and it worked. 
So I shut down and started plugging in my mechanical disk too and the same error reappeared. I shut down the computer and plugged in only USB-Ubuntu again and it was working again. I plugged in the SSD disk and that worked too.
**Long story short: it works with USB-Ubuntu and with the SSD, but not with the mechanical disk. Before the update there were no problems at all.**

This seems to indicate a problem with my mechanical disk... but, I was a bit bold and plugged in the HD-cable to the mechanical disk when the computer and Ubuntu was on and suddenly I got access to the mechanical disk as well. The disk works perfectly and all my persona data is still there.

I suspect for some reason that the auto update that I installed earlier during the day is causing the problem with the disk. But I suspect that more knowledgeable people will say that it is without a doubt my mechanical disk that is at fault.... I googled a bit and found an interesting thread that seem related to my problem but nothing specifically about one disk being affected.
[http://ubuntuforums.org/showthread.php?t=2220583](http://ubuntuforums.org/showthread.php?t=2220583)
This guy seems to have almost the exact setup as me, but I did not quite understand all the lingo and tasks they tried... 



**My questions:**
[LIST=1]
[*]Do you think that the fault lies (solely) with my mechanical disk? A physical error then? 
[*]I am wondering if I should update the driver for my built-in graphic card, but I don't know exactly how... 
[*]Is there some kind of log that I can find somewhere with some magic command...? Is that a good place to start looking for clues? 
[*]Any suggestions what might be causing this? 
[*]Any suggestions to what I can try? 
[*]I want to try a system restore (like the one in Windows) to get a conclusive answer to if it was the auto update today that caused all these problems. Is this possible? I read something about it here:[ http://ubuntuportal.com/2014/02/boot-repair-tool-will-added-on-ubuntu-14-04-trusty-tahr-by-default.html]("http://ubuntuportal.com/2014/02/boot-repair-tool-will-added-on-ubuntu-14-04-trusty-tahr-by-default.html")
[/LIST]
 This program is however not installed by default in the latest ubuntu and the commands presented in the article that you can try during a live Ubuntu session did not work properly.
[B]
I am very new to ubuntu so I ask for patience and thoroughness in your answers. I would also appreciate it if you explain whatever commands and tasks you instruct; [/B]**why you want me to do it, what you are hoping to achieve. **

---

### Post by ThatBum on 2014-09-03
The drive could have failed SMART, some BIOSes refuse to POST and boot if they detect a faulty hard disk. Odd, though...the BIOS should inform you of this.

Try installing gsmartcontol with [FONT=courier new]sudo apt-get install gsmartcontol [/FONT]and running it ([FONT=courier new]sudo gsmartcontol[/FONT]) with the hard disk plugged in. See if it passes SMART.

---

### Post by hai3 on 2014-09-04
1. Maybe
2. You don't need if it is built-it GPU. I went to Intel's site and they said it is in Ubuntu already
3 idk
4no idea
5 remove cmos battery and re-plug it. sometime work
6 bad idea. but u may try

---

### Post by furioususer on 2014-09-05
> **ThatBum said:**
> The drive could have failed SMART, some BIOSes refuse to POST and boot if they detect a faulty hard disk. Odd, though...the BIOS should inform you of this.

Try installing gsmartcontol with [FONT=courier new]sudo apt-get install gsmartcontol [/FONT]and running it ([FONT=courier new]sudo gsmartcontol[/FONT]) with the hard disk plugged in. See if it passes SMART.

What's even more weird is that the disk works perfectly fine when I plug it in AFTER. If the disk was faulty, then there should be some sign about it or detected in some way when it's up and running, right? 


Anyway, I did as instructed. I wrote "sudo apt-get install gsmartcontol" and was asked to type in my password, and it ended with this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]E: Unable to locate package gsmartcontol

[/B]What gives?

---

### Post by furioususer on 2014-09-05
> **hai3 said:**
> 1. Maybe
2. You don't need if it is built-it GPU. I went to Intel's site and they said it is in Ubuntu already
3 idk
4no idea
5 remove cmos battery and re-plug it. sometime work
6 bad idea. but u may try

2. You mean you searched my exact model on Intel's site and found that answer?
5. What would that achieve exactly? Does it reset anything?
6. Why is a bad idea? 
And can I really try it after a problem has arisen? I mean, I haven't manually done any restore points before this so there is nothing to restore to. And like I said earlier, it's not integrated in to the new ubuntu, as the article suggests, so I don't even know how to go about it. But it would be nice if ubuntu had atleast some kind of "reverse" function after installing updates. Is it possible to uninstall just the recent updates?

---

### Post by grahammechanical on 2014-09-05
Please stop and think for a moment before you try things that could produce more problems.

The no signal message is an indication that the computer is not giving a signal to the monitor. But why would the OS not send a signal to the monitor? You said this

> [COLOR=#000000] felt the need to reboot my computer and that was when I ran in to some trouble... [/COLOR][COLOR=#000000]My screen suddenly did not respond. [/COLOR]

Does that mean that as you tried to shut down the screen stopped responding? Or did you reboot and get to a login screen and then to a desktop and then the OS became unresponsive and the screen gave a no signal message? Please describe the exact order of events.

When you disconnect the mechanical disk does Ubuntu load and run as normal? If so then why do you think that you need to change the graphic driver. It does not make sense.

Load into Ubuntu and plug in the mechanical disk and run the Disks utility that will read the smart information of the disk. Click the little cog icon on the top right of the application window and select Smart Data and self test.

Before you do any of that see if file Manager can access the mechanical drive and if it can start backing up your data. While the disk is still working.

If you think that a kernel upgrade cause this problem then at the Grub menu select Advanced Options for Ubuntu and then select a previous kernel from the list of kernels. The one at the top of the list is the last kernel installed. Select one of the kernels below that one. Does the problem go away? If so, keep loading that kernel until the developers patch what is wrong with the most recent kernel.

Regards.

---

### Post by ThatBum on 2014-09-05
Ah, bet you need to enable the universe repository to get gsmartcontrol, but never mind that. Seems there's a utility that can read SMART data built in to Ubuntu.

Be careful with writing data to a potentially failing hard disk, it might make the filesystem more unstable.

EDIT: Something occurred to me, the BIOS could be trying to boot the offending drive. It could have something in the MBR that the BIOS is trying to boot but hanging on. Try changing the boot priorities in BIOS.

---


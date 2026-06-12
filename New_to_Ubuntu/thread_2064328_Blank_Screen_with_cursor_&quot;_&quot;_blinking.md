---
title: "Blank Screen with cursor &quot;_&quot; blinking"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by Wolfram23 on 2012-09-29
So I just got a pretty much free PC today to use as a media server at home. It's an HP with an AMD Athelon X2 5000B. I put in 2gb of DDR2 RAM, and it's got an MSI brand Nvidia 210 GPU. I have it running off HDMI to my receiver.

Ok, so I just installed Ubuntu 12.04.1 desktop with a DVD. Don't have a clue what the partition stuff means, but following the general guide I made a 4gb swap, 150gb "/" and a 846gb "/home" partition. I was assuming I can put all my media in the /home folder...

Anyway, installation went through and it asked to restart and remove the DVD. So I did that and then the screen, after POST, goes black with the "_" cursor blinking in the top left.

I Googled the issue and it said something about the graphics drivers. I followed the instructions which were basically to put the boot disc in, and do a "nomodeset" boot off the disc. That got me into Ubunto.

Then I followed the directions here: [http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html)
and installed the drivers.

Then I rebooted, it asked to take out the DVD, I did so, and then it went back to the black screen with the "_" cursor blinking.

So then I read about the GRUB menu... supposedly you just hold Shift to get into it. Doesn't work. I tried with both a HDD boot and using the DVD.

So I got back into Ubunto off the DVD and "nomodeset" and checked the Nvidia drivers again as described in the latter link above. No dice. Shows nothing. Tried the remove commands and it said nothing found.

No idea what to do now. Please help.

---

### Post by 2F4U on 2012-09-29
> I Googled the issue and it said something about the graphics drivers. I  followed the instructions which were basically to put the boot disc in,  and do a "nomodeset" boot off the disc. That got me into Ubunto.

So you basically booted from the liveCD, but not from your installation.

> Then I followed the directions here: [http://www.noobslab.com/2011/09/nvid...0-oneiric.html]("http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html")
and installed the drivers.

You installed the drivers in the liveCD session, but not in your harddisk installation.

Besides nomodeset, there are other options that may be useful:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Wolfram23 on 2012-09-29
> **2F4U said:**
> So you basically booted from the liveCD, but not from your installation.



You installed the drivers in the liveCD session, but not in your harddisk installation.

Besides nomodeset, there are other options that may be useful:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

That is right. So I know the nomodeset option works to at least get me in, the problem is I don't know how to set it on the HDD install because I can't get into the GRUB menu. I tried holding SHIFT as well as repeatedly tapping it throughout POST and up until the screen becomes blank with the "_" blinking and it never gets into a menu of any sort.

I'm going to try the LiveCD with nomodeset option and then run the last option on the list "Boot From First Hard Disk" and see what happens...

---

### Post by grahammechanical on 2012-09-29
Here is some information on Grub 2:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

Note this point under the heading **Hidden**


> Hidden Menu Operations Not Expected (Abnormal):

The user may be able to display the menu in one or more of the following ways:

Holding down the SHIFT key early in the boot process until the menu displays.

GRUB 2 searches for a depressed SHIFT key signal during boot. If the key is pressed or GRUB 2 cannot determine the status of the key, the menu is displayed.

Pressing the ESC key during a 3 second window as GRUB 2 runs.

Once you get to the Grub menu, highlight the Ubuntu/Linux kernel and press "e" then you should be able to edit the boot parameters

Look for a line that says "ro quiet splash" at the end of it and change it to "ro nomodeset" (without the quotation marks.

Then press f10 to boot. There are some instructions at the Grub menu any way but because you only have one OS you do not normally see the Grub menu.

You should then get to a login screen. But the video mode has not been set. So, look for Additional Drivers (in the Dash) and activate a proprietary driver.

Regards.

---


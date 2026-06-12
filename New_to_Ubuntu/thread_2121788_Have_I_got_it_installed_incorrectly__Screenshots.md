---
title: "Have I got it installed incorrectly?  Screenshots"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by WesternRyno on 2013-03-03
Sorry if you guys are getting sick of me, just doing my best to get to the bottom of this.  Believe me, I'm also reading my ass off.  I will send this to a friend, but thought maybe someone here can make some valued analysis to these?  Thanks for any help.

---

### Post by drpjkurian on 2013-03-03
Please report your problem after this installation if any.

---

### Post by WesternRyno on 2013-03-03
Which installation?

---

### Post by 3rdalbum on 2013-03-03
All I can see are partitions, I can't see the contents of them.

It looks like you've formatted a partition on your SSD for the actual operating system (/), and formatted a large partition on your hard disk for your user documents (/home). You've also got some swap. That's all fine so far; all the sizes are okay. You have, however, left a fair bit of empty unallocated space on the SSD. You might want to at least resize the / partition upwards to fill the SSD so you've got extra usable space should you need it.

I can't see if you have actually put / onto the SSD or /home onto the hard disk. I can't see if you've installed Ubuntu at all. You've obviously booted from a live CD so it seems you haven't installed Ubuntu, or it's not working.

From what I can see, everything is fine. What's not letting you boot into Ubuntu?

---

### Post by WesternRyno on 2013-03-03
Yes, I definitely installed Ubuntu 12.04, I did so from a flashdrive with an ISO I got from Ubuntu.com.  When I was given the option I chose to install on the 750GB Harddisk.  It was working for a bit and then since a simple restart and I can no longer get in?  So it is not working right, and I'm not sure why.  Should those screenshots have shown you were Ubuntu was if it was indeed working correctly?

This is the third time it has done this, so I really don't know at this point if it is me or some serious compatibility issues.

Did a sudo update-grub from the flashdrive and got:

/usr/sbin/grub-prob:  error:  cannot find a device for /  (is dev / mounted?),

This seems telling to me, but I'm not exactly sure in what way.

Thanks for your help by the way

---

### Post by arpanaut on 2013-03-03
So what happened to the install from this thread?   [http://ubuntuforums.org/showthread.php?t=2121354](http://ubuntuforums.org/showthread.php?t=2121354)
Why are you trying to update grub from the live session without mounting your installed  partition?
Shut down your system, remove the flashdrive and reboot, what are the results?

---

### Post by WesternRyno on 2013-03-03
Yes, after the success from the thread you referenced, I added cairo dock, google earth, skype and then when I restarted it went to a purple screen and stayed there.  I tried a dozen times following this to boot in to no avail.  Either got a black or purple screen.
 I tried to update grub because I'm trying my best to figure this out.  I don't know why my partitioned but I'm feeling sure that it is supposed to be but am seeking answers and advice before I proceed.

When I remove the flash and try to boot, I get the blank screens mentioned.  From recovery mode I get a black screen and a cursor asking for a login.

Thanks for your questions.

---

### Post by arpanaut on 2013-03-03
Well... That sucks!
In your bios which video sysem do you have set up?
If set to Intel, it should work by default.
if nvidia you may need to set nomodset as a boot parameter until the proper driver is installed.
If set to optimus then you may need to get back to your buddy in the other thread and get things worked out.

Sorry I have none of these things on any of my systems, but hopefully someone who does know more will happen along.

Good luck!

---

### Post by WesternRyno on 2013-03-03
Hey, thanks for your reply.  In my BIOS:
USB Legacy                               Disabled
WLAN                                       Enabled
SATA Controller Mode                  AHCI (other options are Compatible or RAID)
Graphic Device                           UMA only (other option is Optimus)
Intel Virtual Technology               Disabled
Intel Rapid Start Tech
Memory Remap                           Enabled   

Any ideas, feedback or suggestions on reading are much appreciated.  Thank you.

Quick add:  I re-booted with the Intel Virtual Tech enabled and it took me to a black screen with my computer name and login followed by a prompt.  I log in, enter password and it prompts as if at a terminal.

Did a sudo update-grub which found linux images and added a boot menu entry for EFI firmware configuration and now again sits at a command prompt.

---


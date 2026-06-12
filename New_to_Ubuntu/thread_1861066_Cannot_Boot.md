---
title: "Cannot Boot"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Xanadu001 on 2011-10-15
I have been using Ubuntu 11.04 successfully for a few months now - it's a great product!  Two nights ago I decided to do software updates using the Update Manager (300 updates).  Everything appeared to be fine after updates completed.  It may have absolutely nothing to do with the updates, but the following morning I could not boot the PC.  I got a black screen with the following:

GNU Grub Version 1.99
Ubuntu, with Linux 2.6.38 - General
Ubuntu, with Linux 2.6.38 - General (Recovery mode)

The screen was asking me to select one of the lines using the up/down keys; unfortunately the keyboard and mouse were not functioning, therefore I could do nothing.

I suspect that this is not a unique problem.  Would somebody please be able to explain what I need to do to reboot the PC in simple step by step terms.  I do have the 11.04 software on a CD and have already tried a re-install (11.04 to 11.04).

Regards,

Geoff

---

### Post by Lisiano on 2011-10-15
This is... Odd. Do you have a LiveCD? Please follow this guide up to step 7 [http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/](http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/)
Instead of step 7, use this command
```
sudo update-grub
```
To open a terminal either find it in Dash or press Ctrl+Alt+T.

---

### Post by Xanadu001 on 2011-10-16
Lisiano,
Thank you very much for a prompt reply and what is probably a very useful comment. Unfortunately I wasn't able to fix my problem, almost certainly because of my own lack of technical knowledge.
1. I printed off the guide and steps 1 & 2 went OK.
2. Step 3; I don't know what I am looking for in the left hand panel as far as partitions are concerned, neither do I understand the term 'mount'.  I didn't actually think that I had a partition as when I installed Ubuntu, I thought that I had over-written the previous MS Windows software  and everything else.
3. Under the root/media file I did find a file named 
"**1dc-900fc-9bb8-43bb-a1a3-4fe5f2bbd804**".  Is this what I was looking for, described in the guide as "xx..xx"?
4. Step 4: Found Terminal OK.
5. Step 5: Tried entering the 3 commands with the above file name replacing "xx..xx".  Each time it said "command not found"
6. Step 6; Entered this command with the above file name replacing "xx..xx".  It also said "command not found"
7. I entered your suggestion of "sudo update-grub"; it responded with an error message "cannot stat 'aufs"
8. Clearly I am out of my depth here - are there any other suggestions that you have?
9.  Is it likely that this grub problem would be fixed if I did a complete full install of Ubuntu?  If so am I likely to loose the data files?

Regards,

---

### Post by arashiko28 on 2011-10-16
Since you have the Live CD, take advantage of it and backup all of your data to an external HDD. The term "mount" refers to data media, either internal HDD (partitions), external, USB, it means the device is connected and "turned on", if you choose to unmount then you "turn it off" and if external, you can remove it.

To make a backup, access the filesystem, look for your home folder and by copying that you'll have a full backup. When you re-install, if you lost all of your data, just replace the new empty home folder with the backup, and even your previous background should be back.

Best of lucks

---


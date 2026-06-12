---
title: "Autoboot grub"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by Fred Doolie on 2011-10-04
Total Linux Noob here.  I dont know if this is an Ubuntu question, a Linux question or a grub2 question. Sorry.

Is there a way to set up a one-time auto-default for grub2? Right now it defaults to Ubuntu on a 5 second timeout which is fine most of the time but sometimes I want Windows.  Being a lazy guy (pressing down-down-down-down-enter is too much work LOL) I'd like to tell Grub "The next time you reboot just default to Windows right away with no countdown. Then go back to normal" or  "Boot entry number X right away then go back to normal".

Can be done?

---

### Post by drs305 on 2011-10-04
Yes, you can issue the following command for a 'one-time' boot to a non-default selection:

[COLOR="DarkRed"]First, change the GRUB_DEFAULT=X to **GRUB_DEFAULT=saved** in /etc/default/grub.
Save the file, then "sudo update-grub"
Then:
[/COLOR]
```
sudo grub-reboot <number on the menu>
```
Example: sudo grub-reboot 2   # Remember the first entry is counted as 0
You can use the exact menuentry title as well.

To see the list of menuentries:
```
grep 'menuentry' /boot/grub/grub.cfg
```


You can check the next boot entry with
```
cat /boot/grub/grubenv
```
The next boot will be the one listed in "saved_entry="

---

### Post by Fred Doolie on 2011-10-05
Whoo hoo!  Thanks!

Now little batch files do the job for me 

"Reboot To Windows"

sudo grub-reboot 4
sudo reboot

"Reboot to Puppy Linux"

sudo grub-reboot 5
sudo reboot

and so on

I wonder what other magic Grub2 can do. Boot an ISO image? Time to learn Grub I guess.

---

### Post by drs305 on 2011-10-05
> **Fred Doolie said:**
> Whoo hoo!  Thanks!

I wonder what other magic Grub2 can do. Boot an ISO image? Time to learn Grub I guess.

:-)

Yes, it can boot ISO files if they were designed for it. The last 3 or 4 versions of Ubuntu can do this, as well as some of the other Linux variants.

You can even install from an ISO file without burning a CD.

Here is the link to a guide I wrote about ISO booting from Grub 2:
[ISO Booting with Grub 2]("http://ubuntuforums.org/showthread.php?t=1549847")

When this thread has run its course, please mark it SOLVED via the 'Thread Tools' link to the top right of the first post.

---


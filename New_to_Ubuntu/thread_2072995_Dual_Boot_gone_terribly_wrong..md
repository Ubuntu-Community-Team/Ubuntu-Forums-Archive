---
title: "Dual Boot gone terribly wrong."
date: 2012-10-18
forum: New to Ubuntu
---

### Post by gaz1990 on 2012-10-18
I've used Ubuntu in the past, had no issues, then i got a new PC a while back, and fancied having Ubuntu again, i have the 9.10 disk at the moment, tried to install that. I created a 20GB partition for it and all was going well, then upon reboot, i lost the option for WIndows 7, and it seems to have completely gone. i can't even install 9.10 fully as upon reboot it says it cannot boot from disk, or there is none. the HP recovery disk is still intact, but had an error even uses system restore on windows. Im really freaking out right now, as i dont want to have to buy another hard drive and windows 7 again, and fiddle about inside the PC. can possibly provide more info, if possible. My only option is to keep using the "trial" of ubuntu, which i dont want. is there any way to recover windows, or find the partition that it might be on? as i can access the system recovery so im guessing win 7 is still there in some sense?

---

### Post by newb85 on 2012-10-18
9.10 hit end-of-life in April of 2011.  You would be better off using a currently supported release (10.04, 11.10, 12.04, or 12.10).  But that's not the issue at hand.

Try this first:
```
sudo update-grub
```
Then reboot and see if the option is restored.
Likely won't fix anything, but it's easy and can't hurt.

Then install gparted
```
sudo apt-get install gparted
```
Run gparted and see if the Windows partition is still in tact.

If it is, you should try using Boot-repair.  [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
Boot-repair isn't packaged for releases older than 10.04, so you'll probably need to create a Live CD or USB of a newer release than 9.10.  [s]If your Ubuntu install is currently functional, you should be able to do that.[/s]

Edit: Wow, my reading skills are atrocious.  If you can create a 12.04 CD on another machine, great.  Otherwise, I'll try to come up with a way for you to install Boot Repair on a 9.10 Live session.

---

### Post by Bashing-om on 2012-10-18
does "new pc" = UEFI booting ? 
GParted will show the UEFI partition.

[INDENT]my 2 bits worth <==BDQ
 
[/INDENT]

---

### Post by scoon on 2012-10-18
Hey there, 

See if [THIS]("http://ubuntuforums.org/showthread.php?t=1014708") can help you out.

Thanks, 

Skip

---

### Post by Mark Phelps on 2012-10-19
You shouldn't have just charged blindly ahead -- as Win7 preloaded machines present a whole new set of problems when trying to set them up to dual-boot with Ubuntu.

You said Win7 is gone -- which I doubt -- but to check that, boot from an Ubuntu LiveCD, open a terminal, and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out the partitions on your drive -- so we can see if the Win7 partitions are still there.

---


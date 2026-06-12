---
title: "dd Cloning Ubu to Win7 Machine?"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by mapes12 on 2013-01-09
Here's the situation:-

- My laptop that has been running Ubu for years has started showing signs that it's about to die. It only has Ubu on it. It's my main machine.
- The HDD is fine. The fault lies with other components.
- I have another machine that has Win 7 installed as the only OS. I only use this machine for running specialist software where there is no Ubu alternative. There's loads of empty space on the HDD.
- I have my Ubu system tweaked just how I like it and would like not to have to install from scratch and apply the tweaks all over again.
- I was thinking of taking the HDD out of my laptop, popping it in an external caddy and hooking it up to the Win 7 machine via USB.
- Then, boot the Win 7 machine from a regular live Ubu CD and using the dd command to copy the laptop HDD to the free space on the Win 7 machine.
- Whilst still running the Ubu live CD to then run Boot Repair to create the Grub configuration so that I can choose between Ubu or Win 7 at normal boot up from the HDD.

Can any one see any glaring issues with my plan?

Mark

---

### Post by Michael Dooley on 2013-01-09
Please see the following forum link:

[http://ubuntuforums.org/showthread.php?p=12447278#post12447278](http://ubuntuforums.org/showthread.php?p=12447278#post12447278)

where the responder pretty much lays it out.

---

### Post by dodo3773 on 2013-01-09
If you are connecting directly I think it would be sort of a waste of time waiting on dd personally. If you just partition before hand you should be able to just rsync (something like: "rsync -aAXv /* /path/to/backup/folder --exclude={/dev/*,/proc/*,/sys/*,/tmp/*,/run/*,/mnt/*,/media/*,/lost+found,/home/*/.gvfs}") the contents of the drive to the new partition and then chroot in and re-install grub. Either way you may want to skip the mbr if you are using dd and install grub into the new mbr on the new drive. Here is a couple links:

[https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync](https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync)


[http://www.thegeekstuff.com/2010/09/rsync-command-examples/](http://www.thegeekstuff.com/2010/09/rsync-command-examples/)

All that being said I do not see any glaring issues with your plan as long as you are okay with re-installing grub to the new mbr (unless the new computer isn't mbr; in that case efi, etc..etc.. you know what I mean)

---


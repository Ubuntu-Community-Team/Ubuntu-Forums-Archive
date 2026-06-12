---
title: "[SOLVED] Help needed with the 8.04 internet and drives"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Damien Kane on 2008-06-06
So sorry to ask about this. I took the leap and installed the new 8.04 from scratch and have a few puzzles, and I'm really hoping someone can help!

I installed the 8.04 LTS desktop version.

1. I can no longer connect to the internet. I have a Realtek ethernet which I understand had a lot of problems before. I sorted it out for the 7.10 but can't figure out how to do it for the 8.04. How can I get the new Ubuntu to recognise my hardware and get me connected?

2. When I boot up, there are no drives. I can manually get to them by clicking on Places -> then the drive. They used to be on my desktop. I read about an 'automount' to fix the problem but now, my head hurts. How can I automount my drive?

I hope someone can help me! It's a completely fresh install.

---

### Post by Gourgi on 2008-06-06
> **Damien Kane said:**
> So sorry to ask about this. I took the leap and installed the new 8.04 from scratch and have a few puzzles, and I'm really hoping someone can help!

I installed the 8.04 LTS desktop version.

1. I can no longer connect to the internet. I have a Realtek ethernet which I understand had a lot of problems before. I sorted it out for the 7.10 but can't figure out how to do it for the 8.04. How can I get the new Ubuntu to recognise my hardware and get me connected?

2. When I boot up, there are no drives. I can manually get to them by clicking on Places -> then the drive. They used to be on my desktop. I read about an 'automount' to fix the problem but now, my head hurts. How can I automount my drive?

I hope someone can help me! It's a completely fresh install.

about the second one, basically you have to edit /etc/fstab and add some parameters into it about the device you want to automount
after editing this reboot or 
```

sudo mount -a

```
please read this for the required paraneters [http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab](http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab)

---

### Post by didac on 2008-06-06
Type in a terminal:

```
sudo gconf-editor
```

Navigate to apps/nautilus/desktop and check volumes_visible


As for your Realtek, start a new thread and post the results of 

```
sudo /bin/lspci
```

---

### Post by talktoari on 2008-06-06
For your automounting problem, I found some solution steps:

The command to manually mount a NTFS filesystem from command line is;

sudo mount -t ntfs /dev/sda1 /media/sda1

Of course /dev/sda1 refers to the NTFS filesystem you want to mount and it most likely is different for different installations.

To automount the same drive you would have to edit your /etc/fstab file and add the entry;

/dev/sda1 /mnt/sda1 ntfs users,defaults,umask=000 0 0

You obviously have to have mounted the NTFS Filesystem once before to identify the proper drive number sdax – assuming it’s a SATA drive, if it’s IDE it will show up as hdax.

The "users" option allows anyone to mount/unmount the drive and overrides the default , which is that only root is allowed to mount/unmount.

The value of the permission bits used with umask are the opposite of those used with the chmod command. For example, the following pairs are equivalent:

umask=000 and chmod 777
umask=022 and chmod 755

If you restarted windows uncleanly, meaning you will need to run scandisk at the next startup, the NTFS Filesystem drive won’t automount.  Run this command;

Hope this helps for automounting.

---

### Post by Dutch70 on 2008-06-06
not sure about mounting anything, but I had the same problem 24 hrs ago. 

here's the message that helped me solve mine, also realtek.


Quote
"I had a similar experience when I made some changes. I lost my access to the internet and the twin monitors showed up on the task bar, instead of the connection meter. I found that going back into the router setup and making sure the network data, password, type of security, etc. were exactly the same on the Ubuntu laptop. Once that happened, it worked."

Good luck

---

### Post by Damien Kane on 2008-06-06
The box for volumes_visible was already checked. I thought Ubuntu would mount hard drives automatically as it does for 7.10. I don't understand why Ubuntu got harder to use for simple tasks (from a novice point of view). I just want to use my hard drive when I turn the computer on, and use the internet.

Thanks for all the help, I seriously appreciate it, but I think I'll downgrade and try the next release.

Cheers anyhow

---


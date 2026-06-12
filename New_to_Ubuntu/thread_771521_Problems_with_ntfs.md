---
title: "Problems with ntfs"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by jimjesus on 2008-04-27
So I just got ubuntu hardy installed on my computer and I want it to automatically mount all my ntfs partitions at boot. But when I reboot and login they show up, but I have to mount them again. How do I keep them from unmounting everytime I reboot?

---

### Post by Joeb454 on 2008-04-27
Search synaptic for ntfs-config, or open a terminal and install it by using ```
sudo aptitude install ntfs-config
```

I think it then lives in Applications>System Tools.

If it's not there, then it's Applications>Other

---

### Post by jimjesus on 2008-04-27
Hmm that didn't seem to help. When I log on, all my partitions show up in my "places" dropdown menu. But I have to click them once, and nothing happens but the icon changes and the drive then shows up on my desktop. If I click again, it actually opens a file browser of the drive. I don't want to have to click on them everytime I reboot to get them to show up.

---

### Post by Joeb454 on 2008-04-27
If you have ntfs-config installed you need to run it (should've mentioned that part :p)

And you can then tell it what drives to auto-mount, it's very simple to use :)

---

### Post by jimjesus on 2008-04-27
Well I did run it and all it did was give me two check boxes for write support on internal and external drives.

---

### Post by Joeb454 on 2008-04-27
make sure your drives are not currently mounted then try again...It works for me :confused:

And you need to make sure Write Support For Internal Drives is checked :)

---

### Post by jimjesus on 2008-04-27
Everything is now in working order with my windows partitions. Thank you.

---

### Post by Joeb454 on 2008-04-28
No problem :D Glad it worked :)

---


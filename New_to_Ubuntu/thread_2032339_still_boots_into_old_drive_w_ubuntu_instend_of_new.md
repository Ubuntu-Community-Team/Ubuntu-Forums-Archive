---
title: "still boots into old drive w/ ubuntu instend of new drive w/ubuntu"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by PineappleCore on 2012-07-23
I had ubuntu on a small partition and it is now totally full. I got a new drive and installed ubuntu on there but it wont boot into that installation. 

It's not an option on the boot menu.

---

### Post by drs305 on 2012-07-23
You can try running "sudo update-grub" just to ensure Grub looks for your new OS. If it finds it GRUB should add it to the menu. I understand you want it to boot from the new installation, but this at least may make it accessible.

Please install Boot Repair and click the Recommended Repair button. It might solve the issue. If it doesn't, there is an option to run a boot info script. Post the link to, or the content of, the file it generates so we can see what is happeing with your system. 

Added: The link to BR is in my signature line.

---

### Post by drudogg76 on 2012-07-23
Total newbie here.. so not sure if this would work but...

What I might be tempted to do is unhook the old drive, and re-install Ubuntu on the new drive, make sure grub is booting into the new drive (which I'm sure it would do then), then re-attach your old drive and define it in "fstab" as another drive separate to the OS.

I don't know.. maybe that's just the long way to do it.. I'm sure someone here might have an easier way...

---

### Post by lakona on 2012-07-23
Did update-grub work for you?

I find that the boot-repair gui works, but is not a precise tool. Maybe I can help if you are still having trouble.

---

### Post by Bucky Ball on 2012-07-23
Boot into the old install, 'sudo update-grub' should pick it up, as dr mentioned. 

If you follow drudogg76's idea, you don't need to diddle with the fstab. After the reinstall, again, just run 'sudo update-grub' with the old drive plugged back in and that should pick up the old install and add it. Be reminded, though, that this will change things. Your old drive, sda, will now be seen as sdb and vice versa. ;)

---

### Post by PineappleCore on 2012-07-25
This totally worked niice thanks!

---

### Post by Bucky Ball on 2012-07-25
Great news! Enjoy! ;)

---


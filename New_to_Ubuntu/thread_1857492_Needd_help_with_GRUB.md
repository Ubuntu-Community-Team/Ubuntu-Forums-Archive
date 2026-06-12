---
title: "Needd help with GRUB"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by Djalmahal on 2011-10-10
I installed 11.04 on my friends EEE Pc and after that Windows and Ubuntu booted nicely. My friend asked e then to set it up in a way that Windows boots automatically so I changed etc/default/grub and then ran sudo update-grub

Now the normal Windows is not showing up anymore in the GRUB-menu only the Windows Recovery
Also the Windows Partition shows up as empty!!!

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda2
done


How can I force GRUB to redicover the normal Windows and what happened?

Thanks

---

### Post by Djalmahal on 2011-10-10
I just checked and I made a mistake in Windows recovering it and in that process wiping it off so that's it. Ignore the above mistake.

---

### Post by 2F4U on 2011-10-10
You should then mark this post as solved.

---


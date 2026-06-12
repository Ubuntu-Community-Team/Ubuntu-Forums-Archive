---
title: "How to Change GRUB Settings"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Kymac on 2008-11-23
I am currently running Ubuntu 8.10 on this computer.  About a week ago, I started installing WindowsXP, however, I forgot that it will cause my computer to boot directly into the WindowsXP partition.  Therefore, I unformatted my Windows partition, and replaced it with Linux Mint (it was the closest Live CD I had on hand).  

However, now whenever I wish to boot into my primary Ubuntu partition, I have to wait until I get to the Linux Mint GRUB screen and switch the selection to booting with Ubuntu 8.10.

Is there a simple setting for GRUB that will allow me to switch my first boot priority to my Ubuntu partition, as well as allowing me to delete the Linux Mint partition I am not using?

Thank You,
-Kymac

---

### Post by beanhead on 2008-11-23
ok just go in to Ubuntu open a terminal and type 

sudo gedit /boot/grub/menu.lst  below is the boot order for my hard drive you will see this list near the bottom of your /boot/grub/menu.lst file 
MAKE SURE YOU SAVE A COPY BEFORE EDITING :D just edit so the top list is Ubuntu and you can remove the mint section by just erasing it from the grub.lst . as for erasing it from the hard drive id say just use your partition editor in your Ubuntu or you could use the live CD partition editor.










title		Linux Mint (Light Edition), kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3d4984f5-8bfd-4ea1-bd9c-3befd853a792 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Linux Mint (Light Edition), kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3d4984f5-8bfd-4ea1-bd9c-3befd853a792 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint (Light Edition), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title           Crappy xp
root            (hd0,1)
                makeactive
                chainloader   +1

---

### Post by adult swim on 2008-11-23
you might want to have a look at this thread [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
when you installed linux mint, it over wrote your initial grub setup from your ubuntu install.  if you delete the linux mint partition your computer isnt going to boot anything.  the link i gave you will show you how to restore grub with your ubuntu partition.  once you do that you can delete your mint partition with no problems.  if you have any questions on that post back.

---

### Post by Kymac on 2008-11-23
Thanks to both of you.

I ended up using the approach in adult swim's link (only because the menu.lst file was blank.  It worked perfectly, and now I boot into Ubuntu's GRUB.

Thanks Again,
-Kymac

---


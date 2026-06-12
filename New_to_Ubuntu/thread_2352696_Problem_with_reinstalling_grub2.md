---
title: "Problem with reinstalling grub2"
date: 2017-02-14
forum: New to Ubuntu
---

### Post by forisonex on 2017-02-14
[COLOR=#111111][FONT=Ubuntu]Please help me! So for some reason i realised that my gui was gone (i turned on my laptop and memtest popped out and was still there forever) so after some searching i understood that i have to reinstall grub2.I downloaded ubuntu live cd , put it in a usb stick and booted from there. i opened the terminal and i followed these steps from here : [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo mount /dev/sda1 /mnt
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo mount --bind /dev /mnt/dev && sudo mount --bind /dev/pts /mnt/dev/pts && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo chroot /mnt[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]grub-install /dev/sda[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]grub-install --recheck /dev/sda[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]update-grub
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]exit && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]grub install messages were ok
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]i restarted the laptop,change boot priority and ended up in a error ''Can't find command 'fwsetup' '' ...And i did it again and i saw that after the '' grep-update'' i came up with a warning : Setting GRUB_TIMEOUT to a non-zero valuewhen GRUB_HIDDEN_TIMEOUT is set is no longer supported.Adding boot menu entry for EFI firmware configuration.done . Is this responsible for that ? What is wrong???
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any advice is appreciated[/FONT][/COLOR]

---

### Post by RobGoss on 2017-02-14
You can run the boot repair tool in order to reinstall the Grub boot loader, please see my** sig **for the link follow the instructions as documented

---

### Post by UltimateCat on 2017-02-14
Hi:

If you have the Ubuntu Live CD that you installed your os with you can boot to that live and re-install Grub that way as well.

```

[LIST]
[*]Insert your Ubuntu  CD, reboot your computer and set it to boot from CD in the BIOS and boot  into a live session. You can also use a LiveUSB if you have created one  in the past.
[*]Install and run Boot-Repair.
[*]Click "Recommended Repair".
[*]Now reboot your system. The usual GRUB boot menu should appear.
[/LIST]


```

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If that doesn't work you can manually install Grub.

```
   	 	 	 	   Login with Live CD or usb as root
Find out linux disk with fdisk -l
mnt it 
mount /dev/sda /mnt  (sapce after mount and a space after sdx
To Recover
grub-install –root-directory=/mnt /dev/sda  
```

[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

Hope that helps.;)

---

### Post by forisonex on 2017-02-15
As i posted at the beginning i tried to install grub2 with the instructions i pasted and it didnt work.ill try now to run boot repair and ill post what happened..thanks for the replies guys!

---

### Post by forisonex on 2017-02-15
> **RobGoss said:**
> You can run the boot repair tool in order to reinstall the Grub boot loader, please see my** sig **for the link follow the instructions as documented
bro i just run boot-repair and everything went smooth to normal! thanks a lot for the tip!

---

### Post by RobGoss on 2017-02-15
Awesome I love it when things work out, if you have resolved your issue you can mark this thread as solved. Please use the Thread tool tab at the top of this post

Have a great day

---


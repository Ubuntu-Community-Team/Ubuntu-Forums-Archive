---
title: "Edit boot order"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Gael33 on 2008-11-01
As a newbie to Ubuntu I have not yet come to terms with the concept of terminal commands ... learning fast though :)
I recently upgraded to Ubuntu 8.10 and now my pc wont boot from the first two lines in the grub menu. I have to manually scroll down to the third line and hit enter to boot-up.
Is there a way to remove the first two lines so my computer will boot-up without my intervention?
Thanks in advance.
gael.

---

### Post by ichigo on 2008-11-01
If the two entries belong to another kernel (probably an hardy kernel), you should be able to uninstall the kernel files via synaptic. This should also remove the entries in the boot loader. Just search for the kernel version and remove anything that has the old kernel number in its name...


Only in case this doesn't work, you can still remove the two entries by editing /boot/grub/menu.lst as a root.
make a backup first:
```
sudo cp /boot/grub/menu.list /boot/grub/menu.list.backup
```
Open /boot/grub/menu.list
```
gksudo gedit /boot/grub/menu.lst
```
scroll down and look for the entries you don't need anymore and delete the corresponding passage. Save the file and reboot...

---

### Post by Ryadt on 2008-11-01
Do ```
gksu gedit /boot/grub/menu.lst
```
You will see something like this but in full:
> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

Change the default value from 0 to 2.

---

### Post by bumanie on 2008-11-01
Odd error, but you can go to the menu list and put a # in front of the entries you don't want appearing. To get the list up > gksudo gedit /boot/grub/menu.lst. Ensure you save after editing. It is probably a good idea to make a copy of your menu list before editing it, just in case something goes wrong. > sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

---


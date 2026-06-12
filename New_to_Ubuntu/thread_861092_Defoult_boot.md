---
title: "Defoult boot"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Mitnick on 2008-07-16
well when my computer boots, it boot ubuntu first.

is there a possbility to change the boot, to make windows xp start up first?

---

### Post by benfindlay on 2008-07-16
Yes, you need to edit the menu.lst file. First of all, boot the computer and look at the options in the list. Count down from the top and work out how far down Windows is in the list; either start counting at zero, or count normally and take 1 off.

Open a terminal and type ```
sudo gedit /boot/grub/menu.lst
```
Now look for the following section (near the top)
> 
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

Change the 0 in > default         0 to whatever number you got for windows above.

Hope this helps!

---

### Post by Kevbert on 2008-07-16
Yes.  You can do this by editing the menu.lst file.  Open up Terminal and enter
```
sudo gedit /boot/grub/menu.lst
```
Now you need to look for your Windows XP bootline:
```
title		Windows 95/98/NT/2000
```
Next you need to count from zero the number of times 'title' (without the #) occurs till you get to the windows OS.  So for a standard system with just one Ubuntu kernel and windows the number would be 4.
Now look for the line 
```
default 0
```
and change the line to 
```
default 4
```
Save the file and exit the editor.
When you reboot Windows should be the OS that runs by default.

---

### Post by Mitnick on 2008-07-16
oh thanks for the fast answer :D



well i got a wierd problem dont know whats goin on, am booting up Ubuntu and something wierd poped up:




BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Build-in shell (ash)
Enter 'help' for a list of built-in commands.

(initframfs) _





well i just made a ext3 partition and installed ubuntu on it.

and i reboted the pc, and booted linux it started to load. and this wierd text poped up : / ive got the same problem on my laptop.

---


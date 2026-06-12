---
title: "how to change boot order"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by bcbotha on 2008-11-22
i'm running ubuntu 8.04 and decided to dual boot with open suse. i want to uninstall suse and dual boot with Vista Ultimate. the problem is that i think my boot order is set to boot off the suse partition. i want to be able to choose between only ubuntu and vista

---

### Post by beercz on 2008-11-22
Edit /boot/grub/menu.lst
> 
sudo gedit /boot/grub/menu.lstYou can then change the order of the boot options.

[SIZE=2][COLOR=Black]**Take a backup of this file first though - in case you mess it up!**[/COLOR][/SIZE]

---

### Post by c_o_c_a_s on 2008-11-22
May be this will help you:

[http://ubuntuforums.org/archive/index.php/t-77030.html](http://ubuntuforums.org/archive/index.php/t-77030.html)

Regards

---

### Post by lswest on 2008-11-22
if you want a GUI:

```
sudo apt-get install startupmanager
``` and find the program under System-->Administration-->Startup Manager and you can choose what the default boot option is.

Or the command line way:
```
gksudo gedit /boot/grub/menu.lst
``` and find the default 0 option and change it to the right entry (it starts counting at 0, so entry 5 would be default 4, etc.)

**Since it seems you want to remove Suse and install Vista/use that, you'll need to (after removing SUSE) re-install Ubuntu's GRUB** (well, you can continue using SUSE's but it's more confusing).  Instructions are here: [http://lswest-ubuntu.blogspot.com/2008/06/installing-bootloader-how-to.html](http://lswest-ubuntu.blogspot.com/2008/06/installing-bootloader-how-to.html)
The instructions (gist of them):
> For GRUB restore to MBR:
boot to the LiveCD (this is the easiest way IMHO) and then start a terminal (applications-->accessories-->terminal)and type:

```
sudo grub
find /boot/grub/stage1
root (hd?,?)
setup (hd?)
quit
```
where the (hd?,?) and (hd?) corresponds to the output of find /boot/grub/stage1 (first time round the (hd?,?) stands for the drive (hd?) and the partition (,?) at which Ubuntu (or any Linux) is located, and then the second time round (hd?) just stands for the drive, for the MBR).


---

### Post by caljohnsmith on 2008-11-22
Deleted; didn't see lswest's post above.

---


---
title: "Grub advanced options displaying dozen repeated  options"
date: 2023-08-09
forum: New to Ubuntu
---

### Post by ono2000 on 2023-08-09
I got 3  Linux OS in my hard disk ( Xubuntu , Lubuntu and Mint )  . All three systems work very well. But this morning , I went to choose and try to use an older kernel version  and was surprised by this :
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292577&stc=1[/IMG]

Lubuntu and Mint  has the same problem as showed above . 

   But  Xubuntu  has NO problem as it  showed dow here :
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292578&stc=1[/IMG]

I tried  "[B]sudo update-grub"  ,  but with no luck . 

[/B]When I try  " dpkg --list | grep -e "linux-image" "  .   It shows what it should look like in Grub  ,  as it showed down here  :
**ono@ono-A320MH:~$ dpkg --list | grep -e "linux-image" **
ii  linux-image-5.15.0-76-generic              5.15.0-76.83                               amd64        Signed kernel image generic
ii  linux-image-5.15.0-78-generic              5.15.0-78.85                               amd64        Signed kernel image generic
ii  linux-image-generic                        5.15.0.78.75                               amd64        Generic Linux kernel image

---

### Post by #&amp;thj^% on 2023-08-09
First this is not how I would use any linux system >>>Triple Boot...
But I come in peace so can you show us this please:
```
apt policy os-prober
```
Along with:
```
cat /etc/default/grub
```

---

### Post by ono2000 on 2023-08-09
Thanks for the reply :

I forgot to add , that the System I use daily  the most is Mint. Lubuntu  I use very little . And Xubuntu has been for more than 3 months that I  practically don't use anymore. If my memory is still good  , I think I  installed it in order : Xubuntu , Lubuntu and Mint .  Right now , I'm using  Mint . 

> **1fallen said:**
> First this is not how I would use any linux system >>>Triple Boot...
But I come in peace so can you show us this please:
```
apt policy os-prober
```
s-prober:
  Installed: 1.79ubuntu2
  Candidate: 1.79ubuntu2
  Version table:
 *** 1.79ubuntu2 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
        100 /var/lib/dpkg/status

Along with:
```
cat /etc/default/grub
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by #&amp;thj^% on 2023-08-09
what about "os-prober"?
```
apt policy os-prober
os-prober:
  Installed: 1.81ubuntu2
  Candidate: 1.81ubuntu2
  Version table:
 *** 1.81ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by #&amp;thj^% on 2023-08-09
Never mind i see it now, can you open a terminal now on Mint only, so if your not currently in Mint reboot to it.
Now run:
```
sudo nano /etc/default/grub
```
and at the bottom add this:
```
GRUB_DISABLE_OS_PROBER=false
```
Then update grub
```
sudo update-grub
```
The reason for selecting Mint is that is your go to OS from what you said so far.

---

### Post by ono2000 on 2023-08-09
> **1fallen said:**
> Never mind i see it now, can you open a terminal now on Mint only, so if your not currently in Mint reboot to it.
Now run:
```
sudo nano /etc/default/grub
```
and at the bottom add this:
```
GRUB_DISABLE_OS_PROBER=false
```
Then update grub
```
sudo update-grub
```
The reason for selecting Mint is that is your go to OS from what you said so far.

Sorry , but I'm very low little knowledge in Linux ,  After inserting the code how should I save it?
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292579&stc=1[/IMG]

---

### Post by #&amp;thj^% on 2023-08-09
Glad you showed that, you placed it wrong, clearly said the bottom of that file.
No matter just close that terminal with Key [Ctrl + x]
if it asks to save it press "n" and enter.
What Desktop on Mint? Mate/Cinnamon?

---

### Post by ono2000 on 2023-08-09
I rebooted , but unfortunately , it is still the same . 
Im using  Mint Mate 
After saving the code ,  I did "sudo update-grub"  and rebooted , and checked the Grub Menu , but still the same . 

.[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292580&stc=1[/IMG]

---

### Post by #&amp;thj^% on 2023-08-09
It looks like one of the other Ubuntu Flavors might be the culprit then.
This is why we no longer suggest or hint to dual boots or in this case a Triple whammy.
In Mint, and I'm trying to be very user friendly so be aware of that.
Mint run this and copy and paste back the return please:
```
sudo os-prober
```
To copy from the terminal mouse to the beginning of the shown output and left click and hold pulling the mouse to highlite the text needed then right click copy or key combo [Ctrl + Shift + C]:
mine looks like:
```
&#9492;&#9472;> sudo os-prober
[sudo] password for me: 
/dev/sdc1:Linux Lite 6.2 (22.04):Ubuntu:linux
/dev/mapper/vglinux-root:Linux Lite 6.4 (22.04):Ubuntu1:linux

```
That's not a Dual Boot it's just a part of my set-up, they are Two different Drives. :)

---

### Post by ono2000 on 2023-08-09
> **1fallen said:**
> It looks like one of the other Ubuntu Flavors might be the culprit then.
This is why we no longer suggest or hint to dual boots or in this case a Triple whammy.
In Mint, and I'm trying to be very user friendly so be aware of that.
Mint run this and copy and paste back the return please:
```
sudo os-prober
```
To copy from the terminal mouse to the beginning of the shown output and left click and hold pulling the mouse to highlite the text needed then right click copy or key combo [Ctrl + Shift + C]:
mine looks like:
```
&#9492;&#9472;> sudo os-prober
[sudo] password for me: 
/dev/sdc1:Linux Lite 6.2 (22.04):Ubuntu:linux
/dev/mapper/vglinux-root:Linux Lite 6.4 (22.04):Ubuntu1:linux

```
That's not a Dual Boot it's just a part of my set-up, they are Two different Drives. :)
It gives me that :

[B]ono@ono-A320MH:~$ sudo os-prober
/dev/sda1:Ubuntu 22.04.3 LTS (22.04):Ubuntu:linux
/dev/sda3:Ubuntu 22.04.3 LTS (22.04):Ubuntu1:linux

Linux Mint that I'm using right now is in sda8 .  Its  stranger  that is not showing with this command  .

[/B]> **1fallen said:**
> It looks like one of the other Ubuntu Flavors might be the culprit then.
This is why we no longer suggest or hint to dual boots or in this case a Triple whammy.
Yes ! I didn't knew  that ! I was thinking of deleting Xubuntu. For that it would be enough for me to delete the Xubuntu partition using Gparted ?

---

### Post by #&amp;thj^% on 2023-08-09
> **ono2000 said:**
> 

Linux Mint that I'm using right now is in sda8 .  Its  stranger  that is not showing with this command  .

Yes that is very strange, dose the boot screen look the same as when you first installed Mint? (Or is it different now)

---

### Post by ono2000 on 2023-08-09
> **1fallen said:**
> Yes that is very strange, dose the boot screen look the same as when you first installed Mint? (Or is it different now)

When there were only 2 flavors (Xubuntu and Lubuntu), I remember that Grub was normal and always in the "advanced options for ubuntu " the kernels appeared all correctly numbered with their versions. But when I installed Mint , to be honest , I never got into the advanced option . But anyway. As long as it doesn't affect system security for me it's ok to use like this. Thank you for your help .

---

### Post by #&amp;thj^% on 2023-08-09
> **ono2000 said:**
> When there were only 2 flavors (Xubuntu and Lubuntu), I remember that Grub was normal and always in the "advanced options for ubuntu " the kernels appeared all correctly numbered with their versions. 
That explains a lot for me, which ever was first installed first Xubuntu or Lubuntu is handling grub then.
keep good back-ups of the things you want to keep. You could be good for months and months, or a boot disaster could be just around corner.
Good Luck

---

### Post by grahammechanical on 2023-08-10
This may help. Then, again it may not.

How do you update/upgrade? In Ubuntu and related distributions such a Lubuntu & Xubuntu if we update using the terminal and a new Linux kernel is installed it gets put to the top of all the previous Linux kernels that have been installed. It becomes the default Linux kernel to boot from. Older kernels are not removed until we run

```
sudo apt autoremove
```

If we update/upgrade by means of Software Updater then at the end of the update/upgrade process the autoremove command is run by Software Updater. It will remove all old kernels except the new kernel and the kernel it replaces. So, that there are always two kernels to choose from and we do not have a large collection of Linux kernels taking up space. I cannot comment on how things are done in Linux Mint.

Try loading each Linux distribution and running the autoremove command. Then load into the distribution you think is in charge of Grub and run

```
sudo update-grub
```

That may produce a cleaner Advanced Options selection. It will certainly remove the Ubuntu kernels. It may not have any affect on Linux Mint. I just do not know.

You will have to load each distribution and run that command to update the distribution's Grub configuration file. Keep in mind that sometimes it is Grub itself that is upgraded. When that happens Grub is re-installed to EFI system partition and whatever distribution this is happening on will then take charge of the Grub boot menu.

To put your favourite distribution back in charge of the boot menu you will need to load into your favourite OS and run this command.

[code]sudo grub-install /dev/xxxx   = the boot partition ID. Such as sda1 for old style hard drives or something like /dev/nvme0n1p1 for the modern Nonvolatile Memory Express solid state drives.

The Ubuntu Disks utility will show that ID label.

Regards






Regards

---


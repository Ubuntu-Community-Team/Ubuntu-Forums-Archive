---
title: "Need Help With CrunchBang Linux"
date: 2009-01-31
forum: Other OS Talk
---

### Post by RookieUbuntuUser58 on 2009-01-31
I'm setting up a quad boot with Grub Bootloader being my main bootloader (from my Ubuntu 8.10 install). Well I decided to add CrunchBang Linux to my system. I setup the bootloader to be installed to the CrunchBang partition (as I didn't want to mess up my original Grub Boot Loader). I added CrunchBang to the original Grub Bootloader (in Ubuntu). I click on CrunchBang in the original Grub bootloader and it takes me to another Grub bootloader. There, there is a bunch of Ubuntu versions (different kernels) and Windows XP, no sign of CrunchBang. I click the first Ubuntu option and it loads CrunchBang.

Now obviously I have to edit the Grub bootloader in CrunchBang to fix this. Unfortunately when I put the code

sudo gedit /boot/grub/menu.lst

into terminal, it says sudo gedit command not found.

Being new to CrunchBang what would be the terminal code to edit the menu.lst to fix my problems? 

I tried going through text editor but I dont have the permission. Another thing I tried putting "su" into terminal to become root and enter my password (correctly) but it says authorization failed.

---

### Post by LinuxGuy1234 on 2009-01-31
> **boost3d23 said:**
> I'm setting up a quad boot with Grub Bootloader being my main bootloader (from my Ubuntu 8.10 install). Well I decided to add CrunchBang Linux to my system. I setup the bootloader to be installed to the CrunchBang partition (as I didn't want to mess up my original Grub Boot Loader). I added CrunchBang to the original Grub Bootloader (in Ubuntu). I click on CrunchBang in the original Grub bootloader and it takes me to another Grub bootloader. There, there is a bunch of Ubuntu versions (different kernels) and Windows XP, no sign of CrunchBang. I click the first Ubuntu option and it loads CrunchBang.

Now obviously I have to edit the Grub bootloader in CrunchBang to fix this. Unfortunately when I put the code

sudo gedit /boot/grub/menu.lst

into terminal, it says sudo gedit command not found.

Being new to CrunchBang what would be the terminal code to edit the menu.lst to fix my problems? 

I tried going through text editor but I dont have the permission. Another thing I tried putting "su" into terminal to become root and enter my password (correctly) but it says authorization failed.

1. su requires the "root" password, enter that instead.
2. Do this:
```
su -c "vim /boot/grub/menu.lst"
```
Then press I, then make the change, press Ctrl and C, then type ":wq" (without quotes).

---

### Post by albinootje on 2009-01-31
> **boost3d23 said:**
> 
sudo gedit /boot/grub/menu.lst

into terminal, it says sudo gedit command not found.


Try :
```

sudo nano /boot/grub/menu.lst

```
If nano is not there, install it with "sudo apt-get install nano".

---

### Post by RookieUbuntuUser58 on 2009-01-31
Thanks those suggestions worked. I used albinootje method as it seemed easier. 

What do you mean root password? I thought my root password was my password (only added one password to that distro). I thought I was the root user, just had to use my password to use it.

---

### Post by albinootje on 2009-01-31
> **boost3d23 said:**
>  What do you mean root password? I thought my root password was my password (only added one password to that distro). I thought I was the root user, just had to use my password to use it.

In the past all Linux distributions used a root password, and not sudo by default. Ubuntu is probably the first well-known Linux distribution who switched to using sudo by default.
(Even "Debian stable" still doesn't use sudo by default).

See here for more information : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by snowpine on 2009-01-31
Crunchbang is based on Ubuntu, and as such, uses sudo by default, instead of a root password.

---


---
title: "Install Ubuntu instead of Mint"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by Donalddawg on 2011-09-17
:confused:I have  a desktop PC dual booting Linux Mint Windows 7.  I am trying to replace the Mint with Ubuntu 11.04 but seem to only have the option to replace the whole hard drive or install Ubuntu alongside Mint.

---

### Post by aura7 on 2011-09-17
When you are installing ubuntu you can select the drive where mint is previously installed and then format it and then install ubuntu in it.

You have to do this in by selecting manual mode of selecting partitions while installing.

---

### Post by Donalddawg on 2011-09-17
Tried this yesterday but unsure if it would work and didn't want to go ahead until I was sure.  Thanks

---

### Post by coffeecat on 2011-09-17
Welcome to the forum!

In 11.04, the manual/advanced mode is called "something else". Do post back if you need help with any part of that.

---

### Post by Donalddawg on 2011-09-17
Tried this again.  Attach screenshot and I assume it is SDA 5, 6 & 3.

When I try to install I get message advising that I haven't set up Root.

Been using Linux for a while but only on a sole booting machine - first attempt at dual booting!!!

---

### Post by coffeecat on 2011-09-17
Highlight your Mint root partition (that looks to be sda5, but check that). Now click on Change. Select your preferred filesystem type (go for ext4), tick the format box and select '/' (root) for mountpoint. OK that. You don't need to do anything for the swap partition - the installer picks that up automatically.

If you want the installer to set up mount points for any of your NTFS partitions, you can do the same, but **don't** mark them for formatting (!!), obviously choose ntfs for "use as" and specify a mount point. Whoops - just remembered that there's a bug in the installer that prevents you from entering a custom mountpoint by typing directly in the mountpoint field. You have to be in the live desktop session with the installer run in the desktop, rather than booting straight to the installer. Then you have to type your mountpoint in gedit and copy and paste it into that mountpoint field with a bit of deft mouse left and right clickery.

A suitable mountpoint would be /media/whatever. Change whatever! :)

---

### Post by Donalddawg on 2011-09-17
Thanks.  Just off to try now.  If I don't post again all gone OK - or PC kaput!

---

### Post by madjr on 2011-09-17
here you go (partitioning guide):
[http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/)

---

### Post by gandaran on 2011-09-17
> You have to be in the live desktop session with the installer run in the desktop, rather than booting straight to the installer. Then you have to type your mountpoint in gedit and copy and paste it into that 
clicking the drop-down box and choosing  the preset "/windows" then you can edit the option has worked for me
> A suitable mountpoint would be /media/whatever. Change whatever
I use this setup, keeps all drives neatly mounted on one system folder. 
**/windows/loader** for the windows 7 boot loader partition
**/windows/system** for the C drive
**/windows/data** for the D drive

---

### Post by coffeecat on 2011-09-17
> **gandaran said:**
> clicking the drop-down box and choosing  the preset "/windows" then you can edit the option has worked for me

Good tip - thanks. I remember that this bug crept in at the very last minute, too late for the ISO to be remastered with the bug fix. You can't type into a blank field - if I'm remembering things correctly - but I didn't realise that you could edit one of the predefined ones. Useful to know.

---


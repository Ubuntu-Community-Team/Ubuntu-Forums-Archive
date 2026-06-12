---
title: "Unable to dual boot ubuntu in toshiba satellite"
date: 2019-09-13
forum: New to Ubuntu
---

### Post by tmgfigueiredo on 2019-09-13
I everyone,

I'm trying to make a dual boot instalation of ubuntu, in my pc. It's a Toshiba satellite. I've inserted an usb pen, with the image, and i'm able to make the test. Then I try to install ubuntu, and immediately after the first option, it appears a box, with a lot of question mark. I've searched in internet, and it looks that there is a lot of people with the same problem. But as far as I searched, no solution found!

So I'm asking you to help me, in solving this problem.

---

### Post by pcfan1234 on 2019-09-13
Please tell us the name of your computer, the product number etc.
Give us information about the hardware like GPU and CPU.
Does the usb work on another machine?

---

### Post by ortollj on 2019-09-13
Hi 
I did not encounter any particular problem to install Ubuntu 18.04 in dual boot on my Toshiba SATELLITE-C70. I just followed the process here (iso on a usb key, and shrink of my W10 c: disk of 100 gigas for linux on my  originally W10 one tera disk):
[URL="https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/"]https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/
[/URL]the most delicate is the setting of UEFI .but the only thing I did in UEFI is moving up usb first in the boot device list and disable fast boot.
maybe it could help you too ?
[edited]
sudo fdisk -l

Device          Start        End    Sectors   Size Type
/dev/sda1        2048    2099199    2097152     1G Windows recovery environment
/dev/sda2     2099200    2303999     204800   100M EFI System
/dev/sda3     2304000    2566143     262144   128M Microsoft reserved
/dev/sda4     2566144 1722884870 1720318727 820,3G Microsoft basic data
/dev/sda5  1927686144 1929756671    2070528  1011M Windows recovery environment
/dev/sda6  1929756672 1953523711   23767040  11,3G Windows recovery environment
/dev/sda7  1722886144 1927686143  204800000  97,7G Linux filesystem as you can see above I did a shrink of 100 000 mega Byte of my W10 initial partition.
 and I use the Universal Usb installer Way:
 [Universal Usb Installer]([https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/))

 
 
 beware to click on the good download , not the commercial ones !

---

### Post by yancek on 2019-09-13
You will need to post more information as requested above and in addition, indicate what method/software you used to create the bootable usb.  Did you check the download of the iso prior to putting it on the usb to verify the download?  Have you tried the usb on another computer if you have one available to verify it?

---

### Post by dfault2 on 2019-09-18
1.Use Rufus to create the bootable drive.
2. use "Something else" option while installing
3. Make sure to install the grub bootloader in the same partition as your installation (boot) partition.
4. Restart in windows and use easyBCD software to add ubuntu in your bootable system list.(use syslinux as linux type and select the same partition when adding)
5. Now you'll see the dualboot menu every time you boot your system

Works for me every time I dualboot my windows with any linux flavor.

---


---
title: "Finding ubuntu"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by Nikki5 on 2012-07-17
Hi,
I recently formatted my 33Gb file system which had windows XP installed on it as my windows had stopped working.
I had a dual boot system before with windows XP installed on 33GB partition and ubuntu 10.04LTS on 41GB partition.
But after formatting, while booting I cant find the Grub page which used to provide me options to select the O.S. to boot.Windows boots up automatically.I also cant see that 41 GB partition anywhere on windows.I want my ubuntu 10.04LTS back as I need it for my work.Please suggest what to do.Thanks in advance!!

---

### Post by krustenBrot on 2012-07-17
Take a look at: [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair").

Restoring grub should solve the problem and this seems to be the easiest way. :)

---

### Post by Nikki5 on 2012-07-17
But Boot repair can be installed from ubuntu and as i mentioned i cant find ubuntu now.I have only windows.

---

### Post by Shadius on 2012-07-17
> **Nikki5 said:**
> But Boot repair can be installed from ubuntu and as i mentioned i cant find ubuntu now.I have only windows.

If Windows boots up, boot into it and download Boot-Repair and burn it to a CD. Then reboot with the Boot-Repair CD in the CD drive. Make sure you're BIOS is set to boot from CD first.

---

### Post by robtygart on 2012-07-17
> **Nikki5 said:**
> But Boot repair can be installed from ubuntu and as i mentioned i cant find ubuntu now.I have only windows.

You might be able to use a live CD to fix it.

---

### Post by madjr on 2012-07-17
> **Nikki5 said:**
> But Boot repair can be installed from ubuntu and as i mentioned i cant find ubuntu now.I have only windows.

you need to use boot-repair from a live ubuntu cd/usb.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

soon it will also be included in the ubuntu ISO by default.

---

### Post by sujitrjadhav on 2012-07-17
I always keep a live usb stick with ubuntu and some other linux installed on it. I use multisystem to create live usb. pinguy os comes with boot-repair preinstalled.

---

### Post by Nikki5 on 2012-07-25
Thanks all of you.I burned boot repair iso image on cd.Now what should i do?when i am entering the cd in drive and trying to boot from it it by entering the boot menu and selecting CDROM from options it is not booting....windows starts up.what should i do now?

---

### Post by oldfred on 2012-07-25
How did you burn CD? If still booting from hard drive, it is not finding a bootable image or device to boot from.

Does CD drive work? No loose cables, lens cleaned or it works with other CDs?
Did you verify ISO md5sum?, did you write at a slow speed.

For Ubuntu but instructions work for any bootable CD.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by TheMTtakeover on 2012-07-25
> **Nikki5 said:**
> Thanks all of you.I burned boot repair iso image on cd.Now what should i do?when i am entering the cd in drive and trying to boot from it it by entering the boot menu and selecting CDROM from options it is not booting....windows starts up.what should i do now?

Did you burn the CD correctly? If it boots to windows try restarting your computer rather than turning off and then turning on.

---

### Post by YannBuntu on 2012-07-30
Hello

> **Nikki5 said:**
> Hi,
I recently formatted my 33Gb file system which had windows XP installed on it as my windows had stopped working.
I had a dual boot system before with windows XP installed on 33GB partition and ubuntu 10.04LTS on 41GB partition.
But after formatting, while booting I cant find the Grub page which used to provide me options to select the O.S. to boot.Windows boots up automatically.I also cant see that 41 GB partition anywhere on windows.I want my ubuntu 10.04LTS back as I need it for my work.Please suggest what to do.Thanks in advance!!

you may have formatted the Ubuntu partition by mistake...

Did you install Ubuntu via a liveCD or a liveUSB ?
Do you still have the Ubuntu CD/liveUSB? if yes, please boot on it, choose "Try Ubuntu", install and run Boot-Repair as described [here]("https://help.ubuntu.com/community/Boot-Info#Step_2_-_Install_Boot-Repair_in_the_live-session"), click "Create a Boot-Info" and indicate the URL that will appear.

---

### Post by Chdslv on 2012-07-30
> **Nikki5 said:**
> Hi,
I recently formatted my 33Gb file system which had windows XP installed on it as my windows had stopped working.
I had a dual boot system before with windows XP installed on 33GB partition and ubuntu 10.04LTS on 41GB partition.
But after formatting, while booting I cant find the Grub page which used to provide me options to select the O.S. to boot.Windows boots up automatically.I also cant see that 41 GB partition anywhere on windows.I want my ubuntu 10.04LTS back as I need it for my work.Please suggest what to do.Thanks in advance!!

1) Boot with your Ubuntu CD.

2) Open the terminal and write sudo fdisk -l and you find how many partitions you have and which one is Linux. (You said you had *only* two OSs.)

3) Let's consider it as sda3 for the explanation below. (You may have a different one.)

sudo mount /dev/sda3  /mnt

sudo grub-install --root-directory=/mnt  /dev/sda

Here it is sda, the whole disk)

Once that done;

sudo umount /dev/sda3
sudo reboot

You'd have your grub display and your Ubuntu.

Once in your Ubuntu, you may do 
sudo update-grub to be on the safe side.

If you have not formatted the whole disk, you should be able to get your Ubuntu back.:)

---

### Post by critin on 2012-07-30
> **Nikki5 said:**
> Hi,
**I recently formatted my 33Gb file system which had windows XP installed on it** as my windows had stopped working.
I had a dual boot system before with windows XP installed on 33GB partition and ubuntu 10.04LTS on 41GB partition.
But after formatting, while booting I cant find the Grub page which used to provide me options to select the O.S. to boot.Windows boots up automatically.I also cant see that 41 GB partition anywhere on windows**.I want my ubuntu 10.04LTS back** as I need it for my work.Please suggest what to do.Thanks in advance!!


But Boot repair can be installed from ubuntu and as i mentioned** i cant find ubuntu now.I have only windows.**



If you formatted the windows partition, how do you still have windows?  It looks like ubuntu partition was formatted by mistake.

---


---
title: "ubuntu install"
date: 2015-06-12
forum: New to Ubuntu
---

### Post by suat4 on 2015-06-12
Hi. I have just installed ubuntu from usb. When restarted, it doesnt automatically start with ubuntu.comes back to installation screen.when i changed boot from usb to hdd it says cant find bootable device. Could you please help. Thanks

---

### Post by grahammechanical on 2015-06-12
At the end of the installation process we are asked to restart the computer. That is when we should remove the USB memory stick from the USB port otherwise we will start a Ubuntu live session.

You also should give us information about your machine and any other OS on it. What option did you choose when you chose to install Ubuntu? We have these options

1) Install Ubuntu alongside them [that is other operating systems]
2) Erase disk and install Ubuntu
3) Encrypt the new Ubuntu installation
4) Use LVM with the new Ubuntu installation
5) Something Else

Regards.

---

### Post by suat4 on 2015-06-12
Hi i have acer es 512 freedos. I have chosen erase disk and install ubuntu. Suat

---

### Post by leunam12 on 2015-06-12
Do you want to try boot-repair?

---

### Post by suat4 on 2015-06-12
I tried but didnt work.when i unplug iso usb, it gives error no bootable device.

---

### Post by suat4 on 2015-06-12
I installed again and run boot repair with commands in terminal. Now when i start without usb, error screen appears windows boot cant be found  and then i can chose "unknown device hdd" boot hdd and it starts. It is a bit takes more time to open. Suay

---

### Post by cariboo on 2015-06-12
You can boot from your usb device, and chroot the first partition, or whichever partition Ubuntu is installed on and install grub to the right place to do this use the following commands in a terminal:

```

sudo mnt /dev/sda1 /mnt
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev

sudo chroot /mnt


```

Once you have chrooted the patitiom install and then update grub:

```
grub-install /dev/sda
update-grub
```

you should see the process echo back the operating systems you have installed on your hard drive.

shut down the system, remove the usb drive and restart.

---

### Post by oldfred on 2015-06-12
If newer Acer with UEFI, you have to set a password (never lose that) and specify that ubuntu is allowed to boot.

 Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)
      
 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

 Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)

---


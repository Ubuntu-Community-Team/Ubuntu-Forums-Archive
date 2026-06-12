---
title: "USB Device not seen in VMware"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by exup1000 on 2008-05-20
Hi

I am running Ubuntu 8.04 Heron in VMware on a windows XP machine. I am trying to connect a usb device to be seen in Ubuntu. It is seen in XP ok but not Ubuntu. I have checked the VMware help and it simply says go to VM > Settings > Hardware > USB controller but there is nothing there.
I assume I have to enable detection in Ubuntu. How do I do that?

Regards Exup

---

### Post by pedro_orange on 2008-05-20
Could try mounting it.

```
mount /dev/hda1 /mnt/mydir
```

Mounts /dev/hda1 to /mnt/mydir

If you dunno what it is do a df:

```
pedro@pedro-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             17548080   3349552  13314152  21% /
varrun                  249612       104    249508   1% /var/run
varlock                 249612         0    249612   0% /var/lock
udev                    249612        48    249564   1% /dev
devshm                  249612        12    249600   1% /dev/shm
lrm                     249612     38176    211436  16% /lib/modules/2.6.24-16-generic/volatile
gvfs-fuse-daemon      17548080   3349552  13314152  21% /home/pedro/.gvfs
pedro@pedro-laptop:~$ 


```

As long as the VM has USB Controller added to the hardware list you should be able to see it inside the VM.

Good luck

---

### Post by exup1000 on 2008-05-20
Hi, I have just installed linux for the first time so very new to using it. Could you explain in a little more detail.
I opened a command prompt and typed in df and got this 

au009900@TESTLINUX:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sda1             50516276   2236424  45733956   5% /
varrun                  257804       104    257700   1% /var/run
varlock                 257804         0    257804   0% /var/lock
udev                    257804        44    257760   1% /dev
devshm                  257804        12    257792   1% /dev/shm
lrm                     257804     38176    219628  15% /lib/modules/2.6.24-16-generic/volatile
gvfs-fuse-daemon      50516276   2236424  45733956   5% /home/au009900/.gvfs


Which part is the USB controller. By the way the device plugged in is a USB 256MB key.

---

### Post by pedro_orange on 2008-05-20
[http://www.mydigitallife.info/2006/09/10/how-to-mount-usb-disk-drive-in-unix-or-linux/](http://www.mydigitallife.info/2006/09/10/how-to-mount-usb-disk-drive-in-unix-or-linux/)

Better explained than I could :)

---

### Post by exup1000 on 2008-05-20
Ok, didnt realise it would be this complex a task to install a USB device. Will attempt following this guide tomorrow at work.

---

### Post by prince09 on 2008-05-20
Hi Exup,

[http://ubuntuforums.org/showthread.php?t=795248&highlight=VMware+USB](http://ubuntuforums.org/showthread.php?t=795248&highlight=VMware+USB)

  I was struggling with the same problem yesterday .. I found a way around it in this thread, though it doesn't exactly get Ubuntu to detect your USB .. see if it helps you...

Good Luck! :-)

---

### Post by exup1000 on 2008-05-24
Hi Thanks Prince09, certainly worked and can get to the device, albeit not as a USB device.

---

### Post by exup1000 on 2008-05-25
Hi

worked it out in the end. All I had to do was add the USB port in the VMWARE console before starting Ubuntu. Only after I have added it along with the sound card, would it then be available from VM > Removable devices > USB Devices

cheers

---


---
title: "cannot boot maverick &quot;error: sparse file not allowed&quot;"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by emalaith on 2012-05-28
I read this is a common bug, but no solution I found in the Internet works for me :(
In grub 1.97 after choosing Linux Ubuntu I get
"error: sparse file not allowed, press any key to continue"
hitting any key directs me back to the grub menu.

I ran a liveCD and commented out:
```
#cat << EOF
#if [ -s \$prefix/grubenv ]; then
#  set have_grubenv=true
#  load_env
#fi
#EOF
```in /etc/grub.d/00_header and I still get the same error.

When did it start? I had three partitions with: Windows 7, Ubuntu 10.10 and Mint 12. Mint was installed the most recently, so the grub file loaded at the startup must have been from the Mint partition. Then I formatted the Mint partition, loosing my grub. Then I run some magic grub-rescuing commands from liveCD and everything was working fine for 2 days. Today it won't start due to this sparse file error.

this is my fstab file:
```
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=c1f21bbe-c892-4c21-a78a-16787327238e none            swap    sw              0       0
/dev/sda4    /media/playground    ntfs    defaults     0    0
/dev/sda6 /media/sandbox ext4 defaults 0 0
```this is my fdisk-l:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1        3916    31453185    5  Extended
/dev/sda3   *        3916        6466    20480000    7  HPFS/NTFS
/dev/sda4            6466       30402   192264192    7  HPFS/NTFS
/dev/sda5            1974        3916    15600640   83  Linux
/dev/sda6               1        1974    15850496   83  Linux
```The partition with Ubuntu 10.10 is /dev/sda5.
How can I run grub rescue or something like this when I'm not able to login to Ubuntu 10.10?
Thanks for your help!

---

### Post by matt_symes on 2012-05-28
Hi

Purge and reinstall grub from a LiveCD. See if that fixes the problem.

[http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)

Kind regards

---

### Post by emalaith on 2012-05-29
Hi,
reinstalling grub solved the problem (hopefully for good, because I've already reinstalled grub from liveCD two days back). While following the steps from the link I got an error:
```
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done
```
but my maverick started successfully.
Thank you, matt_symes!

---

### Post by matt_symes on 2012-05-29
Hi

> Cannot find list of partitions!

I think mounting /sys may get rid of that error message (at least i read that somewhere).

```
sudo mount -t sysfs sysfs /mnt/sys
``` 

or

```
sudo mount -o bind /sys /mnt/sys
```

Kind regards

---

### Post by emalaith on 2012-06-03
Hi again,
I can't believe I cannot find a solution in google to another, common (according to my common sense ;)), problem :/
When I got my GRUB back, and was able to start Maverick successfully, I haven't noticed there is no Windows 7 on the list :/ I usually use Linux only, but today I have to do something in C# and I can't start Windows :(

Kind Regards

---


---
title: "Only able to boot in recovery mode"
date: 2014-09-01
forum: New to Ubuntu
---

### Post by bmarci on 2014-09-01
Hi,

I'm using ubuntu 14.04 and when I want to boot the system it stucks at the loading screen. When I enter recovery mode and select resume it works as charm. It might be a little messy with the UUIDs but I don't know the exact source of the problem. Do you have any advice how to fix the normal booting?

---

### Post by deadflowr on 2014-09-01
first, I would try refreshing the grub bootloader with
```
sudo update-grub
```
Then if that is not helpful, perhaps I would boot into a previous version from the boot menu.

In the boot menu, below the option to boot into recovery mode, should be an option to boot into previous versions. This will allow you to boot into older kernels.
(It means previous kernel versions, which you should have a few unless you are super vigilant at cleaning them up)

See if either of them are helpful.

If not, we can dig deeper, but we'll hold off on that for the moment...

---

### Post by grahammechanical on 2014-09-01
If you can load to a desktop using Recovery mode>Resume then there is nothing wrong with the Grub boot menu. Recovery mode runs on Linux. If Grub was looking in the wrong place for the LInux boot image then you would get a Grub rescue prompt.

I suggest that once you get to a desktop using Resume you open System Settings and go to Software and Updates and open the Additional Drivers tab and change video drivers.

The Resume option loads to a desktop using an open source video driver called llvmpipe. So, it seems to me that this problem is caused by a proprietary video driver.

Regards.

---

### Post by bmarci on 2014-09-02
Thanks for the quick answers. I tried everything what is written but unfortunately it hasn't solved yet. Any other ideas?

---

### Post by sotiris2 on 2014-09-02
What driver did you choose from the Additional drivers tab? What is your graphics card?

---

### Post by bmarci on 2014-09-03
I used the NVIDIA binary driver 331.38 (proprietary) and tried the open source one: xserver-xorg-video-nouveau. It didn't matter after rebooting I only saw the loading screen with the running spots.

---

### Post by sotiris2 on 2014-09-03
Did this system use to work? Did you change anything lately? When it is stuck in the dots loop can you get a terminal via ctrl+alt+f1?

---

### Post by bmarci on 2014-09-04
Yes, this system worked. There was a problem with booting and I've messed with fstab to fix it. Now this error has gone but I'm only be able to boot in recovery mode. After pressing ctrl+alt+f1 I only see "-" in the top left corner.

---

### Post by sotiris2 on 2014-09-04
Ok get to grub select which kernel (non recovery you want to boot) and press **e** you will get some code. Near the end (second to last?) you will find a line finishing in ro quiet splash $vt_handoff. Delete quiet splash so its ro $vt_handoff and press ctrl+x to boot. Instead of showing dots it will show text. When it gets stuck check what are the last lines. Maybe they 'll help us understand exactly what is preventing the system from booting.

---

### Post by kansasnoob on 2014-09-04
>  There was a problem with booting and I've messed with fstab to fix it.

Can you provide a little more detail? Did you follow some on-line instructions?

Please post the output of these 5 commands [using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168"):

```
df -H
```

```
sudo parted -l
```

```
sudo blkid -c /dev/null
```

```
cat /etc/fstab
```

```
cat  /etc/initramfs-tools/conf.d/resume
```

---

### Post by bmarci on 2014-09-06
The problem solved. Ater doing "[COLOR=#000000]Delete quiet splash so its ro $vt_handoff and press ctrl+x to boot. " I have seen why it stucks. It was:
 
```
 init: lxc-android-config main process (329) terminated with status 255 
```
 
I googled it and the solution was there in about a minute. This solved it:

[/COLOR]```
sudo apt-get purge android-tools-adb android-tools-fastboot lxc-android-config ubuntu-device-flash

``` 

Now I now how to look after boot problems in the future. Thank you very much. You guys are awesome :)

---


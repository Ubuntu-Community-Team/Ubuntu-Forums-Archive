---
title: "Oneiric doesn't start after interrupted update"
date: 2011-07-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by appi2012 on 2011-07-17
I was updating my 11.10 installation, when it asked me whether I wanted to keep or replace my cupsd (or something like that). I chose replace, but it just froze. I waited for quite some time, but nothing happened. So I tried to restart and planned to use ```
sudo dpkg --configure -a
```
to finish the update. However, my computer wouldn't turn back on.

The first time I turned it on, it showed plymouth, which told me that the disk for / wasn't present. I skipped that error message.
Then, it told me that the disk for /tmp wasn't present either. I skipped that, but then it didn't do anything but repeat the animation. I restarted again, but now my computer stops starting up when it tells me that /run/udev is not writable.

Is there anything I can do to fix this?

Thanks in advance.

---

### Post by cariboo on 2011-07-17
Can you start in recovery mode, then once at the menu select:

```
dpkg
```

---

### Post by garvinrick4 on 2011-07-17
If post 2 does not work you can use another install of same 32 or 64 bit architecture and or
a live Cd of same architecture and use chroot to get into root of your install and hopefully complete updates from there. 
Find your install using:
```
sudo fdisk -l 
```(lower case L)
Find your install and use your own I am using sda5 for this code:
#Make sure internet is working in other install or Live CD as to update and upgrade:
Copy and paste one at a time:
```

 sudo mount /dev/sda5 /mnt
 for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done  
 sudo cp /etc/resolv.conf  /mnt/etc/resolv.conf
 sudo chroot /mnt
 dpkg --configure -a
 apt-get update && apt-get upgrade
 dpkg --configure -a
 exit for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
 sudo umount /mnt
 sudo reboot

```Hopefully you are OK to go now.

#After chroot line you can also use this same code to install grub or update-grub
you are in the root of whatever sda# you are using: for instance below in any
combination that you require.
apt-get purge grub grub-common grub-pc
apt-get install grub-common grub-pc
grub-install /dev/sda
update-grub
#The cp /etc/resolv.conf to /mnt/ect/resolv.conf line of code above is copying your internet connection to /mnt so as to have the internet in working condition, must have a working
internet to start with.

[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by appi2012 on 2011-07-18
Thanks for the replies. Unfortunately, I'm not able to get to a shell when I boot up my computer (Upon starting recovery mode, it hangs after telling me that modem manager cannot connect to the system bus at /var/run/dbus/system_bus {something to that effect}).

However, the 2nd answer might work for me. I actually hoped there would be something like this, and burned a live cd already. I'll give that a shot. Thanks!

---

### Post by appi2012 on 2011-07-18
I was able to run the dpkg commands through the LiveCD, but I couldn't umount /mnt/dev - It keeps saying that the drive is busy.

Should I go ahead and reboot?

---

### Post by garvinrick4 on 2011-07-18
>  Should I go ahead and reboot? 	
Yes.

---

### Post by appi2012 on 2011-07-19
Thanks to garvinrick4, I have my computer working again. Also, that chroot through the live cd can be very useful.

Thanks again.

---


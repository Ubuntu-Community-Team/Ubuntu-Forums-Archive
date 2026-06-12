---
title: "Would it be possible to fix Oneiric via booting into Natty?"
date: 2011-07-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-07-12
Hi,

I am running a multiboot PC that includes Natty and Oneiric.  After last night's update of the latter, I cannot boot into Oneiric because there's no mouse cursor movement and the keyboard freezes.

Since I am still able to boot and run Natty, I am wondering if it's feasible to get into Natty in order to fix Oneiric's problems.  

1)I need to be able to run the following via a terminal:

```

mv /run/udev /run /udev.old

```

OR 

2) Instead of using a live CD, run Natty, directly chroot the Oneiric partition /dev/sdX and type the following commands via a terminal:

```

sudo mount /dev/sdX /mnt
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt

```

Any suggestions?  Thanks a lot for your help

---

### Post by VinDSL on 2011-07-12
> **iClouseau88 said:**
> I am wondering if it's feasible to get into Natty in order to fix Oneiric's problems.[...]
If that's the path you want to take...

I would simply delete /run/udev (in your Oneiric partition).

That should solve the problem.  ;)

---

### Post by linuxman94 on 2011-07-12
You can boot into oneiric recovery mode and drop into a root shell to run that.  The keyboard works in recovery mode.

Or you could just boot recovery and update the system.  The latest udev fixes the keyboard and mouse freezing.

---

### Post by iClouseau88 on 2011-07-12
Hello VinDSL,

Thanks for your reply.  I followed Quackers' advice: unplugging then replugging mouse and keyboard after bootting into Oneiric. Voila!  I am in Oneiric now...

BUT I cannot find /run/udev in the filesystem using the search tool: "No such file"

Any suggestions?

---

### Post by garvinrick4 on 2011-07-12
> sudo mount -o bind /proc /mnt/procAfter this line of code add below and you have a internet connection from
Install you are using now and can update and upgrade from there:
```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```then chroot into /mnt:

# I actually use this method a lot because of multiple installs and is just
easier than rebooting into all the time. Must be same architecture 32 or 64 bit.
This is another way below there are lots of ways I imagine.
```
sudo mount /dev/sda5 /mnt
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done 
sudo cp /etc/resolv.conf  /mnt/etc/resolv.conf
sudo chroot /mnt
```Do not forget to unmount.
exit
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
sudo umount /mnt
## To be precise you can use this with yum, zypper, or whatever once you have used chroot command.
      So not just the apt-get's but other linux flavors also, quite convenient really.

---

### Post by iClouseau88 on 2011-07-12
Hi linuxman94,

Your approach wouldn't work in a multiboot system where Oneiric boots via chainloading.  I am in Oneiric now after booting then rapidly unplugging and replugging the mouse and keyboard.  Thanks for your reply anyway.

---

### Post by plucky on 2011-07-12
> **iClouseau88 said:**
> Hello VinDSL,

Thanks for your reply.  I followed Quackers' advice: unplugging then replugging mouse and keyboard after bootting into Oneiric. Voila!  I am in Oneiric now...

BUT I cannot find /run/udev in the filesystem using the search tool: "No such file"

Any suggestions?

It is **/var/run/udev**

Good Luck

---

### Post by Quackers on 2011-07-12
The new version of udev solves the issue if you run updates.

---

### Post by Harry33 on 2011-07-12
> **plucky said:**
> It is **/var/run/udev**

Good Luck

Nope, the new udev and initramfs sets up these directories:
/run/initramfs
/run/udev
/run/mount

---

### Post by wnelson on 2011-07-13
The run directory is for temporary .rules to be stored. 

A easy way to get out of the frozen screen (X.org) is to:

Alt-SysRq R-E

this will dump you out to a prompt to log in. 

this is the first part of Alt-SysRq R-E-I-S-U-B which will reboot your frozen system.

Walt

---

### Post by plucky on 2011-07-13
> **Harry33 said:**
> Nope, **the new udev** and initramfs sets up these directories:
/run/initramfs
/run/udev
/run/mount

But this problem happened before the new udev was installed.
Before this no /run/udev could be found on my installation,but there was a /var/run/udev which fixed the problem for me.

> BUT I cannot find /run/udev in the filesystem using the search tool: "No such file"

Any suggestions? 

---


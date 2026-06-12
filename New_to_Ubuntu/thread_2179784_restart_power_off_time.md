---
title: "restart power off time"
date: 2013-10-09
forum: New to Ubuntu
---

### Post by crip720 on 2013-10-09
Hi, I have a multi-boot setup with two external USB HDs.  One external hard drive takes a long time to power off[10 to 15sec]?  If not power off competly on a restart, it will send me to grub rescue[device not present?]  Can I increase the time that the computer is powered off during a restart?  Right now I have do a shutdown, wait, and power back on.  I am on Ubuntu 13.10 64b right now.  I can use the terminal, but do need good complete instructions.  This is a testing system, so I can breck it.  Thank you for any help.  Colin.

---

### Post by fantab on 2013-10-09
Some Ext. USB HDD do take up time to poweroff. Usually this happens if some application or another is using it and/or if data is being written to it. If its a NTFS file system them perhaps you can run 'defragmentation'. 
Does this Ext.HDD have an OS on it?
If its sending you to the 'grub rescue' then your BIOS settings are perhaps set to boot USB devices first.... you can fix it by changing the HDD boot order in the BIOS to boot your OS/Grub installed HDD first.

---

### Post by crip720 on 2013-10-10
It has bootable Linux  OSs on it and it is EXT4.  Was just wondering if there is a config file or something to change the time out on restart.  Next restart will check check BIOS, but I think it is setup to boot internal HD first.

---

### Post by tgalati4 on 2013-10-10
You can also use *acpitool* to keep power to the USB bus after the laptop shuts down.  That allows the disk drive's USB and controller to keep power going to flush the cache and finish writing any data.

You can also add some wait statements to the shutdown scripts to allow more time for the disk to spin down.  It's possible that the USB drive or the way you have it mounted (any additional /etc/fstab mounts?) are preventing the drive from unmounting.  An unclean shutdown will leave errors on the disk which require an fsck on the next reboot.

---

### Post by crip720 on 2013-10-10
Hi, I think maybe your wait statments might be what I am looking for.  I  just need them for the restart button, since it seems to power up the laptop,  before the hard drive has a chance to stop.  The hard drive is a Seagate 1TB, and is only mounted by the OS at the time.  Unfortunalty I am only good with copy and paste for the terminal, and have no idea where to find the shutdown scripts or what to change in them.  As I said before I am looking for a way to delay the power on time when using the restart button.  Thank you.  Colin.

---

### Post by tgalati4 on 2013-10-10
Then you will want to become an expert in *upstart*:  [https://help.ubuntu.com/community/UpstartHowto](https://help.ubuntu.com/community/UpstartHowto)

Rebooting is typically done by setting the *runlevel* to 6 using:

```
telinit 6
```

The scripts that are executed are normally located in /etc/rc6.d.

Putting *sleep 30* in any of those scripts would slow down the shutdown process.  You want to investigate the last scripts to be executed.

---

### Post by crip720 on 2013-10-11
I think I will leave well enough alone, before I make a big mess.  Powering off instead of using restart button is looking good.  Thank you for your help and time.  Colin.

---


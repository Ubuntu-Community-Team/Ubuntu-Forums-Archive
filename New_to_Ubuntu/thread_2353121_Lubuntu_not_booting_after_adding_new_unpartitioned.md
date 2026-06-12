---
title: "Lubuntu not booting after adding new unpartitioned drive"
date: 2017-02-19
forum: New to Ubuntu
---

### Post by ianmanning on 2017-02-19
I have Lubuntu running from an internal MicroSD card on an HP Microserver Gen8. One of the SATA drives in my (JBOD) setup failed, so I replaced it with a new unpartitioned drive. Now Lubuntu won't boot past the Lubuntu splash screen. I'm assuming this is because the "old" (failed) drive is still referenced in /etc/fstab, but what's the best way to fix this? Do I need to reboot from a rescue disk and edit fstab to remove the "old" drive, then partition the new drive and edit fstab again?

---

### Post by Keith_Helms on 2017-02-19
Yes, Linux is not happy if your fstab references a disk that's not there.  You can either do like you said - boot from a rescue disk and fix fstab, or you should be able to get to a command line during the bootup that fails and fix fstab from there.

If there's a possiblity one of your JBOD may go missing and you want to be able to boot in that situation, you can add "nofail" to the fstab entries for each of them.  That will let the system ignore the drive missing error for that entry.

---

### Post by DuckHook on 2017-02-19
You can cut out a step as follows:

[LIST=1]
[*]Boot with a LiveUSB.
[*]Backup all important data.
[*]Using gparted, create a partition on your *new* HDD with the type of filesystem that you want. Use care. You don't want to repartition your system HDD or any of your existing ones.
[*]Note the new UUID. You can also get this with ```
sudo blkid
```
[*]Mount your system HDD
[*]```
sudo nano /mnt/etc/fstab
```
[*]Just change the UUID of old HDD to the new one.
[/LIST]
You should now be able to reboot without errors.

You may want to consider autofs: [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

Autofs allows you to take non-system mounts out of fstab and mount them only as needed. They will automatically unmount after a period of inactivity. My practice is to mount as little in fstab as possible, in part to avoid what you've just gone through, but also because the use of autofs, in tandem with hdparm, allows me to spin down moderately-used HDDs for a little bit of power savings and to extend HDD life.

---


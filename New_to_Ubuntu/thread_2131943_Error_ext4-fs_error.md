---
title: "Error ext4-fs error"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by chandramoulivashisth on 2013-04-03
my PC is running on ubuntu 12.04 LTS. My PC is giving error ext4-fs error (device sda1) ext4_lookup:1050: inode #78913: comm update-motd-upd: deleted inode referenced: 180. Can anyboybody help with this.

---

### Post by schragge on 2013-04-03
Open a terminal (press **Ctrl**+**Alt**+**t** in Ubuntu, or **Win**+**t** in Xubuntu), and run
```
sudo touch /forcefsck
``` then reboot. On boot up, file system check will be performed automatically.

---

### Post by chandramoulivashisth on 2013-04-04
On Rebooting
```

* Starting web server apache2                                                                                          *Stop
ping save kernel messages                                                                                                 [OK]
[OK]
*Starting anac(h)ronistic cron                                                                                            [OK]

*Stopping anac(h)ronistic cron                                                                                           [OK]
                                                                                                                                    [OK]

```

and nothing is happening.

---

### Post by schragge on 2013-04-04
Please post the output of
```
sudo ls -l `findmnt -notarget /dev/sda1`/lost+found
``` and ```
dmesg|grep -i fsck
```

---

### Post by chandramoulivashisth on 2013-04-04
```


sudo ls -l `findmnt -notarget /dev/sda1`/lost+found
ls: cannot access findmnt -notarget /dev/sda1/lost+found: No such file or directory

```

---

### Post by schragge on 2013-04-04
Hmm, strange. Looks like backticks in the command were ignored. Please post the output of
```
sudo blkid -o list -c /dev/null
``` And what was the output of *dmesg*?

---

### Post by chandramoulivashisth on 2013-04-04
I am now using Live CD as UBUNTU is not booting. 

no output for dmesg|grep -i fsck

```

device       fs_type label      mount point      UUID
---------------------------------------------------------------------------------
/dev/loop0  squashfs           /rofs    
/dev/sda1   ext4                /media/8b6c2603-734d-43b6-8b31-770ee73d58a9  8b6c2603-734d-43b6-8b31-770ee73d58a9
/dev/sda3   ntfs                (not mounted)     3553A408079FED0F
/dev/sda5   swap               <swap>             7f754a77-6a31-4566-99cb-48847fd0edfc
/dev/sdb1   vfat     UBUNTU 1204  /cdrom      901D-1DDc          

```

---

### Post by schragge on 2013-04-04
If Ubuntu is not booting then you probably should try [uhelp]community/Boot-Repair[/uhelp].

---

### Post by fantab on 2013-04-04
> **chandramoulivashisth said:**
> I am now using Live CD as UBUNTU is not booting. 

If Reinstalling Ubuntu is an option then do so. But before that Using LiveCD back up any important DATA that you may have. Run the Utility called "Disks" and run the SMART test on your HDD.

Using GParted, available on Live CD delete all partitons, re-create and reformat as ext4. And by the way, why do you have NTFS partition? You don't want it if you are only booting Ubuntu/Linux.

---

### Post by chandramoulivashisth on 2013-04-04
ok .. I have reinstalled UBUNTU. Now on rebooting : - 

```

PXE-M0F: Exiting PXE ROM.
No Bootable device -- insert boot disk and press any key

```

Got into BIOS settings, every thing is fine there.

Is there a problem with my Hard Disk??

its only 1 month old.

---

### Post by fantab on 2013-04-04
Did you delete all the partitions and recreated them? or have you just reinstalled?
Boot from Live CD and post the output of [BOOTINFO SCRIPT]("http://bootinfoscript.sourceforge.net/").
If you have doubts about your HDD then run "Disks" from LiveCD and perform SMART tests on your HDD. Tell us what the tests say.

---


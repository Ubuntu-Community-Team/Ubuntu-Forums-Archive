---
title: "Ubuntu will not boot and boot-repair doesn't offer recommended repair option"
date: 2020-06-05
forum: New to Ubuntu
---

### Post by jwalke631 on 2020-06-05
Hi and TIA for any help. I use ubuntu for a shared server system, however I am very much a newb. Yesterday, all the users were automatically disconnected from the shared system, when I came to check the system, it appeared to have crashed. I was only able to do a force shutdown and reboot. Booting is failing. Made a bootable USB and have tried booting both UEFI and Legacy modes and running boot-repair. In both cases boot-repair does not offer a "recommended repair" option. Only the bootInfo link ([http://paste.ubuntu.com/p/Kfh9JMdXNS](http://paste.ubuntu.com/p/Kfh9JMdXNS)). When running "$ sudo fdisk -l" only the USB memory/partition is shown, not any of the other drives in the computer. 

I am running Ubuntu 18.04

When booting everything seems to fail at:
"A start job is running for /home (XX/ 1min 34s)

Then network time sync fails repeatedly followed by 
"failed to start network service"
"failed to start network name resolution"
.
.
.
EXT4-fs error (device sda3): ext4_find_entry_1455: inode #8193: comm systemd: reading directory iblock 0
EXT$-fs (sda3): previous I/O error to superblock detected...

which repeats 

then 

EXT4-fs error (device sda3): ext4_find_entry_1455: inode #8193: comm systemd: reading directory iblock 0
EXT$-fs (sda3): previous I/O error to superblock detected...

then a bunch more I/O errors and Error -5 is finally shown

Is/Has the hard drive failed?

---

### Post by CelticWarrior on 2020-06-05
Welcome.

>  Is/Has the hard drive failed? 				
Yes.

---

### Post by jwalke631 on 2020-06-05
Is there any way to simply install ubuntu onto one of the other drives and use it to boot from rather than the failed drive? There are 4 different drives installed in the machine. I can also still access Grub if that makes a difference.

---

### Post by MoebusNet on 2020-06-05
I'm not an expert. But if this happened to me, I'd back up all my data (hopefully *again*) and decide if I want to buy a new drive or live with what's left. Then reinstall, restore data and done.

---

### Post by jwalke631 on 2020-06-05
Thank you for the input. I believe the system was set up in RAID 1 so I'm not terribly concerned about data loss, but my current plan is to pull all the hard drives and find the one that has failed and see if I can read anything off of any of them before replacing/reinstalling.

---

### Post by zeekstern on 2020-06-06
If you look at /proc/mdstat it will show you the bad disk. You should see a F on one the status lines.

Zeek

---

### Post by MoebusNet on 2020-06-08
You can use Ubuntu to boot from a DVD or USB drive to check your hard drives for data. Here is an article to prepare a Live DVD on a Windows or Ubuntu machine: [https://www.fosslinux.com/895/how-to-create-ubuntu-live-usb-drive-in-windows.htm](https://www.fosslinux.com/895/how-to-create-ubuntu-live-usb-drive-in-windows.htm)

Once you boot from the DVD (or USB drive), you can browse the functional hard drives (unless they are encrypted) without having to remove them from the PC so that you can recover any data you need. You can also use Terminal to determine which is the bad disk, as zeekstern mentioned above. That should save you some time and effort.

---

### Post by jwalke631 on 2020-06-08
Thank you all for the help. I have used the USB drive and when checking drives the only thing that shows up in the list is from the USB drive itself, nothing from the actual machine. 

Thank you zeekstern and MoebusNet for the continued help.

---


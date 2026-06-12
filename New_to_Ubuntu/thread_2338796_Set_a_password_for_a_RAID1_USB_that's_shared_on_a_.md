---
title: "Set a password for a RAID1 USB that's shared on a network?"
date: 2016-10-02
forum: New to Ubuntu
---

### Post by noripsni on 2016-10-02
I've got 2x32GB in software RAID1 shared across the network. No password is required to access this device. How would I setup a password so that it prompts to enter a password when trying to access it from a windows client? Instead of saying I don't have access, no way of entering and user/pass.

I've shared the drive using SAMBA GUI
Successfully made it accessible adding, "force user = <user>", at the end of the smb.conf file. Without this I would not be able to access.

I'm not sure how the my user is, 'root', I never setup a user to be named root.

---

### Post by TheFu on 2016-10-02
Don't use root. Ubuntu isn't designed to use it and it can cause issues when used incorrectly. Using root/sudo with GUI programs can cause unintended problems as well. Be careful, there are usually unintended changes.

RAID has 2 uses.
a) higher performance - USB fails to deliver on this.
b) high-availability - USB fails to deliver on this.
So, first thing is to strongly rethink using RAID for any USB connected storage. Probably not worth the hassle.

32G storage sounds like flash drives.  These typically have FAT32 or xfat as the file system.  On those, Linux permissions are strictly controlled by the mount process/command.  The ower and group are set at mount time.  Using a different, native Linux file system would make this easier, but if flash drives are being used, then wear could be an issue with the normal file systems we'd use.

I've never used a GUI to setup samba. Usually, GUIs only provide access to 20% of the capabilities. Don't know if that it the situation with the GUI you used or not.  I think you need user mode for permissions in the samba config to get passwords to be used. 

So ... to get better advice, please explain the actual storage being used. Is it flash, ssd, spinning disk?  Is the USB v1, 1.1, 2, or 3?

There is a samba how-to for Ubuntu.  "ubuntu samba" should find a few. [https://www.howtoforge.com/tutorial/samba-server-ubuntu-16-04/](https://www.howtoforge.com/tutorial/samba-server-ubuntu-16-04/) is one.  Expect to edit /etc/samba/smb.conf.  For a simple setup, it is really easy. RAID shouldn't matter, but the underlying file system does.  The only real trick I know is to use the **smbpasswd** command to initialize each userid. The How-To explains.

---

### Post by noripsni on 2016-10-03
> **TheFu said:**
> Don't use root. Ubuntu isn't designed to use it and it can cause issues when used incorrectly. Using root/sudo with GUI programs can cause unintended problems as well. Be careful, there are usually unintended changes.

RAID has 2 uses.
a) higher performance - USB fails to deliver on this.
b) high-availability - USB fails to deliver on this.
So, first thing is to strongly rethink using RAID for any USB connected storage. Probably not worth the hassle.

32G storage sounds like flash drives.  These typically have FAT32 or xfat as the file system.  On those, Linux permissions are strictly controlled by the mount process/command.  The ower and group are set at mount time.  Using a different, native Linux file system would make this easier, but if flash drives are being used, then wear could be an issue with the normal file systems we'd use.

I've never used a GUI to setup samba. Usually, GUIs only provide access to 20% of the capabilities. Don't know if that it the situation with the GUI you used or not.  I think you need user mode for permissions in the samba config to get passwords to be used. 

So ... to get better advice, please explain the actual storage being used. Is it flash, ssd, spinning disk?  Is the USB v1, 1.1, 2, or 3?

There is a samba how-to for Ubuntu.  "ubuntu samba" should find a few. [https://www.howtoforge.com/tutorial/samba-server-ubuntu-16-04/](https://www.howtoforge.com/tutorial/samba-server-ubuntu-16-04/) is one.  Expect to edit /etc/samba/smb.conf.  For a simple setup, it is really easy. RAID shouldn't matter, but the underlying file system does.  The only real trick I know is to use the **smbpasswd** command to initialize each userid. The How-To explains.


Thanks for replying! I understand I won't get blazing performance out of these USB 2.0 Flash sticks. I am not looking for speedy read/write times, this would mainly be used for tiny/small files. And the files I used to test out the speed were 100-200mb videos and transferred at around 10mb per second. That's perfectly fine for the intention. What do you mean by, "High - Availability"? The reason for USB RAID is I don't have any sata ports on this micropc. Only the ones used for the internal SSD and DVD drive. The drive is formatted, it shows ext3/ext4 as the filesystem. I've never used root in the terminal, just sudo. And i've never used the terminal to alter anything in the samba GUI just the samba that's used in terminal.

---

### Post by TheFu on 2016-10-03
The [classic definition of HA]("https://en.wikipedia.org/wiki/High_availability") ... is to reduce downtime for critical systems by having redundancy. A "critical system" doesn't depend on USB2 devices.
Better use would be to have 1 for storage and use the other for versioned, daily, backups.  IMHO.  RAID is over used and almost always misused outside a business trying to provide 24/7/365 uptimes.  

Use then mount command to see the real file system being used for any mounted storage.

Journaled file systems will burn through flash drives faster than you'd probably like.  

I can't understand the last sentence. Sorry.

Anyway - was that link helpful for the samba issue?

---

### Post by noripsni on 2016-11-22
> **TheFu said:**
> The [classic definition of HA]("https://en.wikipedia.org/wiki/High_availability") ... is to reduce downtime for critical systems by having redundancy. A "critical system" doesn't depend on USB2 devices.
Better use would be to have 1 for storage and use the other for versioned, daily, backups.  IMHO.  RAID is over used and almost always misused outside a business trying to provide 24/7/365 uptimes.  

Use then mount command to see the real file system being used for any mounted storage.

Journaled file systems will burn through flash drives faster than you'd probably like.  

I can't understand the last sentence. Sorry.

Anyway - was that link helpful for the samba issue?


Thanks for replying!! I read the article and I'll give it a shot!
You mentioned I should have 1 USB stick for storage and the other for versioned/daily backups of the 1st storage. How would I go about setting up that automatically? Or would I have to manually drag and drop? That's the thing I had trouble with windows, having the files on one stick automatically copy itself over to the other.

---

### Post by TheFu on 2016-11-22
Backups: [https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/) - that's 1 way.
Use cron to automate stuff.
Don't use any GUI for automated tasks.

The only trick I'd think would be to use different LABELs for the flash drives and mount each by LABEL, when needed, during backups.
This stuff is pretty basic knowledge for people running Unix systems.

Would really be helpful if my questions were answered and 6 weeks delay didn't happen.

---


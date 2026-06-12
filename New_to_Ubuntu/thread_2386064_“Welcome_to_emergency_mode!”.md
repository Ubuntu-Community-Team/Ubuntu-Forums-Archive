---
title: "“Welcome to emergency mode!”"
date: 2018-02-28
forum: New to Ubuntu
---

### Post by coulthon on 2018-02-28
Bee  using my Ubuntu16.04 for a few months so still so new and now it no longer boots tried a grub repair and nothing...

the error i see says that ata2: SRST failed (error=-16) then it states its slow to respond and limits to 1.5 gbps then says reset failed giving up

So thinking my SSD is playing up? Firmware?

tried to look in fstab but all looked ok i think.

Any help would be welcome, very new to ubuntu

---

### Post by TheFu on 2018-02-28
Always start by checking the system log files - google "ubuntu log files" for how to do that.
The logs will have something related which will be where you go next.

With storage, I always look at: cables, connectors, SMART data, power supplies in that order.  Of course, running an fsck can't hurt.

I don't understand what "my SSD is playing up" means. Please explain.

Firmware seldom is the issue for storage devices that aren't less than 6 months new from the vendor.  If you SSD model was just released by the vendor last month, then looking at the firmware would make sense.  If it is over 6 months old, I wouldn't worry unless you've googled and found something specific for that exact model.

Welcome to the forums.

---

### Post by coulthon on 2018-03-01
[COLOR=#000000]I don't understand what "my SSD is playing up" means. Please explain. 

[/COLOR]That is what my file system is on.

[COLOR=#000000]With storage, I always look at: cables, connectors, SMART data, power supplies in that order. Of course, running an fsck can't hurt.
[/COLOR]
Change the sata port i was in and its i have not seen the same errors but the os still crashes
Did an fsck and i get /dev/sda1: clean, 385670/7069696 files 6687163/28256512 blocks
Thinking i need to reinstall it just setting it all up was a ball ache!!!

---

### Post by TheFu on 2018-03-01
Reinstall won't fix the issues, if it is caused by hardware problems.

Also, this would be a good time to test your restore plans from those backups you've made. No better time than this, right?  Good backups are a thing of beauty. For the OS and applications and settings, it should take less than 30 minutes to have everything back like it was. No need to reinstall everything, since the restore from backup should handle that.

If you don't have a great backup solution, there are lots and lots of tools. Most are very simple for capturing the packages and personal data in /home/.  Aptik [http://ubuntuhandbook.org/index.php/2017/01/aptik-backup-ppa-installed-apps-users-data/](http://ubuntuhandbook.org/index.php/2017/01/aptik-backup-ppa-installed-apps-users-data/) is one of the easier ones, but does have limitations.

---


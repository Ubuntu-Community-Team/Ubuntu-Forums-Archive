---
title: "Printing AND home directory sharing with samba?"
date: 2006-01-19
forum: Outdated Tutorials &amp; Tips
---

### Post by moephan on 2006-01-19
I accidentally posted this in the wrong part of the forums. I reposted it here:
[http://ubuntuforums.org/showthread.php?p=669348#post669348](http://ubuntuforums.org/showthread.php?p=669348#post669348)

Thanks, and sorry for the inconvienience.

Hello,

Our situation is that we have installed Ubuntu on a desktop machine connected to a printer. Ubuntu is working perfectly and the printer is working perfectly. The next step is to make it play nicely with family's XP laptop. We need to be able to use the printer connected to the desktop and also need to be able to access home directories on the desktop from the laptop. 

Before we invest a whole weekend day, could someone let me know if it looks like this solution will work? Here is what I think might be the right smb.conf file:
[global]
workgroup = OURWGNAME
netbios name = ubuntudesktop
printing = CUPS
printcap name = CUPS
map to guest = Bad User
show add printer wizard = No
wins support = yes

[printers]
comment = Print Temporary Spool Configuration
path = /var/spool/samba
printable = Yes
guest ok = Yes
use client driver = Yes
browseable = No

[homes]
comment = Home Directories
browseable = yes
writable = yes
create mask = 0700
directory mask = 0700

Then I think we need to take the following steps:
1. put this in the right directory
2. use sudo smbpasswd -a `whoami` to create passwords for everyone who will access files
3. restart samba (?)
4. on the XP laptop go \\MIDEARTH, click on homes, log in, and see your files
5. on the XP laptop use "add printer" choose network printer, and muddle through the wizard

Any help anticipating problems are providing better alternative solutions would be very much appreciated. Thanks much.

Cheers, Rick

---


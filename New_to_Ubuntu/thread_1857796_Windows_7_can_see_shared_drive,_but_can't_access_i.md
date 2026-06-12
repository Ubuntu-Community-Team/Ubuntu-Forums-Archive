---
title: "Windows 7 can see shared drive, but can't access it"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by pathos_society on 2011-10-11
Hello, first time poster, long time Windows user, total noob to Linux.

I have Ubuntu Desktop installed on a machine (MELFINA) that I intend to use as a home server.  I have a hard drive (YUKI) that I want to share with my Windows 7 computer.  

I can access everything on the Windows 7 computer from the Linux box easily.  However, in Windows 7, MELFINA appears when I click Network.  I double-click MELFINA and YUKI appears as a shared folder.  I double-click YUKI and I get:

"Windows cannot access \\Melfina\yuki

You do not have permission to access \\Melfina\yuki.  Contact your network administrator to request access."

I've run net usershare info and testparm -s:

pathos@MELFINA:~$ net usershare info
info_fn: file /var/lib/samba/usershares/yuki is not a well formed usershare file.
info_fn: Error was Path is not a directory.

pathos@MELFINA:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[YUKI]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = CGROUP
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[YUKI]
    path = /media/YUKI
    read only = No
    guest ok = Yes

Of course, total Linux noob and I don't know how to interpret any of that or what to do next.  Any help will be appreciated.

---

### Post by mastablasta on 2011-10-11
you need to enable sharing for the drive in MELFINA. Also you may need ot install aditional SAMBA (win-linux sharing service) packages.

---

### Post by alexanderedward on 2011-10-18
> **mastablasta said:**
> you need to enable sharing for the drive in MELFINA. Also you may need ot install aditional SAMBA (win-linux sharing service) packages.

i have the same query as the OP.
can someone elaborate on how to enable sharing for the drive?
how would i know if i need to install additional samba packages?

many thanks
alexander

---

### Post by kemtnbkr on 2011-10-18
I'm mostly a n00b myself, but from what little I know, you'll need to install samba to have Windows computers on the network access the shared drive.  (Samba is the Windows within-network file-sharing protocol (if that's the right word)).  

It's relatively easy to setup; just follow these instructions if you're running 11.10: [http://www.unixmen.com/linux-tutorials/566-install-samba-server-in-ubuntu-karmic](http://www.unixmen.com/linux-tutorials/566-install-samba-server-in-ubuntu-karmic)
If you're running an older version, I'm sure you know how to use Google.;)

Once you have samba properly set up, you should be able to access your shared drive with a Windows computer just fine.  I've had it set up in the past, and (as long as you have the proper permissions set) you can read/write to the drive just fine, even if its in a format Windows doesn't recognize.  (I have a 1TB external HD I had set up like this; it is ext4, and windows can read-write to it b/c it's 'wrapped' by the linux OS).  I've never tried to access it with a computer running linux as I only have one, but that may require a different solution, I wouldn't be the one to ask about that.

---


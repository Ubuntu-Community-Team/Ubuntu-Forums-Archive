---
title: "Can't access Ubuntu 12.04.3 from Windows 8 or Mac"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by Joe_Bland on 2013-09-10
I am setting up what I think is a really simple NAS using Ubuntu Server, which has the OS on an SSD and the data in a RAID 1 array.

I want to access the RAID which is at /mnt/nas on all computers on my network of 2 x Windows 8, 1 x Windows 7 and 1 x Mac which are connected by ethernet through a modem router, which dishes out dhcp. I don't care who accesses/reads/writes/changes info on the NAS within our LAN. I plan to install Crashplan on the NAS later, to back up remotely, but won't be using the NAS for anything else.

I have set up Ubuntu, given it static IP, installed and configured Samba and Webmin, created a guest user (studio) in a group (users) and created a Samba share. I can see this on the network from the Win 8 computer.

I've read what I can understand of other posts here and elsewhere, but I just can't get Windows to allow access to the shared directory. Either it says access is denied, or that the directory is no longer available.

I can connect to the NAS with putty, no problem. I'm a bit slow on using the terminal, so if you I need to enter anything there, if you could please let me know in full lines that would be awesome. 

The output of testparm -s is:[INDENT]Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[univers-0]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        guest account =
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
        idmap config * : backend = tdb
        guest ok = Yes

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        guest ok = No
        printable = Yes
        print ok = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        guest ok = No

[univers-0]
        path = /mnt/nas
        force user = studio
        read only = No
        create mask = 0777
        directory mask = 0777

[/INDENT]
Please help! Thank you!!!! :) :smile: :smile:

---

### Post by TheFu on 2013-09-10
Let me rephrase the question, to be certain that I understand.

You have an ubuntu server (no GUI) that you want share files using samba with windows and osx devices on the same LAN.
For some reason, you've created a new userid for this purpose and want to use that for connections by all the other devices instead of using individual user accounts.  Whatever, I suppose that will work.

The RAID1 array is already working fine on the Ubuntu box.
No need to print through this box.
Only the server has a static IP, all other machines are DHCP and change LAN IPs from time to time.
No desire to use NFS for any shared storage, just samba.

Does that sound like your setup?

---

### Post by Joe_Bland on 2013-09-10
Thanks Fu! You have stated my needs correctly (and succinctly).

Few things to clarify:

1. With users, I'm just looking for the most simple solution, and don't need accounts for each user.
2. Windows 8 doesn't support NFS out of the box. Again, keeping it simple.
3. DHCP addresses are within a given range (192.168.1.x)

Thanks again.

---


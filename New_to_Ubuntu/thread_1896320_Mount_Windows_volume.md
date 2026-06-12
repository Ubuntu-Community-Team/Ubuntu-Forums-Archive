---
title: "Mount Windows volume"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by Time Traveler on 2011-12-16
Okay, here's the scenario.

I'm dual booting 11.10 and Win7 on a Dell laptop,  Everything is fine, I can access the Windows volume from Ubuntu no problem.  However when I network into Ubuntu from a remote (XP) machine on my home network, it won't immediately open the Windows volume.

The volume appears in the list but it gives me some kind of error - sorry I didn't jot down the details.

However if I just go to the Laptop and do something on the Windows volume (like use the file manager) it will then open across the network normally.

So it seems that I'm somehow causing the Windows volume to 'wake up'. I'm curious to understand exactly what is happening.

---

### Post by BC59 on 2011-12-16
You can install Storage Device Manager from Ubuntu Software center and tweak the Windows drive from there. There are various parameters you can change, so check if one of them is working for you.

---

### Post by Frogs Hair on 2011-12-16
In advanced settings under desktop see that show mounted volumes is selected . I don't know of any other settings than that .

---

### Post by jerome1232 on 2011-12-16
Following BC59's advise should remedy the problem, I believe what is happening is the volume is not set to automatically mount at boot time, and your file-manager (nautilus) mounts it for you when you click it's icon.

So if you haven't click on it in nautilus yet, it's not mounted thus you can't access it.

---

### Post by Time Traveler on 2011-12-19
Well it was an interesting weekend to say the least.

After fooling around in an attempt to fix this small problem I somehow lost all network connectivity to the Ubuntu server.  I eventually got it working but it was hit and miss, purging and re-installing packages.

Along the way I noticed that the file /etc/Samba/smbusers is empty.  I've been using the system-config-samba GUI to set things up and I have two users defined in it.  I would have expected to find them in that file, no?

Also I have the access set at user level and only specific users allowed, but I'm not getting a login prompt.  I can connect immediately from the XP machines.

---

### Post by Morbius1 on 2011-12-19
You seem to have 2 different problems that overlap because you are using an ntfs partition which is either mounting or not mounting at statup.

Let's look at samba first:

Please post the output of each of the following commands:
```
testparm -s
net usershare info --long
smbtree
```

---

### Post by Time Traveler on 2011-12-19
Edit - To avoid confusion I made a separate post for each command.

I've made changes today to smb.conf and added two users manually to smbusers.  I won't be able to see what happens until I get home from work.  I only have Internet at work so testing is a convoluted process.

Oh, the mounting problem or whatever it was is gone.  The Windows partition mounts and is fully accessible from the remote computers.  The thing I'm working on now is why am I not being asked for login credentials from remote.

Regards -

---

### Post by Time Traveler on 2011-12-19
doc@Lapper:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[root directory]"
Processing section "[Laptis]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
    workgroup = TIMELORDS
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare owner only = No
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

[root directory]
    path = /
    valid users = doc, the_doctor
    read only = No

[Laptis]
    path = /media/Laptis
    valid users = doc, the_doctor
    read only = No
doc@Lapper:~$

---

### Post by Time Traveler on 2011-12-19
doc@Lapper:~$ net usershare info --long
[laptis]
path=/media/Laptis
comment=
usershare_acl=Everyone:F,
guest_ok=n

doc@Lapper:~$

---

### Post by Time Traveler on 2011-12-19
doc@Lapper:~$ smbtree
Enter doc's password: 
TIMELORDS
    \\LAPPER                 Lapper server (Samba, Ubuntu)
        \\LAPPER\IPC$               IPC Service (Lapper server (Samba, Ubuntu))
        \\LAPPER\Laptis             
        \\LAPPER\root directory     
        \\LAPPER\print$             Printer Drivers
QUBICA
    \\DESKSUSAN

---

### Post by Morbius1 on 2011-12-19
You have a Samba Usershare defined from Nautilus that has a different path but the same name as one you have in smb.conf:
> net usershare info --long
[laptis]
path=/media/Laptis
comment=
usershare_acl=Everyone:F,
guest_ok=nGo back into nautilus and "unshare" that folder.

Is /media/Laptis the mount point of the ntfs partition? If so how are you mounting it? Maybe if we knew it's permissions:
```
ls -al /media
```Don't do anything to smbusers.

---

### Post by Morbius1 on 2011-12-19
Your posts are a moving target.
> Oh, the mounting problem or whatever it was is gone.  The Windows  partition mounts and is fully accessible from the remote computers.  The  thing I'm working on now is why am I not being asked for login  credentials from remote.You created 2 samba users on the server - doc and the_doctor. 

When Windows set up network browsing they thought it would be funny if the the Window's client passed his WIndows' login user name and Windows' login password when he browsed the share. 

If your samba user names and samba passwords match the Windows login user name and password then the credentials have already been passed and verified automatically.

---

### Post by Time Traveler on 2011-12-22
> **Morbius1 said:**
> You have a Samba Usershare defined from Nautilus that has a different path but the same name as one you have in smb.conf:
Go back into nautilus and "unshare" that folder.

Done.
> 
Is /media/Laptis the mount point of the ntfs partition? If so how are you mounting it? Maybe if we knew it's permissions:
```
ls -al /media
```Don't do anything to smbusers.

It's in fstab.

/dev/sda3                                  /media/Laptis  ntfs  defaults  0  0

doc@Lapper:~$ ls -al /media
total 24
drwxr-xr-x  4 root root  4096 2011-12-21 23:55 .
drwxr-xr-x 24 root root  4096 2011-12-11 17:11 ..
drwxrwxrwx  1 root root 12288 2011-12-21 02:33 Laptis
drwxr-xr-x  2 root root  4096 2011-12-17 01:38 sda3

---

### Post by Time Traveler on 2011-12-22
> **Morbius1 said:**
> Your posts are a moving target.
Do you shoot skeet?

> 

You created 2 samba users on the server - doc and the_doctor. 

When Windows set up network browsing they thought it would be funny if the the Window's client passed his WIndows' login user name and Windows' login password when he browsed the share. 

If your samba user names and samba passwords match the Windows login user name and password then the credentials have already been passed and verified automatically.Yes, they do match.  Well, as closely as possible.  Unix won't let me use my exact Windows name of "The Doctor" because it contains whitespace.  

However, I tried changing my Windows name to something different and it still let me in.  I'll make a different Samba password and set what happens.

I don't really care if I get straight in at home, but when I'm at work and in range of other computers and mobile devices I don't want anyone that walks in the door to be able to get into my shares.

-------------

Update: changed Samba password, now get login prompt.

---


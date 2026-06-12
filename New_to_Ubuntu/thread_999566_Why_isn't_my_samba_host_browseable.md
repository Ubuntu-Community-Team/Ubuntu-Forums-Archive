---
title: "Why isn't my samba host browseable?"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-12-02
Okay, so I can connect to shares on my ubuntu machine by mapping the drive in windows and then typing in the server ip address and then the share name (i.e., \\192.168.0.101\Storage)

However, whenever I type in the host name (\\cryptinitedemonL\Storage) it can't find it.  The server also does not show up in my network neighborhood or in the browse menu of the mapped drives.

Every other windows computer on my network shows up instantly.  But the ubuntu samba never does.


Here's my samba.conf file.
```
[global]
   browseable = yes
   encrypt passwords = true
   ;hosts allow = 127.0.0.1 127.0.1.1 192.168.0.0/24
   ;interfaces = lo eth0 127.0.0.1 127.0.1.1
   name resolve order = lmhosts host wins bcast 
   netbios name = cryptinitedemonL
   passdb backend = tdbsam
   remote announce = 192.168.0.255
   security = USER
   server string = cryptinitedemonL
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   workgroup = BRANDES
[homes]
   browseable = no
   comment = Home Directories
   writable = yes
[printers]
   browseable = no
   comment = All Printers
   create mask = 0700
   guest ok = no
   path = /var/spool/samba
   printable = yes
   read only = yes
[print$]
   browseable = yes
   comment = Printer Drivers
   guest ok = no
   path = /var/lib/samba/printers
   read only = yes
[DISK]
   admin users = root, adam
   available = yes
   browseable = yes
   comment = DISK
   path = /
   printable = no
   writable = yes
   write list = root, adam


[Storage]
    path = "/media/Storage Drive"
	available = yes
    browseable = yes
    read only = no
	writeable = yes
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = adam
    force group = adam
```

---

### Post by ghostworkz on 2008-12-02
What does the rest of the configure file look like?  That information will be very helpful in trying to figure out why you can't browse to it.

---

### Post by CryptiniteDemon on 2008-12-02
That's the entire config file.

---

### Post by Kellemora on 2008-12-02
Hi CD

As illogical as this is going to sound, try it anyhow!

The machine that is NOT seen on the LAN you need to reboot three times in a row!

We have 8 machines here, one of them is a real stickler for this too!  After an upgrade or a power outage, it never shows up back on the LAN without going through the three reboots.

My theory regarding this is as follows:

When your computer boots up, it looks for the Samba configuration file in /var/lib/samba NOT at the smb.conf file.  This is a binary file, NOT editable by us humanoids!
If you boot up a second time, the computer says to itself, wonder WHY he did that?  Maybe I had better check the smb.conf file to see if something was changed.  OK it has, so it boots up from the smb.conf file THIS TIME.
But if you wait, next boot-up it will look to /var/lib/samba again.
However, if you do a third bootup in a row, it will then write the smb.conf file to the /var/lib/samba file and then should work until you get an upgrade or a power outage without normal shut-down routine.

I know it sounds illogical, but it has been working for us now this way for like 3 months or longer.  Even the persnickety machine will come on-line and be visible to the LAN after 3 reboots in a row.
Provided of course there is nothing wrong with the smb.conf file to start with.  The default smb.conf file is usually correct!  The only thing you need to change is your WORKGROUP to the proper name.

It helps to have smbtree and smbclient installed.
If you type smbtree in terminal and ALL of your shares don't show up, remove smbfs from your system and see if they show up then.  In ALL cases, I've had to remove smbfs (if installed) to see all of our shares!

TTUL
Gary

---

### Post by ghostworkz on 2008-12-02
I'm going to assume you are adding and converting the unix users to samba users?

Disable the name resolution line, netbios, and socket options
Also, take the comments out of this line:
```

path = "/media/Storage Drive"

```

So it should look like this:

```

path = /media/Storage Drive

```

---


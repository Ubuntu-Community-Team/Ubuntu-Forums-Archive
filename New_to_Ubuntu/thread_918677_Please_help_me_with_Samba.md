---
title: "Please help me with Samba"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-09-13
Okay, I've followed every freaking guide that I can on this thing and I just can't get it to work.  Once upon a time it did, but not for the last year.

So I've completely removed it from my system and did a fresh install.  

I have it set to where my share is browseable, but neither ubuntu or windows ever sees it when they browse.  And when I try to map the network drive from windows, it won't use the host name at all.  I still have to type in the ip address (\\192.168.0.101\Storage) and then windows tells me that an extended error has occurred.

Here's my smb conf file.  Please for the love of god help me with this because I just can't get the freaking thing to work.

```
[global]
    ; General server settings
    netbios name = cryptinitedemonL
    workgroup = BRANDES
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = yes

[Storage]
    path = "/media/Storage Drive"
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = adam
    force group = adam
```

---

### Post by tangibleorange on 2008-09-13
try changing "security=user" to "security=share". although it's not very secure, you can at least test to make sure if that's the problem. 
also, change "guest ok=no" to "guest ok=yes"
after you've changed it, restart your samba server with:

```
sudo /etc/init.d/samba restart
```

---

### Post by CryptiniteDemon on 2008-09-13
That didn't do anything.  Now it just tries to make me authenticate with guest and a password.

---

### Post by whitethorn on 2008-09-13
I'm not quite sure if this helps, but have added a samba user already?  I had that problem once, installed samba got everything running then forgot to add a user.

```
sudo smbpasswd -a adam
```  

then input a password.

and then restart samba

```
sudo /etc/init.d/samba restart
```

You might also want to check under System -> Administration -> Users and Groups then Manage Groups, if you user is in the sambashare group

---

### Post by CryptiniteDemon on 2008-09-13
Yeah, I've always had the users in sambashare.  Shows up on the group manager too.  The thing just won't work for me. It's probably some stupid little insignificant thing that nobody would think of.

---

### Post by CryptiniteDemon on 2008-09-13
See now I removed samba and when I reinstall it, it goes through the process fine, but there is no samba folder in /etc, so I can't freaking edit the smb.conf file.  

WTF?!  This is driving me insane.


Edit - Al /etc/init.d/samba restart also returns an error now.  It says it doesn't exist.  Earlier I remove the /etc/samba folder, but that's it.  I don't know why it would even affect the other folder.  Any way to fix this?

---

### Post by gregphil on 2008-09-13
You need to slow down and check each step.

1.  How are you shares done on the Windows machine?
   a.) are they anonymous (guest) or authenticated (per user)?
   b.) what WORKGROUP = domain are the Windows machines set to?
   c.) do you have a fire wall running? (try turning it off to get this working)

2. On the ubuntu box
   a.) is Samba fully installed (do PS  -A and you should see two copies of
smbd running and one copy of nmbd)  This needs to be true.....
   b.) in your /etc/samba/smb.conf is the workgroup=WORKGROUP set to the same workgroup as the Windows boxes?  If you change this file you need to restart samba with something like /etc/init.d/samba restart  (as root)
   c.) do you have a firewall (iptables) enabled?  (disable it for now)

Ok, now can you ping each other (I am going to assume you know how to do a ping test).  You MUST be able to ping in both directions.

If you have gotten this far you are getting close.  First lets try connecting as a client from the ubuntu box to each Windows box.  From a ubuntu console (terminal window) try these command line commands:

[ BTW sharing takes about 12 minutes (really) to be fully up and running on a peer-to-peer network when there is no server, so wait 12 minutes after the most recent samba restarts or Windows re-boots ]

smbtree    (you should be prompted for a password)

This should list all the shares in the WORKGROUP configured in the smb.conf file that are available to your logged on user hosted by any computer on your subnet.  If there are error messages, pay attention to them

smbclient -L COMPUTERNAME    (would do the same for one specific computer)

These should both return the shares you think you have configured on the Windows boxes.  If not check they type of sharing again (authenticated or anonymous) and make sure the Windows configuration and the smb.conf file agree.  In smb.conf this is the "security=USER" or "security=SHARE" line

As mentioned in the earlier posts you need to add any users you want to allow to connect from the Windows box to the ubuntu box in the samba password data base (this is separate from the /etc/passwd data).  Basically you need to add each user with smbpasswd -a USERNAME and supply the password twice.

I think I have typed enough to get you going, I will respond when you post your error messages.

Finally (before you get you hopes up) there is a bug in the gnome gvfs library that makes it impossible for gnome GUI applications (like nautilus network file browser) to BROWSE authenticated shares from Windows boxes.  They can browse anonymous (= no security) shares ok however.  The legacy command line samba commands I listed above and the KDE applications don't have a problem because they don't link to the gnome library.   See:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)
[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

This does not mean that nautilus can not CONNECT to the share, you just need to type in the full path to the share (which is not browsing).  Click on the pencil in nautilus network file browser to switch to text mode in the target dialog box.

For reference here is my working smb.conf file that shares my entire ubuntu disk (not recommended) and allows "root" or "greg" full write access to the disk.  Believe it or not, I trust myself.  Normally the final share, at the bottom of the file, would just be to a "transfer" or "temp" directory.  So change the "path=/"  to some directory you want to share.  The privledges on the shared directory need to be set so the connecting users have the right to "see" or modify files in it (try 0777 to allow everything at first)

[HTML]<pre>

[global]
   browsable = yes
   encrypt passwords = yes
   hosts allow = 127.0.0.1 127.0.1.1 192.168.0.0/24
   interfaces = lo eth0 127.0.0.1 127.0.1.1
   name resolve order = lmhosts host wins bcast 
   netbios name = LIVING-ROOM
   passdb backend = tdbsam
   remote announce = 192.168.0.255
   security = USER
   server string = LIVING-ROOM
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   workgroup = WORKGROUP
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
   admin users = root, greg
   available = yes
   browsable = yes
   comment = DISK
   path = /
   printable = no
   writable = yes
   write list = root, greg

</pre>[/HTML]

Note you would need to correct or comment out the "hosts allow" line, and the WORKGROUP and the computer name (LIVING-ROOM).  The "remote announce" setting might also need to be corrected or commented out, it was my attempt to shorten the 12 minute discovery time on my sub-net.  This works with ubuntu 8.04.1, kubuntu 8.04.1, KDE4.1.1 kubuntu 8.04.1 on my sub-net and allows browsing to my Windows Xp boxes and a couple of CentOS 5.2 linux boxes.

---

### Post by CryptiniteDemon on 2008-09-17
Anyone know how I can get it to put those files back in?  Every time I reinstall samba it doesn't put in the samba.conf file, or the /etc/init.d/samba file.  And the thing is that I didn't even delete the init.d/samba file manually.

---

### Post by NullHead on 2008-09-18
Well ... under normal circumstances, I'd never ever do this ... but it would seem that apt is completely sure that it's samba is fully installed. 

I **do not** like doing this; only had to do it once. 

I'd try downloading the .deb for samba manually, and forcibly installing samba ... [http://packages.ubuntu.com/hardy/samba](http://packages.ubuntu.com/hardy/samba)

Assuming the deb is on your desktop and your terminal is pointing at the desktop, *cd ~/Desktop*, run this command: ```
sudo dpkg -i --force-all samba_3.0.28a-1ubuntu4.4_*
```

If anyone has a better suggestion, let it be known, but I'm pretty sure that should get you your proper files for samba back.

---

### Post by RavUn on 2008-09-18
Why not use the GUI system-config-samba... don't have to configure much.  I got tired of the .conf file so I just use that and it's really easy.  Make sure everyone's in the same workgroup.

---

### Post by CryptiniteDemon on 2008-09-18
> **NullHead said:**
> Well ... under normal circumstances, I'd never ever do this ... but it would seem that apt is completely sure that it's samba is fully installed. 

I **do not** like doing this; only had to do it once. 

I'd try downloading the .deb for samba manually, and forcibly installing samba ... [http://packages.ubuntu.com/hardy/samba](http://packages.ubuntu.com/hardy/samba)

Assuming the deb is on your desktop and your terminal is pointing at the desktop, *cd ~/Desktop*, run this command: ```
sudo dpkg -i --force-all samba_3.0.28a-1ubuntu4.4_*
```

If anyone has a better suggestion, let it be known, but I'm pretty sure that should get you your proper files for samba back.

I get the following message when installing:

>  sudo dpkg -i --force-all samba_3.0.28a-1ubuntu4.4_i386.deb
dpkg - warning: downgrading samba from 3.0.28a-1ubuntu4.5 to 3.0.28a-1ubuntu4.4.
(Reading database ... 155240 files and directories currently installed.)
Preparing to replace samba 3.0.28a-1ubuntu4.5 (using samba_3.0.28a-1ubuntu4.4_i386.deb) ...
Unpacking replacement samba ...
dpkg: samba: dependency problems, but configuring anyway as you request:
 samba depends on samba-common (= 3.0.28a-1ubuntu4.4); however:
  Version of samba-common on system is 3.0.28a-1ubuntu4.5.
Setting up samba (3.0.28a-1ubuntu4.4) ...

Configuration file `/etc/init.d/samba', does not exist on system.
Installing new config file as you request.
 * Starting Samba daemons                                                [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba

---

### Post by CryptiniteDemon on 2008-09-18
Okay, I figured out why it was failing.  For whatever reason it just wouldn't create the smb.conf file by itself, so I put a generic one on there and then everything worked fine.  

So here's my new smb.conf file below.  I can access the shares but I'm still having trouble with mapping the network drives.  This time around in windows when I hit map network drive, my server shows up under the browse section, but none of the shares do under it's tree.

Also, the spot where you can type in \\servername\share, well it won't map a share if I use \\cryptinitdemonL\DISK, but it'll map \\192.168.0.1\DSIK just fine.

```
[global]
   browsable = yes
   encrypt passwords = yes
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
   browsable = yes
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

### Post by gregphil on 2008-09-19
NetBIOS names use to have a length limit of 14 characters (in NT4).  And the character at the very end had special meanings.

I would try shortening your computer NetBIOS name.

---


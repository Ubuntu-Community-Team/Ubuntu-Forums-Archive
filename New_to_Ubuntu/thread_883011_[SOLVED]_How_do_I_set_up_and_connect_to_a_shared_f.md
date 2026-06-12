---
title: "[SOLVED] How do I set up and connect to a shared folder on Windows?"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by KIAaze on 2008-08-07
I managed to access a shared folder on my ubuntu machine from windows using this tutorial:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

However, now I would like to access a shared folder on Windows from Ubuntu.

I tried the following 3 solutions:
1) Places->Connect to server: Nothing happens after entering username+password
*settings used:
service type: Windows share
server: IP address of Windows machine
share: SharedDocs
Domain name: MSHOME (as indicated by windows system properties)
*username+password used: the ones of the windows account

2) [http://note2.industriousone.com/mounting-windows-shares-ubuntu](http://note2.industriousone.com/mounting-windows-shares-ubuntu) : sudo mount -a never ends and no error messages

3) [http://ubuntuforums.org/showpost.php?p=4920136&postcount=11](http://ubuntuforums.org/showpost.php?p=4920136&postcount=11) : Same as previous.

And of course, nothing to see in Places->Network.

My setup:
-Ubuntu laptop + Windows XP desktop connected to the internet over WPA wireless.
-I enabled sharing on the default "shared folder" in windows ("Gemeinsame Dokumente" in German).
Right-click properties shows that its name is "SharedDocs".
-"Sharing allowed for all users on the network" checked.
-"Write access" unchecked

So how can I access this shared folder from my Ubuntu laptop?

My current /etc/samba/smb.conf:
```
[global]
    ; General server settings
	netbios name = KIAaze-LAPTOP
	server string = 
	workgroup = MSHOME
	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

	passdb backend = tdbsam
	security = user
	null passwords = true
	username map = /etc/samba/smbusers
	name resolve order = hosts wins bcast

;	wins support = no

;	printing = CUPS
	printcap name = CUPS

;	syslog = 1
	syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
	path = /var/lib/samba/printers
;	browseable = yes
	guest ok = yes
;	read only = yes
	write list = root
	create mask = 0664
	directory mask = 0775

[printers]
	path = /tmp
	printable = yes
	guest ok = yes
	browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
	path = /home/samba/
;	browseable = yes
	read only = no
;	guest ok = no
	create mask = 0644
;	directory mask = 0755
	force user = KIAaze
	force group = KIAaze

```

---

### Post by bobnutfield on 2008-08-07
Try Places>Connect to Server.  Put the IP address of the Windows machine in the proper place.  If the folder on the Windows machine is shared, you should be able to access it.

---

### Post by KIAaze on 2008-08-07
That's what I tried and nothing happens.

---

### Post by bobnutfield on 2008-08-07
Sorry, I read your post too quickly.  You did mention that you had already tried that.  Do you have a firewall running on your Windows machine?  That has prevented me from accessing it in the past.

---

### Post by KIAaze on 2008-08-07
YES! It's working.
It was because of the firewall. Thanks. :)

I used:
```
sudo mount -t cifs //ip/shareddocs /media/network
```

"Places->Connect to server" gave me this error message even after unmounting /media/network:
> Could not display "smb://IP/shareddocs/".
Error: DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered
Please select another viewer and try again.


But at least one method works.

---


---
title: "Can't see windows shares from hardy"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Jiff77 on 2008-06-22
Well i finally decided to delve into the world of linux and hearing from a friend that ubuntu is the best way to go, I installed Hardy 3 days ago. I have samba installed and configured properly (to the best of my knowledge), and can see shares on my ubuntu machine from windows, but not the other way around. I see the workgroup as well as the machine itself in windows network, but when opened it is blank. I've tried troubleshooting with various guides and how-to's but to no avail. My smb.conf file looks as follows...

[global]
    ; General server settings
    netbios name = keith
    server string =
    workgroup = ARCADIA
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
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
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/share
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = keith
    force group = keith

Would my best bet to be to go to a different version? I've read some things about Hardy that have me wondering. I'm out of ideas and ready to bang my head against the wall in frustration. :x Any help is greatly appreciated as I am enjoying linux thus far aside from this problem that i cant seem to resolve. Thanks again.

---

### Post by mankygitt on 2008-06-22
First - welcome to Ubuntu - each release it gets more and more fun for the many of us who are moving away from the non-open source platform(s).

Secondly - running Ubuntu 7.10 (the previous release), browsing your windows network and accessing shares was very easy. I believe the change in Hardy 8.04 LTS in the file management design has made the job a bit harder. I hope it gets sorted soon. It has been reported by myself and many others as a problem.

In the meantime, the only work-around I have found is as follows:
1. Firstly you need to know the machine and share name you want to connect to.
2. You need to mount the share: There's an easy way to do this in the Ubuntu interface: Click on Places > Connect to Server ...
Choose "Windows Share".
Enter the machine host name or IP address, the share name. The rest is optional.
If you need to supply different credentials (user name/password/domain) to access the share, enter these.
Click ok
3. This, as I said is a work around. I nearly always get an error message when doing the above, but then if I check "Places" the share is there and accessible to browse.

Good luck, keep on with it, and hopefully the limitation introduced in this current build of Nautilus is addressed in a subsequent update.

---

### Post by Dedoimedo on 2008-06-22
Hi,

See if this helps you:

[http://www.dedoimedo.com/computers/linux_commands.html](http://www.dedoimedo.com/computers/linux_commands.html)

[http://www.dedoimedo.com/computers/linux_commands.html#network_sharing](http://www.dedoimedo.com/computers/linux_commands.html#network_sharing)

Cheers,
Dedoimedo

---

### Post by sea_monkey987 on 2008-07-01
are you able to ping your windows computers by their host names?
Also, try this in nautilus address bar (Ctrl + L)
```
smb://IPADDRESS_OF_WINDOWS_COMPUTER/
```

---

### Post by mankygitt on 2008-07-01
using CTRL + L in Nautilus and entering smb://hostname returns no results, but smb://hostname/share works. THe problem is if you need to browse to identify the share name first, you're kinda stuck. a workaround is to try the default shares (c$, d$, etc) to browse for the folder names that might be shared in the hope that the share name matches the folder.. then connect again to that share. (if your access to the admin share c$ is read only and you need write access).

Being able to locate hosts, and shares, was previously available and very functional in Nautilus - it is the 8.04 installation (both fresh and upgraded) where it no longer works.

---


---
title: "Problems with getting people acess to samba"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Comandos on 2008-07-26
hi,
I have a samba server with 3 shares. I'd like different users to have access to only one share. I tried to tell samba to do that but all users can go to whatever share they want currently. Here's my file:


[global]
    ; General server settings
    netbios name = family-desktop
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    invalid users = root bin daemon adm sync shutdown \


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
    ;path = /home/samba/
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

[eyal]
    path = /home/samba/eyal
    browseable = yes
    read only = no
    read list = eyal
    write list = eyal
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user =
    force group =

[gal]
    path = /home/samba/gal
    browseable = yes
    read only = yes
    guest ok = no
    writeable = no
    write list = gal
    read list = gal
    valid users = gal
    create mask = 0644
    directory mask = 0755
    force user =
    force group =

[ehud]
    path = /home/samba/ehud
    browseable = yes
    read only = yes
    guest ok = no
    writeable = no
    write list = ebartfeld
    read list = ebartfeld
    valid users = ebartfeld
    create mask = 0644
    directory mask = 0755
    force user =
    force group =

---

### Post by bab1 on 2008-07-29
Use the share:```
[homes]
``` for that sort of thing.  Make sure that the login on the windows box is the same as smbusers.  I use homes for my Samba setup.  The logged in user can only see and access their share.

---


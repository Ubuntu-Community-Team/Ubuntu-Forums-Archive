---
title: "How to setup up home network"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by wariskampar on 2008-06-22
My question may sound too stupid for some people but please bear with me because I really dont have any idea to start home networking. Since I'm noob, i will explain my intention (setup home networkng)in a non techy term. Here it goes;
1) I have 1 Ubuntu Hardy Heron Lappy, 1 XP Home lappy and Linksys Wireless Router (WRT54GC)
2) Ubuntu unit is connected by ethernet cable while XP is connected wirelessly

I would like to share files between these laptops and if possible sharing the printer as well (i use HP PSC 1500 series). Could someone be kind enough showing me the right direction (Tutorial, link etc) to achieve this. Thanks in advance.

---

### Post by lisati on 2008-06-22
Good questions. 


[LIST]
[*]On your windows machine, you will probably need to run its "Setup a home network Wizard" if you haven't already done so. If you want to share any printers connected to it you will also need to turn on file and printer sharing.
[*]On your *buntu machine, you might find it helpful to set up "samba". Instructions on how to do so can be found at [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) which also has some instructions on what to do on your Windows machine.
[/LIST]

---

### Post by Skerit on 2008-06-22
Why did they decide to remove the "Shared folders" tool, anyway? 
What where they thinking of!? 

I've been bitching about not being able to setup a samba network without having to use the CLI since I started using 5.10 and now they just *removed* it entirely? Could anyone explain the logic behind it, please?

---

### Post by wariskampar on 2008-06-23
I already setup SAMBA in my Ubuntu box. Before that I ping each unit from each other and connection was established. How do I set my XP though because i think something is missing. When I tried to map my ubuntu shared folder (/home/myname/samba), XP prompted that it could not find server. When I look in Windows Network at Nautilus, i dont see any folder. Here is my smb.conf;

[PHP][global]
    ; General server settings
    netbios name = HARDYHERON
    server string =
    workgroup = FAMILY
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
    path = /home/aznan/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = aznan
    force group = aznan
[/PHP]

Hope someone is kind enough to guide me through

---

### Post by kismeras on 2008-06-23
I too am having a similar issue. XP machine can see Ubuntu shared files. However, Ubuntu can see XP machine, but not the shared files. If i switch XP to simple file sharing, then Ubuntu will see the files, but i do not want to use simple file sharing. Thanks.

---

### Post by k3lt01 on 2008-06-23
Well I am the exact opposite, my Ubuntu machines can see all the Windows machines on my home network but the Windows machines cant see the Ubuntu machines and the Ubuntu machines cannot see each other. In the holidays in 2 weeks time I want to finish setting up my Ubuntu server and have the printer on it for everyone to use.

---


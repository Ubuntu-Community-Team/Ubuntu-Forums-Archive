---
title: "Samba V3.5.11 on Desktop 12.04"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by rubiconza on 2012-06-03
Hi guys

I am trying to share my *series* directory on my Ubuntu 12.04 desktop version with my mates at home.

They are all running Windows 7 Ultimate

My PC and my smb.conf

My PC has an extra drive installed and it is showing under media as Storage

so I have the following "directory"

/media/Storage/series

The ownership looks like this

> drwx------ 1 stefanv stefanv    4096 2012-01-29 11:31 series
As for my config file it looks like this

> 
[global]
    workgroup = workgroup
    netbios name = Babylon
    wins support = yes
    log level = 1
    max log size = 1000
    read only = yes
    security = user
    local master = yes
    preferred master = yes
    os level = 33
    guest ok = No
 
[homes]
    comment = %u's Home Directory
    path = /home/%u
    browsable = no
    read only = no

[Share]
    path = /share
    writable = yes
    browsable = yes
    guest ok = yes

[Series]
    path = /media/Storage/series
    browsable = yes
    guest ok = yes
I have an Ubuntu user called stefanv, I also have a virtual box running inside my Ubuntu which has Windows 7 Ultimate on it.  The username for my Windows 7 is also stefanv and the password on the ubuntu and on the windows is exactly the same.

From my stefanv user on the Windows VM I can see my Samba Server broadcasting my linux hostname (stefan-pc) instead of my netbios name which is Babylon.  I can browse to it without suppling a username and password which I take it is because I am set to user level security and because both my usernames and passwords on both the machines are the same.

Only problem I have is that I see my linux hostname and not my netbios name, any ideas why?

That was my first issue, now my second issue

Now I want to share my directories with my mates, but I don't want to create physical users on my box for them, is there any other way I can do it so that they just have "read" access to my files but without write or execute capabilities?

On my Windows 7 VM I created another user called masterofdisaster, but I didn't create a linux user for him, but sadly he can't even browse to the server without supplying a username and password.

Any advice would be most welcome

---

### Post by rubiconza on 2012-06-04
Hey guys, do you have any ideas for me?

---


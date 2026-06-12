---
title: "How to remove 'duplicate sources.list entry'"
date: 2015-02-07
forum: New to Ubuntu
---

### Post by yash_pal2 on 2015-02-07
Ubuntu 14.04 64 bit; 4Gb RAM; dual boot with Windows 7; No PPAs except for GIMP 2.8.14
Whenever I update/upgrade the OS, I get this message while upgrading:

   [SIZE=2]Reading package lists... Done                                                  [/SIZE] 

 [SIZE=2]W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-amd64_Packages)

This same wording is repeated 8 times and then,
   [/SIZE]

[SIZE=2]W: You may want to run apt-get update to correct these problems[/SIZE]

[SIZE=2][SIZE=2]Reading package lists... Done                                                  

I have run sudo [SIZE=2]apt-get update or [SIZE=2][SIZE=2]sudo [SIZE=2]apt-get dist-upgrade or [SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2]sudo [SIZE=2]apt-get autoremove, but these messages keep appearing.

Could anyone tell me how to remove the duplicate.

[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
[/SIZE]

---

### Post by kerry_s on 2015-02-07
use dash to search for "software & updates" look under "other" tab, just highlight & remove the duplicate entry.

---

### Post by yash_pal2 on 2015-02-10
Thanks, I will try it. My internet connection was down for last 2 days and I could not access the site

---


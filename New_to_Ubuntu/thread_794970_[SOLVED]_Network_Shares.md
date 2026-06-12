---
title: "[SOLVED] Network Shares"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Blue Lightning Computers on 2008-05-15
Hi

I am trying to setup network shares to windows servers in ubuntu 8.04 i select "Conect to Server" with service type "Windows Share" the server name share as the folder i want access to and my username for that pc after asking for my password it says it the location is not mounted can someone please help

---

### Post by oedha on 2008-05-15
here's what i did :
open terminal : ==> sudo mkdir /media/x
then :==> sudo mount -t smbfs //computername/foldername /media/x -o username=username,password=password

username can be folder name......
and you may also not to type password=password...you will be asked if you didnt type it

---

### Post by Blue Lightning Computers on 2008-05-15
hi oedha

i tried that and this is what i got

mount: wrong fs type, bad option, bad superblock on //beta/apps,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


any ideas???

---

### Post by exile on 2008-05-15
I haven't had this problem myself but maybe trying [http://note2.industriousone.com/mounting-windows-shares-ubuntu]("http://note2.industriousone.com/mounting-windows-shares-ubuntu") will help?

Good luck.

---

### Post by Blue Lightning Computers on 2008-05-15
thanks guys iv got it sorted now

---


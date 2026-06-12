---
title: "HELP!!, crash after upgrade."
date: 2008-04-26
forum: New to Ubuntu
---

### Post by joemacnz on 2008-04-26
Help please. I upgraded to Hardy from Gutsy, and after restart, I get the following:

>   Busybox v1.1.3 (debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_



I have tried various things, including "mount hdd"
(for lack of any idea) and I got something about "can't find fstab"

---

### Post by asdzxc on 2008-04-26
I guess you've already tried it, but try to turn off the computer and start again. 

I get similar from time to time when restarting, but so far never on a cold start. Don't know why though. So it doesn't neccessarily need to be because of the upgrade..

---

### Post by joemacnz on 2008-04-26
I have restarted the computer many many times. No joy. 

I have tried >  mount /dev/hd1 

and it returned >  can't read /etc/fstab: no such file or directory 


I tried >  /etc 

And it returned permission denied, however, it brings up an error >  sudo not found  if I try anything with sudo

---

### Post by joemacnz on 2008-04-26
Please, anyone?

---

### Post by artir on 2008-04-26
Try a a clean install

---

### Post by joemacnz on 2008-04-26
How? I can't get past the origonal ASH(?) screen. Is there a small something I could download, make into a live cd so that I can get in?

---


---
title: "[SOLVED] rename workgroup"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by lincoln32 on 2008-05-02
Ubuntu 8.04 fresh install shared network drives with out installing samba??? now I need to change group name to workgroup from mshome
the guide for 7.10 do not make sense in 8.04 any ideas?

---

### Post by Barton101 on 2008-05-02
I had this issue and needed help.

In order to do this, run the following command in the Terminal:
sudo gedit /etc/samba/smb.conf

find the line that says "workgroup = WORKGROUP"
and change it to your liking.

Hope this helps :)  Andrew

---

### Post by JunCTionS on 2008-05-03
thanks, I was a bit lazy to try and find the file, this should be configurable from the GUI

for those new to this (I found it useful my first time) if you're in kubuntu you don't have gedit, so instead use kate (although it will give you warnings, ignore them) or use vim.
If using "sudo vim /etc/samba/smb.conf" use the keys to scroll to where you want to edit, then press the Insert key change what you want, then press Escape, type ":write" (without quotes) and then ":quit"

---

### Post by iamnotyou on 2008-05-13
> **Barton101 said:**
> I had this issue and needed help.

In order to do this, run the following command in the Terminal:
sudo gedit /etc/samba/smb.conf

find the line that says "workgroup = WORKGROUP"
and change it to your liking.

Hope this helps :)  Andrew


This is exactly what I was looking for, thanks

---


---
title: "ETC rights changed"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by salmendar on 2013-07-04
hi,
   the problem is that in order to change few files in mysql I ran the command sudo chown -R [user]:[user] /etc and pressed enter without typing mysql and now i am trapped as i cant do anything on my system. please help me

i am running a ubuntu server 12.04 with the basic GUIwithout any desktop applications and my system configuration is

P4 HP 3.2 GHz
4 GB ram 
80 GB hard-disk.

this is my server machine and i really need it running asap so please help....

---

### Post by Impavidus on 2013-07-04
You could try booting into recovery mode, dropping to a root shell and repairing from there. Most files/directories are owned by root:root. However, there are many exceptions, which you'll have to fix manually. You can also backup everything and reinstall.

To edit files in /etc use sudo. If there are a lot of them, copy them to your home dir, modify them and copy them back when finished. This is much safer than changing ownership or permissions of fies in /etc or any other system directory.

---

### Post by salmendar on 2013-07-09
I used the recovery like you suggested but a little google searching helped me and su- commands in the sudoers file did the trick... 
thank you very much for your help.

---


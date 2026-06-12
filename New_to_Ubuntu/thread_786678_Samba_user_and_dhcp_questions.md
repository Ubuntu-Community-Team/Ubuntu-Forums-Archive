---
title: "Samba user and dhcp questions"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by baddnady23 on 2008-05-08
2 questions in regards to samba.  After the upgrade to 8.04, I seem to be having an issue with it.  When I right click to share a folder from my ubuntu machine, it will show up in my windows machine and now it requires a password, which i apparently do not know.  The user name it gives is the same as my ubuntu computer name.  do I have to configure somehow my smb.conf for this?

2nd question is that I was wondering if there is a way to configure samba to dhcp so that i don't have to keep restarting it every time the ip addresses change?

Thanks

---

### Post by adwatkin19 on 2008-05-08
Hiya fella dont know about the second question but if you look at post 3 in this link

[http://ubuntuforums.org/showpost.php?p=3036386&postcount=3](http://ubuntuforums.org/showpost.php?p=3036386&postcount=3)

it will sort you out with the password issue, i had the same thing, and this worked a treat. 

Adam

For got to add something, you mostly need to look at the bit about editing the samba config file. (the last part of it)

---

### Post by baddnady23 on 2008-05-08
thanks but still no dice :-(

---

### Post by superprash2003 on 2008-05-08
always restart samba after making changes sudo /etc/init.d/samba restart .. try following the samba guide here [http://ubuntuguide.org](http://ubuntuguide.org) especially make sure that you add users in the smbusers file as shown in the tutorial

---

### Post by hyper_ch on 2008-05-08
assign static IPs in your lan... then it will always be the same.

---


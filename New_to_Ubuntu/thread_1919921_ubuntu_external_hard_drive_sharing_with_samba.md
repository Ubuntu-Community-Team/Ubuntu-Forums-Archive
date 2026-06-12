---
title: "ubuntu external hard drive sharing with samba"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by luca616 on 2012-02-03
when i try to share my external hard drive from ubuntu to my win7 laptop, i get an error after trying to browse it from windows saying

windows cannot access \\lucaserver\m

you do not have permission to access \\lucaserver\m

i can share the music and pictures folder perfectly. this only happens with the external hdd.

---

### Post by luca616 on 2012-02-03
also i think the fact that it is formatted to ntfs is part of the issue

---

### Post by luca616 on 2012-02-04
*bump*

---

### Post by Morbius1 on 2012-02-04
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Then add the following line to the share definition for [m]:
```
force user = morbius
```[COLOR=Blue]*Change morbius to your own local login user name*[/COLOR]

Then restart samba:
```
sudo service smbd restart
```By default an external ntfs partition will mount with you as owner and with access enabled only to you. Using 'force user" converts the remote user to you for that share.

---

### Post by luca616 on 2012-02-05
thanks for the reply but i just ended up formatting to fat. that seemed to fix it. thanks anyways though

---


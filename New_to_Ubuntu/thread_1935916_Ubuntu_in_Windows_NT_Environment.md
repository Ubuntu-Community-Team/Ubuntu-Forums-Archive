---
title: "Ubuntu in Windows NT Environment"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by dbhavsar709 on 2012-03-05
Hi,

I am new with Ubuntu.. I have mix environment means we have all windows NT servers (Incl. Domain). we have windows and ubuntu client which are connected my doamin. 

I am able to connect my NT share from ubuntu client. I have set my home drive Z: as home directory in ubuntu. (in smb.conf). our users make hyperlinks to connect another files on other drive in office files (.xls or .doc etc). In windows its works fine because its easy to working with map drive. but in ubuntu any way to configure drive like 

Z: = file:///home/likewise-open/<DOMAIN>/<USER>/.gvfs/<share1> on <fileserver>/
Y: = file:///home/likewise-open/<DOMAIN>/<USER>/.gvfs/<share2> on <fileserver>/

any idea....??


Dhaval.

---

### Post by An Sanct on 2012-03-05
Which version of Ubuntu?

In my version, I have "Connect to Server" in the menu "Places", from there I can choose different types of connection, including SMB share.

Alternatively, you can check this [official walkthrough here]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") and map a permanent location.

PS. Linux not use the concept of drive letters.

---


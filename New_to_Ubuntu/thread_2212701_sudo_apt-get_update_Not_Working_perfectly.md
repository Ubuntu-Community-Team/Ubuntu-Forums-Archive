---
title: "sudo apt-get update Not Working perfectly"
date: 2014-03-22
forum: New to Ubuntu
---

### Post by MIraan_Baloch on 2014-03-22
[SIZE=2]**WHen i use to apt get update but update goes to 86% and after that this error comes**[/SIZE]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise Release.gpg     
  Could not connect to pk.archive.ubuntu.com:80 (IP), connection timed out
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates Release.gpg
  Unable to connect to pk.archive.ubuntu.com:http:
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports Release.gpg
  Unable to connect to pk.archive.ubuntu.com:http:
Reading package lists... Done
W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://pk.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Could not connect to pk.archive.ubuntu.com:80 (IP), connection timed out

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://pk.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Unable to connect to pk.archive.ubuntu.com:http:

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://pk.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Unable to connect to pk.archive.ubuntu.com:http:

W: Some index files failed to download. They have been ignored, or old ones used instead.

[B][SIZE=3]
[SIZE=2]But also i connected to internet and plz help me to solve my this problem?[/SIZE][/SIZE][/B]

---

### Post by Korkel on 2014-03-22
Can you connect to a network with cable?

Also, remove the IP in your post. ;)

---

### Post by deadflowr on 2014-03-22
Perhaps the mirror is busted
open a terminal and run
```
software-properties-gtk
```
then go down to where it says
"Download From"
and click on the selection line, then choose other.
In the new window, first try select best server
this will run and search for the best option for you.

Another option in this window is to manually choose an option.
When you think you have a good server, select okay and exit, then rerun the update command.
(It should ask to reload, this means it will re-run the update command)

Hope this helps, somewhat.

---

### Post by MIraan_Baloch on 2014-03-22
I am connect to internet from MObile Braodband LIke EVO

---

### Post by MIraan_Baloch on 2014-03-22
Thanks BOth my problem solved

---


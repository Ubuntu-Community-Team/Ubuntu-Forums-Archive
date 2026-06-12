---
title: "How to set root folder while installing Ubuntu in windows"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by pashok84 on 2011-10-10
Hi,
 
Recently i have downloaded ubuntu 11.04 used install in windows option to install ubuntu.
 
I have my harddisk partitioned my hard disk as 3x 33GB. In drive C i have windows. i completed formated drive D and used it only for Ubuntu.
 
Now i am facing a problem, ubuntu keeps saying "**_*no space available in root*_**". i have not done any settings to set root folder size.
 
Is their any settings needed to make it use full drive/ add additional space for root folder. i am not able to install any software now.
 
Kindly help me in this regard.
 
Thanks and Regards,
Ashok Kumar P

---

### Post by pashok84 on 2011-10-10
Now i understand my mistake(i hope this is mistake). when installing ubuntu through wubi i have selected only drive and not changed any this related to disk space.
 
_How to change this disk space option without uninstalling ubuntu_, as i have already configured my gmails in evolution and it has download 1.5 GB of all my 3 gmail account.
 
I don't want to download it again.

---

### Post by jtarin on 2011-10-10
The way I am reading your post.....You say > used install in windows option to install ubuntu.This would mean it is an installation of WUBI and it is installed on your C:\ drive, not D:\ drive. Before you do anything else go to your /home/usename/.evolution folder ( it will be hidden, so to view it in Nautilus you must use the menu item "View Hidden Files". Backup the folder to some other place or medium not on you Ubuntu install and then if you have to reinstall you can copy it back over.

---

### Post by pashok84 on 2011-10-10
Thanks jtarin.
 
How to make it instal in d drive and with more memory for root.

---

### Post by mastablasta on 2011-10-10
you want a real dual boot (no wubi)?
 
then check here: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
for Wubi install (install inside windows) check here: [http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
 
i would recommed realy dual boot if your D drive is empty. you dont' have to cretae manually the Linux partitions as installer does that automaticly.

---


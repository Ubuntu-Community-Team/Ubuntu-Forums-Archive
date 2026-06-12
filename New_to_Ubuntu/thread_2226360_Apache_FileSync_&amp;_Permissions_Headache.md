---
title: "Apache FileSync &amp; Permissions Headache"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by Anup_Saumithri on 2014-05-26
So heres where I am. I have an apache2 set up that wonderfully renders my PHP project. However the biggest bottleneck points I am facing in the development process are:-

1. Exporting my project from eclipse to var/www/public_html/myproj.
2. Granting 755  read-write permissions to the newly moved files/folders.

To accomplish 1., I am deleting the old myproj and copy pasting the new myproj inside my eclipse to var/www/public_html manually!

#2. Is another pain point. I have to always do sudo chmod -R 755 myproj/ after every move/modification so that necessary read writer permissions are granted.


Are there any time saver formula for the above two?

For 1. I am looking for some nice tools: eclipse plugin or otherwise that syncs up local eclipse project with the remote folder deployed inside apache www directory.

For 2. I am looking for a way of moving files so that I dont have to type in permissions everytime I make even a small changed to the deployed folder structure.

Thanks

---

### Post by newbie2244 on 2014-05-26
How about doing a bash script that would run both commands??

---


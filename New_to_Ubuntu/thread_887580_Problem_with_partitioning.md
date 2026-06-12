---
title: "Problem with partitioning"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Xm3buX on 2008-08-12
I need help partitioning ubuntu so that I can install it. The default thing was:

/dev/sda3[COLOR="White"]...........................[/COLOR]Ubuntu 8.04.1
2% (654.4 MB)[COLOR="White"]....................[/COLOR]98% (34.9 GB)

[COLOR="DarkOrange"]This part was orange[/COLOR][COLOR="White"]....... [/COLOR][COLOR="SlateGray"]This part was grey[/COLOR]

But when I click Foward or next or what ever, it says "Too small size."

Can anyone tell me what to set this to?
Thanks.

Oh, and here is a picture:
[http://i299.photobucket.com/albums/mm313/Xm3buX/ubuntu3.jpg](http://i299.photobucket.com/albums/mm313/Xm3buX/ubuntu3.jpg)

EDIT: I have tried to make the /dev/sda3 thing bigger, I put it to 10GB, but it just loaded for about 40 seconds and went back to the default partitioning thing. 

Help please!

---

### Post by bumanie on 2008-08-12
Try to manually partition, this allows you set up a /, a /home, and a swap. Advantage of a separate /home is that if something goes wrong with the filesystem, you can reinstall to / without affecting /home, thus all your data is safe. Suggest / 8-10gb; swap 1-2gb; /home as large as you like re available space.

---

### Post by phidia on 2008-08-12
From your livecd environment open a terminal from the top panel menu Applications > Acessories > Terminal and enter this > fdisk -l post the output of that here.
How large a drive are you installing to and do you have a windows or other install on there now?

---


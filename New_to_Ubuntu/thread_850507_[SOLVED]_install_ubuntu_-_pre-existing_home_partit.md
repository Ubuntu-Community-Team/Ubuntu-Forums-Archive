---
title: "[SOLVED] install ubuntu - pre-existing /home partition"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by jimmy the saint on 2008-07-05
I have been playing around with a few *ubuntu desktops and have settled on Xubuntu due to its speed, and the fact that it seems to be light years ahead of gnome in dealing with dual monitors.  How the heck does a DE as big as gnome not be able to prevent icons being placed in the dead space created by TwinView whereas a lightweight like XFCE can??  But I digress...  
 
    My question is this: I have a seperate partition (on a seperate disk in fact) that is my /home.  When reinstalling a fresh Xubuntu (to get rid of the plethora of apps from various DEs that keep popping up) how do I keep that /Home??  If I manually choose for the installer to designate that partition, will it reformat it or overwrite it, or will it simply be recognized as being the home directory?

Thanks

JTS

---

### Post by scragar on 2008-07-05
use the advanced partitioning option and set that partition to mount as /home as long as you don't check format then your data will be safe.

---

### Post by Elfy on 2008-07-05
I'm guessing that the xubuntu partitioner is similar to the ubuntu on , ther when using the manul option you

pick partition for root and edit partition to have mountpoint of /  - let it format
pick partition for home and edit partition to have mountpoint of /home  - make sure not tick in format box to not format

---

### Post by jimmy the saint on 2008-07-05
Excellent!!  Thank you both.  I just wanted to double rather than make a painful assumption!!

---

### Post by kansasnoob on 2008-07-05
Just bust out your faithful Ubuntu spiral notebook:

[https://shop.canonical.com/product_info.php?products_id=108&osCsid=c55943f5d3cda4eb4aab3a7f8abe8cd6](https://shop.canonical.com/product_info.php?products_id=108&osCsid=c55943f5d3cda4eb4aab3a7f8abe8cd6)

Then boot either the Ubuntu Live Cd or a GParted Live CD and make some notes of just what is on what partition.

Mine is quite simple now because it's fresh:

[ATTACH]76542[/ATTACH]

Keeping notes will prevent you from installing a new OS over a pre-existing partition!

---


---
title: "Ubuntu doesn't reconize the rest of my HDD"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by JustinoLatino on 2013-02-15
For some reason only a small portion of my 160gb drive is usable by Ubuntu. At first I thought it was a partitioning error but as far as I can tell it isn't. Googled around for about a half hour and scoured the forums but I didn't really know what I was looking for. Hopefully someone can shed some light. 

My tech level is fair but I'm a noob to Linux.

This was a completely empty drive right before I installed 1210 on it and so far all I've added is flashplayer, steam, and teamspeak.

The drive
[IMG]http://i.imgur.com/ECt00KF.png[/IMG]

The space left on the drive
[IMG]http://i.imgur.com/Qp7GXak.png[/IMG]

---

### Post by deadflowr on 2013-02-15
Wait, you installed 12.10 on an NTFS filesystem?

Or are you running Ubuntu through a Windows system.(Wubi, or virtualbox;virtual machine).

As far as I can tell though, the drive lists 149GIB, which is equal to 160GB.

gigabyte vs gibibyte

[http://hexus.net/tech/tech-explained/storage/1376-gigabytes-gibibytes-what-need-know/]("http://hexus.net/tech/tech-explained/storage/1376-gigabytes-gibibytes-what-need-know/")

---

### Post by JustinoLatino on 2013-02-15
Alrighty then... I just tried to check the properties of my root drive and it said that it is 140tb. I'm just going to bite the bullet and reformat AGAIN. This is like the third time I've used that Windows installer and it has never actually installed it correctly. Very aggravating.

---

### Post by carl4926 on 2013-02-15
Dang
I can't figure what you are doing

---

### Post by carl4926 on 2013-02-15
If you are trying to do a proper (real)install just boot the CD or USB, start the install and at this
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png)

Choose - Erase everything and re-install

---

### Post by Impavidus on 2013-02-15
You installed on a completely empty 160GB drive, so clearly you had the intention of making a normal dual boot. However, you did a wubi install. The wubi install made a virtual partition inside the ntfs partition present, which is from Windows' point of view a big file, 6.43GB in your case. As far as Ubuntu is concerned, that virtual partition is your root partition.

Wubi installs can be 30GB at most, so when you install a 10GB game it fills up pretty quickly. Best to do a proper install by booting from a live disk/usb and clicking install. Then select this partition to overwrite. Using the windows installer will not give you what you want.

---

### Post by Mark Phelps on 2013-02-15
It actually wasn't a "completely empty drive" when you went to install Ubuntu.  It's obviously a preinstalled Win7 PC -- as evidenced by the Window boot partition. Looks like what you did was reformat the Win7 NTFS partition -- and then used Wubi to install inside that.

If you boot from an Ubuntu CD/USB, you should have an option to Use the Entire drive.  IF you choose that, it will reformat your drive for you.

---


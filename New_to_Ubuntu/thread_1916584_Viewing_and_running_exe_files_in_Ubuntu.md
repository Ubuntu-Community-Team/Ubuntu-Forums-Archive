---
title: "Viewing and running exe files in Ubuntu"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by abhishek.purkayastha on 2012-01-28
Hi I am new to Ubuntu. I am running Ubuntu 11.10 through Wubi. I have windows 7 installed as well. There are few games installed in windows which have shortcuts in my windows desktop folder.

I can view my windows file systems from Ubuntu by going to file System>Host(which takes me to my C drive). But when I access the windows desktop folder (for eg System>Host>Users>myuser>Desktop) I can't seen any of the shortcuts or exe's. Although I can view exe files which are placed in other folders of my Windows file sysytem.

Is there a way I can see the shortcuts to these games and if I could  see them is there any way by which I can use the shortcuts to play the games from Ubuntu.

Thanks in advance.

---

### Post by 2F4U on 2012-01-28
What sense would it make to run a Windows program through Wubi/Ubuntu? Anyways, by default, you cannot run exe files from Linux. You need Wine or Windows in a virtual environment. However, I don't know if you will be able to run Wine in Wubi.

---

### Post by abhishek.purkayastha on 2012-01-28
My Windows is not currently booting right now.So until I get a repair disk to repair or re-install windows I have to make do with Ubuntu.
By the way I got the files, I was actually looking in a wrong folder. Also I download Wine to run the exe files. But the games do not seem to run properly in Wine, for eg when I run COD-2 all I get is a dark screen with sound but no graphics whatsoever.
Is there anyway to work around this?

---

### Post by Mark Phelps on 2012-01-28
You have to install the games USING Wine in order to play them, and in general, games don't do well.

You need to go to the WineHQ website, the application compatibility search page, and look up the ratings for the games you want to play.

Anything rated less than Gold is going to be a waste of time installing.

Also, modern games often need both hardware 3D acceleration and DirectX 10 support.  Unless you have one of the newer video cards and the accelerated drivers, you will not be able to play the games.

Linux is a BAD choice for trying to play Windows games.

---

### Post by abhishek.purkayastha on 2012-01-28
Thanks a lot!!

---


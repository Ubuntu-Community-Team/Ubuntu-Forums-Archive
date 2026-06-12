---
title: "how to execute .exe files in ubuntu"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by manoj_maddy70 on 2008-07-28
Hi, 
i just wanted to know how to execute .exe files in ubuntu. Is ubuntu suppotrs such kind of format?

---

### Post by sharks on 2008-07-28
There is a program called WINE([http://www.winehq.org/](http://www.winehq.org/))
It emulates some .exe files. check the website for details.

---

### Post by Perfect Storm on 2008-07-28
No, .exe is a windows format. You could use wine to run it though. What are you trying to do?

---

### Post by Elfy on 2008-07-28
Not in itself .exe are windows files.

But you can use wine to run some - it depends what it is. ALternatively run a virtual machine with windows as the guest os.

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by manoj_maddy70 on 2008-07-28
Actually i want to install real player, but it is not allowing me to do so.

---

### Post by lisati on 2008-07-28
> **manoj_maddy70 said:**
> Actually i want to install real player, but it is not allowing me to do so.

Have a look [here]("http://ubuntuforums.org/showthread.php?t=863696&highlight=real+player"), it might be of some help.

---

### Post by Vadi on 2008-07-28
The link should be [http://ubuntuforums.org/showthread.php?t=863696](http://ubuntuforums.org/showthread.php?t=863696)

---

### Post by sharks on 2008-07-28
There is a real player for linux
[http://www.real.com/linux](http://www.real.com/linux)

---

### Post by sharks on 2008-07-28
The command is: (in terminal)

su
<enter root password>
chmod a+x RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin

and at ./RealPlayer10GOLD.bin u should change to version 11

---

### Post by dew5 on 2008-07-28
check out [http://www.associatedcontent.com/article/705055/how_to_install_realplayer_11_in_ubuntu.html?cat=15](http://www.associatedcontent.com/article/705055/how_to_install_realplayer_11_in_ubuntu.html?cat=15)
might help you to download realplayer11 and then [http://www.ubuntux.org/how-to-install-the-realplayer-multimedia-player](http://www.ubuntux.org/how-to-install-the-realplayer-multimedia-player) for installation help..

dew5

---

### Post by linux6994 on 2008-07-28
If you are looking for a windows fix every now and then you can run it or any thing else any other OS virtually. Look at this post, I have used it several times as a guide for installing vmware-player on hardy.

[http://www.smokinglinux.com/tutorials/install-vmware-player-on-ubuntu-gutsy-710](http://www.smokinglinux.com/tutorials/install-vmware-player-on-ubuntu-gutsy-710)

---

### Post by bwang on 2008-07-28
> **sharks said:**
> The command is: (in terminal)

su
<enter root password>
chmod a+x RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin

and at ./RealPlayer10GOLD.bin u should change to version 11

I think the first line should be sudo -i, since su is not enabled on Ubuntu by default

---

### Post by manoj_maddy70 on 2008-07-30
how to install real player in ubuntu, as I am getting error while installing it?

---

### Post by Perfect Storm on 2008-07-30
copy and paste in/output of the terminal. It makes it easier to help you.

---


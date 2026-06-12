---
title: "total nub need some help"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by ryridesmotox on 2012-08-02
Ok so I downloaded Ubuntu onto my laptop tonight over the current windows 7 OS.  My problem is that I can't locate the programs (mostly games) that I previously had installed on my laptop.  Will I need to start windows every time I want to play some gaming programs or is there a way to import the files to the Ubuntu registry?

Thanks in advance for your help.

---

### Post by blade4 on 2012-08-02
I'm guessing you installed ubuntu as a software on Windows - and probably on the very drive where you installed your games . If so , you will find them in the /host file ( dash is your friend here )

---

### Post by Gone fishing on 2012-08-02
Programs in Windows wont just work in Ubuntu - it has its own programs. Some Windows programs including games may be installed in Ubuntu if you first install Wine. [http://ubuntumanual.org/posts/381/top-windows-games-that-run-flawlessly-in-ubuntu-using-wine](http://ubuntumanual.org/posts/381/top-windows-games-that-run-flawlessly-in-ubuntu-using-wine) [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

On the plus side you will find many programs including games in the sofware centre most are free. I also understand that steam games are being ported to Linux and Ubuntu. 

[http://arstechnica.com/gaming/2012/07/steams-newell-windows-8-catastrophe-driving-valve-to-embrace-linux/](http://arstechnica.com/gaming/2012/07/steams-newell-windows-8-catastrophe-driving-valve-to-embrace-linux/)

---

### Post by mlentink on 2012-08-02
Please read this: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by Sandertje on 2012-08-02
Windows software will simply not work in Ubuntu. You can use Wine to run windows software on Ubuntu, but more often than not that doesn't work :P

---

### Post by Breadified on 2012-08-02
Firstly, welcome to Ubuntu ryridesmotox!

If you are new to Wine you might find it easier to use PlayOnLinux to install some of your games from the lists available on there. If you are running Ubuntu 12.04 LTS (Precise Pangolin) then to install, open a terminal (through searching in Dash home or pressing Ctrl-Alt-T) and type:

```
wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
sudo wget http://deb.playonlinux.com/playonlinux_precise.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux
```If you're running another Ubuntu install or would rather download the .deb file, go to the following link and you'll get the information you need there: [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

All the best.

Edit: P.S. I recommend downloading using terminal rather than through the Software Centre as the SC doesn't have the latest version last I checked.

---

### Post by evilsoup on 2012-08-02
> **ryridesmotox said:**
> Will I need to start windows every time I want to play some gaming programs

Pretty much, yes. There are some games that work under wine or playonlinux (both in the Software Centre), but generally speaking you'll need windows for gaming.

> If so , you will find them in the /host file ( dash is your friend here )

Please don't try to boot any software from your /host, with wine or anything else: you run the risk of damaging your windows filesystem.

Another alternative, if your computer is beefy enough, is to try running Ubuntu in a virtual machine on WIndows - this will allow you to switch between the two OSs without having to restart your computer: [here]("http://www.psychocats.net/ubuntu/virtualbox") aer some instructions, if you are interested.

---


---
title: "[SOLVED] Intrepid Ibex Fresh Installatiion : Help"
date: 2008-11-29
forum: Philippine Team
---

### Post by ysNoi on 2008-11-29
Brods, I have a fresh installation of Intrepid Ibex but I could not go to the gnome. I wonder why because I think I have a successful installation because I can see the grub and I can choose between Windows XP and Ubuntu 8.10, kernel 2.6.27-7-server (Dual Booting BTW). And I could successfully launched to the Windows XP but I could not go to the gnome (desktop) of my Ubuntu.

I used the installer I got from shipit.com and able to have a valid integrity test before the installation.

When I choose to boot from Ubuntu, at the bottom of the page, there is something like these :

Ubuntu 8.10 ubuntu tty1

ubuntu login:

What should I do here...? Please help..
Thanks a lot in advanced...! :guitar:

---

### Post by __Ryan__ on 2008-11-29
I think you installed Ubuntu Server instead of Ubuntu Desktop.  The server edition does not come with Gnome or any other desktop installed.

You can either reinstall the Desktop version or install it manually on the server installation.

To do this login with your username and enter the following command.

```
sudo aptitude install ubuntu-desktop
```

---

### Post by ysNoi on 2008-11-29
> **__Ryan__ said:**
> I think you installed Ubuntu Server instead of Ubuntu Desktop.  The server edition does not come with Gnome or any other desktop installed.

Oh I didn't know this thing. This is my first time installing this server edition. 

Anyways, thanks for the quick input. I'm doing it right now using the code you gave. 5% working now, I'll update here later...!

Thanks again bro...!

---

### Post by ysNoi on 2008-11-29
It's all done...! Thanks for the quick help bro..! You're the man...! :guitar::guitar:

[IMG]http://i249.photobucket.com/albums/gg226/ysnoi_lacroxste/Ubuntu/Intrepid_Server_01.png[/IMG]

[IMG]http://i249.photobucket.com/albums/gg226/ysnoi_lacroxste/Ubuntu/Intrepid_Server_02.png[/IMG]

Again, thank you very much for the help..! :):)

---

### Post by zika on 2008-11-29
One question still lingers ...

What is the real difference between 'ordinary' and server edition of Ubuntu?

In old days when I was using Windows I know that whatever could be done to make them more server like helpped in networking and other areas.

I suspect that in Ubuntu case that is not case ... :)

---

### Post by dodimar on 2008-11-30
> **zika said:**
> One question still lingers ...

What is the real difference between 'ordinary' and server edition of Ubuntu?

In old days when I was using Windows I know that whatever could be done to make them more server like helpped in networking and other areas.

I suspect that in Ubuntu case that is not case ... :)

The Ubuntu Desktop install a windows manager (Gnome for Ubuntu and KDE for Kubuntu). The Ubuntu Server edition doens't install that graphical interface. If you install Server edition, it will only install the "base" of Ubuntu and you're going to use Command Line Interface (CLI). This is usually used for servers wherein you control everything is controlled using CLI.

Though, you can still you that graphical interface for servers. But the main point why there is no graphical interface is, once you have setup your server, you'll leave it (most servers don't use monitors). And you control the server remotely or from a different computer on the network.

---

### Post by ysNoi on 2008-12-01
Thanks for the explaination siR dodimar... :guitar::guitar:

---


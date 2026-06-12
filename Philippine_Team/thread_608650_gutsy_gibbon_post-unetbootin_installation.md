---
title: "gutsy gibbon post-unetbootin installation"
date: 2007-11-10
forum: Philippine Team
---

### Post by hydraconsole on 2007-11-10
Magandang Gabi mga Kabayan!

si rj po from Iligan City, Lanao del Norte.

After waiting for 8 hrs, I finally finished installing gutsy gibbon using unetbootin. It can boot in WinXP SP2 but it boots to a command line or terminal in Ubuntu.

How do I get the Ubuntu desktop on my screen? Did I miss something during the installation. I'm sure I chose Ubuntu Desktop in one of the options during the installation.

Need help quick!

---

### Post by loell on 2007-11-10
ano pong nakalagay na error sa terminal?

---

### Post by hydraconsole on 2007-11-10
walang error message.

it just boots up to the terminal with the cursor blinking next to my name and hostname

---

### Post by loell on 2007-11-10
type nyo po,

```
startx
```

at titingnan natin kung desktop , o may error na lalabas.

---

### Post by hydraconsole on 2007-11-10
I tried the startx but it said that it wasn't installed and that i could get it by downloading it somewhere.

I finished downloading it and it ran automatically but I get an error which i forgot to write down.

i tried running the startx again and still i get an error like this:

```
xauth: creating new authority file /home/rj/.serverauth.4326
x: cannot stat /etc/x11/x (no such file or directory), aborting
xinit: server error
```

---

### Post by hydraconsole on 2007-11-10
i thought maybe it could be a monitor or video card problem. I'm using nVidia GeForce2 MX/MX 400 64MB video card. I heard that there might be some issue with nVidia cards with Linux.

I tried to see if the system can autodetect again my video card by using:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg
```

I get an error stating that it can't find /etc/X11/xorg.conf

---

### Post by loell on 2007-11-10
hmm... Xorg is not installed, I guess the desktop stuff isn't installed yet in your system. 

may i ask your system spec? before we try to install ubuntu desktop?

---

### Post by hydraconsole on 2007-11-10
Intel Pentium 2.40GHz, 512MB ddr1 RAM, 25GB NTFS, 14.4GB ext3, 600MB swap. cd-rom (broken)

---

### Post by loell on 2007-11-10
nice , a decent spec.

install ubuntu destop by invoking,

```
sudo apt-get install ubuntu-desktop
```

---

### Post by hydraconsole on 2007-11-10
how long will that take? I'm on a SmartBro wifi connection

---

### Post by loell on 2007-11-10
depends on the network speed, but i'm also using smartbro, 
at tancha ko , about three hours min.

btw, why didn't you install through a burnt ubuntu cd?

---

### Post by ragadanga63 on 2007-11-13
> **loell said:**
> depends on the network speed, but i'm also using smartbro, 
at tancha ko , about three hours min.

btw, why didn't you install through a burnt ubuntu cd?

Oo nga.  Why not download an Ubuntu Live CD iso instead?

---


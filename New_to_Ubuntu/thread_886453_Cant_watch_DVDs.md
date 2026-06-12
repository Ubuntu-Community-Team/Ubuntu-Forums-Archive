---
title: "Cant watch DVDs"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-08-11
for some reason i cant watch dvds...i can view the files on a dvd but when i go to watch them i get errors...anyone have any ideas on how to correct this??

---

### Post by cdtech on 2008-08-11
Let me see your /etc/fstab file.......

---

### Post by Ryadt on 2008-08-11
Try in terminal```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by bpowell2005 on 2008-08-11
Hmmm...have you downloaded the proper codecs from [Mediabuntu]("http://www.medibuntu.org/")? Without those things installed, Ubuntu (out of box) won't decode DVD's properly.

---

### Post by hsienloong on 2008-08-21
Hi everyone, I installed the required packages from Medibuntu.
Now I can watch dvd's but the quality is really bad. Sometimes the movie plays really slow and then it goes suddenly really fast.

Can anyone help please?




-hsienloong

---

### Post by SunnyRabbiera on 2008-08-21
well have you tried alternative players?
Try VLC, Xine and Mplayer out, maybe one of those will work.

---

### Post by Vivaldi Gloria on 2008-08-21
**1)** Enable medibuntu repos following the "Repository HowTo" here:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

You need to enter the following commands as explained there:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

This is true for ubuntu 8.04. For other versions see that link.

**2)** Then install the following programs using the command

```
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 build-essential ubuntu-restricted-extras
```

**3)** Check if encrypted DVDs work. If not try this command in a terminal:

```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

That should do it.

---


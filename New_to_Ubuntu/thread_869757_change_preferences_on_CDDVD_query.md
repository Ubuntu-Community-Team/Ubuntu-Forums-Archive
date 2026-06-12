---
title: "change preferences on CD?DVD query"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Midgetprawn on 2008-07-25
OK I have been having trouble with my DVD drive which is amrked as /dev/cdrom0. If I want to watch DVD's using VLC, Gxine, totem etc will they search for /dev/DVD? 

How can I change the media drive so they can find it as dev/DVD.

Does it matter?

PS still can't watch DVD properly through Ubuntu despite numerous changes although I did get a scrambled picture and distorted sound last time

file:///home/kjb/Desktop/Screenshot.png

---

### Post by Vivaldi Gloria on 2008-07-25
> **Midgetprawn said:**
> OK I have been having trouble with my DVD drive which is amrked as /dev/cdrom0. If I want to watch DVD's using VLC, Gxine, totem etc will they search for /dev/DVD? 

How can I change the media drive so they can find it as dev/DVD.

Does it matter?

PS still can't watch DVD properly through Ubuntu despite numerous changes although I did get a scrambled picture and distorted sound last time

file:///home/kjb/Desktop/Screenshot.png


It doesn't matter if it is /dev/cdrom0 or something else unless you have more than one cd/dvd drive.

Do I understand you correctly: You can mount dvds (their icons appear on the desktop) but you can not play them, right?

If that is the case follow this to install dvd playback:

----------------------------------------------

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

----------------------------------------------

file:///home/kjb/Desktop/Screenshot.png

How on earth the knowledge that there's is a Screenshot.png in your desktop is going to help if you do not attach that image?

---

### Post by irish66 on 2008-11-27
I am having same problem, but entering
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
gets me @command not found" 
I'm using Linux Mint.
M

---


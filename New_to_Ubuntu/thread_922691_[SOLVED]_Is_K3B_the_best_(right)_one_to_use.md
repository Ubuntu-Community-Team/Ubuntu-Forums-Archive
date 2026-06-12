---
title: "[SOLVED] Is K3B the best (right) one to use??"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by sillyboy on 2008-09-17
I am trying to create an image from a dvd using K3B.  I downloaded gISOmount.  I get the error "No non-local files supported". I need step by step advice here.  I want to create an image and then burn it to cd/dvd.
I only have 1 cd/dvd rom in my machine.

Thanks:confused:

---

### Post by bobnutfield on 2008-09-17
I am not familiar with gISOmount, but K3B is the app I have used for years to burn ISO images.  The GUI is very intuitive, simply choose tools, burn ISO image to DVD.  You need then only direct the location of the image you want to burn, and K3b does the rest,

---

### Post by billgoldberg on 2008-09-17
So you have the dvd and need to make a iso file out of it?

You don't need k3b, try dvd::rip.

In a terminal ==>

```
sudo apt-get install dvdrip
```

--

Ignore that.

What are you trying to make a iso from?

After it's made, you can just use brasero. It's installed by default, is equally good as k3b but it integrated better into Gnome.

---

### Post by ww711 on 2008-09-17
k3b is fine to use for burning iso image files, or duplicating discs.

---

### Post by sillyboy on 2008-09-17
> **billgoldberg said:**
> So you have the dvd and need to make a iso file out of it?

You don't need k3b, try dvd::rip.

In a terminal ==>

```
sudo apt-get install dvdrip
```

--

Ignore that.

What are you trying to make a iso from?

After it's made, you can just use brasero. It's installed by default, is equally good as k3b but it integrated better into Gnome.

I downloaded DVDRip. I opened it... and couldn't figure it out.

I then opened Brasero, made an ISO image (did not see where to name it), named barsero.iso.  When I put in a blank DVD the NO MEDIA stayed on, as if there was no media in the drive.  I then put a CD in the drive and it was recognized.  Only problem is that there is not enough ROOM on the CD to copy the ISO.  I then tried a different brand of DVD and the drive still would not recognize that there was a DVD in the drive

HELP!!:confused:

---

### Post by VraiChevalier on 2008-09-17
Correct me if I am mistaken; K3b does not "create" an image does it? I am not sure what application you would use under Ubuntu to do that.

Also, do you have a DVD "ROM" or a DVD burner?

---

### Post by bobnutfield on 2008-09-17
I am confused.  Are you trying to create an ISO or do you HAVE an ISO that you want to burn to DVD.  If you are trying to create an ISO image, you can do that from the command line with the mkisofs command.  But if you already have an ISO file and you simply want to burn it to a DVD, then I would highly recommend K3b.  If you are running Ubuntu with Gnome you can still install K3b (which is actually a KDE app), but it will pull in some KDE files when you install it.  It will usually have no affect on your system to install K3b (I have it installed on my Gnome Desktop).

K3b is mature and stable and will handle just about any burning job.

---

### Post by sillyboy on 2008-09-17
> **VraiChevalier said:**
> Correct me if I am mistaken; K3b does not "create" an image does it? I am not sure what application you would use under Ubuntu to do that.

Also, do you have a DVD "ROM" or a DVD burner?

I created the image in Brasero.

I'm glad you asked that!  When I put my computer together, for this Linux/Ubuntu OS, I neglected to look at the DVD drive.  It is just a reader.:(  I'm going to buy a DVD writer ASAP. 

Many thanks

---

### Post by ulukapata on 2008-09-17
good info


[http://sikh.myminicity.com/tra/](http://sikh.myminicity.com/tra/)

---

### Post by sillyboy on 2008-09-17
> **bobnutfield said:**
> I am confused.  Are you trying to create an ISO or do you HAVE an ISO that you want to burn to DVD.  If you are trying to create an ISO image, you can do that from the command line with the mkisofs command.  But if you already have an ISO file and you simply want to burn it to a DVD, then I would highly recommend K3b.  If you are running Ubuntu with Gnome you can still install K3b (which is actually a KDE app), but it will pull in some KDE files when you install it.  It will usually have no affect on your system to install K3b (I have it installed on my Gnome Desktop).

K3b is mature and stable and will handle just about any burning job.

I would like to use K3B...but used Brasero to create the ISO.  I will definitely try K3B when I get over my senior moment!  Daahhh!

Many Thanks Bob

---


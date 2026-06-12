---
title: "Install Ubuntu from hard drive?"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by SkyShayde on 2012-06-16
First, I have a 2009 Mac Mini
I would like to install Ubuntu on it
I was wondering if it is possible to install it from the hard drive, or if I need to find my flash drive/buy a new one
I effectively want to use a hard drive partition as a usb drive.  

I have rEFIt installed already, and it works

ty in advance


Edit:

I have 2 500gb hard drives, i can't mess with the first at all, and i'd prefer if the second does not need to be erased, although I can if necessary

---

### Post by SkyShayde on 2012-06-16
Sorry for the double post, it wouldn't let me edit again

I found a flash drive, so I don't need this anymore

Edit:

It's not working, I md5'ed it

I'll post the error in a sec

I get the error

The disk could not be read.  

with the options "Initialize"  "Eject" & "Ignore"

Edit3:

Fixed it!  penguintosh.com worked well

---

### Post by black veils on 2012-06-16
do you know after you download the unbuntu installer you need to:

1.  backup all your data!

2.  check the md5sum

3.  use a special application like **Unetbootin**, to make the usb flash drive bootable [http://unetbootin.sourceforge.net/#other](http://unetbootin.sourceforge.net/#other)

4.  this is what the install process will look like, and this guide should help you with partitioning, as you should choose the** something else** option to avoid wiping any harddrives. [http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/](http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/)

the guide is for 11.10, but it will be the same for 12.04

---

### Post by SkyShayde on 2012-06-16
> **black veils said:**
> do you know after you download the unbuntu installer you need to:

1.  backup all your data!

2.  check the md5sum

3.  use a special application like **Unetbootin**, to make the usb flash drive bootable [http://unetbootin.sourceforge.net/#other](http://unetbootin.sourceforge.net/#other)

4.  this is what the install process will look like, and this guide should help you with partitioning, as you should choose the** something else** option to avoid wiping any harddrives. [http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/](http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/)

the guide is for 11.10, but it will be the same for 12.04

Thanks for the help, I got it working already though.  Unetbootin didn't boot with macs i though? and I partitioned everything already

---


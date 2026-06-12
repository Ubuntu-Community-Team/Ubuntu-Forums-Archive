---
title: "prob with qemu any help plz"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by articwolf939 on 2008-09-25
ok im following a tutorial and it says i should run the camand 

qemu-img create xp.img 8g

im tring to install Xp, but when i run the cammand i get this 

Windows$ qemu-img create xp.img 8g
qemu-img version 0.8.2, Copyright (c) 2004-2005 Fabrice Bellard
usage: qemu-img command [command options]
QEMU disk image utility

Command syntax:
  create [-e] [-b base_image] [-f fmt] filename [size]
  commit [-f fmt] filename
  convert [-c] [-e] [-f fmt] filename [-O output_fmt] output_filename
  info [-f fmt] filename

Command parameters:
  'filename' is a disk image filename
  'base_image' is the read-only disk image which is used as base for a copy on
    write image; the copy on write image only stores the modified data
  'fmt' is the disk image format. It is guessed automatically in most cases
  'size' is the disk image size in kilobytes. Optional suffixes 'M' (megabyte)
    and 'G' (gigabyte) are supported
  'output_filename' is the destination disk image filename
  'output_fmt' is the destination format
  '-c' indicates that target image must be compressed (qcow format only)
  '-e' indicates that the target image must be encrypted (qcow format only)

Supported format: vvfat vpc bochs dmg cloop vmdk qcow cow raw
kyle@kyle-desktop:~/Desktop/Windows$ 




any idea on how to create the IMg HDD???

---

### Post by articwolf939 on 2008-09-25
i know it alot of code but any one?

---

### Post by ronnielsen1 on 2008-10-02
I'm trying to figure it out myself now. I used qemu-launcher which gives a gui to qemu which seems to be a lot easier. I had win98 installed and it worked beautiful and fast (lots faster than virtualbox) but I shut it down and couldn't restart it. :(:confused: so I'm reinstalling and try to figure out where I went wrong.

You might try qemu-launcher and see if it works for you

---

### Post by satyam on 2008-12-27
You've to use the command "qemu-img" (with options) to create an image. It should be something like

qemu-img create -t raw foo.img 10G

which tells it to create a 10 gig image, named foo.img, with raw formatting. Or something like that. When you install your virtual OS, it will format the partition to suit.

If you just type 

qemu-img 

you'll see all the options. Cheers.

---


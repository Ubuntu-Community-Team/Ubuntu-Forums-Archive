---
title: "backup script does not work properly"
date: 2006-12-27
forum: Programming Talk
---

### Post by mozkaynak on 2006-12-27
Hi,
I created the following easy script:

> #! /bin/bash
echo backup is starting
cd /home/mozkaynak
tar cvpzf /media/usbdisk/homebackup.tgz ./ --exclude=./.gnome2/epiphany/* --exclude=./.mozilla/firefox/* --exclude=./realplayer10/*
tar cvpzf /media/usbdisk/etcbackup.tgz /etc

echo backup is done. Now testing
tar tzvf /media/usbdisk/homebackup.tgz
tar tzvf /media/usbdisk/etcbackup.tgz

sudo umount /media/usbdisk

it works fine except exclude part. this does not exclude anything.
does anybody know what might be the reason?
Any other improvement suggestions are welcome too.

Thanks in advance.

---

### Post by slavik on 2006-12-28
I think you have to do excludes before providing the directory to compress, as the object to work on is usually the last argument.

---


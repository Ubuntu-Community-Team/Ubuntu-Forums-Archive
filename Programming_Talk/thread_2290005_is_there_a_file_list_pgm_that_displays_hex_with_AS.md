---
title: "is there a file list pgm that displays hex with ASCII for ubuntu?"
date: 2015-08-08
forum: Programming Talk
---

### Post by sam_baker2 on 2015-08-08
Hi,  don't know if this is the right forum to ask this, but I will try here first.  I had an old Amiga computer one time, and it had a file display program that would list a column of hex code on the left side and on the  right side, there would be a listing of ASCII ( most of it was shown as ".......", but when ASCII code was found, the text would be shown ). So, you could see the hex, and find in that hex where ASCII text was.  Does anybody know if Linux has such a lister? or might one of the  programs in the LibreOffice suite do this?  Thanks for any info.

---

### Post by trent.josephsen on 2015-08-08
ASCII, you probably mean. (American Standard Code for Information Interchange)

Sounds like the program 'xxd'. Unfortunately I don't know what package it's in but it might be installed already.

---

### Post by sam_baker2 on 2015-08-08
opps, my bad. Thks trent.josephsen I was thinking of American Institute of Steel Construction.  I checked and I do have xxd and it displays similar to the old Amiga pgm I had, and that is what I am looking for. I would like to find something like xxd  that would display in a scrollable window.

---

### Post by oldfred on 2015-08-08
I have used hexdump which is part of package bsdmainutils.

       Example:  Suppose the BIOS Boot partition is /dev/sdc2.  Then:
sudo dd if=/dev/sdc2 count=62 | hexdump -C

Or to read a sector:

 read a sector:
sudo hdparm --read-sector  115330572 /dev/sda

I have not used this:
wxHexEditor is a hexadecimal file editor suitable
for editing very big files

If you go into synaptic and do a search on hex, you find many programs.
ghex, bless, hexcurse & others.

---

### Post by sam_baker2 on 2015-08-08
Thks oldfred.
ghex seems to be exactly what I am looking for.

---


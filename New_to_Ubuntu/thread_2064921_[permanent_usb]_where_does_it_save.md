---
title: "[permanent usb] where does it save?"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by blacksmith11 on 2012-09-30
Hi all.
I have made a permanent usb with ubuntu. It has a casper-rw and I was wandering where does ubuntu save my data, my programs, my preferences... I mean: does it saves them only in the casper or I can use all the space in the usb key? Moreover, how can I know how much empty memory still I have?
Thanks for help!

---

### Post by C.S.Cameron on 2012-09-30
It saves everything in the casper-rw file.
Max file size in FAT32 is 4GB.
You can also have a home-rw file of 4GB, Just rename a casper-rw file.
You can have casper-rw and home-rw partitions using ext2,3 or 4 filesystems.
I think system monitor should tell how much memory space you have.

---

### Post by Hadaka on 2012-09-30
Hi, to see how much memory you have on the usb stick
with the usb plugged in
click dash button
enter disc in the search field
click disc utility icon
click your usb

this will show any partitions, what type and allow you to name the usb
add additional partitions and a few other options.

---

### Post by HiImTye on 2012-10-01
you can use an ext2/3/4 partition instead of a file for 'casper-rw' if you want to use it transparently so you can access it outside your live session. to do this, you:

[LIST=1]
[*]delete the 'casper-rw' file (this will destroy any data inside of it)
[*]use GParted to resize the partition to the bare minimum (drag it all the way to the left, until it doesn't move anymore. if it gives you an error when you apply, repeat, but increase the size by 1)
[*]create a new partition in the empty space. make sure you give it a label of 'casper-rw'
[/LIST]
and there you are. the benefit of this is that you can also use a partition >4GB

---

### Post by blacksmith11 on 2012-10-01
Thanks everyone! Those are all very useful information!

---


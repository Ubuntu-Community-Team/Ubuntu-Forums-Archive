---
title: "Installing Ubuntu to a partition"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Jaded Misanthrope on 2008-05-26
How would I go about forcing Ubuntu to install to a partition that already exists? I read somewhere that Ubuntu uses the FAT32 file system, so I changed it to this in the installer and press forward, but it said that I 'did not specify a mount point' or something. As I said in another thread, I am *very* new to Ubuntu (and Linux in general, actaully), so this is probably a stupid question.

Would I have to delete the partition and remake it?

---

### Post by shifty_powers on 2008-05-26
ubuntu CAN use the fat32 file system, but by default it'll use something like ext2 or ext3.

when you install, you need to specify what the partition is going to be mounted as, i.e. used for.

so for example, you can specify two partitons, one with / or root mount point. this will contain all of your boot files, programs etc....

and the other can be /home which is where all your personal data, downloads, configs go.

so if something goes wrong you can reisntall ubuntu without losing your personal data ;)

you need to specify these mounts points when you partition the harddrive during installation.

check out the link in my sig for more details ;)

---

### Post by Jaded Misanthrope on 2008-05-26
Okay, thanks. I'll try that just as soon as I get these files shifted; that link looks great as well. :)

---

### Post by bumanie on 2008-05-26
Firstly, ubuntu much prefers to be put in a partition formatted to ext2 or preferably the newer ext3. It is true that it can operate from FAT32, but it won't perform near as well as it will in a native format such as ext3.
At the partitioning stage (sounds as though you are using the manual option) make 8-10g / partition - set size in the first window, set the filesystem format in the second window/box and set the partition label in the third window/box (you should find a / in there). It is also madatory to set up a swap partition, 1-2 g is enough. Set the size in the first box, filesytem format and parttion label as above (although use swap). Then it is a good idea to have a separate /home as large as you like for data. Set as above re size, filesystem format and either choose /home or type /home in the third box.

---

### Post by shifty_powers on 2008-05-26
psychocats rocks

read through it. it will answer a LOT of your questions before you've asked them ;)

---


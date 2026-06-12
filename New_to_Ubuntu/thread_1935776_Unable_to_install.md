---
title: "Unable to install?"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by BruceCM on 2012-03-05
Each time, the installer gets to after asking about the network, when I've chosen one, etc. Then, however, I just get the 'busy' cursor forever! Not sure what other information is likely to help, so thanks in advance & any ideas, please?:o

---

### Post by mapes12 on 2012-03-05
From memory you should be able to skip the network set up at installation and set it up later. The installer is probably trying to find something it can't and that's why it's hanging.

---

### Post by BruceCM on 2012-03-05
Yeah,thanks. Tried that but, sadly, it does exactly the same! Don't know why it didn't occur to me & thanks for the suggestion.:(

---

### Post by asifnaz on 2012-03-05
push escape button and paste here what text you see

---

### Post by BruceCM on 2012-03-05
None? Strangely, installer decided to get to about when I was typing in my name, etc. Then said it couldn't create the ext 4 filesystem! Um? Is that an improvement, though?:(

---

### Post by mastablasta on 2012-03-05
> **BruceCM said:**
> None? Strangely, installer decided to get to about when I was typing in my name, etc. Then said it couldn't create the ext 4 filesystem! Um? Is that an improvement, though?:(
 
yes, how are you installing it? Empty disk, reformatting? Within windows (Wubi)? whole disk, part of disk only?

---

### Post by BruceCM on 2012-03-05
Tried from the DVD I burned & the multiboot stick I created. Whole drive, for now. The only difference in the process I noticed, if it wasn't the whole drive, was it asked you what you wanted to do. Then took you through 'partitioning', etc. Hope that helps!:confused:

---

### Post by mastablasta on 2012-03-05
ok, strange. assuming oyur image is good....
 
try booting into live OS and use gparted to format the disk first to ext 4 and then try to install it.
 
is it possible the disk is faulty?

---

### Post by BruceCM on 2012-03-05
Which disk? The boot disk AND the stick? Trying that, I'll let you know!

---

### Post by gordintoronto on 2012-03-05
What version of Ubuntu?

When you are entering information, use a lot of lower-case and no upper case.

---

### Post by BruceCM on 2012-03-05
11.10, both 64 & 32 bit versions do the same. Whether it'd help to know that so do both versions of Kubuntu & both 64 bit Mints...?

---

### Post by BruceCM on 2012-03-06
Well, GParted couldn't do it, so what next, please? :mad:

---

### Post by BruceCM on 2012-03-07
Help! Now the boot stick won't work &, from the disc, it claims I don't have 5.8 GB of space on here. Where's the 750 HD gone!?:mad:

---

### Post by mastablasta on 2012-03-07
ok.
 
boot from the stick and select try it.
 
then you will get into the OS. ifnd gparted and run it (or open terminal and type in gparted or maybe you will need to type sudo gparted)
 
It should see the disk you are trying to install to. select it and reformat it.
 
if this can't be done then something is wrong with the disk.
 
also since i don't know how you are intsalling - make sure you are installing to the disk and not to your USB stick. here is how install should look like: 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
and for Kubuntu it's something like this: [https://help.ubuntu.com/community/GraphicalInstall/Kubuntu](https://help.ubuntu.com/community/GraphicalInstall/Kubuntu)

---

### Post by BruceCM on 2012-03-07
When the stick did work, it automatically started in Live Mode on here. I've installed Ubuntu a few times overall, on my last laptop & so on & it's always been a pretty simple process. The only thing now in GParted is 4.8 GB, which doesn't make any sense. Since the disc, which was a 4.7 GB RW one has the OS on it, so can't have 4.8 GB left.

---


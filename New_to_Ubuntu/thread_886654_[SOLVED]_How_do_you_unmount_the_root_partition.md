---
title: "[SOLVED] How do you unmount the root partition?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by theozzlives on 2008-08-11
I have Ubuntu 8.04 and want to setup a partition to move my Home directory to. I'm using gparted, but I tried to unmount at the prompt and it says it's in use. please help.....

---

### Post by halitech on 2008-08-11
you can't unmount a partition you are using. You will need to boot from either the Live CD or something like GParted to make the changes

---

### Post by theozzlives on 2008-08-11
> **halitech said:**
> you can't unmount a partition you are using. You will need to boot from either the Live CD or something like GParted to make the changes

gparted says to do it manually

---

### Post by bumanie on 2008-08-11
Suggest you download the [gparted live cd]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779&abmode=1") and try that. You won't have issues with mounted partitions.

---

### Post by snowpine on 2008-08-11
> **theozzlives said:**
> gparted says to do it manually

You need to run GParted from a Live CD.

---

### Post by Vivaldi Gloria on 2008-08-11
> **theozzlives said:**
> gparted says to do it manually

Either boot from the live cd and use the gparted in the live cd

or 

boot using the gparted live cd available here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by kansasnoob on 2008-08-11
> **theozzlives said:**
> gparted says to do it manually

Are you using Gparted from the live CD?

Using Gparted from the Ubuntu OS won't allow you to "unmount" the running partition ............. it would be like sawing off the branch of the tree you're sitting on.

---

### Post by halitech on 2008-08-11
manually from the Live cd version of gparted

---

### Post by kansasnoob on 2008-08-11
A common "stopper" for me has been that the swap partition is still locked (indicated by a keyring) so you may have to click on swap and select swapoff.

Then remember to "swapon" when you're done.

---

### Post by kansasnoob on 2008-08-11
Something that might be helpful, not now but, when you're all done:

[http://ubuntuforums.org/showthread.php?t=879192](http://ubuntuforums.org/showthread.php?t=879192)

---

### Post by theozzlives on 2008-08-11
> **Vivaldi Gloria said:**
> Either boot from the live cd and use the gparted in the live cd

or 

boot using the gparted live cd available here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Takes a long time but it worked! Thanks!!!

---

### Post by halitech on 2008-08-11
glad to hear you got it working :) please remember to mark the thread closed so others will know its solved.

---

### Post by andy_acacia on 2010-05-02
thanks kansas! swapoff did the trick for me.:)

---

### Post by Animal X on 2010-05-02
> **theozzlives said:**
> I have Ubuntu 8.04 and want to setup a partition to move my Home directory to. I'm using gparted, but I tried to unmount at the prompt and it says it's in use. please help.....



if ur moving your home directory, u will need more than Gparted, i recommend mepis for doing chop work like this. i assume copy/paste wont suit your needs then?

sorry, dint c u already got where u needed 2 b. peace

---


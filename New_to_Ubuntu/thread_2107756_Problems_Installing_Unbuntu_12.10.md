---
title: "Problems Installing Unbuntu 12.10"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by wreini on 2013-01-22
I have been trying to get 12.10 running so I can hopefully retrieve data from my WD Sharespace that crashed. I have the DVD downloaded and I get to the Installation type screen when it stalls. It sits on this screen and will not move. I have checked Erase Disk and also use LVM (my sharespace uses LVM for the raid drives). select Continue and it just runs the DVD drive. Lights up like it is trying to do something, but does nothing. Any Ideas? I am trying to install on an older Dell Precision machine.

---

### Post by grahammechanical on 2013-01-22
Please excuse my ignorance, but I see this,

> I am trying to install on an older Dell Precision machine.

and this

> I have checked Erase Disk and also use LVM (my sharespace uses LVM for the raid drives). 

Does this Dell Precision machine have an LVM on it? What are your plans for retrieving data from the WD Sharespace? Are you intending to connect it to the Dell after Ubuntu is installed on it? Or is the WD already connected?

Does the Live session run on this machine? I am not clear about the method you are going to use to get data from the WD Sharespace.

Regards.

---

### Post by wreini on 2013-01-22
I have a IDE 80Gb Harddrive that I am trying to reformat/erase (It has - or had windows XP) I was installing LVM because my SATA drives from the WD Sharespace have LVM.  Here is the link from someone that was able to retrieve their files.

[http://community.wdc.com/t5/WD-ShareSpace/HOWTO-Sharespace-RAID-5-Data-Recovery/td-p/287736](http://community.wdc.com/t5/WD-ShareSpace/HOWTO-Sharespace-RAID-5-Data-Recovery/td-p/287736)

I have not tried to see if Live session runs.

---

### Post by wreini on 2013-01-23
Yes I tried Live session now.  It does work if I do F6 and select nomodeset.  I had found out early that I needed to do the nomodeset to get as far as I did on the install.  I tried also the nodmraid last night and it got a little further.  Said it was installing and the went to the orange backspash screen.  But still stalls the install.

---


---
title: "Brasero - the medium is not writable with the current set of plugins"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by cwmoser on 2008-05-10
Brasero - the medium is not writable with the current set of plugins

This error occurs when I try to select my DVD RW drive.  Brasero works with my CD RW drive.  I was thinking that it once worked with both drives.

Any ideas?

Thanks
Carl

---

### Post by takuhii on 2008-05-12
The DVD Dual Layer but of Brasero is broken. This is being fixed for the next release, apparently, if you download and install the TRUNK version from Braseros SVN repo, the problem will be sorted...

Brasero Homepage: [here]("http://www.gnome.org/projects/brasero/")

---

### Post by shifty_powers on 2008-05-12
or try imgburn thorugh wine.

or install k3b, which imo is better than brasero anyways ;)

---

### Post by olskar on 2008-07-18
This problem is in latest brasero, 0.8

I am not even trying to burn a doblelayerdvd, just an ordinary

---

### Post by midtown on 2008-08-15
I ran into this today too, just trying to burn a CD-R. I sure do miss the old image burning app, it worked so well. I don't think I have had a single positive experience with Brasero where it didn't crash or fail to perform some basic operation. And this is across multiple machines and drives.

EDIT: Oh, you can still use the old method just fine by right-clicking on the ISO and selecting "Write to Disc...", cool!

---

### Post by cetheriel on 2008-08-16
can't burn with brasero either, multiple machines.
though i think it is ubuntu, really, not brasero.

---

### Post by ssameer on 2008-09-20
Downgrading to Brasero 0.7 works. According to the brasero website, that is the stable version.

---

### Post by inguanzo on 2008-10-24
K3B Rocks !!!  Thanks for the tip !

---

### Post by shifty_powers on 2008-10-24
heh np's. Kde ftw ^.^

---

### Post by johnnyrevell on 2008-11-25
yep - i had this problem too until I installed dvd+rw-tools with 

sudo apt-get install dvd+rw-tools

John

---

### Post by conorsulli on 2009-01-23
> **cetheriel said:**
> can't burn with brasero either, multiple machines.
though i think it is ubuntu, really, not brasero.
 Brasero is comletley bug ridden in intrepid, I aslo tried many basic burning tasks on various machines... safe to say this was broken on release...sad.

---

### Post by cetheriel on 2009-01-31
yes, i've upgraded and had no problem with brasero since.

---

### Post by WIGGMPk on 2009-06-04
This is still occuring for myself in Jaunty amd64.


Has anyone found a fix for this? I see a bug report @ [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/322769](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/322769)
but no solution and its marked unimportant.


:(:(:(:(:(

---

### Post by belim on 2009-07-24
I am having the same issue with Jaunty 64bit....

---

### Post by mikechant on 2009-07-24
> Has anyone found a fix for this?

Fix appears to be 'use a different program'!

Personally I use DeVeDe to create .iso files from videos of various formats, and Brasero just to burn the iso. This works fine for me, but you can use various programs such as k3b to burn the iso if Brasero won't even do a simple image burn.

Incidentally, I'd highly recommend DeVeDe for creating video DVDs. It's really easy to create simple menu structures, and it converts all sorts of video formats. 
The one thing to look out for is that it can massively overestimate the amount of space it will need once the video is reencoded - e.g. it tells me that 2x50 minute tv episodes in avi format, encoded at maximum quality, will take up about 4Gb, but actually produces an iso of less than 2.5Gb. I guess it's difficult to calculate and it just gives you the maximum possible.

---


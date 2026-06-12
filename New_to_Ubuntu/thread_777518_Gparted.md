---
title: "Gparted"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by gecko113 on 2008-05-01
One quick question..... Does gparted write over the exisiting hard drive or does it wipe it out completely cause i wanna wipe my hard drive clean nothing on it

---

### Post by aktiwers on 2008-05-01
> **gecko113 said:**
> One quick question..... Does gparted write over the exisiting hard drive or does it wipe it out completely cause i wanna wipe my hard drive clean nothing on it

I think if you delete the partition and create a new one and format, it will wipe completely.
If you choose format, it will format the filesystem.

---

### Post by Tatty on 2008-05-01
I dont think it erases every individual bit if thats what you mean.  I believe there are tools out there to do that, but I do not know what they are called.

---

### Post by sandysandy on 2008-05-01
look here

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

regards

---

### Post by Paqman on 2008-05-01
It can delete whole partitions totally, or you can wipe the data in a partition by reformatting it.

If you want to really, really clean all the data off a drive (for example, if you're selling it and don't want and personal info recovered) you can use [Scrub](http://www.ubuntugeek.com/securly-clear-free-hard-drive-space-with-disk-scrub-utility.html)

---

### Post by rbc on 2008-05-01
If you don't want to install any applications, I do this:
Pop in the LiveCD, go to terminal and type "dd if=/dev/zero of=/dev/whatever_your_drive_is". This will make one pass of your hard drive and write zeros to the whole thing. For more peace of mind, do it two or three times. Note, though, it can take some time depending on how big the hard drive is.

---

### Post by bobpur on 2008-05-01
I agree with rbc. His procedure is, essentially, the way I do it with one exception; I use the Gparted live CD or Parted Magic to do this with. I just have more confidence in a whole cd's worth of performance vs. a little programm tucked amongst other programs. No reason for that, just my preference.
Gparted live CD and Parted Magic are available in ISO form from [www.distrowatch.com](www.distrowatch.com).

Good Luck!

---

### Post by phr0ze on 2008-05-01
DBAN mentioned above is the best to use. It's made just to do one thing... wipe your drive.

---


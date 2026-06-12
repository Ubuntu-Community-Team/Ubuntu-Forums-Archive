---
title: "I screwed up partioning and need help"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by mason215 on 2008-10-27
Ok so i was partioning my HD, and i wasnt paying attention and accidently made my ubuntu partion only 4 gigs. When i realized this, i went into Gparted and this what happened...

[http://img219.imageshack.us/my.php?image=screenshotvi9.png]](http://img219.imageshack.us/my.php?image=screenshotvi9.png])[IMG]http://img219.imageshack.us/img219/7862/screenshotvi9.th.png[/IMG][/URL][[IMG]http://img219.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by mason215 on 2008-10-27
[http://img135.imageshack.us/my.php?image=screenshothb5.png](http://img135.imageshack.us/my.php?image=screenshothb5.png)

---

### Post by porchrat on 2008-10-27
How much RAM do you have?

How new is this install?  Can't you just do a fresh install?

---

### Post by mason215 on 2008-10-27
i have around 512 megabytes of ram, and this a new install. I just wondered if there is anyway to fix it

---

### Post by em4r1z on 2008-10-27
Execute Gparted using a LiveCD.
My system partitions are 5 GB in size and I've never found a problem. Of course, your needs may vary.

---

### Post by kwacka on 2008-10-27
Boot from a live CD, and use gparted (partition editor) to reduce the size of the first partition, merge all (or some) partitions, delete/create partitions.

---

### Post by porchrat on 2008-10-27
Why were you trying to swapoff the swap in that last image?

You can run that command from the console if you would like using something along the lines of:

```
sudo swapoff /dev/sda5
```

Then if you wanted to you could reallocate that but you kind of need that swap...especially with only 512MB of RAM.

My advice is to start over it is much easier and will save you stress.  You can always find out how to manipulate partitions later.

---


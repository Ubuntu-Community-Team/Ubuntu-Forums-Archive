---
title: "Compare md5sums?"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by patrickaupperle on 2008-04-23
Is there any way to, without downloading a program, to md5sum an image and compare it? For clarification I will include an example. I have an image and I put ```
md5sum .iso
``` and it spits out a hash. I then have to compare it myself. Is it possible to make the command line do the comparison?

---

### Post by bluefrog on 2008-04-23
assuming you have a text file containing the md5sums you can do

md5sum -c md5sums-file

it will check the sums with the .iso files in the same folder

You can take example on
[http://cdimage.ubuntu.com/daily/current/MD5SUMS](http://cdimage.ubuntu.com/daily/current/MD5SUMS)

James Dupin

---

### Post by patrickaupperle on 2008-04-23
Thank you, that is what I was looking for, but if I don't have a text file, could I use diff or something? It it impossible without a text file?

---

### Post by bluefrog on 2008-04-23
diff 1.iso 2.iso

in any case you need something to compare it to, either an iso or a checksum in a file

---

### Post by patrickaupperle on 2008-04-24
OK, so know cut and paste the md5sum into the terminal and having it compare them for me.

---


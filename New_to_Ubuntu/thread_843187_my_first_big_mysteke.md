---
title: "my first big mysteke"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by Alexbit on 2008-06-28
Good morning guys.
Last night in a moment of very high stupidity i've put my usb drive (full of data) in my pc and from the console i've done: sudo zcat boot.img.gz > /dev/sdb1.

Result:
I'm unable to see the original content of my key!
There's a way to get they back?

Please give me a chance!
Thank you

---

### Post by fahadsadah on 2008-06-28
Bloody hell!
People usually use cat (and zcat) on files, NOT raw block devices.

The contents of the disk are gone - sorry!

---

### Post by sdennie on 2008-06-28
As was already said, if you redirected something to a raw partition as sudo, you've destroyed the partition.  It looks like you were trying to install a custom kernel so, for future reference, I would try using a guide like this: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu).  It's much safer and integrates nicely with the system.

---

### Post by bumanie on 2008-06-28
You could try [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to retrieve the partition. It's probably your best hope. Could also try photorec from the same site.

---

### Post by geirha on 2008-06-28
[foremost](apt:foremost) might help you get back certain files. Read its  man-page for instructions.

---

### Post by NovaAesa on 2008-06-28
Or if worst comes to worse, you could always take it to a professional if the data was super super important.

---

### Post by Alexbit on 2008-06-30
Well...
cause i'm a very beginner here with *buntu i've recovered my file with a  windows utility.

For instance, this mega-mystake, was caused because i'm looking for a method to instal *ubuntu from a device different to cd...!

Now i've successfully installed Kubuntu from an image downloaded to a partition of my hdd.
I've used "UNetbootin" (here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/))
I've found this tool very usefull!

Thank you for support!
Ale

---


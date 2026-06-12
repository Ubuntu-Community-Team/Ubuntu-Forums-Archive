---
title: "Scan for Bad Sectors"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by technosysind on 2011-09-22
How do I scan for bad sectors on my Hard Drive? Is there any tool for that?

---

### Post by Lisiano on 2011-09-22
```
sudo badblocks -n /dev/sdx
```
Read the man page on other options to badblocks
```
man badblocks
```

---

### Post by technosysind on 2011-09-22
It says
> badblocks: No such file or directory while trying to determine device size

What could be the problem??

---

### Post by Nath4n on 2011-09-22
Menu>system>adminstration>Disk Utility

Use the smart data menu to do it

[IMG]http://i55.tinypic.com/fns7i8.png[/IMG]

[IMG]http://i54.tinypic.com/20a2syp.png[/IMG]
:)

---

### Post by technosysind on 2011-09-22
Yeah, that helps. In case I get any bad sectors, will I be able to mark them?

---

### Post by Nath4n on 2011-09-22
I'm not sure what you mean.

---

### Post by Nath4n on 2011-09-22
Try using Gparted, it's for formating and other utilities but it has options to check disk, it's a bit more advanced

```
 sudo apt-get install gparted 
```

Access it by typing gparted in a terminal or in the admin menu.

---

### Post by technosysind on 2011-09-22
I mean to say, that if I have bad sectors, is there a way to mark/ignore them so that the bad sectors are skipped.

---

### Post by Nath4n on 2011-09-22
I am pretty sure it automatically handles them for you.

In the pic of disk utility above I have 11 bad sectors so yes it does mark them and handle them.

---

### Post by technosysind on 2011-09-22
Ok, I've put my hard drive on self test. I hope I don't have any bad sectors. Will let u know if I need any further assistance. Thank u very much :)

---

### Post by Nath4n on 2011-09-22
Your welcome. :)

---


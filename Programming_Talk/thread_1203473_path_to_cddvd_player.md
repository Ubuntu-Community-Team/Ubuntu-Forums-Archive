---
title: "path to cd/dvd player"
date: 2009-07-03
forum: Programming Talk
---

### Post by swappo1 on 2009-07-03
Hello,

I am writing a program to list the contents of a cd/dvd.  I am not sure how to find the path to the player to access the contents of the disk.

---

### Post by jtdeloach10 on 2009-07-04
Wouldn't you just go like if it was php
[php]
$location = '/media/cdrom';
$open = opendir($location, r);
$read = readdir($open);
print $read;
[/php]
something like that, not sure what language you doing it in, but it would be similar. that would output everytinhg on the cd.

Isn't it always /media/cdrom? Or dvdrom perhaps?

---


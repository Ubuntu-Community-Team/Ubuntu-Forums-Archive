---
title: "I broke my xubuntu os"
date: 2020-06-07
forum: New to Ubuntu
---

### Post by thewhitekeygamer on 2020-06-07
Hello everyone. I accidentally broke my xubuntu os :oops: I ran the broken partion through a program called boot repair and I got an error message. The error message is on this website under sda6. [http://paste.ubuntu.com/p/kS2tM3wDkT/](http://paste.ubuntu.com/p/kS2tM3wDkT/). When I try to boot xubuntu, I only get a terminal like screen that says gnu grub version 2. if I can't repair the os, would It be possible to restore some files? thanks for reading.

---

### Post by Bashing-om on 2020-06-07
thewhitekeygamer; Hello -

Ouch !
as the log reports:
> 
sda6:
File system:       ext2


And I do not think the log reflects invalid info -
I do suggest that you re-install fresh ubuntu -  as the ext2 file system does not support many features (file journaling) that is in the current ext4 file system.

ext4 is the default file system - old now but so solid.

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by Autodave on 2020-06-08
You can try booting the PC with a USB or DVD with an installation .iso on it.  Then, you may be able to access the HD and copy some files from it.  Your chances are slim, but it is worth a try.

---

### Post by ActionParsnip on 2020-06-08
.

---


---
title: "I upgraded 12.04 to 14.04 buut its showing following message.Please help me solve it"
date: 2014-08-26
forum: New to Ubuntu
---

### Post by ranjan2 on 2014-08-26
Hello Friends,

I upgraded my Ubuntu 12.04 to 14.04. But, it is showing init not found message. What can I do to solve it. The picture is attached.

Thanks

---

### Post by overdrank on 2014-08-26
Hi and welcome, moved to New to Ubuntu. :)

---

### Post by ajgreeny on 2014-08-26
Only once have I had that boot message in the past.  I booted to a live system and ran ```
sudo e2fsck /dev/sda1
``` where sda1 was my installed Ubuntu root partition.

On rebooting to the installed version all was well. I have no idea what was the cause; I was just thankful that the filesystem check managed to put it right.  Worth a try, I think.

---

### Post by jdeca57 on 2014-08-26
This error message seems to indicate that there is a problem with the file system. Look at [http://ubuntuforums.org/showthread.php?p=12268329#post12268329](http://ubuntuforums.org/showthread.php?p=12268329#post12268329) they had the same problem and give a solution.

---

### Post by kansasnoob on 2014-08-26
Looks like it may be a Wubi install, is that right?

If so, **[COLOR="#FF0000"]and only if so[/COLOR]**, I think this should work:

[http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696](http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696)

If you're not absolutely sure then wait for someone more knowledgeable to have a look, or at least only try the temporary edit to to the grub boot line (changing ro to rw) rather than making any permanent change.

---


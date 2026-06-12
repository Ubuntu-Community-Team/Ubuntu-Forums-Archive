---
title: "How can one view the time and date on when a directory was created?"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by MemoryMarc on 2013-06-24
Hello, I'm running Ubuntu 12.04 and would like to know the date and time on when this folder "/tmp" (in File System) was created.  I tried right clicking the icon and viewing its Properties but it did not display a time stamp.  Any method would be great, thank you.

-M

---

### Post by oldos2er on 2013-06-24
You can easily do this in a terminal ```
ll /tmp
``` that is two letter "ells" together.

---

### Post by Rob Sayer on 2013-06-24
I suspect /tmp was created when you installed ubuntu.

---

### Post by MemoryMarc on 2013-06-24
Thanks for the reply.  However, that command only shows when the folder was last accessed, not created.

After more researching I found this helpful answer,

[http://askubuntu.com/questions/78196/is-it-possible-to-check-when-a-folder-or-a-file-is-created](http://askubuntu.com/questions/78196/is-it-possible-to-check-when-a-folder-or-a-file-is-created)

-M

---

### Post by Kujua on 2013-06-24
ll (ls -l) will not show the creation time.

If you are having an ext4 filesystem, you can try this:
```
debugfs -R "stat <path-to-file>" <device>
```

<device> should be /dev/sdaX. You can find X using 'mount' command.

You don't need to do all this if you just want to know when /tmp was created. Like the previous post says, /tmp was there since the beginning.

---

### Post by MemoryMarc on 2013-06-24
> **Kujua said:**
> ll (ls -l) will not show the creation time.

If you are having an ext4 filesystem, you can try this:
```
debugfs -R "stat <path-to-file>" <device>
```

<device> should be /dev/sdaX. You can find X using 'mount' command.

You don't need to do all this if you just want to know when /tmp was created. Like the previous post says, /tmp was there since the beginning.

Thanks Kujua. I used /tmp as an example as file names can be changed around.  What is an ext4 file system? How would I check for/install that feature?

-M

---

### Post by grcastleton on 2013-06-24
> Thanks Kujua. I used /tmp as an example as file names can be changed around. What is an ext4 file system? How would I check for/install that feature?


ext4 is a type of file system, it determines how files are stored on your hard drive.

Type 'mount' in a terminal and look at the first line. Should be something like:

```
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
```

the ext4 tells you what type of file system you have. Changing the type of filesystem is probably something you would want to do when you initially install the OS, not really something you can easily to later.

---

### Post by trevorhanning on 2013-06-24
run ls -l | grep FILENAME in a terminal

---

### Post by MemoryMarc on 2013-06-25
ok I used mount and i do have the ext4 file system I'll go ahead and try Kujua's and trevorhanning's methods

---


---
title: "get symlink destination"
date: 2007-03-29
forum: Programming Talk
---

### Post by Mateo on 2007-03-29
anyone have a good way (terminal of course), to get the destination of symlinks? thanks.

I'm trying to make a script to mv the destination files, but i've read that mv doesn't follow symlinks.  So I was going to write the destinations to a file and then mv that way.

---

### Post by yabbadabbadont on 2007-03-29
```
/home/daffy $ file /etc/localtime
/etc/localtime: symbolic link to `/usr/share/zoneinfo/US/Central'

```
It's ugly, but it should work.

---

### Post by Mateo on 2007-03-29
huh?

---

### Post by yabbadabbadont on 2007-03-29
Run file on the item of interest and parse the text it prints out.

---

### Post by Mateo on 2007-03-29
i have no clue what you are talking about.  I want a command that scans a symbolic links and gives the destination.  I have no clue what localtime or /usr/share/zoneinfo/US/Central has to do with that.

---

### Post by yabbadabbadont on 2007-03-29
Clearly, from the output I posted, /etc/localtime is a symbolic link that points to /usr/share/zoneinfo/US/Central.  If that wasn't obvious, perhaps you might want to tackle an easier problem.  ;)

---

### Post by Mateo on 2007-03-29
ohh I see now.  i'll try it.

---

### Post by Mateo on 2007-03-29
that won't work because it includes the words "symbolic link to..".  I need for it to be just the destination.  i wonder if there's another command that can achieve this.

---

### Post by hod139 on 2007-03-29
How about ```
 ls -l foo
```**Edit:** If you want just the destination you can use awk
```
 
ls -l foo | awk '{print $10}' 
```This is not a very robust solution.  Spaces in filenames will kill it for one, but maybe it's a good start.

---

### Post by yabbadabbadont on 2007-03-29
> **Mateo said:**
> that won't work because it includes the words "symbolic link to..".  I need for it to be just the destination.  i wonder if there's another command that can achieve this.

I told you that you would need to parse the output.  :D

Read up on the sed, awk, and cut utilities.  The proper combination of them, combined with the file command, should get you what you need.

---

### Post by Mateo on 2007-03-29
ok, I think that will do.  thanks a lot (to both of you).

---

### Post by Mr. C. on 2007-03-29
Don't forget to remove (and remake) the symlink.

```
test -L *filename*
test -h *filename*

```
will indicate if a file is a symlink.

MrC

---

### Post by gerald.schnabel on 2009-07-06
I know this thread is a little bit older, but I found them in google as I searched for a solution to get the destination for a symlink.

And I found the nice command ```
readlink something
``` that will return the destination and just the destination of a symlink.

---


---
title: "[SOLVED] quick question"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by sweeneytodd on 2008-06-01
whats the difference between ext2 and ext3, the root has to be on ext3 i think so what is the main purpose for ext2 or is it like a upgrade, as in fat16 and fat32

---

### Post by %hMa@?b&lt;C on 2008-06-01
ext3 is the same as ext2 but ext3 provides journaling
Journaling makes it so you don't have to fsck your filesystem after a crash

edit: due to the journaling, it does infact make the memory/cpu work a little higher and the write cycle is higher so it is not recommended on solid state drives

---

### Post by sayakb on 2008-06-01
Ext3 filesystem is nothing but next version of ext2 filesystem with journaling support. Ext3 has been structurally implemented same as ext2 so they have same data structures. The most important difference between Ext2 and Ext3 is that Ext3 supports journaling which allows fast recovery from disk problems. You also get reliability and a better performance with ext3. Ext3 is designed to take care of both metadata and data.

---

### Post by shifty_powers on 2008-06-01
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

will start you off ;)

---

### Post by Fedz on 2008-06-01
As good as an explanation as any: [Wikipedia > ext3](http://en.wikipedia.org/wiki/Ext3) and [ext2](http://en.wikipedia.org/wiki/Ext2) ;-)

---

### Post by sweeneytodd on 2008-06-01
whats fsck?

---

### Post by %hMa@?b&lt;C on 2008-06-01
> **sweeneytodd said:**
> whats fsck?

fsck is the command to run a filesystem check for consistancy
it is the equivalent to the program "CHKDSK" on windows

---

### Post by Seisen on 2008-06-01
[http://en.wikipedia.org/wiki/Fsck]("http://en.wikipedia.org/wiki/Fsck")

---


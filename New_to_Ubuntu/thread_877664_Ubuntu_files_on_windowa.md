---
title: "Ubuntu files on windowa"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by adobrakic on 2008-08-02
How can I get to my ubuntu files while I'm on Windows. For example watch a movie on windows that's been saved to ubuntu.
I know how to get windows files on ubuntu, but not the other way around.

---

### Post by collinp on 2008-08-02
Have a look at this: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by adobrakic on 2008-08-02
I installed it, but I have no idea how to use it. I made the ubuntu partition Z: but didn't make the swap anything. Is the program supposed to be in the start menu or something

--edit--

Nevermind, I found it under My Computer, but when I try to access it, it asks me to format.

---

### Post by perlluver on 2008-08-02
> **adobrakic said:**
> I installed it, but I have no idea how to use it. I made the ubuntu partition Z: but didn't make the swap anything. Is the program supposed to be in the start menu or something

Yes there, or you should just be able to double click on the drive.  If I remember correctly, you might have to restart Windows.

No don't format it.  Try a reboot first.

---

### Post by collinp on 2008-08-02
Your ubuntu partition should be under My Computer in Windows. If its not, then your Ubuntu partition is a ext3 partition and not a ext2 partition. Also, reboot windows if you havent already.

---

### Post by adobrakic on 2008-08-02
Yeah it's ext3

---

### Post by collinp on 2008-08-02
Hmm, have a look at [This]("http://www.diskinternals.com/linux-reader/") and [This]("http://www.howtoforge.com/access-linux-partitions-from-windows").

---

### Post by castor_troy on 2008-08-02
Have a look at [this]("http://fs-driver.org/index.html").
The linux drive will show up on your windows explorer and my computer.
You can use it as you use any other drive. You wont even realise it's a ext3 filesystem.

Dont be bothered that it says ext2. Both ext2 and ext3 are fundamentally the same.
The Ext3 file system is the Ext2 file system which has been extended by journaling. Ext3 is backward-compatible to Ext2 - an Ext3 volume can be mounted and used as an Ext2 volume.

I've been using it and it works just fine.

---


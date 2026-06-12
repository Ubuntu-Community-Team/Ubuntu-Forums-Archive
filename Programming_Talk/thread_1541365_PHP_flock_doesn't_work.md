---
title: "PHP flock doesn't work?"
date: 2010-07-29
forum: Programming Talk
---

### Post by NoBugs! on 2010-07-29
I tried the PHP [flock]("http://php.net/manual/en/function.flock.php") command on Ubuntu server, it is supposed to "lock" files, but it doesn't seem to work. After making an exclusive lock on a file for writing, I can still open, edit, save, and reopen the file in a text editor.

---

### Post by NoBugs! on 2010-08-02
Is this a bug in php?

---

### Post by Arndt on 2010-08-04
> **NoBugs! said:**
> Is this a bug in php?

From "man 2 flock":

      flock()  places  advisory  locks  only; given suitable permissions on a
       file, a process is free to ignore the use of flock() and perform I/O on
       the file.

---

### Post by soltanis on 2010-08-04
File locking only works if applications request a lock on the file after opening it (at which point if another process holds it, it will block). However, since as Arndt pointed out, the locks are advisory, there is no mechanism that prevents you from actually opening the file or writing modifications to it while a lock is being held by another process. Your text editor, then, is merely ignoring the lock, or a better way to put it is that it doesn't request a lock on the file in the first place, so it is ignorant of any locks being held.

---

### Post by Hellkeepa on 2010-08-07
HELLo!

Morale: Don't make your apps depend upon locks, but make it multi-user aware. Not only will this save both you and your users from headaches, but it would enable your app to play very nicely along the likes of Dropbox and other applications that might want to change/read the file as well. An added bonus, if there ever was. ;-)

Happy codin'!

---


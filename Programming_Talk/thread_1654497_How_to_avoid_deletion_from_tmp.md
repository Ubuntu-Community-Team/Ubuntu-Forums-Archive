---
title: "How to avoid deletion from /tmp"
date: 2010-12-28
forum: Programming Talk
---

### Post by hakermania on 2010-12-28
Hello :)
I want to place a file to /tmp
I 've noticed that /tmp folder is cleaned up once in a while and in every restart.
I want to avoid this. Is there anyway to tell system NOT to delete this specific file?

---

### Post by odyniec on 2010-12-28
The /var/tmp directory is intended for storing temporary files that should be preserved on reboot.

What is the purpose of that file that you want to preserve? There might be a more appropriate location for it in the filesystem hierarchy.

---

### Post by hakermania on 2010-12-28
It is something personal that must not go to the wrong hands :D

---

### Post by Vaphell on 2010-12-28
it doesn't make sense - assuming you will have the persistent file in /tmp, if the 3rd party gets first to it, you won't do anything either way to prevent the access.
Just bury it in some oddball part of file hierarchy where nobody looks, compress it with a password and change extension or put it on an encrypted partition.

---

### Post by karthick87 on 2010-12-28
The default setting that tells your system to clear /tmp at reboot is  held in the [COLOR=Red]/etc/default/rcS[/COLOR] file.The value we’ll look at is TMPTIME.The current value of [COLOR=Red]**TMPTIME=0**[/COLOR]  says delete files at reboot despite the age of the file.Changing this  value to a different (positive) number will change the number of days a  file can survive in [COLOR=Red]/tmp[/COLOR].
```
TMPTIME=7
```
This  setting would allow files to stay in /tmp until they are a week old,  and then delete them on the next reboot.  A negative number [COLOR=Red](TMPTIME=-1)[/COLOR] tells the system to never delete anything in [COLOR=Red]/tmp[/COLOR].

---

### Post by MadCow108 on 2010-12-28
> **hakermania said:**
> It is something personal that must not go to the wrong hands :D

the /tmp folder is usually readable (and writable) by all users so it is definitely the wrong place for private stuff.

Why not save it in the (encrypted) home folder? there at least only your user and root (when unencrypted) can see it.

for temporary(!) private data cache you can use unnamed tempfiles which are not visible in the filesystem to others.

---

### Post by hakermania on 2010-12-28
Thx for your suggestions, I'll use truecrypt (btw, it's not packaged?)

---

### Post by karthick87 on 2010-12-28
BTW answer for your question is in post #5,have you tried that??

---

### Post by hakermania on 2010-12-28
@karthick87
Yes, thank you

---

### Post by Tony Flury on 2010-12-29
I stil don't understand why you want to store anything in /tmp - and if you turn off automatic deletions, eventually /tmp will fill up, and your PC might stop working - i.e. the / partition full.

---

### Post by nvteighen on 2010-12-29
For whatever's sake, don't follow karthick87's advice.

There's a filesystem hierarchy for a good reason: keeping the OS clean. If you want to store application data, there are several places to do it, but not /tmp... and please, don't make your program modify the user's preferences on how often /tmp is cleaned. Imagine you install a program that does that without asking you, wouldn't you be mad if you figured out that /tmp is filling up and you don't know what's causing it?

To save application data, use something under the user's home directory or use /etc if system-wide. Encrypt it if you think it's necessary, but respect the filesystem's hierarchy, please.

More generally, don't ever modify system user preferences without asking the user for permission. IMO, responsible programming requires you to inform the user of what you're doing to what essentially is his or her computer.

(Personal anecdote. One of the reasons why I immediately uninstalled Google Chrome for GNU/Linux when it was released is because it fiddles with the APT sources file without telling you... If at least it had told me, I'd have given it a second thought and possibly kept it. Some months later, I ended up installing Chromium when it entered the Debian testing repos :).)

---

### Post by karthick87 on 2010-12-29
@nvteighen I dont recommend him to follow that..But for his question that was the answer..

---

### Post by Vox754 on 2010-12-29
> **karthick87 said:**
> @nvteighen I dont recommend him to follow that..But for his question that was the answer..

Lol!

This is exactly my complaint with some users.

They are trigger-happy. They will answer your question, no matter if that solution is sub-optimal or plain wrong.

Who cares! He got what he wanted right?

---

### Post by odyniec on 2010-12-29
> **Vox754 said:**
> This is exactly my complaint with some users.

They are trigger-happy. They will answer your question, no matter if that solution is sub-optimal or plain wrong.

Who cares! He got what he wanted right?

The "solution" appears to be copied word-by-word from ubuntu-tutorials.com ([http://ubuntu-tutorials.com/2008/01/19/changing-the-tmp-cleanup-frequency/](http://ubuntu-tutorials.com/2008/01/19/changing-the-tmp-cleanup-frequency/)), so he probably just googled it and pasted whatever seemed relevant. Oh well.

---


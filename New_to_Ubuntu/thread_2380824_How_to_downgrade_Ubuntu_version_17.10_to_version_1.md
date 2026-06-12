---
title: "How to downgrade Ubuntu version 17.10 to version 16.04"
date: 2017-12-20
forum: New to Ubuntu
---

### Post by himynameis2 on 2017-12-20
> **QIII said:**
>  Do you know how to preserve your important data and /home partition?  If not, just ask.

I'm trying to do the same that OP is [in this thread: [https://ubuntuforums.org/showthread.php?t=2368418]](https://ubuntuforums.org/showthread.php?t=2368418]) (except from 17.10 to 16.04.3 LTS) and don't know how to do this. Could you point me in the right direction?

---

### Post by oldos2er on 2017-12-22
Post moved to its own thread. Always start a new thread, rather than posting in an older "Solved" one, for greater visibility.

---

### Post by ian-weisser on 2017-12-22
All the instruction you need is in the old thread.
Did you read it?
What parts do you need help with?

---

### Post by DuckHook on 2017-12-22
Hello himynameis2.

Are you asking about QIII's instructions?> **QIII said:**
>  Do you know how to preserve your important data and /home partition?  If not, just ask.
The important data is all in /home. You may also want to print out the contents of:```
cat /etc/default/grub
```…and:```
cat /etc/fstab
```…but this is not critical because they get created during your install with different settings. It's just nice to have some old references in case you made any customizations. If you are just starting out and have no data you wish to preserve, then you can even skip backing up.

Simply back up the whole /home directory to external storage. There are all sorts of methods from using backup software like Deja Dup to rsync (look at the link in my sig) to simply dragging and dropping the files you want using Nautilus. The important thing is to test your backup to make sure it is restorable.

Once all data is safe, simply run the install routine from a LiveUSB and follow instructions.

NOTE

You are not "downgrading". Such an exercise is next to impossible. You are wiping out your old Artful install and replacing it with a pristine Xenial install. That's why you must have all of your important data backed up to external storage. It gets deleted during the install process.

---


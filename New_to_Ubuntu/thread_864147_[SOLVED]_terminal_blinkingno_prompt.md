---
title: "[SOLVED] terminal blinking/no prompt"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-19
so I'm following the tutorial here:

   [http://ubuntuforums.org/showthread.php?t=688872&page=12](http://ubuntuforums.org/showthread.php?t=688872&page=12)

and I got to here:

... up testdisk (6.8-1) ...
Setting up xfsprogs (2.9.4-2) ...

Setting up wipe (0.21-3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
root@CRONUS:/# depmod -a $(uname -r)
root@CRONUS:/# update-initramfs -u -k $(uname -r
> update-initramfs -u -k $(uname -r)

at which oint my cursor is just blinking after forgetting to add a parenthases.  I tried it over as you can see but nothing happened.
how can I proceed?

---

### Post by JagDragon on 2008-07-19
This often happens with accidental typo's. A simple fix: Ctrl+C (As if you were copying something). Ctrl+C Terminates any script or program running within the terminal, so you can apply it to a wide range of malfunctions. ;)

---

### Post by linfidel on 2008-07-19
> **JagDragon said:**
> This often happens with accidental typo's. A simple fix: Ctrl+C (As if you were copying something). Ctrl+C Terminates any script or program running within the terminal, so you can apply it to a wide range of malfunctions. ;)
This is a feature, for splitting a command into more than one line - it's waiting for you to complete the command.  If all it needs is the parenthesis, simply enter it, and press Return.  It does the same thing with quotes.

For example, you can type:  ls "*
and it will respond with a right angle bracket.
Then, type the ending quote, and it will proceed.

---


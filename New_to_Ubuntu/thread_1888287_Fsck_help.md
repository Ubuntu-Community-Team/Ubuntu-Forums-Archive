---
title: "Fsck help"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by projecthikari on 2011-11-29
Ok, so one of my laptops requested that a manual fsck be preformed, and after a little fumbling, I found something that would help me.
So, I type the command: sudo fsck /dev/sda1
And it then says:
"/dev/sda1 contains a file system with errors, check forced.
pass 1: checking Inodes, blocks, and sized
Error reading block 312 (Attempt to read block from filesystem resulted in short read). Ignore error<y>?"

At this point, I selected Yes.

And then it asks:
"Force rewrite<y>?"

What I want to know is will this rewrite/wipe the system? I kind of need the files on this laptop.

Thanks!

---

### Post by projecthikari on 2011-11-29
Bump. :(

---

### Post by Lars Noodén on 2011-11-29
It's not a good idea to fsck a live system so be sure that you are doing all this from the installation CD's rescue mode.

---

### Post by mcduck on 2011-11-29
If the files are of any importance, you surely have backups?

And in case you don't, now it's the time you definitely should make one.

Yes, whatever fsck does might result in some missing files, but in that case the files are already broken (which is why fsck is trying to repair the dilesystem in the first place). (The rewrite it's asking about doesn't mean rewrititng the entire file system, it means rewriting whatever information it found to be broken.)

edit: also +1 to above about either running fsck from a live system, or scehduling it to be run at boot time.You shouldn't try checking a mounted file system, especially if it's your root partition.

---


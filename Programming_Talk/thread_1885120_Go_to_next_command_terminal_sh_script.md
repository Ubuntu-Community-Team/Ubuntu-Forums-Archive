---
title: "Go to next command terminal sh script"
date: 2011-11-22
forum: Programming Talk
---

### Post by ryanrio95 on 2011-11-22
I have an script to build Riome in this case.
When the script is:

unsquashfs filesystem.squashfs
chroot rootdir

Then it does unsquashfs but after that the script stops.
Is there some symbol or some text that i can add to the lines that stops the script to let it continue and follow to the next line?

Greets, ryan.

---

### Post by ryanrio95 on 2011-12-01
no one knows i saw &'s and /'s at the end of lines in scripts??

---

### Post by Arndt on 2011-12-01
> **ryanrio95 said:**
> no one knows i saw &'s and /'s at the end of lines in scripts??

I don't understand what you are saying here, but in order to use 'chroot', you need to have root privileges. For some reason, the manual page for the program doesn't mention this, but the page for the system call (man 2 chroot) does.

---

### Post by ehmicky on 2011-12-01
Hi,
You might use the wrong words : I guess when you say "stops" (that we understand as "the script quits/exits"), you want to say "wait", that is the next command is not processed until the former has finished. If so, you might want to add an ampersand & at the end of your line to make it a background job.

---

### Post by ryanrio95 on 2011-12-20
how to use this command?
and secondly
after:
sudo chroot squashfs-root

in my sh script are a lot of other lines.
but after this command the script just stops and doesn't launch the command following :(
can someone help me out?

greats, ryan.

---


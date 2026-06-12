---
title: "boot problem"
date: 2014-10-25
forum: New to Ubuntu
---

### Post by nemanja4 on 2014-10-25
Hello everybody!

I got my new computer with ubuntu which I liked, and wanted to learn more about it. I also wanted a windows on my computer as well so I created separate partition, and set up dual boot option. During this I moved my partition with ubuntu in orded to merge two unlocated partitions.
After this I am having problems with booting my linux. I tried tutorial on gparted regarding this, but I failed. After that I started boot-repair. and here is my log [http://paste.ubuntu.com/8675582/](http://paste.ubuntu.com/8675582/) When I try to boot linux Grub2 goes to safe mode and I don't know how to go further.

Anyone has an idea, how to restore my ubuntu?

Thanks!

N.

---

### Post by nerdtron on 2014-10-25
HHHmm so Ubuntu come pre installed? Better have windows installed first, then use "Install alongside windows" on the Ubuntu installation screen.

If this is a new computer and has no data yet, it could save you the hassle of repair so just reinstall everything, windows first.

---

### Post by oldfred on 2014-10-25
I do not see anything wrong.

It does look like you updated Ubuntu to 14.04.1, but may have installed grub to the partition boot sector of sda2. That would never work, but Boot-Repair says it reinstalled grub to MBR, so then it should boot.

What exactly is boot error?
Do you get grub menu? 
Can you boot recovery mode?

---

### Post by ajgreeny on 2014-10-25
How did you move the ubuntu partition?  You should always use Linux applications to work on Linux partitions as some windows applications will make the partition into a dynamic partition which will never work with Linux.

I see no evidence of this but I'm asking the question just to make sure.

---


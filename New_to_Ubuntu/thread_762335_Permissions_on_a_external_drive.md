---
title: "Permissions on a external drive"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by ortizn on 2008-04-22
I have a western digital my book external hard drive is formatted in vfat.  I recently cold booted my computer while the drive was mounted.  I am able to mount the drive again, but with some significant problems i can only mount the drive as root in a partition editor program.  Additionally when the drive is mounted I only have read access. 

This is the error when the drive is plugged in:

Cannot Mount Volume
Invalid mount option when attempting to mount the volume 'My Book'.

Ive tried to fix the problem in the terminal using sudo chown or chmod but it doesnt seem to work.  The drive is owned by root.

If you could please help me restore the appropreate permissions and mounting I would very much appreciate it.

Thanks,

Nick

---

### Post by Thanoulis on 2008-04-22
First of all, try to run a file system check while unmounted...
```
sudo fsck.vfat <device name>
```
Second, try to alter the mountpoint's directory privileges.
Third, good luck :)

---

### Post by blankphoto on 2008-04-23
Im having some what the same problem. I have a total of 5 HDs im my rig, and can not seem to get permission to access them unless they are formated in a non linux FS. I have tried both EXT3 and EXT2, I am new to Linux so am I missing something?

Why does Root Own these drives?
Is there a FS other than the 2 mentions that I should be using?
How do I aquire control over them?
Can it be down in the GUI? (hate terminals.command lines)

Thanks in advance.
Brian

---


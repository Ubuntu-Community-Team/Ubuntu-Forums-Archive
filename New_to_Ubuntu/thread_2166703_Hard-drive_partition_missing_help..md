---
title: "Hard-drive partition missing help."
date: 2013-08-10
forum: New to Ubuntu
---

### Post by Gemma_McCombe on 2013-08-10
Hi,  I have a HP N40l microserver. I just unplugged my hard-drive whilst switched off. I put it back in again but no it's only see the OS partition and not the rest of the drive.  What should I do to fix this?

---

### Post by Bashing-om on 2013-08-10
Gemma_McCombe; Hi ! Welcome to the forum.

Well, as it does boot and you do have an operating system .. can not be much messed up.
Show us what your disks look like; Terminal codes: -keycombo ctl+alt+t yields a terminal-
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```
And what you are trying to mount:
```

cat /etc/fstab

```
and what is mounted:
```

mount

```
*place the outputs between code (#) tags from the options at the top of the thread*

[INDENT][INDENT]a tale in the telling[/INDENT][/INDENT]

---

### Post by Gemma_McCombe on 2013-08-10
Decided to start from sratch again as I'm quite new to this I hadn't put much on there. I had gnome installed before, however when using it I didn't have full permissions is there a way around this?

---

### Post by Bashing-om on 2013-08-10
Gemma_McCombe;
Nothing at all wrong with (re-)installing .. so long as you learn from the experience...
as to "full permissions" .. there is none 'till you tell the system you want full access. This is accomplished by preceding a system directive with the term "sudo" - Super User DO- or the graphical equivalent "gksudo". 

For now this will serve your needs to gain "full permission" ...
For full disclosure ... in terminal:
```

man sudo

```

As a general rule, (re-)installing is a means that works in all situations, but, is a means of last resort.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---


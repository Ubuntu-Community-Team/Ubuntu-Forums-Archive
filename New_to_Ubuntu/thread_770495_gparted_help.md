---
title: "gparted help"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by nhovan on 2008-04-27
im trying to repartition my machine. i have 2 main partitions. one had vista on it the other ubuntu. i want to destroy the vista partition and resize the ubuntu one so that it takes over that space.
i can unmount the vista one and format it to my ubuntu partition but i cant figure out how to resize the ubuntu partition for the unallocated space. any help?

---

### Post by artir on 2008-04-27
You cant resize the partition you are working on. I recommend you to boot from the LiveCD and make tha changes from there. ATTENTION: You will need to reconfigure GRUB to eliminate windows from it. 

My recomendarion: clean install choosing "guided and erase disk"

---

### Post by southernman on 2008-04-27
Much easier to just edit your /boot/grub/menu.lst file at the same time you boot from the livecd to resize your ubuntu partition.

Your choice though. Just say the word!

---

### Post by southernman on 2008-04-27
Here are the edits you need to make. First do

```
gksudo gedit /boot/grub/menu.lst
```

Look for this section (toward the top of the file) and edit what you see in bold text:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default **0**
```

Now go to the bottom of this file and remove everything from below the following text:

```

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Do this either before or after you've resized the partition, not during. ;)

---


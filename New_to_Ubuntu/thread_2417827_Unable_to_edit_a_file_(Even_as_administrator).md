---
title: "Unable to edit a file (Even as administrator)"
date: 2019-04-27
forum: New to Ubuntu
---

### Post by yoshiki2 on 2019-04-27
I am supposed to edit file "/sys/class/dmi/id/modalias" and  then play with the configurations to adjust my touchpad. However. I am  unable to edit the file modalias.
 I even used administrator rights on  Nautilus to adjust it, however it still didn't let me edit the file.
Any ideas?

---

### Post by yetimon_64 on 2019-04-27
> **yoshiki2 said:**
> I am supposed to edit file "/sys/class/dmi/id/modalias" and  then play with the configurations to adjust my touchpad. However. I am  unable to edit the file modalias.
 I even used administrator rights on  Nautilus to adjust it, however it still didn't let me edit the file.
Any ideas?

[s]That file is read only even for root...
```
ls -la /sys/class/dmi/id/modalias
-r--r--r-- 1 root root 4096 Apr 28 08:02 /sys/class/dmi/id/modalias
```

Being a "read only for root file" I would  suggest you make a backup of the file before attempting any changes  with...
```
sudo cp /sys/class/dmi/id/modalias /sys/class/dmi/id/modalias.BAK
```
This gives you an original copy which, if you mess up the file, will  allow you to easily revert to the original state with the command ...
```
sudo cp /sys/class/dmi/id/modalias.BAK /sys/class/dmi/id/modalias
```

If you must manually edit it you first have to change the permissions for root to be able to edit it eg.
```
sudo chmod 644 /sys/class/dmi/id/modalias
```

Then try what you first did and edit the file as "administrator".

Once you make your edits and save the file, return the file back to read only for root with ...
```
sudo chmod 444 /sys/class/dmi/id/modalias
```

Though I must admit I don't know how wise it is to alter such a locked down file. I have explained how to do what you want but am not so sure if it is OK to do so, that is for you to decide. Usually "read only for root" files are set to such a strong setting for very good reasons, be careful editing such files.[/s]

Edit: See posts 5 & 6 below for why these instructions are struck out. Yeti.

Regards, yeti.

---

### Post by yoshiki2 on 2019-04-27
Thanks,
I am trying to edit the libinput settings to fix my touchpad according to bugs.freedesktop. Could you scroll down to comment 17 and tell me if I  am understanding their instructions correctly?
[https://bugs.freedesktop.org/show_bug.cgi?id=104990#](https://bugs.freedesktop.org/show_bug.cgi?id=104990#)
Thanks

---

### Post by yetimon_64 on 2019-04-27
> **yoshiki2 said:**
> Thanks,
I am trying to edit the libinput settings to fix my touchpad according to bugs.freedesktop. Could you scroll down to comment 17 and tell me if I  am understanding their instructions correctly?
[https://bugs.freedesktop.org/show_bug.cgi?id=104990#](https://bugs.freedesktop.org/show_bug.cgi?id=104990#)
Thanks

[s]If you are following that advice it sounds as though you may need to edit that file.

Definitely **make a backup first** in the terminal as I describe above BEFORE you open the file for editing. Being a hardware related file you may lose some touchpad functionality IF you make any mistakes. Be prepared for such by making a backup copy of the system file first.

Once you finish editing return the permissions on that file back to read only for root (octal permissions: 444) also as I note above.[/s]

Edit: see posts 5 and 6 for why this is struck out.

Good luck, yeti.

---

### Post by CatKiller on 2019-04-28
That is [not a file](https://www.thegeekdiary.com/understanding-the-sysfs-file-system-in-linux/). You can read from it and send text to it, but you can't open it in a text editor.

---

### Post by yetimon_64 on 2019-04-28
> **CatKiller said:**
> That is [not a file]("https://www.thegeekdiary.com/understanding-the-sysfs-file-system-in-linux/"). You can read from it and send text to it, but you can't open it in a text editor.

After some further checking OP this appears to be right. Even with the permissions change above I suggested the file still cannot be written to.

Ignore my previous instructions OP as you can't even back up the file as I first thought possible.  I could open it in a root text editor but could not write to it even with read/write permissions set. My previous post is NOT workable. I don't think the bug report you were following will work now by the looks of this.

Thanks for that info CatKiller. Cheers, yeti.

---


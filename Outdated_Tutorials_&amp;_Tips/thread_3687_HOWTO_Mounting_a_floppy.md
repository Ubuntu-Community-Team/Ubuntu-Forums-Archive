---
title: "HOWTO: Mounting a floppy"
date: 2004-11-08
forum: Outdated Tutorials &amp; Tips
---

### Post by wallijonn on 2004-11-08
If you want to use the floppy with Windows:

start a root terminal ([COLOR=Blue]Applications -> System Tools -> Root Terminal[/COLOR])

```

sudo gedit /etc/fstab

```
Change the floppy line to read:
```

/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0

```
{exit, save}
```

sudo gedit /etc/modules

```
add [COLOR=Green]floppy[/COLOR] to the end of the list. (unless "floppy" is already there).
{exit,save}

<reboot>

Right click top task bar.
[COLOR=RED]Add to Panel[/COLOR]
Highlight [COLOR=RED]Disks -> Add.[/COLOR]

Insert a floppy.
Click the Disk icon on the panel bar.
Double click the floppy icon.
You should be able to see if anything is written on the floppy.
Drag a file into that open floppy window. That should write it.
Right Click the desktop floppy icon -> [COLOR=BLUE]Unmount Volume[/COLOR].

To format:
Right click a mounted floppy, [COLOR=GREEN]Unmount Volume[/COLOR]. Otherwise:
[COLOR=BLUE]Applications -> System Tools -> Floppy Formatter.[/COLOR]
You will only be able to format in DOS mode

If you [COLOR=BLUE]Add to Panel -> Disk Mounter -> Preferences -> Mount in Directory: /media/floppy0[/COLOR], 

Clicking once the floppy mounter taskbar icon should mount & open the floppy. 

-----------------------------------------------------------------------------------------------------------------------------------

If you wish to use the floppy just for Linux, then

start a root terminal
```

sudo gedit /etc/fstab

```
Change the floppy line to read:
```

/dev/fd0        /media/floppy0  ext2    rw,user,noauto  0       0

```


.

---

### Post by wallijonn on 2005-02-22
/dev/fd0        /media/floppy0  vfat,ext2    rw,user,noauto  0       0

---

### Post by lionroar on 2007-06-08
Hi I am kind of confuse about this procedure. I do the first step you say and then go to the "Floppy"  or the fs tab and enter the following code: 

/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0

Then save and exit and then go back to the terminal and type:

sudo gedit /etc/modules


Now add "floppy" at the end of the list if is not mentioned there and then save and exit.

Do you reboot from the terminal or do it from the desktop. Or does it even matter.

---

### Post by pneaveill on 2007-09-26
> **lionroar said:**
> Hi I am kind of confuse about this procedure. I do the first step you say and then go to the "Floppy"  or the fs tab and enter the following code: 

/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0

Then save and exit and then go back to the terminal and type:

sudo gedit /etc/modules


Now add "floppy" at the end of the list if is not mentioned there and then save and exit.

Do you reboot from the terminal or do it from the desktop. Or does it even matter.

Although someone with a little more experience than I have may clarify a bit, I am not aware that it should matter how it reboots

---


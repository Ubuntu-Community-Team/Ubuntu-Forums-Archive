---
title: "Not really a beginners question but.."
date: 2008-04-26
forum: New to Ubuntu
---

### Post by kg87 on 2008-04-26
Ok my problem is relatively simple,

When i start ubuntu hardy, there's a few things i want on startup that im currently having to do manually.

1. Mount a windows xp partition with

sudo mount /dev/sda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222

2. Open gdesklets automatically (loving the oversized clock)

3. Reset compiz with 

compiz --replace. 

is there any way to automate this process?

Thanks in advanced guys

KG87

---

### Post by scragar on 2008-04-26
go System>Prefernces>Sessions easy enough, just add them to the list.

the first one however can easily be done by editing fstab:
```
gksudo gedit /etc/fstab
```
```

/dev/sda2	/media/windows     ntfs    defaults        0       2

```

---

### Post by hackle577 on 2008-04-26
Put them into a shell script and set it to run on startup. You may have to put a small delay on the Compiz command though. Might look something like:

```
#!/bin/sh

gdesklets

sleep 10
compiz --replace
```

These commands might no be exact, so someone with a bit more experience will have to fill in the details.

EDIT: I guess scragar's way would be easier lol

---

### Post by Hellishcross on 2008-04-26
Under Applications > Add/Remove... there is a tool to read and write NTFS formats that you can download and then use to read an NTFS partition using a point and click method. Once you download it, it would be under Applications > System Tools. It's called NTFS configuration tool.

---

### Post by kg87 on 2008-04-26
another question then, Thanks to both of you for a quick response, but

scragar, I had something similar already (after reading many tutorials), yours looked a little more streamline :D

hackle577, would i do that in terminal?

---

### Post by tamoneya on 2008-04-26
you should put hackie577's script into a file and then auto start the script.  To do this go System -> Preferences -> Sessions

---

### Post by kg87 on 2008-04-26
Thanks everyone!, Just one more question, 

How do i make a shortcut to the "windows" folder, as make link is grayed out on the menu :S

---

### Post by scragar on 2008-04-26
just create a launcher and direct to launch:
```
nautilus /media/windows
```

---

### Post by SunnyRabbiera on 2008-04-26
you might also be able to make one using the configuration editor, its hidden so you have to unhide it.
very simple:
just right click on your menu and select "edit menu's"
from there go down to "system tools" and put a little checkbox next to the "configuration editor"
It should have an option to show other drives like windows shares in apps, by going down to "nautilus" and clicking the little arrow and select "desktop"
if there are drives to be shown it might list them here.

---


---
title: "Any recommendations for GUI for simple listing of folder sizes"
date: 2020-06-28
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2020-06-28
Windows allow user to hover over folder name and see it's size. Does Ubuntu have a GUI which provides quick way to determine folder sizes?

---

### Post by Holger_Gehrke on 2020-06-28
Doesn't the file manager show the sum of the sizes of the files in a directory when right clicking on a folder and selecting properties ? 

Beyond that there's baobab aka Disk Usage Analyzer, which is meant for finding out what exactly is using all that space ...

Holger

---

### Post by daniewicz on 2020-06-28
> [COLOR=#000000]Doesn't the file manager show the sum of the sizes of the files in a directory when right clicking on a folder and selecting properties ?[/COLOR]

Yes it does in Ubuntu 20.04.

---

### Post by ActionParsnip on 2020-06-29
CLI is a bit easier:
```

du -ash /path/to/folder

```

---

### Post by SeijiSensei on 2020-06-29
> **daniewicz said:**
> Yes it does in Ubuntu 20.04.

Same is true for Dolphin, the file manager that comes with KDE/Kubuntu. Right-click > Properties.

---

### Post by ajgreeny on 2020-06-29
And it's the same in Xubuntu using thunar, but like ActionParsnip I think it's  even quicker and more useful to use a du command with some different options to those he shows which just throw an error message for me.

The command I have set as an alias is ***du -h -d 1 | sort -h***which lists all folders and sorts them by size of their content.
```
4.0K	./abcde
4.0K	./Desktop
4.0K	./.mkusb
4.0K	./MY_PVR
4.0K	./System Volume Information
4.0K	./.xournal
8.0K	./.ssh
12K	./.dbus
28K	./.gnupg
32K	./.gconf
44K	./.dvdcss
68K	./.audacity-data
76K	./.pki
100K	./.hugindata
156K	./Playlists
248K	./Icons
400K	./.thumbnails
412K	./.java
544K	./.openshot_qt
880K	./Abiword_docs
1.1M	./Misc
1.2M	./Phone
1.3M	./.foobillardplus
1.6M	./.zoom
2.5M	./Calibre Library
5.8M	./Power_Supplier
7.9M	./Attachments
9.6M	./.get_iplayer
9.8M	./Quicknotes
42M	./dwhelper
42M	./.local
81M	./Bank
153M	./.googleearth
274M	./Dropbox
335M	./snap
391M	./.mozilla
424M	./PDF
481M	./mp3edit
547M	./Pics
665M	./.config
1.6G	./.cache
1.9G	./Backup
3.0G	./.thunderbird
4.9G	./Documents
8.1G	./VirtualBox VMs
13G	./Music2
14G	./Music
19G	./Audio_recording
22G	./Downloads
44G	./Pictures
68G	./Videos
201G	.

``` 
Does it really need to be a GUI?

---

### Post by ActionParsnip on 2020-06-30
I'd use:
```

du -a $HOME | sort -n -r | head -n 10

```

If you want the 10 largest. If you notice from ajgreeny's output they aren't in size order :)

---


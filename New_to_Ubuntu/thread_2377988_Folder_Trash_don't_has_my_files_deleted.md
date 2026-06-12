---
title: "Folder Trash don't has my files deleted"
date: 2017-11-18
forum: New to Ubuntu
---

### Post by sed_faster on 2017-11-18
Hello folks,

When I execute delete over a file or folder supposedly this archiver should be send to folder trash. Instead this files never been sent to this folder. I searched on this locate:
```

:~/.local/share/Trash$ tree
.
&#9500;&#9472;&#9472; expunged
&#9500;&#9472;&#9472; files
&#9492;&#9472;&#9472; info

3 directories, 0 files

```
and I not found anything.
Or my files it is sent directly to space :P or files are being send to another folder on my system. Where should I look?

Thanks

---

### Post by Autodave on 2017-11-18
The DELETE command does exactly that: it deletes them.  Use the Move To Trash command to put them in the trash can to delete or recover later.

---

### Post by Holger_Gehrke on 2017-11-18
Well, Autodave has me beat in terms of reading comprehesion. I assumed you had moved to trash and couldn't find it, and wrote this:

[I]This depends on a lot of things. First, what program did you use to delete the file, as what user did you do it and on what device where the files. If you used the normal file manager (Nautilus, Thunar, pcmanfm on Ubuntu,XUbuntu, Lubuntu) and where logged in as the user in whose ~/.local/share/Trash you looked and they where somewhere on the same device and partition as this Trash directory, the deleted files should indeed be in Trash/files and there should be some Data needed for putting the files back in Trash/expunged and Trash/info.If the files where somewhere else, let's say on an USB-drive, then there should now be a Directory .Trash-"uid" on the device with the same structure as ~/local/share/Trash inside ... If you were logged in as a different user at the time, look in the .local/share/Trash in that users home directory. If you used something else to do the deletion you may be out of luck depending on the program (if you used 'rm' on the command line, the data is as good as gone; undeleting is not fun and far from always successful)
[/I]
Thats what I get for not reading close enough (and usually using keyboard shortcuts (<del> for move to trash and <shift>-<del> to delete) and not knowing the text of the menu-items ...

Holger

---


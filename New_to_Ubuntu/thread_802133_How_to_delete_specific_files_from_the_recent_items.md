---
title: "How to delete specific files from the recent items list?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Donalb on 2008-05-21
Hey all,
OK lets say I open Movie Player and use the file open option to open a new file.
I'll get a list of previously opened files.
So, how do I wither clear that list, or remove items from the list?

I'm using Movie Player as an example. Take a test file as another example. I have a text file with a lot of sensitive info in it from eWallet in XP. However Revelation's XML import isn't working correctly so I'll have to put it in by hand so since it's going to take some time, I haven't locked the text file. 
So if I don't want the teenagers to see the file... how can I delete it from the recently opened files list?

Cheers
Donal

---

### Post by bubba_169 on 2008-05-21
By clicking to "Places->recent->clear" this should clear all the recent items from your menus, including the media player etc.

Dont know about individual files though...

EDIT: Actually I have just found the recent files are listed in a file in your home folder called .recently-used.xbel You can edit this by typing in a terminal

```
gedit .recently-used.xbel
```

It looks to be in xml format and you should be able to take out individual sections without causing any damage. Be careful though and make sure if you delete sections to get the whole section and leave no odd tags...

---

### Post by N.N. on 2008-05-21
If you want to remove all items from the recent documents list, go to "Places" > "Recent documents" > "Clear recent documents". If you want more fine-grained control, edit the hidden file(s) called .recently-used and/or .recently-used.xbel which are located in your home directory. (In the file manager press CTRL+H or go to "View" > "Show hidden files" to toggle the display of hidden files).

---

### Post by Donalb on 2008-05-21
Thanks guys!

---

### Post by Rastanarcharismarx on 2010-05-17
Whenever I delete anything in .recently-used.xbel and save, close and re-open the file; the file seems to be restored to how it was before I edited it. Is there a way to solve this?
I'm using Ubuntu 10.04 Lucid Lynx.

---


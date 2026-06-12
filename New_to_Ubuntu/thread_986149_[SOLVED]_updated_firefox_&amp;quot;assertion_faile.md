---
title: "[SOLVED] updated firefox &amp;quot;assertion failed"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by mike22 on 2008-11-18
Hi, after I updated firefox(don't know what was updated) I am unable to search from the search bar and I cannot manage my bookmarks. I've set the preferences in software sources to update to the newest releases stable or not. Here is the message that I get when I try searching. Please note I am new to ubuntu and I'm 17.


```
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:get_currentEngine()
9:doSearch(yahoo,current)
10:handleSearchCommand([object KeyboardEvent])
11:onTextEntered()
12:handleEnter(false)
13:onKeyPress([object KeyboardEvent])
14:onxblkeypress([object KeyboardEvent])
```

edit: I know little about open source, coding,maybe even computers in general, but does it have to do the script?

---

### Post by beercz on 2008-11-18
> **mike22 said:**
> Hi, after I updated firefox(don't know what was updated) I am unable to search from the search bar and I cannot manage my bookmarks. I've set the preferences in software sources to update to the newest releases stable or not. Here is the message that I get when I try searching. Please note I am new to ubuntu and I'm 17.


```
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:get_currentEngine()
9:doSearch(yahoo,current)
10:handleSearchCommand([object KeyboardEvent])
11:onTextEntered()
12:handleEnter(false)
13:onKeyPress([object KeyboardEvent])
14:onxblkeypress([object KeyboardEvent])
```edit: I know little about open source, coding,maybe even computers in general, but does it have to do the script?

I had a similar problem when I recently updated firefox.  I think it's the database for your bookmarks and settings may have got corrupted.

I solved it by doing the following:

Close Firefox.
[B]
Backup your /home/<username>/.mozilla directory!![/B]

Click Places->Search for files

Browse for the above .mozilla directory (right click on the dialog box and turn on the 'Show Hidden Files' checkbox).

In the 'Name contains' box, enter:

places.sqlite

And then click the Find button.

Move all found files to the wastebasket.

Close the find utility and restart firefox.

Good luck.

---

### Post by mike22 on 2008-11-18
After reading similar posts, I found out that I had to restart firefox. Oops!

---


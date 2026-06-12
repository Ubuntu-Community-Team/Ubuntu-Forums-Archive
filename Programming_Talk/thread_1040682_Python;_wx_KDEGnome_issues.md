---
title: "Python; wx KDE/Gnome issues"
date: 2009-01-15
forum: Programming Talk
---

### Post by Sprut1 on 2009-01-15
I don't know if anyone have been reading the Aircrack-ng Guide: [http://ubuntuforums.org/showthread.php?t=528276&page=26](http://ubuntuforums.org/showthread.php?t=528276&page=26) - but I'm currently making a GUI for the aircrack-ng suit (using the wx modules). Users who have tested my program have reported several bugs that really isn't a problem at my desktop (I run KDE).

First:
```
AttributeError: 'ListCtrl' object has no attribute 'ItemCount'
```
I read the help page for ListCtrl and found out there were no "ItemCount", but instead "GetItemCount()" - either way it works at my desktop, why is this?

Second:
I have a question dialog with the options Yes/No. Clicking No will exit the program and Yes will continue. One user reports that both buttons exit program, at my desktop it works perfectly.

Has this something to do with the window manager, Gnome/KDE? Or has it something to do with different versions of python runtime, wxpython and so on? I'm fairly new to this and need some pointers. Any help at all appriciated.

---

### Post by iQuizzle on 2009-01-16
eek this is a very hairy problem. i had a similar thing today where on some computers, the treectrl would produce a segmentation fault and others not. it turned out that between wx versions 2.6 and 2.8 some changes were made such that a certain library i was importing caused the error.

if i were you, i'd first determine if it's a problem with the wx version (since both 2.6 and 2.8 are in the ubuntu repository). if that's the case, then some change was made such that your program isn't compatible across wx versions.

---

### Post by Sprut1 on 2009-01-16
> **iQuizzle said:**
> eek this is a very hairy problem. i had a similar thing today where on some computers, the treectrl would produce a segmentation fault and others not. it turned out that between wx versions 2.6 and 2.8 some changes were made such that a certain library i was importing caused the error.

if i were you, i'd first determine if it's a problem with the wx version (since both 2.6 and 2.8 are in the ubuntu repository). if that's the case, then some change was made such that your program isn't compatible across wx versions.

Okay thanks, I was afraid this was the case. I checked my packages and realized I had both 2.6 and 2.8 installed, maybe I should remove everything related to 2.6? That way I can determine if that was an issue, or does it automatically use the newest version? Thanks!

---


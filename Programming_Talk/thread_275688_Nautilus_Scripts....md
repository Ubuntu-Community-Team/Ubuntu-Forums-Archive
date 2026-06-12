---
title: "Nautilus Scripts..."
date: 2006-10-11
forum: Programming Talk
---

### Post by fatsheep on 2006-10-11
I've made three nautilus scripts, one that permananetly deletes files as root, one that executes files as root, and one that opens files as root in Gedit.  However, the only one that works is my gedit script :confused: 

> 
#!/bin/bash
gksudo gedit $NAUTILUS_SCRIPT_SELECTED_URIS

(gedit script)

It works perfectly, even opening multiple files.  However the other two scripts do absolutely nothing:

> 
#!/bin/bash
sudo $NAUTILUS_SCRIPT_SELECTED_URIS

(this one is supposed to execute files as root)

> 
#!/bin/bash
sudo rm -r $NAUTILUS_SCRIPT_SELECTED_URIS

(this one is supposed to remove files recursively as root)


I've been fiddling around with these things for quite some time to no avail  so any pointers would be appreciated. :)

---

### Post by catlett on 2006-10-11
I took the easy way out and installed downloaded the scripts here [http://g-scripts.sourceforge.net/index.php](http://g-scripts.sourceforge.net/index.php) , unzipped and dragged them into .gnome . Now I have more scripts thean I can use.:D  Anyways, if noone answers here, that is the site to check out.

---

### Post by skymt on 2006-10-11
Just swap gksudo for sudo in the last two.

---

### Post by fatsheep on 2006-10-11
> **catlett said:**
> I took the easy way out and installed downloaded the scripts here [http://g-scripts.sourceforge.net/index.php](http://g-scripts.sourceforge.net/index.php) , unzipped and dragged them into .gnome . Now I have more scripts thean I can use.:D  Anyways, if noone answers here, that is the site to check out.

Yea I have those but I thought I'd learn more if I made some myself. :) 

> **skymt said:**
> Just swap gksudo for sudo in the last two.

I tried that - same results. :-k

---


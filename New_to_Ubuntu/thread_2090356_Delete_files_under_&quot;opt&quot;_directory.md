---
title: "Delete files under &quot;opt&quot; directory"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by brodedra on 2012-12-02
I recently downloaded some e-books from the Ubuntu software center to learn Ubuntu. I am however not able to delete this books for some reason. I am wondering if this is abnormal or just because being a system folder "opt" under the file system I am not able to manipulate it?

Would there be a way to remove this e-books and reclaim space on my drive :confused:

---

### Post by brodedra on 2012-12-02
I recently downloaded some e-books from the Ubuntu software center to learn Ubuntu. I am however not able to delete this books for some reason. I am wondering if this is abnormal or just because being a system folder "opt" under the file system I am not able to manipulate it?

Would there be a way to remove this e-books and reclaim space on my drive :confused:

PS: Attached file is the screenshot of the folder I wanted to delete permanently.

---

### Post by Foxheadz on 2012-12-02
If you installed them from the software center I would suggest trying to uninstall the packages from the software center as well, if that does not work open the file manager as root ```
gksudo nautilus
``` and then try to delete the files from that window.

---

### Post by arpanaut on 2012-12-02
Have you tried removing through software center?
Usually you would remove things by the same method you acquired, installed etc.
/opt is a system directory so you would need to use the program that put the files there in the first place to remove them.

---

### Post by lisati on 2012-12-02
Threads merged, so that the communiy's ability to help isn't diluted.

---

### Post by brodedra on 2012-12-02
Thanks for your help. It works both ways (of which I wasn't aware) first by using 'gksudo nautilus' command and secondly by uninstalling from the Ubuntu Software center. 

Thanks once again Foxheadz!

---


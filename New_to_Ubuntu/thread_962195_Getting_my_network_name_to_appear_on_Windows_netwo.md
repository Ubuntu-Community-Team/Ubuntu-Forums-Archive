---
title: "Getting my network name to appear on Windows network?"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by wrybread on 2008-10-29
I'm guessing this comes up a lot, but searching around I haven't found any good way to do it. Some people talk about installing DNS servers and all that, but I'm guessing that's no longer necessary?

So what's the current best way to have my Ubuntu box accessible (pingable) by name from a Windows box? Ideally this wouldn't involve installing any software on the Windows boxes, since I need it to work from quite a few Windows boxes.

Thanks for any help.


EDIT: 

Figured it out. I think all I had to do was install winbind, but I needed to install samba anyway. After the following line my Ubuntu box is pingable by name from Windows:

sudo apt-get install samba smbfs smbclient winbind

---


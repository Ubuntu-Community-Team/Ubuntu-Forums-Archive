---
title: "Where is hid-ids.h file?"
date: 2009-09-19
forum: Repositories &amp; Backports
---

### Post by TTonic on 2009-09-19
Hi there =)

I have installed newest sources, and newest headers but still that file is not there. It should be in /lib/modules/2.6.31-10-generic/build/drivers/hid/ but I cannot find the file anywhere in my system.

If I have understood correctly, it should be there according to this: [http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/](http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/) 

Or am I missing something...?

version: Karmic Aplha 6 netbook-remix i386

edit: Now I have learned that, with kernel from kernel.org that file is in place. So I can resolve this now. So this is just another dev clinch. Should I put a word forward according to this matter?

---

### Post by Bachstelze on 2009-09-21
You propably did it wrong the first time. How did you "install the newest sources"?

---

### Post by gali98 on 2009-10-08
I have this same problem.
It is no where on my system, and I need it to compile linux-wacom.
It should be in the ubuntu kernel packages.
I filed a bug here:
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/446776](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/446776)
Kory

---

### Post by urulooke on 2009-12-21
Same problem here, does anyone has found a workaround?:confused:

---

### Post by Favux on 2009-12-21
Hi urulooke,

Welcome to Ubuntu Forums!

Yes gali98 found a workaround, it's available in the Ubuntu git repository:
```
wget http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h
```
Copy it into place:
```
sudo cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h
```

Hope this helps.

---


---
title: "[SOLVED] cant add any workspaces"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by inxygnuu on 2008-10-03
Ok, so just a day ago I had 4 workspaces, when I turned my computer  back on I had 2 workspaces:confused:. And when I right clicked and pressed properties a properties window that only says columns and rows came up.
I really want more than 2 workspaces, can anyone give me any help?:confused::confused::confused::confused:

---

### Post by timstone on 2008-10-03
add more columns

---

### Post by fooman on 2008-10-03
are you running compiz/fusion(visual effects)?

---

### Post by inxygnuu on 2008-10-03
yes I am running Compiz, and I did add a column (it is set to four, by me) but I still have two. I could change the number not too long ago...:-k:-k

---

### Post by fooman on 2008-10-03
running compiz, you will need compizconfig-settings manager.

if it is installed,  you should find it under system > preferences > compizconfig setting manager

if it is not there,  you will need to install it.  use synaptic (system > administration > synaptic package manager), or in a terminal:

```
sudo apt-get install compizconfig-settings-manager
```

after its installed, find it where i mentioned above and open it.  when it opens, look under > general options > desktop size.  change the horizontal virtual size to 4.

see if that works.

---

### Post by inxygnuu on 2008-10-03
thank you, it works!:D:popcorn::KS:):o:guitar:

---


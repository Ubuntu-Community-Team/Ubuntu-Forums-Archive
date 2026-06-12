---
title: "Help!!!!!!"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by raedbenz on 2008-07-14
Hi,
i have by mistaken unpacked a root file for embedded linux, inside the root directory of my ubuntu8.04. and now it doesn't boot.
 any help???

thanks

---

### Post by kool_kat_os on 2008-07-14
"unpacked"?

what do you mean?

next time...use an actual title...

---

### Post by raedbenz on 2008-07-14
> **kool_kat_os said:**
> "unpacked"?

what do you mean?
i did:
tar -xjf /cs-e9302_root2.tar.gz

---

### Post by kool_kat_os on 2008-07-14
just take the files you unpacked and repack them?

---

### Post by raedbenz on 2008-07-14
> **kool_kat_os said:**
> just take the files you unpacked and repack them?

lol 
i cant start my OS...it doesn work...
how,,,the files that are created have the same name as the directoris inside "/", which means everyting is overwitten.

---

### Post by kool_kat_os on 2008-07-14
maybe use the live cd?

---

### Post by tjwoosta on 2008-07-14
> lol
i cant start my OS...it doesn work...
how,,,the files that are created have the same name as the directoris inside "/", which means everyting is overwitten.

well you might be able to just copy the files from the live cd to your harddrive

pop in the live cd

mount your ubuntu partition  

use gksudo nautilus to navigate to the root directory of your harddrive

then use gksudo nautilus to copy all the appropriate files from the root directory of the live cd to the root directory of the harddrive

---

### Post by tjwoosta on 2008-07-15
any luck?

---

### Post by raedbenz on 2008-07-15
> **tjwoosta said:**
> any luck?

yes actually, what i did i got the live cd and installed Ubuntu again without formatting the drive..and all my previous settings now exist (survived)
thanks

---

### Post by candtalan on 2008-07-15
hey! I did not know you could do that! Well done.

---

### Post by raedbenz on 2008-07-15
> **candtalan said:**
> hey! I did not know you could do that! Well done.
lol me either i just discovered it yesterday.
cheers

---

### Post by hyper_ch on 2008-07-15
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---


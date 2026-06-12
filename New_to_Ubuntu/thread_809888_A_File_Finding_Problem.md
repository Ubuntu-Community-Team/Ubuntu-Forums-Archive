---
title: "A File Finding Problem"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by rjdsmiths on 2008-05-27
So I Have Installed Xmms2 But have run into a problem

I Can't find the damn folder it is in. I need to find the folder so I can install a GUI. The place I have looked so far is in my home folder ( yes I did set it to show hidden folders) 

Any Help would be greatly appreciated

Cheers

Rjdsmith

---

### Post by quelx on 2008-05-27
from the terminal try ```
whereis xmms2
```

---

### Post by Paqman on 2008-05-27
> **rjdsmiths said:**
> I need to find the folder so I can install a GUI.

If you're just trying to make a launcher, you don't need the full path. Linux can launch an application using just the name.

---

### Post by rjdsmiths on 2008-05-27
Thanks Quel X for awnseing 

But sadly the locations that wheis xmms2 gives, ther is no xmms2 at all.

any help?

---

### Post by spiderbatdad on 2008-05-27
Sometimes necessary to update the database first:
```
sudo updatedb
```
Then try:
```
whereis xmms

or

locate xmms
```

---

### Post by quelx on 2008-05-27
> **rjdsmiths said:**
> Thanks Quel X for awnseing 

But sadly the locations that wheis xmms2 gives, ther is no xmms2 at all.

any help?

well the binary is **/usr/bin/xmms2**. **whereis** should find it without **updatedb** since it searches the path not the slocate database.  Are you sure you installed it?

What does ```
sudo apt-get install xmms2
``` give you?

---


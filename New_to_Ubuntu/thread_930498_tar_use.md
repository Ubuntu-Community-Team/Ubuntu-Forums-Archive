---
title: "tar use"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by freelancelote on 2008-09-26
Hi,
how do I append some files to a .tar archive using tar programme?

---

### Post by Bucky Ball on 2008-09-26
Try this:

Right click the tar file you want to add files to and choose 'Archive Manager' at the top. One of the icons in there to the right gives you the option to add files.

Is that what you mean? If not, to create one, right click a folder and choose the archive option ... :)

---

### Post by freelancelote on 2008-09-26
Hi, Thanks Bucky Ball.
Sorry I wasn't more clear... I meant using the command line :)

---

### Post by phidia on 2008-09-26
From the man page (see man tar) "tar -r" 
>  -r, --append
              append files to the end of an archive


---


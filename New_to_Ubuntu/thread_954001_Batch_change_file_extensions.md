---
title: "Batch change file extensions?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-10-20
Hi, all;

I'm working with html/php files in Kompozer.  They need to be php on my site, and html when I'm working with them in Kompozer since Kompozer does not natively support php editing and I don't have the skillz to text edit php.  The ugly hack I came up with is batch changing file extensions to php when uploading them to my site, and batch changing them back to html when I'm ready to work on them again.

(1) Is there a good tool where I can select the files I want (20 or so) to batch convert their file extensions from html-->php-->html...?

(2) Is there a less ugly hack for this?

---

### Post by bodhi.zazen on 2008-10-20
I am not following you , you should in theory not need to change the extension to open the files for editing ;)

---

### Post by tarahmarie on 2008-10-20
That may be the theory, but it is not the practice.  One cannot open PHP files in Kompozer.

---

### Post by bodhi.zazen on 2008-10-20
use rename (see man rename)

rename 's/.html/.php/' *.html

---


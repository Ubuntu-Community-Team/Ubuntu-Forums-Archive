---
title: "Newbie problem with GTK+ in Anjuta"
date: 2009-10-12
forum: Programming Talk
---

### Post by Mitchell314 on 2009-10-12
Hello.

I have recently been trying to learn how to use GTK+ in C. I'm using Anjuta IDE, and when I start up a new project, I get "missing packages: libglade-2.0>=2.6.0". I had another issue before that, but I searched here and google and ran "apt-get install libgtk2.0-dev", which solved the first problem. I can't seem to get past this new issue though.

Thanks.

---

### Post by fct on 2009-10-13
Try with:

apt-get install libglade2-dev

Also learn to love this command:

apt-cache search <query>

where <query> could be "libglade devel"

---

### Post by Mitchell314 on 2009-10-13
That worked. Thanks. :)

---


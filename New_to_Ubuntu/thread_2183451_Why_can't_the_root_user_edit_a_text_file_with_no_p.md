---
title: "Why can't the root user edit a text file with no permissions in emacs?"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by noahsdev on 2013-10-24
A file which has chmod 000 can be edited as sudo in pico but not in emacs, why? Emacs can read it but when I try and make a change it says buffer is read-only. I know how to change permissions, that is not a problem, I am just curious why emacs doesn't work in this situation.
Thanks.

---

### Post by Johan De Cauwer on 2013-10-25
I'm not sure about Emacs but LibreOffice has a similar behaviour with read-only files. The program only shows the file. Solution is to write the file to another place and when it's writable the program allows editing. It's a programming question, I guess.

---


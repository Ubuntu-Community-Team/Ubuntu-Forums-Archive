---
title: "How to edit a file using a command?"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by termvrl on 2012-10-17
Hi all,

I want to edit a file. Usually, i "vi *file.conf* " and press "i" and key in "123" and "esc" , ":wq!" . Is there any way that i can do it in single line. like copy and paste.

Thanks.

---

### Post by shreepads on 2012-10-17
Do you mean edit or create?

To create
$ echo 123 > file.conf

To append to existing
$ echo 123 >> file.conf

To do more complicated editing you can try using this approach along with sed, see:
 [http://manpages.ubuntu.com/manpages/lucid/en/man1/9base-sed.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/9base-sed.1.html)

---

### Post by termvrl on 2012-10-17
HI shreepads,

Thanks for your help.

:)

---


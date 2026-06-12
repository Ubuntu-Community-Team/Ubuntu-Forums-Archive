---
title: "what is &quot;file.txt~&quot; ?"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by sha1sum on 2013-10-24
Hello guys

Sometimes I see this:

```
$ ls
file.txt   file.txt~
```

what is this "file.txt~" and why is it there?

---

### Post by deadflowr on 2013-10-24
I never see that, but you can open it and read what it says.:P

Could you think of anything you did that would've generated that?

---

### Post by ||0BL1v10N|| on 2013-10-24
If the file is open it is a temporary copy should the OS encounter an error or powered off unintensionally.

---

### Post by jerome1232 on 2013-10-24
Some editors such as vim, gvim, and gedit, store a backup copy of text files when you save them with a ~ at the end. So it's just the copy previous to your last save.

---

### Post by sha1sum on 2013-10-24
That seems to be the answer. If I open a .txt file with gedit and edit some stuff, it automatically creates a .txt~ file with contains a previous version. I wonder if they delete themselves later on.

Edit: the answer to my previous question seems to be no. The file.txt~ copy does not get deleted, even if the original file is removed.

---

### Post by Lars Noodén on 2013-10-24
The don't get deleted unless you do it manually or set up something to do it automatically.  However, the contents will get replaced each time you edit the main file.  If you want, but I wouldn't recommend it, you can change the configuration of your editor to not make backup files.  They can be a bit of an annoyance, but can come in handy.

---

### Post by sha1sum on 2013-10-24
Thanks for your reply. They don't bother me, I was just curious. :)

---


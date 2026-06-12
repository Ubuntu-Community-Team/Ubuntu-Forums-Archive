---
title: "unrar all rar files in a directory"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Kris2456 on 2008-12-01
I would like to unrar some multi part rar files on my desktop.

However, i would like unrar to do it all in one go with one command. I have tried the command:

$ unrar e *.part1.rar

however this just tells me that there are no files to extract. Essentially, i dont want to have to unrar every file in the folder, and extract the file contained in the same folder (hence the 'e' switch).

I would appreciate any help.

---

### Post by jgoguen on 2008-12-01
Try this command:

```
for file in *.part01.rar; do unrar x ${file}; done;
```

---

### Post by Kris2456 on 2008-12-01
Worked a treat, thanks!

---

### Post by jimmy the saint on 2008-12-01
I believe that file roller (Ubuntu's archive manger) handles multipart .rar files.  When I have multipart archives, it handles them just fine.  When I unrar part1 the entire archive is unpacked.

---

### Post by theozzlives on 2008-12-01
I use archive manager and select the files I want

---

### Post by jgoguen on 2008-12-01
> **Kris2456 said:**
> Worked a treat, thanks!
Great :)  Could you mark the thread as solved?  Doing so will let other users know that you were able to solve your problem, and that they may find an answer here.  To do so, click the **Thread Tools** link above and to the right of your first post.  A menu drops down, one of the options there is to mark the thread as solved.

Thanks! :)

---


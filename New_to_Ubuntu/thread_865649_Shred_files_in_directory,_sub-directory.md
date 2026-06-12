---
title: "Shred files in directory, sub-directory"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by surferninja on 2008-07-20
I am attempting to shred a bunch of folders and their contents and their sub-folders and their contents.  Is their some way to select/extract the contents of the folders and subfolders?

thanks

---

### Post by tamoneya on 2008-07-20
how are you currently doing the shreding them.  Typically if you are in command line you can use a -R option for recursion.

---

### Post by surferninja on 2008-07-20
Yes, i am doing this the command line.  To try to select the files, i was using * but the command line said it couldn't shred directories

---

### Post by tamoneya on 2008-07-20
can you give me the command you are using.  It probably just needs a -R option.

---

### Post by surferninja on 2008-07-20
That is to say, the command i was using looked like this
```

shred * -n 8 --remove
```

---

### Post by tamoneya on 2008-07-20
read this:
[http://www.slac.stanford.edu/comp/unix/secure-erase.html#EraseFiles](http://www.slac.stanford.edu/comp/unix/secure-erase.html#EraseFiles)
Just be careful when you do it.  Carefully think about the symbolic links comment they make to make sure you dont erase something you dont mean to.

---


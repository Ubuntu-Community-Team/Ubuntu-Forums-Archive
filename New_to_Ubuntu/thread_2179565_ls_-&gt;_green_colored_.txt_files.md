---
title: "ls -&gt; green colored .txt files"
date: 2013-10-08
forum: New to Ubuntu
---

### Post by sha1sum on 2013-10-08
When I type the command **ls** in the command line, the file names of certain text files are displayed in green. What does this mean?

---

### Post by CharlesA on 2013-10-08
It means they have execute permissions.

You can verify that by running:
```
ls -l
```

Permissions can be altered by using chmod:

```
chmod -X /path/to/files
```

---

### Post by Iowan on 2013-10-08
Those look like executable files (scripts?).

Oops - outtyped by **CharlesA** again...

---

### Post by heir4c on 2013-10-08
I find something that answer your question:
[http://askubuntu.com/questions/17299/what-do-the-different-colors-mean-in-the-terminal](http://askubuntu.com/questions/17299/what-do-the-different-colors-mean-in-the-terminal)

---

### Post by sha1sum on 2013-10-09
Thanks for the information guys.

I found that indeed the .txt files were executable. I tried to change that using the following command:

```
chmod 600 file.txt
```

However it did not work, the permissions stayed -rwx------. When I moved the file to another directory however, the same command did work. What could be going on?

---


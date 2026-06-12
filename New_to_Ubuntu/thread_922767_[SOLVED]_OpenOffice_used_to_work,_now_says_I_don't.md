---
title: "[SOLVED] OpenOffice used to work, now says I don't have permission to use it."
date: 2008-09-17
forum: New to Ubuntu
---

### Post by iaskedalice09 on 2008-09-17
I installed Abiword for the time being but I need the presentation programme. Here's a screencap. I changed the ownership of the file to me but nothing works. What do I do?

Thanks!

---

### Post by lazyart on 2008-09-17
That's not a file, it's a directory.  Try```
sudo chown tom:tom -R /home/tom/.openoffice.org2
```That will give you ownership of everything in that directory and any subdirectories that might be in there.

---

### Post by iaskedalice09 on 2008-09-17
Thanks, the -R did it. I thought that might be it since to delete a directory, you do rm -R. Is it the same for copy and the like? That is, to copy an entire directory, do you do cp -R /path/to/folder/?

Thanks so much again...I should know that!

---

### Post by lazyart on 2008-09-19
It's probably a good bet, but do cp --help to be sure.

---

### Post by Mornedhel on 2008-09-19
man cp

```

[...]
-R, -r, --recursive
              copy directories recursively
[...]

```Yup. There generally is a --recursive option for basic utilities. When there isn't, you write a loop around your command with a Bash script.

---


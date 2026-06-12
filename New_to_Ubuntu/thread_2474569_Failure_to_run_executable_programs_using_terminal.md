---
title: "Failure to run executable programs using terminal"
date: 2022-05-03
forum: New to Ubuntu
---

### Post by anthony-2 on 2022-05-03
When i was running ubuntu 21.10 i could use "make" to create executable files for C and run them with a simple ./nameoffile command just the same with nasm files let alone any other command. But since upgrading(fresh install from disk) to 22.04 all these commands are unrecognizable by the system, if i just type the command[$./nameoffile] it tells me that i don't have permissions[bash: ./nameoffile permission denied] if i prefix sudo e.g sudo ./nameoffile i get "sudo: ./nameoffile: command not found " result. This has put a strain on work progress.

---

### Post by vanadium on 2022-05-03
1) Make sure your current directory is the one where "nameoffile" resides.
2) Make sure "nameoffile" has the executable bit set.

---

### Post by Impavidus on 2022-05-03
There could be multiple issues here.

**make** isn't installed by default (I think). Have you installed it after you installed 22.04? You also need a compiler.

When you compile something, the compiler automatically adds execute permissons to the file. At least it does so on 21.10 and has done so for ages. Has that changed on 22.04? Make sure the executable has execute permission for you. When no compiler is involved (executable scripts), you always have to add execute permission yourself.

Just prefix sudo isn't the way to deal with "permission denied". Use sudo only when you need it and make sure you know why you need it.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ActionParsnip on 2022-05-03
if the file you are running is not in the folder your terminal is in, then that will fail. You can see your location with
```

pwd

```
If this needs changing then use the "cd" command exactly the same way as you would in Windows.

---


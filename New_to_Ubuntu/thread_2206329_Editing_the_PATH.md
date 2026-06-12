---
title: "Editing the PATH"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by LYXDhE3 on 2014-02-18
Hello,
I am relatively new to Ubuntu and UNIX-like operating systems. I am having difficulty knowing how to edit the PATH environment variable.
I was trying to install TeX live. I tried to follow the online directions, but I got stuck at the part where it said you have to add the directory where the TeX live binaries are. I can't figure out which directory that is.
As advised, I searched the forums before posting. I did find another question involving installing TeX live, but in that person's case, their installation was in a completely different directory than mine. So it didn't help me.
I tried looking around the file system, and I see so many folders that have "tex" and "bin" in them, how do I know which one it is? Would **/usr/share/ **be enough, or does the item need to be longer?
I realize that environment variables are not something I want to blindly play around with if I'm not sure.
I subsequently found another program that serves the purpose I orginally downloaded the first one for; however, it is still something I want to know about installing software in general.

---

### Post by fdrake on 2014-02-18
to find the relative libraries do
```
whereis tex
```

to add the folder to your path
```
echo "export PATH=$PATH:/path/of/tex" >> ~/.bashrc 
```
logout/login

---

### Post by LYXDhE3 on 2014-02-18
Thanks!

---


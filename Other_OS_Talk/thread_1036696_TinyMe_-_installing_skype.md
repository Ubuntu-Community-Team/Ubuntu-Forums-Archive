---
title: "TinyMe - installing skype"
date: 2009-01-11
forum: Other OS Talk
---

### Post by Ampi on 2009-01-11
I'm new to TinyMe and I'm trying to install skype. 

Of course I cannot find it in the repositories, so I'm trying to compile it myself (tar.bz2). 

When I open the tar.bz2 I find no configure file and the readme doesn't say much. There is also an executable, but if I try to run: 
```

./skype:error while loading shared libraries: libXss.so.1:cannot open shared object file: No such file or directory

```
Trying to download the missing lib, using (as root)
```
apt-get install libXss.so.1
```
I get
```
E: Couldn't find package libXss.so.1
```

What could I do to get Skype running? (Does this go for all programs that are not in the repositories?)

---

### Post by Hallvor on 2009-01-11
It is in the repos!

Did you click reload in Synaptic? You are supposed to have one PCLinuxOS repository as well as the TinyMe repository. Skype should be in the PCLinuxOS repository.

---

### Post by Ampi on 2009-01-11
Check! I did that! So now it works fine :) thanks!

---


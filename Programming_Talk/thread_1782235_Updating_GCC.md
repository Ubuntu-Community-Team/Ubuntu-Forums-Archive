---
title: "Updating GCC"
date: 2011-06-14
forum: Programming Talk
---

### Post by malakar.subhendu on 2011-06-14
Can anyone please tell me how to update the gcc.
Mine is Ubuntu 10.10 which has gcc 4.4.5.
I want to update it to 4.6.
Thanks.

---

### Post by kvv_1986 on 2011-06-14
You could compile it from source, but a better option would be to use Virtualbox and install a distro which has the gcc version you need. It will save you a lot of hassle.

If you don't want to use Virtualbox for some reason, get the GCC source from [here]("http://ftp.gnu.org/gnu/gcc/gcc-4.6.0/"), and follow the instructions in readme to compile it.

After this, you will have to export the path with the GCC executable. I think it would be the "<directory you compiled it to>/bin".

```
export PATH=<insert gcc-executable-directory>:$PATH
```

So when you type "gcc --version" in bash, it will search $PATH for gcc, and will return the first instance of it that it finds.

But, I would still suggest that you use Virtualbox. It will likely save you some time.
If you use Virtualbox, use Fedora 15 XFCE, as it will run better than gnome.

---

### Post by malakar.subhendu on 2011-06-15
Is there any way to reinstall the given gcc version completely with the newer version?

---

### Post by TwoEars on 2011-06-15
> **malakar.subhendu said:**
> Is there any way to reinstall the given gcc version completely with the newer version?

Can I ask why you want to do this? I don't suggest it at all - if you're new to programming, newer isn't always better, especially not with changing your system's provided compiler.

---


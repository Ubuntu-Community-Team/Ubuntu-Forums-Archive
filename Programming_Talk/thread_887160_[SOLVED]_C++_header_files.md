---
title: "[SOLVED] C++ header files"
date: 2008-08-11
forum: Programming Talk
---

### Post by Kolmogorov on 2008-08-11
Hi,

Is there anyone that know where i can find the various header files of the GNU g++ compiler ? Is there a special bash command to find these on my comp ?

Thanks

---

### Post by dwhitney67 on 2008-08-11
Look under /usr/include/c++/4.2.3, or whatever version of GCC you are using.

```
$ gcc --version
```

---

### Post by Kolmogorov on 2008-08-11
That's it ! Thank you very much ;).

---

### Post by LaRoza on 2008-08-11
> **Kolmogorov said:**
> Hi,

Is there anyone that know where i can find the various header files of the GNU g++ compiler ? Is there a special bash command to find these on my comp ?

Thanks

Although you got an answer, you can also use shell tools like whereis and find.

```

~$whereis stdio.h
stdio: /usr/include/stdio.h
~$


```

---


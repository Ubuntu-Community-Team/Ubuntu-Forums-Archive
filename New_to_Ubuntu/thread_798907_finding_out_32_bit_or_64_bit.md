---
title: "finding out 32 bit or 64 bit"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by psychoelf000 on 2008-05-18
how do I find out if my Ubuntu is 32 bit or 64 bit? and uname -a does not help at all.
This is a ubuntu shipped with a new dell pc and shows as version 7.10. The processor also supports 64 bit.

---

### Post by tamoneya on 2008-05-18
```
uname -m
```
x86_64 = 64 bit
i686 = 32 bit

---

### Post by Vicfred on 2008-05-18
```
unam -m
```

on firefox > help > about mozilla firefox

```
Mozilla/5.0 (X11; U; **Linux x86_64**; en-US; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5
```

---

### Post by psychoelf000 on 2008-05-18
> **tamoneya said:**
> ```
uname -m
```
x86_64 = 64 bit
i386 = 32 bit

thank you very much. I was getting real mad at my computer.

---

### Post by tamoneya on 2008-05-18
> **Vicfred said:**
> ```
unam -m
```

on firefox > help > about mozilla firefox

```
Mozilla/5.0 (X11; U; **Linux x86_64**; en-US; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5
```

You can technically have 32 bit firefox installed on a 64 bit machine and it is a common way for some people to deal with flash not working with 64 bit browsers.  So if it says 64 bit you can be positive that you have a 64 bit machine but if it says 32 bit you cant be quite sure.  Not a bad method.  But also not totally foolproof.

---

### Post by loki_dre on 2010-01-26
thanks that worked

---

### Post by PCA on 2010-01-27
> **Vicfred said:**
> ```
unam -m
```

on firefox > help > about mozilla firefox

```
Mozilla/5.0 (X11; U; **Linux x86_64**; en-US; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5
```

I tried that, I don't think It tells you what cpu you have. For me, it shows i686. and I have a 64 bit dual core.

---

### Post by howefield on 2010-01-27
> **PCA said:**
> I don't think It tells you what cpu you have.

If you want to know if your CPU is 64 bit, type this into a terminal.

```
cat /proc/cpuinfo | grep lm
```

If you get output, it is 64 bit, if you get nothing then it's 32 bit.

---

### Post by PCA on 2010-01-29
Yep.. That gives me an output.. One more thing, what do you guys think of the 64 bit version of the OS? I tried installing the 64 bit version of Jaunty once, but I had problems with it. It used to hang/ crash. did anyone else have this problem? and are the same software available for 64bit? also is there any perfomance improvement?

---

### Post by Merk42 on 2010-01-29
> **PCA said:**
> Yep.. That gives me an output.. One more thing, what do you guys think of the 64 bit version of the OS? I tried installing the 64 bit version of Jaunty once, but I had problems with it. It used to hang/ crash. did anyone else have this problem? and are the same software available for 64bit? also is there any perfomance improvement?

There is very little, to no reason not to use 64bit. If your processor supports 64bit, get 64bit.
Even stuff like Java and Flash have 64bit versions which work fine.

[Here is an article](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1) showing 64bit's improvement over 32bit, yes it is more than just "more RAM".

---

### Post by philinux on 2010-01-29
> **psychoelf000 said:**
> how do I find out if my Ubuntu is 32 bit or 64 bit? and uname -a does not help at all.
This is a ubuntu shipped with a new dell pc and shows as version 7.10. The processor also supports 64 bit.

Have a read of this benchmark comparison.
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

I've been running 64 bit for 18 months. Not one hassle.
32 bit apps like adobe acroread pull in ia32libs and nspluginwrapper etc and run just fine. I use the 64 bit flash plugin from adobe which is much better than the 32 bit version.

---

### Post by Sef on 2010-01-29
Locked. Necromancing.

---


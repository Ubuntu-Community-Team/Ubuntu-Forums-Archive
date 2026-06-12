---
title: "Which version am I running? Amd 64 or x8s?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by boron on 2008-09-13
how can I tell which version of Ubuntu I've installed? I have an AMD 64 processor and installed using Wubi. Did it detect my processor and download the correct version or did I get the x86 version? How can I tell?
Thanks in advance.

---

### Post by Rhubarb on 2008-09-13
Open up a terminal (Applications --> Accessories --> Terminal)
and type this in:
```
uname -m
```

---

### Post by SunnyRabbiera on 2008-09-13
or if you need a gui app go up to system> administration> system monitor.
In that check check the first tab.

---

### Post by Rhubarb on 2008-09-13
> **SunnyRabbiera said:**
> or if you need a gui app go up to system> administration> system monitor.
In that check check the first tab.

In this particular case, the system monitor won't show you the platform architecture, only the kernel being used.
You're best of using the terminal with **uname -r** in this case.

As you can see here:

---

### Post by SunnyRabbiera on 2008-09-13
> **Rhubarb said:**
> In this particular case, the system monitor won't show you the platform architecture, only the kernel being used.

You're best of using the terminal with **uname -r** in this case.

well it does list the possessor and kernel type, I think he was asking what kernel he was using.

---

### Post by egalvan on 2008-09-13
> **SunnyRabbiera said:**
> or if you need a gui app go up to system> administration> system monitor.
In that check check the first tab.

Is there an equivalent in Kubuntu?

---


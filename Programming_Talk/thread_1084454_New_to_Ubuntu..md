---
title: "New to Ubuntu."
date: 2009-03-02
forum: Programming Talk
---

### Post by Evontroy on 2009-03-02
Hello all, 

I've been programming in Windows for a little over a year now, using Visual Studio for my development needs. I'm new to Ubuntu and need advice for finding a compiler similar to Visual Studio. I will generally be coding in C++ and maybe a little C#. Thanks in advance!

---

### Post by howlingmadhowie on 2009-03-02
the standard compiler for c++ is the g++ translator for the gnu compiler collection. you can install this by typing:

```
sudo apt-get install build-essential
```

in a terminal, or alternatively by going to "system->administration->Synaptic package manager" and selecting "build-essential" in the package list. 

you seem to be looking for an IDE as well. in that case i can recommend Netbeans or (at a stretch) eclipse. both can also be installed over the Synaptic package manager. 

one point to notice is that the version of eclipse you can install over Synaptic is quite old. you may prefer to download a newer version from the eclipse website directly.

---

### Post by Evontroy on 2009-03-02
> **howlingmadhowie said:**
> the standard compiler for c++ is the g++ translator for the gnu compiler collection. you can install this by typing:

```
sudo apt-get install build-essential
```

in a terminal, or alternatively by going to "system->administration->Synaptic package manager" and selecting "build-essential" in the package list. 

you seem to be looking for an IDE as well. in that case i can recommend Netbeans or (at a stretch) eclipse. both can also be installed over the Synaptic package manager. 

one point to notice is that the version of eclipse you can install over Synaptic is quite old. you may prefer to download a newer version from the eclipse website directly.

Thanks for the speedy reply. One of the reasons why I am slowly transitioning to Linux is because of the large community (that's pretty much evident here).

---

### Post by monkeyking on 2009-03-02
welcome :)

---

### Post by konqueror7 on 2009-03-02
for C# you can try Mono Develop, but the IDE is far from similar to Visual Studio..in my setup, i use an XP vm, and there develop .net applications within ubuntu...

---

### Post by directhex on 2009-03-02
> **konqueror7 said:**
> for C# you can try Mono Develop, but the IDE is far from similar to Visual Studio..in my setup, i use an XP vm, and there develop .net applications within ubuntu...

Monodevelop has more in common with its distant ancestor SharpDevelop

One plus point for MD is the integrated GTK# designer

---


---
title: "Creating deb file locally: dependencies"
date: 2017-02-12
forum: Packaging and Compiling Programs
---

### Post by Achilles124 on 2017-02-12
One of the things that is asked for when making a deb file is dependencies. I have two questions on that:

1. How to find what the dependencies are the package depends on?
2. Is it really necessary to fill that in when you are making a package only for local use?

Thanks beforehand.

---

### Post by howefield on 2017-02-12
Thread moved to the "*Packaging and Compiling Programs*" forum for a better fit.

---

### Post by ian-weisser on 2017-02-12
1) If you compile the binary in the package, the dependencies are all the libs you link to. If you use a script (like Python), the dependencies are your includes.

2) Not really, but doing it right makes maintaining the package easier.

---

### Post by &amp;KyT$0P# on 2017-02-13
> **ian-weisser said:**
> 1) If you compile the binary in the package, the dependencies are all the libs you link to.
And if you don't know what libs the binaries are linking to, see [this thread]("https://ubuntuforums.org/showthread.php?t=2346506") for one way to find out.

> **Achilles124 said:**
> 2. Is it really necessary to fill that in when you are making a package only for local use?
If you are planning to install it on multiple machines with different installed packages, I would say yes.

---

### Post by Achilles124 on 2017-02-14
Thank you for your answers.

---


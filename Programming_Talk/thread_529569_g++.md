---
title: "g++"
date: 2007-08-19
forum: Programming Talk
---

### Post by Fonon on 2007-08-19
Hi.  I'm trying to get into programming with C++, and I recently downloaded Geany.  It claimed it didn't work because it couldn't find the "g++".  So, I tried Anjuta, and the same thing happened.  I did some research, and it turns out that it is the compiler, but the installation instructions are very unclear to me.  Could anyone help me out on this one?  Thanks.

---

### Post by Jessehk on 2007-08-19
```

sudo aptitude update && sudo aptitude install build-essential

```

:)

---

### Post by Fonon on 2007-08-19
I put all of that in the terminal at one time, right?  Thanks!

---

### Post by Jessehk on 2007-08-19
> **Fonon said:**
> I put all of that in the terminal at one time, right?  Thanks!

Yes. By default Ubuntu does not install the compilers and libraries necessary to program in C and C++.

The build-essential package installs everything. The command I gave you is actually 2 commands linked together by the "&&" which runs the second one if the first one succeeds.

The first command:
```

sudo aptitude update

```

Updates the software sources and the second command:
```

sudo aptitude install build-essential

```

installs the *build-essential* package.

---

### Post by Fonon on 2007-08-19
Thank you!  I tried it, and it was just what I needed.

---


---
title: "Packaging Java source code"
date: 2007-11-11
forum: Programming Talk
---

### Post by dismal_denizen on 2007-11-11
What is the best way to package my Java source code to make it easy for others to build? Is there a Java version of make?

---

### Post by Ramses de Norre on 2007-11-11
> **dismal_denizen said:**
> Is there a Java version of make?
Absolutely, Apache's [Ant](http://ant.apache.org/).

---

### Post by rekahsoft on 2007-11-11
> **Ramses de Norre said:**
> Absolutely, Apache's [Ant](http://ant.apache.org/).

Could not agree more :D :D :P

---

### Post by kknd on 2007-11-11
> **Ramses de Norre said:**
> Absolutely, Apache's [Ant](http://ant.apache.org/).

+1

Ants are cool.

---

### Post by egibby on 2007-11-11
Depending on what your needs are, it might be simpler to just bundle all the compiled byte code (since it is portable) into a jar file and distribute that.  Others can then include your jar file when building their projected and be able to call the classes in your code.

-- egibby

---

### Post by dismal_denizen on 2007-11-11
Thanks guys, I'll take a look at Ant. I will create bytecode versions of each project, but I want to be open source friendly so that other Java programmers can get ideas from what I do.

---

### Post by geirha on 2007-11-12
There's also maven [http://maven.apache.org/](http://maven.apache.org/)

---


---
title: "Python and C++"
date: 2006-03-09
forum: Programming Talk
---

### Post by krypto_wizard on 2006-03-09
I was a C Programmer for a while. Lately started to learn Python for one small project at school. I joined a small company where they use C++ for development.

Can we use Python and C++ together ? I mean create some classes in Python and some number crunching algorithms coded in C++ (for speed) and integreate both of them.

Could somebody just show a real small example or give pointers to the same.

Thanks

---

### Post by hod139 on 2006-03-09
You can, and this has been done.  [http://numeric.scipy.org/](http://numeric.scipy.org/)

---

### Post by mdh on 2006-03-09
You can call C++ routines from Python scripts using the swig interface. See swig [homepage]("http://www.swig.org/") for more information.

---

### Post by thumper on 2006-03-09
I have used swig successfully for moderate sized projects.

For something small, I just did a hand crafted plug-in following the example in Python in a Nutshell.

---


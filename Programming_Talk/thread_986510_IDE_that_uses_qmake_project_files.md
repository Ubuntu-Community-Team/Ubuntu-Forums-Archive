---
title: "IDE that uses qmake project files"
date: 2008-11-18
forum: Programming Talk
---

### Post by 10nitro on 2008-11-18
Does anyone know of an IDE that would let me use a qmake .pro project file as the project file?

---

### Post by samjh on 2008-11-18
I'm not sure, but have a look at QDevelop.

---

### Post by snova on 2008-11-18
All IDE's I know of have their own bookkeeping to do, and QMake project files don't cater to anything more than the build process. So although one might exist, don't count on it.

---

### Post by Zugzwang on 2008-11-19
> **snova said:**
> All IDE's I know of have their own bookkeeping to do, and QMake project files don't cater to anything more than the build process. So although one might exist, don't count on it.

Actually, the IDE **could** write its additional data as comments into this .pro file. So it wouldn't be a problem.

But I don't know any such IDE either. Kdevelop can normally import such project quite well.

---

### Post by tanderson on 2008-11-19
Maybe qt creator. It's beta now but looks promising.

[URL="http://trolltech.com/developer/qt-creator"]

---

### Post by samjh on 2008-11-20
I can now confirm that QDevelop does use *.pro files to manage projects.

---


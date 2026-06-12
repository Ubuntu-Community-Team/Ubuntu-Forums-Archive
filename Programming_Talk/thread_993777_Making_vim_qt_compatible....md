---
title: "Making vim qt compatible..."
date: 2008-11-26
forum: Programming Talk
---

### Post by kcode on 2008-11-26
I will be working on qt project this December. I want to know if there exists any plugin for vim, which will make coding (qt) easier. 

thanks

---

### Post by samjh on 2008-11-26
Although I use vim for most of my coding needs, I prefer to use an IDE for Qt, namely QDevelop (sudo apt-get install qdevelop) because it makes managing source files easier and uses Qt's *.pro files to manage projects.

Sorry, it doesn't really answer your question.  I've been trying to find a decent Qt addon for vim too, but no luck.  QDevelop is nice though, you should try it. :)

---

### Post by kcode on 2008-11-26
> **samjh said:**
> Although I use vim for most of my coding needs, I prefer to use an IDE for Qt, namely QDevelop (sudo apt-get install qdevelop) because it makes managing source files easier and uses Qt's *.pro files to manage projects.

Sorry, it doesn't really answer your question.  I've been trying to find a decent Qt addon for vim too, but no luck.  QDevelop is nice though, you should try it. :)

Yaa...I was felling IDE for Qt would be better option. Is KDevelop better than eclipse || Netbeans for a Qt project?

vim rocks! :wink:
Thanks

---

### Post by samjh on 2008-11-27
I haven't used KDevelop, and have only used Eclipse for Java and ordinary C++ projects.

IMHO, you'd probably be better off with KDevelop.  However, Qt4 version of KDevelop have not yet been released, so KDevelop is still tied to Qt3 I think.

Try QDevelop.  It's simple and easy to use.  Qt Software has also released Qt Creator, which is a somewhat more sophisticated IDE; see their website for details.

---

### Post by tlinuxx on 2010-08-14
Yes we can.To build the Qt tags just paste the following code in bash, ctags -R --c++-kinds=+p --fields=+iaS --extra=+q -f FILE_LOCATION /usr/include/qt4, now vim will do the completion work after '.' or '::' or '->'

---


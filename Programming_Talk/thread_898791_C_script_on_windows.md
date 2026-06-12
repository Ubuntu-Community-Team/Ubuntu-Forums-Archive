---
title: "C script on windows"
date: 2008-08-23
forum: Programming Talk
---

### Post by jon zendatta on 2008-08-23
hello
i have a little c script i wrote on ubuntu. i need to save, compile & run on my employers windows xp.
i googled this & got mixed messages.
so far i have installed this [http://www.mingw.org/](http://www.mingw.org/) compiler.
cheers

---

### Post by shankhs on 2008-08-23
You can install cygwin and do all the programming stuffs in windows which you did in ubuntu or any linux.
google cygwin and you will get every info.

---

### Post by loganwm on 2008-08-23
On the MinGW site you can download the auto installer:

[https://sourceforge.net/project/showfiles.php?group_id=2435&package_id=240780](https://sourceforge.net/project/showfiles.php?group_id=2435&package_id=240780)

and Install it, it has instructions how how to add to your path as well, follow them and it should work very similarly to on your current box.

[http://www.mingw.org/node/24](http://www.mingw.org/node/24)

The above link is a link to one of the tutorials on their site about installing.


I haven't tried anything advanced yet, but all of the standard C library programs should work, follow the guides on the site and you're all set. :)

---

### Post by LaRoza on 2008-08-23
C "script"? You want an interpreter? I use tcc [http://bellard.org/tcc/](http://bellard.org/tcc/)

---

### Post by Majorix on 2008-08-23
He said in his post that he wanted a compiler. I think he did not mean "scripting". Other than that, tcc is not the de facto compiler, so there might be issues for the user of it when he wants to port his code.

---

### Post by ad_267 on 2008-08-23
Another option is to use Microsoft Visual Studio. You can get VS C++ Express for free from [http://www.microsoft.com/express/2005/download/default.aspx](http://www.microsoft.com/express/2005/download/default.aspx)

---

### Post by LaRoza on 2008-08-23
> **Majorix said:**
> He said in his post that he wanted a compiler. I think he did not mean "scripting". Other than that, tcc is not the de facto compiler, so there might be issues for the user of it when he wants to port his code.
tcc is also a compiler (in fact, it out performs gcc in some ways)

tcc follows the C standard, so it shouldn't be a problem.

---


---
title: "Can I get Python calltips in geany?"
date: 2009-11-01
forum: Programming Talk
---

### Post by rob86 on 2009-11-01
In some editors/int. shells like PyShell it will give information about a function you are typing.  You know, typing "time.clock(" will pop up a window with some helpful information about the function describing its parameters and a little paragraph about its use.  I think these are called call tips? I'm not sure, really.  Is there any way to get this in geany for python functions or is geany not capable of this?

---

### Post by StunnerAlpha on 2009-11-02
I am interested in knowing this as well. But I doubt it as geany is a really light editor. I have no clue though and would like to know for sure. Thanks.

---

### Post by rob86 on 2009-11-02
> **StunnerAlpha said:**
> I am interested in knowing this as well. But I doubt it as geany is a really light editor. I have no clue though and would like to know for sure. Thanks.

 I looked at the Geany manual and it says to use CTRL-Shift-Space (I think, I can't remember now but its in the manual) to bring up a call tip, though I did this all over my code and I couldn't get anything to come up when using these keys. I don't even know if what I'm trying to get is called a call tip, because I haven't been able to make a "calltip" show up to know what it is;)  I asked this questions on three forums and I haven't got a single answer for this question. I also googled for python calltips geany and i couldn't find much. I don't know, maybe it's a stupid question or something :)

---

### Post by Can+~ on 2009-11-02
I'm not sure, sometimes geany does help you, others not. I get the feeling that it tries to remember certain strings, because sometimes, it offers me C completion when writing python.

If you want full code completion and tips, install Eclipse and it's python plugin.

---

### Post by yanxy on 2012-04-04
I write a plugin to show tips for python in geany. You can download it from [my blog]("http://blog.sciencenet.cn/home.php?mod=space&uid=404069&do=blog&id=554934") and try it.

Good Luck!


[IMG]http://image.sciencenet.cn/album/201204/05/215634eoss8hq8oyq8qky3.png[/IMG]


[IMG]http://image.sciencenet.cn/album/201204/05/2156348xpatemjxx86aisp.png[/IMG]

---

### Post by MadCow108 on 2012-04-04
you might want to look into a more specialized python ide. The nature of python offers a lot of possibilities for ide's which are hard to export in a general editor like geany.
e.g. [http://code.google.com/p/spyderlib/](http://code.google.com/p/spyderlib/)

---

### Post by yanxy on 2012-04-05
> **MadCow108 said:**
> you might want to look into a more specialized python ide. The nature of python offers a lot of possibilities for ide's which are hard to export in a general editor like geany.
e.g. [http://code.google.com/p/spyderlib/](http://code.google.com/p/spyderlib/)

It seems that spyder can only show tips(doc) for python's built-in module and can't deal with alias of module. 

For example, when I type:
import time as t
t. (show nothing......)

or

import scipy
scipy. (show nothing......)

---


---
title: "Tkinter or not?"
date: 2010-11-11
forum: Programming Talk
---

### Post by CaptainMark on 2010-11-11
Im a programming noob learning python at the moment from a book. The book is not linux specific and the author uses the gui toolkit Tkinter, 

Question 1: Is this included in Ubuntu? I have an entry for python-tk in the software centre that looks like it could be the one
Question 2: Is this a simlilar thing to GTK? I know this name and assume it is a popular choice
Question 3: (If they are a similar thing.) What are the pros and cons of each?
Question 4: How much do they vary in use? Really am i going to find it difficult using another GUI toolkit than the one used in the book.

Thanks in advance for any answer/opinions
Mark

---

### Post by dv3500ea on 2010-11-11
1) Yes, python-tk is the package for it
2) Yes, they are both GUI toolkits
3) GTK fits very well into the desktop but TK doesn't (it looks really ugly). TK is easier to learn (from perl TK experience)
4) All GUI toolkits vary in their use but you can use the same event oriented principles in them all.

I highly reccommend [this tutorial]("http://zetcode.com/tutorials/pygtktutorial/") for pygtk. I found GTK really confusing until I read this.

---

### Post by juancarlospaco on 2010-11-12
You can do VERY nice things with TK.
I.E.:

NameBench: [http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)
"Namebench was written using open-source tools and libraries such as Python, Tkinter"

Skencil: [http://www.skencil.org/](http://www.skencil.org/)
"Skencil is written in Python with an Tkinter GUI."

SK1: [http://sk1project.org/modules.php?name=Products&product=sk1&op=screenshots#screenshots](http://sk1project.org/modules.php?name=Products&product=sk1&op=screenshots#screenshots)
"We migrated to TTK, added CMYK support, color management, and Cairo-based engine."

*SK1 its like a Corel Draw, but Open Source and made using TK.*

---

### Post by CaptainMark on 2010-11-14
Thanks i think ill try GTK if I find it too difficult i will learn tk from the book and get a gtk book later.

---


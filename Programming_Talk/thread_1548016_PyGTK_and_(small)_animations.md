---
title: "PyGTK and (small) animations"
date: 2010-08-07
forum: Programming Talk
---

### Post by devildante_ on 2010-08-07
Hello,

I've been searching for a few days for a way to do some animation stuff with GTK+ widgets (not big effects, just something like fading and transition to another widget/container), but I haven't been able to find anything. Can you point me to a tutorial/documentation/code snippet related to this issue?
I program mainly in Python - but if all you've got is C related, no problem :)

Thank you,
devildante

---

### Post by km0r3 on 2010-08-07
> **devildante_ said:**
> Hello,

I've been searching for a few days for a way to do some animation stuff with GTK+ widgets (not big effects, just something like fading and transition to another widget/container), but I haven't been able to find anything. Can you point me to a tutorial/documentation/code snippet related to this issue?
I program mainly in Python - but if all you've got is C related, no problem :)

Thank you,
devildante

Hello and Welcome to the Forums devildante_,

Unfortunately it wasn't very easy to find something that might fit your needs, but I can come up with the following links:


[LIST]
[*]The guys over at OLPC have made a small hack to animate simple animations with GTK. I suggest you might check it out yourself: [http://wiki.laptop.org/go/PyGTK/Smooth_Animation_with_PyGTK](http://wiki.laptop.org/go/PyGTK/Smooth_Animation_with_PyGTK)
[*]An interesting project I have found is [clutter]("http://www.clutter-project.org/"), which does the following:
> Clutter is an open source ([LGPL 2.1]("http://www.clutter-project.org/about/licence")) software library for creating fast, compelling, portable, and dynamic graphical user interfaces.
Sounds just like what you need, and the best thing is that it has [Python language bindings]("http://www.clutter-project.org/about/language-bindings").
[/LIST]
Let me know if you have found something, and don't forget to mark this thread as solved if you haven't got any more questions.

---

### Post by km0r3 on 2010-08-07
Oh, I have seen a live demo of clutter in the [Acire Snippets]("http://aciresnippets.wordpress.com/") repository. It has also other great snippets you might find useful.

---


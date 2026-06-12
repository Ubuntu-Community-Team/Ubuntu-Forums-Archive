---
title: "PyQt Question"
date: 2006-10-02
forum: Programming Talk
---

### Post by kuja on 2006-10-02
Alrighty, I just recently started using PyQt, and am dirt new to both Python and Qt. Fortunately most of it's coming along pretty easy, especially seeing as the app is small and simple. 

I'm hoping someone around here has some experience with it :P

I've got one issue that seems to stand in my way at the moment, and that is, that if a function takes a sustainably long time to do things, for example if it's fetching a file, or something of that nature, the gui hangs until the entire function is done.

Here's what I'm working with at the moment: [http://www.xnowherex.net/ubuntu/simple64-0.6.4.tar.bz2](http://www.xnowherex.net/ubuntu/simple64-0.6.4.tar.bz2)

Anyone know what to do about it?

---

### Post by flightcrank on 2006-10-02
you might want to look into python threads, or use some sort of QT progress bar to display to the user that stuff is happining ect

---


---
title: "Is it possible to recreate a Java applet using Python?"
date: 2007-12-18
forum: Programming Talk
---

### Post by user1397 on 2007-12-18
There's this simple little Java applet game, called Soccer Slime, and its source code is here: [http://fractal.leet.net.au/download.php?target=files/wcss.zip](http://fractal.leet.net.au/download.php?target=files/wcss.zip)

Here's the actual game: [http://www.uwesu.net/dosserscorner/wcss/WorldCupSoccerSlime.html](http://www.uwesu.net/dosserscorner/wcss/WorldCupSoccerSlime.html)

I am wondering whether it is possible to recreate this game to the fullest extent, but written in Python and wxPython...

---

### Post by LaRoza on 2007-12-18
For embedding in a browser, you can't use Python, however, you could use Python and PyGame for it, it looks like a rather simple game to program.

---

### Post by user1397 on 2007-12-18
> **LaRoza said:**
> For embedding in a browser, you can't use Python, however, you could use Python and PyGame for it, it looks like a rather simple game to program.Ah yes, PyGame...I had forgotten about that.  So PyGame works also for embedding applets in web browsers? (with the <blockquote> and <applet> tags, like java applets?)

And yes, it indeed may look simple to program, though for me, it is an extremely daunting prospect...:(

---

### Post by LaRoza on 2007-12-18
> **ubuntuman001 said:**
> Ah yes, PyGame...I had forgotten about that.  So PyGame works also for embedding applets in web browsers? (with the <blockquote> and <applet> tags, like java applets?)

And yes, it indeed may look simple to program, though for me, it is an extremely daunting prospect...:(

No, I said you can't embed Python in a browser, but for a standalone game, Python and PyGame would work.

I have never made anything like it, so I am not saying it is "simple" as in "easy", just possible without any of the issues of people who want to program Doom as their first program.

---

### Post by Tuna-Fish on 2007-12-18
Actually, check out jython. It's a python interpreter that runs on java. You can probably run that in a java applet.

---

### Post by user1397 on 2007-12-19
> **LaRoza said:**
> No, I said you can't embed Python in a browser, but for a standalone game, Python and PyGame would work.

I have never made anything like it, so I am not saying it is "simple" as in "easy", just possible without any of the issues of people who want to program Doom as their first program.Ah, ok, thanks.

---

### Post by user1397 on 2007-12-19
> **Tuna-Fish said:**
> Actually, check out jython. It's a python interpreter that runs on java. You can probably run that in a java applet.though that does sound very interesting, I am not interested in learning java first and then python :) it's one step at a time for me!

---

### Post by pmasiar on 2007-12-19
> **ubuntuman001 said:**
> though that does sound very interesting, I am not interested in learning java first and then python :) it's one step at a time for me!

1) I am not sure if jython runs in applet - in fact, I doubt. But if anyone can try it, I would love to be proven wrong! :-)

2) You don't need to know any Java to run Jython. it is just implemented on top of Java/JVM. Python is implemented in C, but you don't need to know any C to run it either, right?

---

### Post by cwaldbieser on 2007-12-19
> **pmasiar said:**
> 1) I am not sure if jython runs in applet - in fact, I doubt. But if anyone can try it, I would love to be proven wrong! :-)


[http://www.jython.org/applets/index.html]("http://www.jython.org/applets/index.html")

---

### Post by pmasiar on 2007-12-20
Thats awesome, Jython is implemented as 200K java applet. Not bad! Thanks for the link!

---


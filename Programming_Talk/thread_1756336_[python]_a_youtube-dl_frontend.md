---
title: "[python] a youtube-dl frontend"
date: 2011-05-12
forum: Programming Talk
---

### Post by Riisen on 2011-05-12
hi
i am new to python and have written a simple gui for making mp3's from youtube videos with pygtk, i just have one annoying problem :P
and i cant get the progressbar to work.. any ideas?

well heres the code:
[http://spunk.neotor.se/python/youtube-dl-gui/test.py]("http://spunk.neotor.se/python/youtube-dl-gui/test.py")

---

### Post by An Sanct on 2011-05-12
I'll try to answer the progress bar question.

Take a look at this [Python package]("http://pypi.python.org/pypi/progressbar/2.2").

note: Try not to involve such content providers into your questions, since its a question about programming, but most answers/replies will be like "it is against the rules/"terms and conditions" of _____ to do that."

---

### Post by Riisen on 2011-05-12
> **An Sanct said:**
> I'll try to answer the progress bar question.

Take a look at this [Python package]("http://pypi.python.org/pypi/progressbar/2.2").

note: Try not to involve such content providers into your questions, since its a question about programming, but most answers/replies will be like "it is against the rules/"terms and conditions" of _____ to do that."

hi, thanks for answear but sorry if i wasn't to clear
the problem is that the main window doesnt uppdate while running a define,
so it looks like it freezes and then its done
is there a way to keep the __init__ updateing while running another define?
not sure how i should explain it...

thanks in advance

---

### Post by Zugzwang on 2011-05-12
> **Riisen said:**
> hi, thanks for answear but sorry if i wasn't to clear
the problem is that the main window doesnt uppdate while running a define,
so it looks like it freezes and then its done
is there a way to keep the __init__ updateing while running another define?
not sure how i should explain it...

thanks in advance

Look into threading. In a nutshell, you want to run your workload in a different thread in order to have the main thread free for the GUI business.

---

### Post by An Sanct on 2011-05-12
+1 Yes, have several threads assigned:

-1 "worker" thread (that does the download)
-1 GUI refresher/updater

---

### Post by Riisen on 2011-05-12
thanks i will look into threading :)
i will post how it goes when i've looked into it

---


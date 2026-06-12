---
title: "Python - Get keypress"
date: 2006-11-22
forum: Programming Talk
---

### Post by ironfistchamp on 2006-11-22
Hey all

Is there a built in function to get a key press rather than store the key and then test on its value. It would be so much easier for me (and users) to work on the key press rather than testing the value. Is this possible to do?

Thanks

Ironfistchamp

---

### Post by dwblas on 2006-11-22
Do you mean something other than hitting the Enter key afterwards, as in raw_input?

---

### Post by foxylad on 2006-11-23
This is one of the few things that is easier in VB (or any windows language) than in python, mainly because python has to work on any platform. The answer is the curses module, although you should google for some examples to see how it all hangs together. Unfortunately it is a lot more complex than a simple kbhit() function.

Cheers!
FoxyLad

---

### Post by ironfistchamp on 2006-11-23
Right it does appear that curses is the only real way to do it. That is a shame because PyCurses is very poorly documented :( 

I anyone has a decent indepth tutorial I would be very grateful

Thanks

Ironfistchamp

---

### Post by dwblas on 2006-11-23
Here is a link to how you could do it with Tkinter, which is included with Python.  This site has examples for a lot of programming languages.  Just click on Python above the black bar for a listing.
[http://www.faqts.com/knowledge_base/view.phtml/aid/3596/fid/264](http://www.faqts.com/knowledge_base/view.phtml/aid/3596/fid/264)

---

### Post by ironfistchamp on 2006-11-23
Thanks for the link. Is Tkinter not a GUI toolkit. I am looking to do this for a console application only. 

Thanks

Ironfistchamp

---


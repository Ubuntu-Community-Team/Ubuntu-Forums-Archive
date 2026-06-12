---
title: "Noobish question about gui toolkits"
date: 2011-01-02
forum: Programming Talk
---

### Post by CaptainMark on 2011-01-02
Im learning python and C at the same time, this might be a stupid question but i figure i should do my research before I get too far in, When making a gui would the coding for a specific gui toolkit be the same whichever language you use for a program.
Example: If ive made a program in python AND in C that gives exactly the same experience to the user and i want to give it a gui would the coding be the same for both programs or would it be completely different for each.
Im not sure ive explained myself very well, but hopefully you get what I mean, my aim is to be able to program in python and c using gtk for both, I was just trying to figure out how much of a workload ive given myself.
Thanks
Mark

---

### Post by worksofcraft on 2011-01-02
> **CaptainMark said:**
> Im learning python and C at the same time, this might be a stupid question but i figure i should do my research before I get too far in, When making a gui would the coding for a specific gui toolkit be the same whichever language you use for a program.
Example: If ive made a program in python AND in C that gives exactly the same experience to the user and i want to give it a gui would the coding be the same for both programs or would it be completely different for each.
Im not sure ive explained myself very well, but hopefully you get what I mean, my aim is to be able to program in python and c using gtk for both, I was just trying to figure out how much of a workload ive given myself.
Thanks
Mark

Python is an object oriented language and C is not.
In python you will be using PyGTK a set of advanced abstract and object oriented wrappers for the raw GTK interface you will be using in C. The two will be very different and a lot harder in C. It may be possible to bypass PyGTK and do it the hard way in both languages and that could be beneficiel for didactic purposes too :)

---

### Post by CaptainMark on 2011-01-02
Hmm, well ive done a lot more work on python i may just concentrate on that more for now.
What is the best way to learn GTK with Python then, the book uses tkinter which doesnt make for eye catching programs. Can you recommend any books or online guides for complete beginners to GUI programming?

EDIT: Its probably worth mentioning too im learning with Python3, I can only find good guides for python2 which i cant use

---

### Post by worksofcraft on 2011-01-02
> **CaptainMark said:**
> Hmm, well ive done a lot more work on python i may just concentrate on that more for now.
What is the best way to learn GTK with Python then, the book uses tkinter which doesnt make for eye catching programs. Can you recommend any books or online guides for complete beginners to GUI programming?

EDIT: Its probably worth mentioning too im learning with Python3, I can only find good guides for python2 which i cant use

Python, C, C++ and several other languages can all build the same  gui interfaces when they are defined with the glade interactive user interface designer. Sadly once again I don't think there are any tutorials for the new Python 3.x yet.

---


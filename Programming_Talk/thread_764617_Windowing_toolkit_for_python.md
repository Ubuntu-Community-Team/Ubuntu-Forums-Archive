---
title: "Windowing toolkit for python"
date: 2008-04-24
forum: Programming Talk
---

### Post by JamesUser on 2008-04-24
Hi,

I am new to python programming. I just started learning by making a small desktop app. I want to make GUI applications. I started with Tkinter but I see that it is quite limited, like it doesn't have widgets like status bar etc. I want my applications to look great and obviously work great on both linux and windows.

Should I choose pyGTK or wxPython? I hate having to familiarise myself with new api for every toolkit. Can you guys tell me which windowing toolkit you use with Python and why you use them?

Thanks.

---

### Post by luisromangz on 2008-04-24
Between pyGTK or wxPython, pyGTK; but the best toolkit avalaible is Qt (and its pyqt bindings in your case).

---

### Post by tseliot on 2008-04-24
I use both pyGTK and pyQT4.

I think you will find more tutorials on pyGTK on the web (with respect to the ones on pyQT4).

---

### Post by pmasiar on 2008-04-24
As a beginner, don't worry about GUI at first. Learn command-line programming, it is much simpler. See wiki in my sig for training tasks.

With GUI, you do not know the order how user will interact with form controls, so you have to handle events - and it is harder just plain ordered commandline input. 

If you really have to have GUI, get a really simple one: EasyGUI. No events, no problems! :-)

---

### Post by JamesUser on 2008-04-25
I am not new to programming. Am very comfortable wtih Core Java. The concept of event handling is not new to me either. Used to writing AWT listeners. So, am happy to learn something. It's just that I don't want to spend too much time learning the toolkit api. Nor do I want to learn another set of api as early as next month if my present choice becomes defunct.

I think I will go for pyGTK. Guess it will be around for some time to come and has a good collection of widgets. Thanks for all your replies.

---

### Post by CostaRica on 2008-06-04
PyGTK does not have a good grid for handling database-driven apps.  wxPython has maybe the best grid I have ever seen! Maybe PyGTK is more popular and with more tutorials, but with fewer widgets in that matter.  wxPython has a great book: "wxPython in Action".  Maybe one should consider the kind of apps one is going to develop.

---

### Post by MicahCarrick on 2008-06-04
My bias is towards GTK+ (PyGTK) for a multitude of reasons--but it's a moot point really.

Being that there are as many opinions to the debate over which toolkit is better to use as there are toolkits you can use, you will have to get a basic understanding of each of the main toolkits, weight the pros and cons, and dive in. Don't be afraid, you can learn another one later. Having experience with several will only make you a better developer.

What I recommend is to read the home page and the wikipedia article on each of the main toolkits you haven't tried (pyQt, pyGtk, and wxWidgets). Then think about what you are trying to achieve with your first project, and dive in to the toolkit that fits best. Don't be closed to trying a new toolkit later.

So, that's my opinion. Good luck and happy programming.

---


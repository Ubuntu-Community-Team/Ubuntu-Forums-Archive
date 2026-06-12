---
title: "[SOLVED] Python and QT4 Designer"
date: 2008-11-12
forum: Programming Talk
---

### Post by thornmastr on 2008-11-12
Hi,

I am looking for a tutorial teaching how to use QT4 Designer with Python. There are a number of very good tutorials for QT3, but I do not want to drop back from QT4.I have no problem designing the form(s) using QT4 designer; including signals and slots; but......I am not even certain why the form has to be saved as a .ui file rather  than a .frm file. I have no idea how to generate the python shells I can use to fill in the code for my defined events and the lack of a really good tutorial or two  is certainly placing me under a real handicap.

Any pointers, literally, to some tutorials would be most appreciated.



Thanks,

---

### Post by SabreWolfy on 2008-11-13
I'm also looking for this kind of a tutorial. I've spent much time trying to find a good IDE and toolkit designer for Python. There seem to be plenty of IDE programs, but fewer designers. I tried wxPython, but that requires writing the GUI code by hand. There is also wxGlade which I'm looking at. I have Eric and QT4 designer but have no idea how to use them or get them to work together. Is QT4 the best route to go? PyQt? wxPython? Tkinter?

---

### Post by snova on 2008-11-13
I am uncertain as to what the question is, but if it helps, know that you need to use pyuic4, which "compiles" UI files to Python code.

---

### Post by OutOfReach on 2008-11-13
It saves it as a .ui file, because Qt is available to a number of languages so it provides a universal format instead of just one language.

pyuic4 is most commonly used for converting .ui into .py, using it was explained in a book I was reading about Python + Qt4. But basically, you just run it in the directory containing the .ui files. (Note it also works for other Qt-related files such as .qrc resources files). I think pyuic is including with the PyQt packages.

---

### Post by thornmastr on 2008-11-13
These two replies were most helpful. I used pyuic4 to generate a .py file, however, I think this leads me to what I hope will give me the real answer to this quest. This generated file makes no mention at all of the Slots and Signals I am using. For instance, I have two buttons where I have defined a function to associate with each button. I have defined the function(s) as  slots. Now, what tool, if any, generates the python shell specifying all Slots and Signals in use. If I have to generate that file myself, is there any documentation outlining the process.

Thank you for all the assistance given to date.


Robert

---

### Post by OutOfReach on 2008-11-13
I am very positive that the signals and slots (defined in the designer) are automatically connected by the .py file that was generated.

---


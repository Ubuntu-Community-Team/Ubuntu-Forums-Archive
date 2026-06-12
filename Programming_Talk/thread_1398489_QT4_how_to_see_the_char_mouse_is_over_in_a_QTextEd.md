---
title: "QT4: how to see the char mouse is over in a QTextEdit or else make own text widget"
date: 2010-02-04
forum: Programming Talk
---

### Post by Zorgoth on 2010-02-04
I am trying to design a widget with the following functionality -

i need to be able to insert text (although usually it will be read-only), and upon toggling a particular mode I need to be able to accept a list of terms in the text from a QProcess (I am designing a GUI for a text-only ML program) (in the form of an integer representing the first character in the term and an integer representing the length of the term - in this case there is no overlap problem), highlight these terms, and then click on one to select it and perform an action (so basically the term simulates a simple button).

Unfortunately, I cannot figure out how to use a QTextEdit, QLabel, or any other text display widget I know of to identify a character based on a screen position in QT4, so I can't program in the "button" functionality to the text. Could someone ideally tell me how to do this or if it is impossible tell me how to design my own simple text display widget?

I am pretty new to QT so it is very likely I am missing something obvious.

---


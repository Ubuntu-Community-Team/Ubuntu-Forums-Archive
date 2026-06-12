---
title: "Syntax Highlighting in Swing"
date: 2008-04-10
forum: Programming Talk
---

### Post by DBQ on 2008-04-10
Hi everybody.

I am developing a program in Java Swing that uses a JTextArea which displays the syntax of  a very simple language which I designed.  It has only about 4 reserved words.  I would like to have syntax highlighting for those reserved words in the JTextArea.  Is there a solution for that?  I tried googling, but did not find anything concrete.  Any hints would be great.  Examples even better.

Once again all I am looking for is an ability to highlight a few reserved words.

---

### Post by heikaman on 2008-04-10
you will need to use a javax.swing.text.Highlighter object 
read this :

[http://exampledepot.com/egs/javax.swing.text/style_HiliteWords.html](http://exampledepot.com/egs/javax.swing.text/style_HiliteWords.html)

---


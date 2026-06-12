---
title: "QT4 designer newbie question"
date: 2009-08-25
forum: Programming Talk
---

### Post by Peter Frank on 2009-08-25
I have learned some manual QT coding, but I'm having problems with using the designer. In particular, I don't know how to add must own functions as slots.

For example, can someone show me step by step instructions on how to do the following simple task? A program which has two text boxes for the user to enter numbers, and an "Multiply" push button which will display the result a*b. I know how to do this when coding manually, but in the designer, I only know how to connect the default signals and slots using Drag 'n Drop. I don't know how to add my own function.

Thanks for help!

---

### Post by mart_k on 2009-08-25
Have you read [this](http://doc.trolltech.com/4.5/designer-using-a-ui-file.html) documentation? It explains how to use a .ui-file in your program.

Designer can only do simple connect of signals and slots. It cannot provide implementations of custom slots. So after you made your form, you let it generate the source files. You use that files to make a new class and you use the generated class there. In your new class, you can implement your custom slot.

---


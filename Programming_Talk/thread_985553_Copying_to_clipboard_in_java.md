---
title: "Copying to clipboard in java"
date: 2008-11-17
forum: Programming Talk
---

### Post by skipsbro on 2008-11-17
How can I copy a string in lava to the clipboard?

---

### Post by tinny on 2008-11-18
> **skipsbro said:**
> How can I copy a string in lava to the clipboard?

Have a look at the JDIC (Java Desktop Integration Components) project.

[https://jdic.dev.java.net/](https://jdic.dev.java.net/)

I believe they have some sort of API for this.

---

### Post by cl333r on 2008-11-18
If you don't wanna dig into the APIs:
JTextFied tf = new JTextField();
tf.setText( yourString );
tf.copy();

---

### Post by drubin on 2008-11-18
> **cl333r said:**
> If you don't wanna dig into the APIs:
JTextFied tf = new JTextField();
tf.setText( yourString );
tf.copy();

If that is in the standard java libs. Then you can definitely take a look at the JTextField/parents components and see how they do it and just implmeent that.

Quick google.
[http://www.javapractices.com/topic/TopicAction.do?Id=82](http://www.javapractices.com/topic/TopicAction.do?Id=82) 
[http://www.devx.com/Java/Article/22326](http://www.devx.com/Java/Article/22326)

---

### Post by tinny on 2008-11-18
> **cl333r said:**
> If you don't wanna dig into the APIs:
JTextFied tf = new JTextField();
tf.setText( yourString );
tf.copy();

Cool, that looks like what the OP wants.

Quote from the javadoc
> 
Transfers the currently selected range in the associated text model to the system clipboard, leaving the contents in the text model. The current selection remains intact. Does nothing for null selections. 


---

### Post by drubin on 2008-11-18
> **tinny said:**
> Cool, that looks like what the OP wants.

Quote from the javadoc

> Transfers the currently selected range in the associated text model to the system clipboard, leaving the contents in the text model. The current selection remains intact. Does nothing for null selections.

According to that quote you are going to have to select the text as well.
[Start]("http://www.docjar.com/docs/api/javax/swing/text/JTextComponent.html#setSelectionStart(int)") 
[End]("http://www.docjar.com/docs/api/javax/swing/text/JTextComponent.html#setSelectionEnd(int)")
> 
If you don't wanna dig into the APIs:
JTextFied tf = new JTextField();
tf.setText( yourString );
tf.copy();

Question: will this work with out the Component being displayed on the screen?

---


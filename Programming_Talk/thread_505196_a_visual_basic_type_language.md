---
title: "a visual basic type language?"
date: 2007-07-20
forum: Programming Talk
---

### Post by slavik on 2007-07-20
I started working on a perl script to take a .glade file from glade3 and generate a skeleton perl file which would have all the subroutines declared that are noted as signals in the .glade file.

I started thinking further and realised that with the power of perl's regex, it could be possible to define a very simple language that could then be translated to another language (that has libglade and gtk2 bindings)

basically, this is a code generation program. before on work on it more (I def will) I wanted to get opinions of people. eventually, it might be possible to add stuff to glade3 gui and turn it into some kind of a vb clone for linux.

---

### Post by ankursethi on 2007-07-20
You might want to check out Gambas if you want a VB clone. [http://gambas.sf.net](http://gambas.sf.net)

---

### Post by slavik on 2007-07-20
well, what I want to create is something much simpler than gambas (no interpreter, only a translator) ...

basically, I want to allow people to say something like this:
// label1 is a label widget ...
label1.text = "Hello World";

and then translate it into the proper language (since you first have to get the widget and everything).

---


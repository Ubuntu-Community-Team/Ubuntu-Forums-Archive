---
title: "PyQt creating widgets"
date: 2007-10-29
forum: Programming Talk
---

### Post by happysmileman on 2007-10-29
I'm using PyQt (well learning to use it) and the tutorial is inconsistent about creating the widgets as a member of the class... For example sometimes it uses:
```
self.textEdit = QtGui.QTextEdit()
```
and sometimes it uses
```
textEdit = QtGui.QTextEdit()
```

Anyone want to explain or link to a reason why you might use self? Is it something you eityher always or never do, is it personal preference or are there times when you'll need it and times you won't?

---

### Post by dataw0lf on 2007-10-29
'self' references the object instance.  You have to pass it to each method of a class, and to access / assign properties, you use 'self'.
So in one instance, textEdit is the property of the object, whilst in the other instance, it isn't (or is a class property).

---

### Post by happysmileman on 2007-10-29
> **dataw0lf said:**
> 'self' references the object instance.  You have to pass it to each method of a class, and to access / assign properties, you use 'self'.
So in one instance, textEdit is the property of the object, whilst in the other instance, it isn't (or is a class property).

I understand I think, but what exactly are the advantages/disadvantages or declaring a widget like this. I'm assuming for it to be referenced outside that function it needs to be made with "self.textEdit" but any other reasons?
And am I ONLY supposed to use it in those cases?

---

### Post by dataw0lf on 2007-10-29
Declaring a widget like this binds it to the class.  I've never used Qt, but generally you'd want your widgets to be part of a parent Window, Root, or whatever, subclass.

---

### Post by happysmileman on 2007-10-29
> **dataw0lf said:**
> Declaring a widget like this binds it to the class.  I've never used Qt, but generally you'd want your widgets to be part of a parent Window, Root, or whatever, subclass.

So you're saying that it's always better to use "self.textEdit" so that it's considered part of the class and can be accessed by other functions?

---


---
title: "Python attribute question"
date: 2010-03-23
forum: Programming Talk
---

### Post by Mordred on 2010-03-23
Hi,

I am doing some python development and need the following:

I would like to loop over the attributes of a class and print
the attribute name and value.

E.g. 

[PHP]class Example(object()):
  bool1 = True
  bool2 = False[/PHP]

Would yield:

[PHP]bool1 = True
bool2 = False
[/PHP]

on the prompt.

I need this to update the values of a model with the values entered in a form in django.

---

### Post by snova on 2010-03-23
> **Mordred said:**
> Hi,

I am doing some python development and need the following:

I would like to loop over the attributes of a class and print
the attribute name and value.

E.g. 

[PHP]class Example(object()):
  bool1 = True
  bool2 = False[/PHP]

Would yield:

[PHP]bool1 = True
bool2 = False
[/PHP]

on the prompt.

I need this to update the values of a model with the values entered in a form in django.

The simplest way to actually do it would probably be to iterate over **dir(your_object)** and filter out the attributes with underscores.

But that still leaves the question of *why* you would want to do it. This sounds like exactly the kind of thing you shouldn't be doing, more so if input comes from the web.

---

### Post by wmcbrine on 2010-03-23
You can find the attributes using dir(). This will also include a bunch of standard attributes that you don't care about, marked off with double underscores on each side of their names.

Edit: Ah, beaten to it.

---

### Post by Mordred on 2010-03-24
Hi,

using django's ModelForms instead.

Solved my problem.

Thanks for the replies!

---


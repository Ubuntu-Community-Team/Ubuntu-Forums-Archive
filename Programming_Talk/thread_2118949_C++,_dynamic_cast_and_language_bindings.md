---
title: "C++, dynamic_cast and language bindings"
date: 2013-02-22
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2013-02-22
This is more of a theoretical question that popped into my mind than an actual problem I am currently facing.

If I understand correctly, the use of dynamic_cast is this:
1. Have class B, which is derived from base class A.
2. Create a variable to B and instantiate it.
3. Create a variable to A and assign to it the value of variable created in the previous step. Let's name it X.
4. Try to dynamic_cast X to a type of class B and it succeeds.


But what happens when language bindings are involved? Does this still work and how? Take for example gtk and gtkmm. A Gtk::Button is a derived class of Gtk::Widget. I suppose if you did the above steps, dynamic_cast will suceed. But how?

If I understand language bindings correctly, gtkmm just wraps around the relevant gtk C functions and doesn't actually subclass the various classes. So how is this even possible?

---

### Post by GeneralZod on 2013-02-22
I just checked out the source for gtkmm and can confirm that Gtkmm::Button inherits from Gtkmm:Bin, as suggested [here](http://developer.gnome.org/gtkmm/3.6/classGtk_1_1Button.html#a188bfc5caf8e3c68d6d80b54186d8961) (inheriting from Gtkmm::Activatable is marked as TODO) - so based on this spot-check, it does in fact attempt to mirror the Gtk hierarchy using C++ inheritance.

---

### Post by SledgeHammer_999 on 2013-02-22
So just subclassing the wrapper-base class but continuing to also wrap the C gtk functions is sufficient for dynamic_cast to work?

---

### Post by trent.josephsen on 2013-02-22
As opposed to... what? The fact that gtkmm wraps C functions doesn't change how inheritance works. If it works for classes you created, why wouldn't it work for classes in libraries?

---


---
title: "Objective-C and GUIs"
date: 2006-09-21
forum: Programming Talk
---

### Post by coder_ on 2006-09-21
I've started to fool around in Obj-C and wanted to know if there are any other way to create GUIs for my applications than using Gorm and such.

I'm looking for another GUI toolkit such as Qt or a Gnome one with bindings for Objective-C.  Cacoa is dead and the homepage is gone.  Gtoolkit doesn't seem to work with 64 bit.  The Qt bindings apparently are dead, and I can't find Gnome bindings.

So any Objective-C coders out there who can give me a hint or so, that'd be very helpful. :o)  Thanks in advance.

---

### Post by Note360 on 2006-09-22
I think their may be a solution (I am thinking of learning Objective-C or Ruby soon)

Gnome-Obj-C
GTKKit
.That looks like your solution. I am looking for documentation

---

### Post by Daverz on 2006-09-22
> **Note360 said:**
> 
Gnome-Obj-C
GTKKit
.That looks like your solution. I am looking for documentation

Pretty sure those are dead.  Anything that hasn't been updated for gtk2 is very, very dead.  Which is sad, because ObjC and gtk2 would probably be a great match.

GNU SmallTalk comes with gtk bindings, but I think there's only one guy working on that, so progress is very slow.

More bindings here:

[http://gtk.org/bindings.html](http://gtk.org/bindings.html)

Though they aren't very good at updating that list, so you may have to google for more up to date info.

BTW, if your interested in Lisp bindings, you'll find a list at

[http://www.cliki.net/GTK%20binding](http://www.cliki.net/GTK%20binding)

---

### Post by Note360 on 2006-09-22
Where did lisp bindings come from?

---

### Post by Daverz on 2006-09-22
> **Note360 said:**
> Where did lisp bindings come from?

I just threw that in for shits and giggles.

---

### Post by skymt on 2006-09-22
Objective-C can call C functions, so your best bet is probably the plain old C API for GTK.

---

### Post by Note360 on 2006-09-23
the C API may work as skymt suggested. However, will you be able to use obj-c  code in the GUI if you where to do that?

Oh, I also kinda like lisp. Howvere, so sar I havent done ANY gui programming in any language. I am working on it. It is just that I am soooo interested in making cli applications. (at the moment)

---


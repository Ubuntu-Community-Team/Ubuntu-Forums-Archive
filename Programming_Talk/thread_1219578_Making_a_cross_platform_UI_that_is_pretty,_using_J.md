---
title: "Making a cross platform UI that is pretty, using Java"
date: 2009-07-21
forum: Programming Talk
---

### Post by phrostbyte on 2009-07-21
Is this possible? :D Long time since I've looked at Java.

Does Eclipse have a SWT visual designer?

---

### Post by juancarlospaco on 2009-07-21
Python can be cross-platform too :)
*random example:Bleachbit for Windows*

---

### Post by apoth on 2009-07-22
Turn on GTK look and feel if present?

---

### Post by kpkeerthi on 2009-07-22
> **phrostbyte said:**
> Is this possible? :D Long time since I've looked at Java.

yes. SWT is a better choice compared to Swing if you want to do Java way. 

> **phrostbyte said:**
> 
Does Eclipse have a SWT visual designer?

There is. [http://www.eclipse.org/vep/](http://www.eclipse.org/vep/) . But I haven't seen much progress in a long time.

[http://www.eclipse.org/swt/faq.php#guibuilder](http://www.eclipse.org/swt/faq.php#guibuilder)

---

### Post by apoth on 2009-07-22
I prefer Swing to SWT.

---

### Post by The Cog on 2009-07-22
This may be of interest:
[http://java-gnome.sourceforge.net/](http://java-gnome.sourceforge.net/)

---

### Post by kknd on 2009-07-22
If you don't mind the strange look and feel (the GTK one have a lot of glitches) of Swing (and it's huge memory usage), use Swing, as it comes with the JRE.

Else, you can try JavaGNOME (for GTK+) or QtJambi (for Qt).

---


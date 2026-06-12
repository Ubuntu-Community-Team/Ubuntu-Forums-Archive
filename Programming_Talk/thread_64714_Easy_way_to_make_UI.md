---
title: "Easy way to make UI?"
date: 2005-09-11
forum: Programming Talk
---

### Post by gflores on 2005-09-11
I was wondering if there are any WYSIWYG editors for making a nice UI, similar to that of Visual C++. With that program, it makes it very easy to create an nice looking application. The only one I've found is from QT. Is there one for the GTK look?

---

### Post by az on 2005-09-11
Glade?

---

### Post by Nightblade on 2005-09-12
[QUOTE=gflores]I was wondering if there are any WYSIWYG editors for making a nice UI, similar to that of Visual C++. With that program, it makes it very easy to create an nice looking application. The only one I've found is from QT. Is there one for the GTK look?[/QUOTE]
 Well you have to mean Glade.

---

### Post by DancingSun on 2005-09-12
Ditto.

---

### Post by gordyt on 2005-09-15
Thanks for the Glade recommendations.  I installed it today and was amazed at how easy it is to put together a functional and attractive using Glade.

--gordy

---

### Post by Daniel G. Taylor on 2005-09-15
There is also Gazpacho, another GUI designer for GTK+

It's written in Python and uses PyGTK.

[http://gazpacho.sicem.biz/](http://gazpacho.sicem.biz/)

---

### Post by jdong on 2005-09-15
I recommend Glade... It can be used from many many different languages, and is very portable...


Recently, I've been playing with Monodevelop and glade#, and it certainly brings SWF ease of #Develop/VS.NET to all platforms :)

---

### Post by Daniel G. Taylor on 2005-09-16
I should probably mention, Gazpacho outputs Glade XML files so it's essentially just a different interface for making the GUI (as compared to Glade itself); you still use libglade to load the GUI in your programs (or python-glade, glade#, etc).

---

### Post by Haegin on 2005-09-17
Is there a way to get glade to work with ruby so under the glade options where it says "Language: C  C++  Ada 95" you can also select ruby?

Thanks

---

### Post by Daniel G. Taylor on 2005-09-17
[QUOTE=Human Prototype]Is there a way to get glade to work with ruby so under the glade options where it says "Language: C  C++  Ada 95" you can also select ruby?

Thanks[/QUOTE]
 Those options are sort of old and you really don't need to worry about them anymore, since the  "right" way of doing things these days is to save the Glade XML file and load it using libglade instead of having Glade generate code to create all the controls. In ruby you just need to have ruby-gnome2 installed and you will be able to load Glade XML files:
[http://ruby-gnome2.sourceforge.jp/hiki.cgi?GladeXML](http://ruby-gnome2.sourceforge.jp/hiki.cgi?GladeXML)

After you open the Glade XML file you will want to connect to signals and start the main GTK+ loop and you should be set.

---


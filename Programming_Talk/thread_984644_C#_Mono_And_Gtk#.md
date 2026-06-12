---
title: "C# Mono And Gtk#"
date: 2008-11-16
forum: Programming Talk
---

### Post by davidcaiazzo on 2008-11-16
Does anyone know of any good tutorials for mono and Gtk#. I have searched google in a few different ways and can't seem to come across anything past Hello World. Right now I know how to connect buttons with actions but I don't really know much else. Like how to initiate the open/save dialogue and making my own widgets.

---

### Post by cabalas on 2008-11-16
Have you tried the tutorials at mono-project.com, they appear to have a range of tutorials. 

[http://www.mono-project.com/GtkSharpTutorials](http://www.mono-project.com/GtkSharpTutorials)

---

### Post by directhex on 2008-11-17
Create a Gtk.FileChooserDialog object, then Run() it.

The object's Filename (or Filenames) properties give you the selected filename(s). Fiddle other properties on the object to alter its behaviour.

---

### Post by davidcaiazzo on 2008-11-17
Thanks for the replies. I some more tuts on mono-project and am moving in the right direction. Thanks.

---


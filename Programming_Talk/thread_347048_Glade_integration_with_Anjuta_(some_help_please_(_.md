---
title: "Glade integration with Anjuta (some help please? :( )"
date: 2007-01-26
forum: Programming Talk
---

### Post by faraazs on 2007-01-26
I'm trying to integrate glade with anjuta. Following some instructions I found on the forum, I simply just installed everything (glade and anjuta) with synaptic. However, when I click new -> glade file in anjuta, it seems like nothing happens...I even tried to add it through the plugin manager thinking it might be there but its not...

am I doing something wrong? Any help for me please :). It will be most appreciated :).

---

### Post by lnostdal on 2007-01-26
just start glade by itself then generate xml-files (edit: they are xml-files but they end with .glade) and load them using the libglade api.

it's something that can be done very simple without any IDE getting in your way:
  [http://developer.gnome.org/doc/API/2.0/libglade/libglade-notes.html#libglade-basics](http://developer.gnome.org/doc/API/2.0/libglade/libglade-notes.html#libglade-basics)

my recommendation in general? use anjuta (or any editor really) as an editor _only_ and use things like scons to manage the build-process -- it's usually way simpler and stays out of your way.. also call the build-script/scons as an external process from the editor instead of having the editor generate/handle these things for you automatically 

edit:
here's how i do this using SWGtk ("home made") with Lisp btw. (this has nothing to do with your question but i feel like posting it for fun as i've been at this for a couple of hours now):
```

(withSWGtk
  (let ((xml (make-instance 'XML :filename "/home/lars/programming/lisp/swgtk/tests/glade.glade"))) 
    (getWidget "button1" xml :clicked-event (iambda (write-line "Hello World")))
    (getWidget "window1" xml :title "blah"))))

```

..as soon as i press enter at the last closing parenthesis a window pops up with a button in it, just as it looked when i designed it in glade ..  clicking the button prints "Hello World" in the REPL .. pretty cool and simple :)

---

### Post by faraazs on 2007-01-26
Alright, I'll try to do it that way instead...

I have another error which I am not sure about though. When I build C files, I think it works fine but when building a C++ project, I get this error:```
Error running glade-- to generate the C++ source code.
Check that you have glade-- installed and that it is in your PATH.
Then try running 'glade-- <project_file.glade>' in a terminal.
```

---

### Post by lnostdal on 2007-01-26
> **faraazs said:**
> Alright, I'll try to do it that way instead...

I have another error which I am not sure about though. When I build C files, I think it works fine but when building a C++ project, I get this error:```
Error running glade-- to generate the C++ source code.
Check that you have glade-- installed and that it is in your PATH.
Then try running 'glade-- <project_file.glade>' in a terminal.
```

don't bother with the generated code; just load the .glade file as shown in the example i linked to 

generating code from glade has been deprecated for some time

---


---
title: "What are APIs?"
date: 2005-12-31
forum: Programming Talk
---

### Post by harisund on 2005-12-31
And how do I use them? 

These days, wherever I go there seem to be APIs... Google has hundreds.. XML-RPC seems to be the rage.. 

And what does it mean "binding in" a certain language? 

Let's say I want to create a GTK based app using Glade.. now GTK is written in C.. what if i need to write C++ code, since I am more familiar with that? Any other language? 

I have some experience with both languages like C++ and web based languages like Javascript, PHP and stuff.. so how do I make a start? 

Thanks ! There are some interesting projects on Freshmeat and Sourceforge, but I really needed some help to start out on them..

---

### Post by coredump on 2005-12-31
API stands for Application Programming Interface.  It's shorthand for the set of function calls that an application can make on a library or operating system.  For instance, in C, there's an API for opening, reading/writing and closing files: fopen, fread, fwrite, fclose.  That API is defined in the C Standard Library.

The idea of "binding" in a certain language refers to the idea that a given set of APIs in, say, C might not work well in, say, BASIC.  You'd want a slightly different way to access string variables, perhaps, or maybe the sizes of the integer parameter might need changing slightly.  Anyway, that's where the binding comes in; you'd have a set of functions that work well in C, another (perhaps for object-oriented) set for C++, andother set for Ada, and so on.  Same library, same overall capabilites, but differences in the details of how the functions appear in each language.

---

### Post by LordHunter317 on 2005-12-31
Not quite correct.

An API is, more simply, the interface used to access some library or interact with another piece of code.  Traditionally, this would have been a set of library functions that you called.  These days, with things like XML-RPC and SOAP being common place, an API may take a different form.  It's not strictly limited to a set of functions (or even classes) anymore, *per se*, although that's the most common form.

A language binding refers to your ability to access an API in more than one language.  For example, wxwidgets can be programmed in C, C++, Python, and many other languages.  The API provides identical functionality in each language.  The binding refers to what language you're using the API in.  Many modern libraries are accessible in multiple languages.

---

### Post by guice on 2005-12-31
> An API is, more simply, the interface used to access some library or interact with another piece of code.
/nod, as simple as that.

---

### Post by tageiru on 2006-01-01
[QUOTE=harisund]Let's say I want to create a GTK based app using Glade.. now GTK is written in C.. what if i need to write C++ code, since I am more familiar with that? Any other language?[/QUOTE]
Then you would use gtkmm which is gtk for c++. Gtk has bindings for several languages; c++, c-sharp, java, python...

Glade is language neutral. You just load the glade xml file in to your application at runtime. There is extensive documentation at the Glade site.

---

### Post by harisund on 2006-01-02
thanks ! That clears up a few things I had in mind ..

---


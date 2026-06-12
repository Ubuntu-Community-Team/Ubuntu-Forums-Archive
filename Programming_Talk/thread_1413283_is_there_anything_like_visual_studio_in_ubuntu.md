---
title: "is there anything like visual studio in ubuntu ???"
date: 2010-02-22
forum: Programming Talk
---

### Post by nos09 on 2010-02-22
is there anything like visual studo in ubuntu and if there is the what are the feathers they provide..
i m new to this programming business.. so use more understandable language * ( for now  :P )

---

### Post by fallenshadow on 2010-02-22
Maybe take a look at:

> [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

and

[http://monodevelop.com/](http://monodevelop.com/)


I think you can program with Visual Basic using Mono and with Monodevelop you can drag and drop to design your GUI.

---

### Post by Simian Man on 2010-02-22
For C# or Visual Basic, use MonoDevelop.  Though I'd really not suggest using Visual Basic at all.  It's not very well-supported and has nothing that C# doesn't have.

For C++, you have many more options.  I like Eclipse for a C++ IDE, but there are many others as well.

---

### Post by e24ohm on 2010-02-22
If you C++, you might want to look at Qt; however, the Mono Project previouslly recommended is yoiur only choice for C#, and VB.

J

---

### Post by leg on 2010-02-22
I have always found codeblocks to be a perfectly good IDE to use.

---

### Post by matmatmat on 2010-02-22
qt-creator includes a ui designer.

---

### Post by Tibuda on 2010-02-22
Ajunta
Eclipse
NetBeans
MonoDevelop
Code::Blocks

---

### Post by matthew.ball on 2010-02-22
I think when one asks for a Visual Studio-like IDE they're essentially asking for a GUI-Designer.

I have found in GNU/Linux things are slightly different to how they're done in Windows - I believe it's perhaps a side-effect of the Unix philosophy "create one application that does its job *very* well".

So you'll tend to get separate applications for creating a GUI, and then a different application for writing code. This isn't actually a bad thing, and in the end almost gives you an advantage, in that you're free to use what accommodates your style of programming.

An example of a separate GUI-Designer and an IDE is Glade and perhaps Anjuta (though, I have seen that Anjuta now includes a Glade-plugin feature). You design your GUI with Glade, and then write your code (and compile) with Anjuta.

There are a few different GUI-Designers available, and quite a few different IDEs available, I will try and provide a short list in what follows (a few of these have already been mentioned):

GUI-Designer:
**Glade** - [http://glade.gnome.org/](http://glade.gnome.org/) - this is a designer for the GTK+ framework. If you're interested in building applications for GNOME, this would be a good place to look.
**wxGlade** - [http://wxglade.sourceforge.net/](http://wxglade.sourceforge.net/) - this is a designer for the wxPython framework. This provides a very nice cross-platform "native" look to your applications.
**wxFormBuilder** - [http://wxformbuilder.org/](http://wxformbuilder.org/) - this is a designer for the wxWidgets framework (essentially the same as above). The differences between these two are largely subjective - in my opinion I have found wxFormBuilder to be a bit more mature than wxGlade, and thus offers to do more. wxFormBuilder generates C++ code, while wxGlade generates Python code, this could be an important distinction depending on your level of experience and what you're interested in programming.

Development Environment:
**Anjuta** - [http://www.anjuta.org/](http://www.anjuta.org/) - A fairly mature IDE for the C-family of languages. In my brief playing around with this, I found it able to do anything I was looking for - though this could be different for others.
**Code::Blocks** - [http://www.codeblocks.org/](http://www.codeblocks.org/) - A cross-platform IDE written with the aforementioned wxWidgets framework. Just as above, there is not much this doesn't offer.

GUI-Designer & Development Environment:
**QtCreator** - [http://qt.nokia.com/products/developer-tools](http://qt.nokia.com/products/developer-tools) - An incredibly well-featured modern C++ environment. This seems to offer everything Visual Studio offers, I haven't had any experience with it, but it's common to find people raving about how good it is.
**MonoDevelop** - [http://monodevelop.com/](http://monodevelop.com/) - An IDE designed primarily for C# (though I believe it supports other languages too). I haven't had much experience with this IDE, but the short time I have played around with some code I was able to make exactly the applications I was after in a short time, pretty powerful and complete tool-set.
**Gambas** - [http://gambasrad.org/](http://gambasrad.org/) - An environment for rapid application development, similar in some respects to Microsoft's Visual Basic - but don't take that analogy too far, it's still quite different. I don't have any experience with it, but I have heard a bit of talk about it and figured it may be interesting.

Please note that I haven't listed any of the [many] available Java IDEs - I have no experience with Java at all, and to recommend it would be wrong on my part considering - if you are interested in Java, there has been a few IDEs listed above. Most of them are going to be available for both Windows and GNU/Linux and in that respect I would guess most come with a GUI-Designer of some sort.

There are a few other more "obscure" development environments available - perhaps people would call them text-editors++ - such as **Vim** or **Emacs** (re: [http://www.vim.org/](http://www.vim.org/) and [http://www.gnu.org/software/emacs/](http://www.gnu.org/software/emacs/) respectively) these are usually used in a terminal (though Emacs has an X version, I've not used it so I won't comment on it) - but don't let that fool you, they are quite capable. The issue here is the learning curve for using either application is really quite large - unless you're very motivated they will come across as rather esoteric. That said, it's probably important for a GNU/Linux developer to learn one of these editors, simply based on the fact who knows if you'll ever have to do work in the terminal.

Just from me personally: if I'm going to make a GUI-application, I would use Emacs and wxFormBuilder.

---

### Post by Simon17 on 2010-02-22
No.

Don't get me wrong. Linux has plenty of good IDEs, but none of them are one tenth of what Visual Studio is.

---

### Post by SKLP on 2010-02-23
I would say MonoDevelop. It is similar to VS (it even uses the same .sln file format), I think it's the only IDE on linux that offers "proper" code completion(like VS), in the sense that it can automatically pop up early (i.e. before "."), and that it can complete on punctuation.
Moreover, it offers an integrated GUI designer for Gtk# (think VS Windows Forms designer, but for linux-native UI). 
Sadly, Mono in Ubuntu is not version 2.6 yet and so it lacks the Mono "Soft debugger", which is pretty much needed to get a reliable debugger in MonoDevelop.

---


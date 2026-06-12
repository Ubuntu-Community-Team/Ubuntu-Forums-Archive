---
title: "Non-interpreted language?"
date: 2008-03-06
forum: Programming Talk
---

### Post by microfi on 2008-03-06
Hi folks!
I'm new to programming in Linux (in Windows I used to make apps in Delphi), and I've been seeking the programming languages available. I found MonoDevelop, Eclipse, Anjuta, Lazarus and Python, QT4. The thing it is, most of them are interpreted: Mono is .NET, Eclipse makes JAR files, Python is that too... This idea is a bit odd for me. For instance, if I compile an EXE with Delphi, I'll be able to run it in any computer running Windows, with no need to download an interpreter or "virtual machine". It seems that the interpreted app is not solid, or even well-compiled...
The remaining IDEs (Anjuta, Lazarus and QT4) presented their disadvantages:
- I wasn't able to deal with the integrated Glade in Anjuta;
- Lazarus does not support GTK2 and it's crashy; also it generates giant binaries;
(I haven't tried QT4 at all yet).
So, is there any IDE I can try? In which programs do you make things like Banshee, GIMP, etc..?

Thanks, Filipe

---

### Post by slavik on 2008-03-06
you do not need to use the built in glade in anjuta ... it is there as more of a convenience thing. :)

---

### Post by microfi on 2008-03-06
Thanks!
But will Anjuta make Linux-native applications? I don't know if it sounds a little odd, but I was used to the EXEs from Windows that run on every machine, with no need of interpreters...:)

---

### Post by LaRoza on 2008-03-06
> **microfi said:**
> Thanks!
But will Anjuta make Linux-native applications? I don't know if it sounds a little odd, but I was used to the EXEs from Windows that run on every machine, with no need of interpreters...:)

IDE's aren't compilers.

EXE's from Windows won't run on every machine. (Try it on a Mac or Linux...)

What language are you looking at?

Languages that are normally compiled are: C, C++, D, Objective-C, Fortran, Ada, etc.

---

### Post by LaRoza on 2008-03-06
> **microfi said:**
> Hi folks!
I'm new to programming in Linux (in Windows I used to make apps in Delphi), and I've been seeking the programming languages available. I found MonoDevelop, Eclipse, Anjuta, Lazarus and Python, QT4. The thing it is, most of them are interpreted: Mono is .NET, Eclipse makes JAR files, Python is that too... This idea is a bit odd for me. For instance, if I compile an EXE with Delphi, I'll be able to run it in any computer running Windows, with no need to download an interpreter or "virtual machine". It seems that the interpreted app is not solid, or even well-compiled...
The remaining IDEs (Anjuta, Lazarus and QT4) presented their disadvantages:
- I wasn't able to deal with the integrated Glade in Anjuta;
- Lazarus does not support GTK2 and it's crashy; also it generates giant binaries;
(I haven't tried QT4 at all yet).
So, is there any IDE I can try? In which programs do you make things like Banshee, GIMP, etc..?


MonoDevelop, Eclipse, Anjuta, Lazarus and Python, QT4 are a mix of tools. You have IDE's, a language, and a GUI toolkit all thrown in together.

What exactly are you looking for?

<edit>

It seems you are used to a locked in language, that is closely associated with an IDE. There are no widely used languages on Linux like that. Languages are not tied to any tools in the free world. So, you have to pick a language, then find a tool you like.

I listed languages that are normally compiled earlier, and I suggest you look into those.

If you need resources in learning, see my wiki.

---

### Post by WW on 2008-03-06
In your question, you seem to be intermingling several related but distinct concepts.

An IDE is not necessarily restricted to a single language, and many of the common languages have multiples IDEs available that support them.  For example, if you want to write code in C++ (a compiled language), there are many IDEs you can use: Anjuta, KDevelop, Eclipse+CDT, Code::Blocks, NetBeans, etc.  And an IDE such as Eclipse can be used for Java, C++, Python, and probably other languages.

QT4 and GTK+ are GUI libraries, not languages. (And there are others, e.g. FLTK.) "Wrappers" are available that allow you to use these libraries in many different languages.  For example, GTK+ is available in Python via the pygtk module, and in C++ with the gtkmm library.

A programmer creating a GUI program has many choices to make (more than the traditional Windows programmer): What language to use?  What GUI library to use? What IDE (if any) to use?

You want a compiled language; I recommend C++. (But I don't know anything about Lazarus; it could be good, too.)  For a GUI library, you'll probably want to do some research to figure out which one you prefer.  (A multi-platform GUI package to consider is wxWidgets.)

Finally you can pick an IDE; which one seems to be a highly personal decision.


EDIT:  I guess I could have just said "I agree with LaRoza!" :)

---

### Post by t3hi3x on 2008-03-06
> **WW said:**
> In your question, you seem to be intermingling several related but distinct concepts.

An IDE is not necessarily restricted to a single language, and many of the common languages have multiples IDEs available that support them.  For example, if you want to write code in C++ (a compiled language), there are many IDEs you can use: Anjuta, KDevelop, Eclipse+CDT, Code::Blocks, NetBeans, etc.  And an IDE such as Eclipse can be used for Java, C++, Python, and probably other languages.

QT4 and GTK+ are GUI libraries, not languages. (And there are others, e.g. FLTK.) "Wrappers" are available that allow you to use these libraries in many different languages.  For example, GTK+ is available in Python via the pygtk module, and in C++ with the gtkmm library.

A programmer creating a GUI program has many choices to make (more than the traditional Windows programmer): What language to use?  What GUI library to use? What IDE (if any) to use?

You want a compiled language; I recommend C++. (But I don't know anything about Lazarus; it could be good, too.)  For a GUI library, you'll probably want to do some research to figure out which one you prefer.  (A multi-platform GUI package to consider is wxWidgets.)

Finally you can pick an IDE; which one seems to be a highly personal decision.


EDIT:  I guess I could have just said "I agree with LaRoza!" :)

Well said. The only thing I would add, is don't be afraid of interpreted languages with Linux. They aren't like Java: they actually work well, and they are rather easy. If you're coming from window$ and want to get into programming, I would suggest jumping into python or perl - even though they are interpreted. And since the "VMs" are almost always a part of the system, then potability isn't a huge issue. Unless you want super efficient and super potability, in that case C/C++ is your best option and make sure you use portable libraries.

---

### Post by pmasiar on 2008-03-06
If your concern is that with interpreted language you need to provide runtime, don't worry. Most linuxes include 'runtime' for Perl, Python out-of-the-box.

If your concern is IDE, there are many decent IDEs for most languages, but gurus often use universal super-editor like vim or emacs, bacause if you edit daily code many langugaes, single powerful customizable editor is preferable (they say) to bunch of different IDEs and other editors.

---

### Post by lnostdal on 2008-03-06
write your application first, then worry about deployment later ...

if you haven't figured out how to deploy your application by the time your application is written come back here and ask "how do i deploy my xxxx-application written in xxxxx-language?"

---

### Post by microfi on 2008-03-07
Thanks very much!!
I'll take a look on the languages you said and I'll find the one that satisfies me...
Regards, Filipe

---

### Post by Fbot1 on 2008-03-09
> **microfi said:**
> 
- Lazarus does not support GTK2 and it's crashy; also it generates giant binaries;

[http://wiki.freepascal.org/Size_Matters#Rule_of_thumb.2C_what_are_current_realistic_sizes_for_Free_Pascal.2FLazarus_binaries.3F](http://wiki.freepascal.org/Size_Matters#Rule_of_thumb.2C_what_are_current_realistic_sizes_for_Free_Pascal.2FLazarus_binaries.3F)

Also, it supports most of Gtk2.

---


---
title: "Ubuntu Programming, where do I start?"
date: 2009-09-01
forum: Programming Talk
---

### Post by MetaDark on 2009-09-01
I want to learn how to make Ubuntu applications. I am already familiar with creating Windows applications and I really prefer to make the visual part of the application with a GUI programming application. I am most fimiliar with C# but I don't think there is a way to create a C# project without making it an executable application.

I am also a bit familiar with C++ and I am pretty sure Ubuntu Applications can use C++. What GUI programming application would you suggest I use?

---

### Post by falconindy on 2009-09-01
Creating graphical applications for Ubuntu can be done in a variety of languages -- C++, Python, Ruby, Java, PHP and Perl are the popular options. the trick is sourcing the proper graphical library to create and manage your windows. However, this will tie your application to a particular desktop environment. Gnome uses GTK, and KDE Uses Qt. I'm not familiar with the libraries used for other environments.

---

### Post by paradigm2 on 2009-09-01
Really I think the best thing to do is find an open source project and start trying to help with minor bug fixes and such (After studying the code).  You'll usually have to learn to grab the development tree and they will also list a suggested development environment.  That's the best way to learn, not from a book.  Just jump in. :)

---

### Post by sloggerkhan on 2009-09-01
For you, try mono or python. There are a number of windowing toolkits/bindings for python and it's an easy to use/learn language. Mono is basically c#, so it should be pretty easy for you, too.

---

### Post by credobyte on 2009-09-01
All I can say is, learn Java ( tough, I've stopped learning it due to an insane lack of time :( ).

---

### Post by Bachstelze on 2009-09-01
Moved to Programming Talk.

---

### Post by MetaDark on 2009-09-01
I agree paradigm2. Do you know were I can find open source C++ projects that I can help out with?[]("http://ubuntuforums.org/member.php?u=802173")

---

### Post by haTem on 2009-09-02
In addition to language choice, you'll have to choose a toolkit. If you're a Gnome/Ubuntu person, go the gtk route. If you prefer KDE/Kubuntu, go for qt4.

Gtk has both C# and C++ bindings.
[LIST]
[*] C#: [http://www.mono-project.com/GtkSharp](http://www.mono-project.com/GtkSharp)
[*] C++: [http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html)
[/LIST]

As for existing applications you can help out with: 
[LIST]
[*] Mono/C#: Tomboy Notes, Gnome Do 
[*] C++: inkscape, gparted, gnome-system-monitor
[/LIST]

GUI Programming Tools
[LIST]
[*] Mono/C#: MonoDevelop
[*] C++: Glade (the ui designer for gtk) in conjunction with your favorite IDE, or if you prefer, you can try anjuta (it integrates glade so that everything is in one application).
[/LIST]

As for Qt,
[LIST]
[*] C++: [http://zetcode.com/tutorials/qt4tutorial/firstprograms/](http://zetcode.com/tutorials/qt4tutorial/firstprograms/)
[*] C#: I don't think its C# bindings are mature yet
[/LIST]

Existing applications you can help out with:
[LIST]
[*] Pretty much any KDE application.
[/LIST]

GUI Programming Tools
[LIST]
[*] Qt Creator (personal note: this is the best IDE I have ever used!)
[*] KDevelop
[/LIST]

Good luck!

---

### Post by directhex on 2009-09-02
> **MetaDark said:**
> I want to learn how to make Ubuntu applications. I am already familiar with creating Windows applications and I really prefer to make the visual part of the application with a GUI programming application. I am most fimiliar with C# but I don't think there is a way to create a C# project without making it an executable application.

I am also a bit familiar with C++ and I am pretty sure Ubuntu Applications can use C++. What GUI programming application would you suggest I use?

Why not fire up MonoDevelop and create a new GTK# project? It has a GUI designer and a full C# 3.0 compiler...

---

### Post by MetaDark on 2009-09-02
Well MonoDevelop compiles into exe's and wine doesn't know if it's a Windows application or MonoDevelop application, which also reminds me of another question. What is the Ubuntu Equivlent of exe files?

---

### Post by Tibuda on 2009-09-02
ELF files, but they usually don't have extensions. Mono binaries have the EXE extension.

---

### Post by MetaDark on 2009-09-02
I finally figured out how to run those exe's I made using MonoDevelop, I can't believe all I had to do was create a launcher to my application.

It's weird how it doesn't load when you just do the double click.

Thanks guys for your help :D

---

### Post by directhex on 2009-09-03
> **MetaDark said:**
> I finally figured out how to run those exe's I made using MonoDevelop, I can't believe all I had to do was create a launcher to my application.

It's weird how it doesn't load when you just do the double click.

Thanks guys for your help :D

That's a GNOME problem.

If you try to execute it directly in a terminal (i.e. with ./foo.exe) then the kernel knows what to do, thanks to a system called binfmt ([binfmt-support](apt:binfmt-support) package) - if it's a managed app, Mono will be used to run it. If it's a Wine app, Wine will be used to run it. You can get the same thing from running .jar files (Java archives) directly

---

### Post by MetaDark on 2010-09-02
This is kind of an old thread but, do you guys know any good GUI IDE's for GTK on C++, all I found was Netbeans and that is for Qt.

Edit: I think I heard of something called Eclipse, I will go check it out.

---

### Post by ibuclaw on 2010-09-02
The only other two I can add to your list is Geany and Vim.

---

### Post by hakermania on 2010-09-02
Use QT4. the best

---

### Post by GenBattle on 2010-09-02
GUI editors for GTK and the like generally aren't integrated directly into IDEs, Monodevelop is the exception. I believe eclipse has a plugin for GTK interface generation.

---


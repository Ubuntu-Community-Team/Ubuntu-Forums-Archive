---
title: "C tutorials?"
date: 2009-05-12
forum: Programming Talk
---

### Post by frustphil on 2009-05-12
Hi.. anyone know of a C GUI programming tutorial? Preferably a CLI one...?

---

### Post by ajackson on 2009-05-12
> **frustphil said:**
> Hi.. anyone know of a C GUI programming tutorial? Preferably a CLI one...?

[This]("http://lambdagrok.wikidot.com/learn:c") site has a lot of links to various C tutorials, articles, etc. Don't know if any of them contain GUI stuff but it's worth a look.

---

### Post by samjh on 2009-05-12
> **frustphil said:**
> Hi.. anyone know of a C GUI programming tutorial? Preferably a CLI one...?

CLI GUI?  You'd be looking at the ncurses library.

```
sudo apt-get install ncurses-dev
```

Comprehensive tutorial: [http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/)

---

### Post by ajackson on 2009-05-12
> **samjh said:**
> CLI GUI?  You'd be looking at the ncurses library.
I might be wrong but I took it as meaning a tutorial for GUI that you didn't need an IDE for (i.e. told you what commands to type at the CLI to compile, link, run, etc).

---

### Post by frustphil on 2009-05-12
> **ajackson said:**
> I might be wrong but I took it as meaning a tutorial for GUI that you didn't need an IDE for (i.e. told you what commands to type at the CLI to compile, link, run, etc).

Exactly... I'd like to learn C. I know the basic syntax already. Now I'd like to take it to another level, GUI programming. I'll look into the site you suggested. Thanks.

---

### Post by frustphil on 2009-05-12
> **samjh said:**
> CLI GUI?  You'd be looking at the ncurses library.

```
sudo apt-get install ncurses-dev
```Comprehensive tutorial: [http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/)

Looks like this is what I am looking for... 
A couple of questions though.. How does ncurses differ from gtk+? Can it be ran on a Windows environment?

---

### Post by samjh on 2009-05-12
I thought you meant text-mode GUI (ie. a GUI that runs in terminal).

Ncurses is used for making GUI for text consoles (eg. [Midnight Commander]("http://en.wikipedia.org/wiki/GNU_Midnight_Commander"), [w3m]("http://en.wikipedia.org/wiki/W3m"), [aptitude]("http://en.wikipedia.org/wiki/Aptitude_(program)")).  GTK+ is a graphical toolkit for the X windowing system.

---

### Post by frustphil on 2009-05-12
> **samjh said:**
> GTK+ is a graphical toolkit for the X windowing system.
This is what I'd like to learn. Any way I can code gtk+ through CLI? Or are there any IDEs which only have the basic features that I can use? Is gtk+ the standard GUI toolkit for C? 

P.S Sorry if I might have used wrong terms as I am totally new to programming...

---

### Post by cabalas on 2009-05-12
> **frustphil said:**
> This is what I'd like to learn. Any way I can code gtk+ through CLI? Or are there any IDEs which only have the basic features that I can use? Is gtk+ the standard GUI toolkit for C? 

P.S Sorry if I might have used wrong terms as I am totally new to programming...

There is no standard GUI toolkit for C.  However Gtk+ is the standard UI toolkit for gnome. The official Gtk tutorial can be found here [http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/) if I remember correctly it assumes that you are compiling everything from the command line.

---

### Post by shababhsiddique on 2009-05-13
> **frustphil said:**
> Hi.. anyone know of a C GUI programming tutorial? Preferably a CLI one...?
I am getting confused! CLI ?? :confused:

---

### Post by ajackson on 2009-05-13
> **shababhsiddique said:**
> I am getting confused! CLI ?? :confused:
Command Line Interface or via a terminal in even simpler speech.

---

### Post by adredz on 2009-05-13
[...deleted...]

---

### Post by frustphil on 2009-05-13
> **shababhsiddique said:**
> I am getting confused! CLI ?? :confused:

Sorry, I should have said programming from the console or with an IDE that does not support drag and drop feature.

---

### Post by frustphil on 2009-05-13
> **cabalas said:**
> There is no standard GUI toolkit for C.  However Gtk+ is the standard UI toolkit for gnome. The official Gtk tutorial can be found here [http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/) if I remember correctly it assumes that you are compiling everything from the command line.

Thanks!:)

---


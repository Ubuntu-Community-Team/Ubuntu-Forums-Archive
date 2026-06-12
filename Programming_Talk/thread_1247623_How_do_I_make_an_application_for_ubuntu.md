---
title: "How do I make an application for ubuntu?"
date: 2009-08-23
forum: Programming Talk
---

### Post by Sashin on 2009-08-23
Is there an equivalent to visual basic that'll make programs for a gnome desktop?

If not is there a guide to do this from scratch?

---

### Post by BackwardsDown on 2009-08-23
It seems that you don't know about programming, so if you want to create programs you should start learning how to program. My personal favorite is the programming language python but we have a programming-subforum here :)

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

There is also a sticky with the name "Read Before Posting: Forum FAQ's, how to learn to program, and Linux programming"

Good luck!

---

### Post by Sashin on 2009-08-23
Well I'm learning python actually, but is it possible to use it in conjunction with a GUI?

---

### Post by BackwardsDown on 2009-08-23
Offcourse, you can use PyGTK for that. 

[http://pygtk.org/](http://pygtk.org/)

---

### Post by Sashin on 2009-08-23
Apparently ubuntu already comes with it. but typing pygtk in terminal doesn't run it how do I use it?

---

### Post by BackwardsDown on 2009-08-23
Here is a tutorial on how to use it:

[http://pygtk.org/pygtk2tutorial/ch-GettingStarted.html](http://pygtk.org/pygtk2tutorial/ch-GettingStarted.html)

---

### Post by Nevon on 2009-08-23
> **Sashin said:**
> Apparently ubuntu already comes with it. but typing pygtk in terminal doesn't run it how do I use it?

PyGTK is not a program per se, but rather bindings for the Gimp Toolkit (GTK). You use it from within your Python applications. However, you should definitely learn to do command-line driven applications before attempting to make an application with a graphical user interface - as that is a fairly advanced topic.

---

### Post by armageddon08 on 2009-08-23
Can GTK be used to create GUI for java apps?

---

### Post by Nevon on 2009-08-23
> **armageddon08 said:**
> Can GTK be used to create GUI for java apps?

Seems so. [https://launchpad.net/java-gnome](https://launchpad.net/java-gnome)

---

### Post by armageddon08 on 2009-08-23
> **Nevon said:**
> Seems so. [https://launchpad.net/java-gnome](https://launchpad.net/java-gnome)

Wow! That's encouraging.

---

### Post by lovinglinux on 2009-08-23
I'm having a lot of fun developing Firefox extensions. The graphical part is pretty easy with [XUL](http://en.wikipedia.org/wiki/XUL) (XML User Interface Language) and most of the coding is done with javascript. Nevertheless, you can launch bash and python scripts from it, among other things.

I have started the development of my first extension, called FoxMediaCenter, 8 months ago and it has evolved a lot since then. Take a look at the [extension page on Mozilla web site](https://addons.mozilla.org/en-US/firefox/addon/10991) or the [extension official web site]("http://fmc.isgreat.org").

If you don't want to create an extension for Firefox, you can use the same languages and API to create [XULRunner](http://en.wikipedia.org/wiki/XULRunner) standalone applications.

**More info:**

Extensions - [https://developer.mozilla.org/En/Developing_add-ons](https://developer.mozilla.org/En/Developing_add-ons)

XULRunner - [https://developer.mozilla.org/en/XULRunner](https://developer.mozilla.org/en/XULRunner)

Forums - [http://forums.mozillazine.org](http://forums.mozillazine.org)

BTW, I am a total noob in regard to programming, specially javascript. I have started with a lot of bash scripts and now the extension is almost entirely javascript based.

---

### Post by Exodist on 2009-08-23
Try GLADE, 
Its in the repos but you will want to get the glade-gnome-3 package.

---

### Post by bapoumba on 2009-08-23
Moved to PT.

---

### Post by Major_Kong on 2009-08-23
> **Sashin said:**
> Is there an equivalent to visual basic that'll make programs for a gnome desktop?

If not is there a guide to do this from scratch?

If you want a integrated development environment to make some GUIs, try MonoDevelop, and create a new Gtk# project.

[http://monodevelop.com/Documentation/Stetic_GUI_Designer](http://monodevelop.com/Documentation/Stetic_GUI_Designer) - a short tutorial for gui design using monodevelop.


More recommended reading:
[http://mono-project.com/FAQ:_General](http://mono-project.com/FAQ:_General)
[http://www.devx.com/opensource/Article/32302?trk=DXRSS_DOTNET](http://www.devx.com/opensource/Article/32302?trk=DXRSS_DOTNET)

---

### Post by bender1234 on 2009-08-23
> **armageddon08 said:**
> Can GTK be used to create GUI for java apps?

Why would you really need it? You already have good layout managers, and can select 
your lookandfeel :)
 
I really miss gridbaglayout, wish we had it in C/C++.

cheers 
bender

---

### Post by bender1234 on 2009-08-23
> **Sashin said:**
> Is there an equivalent to visual basic that'll make programs for a gnome desktop?

If not is there a guide to do this from scratch?

If you're not afraid of some real programming *duck* have a look at C++ and gtk+ or Qt :)
Qt Designer is fairly decent(I just write the .cpp myself though).

cheers,
Bender

---

### Post by Mirge on 2009-08-23
Did you have something specific in mind that you wanted to write? Or are you just trying to figure out if you're interested in getting into programming or not?

---

### Post by twright on 2009-08-23
> **armageddon08 said:**
> Wow! That's encouraging.
Well, whilst i'm sure that some people swear by it doing it that way mostly defeats the point of using java. If you just use swing and the visual designer in netbeans (which IMO is better than any available for gtk) it will be much easier and look native in the end anyway.

---


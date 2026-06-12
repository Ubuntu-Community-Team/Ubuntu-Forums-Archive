---
title: "GUI developement for a begginner"
date: 2006-02-07
forum: Programming Talk
---

### Post by IanWright on 2006-02-07
Hi guys, I was just wondering if anyone could recommend a method/language for designing GUI's for a begginner. I've not even installed Linux yet, but when I do I need to integrate an interface with the netem functions included in the Linux 2.6 kernel.

A guy called mips suggested I post in the programming forum about the GUI side of things, any suggestions and whether KDE or GNOME would be better would be greatly appreciated. Also, the more simple the design method is, the better, as its for a Uni project that I've got a limited time to develop.

Thanks for your help :)

Ian

---

### Post by mostwanted on 2006-02-07
Tcl/Tk was big a few years back, now it seems Python/GTK and Ruby/Gtk gets the most attention these days when it comes to rapid development.

I personally feel C# or Boo or some other Mono/.NET language with Gtk# is the most well-designed way to make GUIs in Linux. It's very much like Java's SWING, only more clean IMO!

Just because Ruby is the coolest language of the bunch, I'm gonna say Ruby/Gtk, but the best bindings to Gtk+ are definitely Gtk#.

If you already know C/C++, go with Gtk+ (Gnome) or Qt (KDE). 

Man, that post had a lot of slashes ;)

EDIT: Upon re-reading your posts, I have to ask you: you do have prior experience in programming, right? :)

---

### Post by IanWright on 2006-02-07
Done some C, VB and a tiny bit of Java though I ain't too good at it...

---

### Post by percent20 on 2006-02-07
I have to agree with mostwanted.  

Mono is a very good way to go doing C# development.  I currently am working with it and love it.  To find out more here are some resources

[Http://mono-project.org/](Http://mono-project.org/)

irc:
irc.gnome.org
#mono 

I would suggest you go tot he site read up on it.  Go to the irc talk to some people every one is very willing to help out and you can get great help too.

---


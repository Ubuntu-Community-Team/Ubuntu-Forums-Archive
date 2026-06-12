---
title: "Looking for a windowing toolkit"
date: 2010-06-03
forum: Programming Talk
---

### Post by h.r. on 2010-06-03
Hey all,

I'm currently looking for a windowing toolkit to use for an application I'm writing. I've heard people recommend GTK+, qt, fltk, wzwidgets, and others, and I'd love your advice. I'm not too picky on language, as long as it works with something c-like. Java is not out of the question if you think swing is the best way to go.

Here are its characteristics of what I am trying to create. I know I'm erring on the verbose side, but I hope that explaining my goal will help me find the best tool.

1. The program I am writing is for my own use. It needs no more portability than the environment in which it is developed (an Ubuntu box). Licensing is also thereby immaterial. It doesn't need to compile into a tiny executable, run lightning fast, or be particularly gorgeous.

2. The program is a piece of organizational software for a bunch of data, almost like a personal organizer application, but very customized, so it is very interface-centered. In fact it is almost simultaneously an experiment in user interfaces.

3. I don't need a lot of nice components that do fancy stuff, like text editors, file browsers, etc.

4. I do, however, need flexible components and the ability to create my own components, since I will be developing a gui that will help me organize and manipulate my data. I want to push the limits of how data is presented and organized. Things like drag and drop, flexible layout managers, mouseover, and context click support and are a must. A well-organized OOP system would also be great towards this end.

5. I would like to emphasize speed and ease of development (including ease of learning to use this toolkit). Availability of a drag-and-drop/wysiwyg editor would help a lot towards this goal, but is not fundamentally required if the code is clear to deal with. I currently do most of my programming in notepad/gedit, but have experience with eclipse and visual studio.

Thanks for taking the time to read and give your input!

---

### Post by James78 on 2010-06-03
Based on what you want, I'd say use GTK. It's not cross platform portable as far as I know, it'll work out of the box in Ubuntu, and it's very flexible. If you want an easier way to do it, take a look at GTK Glade too.

---

### Post by nvteighen on 2010-06-03
You've got two powerful toolkits, Qt and GTK+, and both are more or less the same, except for the issue that Qt also includes some features not related to GUIs, while GTK+ focuses only on that.

I'd invert the question and ask myself what's the best programming language for such a task and then take a look at what bindings are available for what toolkit. IMO, Qt and GTK+ will both work for you equally, so it's the language which matters most. As you seem to want good OOP support, unless you want to use GLib's OOP, C seems to be out.

Python seems to be oddly out because you want a C-like language.

So, what have we left? C++, Perl, Java, C# and maybe even Javascript. C++ has Qt natively and the gtkmm bindings. Perl has GTK+ bindings... not sure whether it has Qt ones too. Java uses its own Swing, so it's a native solution. (Mono) C#, AFAIK, only has Gtk#. Javascript could be a nice solution as you'd use HTML as your GUI toolkit.

IMO, if that's the list of remaining languages, I'd go for C++/Qt or Java/Swing.

---

### Post by juancarlospaco on 2010-06-03
> **h.r. said:**
> 
It doesn't need to ... run lightning fast, 

I don't need a lot of nice components that do fancy stuff,

need flexible components 
I want to push the limits of how data is presented and organized. 

I would like to emphasize speed


lol, you say opposite things sometimes... :)

---

### Post by h.r. on 2010-06-03
I do not need complex pre-built components, while I do need the flexibility to create custom components.

It doesn't need to run fast, but it needs to be fast to develop.

I had thought this was clear from the original post; sorry if it was not.

---

### Post by Simian Man on 2010-06-03
I would say QT with C++ and QT Creator would be your best bet.  That provides a very nice, well-integrated solution with more power than you probably need.

Normally I'd recommend C# and GTK# but I'm not sure how easy it would be to create custom components in that environment.

---


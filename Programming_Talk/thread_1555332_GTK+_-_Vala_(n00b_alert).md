---
title: "GTK+ - Vala? (n00b alert)"
date: 2010-08-17
forum: Programming Talk
---

### Post by Zorgoth on 2010-08-17
I learned recently about the existence of Vala, a programming language being developed specifically for GNOME, which supposedly has easier syntax than C but has almost C-like speed.  Does anyone know anything about it?

What stage of development is it in?  Could a novice-intermediate level programmer work with it and get results as good as with more traditional languages?  Or is it still an ongoing project that isn't ready for less experienced programmers?

I am thinking of learning GTK+; I am moderately familiar with Qt (which I quite like), but that is essentially the limit of my graphical development knowledge.  I know nothing currently about GNOME libraries, but I am ready to learn, as any software I develop would probably be primarily aimed at GNOME use (since I use GNOME).  My initial idea was to learn gtkmm because C++ is the language I am most familiar with.  However the idea of a language like Vala which is presumably being designed with GTK+ and all those G* development tools in mind is intriguing.

Do you think that learning Vala together with GTK+ is a good idea?

I do not know C#.

I am not any kind of C++ master and do not know a lot of the STL stuff, so I am not attached too deeply to the language.

I am also considering learning Python with GTK+, as doing numerical stuff in Matlab and learning more about bash scripting has gotten me much more interested in high level languages, and I imagine that since my GUIs would mostly be lightweight frontends to more resource-consuming command-line processes I wouldn't notice the performance difference - how would you compare the difficulty of Python/GTK+, gtkmm, and Vala/GTK+ - how hard to learn, and how does development time of a GUI compare in each?

Although as I said I think that python will be fine for most of my purposes, I would like to know something like gtkmm or Vala/GTK+ 

a) so that I can write faster GUIs if some program I am creating becomes very complicated and so that I can write GUIs that are integrated better with the backend, which I doubt I will want to write in Python.

and b) because I fundamentally like lowish-level programming and I think it is probably good for me

---

### Post by GenBattle on 2010-08-17
I would recommend you also look at Go ([http://golang.org](http://golang.org)) as an option, although it's still very experimental and the GTK bindings are far from perfect. Fits your description of a low level language, but probably more suited to the backend development than the GUI end (until the language matures a bit more).

---

### Post by matmatmat on 2010-08-18
It should be stable enough for you to just write programs in it. [Cheese]("http://projects.gnome.org/cheese/"), [Shotwell]("http://yorba.org/shotwell/") and [Lombard]("http://yorba.org/lombard/") are written in Vala.

---

### Post by SledgeHammer_999 on 2010-08-18
First of all Gtk+, is not a GNOME library.

Second, most of the members here recommend PyGtk, I personally prefer Gtkmm. To tell the truth I've never took python seriously. I tried once to read code and help a project (emesene2) but I was frustrated. I can't stand to not know what kind of variable type a function accepts. I just like to look at the definition and know that it accepts an int or a std::string. Also the same thing applies about the type it returns. To tell the truth the PyGtk API docs have all this info, but the functions someone else has written don't. So I don't want to go around guessing what goes here and what goes there. Maybe this is a side-effect of C++, I dunno.

For GUI development. Generally there are 2 ways you can do it. Write all the code yourself manually. Vala, Python and C++ versions of Gtk can accomplish this in relatively the same number of lines, which is small and readable. But if you use the C API it will be much bigger. The other way is to build your GUI visually using Glade and then load the .glade file in your code. Every language mentioned above is the same give or take on this point. So to sum up, it doesn't really matter if you choose Vala, Python or C++ for your GUI. It matters for your non-gui stuff.

---

### Post by kahumba on 2010-08-18
I'm a Java dev but I tried Gtk in C, C++ and now in Vala and Vala is certainly better than C++ and I'm not even comparing to C cause programming GTK apps in C is a nightmare. A few pros for Vala that I like:

1) It's comfortable to write code in
2) Doesn't require you to write header files - this is such a relief for me since I hate having to keep synchronizing the header files with my source code, thus mostly wasting time and "brain cycles".
3) (Much) easier and simplified memory management (those nasty C/C++ memory leaks hard to find won't likely bother you that often) but Vala also allows you to use "true" C/C++ pointers if you need more speed and control (which is seldom the case).
4) To some degree it's what C++ was supposed to be if you know what I mean because it also offers in-code properties etc etc making it much friendlier than C++.
5) It's fairly stable so you can write small and middle size apps and trust me you won't need to write huge projects any time soon and by that time Vala's gonna evolve to handle those as well.

But, if you think you can get away with Python - go for it cause Vala is still a compiled language and despite it being (much) more powerful and fast and no matter how friendlier it is than C/C++ it can never be as easy as Python.

---

### Post by SledgeHammer_999 on 2010-08-18
> **kahumba said:**
> 
2) Doesn't require you to write header files - this is such a relief for me since I hate having to keep synchronizing the header files with my source code, thus mostly wasting time and "brain cycles".

Technically speaking you can do the same in C and C++.

> **kahumba said:**
> 3) (Much) easier and simplified memory management (those nasty C/C++ memory leaks hard to find won't likely bother you that often) but Vala also allows you to use "true" C/C++ pointers if you need more speed and control (which is seldom the case).

This is specific to Gtkmm. You can use Gtk::Manage on a widget. What it does? You create an instance of the widget(though "new Gtk::Button;"). You put that in a container. In gtk every widget has to be in a container(except the Gtk::Windows). Each container can have more than one children. When you Gtk::Manage a widget, then it gets deleted automatically when it's container gets deleted. So you only have to remember to delete the container(or the container's container etc).

---

### Post by Lootbox on 2010-08-18
> **SledgeHammer_999 said:**
> To tell the truth I've never took python seriously. I tried once to read code and help a project (emesene2) but I was frustrated. I can't stand to not know what kind of variable type a function accepts. I just like to look at the definition and know that it accepts an int or a std::string. Also the same thing applies about the type it returns. To tell the truth the PyGtk API docs have all this info, but the functions someone else has written don't. So I don't want to go around guessing what goes here and what goes there. Maybe this is a side-effect of C++, I dunno.

I'm probably one of very few, but I agree completely. I find that for small scripts, the dynamic type system is marginally more convenient, but as soon as multiple components begin interacting, code becomes much more difficult for me to read.

[edit] Sorry, I don't mean to divert your thread.

---

### Post by kahumba on 2010-08-18
> **SledgeHammer_999 said:**
> Technically speaking you can do the same in C and C++.

This is specific to Gtkmm. You can use Gtk::Manage on a widget. What it does? You create an instance of the widget(though "new Gtk::Button;"). You put that in a container. In gtk every widget has to be in a container(except the Gtk::Windows). Each container can have more than one children. When you Gtk::Manage a widget, then it gets deleted automatically when it's container gets deleted. So you only have to remember to delete the container(or the container's container etc).

True but in Vala it's more handy cause it's built-in at the language level and it's more flexible cause it deals with pretty much anything not just widgets and you don't have to write each time the "Gtk::manage" strings which spares you time, code space and the extra brain cycles. I do program in Gtkmm but I'm learning Vala now and I really think it's more handy and "pretty".

---

### Post by SledgeHammer_999 on 2010-08-18
True enough. The bottomline is use whatever suits you.

---

### Post by kahumba on 2010-08-18
> **SledgeHammer_999 said:**
> Technically speaking you can do the same in C and C++.

Yes but given **the nature of C++** it's not a viable solution to program for serious without header files.

---

### Post by JoeDavis on 2010-08-18
Vala is stable enough for application development, it reached version 0.9.6 today. With any luck we could see a version 1.0 by the end of the month.

---

### Post by gorilla3d on 2010-08-18
Its a great language, however it does not protect you from making the same mistakes you make in C or C++. In fact because your going to end up using threads or weak references in Vala your going to eventually shoot yourself in the foot with a segment fault.

I have found vala, makes code much more manageable, but compared to C or C++ your not going to write applications faster.

---

### Post by interval1066 on 2010-08-19
> **kahumba said:**
> A few pros for Vala that I like:

1) It's comfortable to write code in
2) Doesn't require you to write header files - this is such a relief for me since I hate having to keep synchronizing the header files with my source code, thus mostly wasting time and "brain cycles".
3) (Much) easier and simplified memory management (those nasty C/C++ memory leaks hard to find won't likely bother you that often) but Vala also allows you to use "true" C/C++ pointers if you need more speed and control (which is seldom the case).
4) To some degree it's what C++ was supposed to be if you know what I mean because it also offers in-code properties etc etc making it much friendlier than C++.
5) It's fairly stable so you can write small and middle size apps and trust me you won't need to write huge projects any time soon and by that time Vala's gonna evolve to handle those as well.

But, if you think you can get away with Python - go for it cause Vala is still a compiled language and despite it being (much) more powerful and fast and no matter how friendlier it is than C/C++ it can never be as easy as Python.

I don't quite understand your issue with header files. I've never had problems "synchronizing" headers with the rest of the source, I'm not exactly sure what that means... a header files is just a section of the source code that may or may not contain definitions that you can share with other source files that require those same definitions. You can write C applications without ever writing header files. Not recommended, but possible.

As for Vala, I don't know anything about it, but it sounds interesting. But it also sounds immature. I see lots and lots of Gnome apps written in python, might as well use it. Its not for me, but it appears to be a successfully used tool with lots of folks.

---

### Post by kahumba on 2010-08-19
> **interval1066 said:**
> I don't quite understand your issue with header files.

What don't you understand? The obvious issues with header files? Is it flash news to you that one of the reasons why C#/Java like languages are easier to program in is cause they don't require you to use/keep up to date header files while developing a project? Stop underestimating and hijacking obvious facts.

---

### Post by interval1066 on 2010-08-19
> **kahumba said:**
> What don't you understand? The obvious issues with header files? Is it flash news to you that one of the reasons why C#/Java like languages are easier to program in is cause they don't require you to use/keep up to date header files while developing a project? Stop underestimating and hijacking obvious facts.

Stop being an ***. I've not found maintaining header files to be that much of a bother. Too bad for you if you have. I mean, REALLY TOO BAD FOR YOU. You must be a simpleton, because they really aren't THAT big a deal.

YOU: "Yes but given the nature of C++ it's not a viable solution to program for serious without header files."

You sound like an utter fool, and obviously scared of C programming. You make it sound like some kind of ancient and arcane practice. I, and thousands of programmers around the globe use C/C++ all the time. I use it exclusively for Gnome Desktop Programming. Its not my fault your scared of C programming. Get a grip. And your just wrong about header files being some kind of pain in butt. Of all the complaints I've read online about C++, yours is about the stupidest I've ever come across.

---

### Post by kahumba on 2010-08-19
Congratulations, you're the king of hijacking/misinterpreting my points!
1) I never said/implied header files are difficult, I just said it's better not to have to deal with them because of the already mentioned issues.
2) Don't shout and don't take it personal or you (and I) can easily get banned without warning, so if you don't agree or are in bad mood - calm down and/or take a hike.

---


---
title: "plz help me write my &quot;Hello World&quot; program for Gnome"
date: 2007-07-06
forum: Programming Talk
---

### Post by medya on 2007-07-06
hi I wan to start learning programing for linux (gnome)

I alreayd know some C++ in text mode.

now I want to write a program that will show Hello World or something in a gnome window.
what should I do .

I guess it would be easy. but would somebody help me step by step , I just wanna start moving , I am sure after doing this I will learn by myself.

---

### Post by lisati on 2007-07-06
Most flavours of Ubuntu come with "gcc" which can compile 'C' programs.

The command console (terminal) can be found under "Accessories" on the Applications menu. From there you can use gedit, vi, emacs or similar to edit your program. You can then use gcc to compile your program

Hope that's enough to help you get started

---

### Post by medya on 2007-07-06
thats not what I needed, I want to show a simple message in GUI window .
would somebody just tell me step by step, what to do ?

just a very quick start to GUI programming.

---

### Post by the_unforgiven on 2007-07-06
> **medya said:**
> thats not what I needed, I want to show a simple message in GUI window .
would somebody just tell me step by step, what to do ?

just a very quick start to GUI programming.
Here is a simple tutorial on GTK+ 1.2:
[http://www.gtk.org/tutorial1.2/](http://www.gtk.org/tutorial1.2/)

It's a bit outdated, but the concepts are the same.

C++ bindings for GTK+/GNOME exist as gtkmm:
[http://gtkmm.sourceforge.net/](http://gtkmm.sourceforge.net/)

Here is gtkmm docs link:
[http://gtkmm.sourceforge.net/docs/gtkmm-2.4/docs/](http://gtkmm.sourceforge.net/docs/gtkmm-2.4/docs/)

HTH ;)

---

### Post by medya on 2007-07-06
thanks but still I would apperciate it if somebody tell me a very quick thing to do :
I know I am strange but I am like that
I like to make a program first then learn programing ...

can sombody just help me make a Window in gnome which says Hello World and it has a OK button which will exit the program by clicking on it.

I would appeciate it if someone tell me to do this qucik thing step by step

---

### Post by badactress on 2007-07-06
Hi,

This link:  [http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03s07.html]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03s07.html")

Is your Hello World program :)  Though you might need to read back through the earlier parts of the tutorial to fully understand how it works.. and also to make sure you have the correct dev libraries installed to be able to compile a gtk application.

Hope this helps a little..

---

### Post by samjh on 2007-07-06
You're not going to get much simpler than doing these:

1. Install GTKmm:
```
sudo apt-get install libgtkmm-2.4-dev
```

2. Go to [http://gtkmm.sourceforge.net/docs/gtkmm-2.4/docs/tutorial/html/ch03.html](http://gtkmm.sourceforge.net/docs/gtkmm-2.4/docs/tutorial/html/ch03.html) and follow the instructions to create your first Hello World using GTK.

If you can't be bothered to read, then copy-paste this into a helloworld.cpp file:
(be warned that this is an extremely simple example, and it does not exit gracefully)
```
#include <gtkmm.h>

int main(int argc, char *argv[])
{
    Gtk::Main kit(argc, argv);

    Gtk::Window window;

    Gtk::Main::run(window);
    
    return 0;
}
```
... and compile it using:
```
g++ helloworld.cpp -o helloworld `pkg-config gtkmm-2.4 --cflags --libs`
```

---

### Post by rye_ on 2007-07-06
Hi,

I don't know the code off of the top of my head, and I doubt anyone on the forum will do something for you that just required a few minutes of reading from the sites above (I mean no offence in saying this).
(EDIT : in the space of seeing your message and writing my response, two posters above have kindly offered examples.)

But.. one option would be to google for examples, or If you download a C IDE (kdevelop, anjuta, code::blocks) then they tend to provide options for gui programs (Qt, GTK+, wxWidgets etc) which also contain sample programs.

Certainly I would advise that if your C skills are very new, Then you are better learning and practicing the constructs of the language, relying on the terminal input and output rather then learning a gui sub-language.
This was my tack.

Ryan

---

### Post by medya on 2007-07-06
Thanks a lot to you all of you, you ubuntu forum users are great  !

:) I have many many IDEAS to make COOOL GREAT programs for ubuntu , I am starting to learn thigns... thanks again.

---

### Post by medya on 2007-07-06
ok guys I wrote my first program, how can I make a deb package out of my .C file ?

---

### Post by jurkki on 2007-07-07
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

---

### Post by medya on 2007-07-08
I see most of the good programs for ubuntu are written by python , can somebody give me some good tutorial links , to learn making GUI programs using python.

---

### Post by ButteBlues on 2007-07-08
If you know Python, just search for the pygtk site. Tons of good information there.

---


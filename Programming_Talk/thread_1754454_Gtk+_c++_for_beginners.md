---
title: "Gtk+ c++ for beginners"
date: 2011-05-10
forum: Programming Talk
---

### Post by Jagoly on 2011-05-10
Hello. A while ago I started learning c++, but I got slack. Now I'm getting back into it, and I'd like to start making some graphical applications. So I have a few queries:

If I were to learn gtk, It would be used for "normal" applications, right?
If wanted to use fancy graphics, eg a game, I would have to separately learn something like sfml, allegro, opengl, ect.
Does anyone here know any good books/guids for gtk?

Thanks!

---

### Post by PaulM1985 on 2011-05-10
I have done a little work with GTK in the past.  However I was using gtkmm which is the C++ binding for GTK.  I just picked it up from the website:
[http://www.gtkmm.org/en/](http://www.gtkmm.org/en/)
There is a documentation section with examples and links to the API.

There seem to be a few applications "normal" applications that use GTK.  See here: [http://en.wikipedia.org/wiki/GTK%2B#Applications](http://en.wikipedia.org/wiki/GTK%2B#Applications)

For the "fancy graphics" side of things I would look into opengl.  I have used that a little in the past and it is something I am about to start looking into again.  There are plenty of tutorials for it.  I found this to be the best:
[http://www.videotutorialsrock.com/](http://www.videotutorialsrock.com/)

If you are looking to use opengl and GTK you will have to bind them together somehow. I don't know how this is done but I am sure you will find stuff through google.

Paul

---

### Post by Jagoly on 2011-05-10
Whoa, thanks! Do you know where I might be able to grab a PDF of that? With google I can only find pdf's for gtkmm 2.4. When of programming, 90% of the time I don't have an Internet connection.

Had a bit of a look through it, and it wasn't as scary as I thought it would be. This is going to be fun!

---

### Post by nvteighen on 2011-05-10
> **Jagoly said:**
> Whoa, thanks! Do you know where I might be able to grab a PDF of that? With google I can only find pdf's for gtkmm 2.4. When of programming, 90% of the time I don't have an Internet connection.

Had a bit of a look through it, and it wasn't as scary as I thought it would be. This is going to be fun!

Much better, do the following in the Terminal:

```

sudo apt-get install devhelp libgtkmm2.4-doc

```

DevHelp is a nice documentation browser; libgtkmm2.4-doc is the whole documentation, which you'll be able to look up using DevHelp offline (also, any web browser, but DevHelp is better IMO).

Of course, in order to develop using Gtkmm, you have to install libgtkmm2.4-dev, build-essentials (which gets all essential development packages), and possibly some GUI designer (designing GUIs by hand in source code can be really hard). Install all of these using apt-get.

---

### Post by Jagoly on 2011-05-11
thanks! I have no idea why I didn't just do this in the first place. Plus, it's ```
libgtkmm-2.4-doc
``` not ```
libgtkmm2.4-doc
```

EDIT: Just finished installed, I tested it out, devhelp is awesome!!! MUCH better than any pdf.

---

### Post by nvteighen on 2011-05-11
> **Jagoly said:**
> thanks! I have no idea why I didn't just do this in the first place. Plus, it's ```
libgtkmm-2.4-doc
``` not ```
libgtkmm2.4-doc
```

EDIT: Just finished installed, I tested it out, devhelp is awesome!!! MUCH better than any pdf.

Oh, yes. My fault :P

---


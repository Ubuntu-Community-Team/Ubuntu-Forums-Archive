---
title: "How are toolkits combined with C++?"
date: 2010-12-31
forum: Programming Talk
---

### Post by mickbuntu on 2010-12-31
Hello,

   I got a question just out of interest.  Ok, you have C++ which is a language that does not have a gui. Next, you have toolkits for it to add the gui widgets.   If one learns C++ lets say how does it get added to the gui given example  here would be qt4, or gtk2 most used esp on linux.

Can someone show me the most most basic none fancy example how C++ looks compared to how GTK+/qt4 looks toolkits when applied to the language. I want to see how the language adds the toolkit component to it. Also if one knows C++ how difficult is it to lets say implement the knowledge to toolkits?

what changes when you introduce toolkits to C++ and what stays?

I mean you have gazillion tutorials to learn C++ but many of those especially for linux do not show how to combine the knowledge. Or maybe I am just not looking in the right place just it seems that C++ is hard but learn-able language if one commits to it what is harder to to add the graphical components to it.

---

### Post by worksofcraft on 2010-12-31
> **mickbuntu said:**
> Hello,

   I got a question just out of interest.  Ok, you have C++ which is a language that does not have a gui. Next, you have toolkits for it to add the gui widgets.   If one learns C++ lets say how does it get added to the gui given example  here would be qt4, or gtk2 most used esp on linux.

Can someone show me the most most basic none fancy example how C++ looks compared to how GTK+/qt4 looks toolkits when applied to the language. I want to see how the language adds the toolkit component to it. Also if one knows C++ how difficult is it to lets say implement the knowledge to toolkits?

what changes when you introduce toolkits to C++ and what stays?

I mean you have gazillion tutorials to learn C++ but many of those especially for linux do not show how to combine the knowledge. Or maybe I am just not looking in the right place just it seems that C++ is hard but learn-able language if one commits to it what is harder to to add the graphical components to it.

The Graphical User Interface (GUI) is not part of any programming language it is part of your operating system.

The operating system provides an Application Programming Interface (API) which in C++ is defined with header files and accessed through linked libraries.

On Linux, Gui libraries from different sources often include higher levels of abstraction so that you don't have to manipulate everything at the basic X11 protocol level... what level are you interested?

---

### Post by mickbuntu on 2011-01-01
Thank you for the reply I was just curious. I'm actually interested in general application development rather than bare bones. Thanks Again.

** Update: I have found an interesting book called: C++ GUI Programming with Qt4 it also includes how the convergence happens. **


> **worksofcraft said:**
> The Graphical User Interface (GUI) is not part of any programming language it is part of your operating system.

The operating system provides an Application Programming Interface (API) which in C++ is defined with header files and accessed through linked libraries.

On Linux, Gui libraries from different sources often include higher levels of abstraction so that you don't have to manipulate everything at the basic X11 protocol level... what level are you interested?

---

### Post by worksofcraft on 2011-01-01
> **mickbuntu said:**
> Thank you for the reply I was just curious. I'm actually interested in general application development rather than bare bones. Thanks Again.

** Update: I have found an interesting book called: C++ GUI Programming with Qt4 it also includes how the convergence happens. **

As an offshoot of my work on localization of numbers there is a module called cs_glade in my [internationalization library]("http://code.google.com/p/speaknumber/downloads/list") (file cs_lib-0.0.1.tar) and as far as I'm concerned it is so much simpler to use... whatever... if you do wanna try it out, extract the archive, build it with ./build.sh and just see how simple my interactive ./helloglade and ./vending examples are... ./base is not to hard to follow either.

There is also an archive containing tutorial and documentation although that is more focussed on i18n and l10n aspects :lolflag:

---


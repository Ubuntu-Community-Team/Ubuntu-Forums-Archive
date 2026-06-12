---
title: "Windows Desktop Programming with C++ and QT4?"
date: 2007-11-07
forum: Programming Talk
---

### Post by chrisfay on 2007-11-07
I was curious if anyone had suggestions for building desktop GUI applications for windows using various GUI toolkits/IDE's. 

I have experience using Java and C# for this purpose, but have recently been charged with building some Win applications in C++ to bypass issues surrounding customer environments not having .Net or a JVM installed. I am fairly spoiled by the ease of building such apps with .Net and Java form builders and am looking for a similar fashion to develop in C++.

I have been toying with the QT4/VS 2005 C++ combination but wanted input regarding other possibilities before trudging too far into it. I realize this is not really a Linux/Ubuntu based question, but have had a great history with this forum for various help and resources. 

What are some good GUI toolkits, full IDE's or development strategies for building Windows desktop Apps? My experience with C++ is fairly low in comparison to Java and C#, but would like some input on where to start if possible. Any recommendations would be appreciated....

Thx!

---

### Post by LaRoza on 2007-11-07
You can try wxWidgets. My wiki has GUI references for C++, and other languages.

---

### Post by samjh on 2007-11-07
> **chrisfay said:**
> I am fairly spoiled by the ease of building such apps with .Net and Java form builders and am looking for a similar fashion to develop in C++.

I have been toying with the QT4/VS 2005 C++ combination but wanted input regarding other possibilities before trudging too far into it. I realize this is not really a Linux/Ubuntu based question, but have had a great history with this forum for various help and resources. 

What are some good GUI toolkits, full IDE's or development strategies for building Windows desktop Apps?!

The two most mature libraries which support form-based GUI development are GTK+ and QT.

WIth GTK+, you can use the Glade designer, which will generate a *.glade file.  You can then use the libglade library in your C or C++ code to dynamically load and work with the GUI.  GTK+ and libglade is written using C, and those libraries are still very popular even for C++ programmers.  If you want pure C++, use GTKmm and libglademm, which are C++ bindings for GTK+ and libglade, respectively.

GTK: [http://www.gtk.org/](http://www.gtk.org/)
Glade: [http://glade.gnome.org/](http://glade.gnome.org/)
libglade: [http://www.jamesh.id.au/software/libglade/](http://www.jamesh.id.au/software/libglade/)


With QT, it has QT-designer and a range of tools for documentation, localisation, etc.  The benefit of QT is that is more than just a GUI library.  It is more like MFC, in that it uses its own strings and data types, includes libraries for networking, database access, etc.  Unfortunately my experience with QT form design is very limited, so I can't advise you any further.

QT 4.3: [http://doc.trolltech.com/4.3/index.html](http://doc.trolltech.com/4.3/index.html)
QT with Visual Studio: [http://doc.trolltech.com/vs-integration-1.2/index.html](http://doc.trolltech.com/vs-integration-1.2/index.html)
QT Eclipse plugin: [http://trolltech.com/developer/downloads/qt/eclipse-integration-download](http://trolltech.com/developer/downloads/qt/eclipse-integration-download)

---

### Post by chrisfay on 2007-11-08
Thank you both - I had stumbled upon WxWidgets the other day, but hadn't realized there was an integrated version with DevC++ which may be just what I need. 

Glade/Anjuta looks pretty slick as well and may have to check that out.

---

### Post by the_unforgiven on 2007-11-08
As for the IDE, you might want to check out [Code::Blocks]("http://www.codeblocks.org") - a cross-platform IDE that supports both GTK+ and QT project templates.

---

### Post by aks44 on 2007-11-08
The good part with Qt is that you can quite easily develop from the comfort of Linux and (provided you use NO Linux-specific code) cross-compile it on Linux for a Windows target (using MinGW).

I have no real world experience about that but all my experiments showed that it works quite well.

Qt4 + boost should give you all the necessary platform-independence you need, after that you only need to switch between the GCC and MinGW toolchains depending on what target you need to build.

---


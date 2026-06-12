---
title: "Gtk Multithreading problems ?"
date: 2013-01-09
forum: Programming Talk
---

### Post by DaviesX on 2013-01-09
Hi, ):P now I have a problem. I have a GUI program that uses Gtk and build with Glade. And it has a menu bar in it. When I press a menu, it receives a signal and call a function from a rendering library which keeps looping and uses Cario surface to print something to a GtkImage widget.

In order to let GtkImage refresh to display what is in the Cario surface, I want to create another thread to keep the GUI active. So I use POSIX pthread functions to create a thread. 
```

pthread_t id;
pthread_create ( &id, nullptr, RenderFramesLoop, nullptr );

```

Actually it works for a few second, but as soon as I move the mouse in that GUI window, it crashes and prints as following: 

```

(X3dRenderLibrary:20185): Gdk-WARNING **: The program 'X3dRenderLibrary' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadLength (poly request too large or internal Xlib length erro'.
  (Details: serial 1131 error_code 16 request_code 29 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

So I look through Google and find that Gtk actually has some thread managing functions too. I haven't tried those functions yet, but I am confused. Why Gtk should have those functions ? What are the differences ? Does those functions could probably solve the crash ? And how could I use it properly ?

Thank you :)

---

### Post by SledgeHammer_999 on 2013-01-09
The basic rule of conduct for Gtk is: You do not call GUI functions from another thread. You only do that from the main thread(also called gui thread). You could do it from another thread but you need to acquire some specific GDK locks first, if I remember correctly.

I cannot help you more without a code sample or example code. Also could you tell in more detail what your threads are doing(or trying to do)?

About Gtk threads: They wrap around the posix thread functionality(or windows thread depending on platform) and provide a way to write crossplatform multithreaded programs. Also you can use/intergrate them with other Gtk stuff easier (callbacks,signals, mainloops etc).

---

### Post by bird1500 on 2013-01-09
Don't use GDK's enter/leave mechanisms for accessing gtk from different threads - it's been deprecated since gtk 3.4 or 3.6, don't recall exactly.
So if you're oriented towards the future and don't want compiler warnings all over use:

Glib::signal_idle().connect(sigc::ptr_fun(myFunc))

 where myFunc will run in the main thread despite being called from another thread. It's not handy at all but that's what the Gtk devs want you to do from now on.
myFunc should look like this:
bool myFunc() {
 //do stuff;
 return false;
}

These are gtkmm (C++) examples,  gtk (C) should be similar.

And, you don't need to init the threading functionality in gdk or gtk any longer either.
[http://gtk.10911.n7.nabble.com/deprecating-gdk-threads-td21306.html](http://gtk.10911.n7.nabble.com/deprecating-gdk-threads-td21306.html)

---

### Post by DaviesX on 2013-01-09
Thank you both first.
According to SledgeHammer, "You do not call GUI functions from another thread" but I did call a cairo paint function in that thread. So probably it is the cause. 
 
And bird1500 said "Don't use GDK's enter/leave mechanisms for accessing gtk from different threads". Does it mean I should not use gdk lock as a solution ?
 
If that is so, can I change all those cairo functions in another thread to OpenGL function to avoid accessing GUI ? If that works, is there anyway to have Gtk work with OpenGL(I mightonly use OpenGL's surface display function) ? It seems that OpenGL only has interface for XWindow. But I don't want to use XWindow 'cause Glade is way more convinent. It might be hard to redo all the GUI. Is there anyway to do in that way ?

---

### Post by bird1500 on 2013-01-09
It used to be that you could call gtk API functions from different threads if these calls sat between gdk_threads_enter() and gdk_threads_leave() - which was pretty handy. Now it's deprecated, though still works and you'll get warnings when compiling. Gtk4 plans to remove this functionality completely.

There's the OpenGL Gtk2 extension (to be installed separately) which hasn't been ported to Gtk3, so you probably can't do OpenGL in a Gtk3 GUI.

For OpenGL Qt4 is way better I hear, though haven't tried out myself.

The Gtk2 OpenGL extension:
> 
apt-cache show libgtkgl2.0-dev

Package: libgtkgl2.0-dev
Priority: optional
Section: universe/libdevel
Installed-Size: 124
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Sam Hocevar <sho@debian.org>
Architecture: amd64
Source: gtkgl2
Version: 2.0.1-2
Provides: gtkgl-dev
Depends: libgtkgl2.0-1, libgtk2.0-dev
Conflicts: gtkgl-dev
Filename: pool/universe/g/gtkgl2/libgtkgl2.0-dev_2.0.1-2_amd64.deb
Size: 16516
MD5sum: ebbbaeaa2e4a40aebdc2717c863816fb
SHA1: a69d87f712265c4c116fc785d43536fb744f4fb3
SHA256: e674cc447233588b74e9a57df2273f6dfc3d17daf72aeeedbb1837d4a2640f52
Description-en: OpenGL context support for GTK+ (development files)
 The gtkgl library provides GtkGLArea (a GTK+ widget containing an OpenGL
 context for fast 2D and 3D graphics), GdkGLPixmap (an off-screen rendering
 context) and GdkGLContext (an OpenGL extension for virtually any drawable
 widget).
 .
 This package contains the headers and static library.
Homepage: [http://www.mono-project.com/GtkGLArea](http://www.mono-project.com/GtkGLArea)
Description-md5: 13458bfb9ef3acff57f4f800c12e5c07
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu




---

### Post by DaviesX on 2013-01-09
Ok, I see. I read the website you posted. It seems to be a separated project from Gtk rather than built-in Gtk APIs. I wonder why doesn't Gtk support OpenGL internally ? It's so sad that gnome 3 has already been highly GPU-accelerated while Gtk is still so poor in supporting OpenGL @,@ Don't they decide to give up graphics programs ?

---

### Post by DaviesX on 2013-01-09
Actually they indeed has such GL extension
gtkglext
[http://projects.gnome.org/gtkglext/](http://projects.gnome.org/gtkglext/)
I think I'll try that later :)

Thank you everybody

---

### Post by bird1500 on 2013-01-10
Afaik gtkglext doesn't support Gtk3 either, only Gtk2.

---


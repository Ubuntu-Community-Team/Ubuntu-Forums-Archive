---
title: "python pyclutter pyclutter-gst gstreamer problem"
date: 2010-06-27
forum: Programming Talk
---

### Post by Vids on 2010-06-27
I am trying to display video using gstreamer. 
my reference :[http://www.hindsightlabs.com/blog/2010/02/09/pyclutter-video-tutorial/](http://www.hindsightlabs.com/blog/2010/02/09/pyclutter-video-tutorial/)

Prob: I am not able to install pyclutter and pyclutter-gst packages.  Packages not found in the repository. Hence not able to import clutter-gst.

What I tried:

1) 
-I installed libclutter, cairo, gtk, gst , python-clutter, python-gst etc using the sudo apt-get command.
-Then couldn't find pyclutter package.

2)
-So downloaded the sources clutter-1.0.0,clutter-gst-0.10.0 pycairo-1.0.0 and installed them from source using ./configure, make and sudo make install. It went through.
-Downloaded pyclutter-1.0.0 source. 

cd pyclutter-1.0.0
./configure  (worked)
make

The following error comes:
[I][SIZE=1]Could not write method ClutterBindingPool.override_closure: No ArgType for GClosure*
***INFO*** The coverage of global functions is 100.00% (48/4:cool:
***INFO*** The coverage of methods is 99.80% (495/496)
***INFO*** The coverage of virtual proxies is 100.00% (19/19)
***INFO*** The coverage of virtual accessors is 100.00% (24/24)
***INFO*** The coverage of interface proxies is 100.00% (5/5)
  CC    clutter.o
clutter-cairotexture.override:90:21: error: pycairo.h: No such file or directory
clutter-cairotexture.override:92: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
clutter-cairotexture.override: In function ‘_wrap_clutter_cairo_set_source_color’:
clutter-cairotexture.override:29: warning: implicit declaration of function ‘PycairoContext_GET’
clutter-cairotexture.override:29: warning: passing argument 1 of ‘clutter_cairo_set_source_color’ makes pointer from integer without a cast
clutter.c: In function ‘_wrap_clutter_cairo_texture_create_region’:
clutter.c:11388: warning: implicit declaration of function ‘PycairoContext_FromContext’
clutter.c:11388: warning: return makes pointer from integer without a cast
clutter-cairotexture.override: In function ‘_wrap_clutter_cairo_texture_create’:
clutter-cairotexture.override:129: warning: return makes pointer from integer without a cast
clutter.c: In function ‘_wrap_clutter_path_to_cairo_path’:
clutter.c:13453: error: ‘PycairoContext’ undeclared (first use in this function)
clutter.c:13453: error: (Each undeclared identifier is reported only once
clutter.c:13453: error: for each function it appears in.)
clutter.c:13453: error: ‘cr’ undeclared (first use in this function)
clutter.c:13455: error: ‘PycairoContext_Type’ undeclared (first use in this function)
make[2]: *** [_clutter_la-clutter.lo] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2[/SIZE][/I]

How do I go forward? Any help is appreciated!

---

### Post by splicerr on 2010-06-28
Don't know which version you're running but pyclutter is in the Lucid repositories.

```

$ apt-cache search python clutter
python-clutter - Open GL based interactive canvas library - Python bindings
python-clutter-dbg - Open GL based interactive canvas library - Python bindings debugging symbols
python-clutter-dev - Open GL based interactive canvas library - Python bindings development files
python-clutter-doc - Open GL based interactive canvas library - Python bindings documentation
python-clutter-gtk - Python bindings for Clutter-Gtk
python-clutter-gtk-dbg - Python bindings for Clutter-Gtk - debugging symbols
python-clutter-gtk-dev - Python bindings for Clutter-Gtk - development files

```

---

### Post by Vids on 2010-06-28
Thanx splicerr. I could find the first 2 in the repository.

I installed the following:
$ sudo apt-get install libclutter-0.6-0 libclutter-0.6-dev   libclutter-gtk-0.6-0 libclutter-gtk-0.6-dev libclutter-gst-0.6-0 libclutter-gst-0.6-dev libclutter-cairo-0.6-0 libclutter-cairo-0.6-dev python-clutter python-gst0.10 python-gtk2


And I am trying to run the example code:[INDENT]import clutter, gst, cluttergst

stage = clutter.Stage()
stage.set_size(1024,768)
stage.connect('destroy', clutter.main_quit)

tx = cluttergst.VideoTexture()
tx.set_uri("file:///Users/cmerand1/Desktop/hindsightlabs/bazooka/examples/yu3.mp4")
tx.set_playing(True)

stage.add(tx)
stage.show_all()
clutter.main()
[/INDENT]I am getting the following error: 
$python example5.py
Fatal Python error: can't initialize module clutter
Aborted

Also, could you find pyclutter-gst in the repository. Thanx.

[EDIT]
I upgraded to ubuntu 10.4 to install libclutter-1.0.0 and other updated packages. Then I could install the pyclutter-gst module for importing cluttergst.

---


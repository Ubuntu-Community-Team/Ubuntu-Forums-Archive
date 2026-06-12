---
title: "Pythons cluttergst module"
date: 2010-05-08
forum: Programming Talk
---

### Post by Admiral Yi on 2010-05-08
I need help with cluttergst. I have been trying to follow recent python tutorials in linux format magazine. I have used Python for a while, but never the clutter module. However, every time I run my code I get:

```
    import cluttergst 
ImportError: No module named cluttergst

```

I have searched high and low through the repos and over the Internet, but can't find anything to do with cluttergst. What do I need to install to get this module?

EDIT: Also, I have this simple code:
```
import gst
import clutter

stage=clutter.Stage()
stage.set_title("Clutter Camera")
stage.set_size(320,290)
stage.set_color(clutter.Color(255,255,255,255))
stage.show()
```

It should just create a blank box. When I run it line by line in the interpreter, it works fine and produces said blank box. If I run 'python program.py' from the command line, nothing happens. No errors, just nothing. Any ideas?

---

### Post by steeleyuk on 2010-05-08
This is a small sample of code to get the box to display, with some slight modifications to make it work better.

```
#!/usr/bin/env python

# Import clutter module
import clutter

stage=clutter.Stage()
stage.set_title("Clutter Camera")
stage.set_size(320,290)
stage.set_color(clutter.Color(255,255,255,255))
# Allow us to quit properly
stage.connect("destroy", lambda q: clutter.main_quit())
stage.show()
# Clutter main loop, makes the window display until event
clutter.main()
```

As to why you need "cluttergst", I don't know whether its a misprint or something else. It should be "import clutter", and "import gst" (gstreamer), as you have it in the code you posted.

The reason the second piece of code isn't working (technically it is working, you're just not seeing the window) is because you don't have "clutter.main()" (see sample above). This is the clutter main loop, which makes the window display on screen until an event occurs.

---

### Post by Admiral Yi on 2010-05-08
Ah thanks, that new code works better. As to the cluttergst, I don't need it for that bit of code I know, but it is needed for something else. The tutorial I am following uses it, and some trial and error it seems to be necessary for the line:

```
self.video1 = gst.VideoTexture()
```

I would really like to know where I can get this module.

---

### Post by steeleyuk on 2010-05-08
I've had a good look around, and you're right, there is a cluttergst module. However it doesn't look like there is a deb for the latest version anywhere. Its not in the Karmic or Lucid repo's either from what I can see.

You could download and compile it [from here]("http://www.clutter-project.org/sources/") though if you wanted. Though, you might need to compile other libraries to get it to work.

---

### Post by Admiral Yi on 2010-05-09
Ah, thanks. I can't believe I didn't find that. I will try compiling.

---

### Post by Admiral Yi on 2010-05-09
Didn't work. I installed clutter, clutter-gst, pyclutter and pyclutter-gst and it still says there is no module called cluttergst. All the installs defiantly worked. Any other ideas?

---

### Post by steeleyuk on 2010-05-09
I think I've cracked it. I downloaded the version from the git repository with the command (sudo apt-get install git-core if you don't have git installed):

```
git clone git://git.clutter-project.org/bindings/pyclutter-gst
```

Once the clone has been made, cd to the directory pyclutter-gst and type:

```
./autogen.sh
make
sudo make install
```

The compile of the git-version worked fine for me, so it seems like a problem with the currently released packages. You can then import cluttergst.

---

### Post by Admiral Yi on 2010-05-09
Worked perfectly! Many thanks for you time, ill mark this as solved now.

---

### Post by Vids on 2010-06-26
I have the exact problem of not able to install pyclutter-gst module.

I tried the crack steeleyuk mentioned.
git clone git://git.clutter-project.org/bindings/pyclutter-gst
cd pyclutter-gst
./autogen.sh


Then I am getting the following error..

checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.9... not found.
  testing automake-1.10... not found.
  testing automake-1.11... not found.
***Error***: You must have automake >= 1.9 installed
  to build PyClutter-Gst.  Download the appropriate package for
  from your distribution or get the source tarball at
    [http://ftp.gnu.org/pub/gnu/automake/automake-1.9.tar.gz](http://ftp.gnu.org/pub/gnu/automake/automake-1.9.tar.gz)

checking for libtool >= 1.4.3...
  testing libtoolize... found 1.5.26
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
./autogen.sh: line 156: --print-ac-dir: command not found
ACLOCAL=
AUTOCONF=autoconf
AUTOCONF_VERSION=2.61
.......
.........
.........
Checking for required M4 macros...
  libtool.m4 not found
  pkg.m4 not found
Checking for forbidden M4 macros...
***Error***: some autoconf macros required to build PyClutter-Gst
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?


Any idea whats going wrong. 
Any help is appreciated.

Thanks~

---

### Post by Can+~ on 2010-06-26
Well, you actually got a very helpful tip there:

> ***Error***: You must have automake >= 1.9 installed
to build PyClutter-Gst. Download the appropriate package for
from your distribution or get the source tarball at

You lack automake, and I think automake comes with the basic build-essential package. Do you have [build-essential]("apt:build-essential") installed? If not, click on that link.

---

### Post by Vids on 2010-06-27
@Can+~ : Thanks. automake was the problem :)

 I have downloaded and installed clutter 1..0.0 , clutter-gst-0.10.0 and pycairo-1..0.0. Then when I try to install pyclutter-1..0.0 I get the following error.

cd pyclutter-1..0.0
./configure 

//this works fine

make

[I][SIZE=1]Could not write method ClutterBindingPool.override_closure: No ArgType for GClosure*
***INFO*** The coverage of global functions is 100.00% (48/48)
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

Any idea? And Is this pyclutter-gst module only compatible with the 1..0.0 version? When I install via sudo apt-get install I get a newer version of all the pacakages. Because of that I had to download the sources and install it manually. Is there a version that works with the latest one?

Thanks!!

---

### Post by Vids on 2010-06-27
@[Admiral Yi]("http://art.ubuntuforums.org/member.php?u=739644")

From where did you install pyclutter? Is it from source and which version
Thanks

---

### Post by powerclam on 2011-06-06
> **steeleyuk said:**
> I think I've cracked it. I downloaded the version from the git repository with the command (sudo apt-get install git-core if you don't have git installed):

```
git clone git://git.clutter-project.org/bindings/pyclutter-gst
```
Sadly, this no longer works, as the clutter project has moved its git repos to gnome.org.
[http://www.clutter-project.org/blogs/archive/2011-03/change-git-repositories-clutter](http://www.clutter-project.org/blogs/archive/2011-03/change-git-repositories-clutter)
and simple url-substitution doesn't lead where one might hope.
Any help with this would be greatly appreciated.

---


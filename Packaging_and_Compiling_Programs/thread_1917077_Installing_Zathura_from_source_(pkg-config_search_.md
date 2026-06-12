---
title: "Installing Zathura from source (pkg-config search path error)"
date: 2012-01-29
forum: Packaging and Compiling Programs
---

### Post by floydian_slip on 2012-01-29
Hi,

I'm trying to install the [djvu plugin]("http://doc.pwmt.org/zathura/plugins.html#djvu") for the document viewer [Zathura]("http://pwmt.org/projects/zathura/"), and I'm getting some errors. (Originally, I tried installing Zathura itself from source and got the same errors, then realized that there is a version of Zathura in the Ubuntu repositories, so I grabbed that, which works just fine but only for PDFs.)

So I downloaded the zathura-djvu folder (via git, as described on the site), and here's what happens when I cd into the directory and type "make":

```

brian@brian-pc:~/zathura-djvu$ make
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package ddjvuapi was not found in the pkg-config search path.
Perhaps you should add the directory containing `ddjvuapi.pc'
to the PKG_CONFIG_PATH environment variable
No package 'ddjvuapi' found
Package zathura was not found in the pkg-config search path.
Perhaps you should add the directory containing `zathura.pc'
to the PKG_CONFIG_PATH environment variable
No package 'zathura' found
Package girara-gtk2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `girara-gtk2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'girara-gtk2' found
djvu build options:
CFLAGS  = -std=c99 -fPIC -pedantic -Wall -Wno-format-zero-length    
LDFLAGS = 
DFLAGS  = -g
CC      = cc
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package ddjvuapi was not found in the pkg-config search path.
Perhaps you should add the directory containing `ddjvuapi.pc'
to the PKG_CONFIG_PATH environment variable
No package 'ddjvuapi' found
Package zathura was not found in the pkg-config search path.
Perhaps you should add the directory containing `zathura.pc'
to the PKG_CONFIG_PATH environment variable
No package 'zathura' found
Package girara-gtk2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `girara-gtk2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'girara-gtk2' found
CC djvu.c
djvu.c:4:35: fatal error: girara/datastructures.h: No such file or directory
compilation terminated.
make: *** [djvu.o] Error 1

```

I don't really have much experience with make, make install, etc., or with pkg-config, so I'm not quite sure what this all means. Thing is, since Zathura works fine, I must have most/all of the dependencies, so I'm not sure why it can't find things...

Any help would be greatly appreciated. Thanks!

Brian

---

### Post by oldos2er on 2012-01-29
Moved to Packaging and Compiling Programs.

---

### Post by floydian_slip on 2012-01-29
I've made some progress. I realized I needed to do (at least) the following things:

(1) add /usr/lib/pkgconfig to pkg-config search path. This is the directory that contains all the relevant .pc files. To do this, I edited my .profile file and added this line:

```

# Add /usr/lib/pkgconfig to PKG_CONFIG_PATH
PKG_CONFIG_PATH=/usr/lib/pkgconfig:$PKG_CONFIG_PATH; export PKG_CONFIG_PATH

```

Then to update that file I just restarted my computer, because I couldn't remember the command to update paths.

(2) install a bunch more developer files, including libgtk2.0-dev, libdjvulibre-dev, libpoppler-glib-dev, and libsqlite3-dev. Basically, any time it said it couldn't find a particular package, it's because I needed the developer files for that package.

(3) build and install both girara (GTK v. 2, not 3) and zathura from source before installing the djvu or pdf (poppler) plugins.

So in the end, after lots of trial and error, I acquired all the necessary dev files, then I installed girara from source (using GTK 2), then zathura from source, then the two plugins.

The program now works and can open pdf and djvu files. However, some things are buggy, e.g. tab completion doesn't work properly and zoom-to-width fails. But I think it's because when I run zathura from terminal, I get these errors:

```

brian@brian-pc:~$ zathura 
info: successfully loaded plugin /usr/lib/zathura/djvu.so
info: successfully loaded plugin /usr/lib/zathura/pdf.so
error: Could not open configuration file '/etc/xdg/zathurarc'
error: Could not open configuration file '/etc/xdg/zathurarc'
error: Could not open configuration file '/etc/xdg/xdg-xubuntu/zathurarc'
error: Could not open configuration file '/etc/zathurarc'
error: Could not open configuration file '/home/brian/.config/zathura/zathurarc'

```

Perhaps the zathura provided by the Ubuntu repository comes with a zathurarc config file that fixes the problems I'm currently having, whereas when building from source, there is no such file...

---

### Post by floydian_slip on 2012-01-29
By the way, I'd prefer to just use the zathura that Ubuntu's repository provides. But if I'm not mistaken, if you want djvu support, you need the djvu-plugin, which requires that you build zathura from source.

If there is a way to get djvu-plugin working for the repository version, I'd really like to know.

---


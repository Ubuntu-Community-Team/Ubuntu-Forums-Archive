---
title: "problems building gtk+-2.10.0"
date: 2007-02-08
forum: Programming Talk
---

### Post by Keith Hedger on 2007-02-08
I have run into problem building gtk+-2.10.0 from source, agter compiling and installing the various dependencies (GLIB,ATK,PANGO which work fine) I get undefined reference errors when building gtk, it seems to be looking in /usr/lib instead of /usr/local/lib (where I installed GLIB etc), I have set /etc/ld.so.conf and run ldconfig, readelf says the symbols are in GLIB in/usr/local/lib, I have tried setting various envs and configure options ie:

export LD_LIBRARY_PATH=/usr/local/lib
/configure --prefix=/usr/local (for GLIB)
./configure --prefix=/usr/local --with-glib-prefix=/usr/local (for GTK)

but still no joy I hope someone can help!

---

### Post by jblebrun on 2007-02-08
> **Keith Hedger said:**
> I have run into problem building gtk+-2.10.0 from source, agter compiling and installing the various dependencies (GLIB,ATK,PANGO which work fine) I get undefined reference errors when building gtk, it seems to be looking in /usr/lib instead of /usr/local/lib (where I installed GLIB etc), I have set /etc/ld.so.conf and run ldconfig, readelf says the symbols are in GLIB in/usr/local/lib, I have tried setting various envs and configure options ie:

export LD_LIBRARY_PATH=/usr/local/lib
/configure --prefix=/usr/local (for GLIB)
./configure --prefix=/usr/local --with-glib-prefix=/usr/local (for GTK)

but still no joy I hope someone can help!

Can you show us the actual errors that you're getting? Are you getting these errors during configure, or make?

---

### Post by Keith Hedger on 2007-02-08
The problem is at compile time not during configure, this is the bit that fails:

make[2]: Entering directory `/media/BackingStore/Glade3/gtk+-2.10.0/gtk'
/bin/sh ../libtool --mode=link gcc  -DG_DISABLE_DEPRECATED -g -O2 -Wall   -o gtk-query-immodules-2.0  queryimmodules.o libgtk-x11-2.0.la ../gdk-pixbuf/libgdk_pixbuf-2.0.la ../gdk/libgdk-x11-2.0.la
gcc -DG_DISABLE_DEPRECATED -g -O2 -Wall -o .libs/gtk-query-immodules-2.0 queryimmodules.o  ./.libs/libgtk-x11-2.0.so -L/usr/local/lib /media/BackingStore/Glade3/gtk+-2.10.0/gdk/.libs/libgdk-x11-2.0.so /usr/local/lib/libatk-1.0.so ../gdk-pixbuf/.libs/libgdk_pixbuf-2.0.so ../gdk/.libs/libgdk-x11-2.0.so /usr/lib/libpangocairo-1.0.so /usr/lib/libcairo.so /usr/lib/libpangoft2-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so /usr/lib/libglib-2.0.so /usr/local/lib/libpango-1.0.so /usr/local/lib/libcairo.so /usr/lib/libfreetype.so -lz -lpng12 -lfontconfig -lXext -lXrender -lX11 -lXinerama -lXrandr -lXcursor -lXfixes /media/BackingStore/Glade3/gtk+-2.10.0/gdk-pixbuf/.libs/libgdk_pixbuf-2.0.so /usr/local/lib/libgmodule-2.0.so -ldl /usr/local/lib/libgobject-2.0.so /usr/local/lib/libglib-2.0.so -lm -Wl,--rpath -Wl,/usr/local/lib
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_title'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_is_private'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_description'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_size'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_free'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_type_register_static_simple'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_pdf_surface_create'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_surface_set_fallback_resolution'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_load_from_file'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_visited'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_modified'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_key_file_set_double'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_mime_type'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_is_private'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_has_item'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_key_file_get_double'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_applications'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_ps_surface_set_size'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_uris'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_new'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_description'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_title'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_surface_get_type'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_to_file'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_add_group'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_pdf_surface_create_for_stream'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_add_application'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_remove_item'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_mime_type'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_move_item'
./.libs/libgtk-x11-2.0.so: undefined reference to `cairo_pdf_surface_set_size'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_groups'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_app_info'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_added'
collect2: ld returned 1 exit status

if you look at the top bit closely you can see that it is trying to link to the various libs (CAIRO,GLIB etc) in /usr/lib instead of /usr/local/lib which seems to be where the error is but I cant see any way of getting the makefiles to do it the other way around.

---

### Post by Keith Hedger on 2007-02-11
Well I sorted it out it seems the problem was in ltmain.sh which builds libtool at configure time (debugging auto generateds scripts is a nightmare of biblical proportions!), unfortunatly th .am files needed to build ltmain via automake were not in the archive so I dont know if the problem is with automake or gtk but glade3 had the same problem, oh well! got everything compiled and running now:)

---

### Post by hotpoo on 2007-04-03
Keith,
    I'm running into the exact same issue myself, but I'm a bit confused about your solution. Would you mind explaining what you did to resolve this?

Bill

---

### Post by hotpoo on 2007-04-04
Nevermind. :-) I finally got it working. I installed FreeType, removed/reinstalled pango, ran ldconfig, then was finally able to get gtk to compile with no errors. Huzzah!

Bill

---

### Post by Keith Hedger on 2007-04-05
Hi
Sorry about the delay in replying but I got a bit of grit in my eye and have been off the computer, anyway...

I'm doing this from memory so bear with me! The script that builds libtool which actually links the library does not seem to properly take account of the prefix variable passed to  configure,
ie it looks in /usr/lib etc BEFORE looking in /$prefix/lib which means that it finds the standard libs first,
 so I hacked the ltmain.sh script to make sure it looks in /$prefix first, this was a long job and I wont go into details, 
 so I have affixed the ltmain.sh file to this post, just unpack it and drop it int your gtk folder then rerun configure, 
 I also had to use this script to build glade 3,(which was why I was building gtk in the first place).
 If you need to tweak the changes I have made to the script I have marked them with #XXXXX just do a search in your text editor.
 I keep development packages well out of the usual system seach paths and use a script to setup the enviroment first, you may want to do the same.
 I use this script placed in /usr/local/bin (dont forget to make it executable and change the location of your development folder)

#|/bin/bash

DEVPREFIX=/media/BackingStore/development/local

LD_LIBRARY_PATH="$DEVPREFIX/lib:/usr/local/lib:/usr/lib:$LD_LIBRARY_PATH"
PKG_CONFIG_PATH="$DEVPREFIX/lib/pkgconfig:/usr/local/lib/pkgconfig:/usr/lib/pkgconfig:$PKG_CONFIG_PATH"
PATH="$DEVPREFIX/bin/:$PATH"

export LD_LIBRARY_PATH PKG_CONFIG_PATH PATH
exec "$@"

Then I use (for instance) devtool ./configure --prefix=$DEVPREFIX to run the configure script (DEVPREFIX) is set in my bashrc file.

Hope this fixes your problem, sorry for being so long winded.

P.S
Got this post ready to go then saw your last post glad you got it sorted but I thought I'd post this any way incase someone else had trouble.

---

### Post by anupamsr on 2007-06-27
--- Is not working ---

---


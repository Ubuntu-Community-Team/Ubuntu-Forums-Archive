---
title: "Where is GTK for Ubuntu 8.04?"
date: 2008-09-13
forum: Programming Talk
---

### Post by resander on 2008-09-13
From an Ubuntu newbie on 8.04.

My first step is to find the header files, e.g. gtk.h, for the demo programs in the tutorial at gtk.org. No luck so far after hours of searching and looking at forum posts. 

I used the Synaptic Manager with search key 'gtk' but could not find the gtk package. I found packages with libgfc in the name, for example libgfcui-dev and installed these. Searching on gtk.h using Search for Files in the Places menu gave no matches. However, many files ending in .hh showed up in usr/include/gfc-2.0/gfc/gtk. These were C++ definitions.

How can I find the .h header files for the C demo programs and corresponding static libraries?

---

### Post by Perfect Storm on 2008-09-13
```
sudo apt-get install libgtk2.0-dev
```

/usr/include/gtk-2.0/gtk/gtk.h

---

### Post by resander on 2008-09-13
Many thanks!

Thats'it! Now the demo program works fine in the code::blocks IDE.

BUT, why couldn't I find GTK using the synaptic manager? What should I have used to find it? Of course these are not programming questions, but may help other newcomers from the Windows programming world, so I am asking here?

Aterigen, ett stort tack.

---

### Post by WitchCraft on 2008-09-13
> **resander said:**
> Many thanks!

Thats'it! Now the demo program works fine in the code::blocks IDE.

BUT, why couldn't I find GTK using the synaptic manager? What should I have used to find it? Of course these are not programming questions, but may help other newcomers from the Windows programming world, so I am asking here?

Aterigen, ett stort tack.

apt-get install apt-file
apt-file update

apt-file search gtk.h
> 
all:~# apt-file search gtk.h
bibledit: /usr/share/bibledit/gtk.html
ebook-dev-ggad: /usr/share/doc/ebook-dev-ggad/html/cha-gtk.html
gambas2-doc: /usr/share/gambas2/help/help/comp/gb+gtk.html
gnome-dev-doc: /usr/share/doc/gnome-dev-doc/html/C/orbitgtk.html
libcairo-ocaml-dev: /usr/share/doc/libcairo-ocaml-dev/html/Cairo_lablgtk.html
libcairo-ocaml-dev: /usr/share/doc/libcairo-ocaml-dev/html/type_Cairo_lablgtk.html
libcanberra-doc: /usr/share/gtk-doc/html/libcanberra/libcanberra-canberra-gtk.html
libcanberra-gtk-dev: /usr/include/canberra-gtk.h
libclaws-mail-dev: /usr/include/claws-mail/imap_gtk.h
libclaws-mail-dev: /usr/include/claws-mail/mh_gtk.h
libclaws-mail-dev: /usr/include/claws-mail/news_gtk.h
libclaws-mail-dev: /usr/include/claws-mail/prefs_gtk.h
libdebconfclient0-dev: /usr/include/cdebconf/cdebconf_gtk.h
libgalago-gtk-dev: /usr/include/libgalago-gtk/galago-gtk.h
libgfcui-dev: /usr/include/gfc-2.0/gfc/gtk/gtk.hh
libggz-gtk-dev: /usr/include/ggz-gtk.h
libginspx-dev: /usr/include/ginspector/ginspector-gtk.h
libgladeui-1-dev: /usr/include/libgladeui-1.0/gladeui/glade-gtk.h
libglrr-gtk-dev: /usr/include/glrr-gtk/glrr-gtk.h
libgoffice-0-6-dev: /usr/include/libgoffice-0.6/goffice/gtk/goffice-gtk.h
libgoffice-0-dev: /usr/include/libgoffice-0.4/goffice/gtk/goffice-gtk.h
**libgtk1.2-dev: /usr/include/gtk-1.2/gtk/gtk.h**
libgtk2-ruby1.8: /usr/lib/ruby/1.8/i486-linux/rbgtk.h
**libgtk2.0-dev: /usr/include/gtk-2.0/gtk/gtk.h**
**libgtk2.0-doc: /usr/share/doc/libgtk2.0-doc/gtk/gtk.html**
libguilegtk-1.2-dev: /usr/include/guile-gtk.h
liblablgtk2-ocaml-dev: /usr/lib/ocaml/3.10.2/lablgtk2/ml_gtk.h
liblua5.1-gtk-dev: /usr/share/doc/liblua5.1-gtk-dev/reference/modules/gtk.http_co.html
libmorph-dev: /usr/include/xmorph/warp-gtk.h
libocamlnet-ocaml-doc: /usr/share/doc/libocamlnet-ocaml-doc/html-main/Uq_gtk.html
libocamlnet-ocaml-doc: /usr/share/doc/libocamlnet-ocaml-doc/html-main/type_Uq_gtk.html
libogmrip-dev: /usr/include/ogmdvd/ogmdvd-gtk.h
libogmrip-dev: /usr/include/ogmrip/ogmrip-gtk.h
libpigment0.3-dev: /usr/include/pigment-0.3/pgm/gtk/pgmgtk.h
libswfdec-0.6-dev: /usr/include/swfdec-0.6/swfdec-gtk/swfdec-gtk.h
libtracker-gtk-dev: /usr/include/libtracker-gtk/tracker-gtk.h
lsb-build-desktop3: /usr/include/lsb3/gtk-2.0/gtk/gtk.h
pike7.6-reference: /usr/share/doc/pike7.6-doc/html/reference/ex/predef_3A_3A/GTK/setup_gtk.html
python-gtk2-dev: /usr/include/pygtk-2.0/pygtk/pygtk.h
python-gtk2-dev: /usr/include/python2.4/pygtk-2.0/pygtk/pygtk.h
r-cran-rgtk2: /usr/lib/R/site-library/RGtk2/include/RGtk2/gtk.h
scilab-doc: /usr/lib/scilab-4.1.2/man/eng/utilities/with_gtk.htm
scilab-doc: /usr/lib/scilab-4.1.2/man/fr/utilities/with_gtk.htm
wx2.6-headers: /usr/include/wx-2.6/wx/gtk/tbargtk.h
wx2.6-headers: /usr/include/wx-2.6/wx/gtk/win_gtk.h
wx2.8-headers: /usr/include/wx-2.8/wx/gtk/assertdlg_gtk.h
wx2.8-headers: /usr/include/wx-2.8/wx/gtk/tbargtk.h
wx2.8-headers: /usr/include/wx-2.8/wx/gtk/treeentry_gtk.h
wx2.8-headers: /usr/include/wx-2.8/wx/gtk/win_gtk.h
xdialog: /usr/share/doc/xdialog/html/gtk.html
xemacs21-bin: /usr/lib/xemacs-21.4.21/i486-linux-gnu/include/console-gtk.h
xemacs21-bin: /usr/lib/xemacs-21.4.21/i486-linux-gnu/include/gccache-gtk.h
xemacs21-bin: /usr/lib/xemacs-21.4.21/i486-linux-gnu/include/glyphs-gtk.h
xemacs21-bin: /usr/lib/xemacs-21.4.21/i486-linux-gnu/include/gui-gtk.h
xemacs21-bin: /usr/lib/xemacs-21.4.21/i486-linux-gnu/include/objects-gtk.h
xemacs21-bin: /usr/lib/xemacs-21.4.21/i486-linux-gnu/include/scrollbar-gtk.h
xemacs21-bin: /usr/lib/xemacs-21.4.21/i486-linux-gnu/include/ui-gtk.h


alternative: 
apt-get update
apt-cache search libgtk | grep "\-dev"
> 
all:~# apt-cache search libgtk | grep "\-dev"
libgtk-directfb-2.0-dev - Development files for the GTK+ library - DirectFB version
libgtk-java-dev - Java bindings for GTK+ (development files)
libgtk-vnc-1.0-dev - A VNC viewer widget for GTK+ (development files)
[B]libgtk1.2-dev - Development files for the GIMP Toolkit
libgtk2.0-dev - Development files for the GTK+ library[/B]
libgtkada2-dev - Development files for libgtkada2
libgtkdatabox-0.9.0-0-dev - A Gtk+ library to display large amounts of numerical data
libgtkextra-dev - A useful set of widgets for GTK+ (development files)
libgtkextra-x11-2.0-dev - A useful set of widgets for GTK+ (development files)
libgtkgl2.0-dev - OpenGL area for GTK (development files)
libgtkglext1-dev - OpenGL Extension to GTK+ (development files)
libgtkglextmm-x11-1.2-dev - C++ bindings for GtkGLExt (Development files)
libgtkhex0-dev - GNOME Hex editor for files (development headers)
libgtkhtml2-dev - HTML rendering/editing library - development files
libgtkhtml3.14-dev - HTML rendering/editing library - development files
libgtkhtml3.8-dev - HTML rendering/editing library - development files
libgtkimageview-dev - image viewer widget for GTK+ (development files)
libgtkimreg-dev - GTK+ widget to select regions of GdkImages
libgtkmathview-dev - rendering engine for MathML documents
libgtkmm-2.4-dev - C++ wrappers for GTK+ 2.4 (development files)
libgtkmm-dev - C++ wrapper for GTK+ 1.2 (development files)
libgtkol0-dev - GTK+ C++ Object Layer - development files
libgtksourceview-dev - development files for the GTK+ syntax highlighting widget
libgtksourceview2.0-dev - development files for the GTK+ syntax highlighting widget
libgtksourceviewmm-2.0-dev - C++ binding of GtkSourceView - development files
libgtkspell-dev - Development files for GtkSpell
libgtkxmhtml-dev - The GNOME gtkxmhtml (HTML) widget -- development package
liblablgtkmathview-ocaml-dev - OCaml bindings for libgtkmathview, a GTK widget to render MathML
liblablgtksourceview-ocaml-dev - OCaml bindings for libgtksourceview, a source editor GTK+ widget


---


---
title: "GLADE Problems"
date: 2005-11-29
forum: Programming Talk
---

### Post by blanky on 2005-11-29
*Posted this in LinuxQuestion.Org first, but it didn't get replies, hopefully someone here can help :)*

Hey guys, after looking at WxWidgets, QT, etc., I thought I'd try GLADE. I downloaded build-essential, glade, and all other stuff that it needed (the dependencies were handled and I didn't see/forgot). Everything runs fine, I just made a window (didn't rename) and a fixed position widget, and I made a button, not altering any of them from the defaults. Now, when I build code, (I've tried C and C++), everything seems to go alright. After, I go into the directory and do **./autogen.sh**. First it had a lot of errors, now, most of them are fixed since I downloaded a library that was -dev or something, I think it was glib-dev, or something else, some were solved. It's just an error that says GTK didn't meet requirements, but apparently I have the latest GTK (I think). Sorry guys, I'm very new to programming in linux, here's the output I get:

> 
jorge@blankpc:~/Projects/test$ sh ./autogen.sh
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running glib-gettextize...  Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
(gnu ftp site, censored cause I have less than 5 posts, not allowed to show URLs).

Making ./aclocal.m4 writable ...
Running aclocal  ...
Running autoheader...
Running automake --gnu  ...
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./missing'
automake: configure.in: installing `./config.guess'
automake: configure.in: installing `./config.sub'
automake: Makefile.am: installing `./INSTALL'
automake: Makefile.am: installing `./COPYING'
Running autoconf ...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.0.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the PACKAGE_CFLAGS and PACKAGE_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.


Sorry for the long quote, but I think everything helps. I appreciate any help I get, thanks.

---

### Post by doclivingston on 2005-11-30
[quote=blanky]Package requirements (gtk+-2.0 >= 2.0.0) were not met.[/quote]

This means that you need to install the GTK development libraries - from memory the package is called libgtk2-dev or similar.

---

### Post by blanky on 2005-11-30
Thanks bud! I'll try that as soon as I can, I already installed some/one of the dev I think I hope its not that or the problem would be something else, I'm gonna try, thanks!

---

### Post by dj961 on 2005-11-30
Dont use the code generation feature in glade, it's broken and will be removed in future versions

---

### Post by blanky on 2005-11-30
oh really? Um..okay, then what should I use? Thanks for the help.

---

### Post by dj961 on 2005-11-30
libglade
[http://www.jamesh.id.au/software/libglade/](http://www.jamesh.id.au/software/libglade/)
[http://developer.gnome.org/doc/API/2.0/libglade/index.html](http://developer.gnome.org/doc/API/2.0/libglade/index.html)

---

### Post by blanky on 2005-11-30
Thanks, I'll get them, but how do I integrate it with GLADE? I mean, can I even still use GLADE for the WYSIWYG part of creating the window? Then export to XML? If so, how would I go about integrating libglade with this, or does it does it by itself when I install.

---

### Post by doclivingston on 2005-11-30
The code-generation part of glade is deprecated, and using libglade is much nicer. What you do is create some UI in glade and then save it as a .glade file (which is xml).

[http://developer.gnome.org/doc/API/2.0/libglade/GladeXML.html](http://developer.gnome.org/doc/API/2.0/libglade/GladeXML.html)


Then you use the libglade calls like this:

```
GladeXML *xml = glade_xml_new ("file.glade", "widget_name", translation_domain);
```

Will load the glade file "file.glade" and construct the UI from "widget_name" down. If you have created an entire window in Glade, just pass it's name. If you want to create a menu, or some widgets to put somewhere, you have to put them in a window in the Glade UI builder - but you pass the name of the widget you want, and it won't create the window.

If you don't know much about i18n yet, just pass NULL for the translation domain and deal with it later.


```
GtkWidget *widget = glade_xml_get_widget (xml, "widget_name");
```
will give you a widget inside the UI that has been loaded. This is useful if you've create a window, and you need to access certain widget inside it.



You can connect glade signals to functions, so that things are run when you press buttons, etc.

You can do this manually by using one of the following, where "signal-name" is whetever you entered into Glade
```
glade_xml_construct (xml, "signal-name", (GCallback) callback);
glade_xml_signal_connect_data (xml, "signal-name", (GCallback) callback, userdata);
```

You can also have this automatically, and glade will connect signals and functions of the same name
```
glade_xml_signal_autoconnect (xml);
```

---

### Post by blanky on 2005-12-01
Thanks, that's really helpful. However, is there anyway to still use WYSIWYG drawing of the window? And somehow expert to XML? The WYSIWYG is mainly what got me interested in GTK, lol, didn't like QT. If not then I guess that's allright, I'll try and learn it that way.

---

### Post by dj961 on 2005-12-01
Yeah, you draw your GUI in glade(wysiwyg) and load the resulting *something*.glade(its an XML file) file into you program with libglade(as described above)
EDIT:Ugh I just realised I'm repeating what doclivingston said.

---

### Post by blanky on 2005-12-01
Thanks! At least you clarified :) Thanks thanks thanks! :D

---


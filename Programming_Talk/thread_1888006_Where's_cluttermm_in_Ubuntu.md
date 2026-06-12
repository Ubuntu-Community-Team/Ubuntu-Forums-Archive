---
title: "Where's cluttermm in Ubuntu?"
date: 2011-11-28
forum: Programming Talk
---

### Post by t1497f35 on 2011-11-28
Hi,
The cluttermm docs say I need to install libcluttermm-1.0-dev on Ubuntu but Ubuntu (11.10) tells me there's no such package. There's no cluttermm package at all.
Can anyone enlighten me please what's up? Googling "cluttermm on Ubuntu" yields no info.

---

### Post by ehmicky on 2011-11-28
Hi,
I didn't find any GNU/Linux package either. If you don't find it, you can still compile from [source](http://ftp.gnome.org/pub/GNOME/sources/cluttermm/1.3/)

---

### Post by MG&amp;TL on 2011-11-28
Gtk = GNOME graphical widgets/libs for GNOME, in C.

gtkmm = GNOME Gtk wrapper for C++.

Therfore I guess:

clutter = GNOME3/shell widgets/libs/window manager code

cluttermm = GNOME3 C++ wrapper.

I guess it hasn't made it yet into repos. I think you can probably use the C ones :confused:

---

### Post by t1497f35 on 2011-11-28
@[ehmicky]("http://ubuntuforums.org/member.php?u=1494126")
Thanks, I already did that and installed it, but that's useless, cause when compiling a test app it yields errors. I Googled around how to fix it but couldn't find an answer so I gave up. Hopefully Ubuntu 12.04 will feature clutter in the repos.

The test app that doesn't compile is [here]("http://www.openismus.com/documents/cluttermm_tutorial/1.0/docs/tutorial/html/sec-stage.html"), and the errors say:

```

g++ -Wall -g `pkg-config --cflags --libs cluttermm-1.0` -o example main.cc
/tmp/ccZox84x.o: In function `on_stage_button_press':
/home/fox/main.cc:29: undefined reference to `clutter_event_get_coords'
/tmp/ccZox84x.o: In function `main':
/home/fox/main.cc:42: undefined reference to `Clutter::init(int*, char***)'
/home/fox/main.cc:45: undefined reference to `Clutter::Stage::get_default()'
/home/fox/main.cc:46: undefined reference to `Clutter::Actor::set_size(float, float)'
/home/fox/main.cc:47: undefined reference to `Clutter::Color::Color(unsigned char, unsigned char, unsigned char, unsigned char)'
/home/fox/main.cc:47: undefined reference to `Clutter::Stage::set_color(Clutter::Color const&)'
/home/fox/main.cc:47: undefined reference to `Clutter::Color::~Color()'
/home/fox/main.cc:49: undefined reference to `Clutter::Actor::show()'
/home/fox/main.cc:52: undefined reference to `Clutter::Actor::signal_button_press_event()'
/home/fox/main.cc:52: undefined reference to `sigc::connection::~connection()'
/home/fox/main.cc:55: undefined reference to `Clutter::main()'
/home/fox/main.cc:47: undefined reference to `Clutter::Color::~Color()'
/home/fox/main.cc:59: undefined reference to `Glib::ustring::~ustring()'
/home/fox/main.cc:59: undefined reference to `Glib::operator<<(std::basic_ostream<char, std::char_traits<char> >&, Glib::ustring const&)'
/home/fox/main.cc:59: undefined reference to `Glib::ustring::~ustring()'
/tmp/ccZox84x.o: In function `slot_rep':
/usr/include/sigc++-2.0/sigc++/functors/slot_base.h:84: undefined reference to `sigc::trackable::trackable()'
/tmp/ccZox84x.o: In function `~slot_rep':
/usr/include/sigc++-2.0/sigc++/functors/slot_base.h:87: undefined reference to `sigc::trackable::~trackable()'
/usr/include/sigc++-2.0/sigc++/functors/slot_base.h:87: undefined reference to `sigc::trackable::~trackable()'
/tmp/ccZox84x.o:(.gcc_except_table+0x64): undefined reference to `typeinfo for Glib::Error'
/tmp/ccZox84x.o: In function `~SignalProxy1':
/usr/include/glibmm-2.4/glibmm/signalproxy.h:168: undefined reference to `Glib::SignalProxyNormal::~SignalProxyNormal()'
/tmp/ccZox84x.o: In function `~slot1':
/usr/include/sigc++-2.0/sigc++/functors/slot.h:493: undefined reference to `sigc::slot_base::~slot_base()'
/tmp/ccZox84x.o: In function `Glib::SignalProxy1<bool, _ClutterButtonEvent*>::connect(sigc::slot<bool, _ClutterButtonEvent*, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil> const&, bool)':
/usr/include/glibmm-2.4/glibmm/signalproxy.h:184: undefined reference to `Glib::SignalProxyNormal::connect_(sigc::slot_base const&, bool)'
/usr/include/glibmm-2.4/glibmm/signalproxy.h:184: undefined reference to `sigc::connection::connection(sigc::slot_base&)'
/tmp/ccZox84x.o: In function `slot1<bool (*)(_ClutterButtonEvent*)>':
/usr/include/sigc++-2.0/sigc++/functors/slot.h:526: undefined reference to `sigc::slot_base::slot_base(sigc::internal::slot_rep*)'
collect2: ld returned 1 exit status


```

---

### Post by ehmicky on 2011-11-28
What's the output of pkg-config --libs --cflags cluttermm-1.0 ?

---

### Post by t1497f35 on 2011-11-28
Here it is:
> 
fox@fox:~$ echo `pkg-config --libs --cflags cluttermm-1.0`
-pthread -I/usr/local/include/cluttermm-1.0 -I/usr/local/lib/cluttermm-1.0/include -I/usr/include/clutter-1.0 -I/usr/include/cogl -I/usr/include/cairo -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/libdrm -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/pangomm-1.4 -I/usr/lib/pangomm-1.4/include -I/usr/include/atkmm-1.6 -I/usr/include/json-glib-1.0 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -pthread -L/usr/local/lib -lcluttermm-1.0 -lclutter-glx-1.0 -lpangomm-1.4 -latkmm-1.6 -lcairo-gobject -lcogl-pango -ljson-glib-1.0 -lGL -lpangoft2-1.0 -lXi -lcogl -lgdk_pixbuf-2.0 -ldrm -lX11 -lXext -lXdamage -lXcomposite -lgio-2.0 -lfreetype -lfontconfig -lXfixes -lcairomm-1.0 -lpangocairo-1.0 -lpango-1.0 -lcairo -lgmodule-2.0 -latk-1.0 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lgthread-2.0 -lrt -lglib-2.0


Do you also use Ubuntu 11.10? Does it compile on your computer?

---

### Post by bluexrider on 2011-11-28
I don't know where you google goes but mine says

[http://www.ubuntuupdates.org/packages/show/357423](http://www.ubuntuupdates.org/packages/show/357423)

---

### Post by t1497f35 on 2011-11-28
> **bluexrider said:**
> I don't know where you google goes but mine says

[http://www.ubuntuupdates.org/packages/show/357423](http://www.ubuntuupdates.org/packages/show/357423)

We're talking here about cluttermm (the C++ backend).

---

### Post by bluexrider on 2011-11-28
right then, thanks

---

### Post by ehmicky on 2011-11-28
There's something weird : you compile with the flag -lglibmm-2.4, but it complains about not finding the symbols for Glib::ustring. What's the output of :
```
ls -l /usr/lib/lib*mm*
```

---

### Post by t1497f35 on 2011-11-28
I checked, libglibmm-2.4-dev was/is installed, ls -l /usr/lib/lib*mm* yields:

> 
fox@fox:~$ ls -l /usr/lib/lib*mm*
-rw-r--r-- 1 root root     967 2011-05-02 12:36 /usr/lib/libatkmm-1.6.la
lrwxrwxrwx 1 root root      21 2011-05-02 12:36 /usr/lib/libatkmm-1.6.so -> libatkmm-1.6.so.1.1.0
lrwxrwxrwx 1 root root      21 2011-10-09 01:37 /usr/lib/libatkmm-1.6.so.1 -> libatkmm-1.6.so.1.1.0
-rw-r--r-- 1 root root  302888 2011-05-02 12:36 /usr/lib/libatkmm-1.6.so.1.1.0
-rw-r--r-- 1 root root  246280 2011-05-25 17:33 /usr/lib/libcairomm-1.0.a
-rw-r--r-- 1 root root     986 2011-05-25 17:33 /usr/lib/libcairomm-1.0.la
lrwxrwxrwx 1 root root      23 2011-05-25 17:33 /usr/lib/libcairomm-1.0.so -> libcairomm-1.0.so.1.4.0
lrwxrwxrwx 1 root root      23 2011-10-09 01:37 /usr/lib/libcairomm-1.0.so.1 -> libcairomm-1.0.so.1.4.0
-rw-r--r-- 1 root root  144064 2011-05-25 17:33 /usr/lib/libcairomm-1.0.so.1.4.0
lrwxrwxrwx 1 root root      21 2011-08-22 11:32 /usr/lib/libgdkmm-2.4.so.1 -> libgdkmm-2.4.so.1.1.0
-rw-r--r-- 1 root root  310136 2011-08-22 11:33 /usr/lib/libgdkmm-2.4.so.1.1.0
lrwxrwxrwx 1 root root      21 2011-09-28 08:48 /usr/lib/libgdkmm-3.0.so -> libgdkmm-3.0.so.1.1.0
lrwxrwxrwx 1 root root      21 2011-10-09 01:37 /usr/lib/libgdkmm-3.0.so.1 -> libgdkmm-3.0.so.1.1.0
-rw-r--r-- 1 root root  251816 2011-09-28 08:48 /usr/lib/libgdkmm-3.0.so.1.1.0
-rw-r--r-- 1 root root 2019074 2011-09-28 07:08 /usr/lib/libgiomm-2.4.a
-rw-r--r-- 1 root root     953 2011-09-28 07:08 /usr/lib/libgiomm-2.4.la
lrwxrwxrwx 1 root root      21 2011-09-28 07:08 /usr/lib/libgiomm-2.4.so -> libgiomm-2.4.so.1.3.0
lrwxrwxrwx 1 root root      21 2011-10-09 01:37 /usr/lib/libgiomm-2.4.so.1 -> libgiomm-2.4.so.1.3.0
-rw-r--r-- 1 root root 1042552 2011-09-28 07:08 /usr/lib/libgiomm-2.4.so.1.3.0
-rw-r--r-- 1 root root  758550 2011-09-28 07:08 /usr/lib/libglibmm-2.4.a
-rw-r--r-- 1 root root     960 2011-09-28 07:08 /usr/lib/libglibmm-2.4.la
lrwxrwxrwx 1 root root      22 2011-09-28 07:08 /usr/lib/libglibmm-2.4.so -> libglibmm-2.4.so.1.3.0
lrwxrwxrwx 1 root root      22 2011-10-09 01:37 /usr/lib/libglibmm-2.4.so.1 -> libglibmm-2.4.so.1.3.0
-rw-r--r-- 1 root root  418120 2011-09-28 07:08 /usr/lib/libglibmm-2.4.so.1.3.0
-rw-r--r-- 1 root root   24980 2011-09-28 07:08 /usr/lib/libglibmm_generate_extra_defs-2.4.a
-rw-r--r-- 1 root root    1100 2011-09-28 07:08 /usr/lib/libglibmm_generate_extra_defs-2.4.la
lrwxrwxrwx 1 root root      42 2011-09-28 07:08 /usr/lib/libglibmm_generate_extra_defs-2.4.so -> libglibmm_generate_extra_defs-2.4.so.1.3.0
lrwxrwxrwx 1 root root      42 2011-10-09 01:37 /usr/lib/libglibmm_generate_extra_defs-2.4.so.1 -> libglibmm_generate_extra_defs-2.4.so.1.3.0
-rw-r--r-- 1 root root   18752 2011-09-28 07:08 /usr/lib/libglibmm_generate_extra_defs-2.4.so.1.3.0
lrwxrwxrwx 1 root root      21 2011-08-22 11:32 /usr/lib/libgtkmm-2.4.so.1 -> libgtkmm-2.4.so.1.1.0
-rw-r--r-- 1 root root 4560584 2011-08-22 11:33 /usr/lib/libgtkmm-2.4.so.1.1.0
lrwxrwxrwx 1 root root      21 2011-09-28 08:48 /usr/lib/libgtkmm-3.0.so -> libgtkmm-3.0.so.1.1.0
lrwxrwxrwx 1 root root      21 2011-10-09 01:37 /usr/lib/libgtkmm-3.0.so.1 -> libgtkmm-3.0.so.1.1.0
-rw-r--r-- 1 root root 4799256 2011-09-28 08:48 /usr/lib/libgtkmm-3.0.so.1.1.0
lrwxrwxrwx 1 root root      15 2011-05-02 07:21 /usr/lib/libmms.so.0 -> libmms.so.0.0.2
-rw-r--r-- 1 root root   63936 2011-05-02 07:21 /usr/lib/libmms.so.0.0.2
-rw-r--r-- 1 root root   39544 2011-10-14 11:46 /usr/lib/libnepomukcommon.so
-rw-r--r-- 1 root root     981 2011-07-27 18:47 /usr/lib/libpangomm-1.4.la
lrwxrwxrwx 1 root root      24 2011-07-27 18:47 /usr/lib/libpangomm-1.4.so -> libpangomm-1.4.so.1.0.30
lrwxrwxrwx 1 root root      24 2011-10-09 01:37 /usr/lib/libpangomm-1.4.so.1 -> libpangomm-1.4.so.1.0.30
-rw-r--r-- 1 root root  176936 2011-07-27 18:47 /usr/lib/libpangomm-1.4.so.1.0.30


Note, libgtkmm-2.4-dev was not installed (only gtkmm 3 dev), but after installing it nothing changed.

---

### Post by ehmicky on 2011-11-28
Oops, I forgot : what about :
```
ls -l /usr/local/lib/*
```
since you compiled from source.

---

### Post by t1497f35 on 2011-11-28
ls -l /usr/local/lib/* says:

> 
fox@fox:~$ ls -l /usr/local/lib/*
-rwxr-xr-x 1 root root     1795 2011-11-28 18:25 /usr/local/lib/libcluttermm-1.0.la
lrwxrwxrwx 1 root root       25 2011-11-28 18:25 /usr/local/lib/libcluttermm-1.0.so -> libcluttermm-1.0.so.1.0.0
lrwxrwxrwx 1 root root       25 2011-11-28 18:25 /usr/local/lib/libcluttermm-1.0.so.1 -> libcluttermm-1.0.so.1.0.0
-rwxr-xr-x 1 root root  4008988 2011-11-28 18:25 /usr/local/lib/libcluttermm-1.0.so.1.0.0

/usr/local/lib/cluttermm-1.0:
total 4
drwxr-xr-x 2 root root 4096 2011-11-28 18:25 include

/usr/local/lib/pkgconfig:
total 4
-rw-r--r-- 1 root root 651 2011-11-28 18:25 cluttermm-1.0.pc

/usr/local/lib/python2.7:
total 8
drwxrwsr-x 2 root staff 4096 2011-10-07 20:49 dist-packages
drwxrwsr-x 2 root staff 4096 2011-10-07 20:49 site-packages

/usr/local/lib/python3.2:
total 4
drwxrwsr-x 2 root staff 4096 2011-10-09 02:26 dist-packages



/usr/local/lib/pkgconfig/cluttermm.pc contains:

> 
prefix=/usr/local
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
datarootdir=${prefix}/share
datadir=${datarootdir}
includedir=${prefix}/include

gmmprocdir=${datadir}/cluttermm-1.0/proc
docdir=${datarootdir}/doc/cluttermm-1.0
doxytagfile=${docdir}/reference/cluttermm-1.0.tag
htmlrefdir=${docdir}/reference/html
htmlrefpub=http://library.gnome.org/devel/cluttermm/unstable/

Name: cluttermm
Description: C++ binding for clutter
Version: 1.3.3
URL: [http://www.gtkmm.org/](http://www.gtkmm.org/)
Requires: clutter-1.0 >= 1.3.8 pangomm-1.4 >= 2.27.1 atkmm-1.6 >= 2.22.2
Libs: -L${libdir} -lcluttermm-1.0
Cflags: -I${includedir}/cluttermm-1.0 -I${libdir}/cluttermm-1.0/include



---

### Post by SevenMachines on 2011-11-28
Ubuntu uses passes --as-needed by default to the compiler now, many a thread in the compiling forums about this. Short version, you need to put the linking after the source,

ie, bad...
```
$ g++ -Wall -g `pkg-config --cflags --libs cluttermm-1.0` -o example main.cc
/tmp/ccyZEdIP.o: In function `on_stage_button_press':
/home/seven/Desktop/temp/main.cc:29: undefined reference to `clutter_event_get_coords'
/tmp/ccyZEdIP.o: In function `main':
/home/seven/Desktop/temp/main.cc:42: undefined reference to `Clutter::init(int*, char***)'
/home/seven/Desktop/temp/main.cc:45: undefined reference to `Clutter::Stage::get_default()'
/home/seven/Desktop/temp/main.cc:46: undefined reference to `Clutter::Actor::set_size(float, float)'
/home/seven/Desktop/temp/main.cc:47: undefined reference to `Clutter::Color::Color(unsigned char, unsigned char, unsigned char, unsigned char)'
/home/seven/Desktop/temp/main.cc:47: undefined reference to `Clutter::Stage::set_color(Clutter::Color const&)'
/home/seven/Desktop/temp/main.cc:47: undefined reference to `Clutter::Color::~Color()'
/home/seven/Desktop/temp/main.cc:49: undefined reference to `Clutter::Actor::show()'
/home/seven/Desktop/temp/main.cc:52: undefined reference to `Clutter::Actor::signal_button_press_event()'
/home/seven/Desktop/temp/main.cc:52: undefined reference to `sigc::connection::~connection()'
/home/seven/Desktop/temp/main.cc:55: undefined reference to `Clutter::main()'
/home/seven/Desktop/temp/main.cc:47: undefined reference to `Clutter::Color::~Color()'
/home/seven/Desktop/temp/main.cc:59: undefined reference to `Glib::ustring::~ustring()'
/home/seven/Desktop/temp/main.cc:59: undefined reference to `Glib::operator<<(std::basic_ostream<char, std::char_traits<char> >&, Glib::ustring const&)'
/home/seven/Desktop/temp/main.cc:59: undefined reference to `Glib::ustring::~ustring()'
/tmp/ccyZEdIP.o: In function `slot_rep':
/usr/include/sigc++-2.0/sigc++/functors/slot_base.h:84: undefined reference to `sigc::trackable::trackable()'
/tmp/ccyZEdIP.o: In function `~slot_rep':
/usr/include/sigc++-2.0/sigc++/functors/slot_base.h:87: undefined reference to `sigc::trackable::~trackable()'
/usr/include/sigc++-2.0/sigc++/functors/slot_base.h:87: undefined reference to `sigc::trackable::~trackable()'
/tmp/ccyZEdIP.o:(.gcc_except_table+0x64): undefined reference to `typeinfo for Glib::Error'
/tmp/ccyZEdIP.o: In function `~SignalProxy1':
/usr/include/glibmm-2.4/glibmm/signalproxy.h:168: undefined reference to `Glib::SignalProxyNormal::~SignalProxyNormal()'
/tmp/ccyZEdIP.o: In function `~slot1':
/usr/include/sigc++-2.0/sigc++/functors/slot.h:493: undefined reference to `sigc::slot_base::~slot_base()'
/tmp/ccyZEdIP.o: In function `Glib::SignalProxy1<bool, _ClutterButtonEvent*>::connect(sigc::slot<bool, _ClutterButtonEvent*, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil> const&, bool)':
/usr/include/glibmm-2.4/glibmm/signalproxy.h:184: undefined reference to `Glib::SignalProxyNormal::connect_(sigc::slot_base const&, bool)'
/usr/include/glibmm-2.4/glibmm/signalproxy.h:184: undefined reference to `sigc::connection::connection(sigc::slot_base&)'
/tmp/ccyZEdIP.o: In function `slot1<bool (*)(_ClutterButtonEvent*)>':
/usr/include/sigc++-2.0/sigc++/functors/slot.h:526: undefined reference to `sigc::slot_base::slot_base(sigc::internal::slot_rep*)'
collect2: ld returned 1 exit status

```...good!
```
$ g++ -Wall -g -o example main.cc `pkg-config --cflags --libs cluttermm-1.0`                  
$ ./example 
```

---

### Post by t1497f35 on 2011-11-28
Thanks a lot SevenMachines, it works now!
I actually knew that one has to put the libs at the end (starting with Ubuntu 11.10) and did so at the very beginning, but I apparently did it the wrong way since it compiled but yielded an error when I tried running it (can't recall what error), so I reverted it to the original command line (as on that site).
But the way you put it works now.

---


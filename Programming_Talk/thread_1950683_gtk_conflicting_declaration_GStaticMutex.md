---
title: "gtk conflicting declaration GStaticMutex"
date: 2012-04-01
forum: Programming Talk
---

### Post by adrian01 on 2012-04-01
Whilst trying to build the sample Gnome Image viewer (as below) via Eclipse CDT.
I get errors to do with GStaticMutex being previously declared. I have set `pkg-config --cflags gtkmm-3.0` and also tried gtkmm-2.4
Also tried setting each of  the 4 defines like GTK_DISABLE_DEPRECATED.
Also tried Anjuta IDE.

```

#include <gtkmm.h>
#include <iostream>


void button_clicked()
{
std::cout << "Hello World!" << std::endl;

}

int main(int argc, char *argv[])

{
Gtk::Main kit(argc, argv);

Gtk::Window main_window;

Gtk::Button button( "Click here" );

main_window.set_title( "Eclipse/GTKmm Demo" );

main_window.set_border_width( 4 );
main_window.set_default_size( 200, 50 );


main_window.add( button );
button.show();


button.signal_clicked().connect( sigc::ptr_fun(button_clicked) );


Gtk::Main::run( main_window );

return 0;

}

```Building in directory: /home/ady/image-viewer/Debug
make
make  all-recursive
make[1]: Entering directory `/home/ady/image-viewer/Debug'
make[1]: Entering directory `/home/ady/image-viewer/Debug'
Making all in src
make[2]: Entering directory `/home/ady/image-viewer/Debug/src'
make[2]: Entering directory `/home/ady/image-viewer/Debug/src'
CXX    main.o
In file included from /usr/include/glib-2.0/glib.h:108:0,
from /usr/include/glibmm-2.4/glibmm/unicode.h:27,
from /usr/include/glibmm-2.4/glibmm/ustring.h:25,
from /usr/include/glibmm-2.4/glibmm/containerhandle_shared.h:24,
from /usr/include/glibmm-2.4/glibmm/arrayhandle.h:23,
from /usr/include/glibmm-2.4/glibmm.h:84,
from /usr/include/gtkmm-3.0/gtkmm.h:87,
from /home/ady/image-viewer/src/main.cc:20:
/usr/include/glib-2.0/glib/deprecated/gthread.h:126:0: warning: "g_static_mutex_get_mutex" redefined [enabled by default]
/usr/lib/i386-linux-gnu/glib-2.0/include/glibconfig.h:171:0: note: this is the location of the previous definition
/usr/include/glib-2.0/glib/deprecated/gthread.h:127:0: warning: "G_STATIC_MUTEX_INIT" redefined [enabled by default]
/usr/lib/i386-linux-gnu/glib-2.0/include/glibconfig.h:170:0: note: this is the location of the previous definition
In file included from /usr/include/glib-2.0/glib/gasyncqueue.h:34:0,
from /usr/include/glib-2.0/glib.h:34,
from /usr/include/glibmm-2.4/glibmm/unicode.h:27,
from /usr/include/glibmm-2.4/glibmm/ustring.h:25,
from /usr/include/glibmm-2.4/glibmm/containerhandle_shared.h:24,
from /usr/include/glibmm-2.4/glibmm/arrayhandle.h:23,
from /usr/include/glibmm-2.4/glibmm.h:84,
from /usr/include/gtkmm-3.0/gtkmm.h:87,
from /home/ady/image-viewer/src/main.cc:20:
/usr/include/glib-2.0/glib/gthread.h:51:16: error: ‘union’ tag used in naming ‘struct _GMutex’ [-fpermissive]
/usr/include/glib-2.0/glib/gthread.h:58:7: error: ‘union’ tag used in naming ‘struct _GMutex’ [-fpermissive]
In file included from /usr/include/glib-2.0/glib.h:108:0,
from /usr/include/glibmm-2.4/glibmm/unicode.h:27,
from /usr/include/glibmm-2.4/glibmm/ustring.h:25,
from /usr/include/glibmm-2.4/glibmm/containerhandle_shared.h:24,
from /usr/include/glibmm-2.4/glibmm/arrayhandle.h:23,
from /usr/include/glibmm-2.4/glibmm.h:84,
from /usr/include/gtkmm-3.0/gtkmm.h:87,
from /home/ady/image-viewer/src/main.cc:20:
/usr/include/glib-2.0/glib/deprecated/gthread.h:135:3: error: conflicting declaration ‘typedef struct GStaticMutex GStaticMutex’
/usr/lib/i386-linux-gnu/glib-2.0/include/glibconfig.h:159:30: error: ‘GStaticMutex’ has a previous declaration as ‘typedef struct _GStaticMutex GStaticMutex’
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/ady/image-viewer/Debug/src'
make[2]: Leaving directory `/home/ady/image-viewer/Debug/src'
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
make[1]: Leaving directory `/home/ady/image-viewer/Debug'
make[1]: Leaving directory `/home/ady/image-viewer/Debug'
Completed unsuccessfully
Total time taken: 8 secs

---

### Post by r-senior on 2012-04-01
Compiles and works OK for me as a simple command-line compile using:

```
g++ test.cpp -o test `pkg-config --cflags --libs gtkmm-3.0`
```

---

### Post by r-senior on 2012-04-01
In case it's a library issue, I just happen to have created a brand new VM of Ubuntu 12.04 and these were the steps to get this to compile:

```

$ sudo apt-get update
$ sudo apt-get install build-essential
$ sudo apt-get install libgtkmm-3.0-dev
$ g++ test.cpp -o test `pkg-config --cflags --libs gtkmm-3.0`

```

I'd suggest starting from there. If that works, it's a problem with the setup in the IDE.

---

### Post by adrian01 on 2012-04-02
All the update and install reported everything was up to date.
The command line compile fails with the same error.
Going to search for verbose flags to see if they point the way.....

---

### Post by adrian01 on 2012-04-02
Fixed it !
I removed Glib and associated libs, then reinstalled GTK 3.
Still got issues with Eclipse and  [I]undefined reference to Glib::ustring..........
But it is now ok from command line and Anjuta - so I can get going on some real dev now.

Thanks for the clue r-senior regarding updates to libs.
[/I]

---


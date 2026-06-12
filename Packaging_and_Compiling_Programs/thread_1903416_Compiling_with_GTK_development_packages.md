---
title: "Compiling with GTK development packages"
date: 2012-01-02
forum: Packaging and Compiling Programs
---

### Post by Minguo on 2012-01-02
Hi.  I have been trying to compile and install some programs mentioned in this thread. [http://ubuntuforums.org/showthread.php?p=11408483#post11408483](http://ubuntuforums.org/showthread.php?p=11408483#post11408483)

Unfortunately, I am unable to compile any of them despite downloading the needed packages from the ubuntu repos. I am using Ubuntu 11.10

Here they are in turn, first is jumanji, a minimalist browser.
[http://pwmt.org/projects/jumanji/](http://pwmt.org/projects/jumanji/)
```
Listed dependencies:
libwebkit (>= 1.2.1)
libsoup (>= 2.22.4)
libunique (>= 1.1.2)
gtk2 (>= 2.18.6)
glib (>= 2.22.4)
```

I have installed these packages from the ubuntu repositories using synaptic:
libwebkit-dev,
 libwebkitgtk-dev,
 libsoup2.4-dev,
 libunique-dev,
 libgtk2-dev, 
libglib2.0-dev

but running make produces this output.

```
Package javascriptcoregtk-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `javascriptcoregtk-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'javascriptcoregtk-1.0' found
Package javascriptcoregtk-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `javascriptcoregtk-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'javascriptcoregtk-1.0' found
jumanji build options:
CFLAGS  = -std=c99 -pedantic -Wall -Wextra -I. -I/usr/include 
LIBS    = -lc  -lpthread -lm
DFLAGS  = -O0 -g
CC      = cc
Package javascriptcoregtk-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `javascriptcoregtk-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'javascriptcoregtk-1.0' found
CC jumanji.c
jumanji.c:14:26: fatal error: libsoup/soup.h: No such file or directory
compilation terminated.
make: *** [jumanji.o] Error 1

```

I have the libsoup development package installed, so I do not know why it complains about that.

Also, Ubuntu does not have a package for javascriptcoregtk-1.0, but Debian does. [http://packages.debian.org/search?keywords=gir1.2-javascriptcoregtk-1.0]("http://packages.debian.org/search?keywords=gir1.2-javascriptcoregtk-1.0")


Unfortunately, installing that package does not fix the problem, (same error when running make.)  
Ubuntu does provide a package called gir1.2-webkit-1.0 which conflicts with the debian package, but installing that still gives the same error message.


Another software which gives a similar problem is dwb, another minimalist browser.
[dwb](http://portix.bitbucket.org/dwb/)
```
Listed dependencies:
libsoup >= 2.32
webkitgtk >= 1.4.0
gtk+-2.0 or gtk+-3.0
```

As before, I have the 
libgtk2.0-dev,
libwebkitgtk-dev,
and libsoup2.4 -dev 
packages installed from the Ubuntu repos.

Whlie compiling starts, it eventually spits out a lot of undefined reference errors, the bottom of which are like so.

```
view.o: In function `view_inspect_web_view_cb':
view.c:(.text+0xbe): undefined reference to `g_type_check_instance_cast'
view.o: In function `view_populate_popup_cb':
view.c:(.text+0x200): undefined reference to `g_list_free'
view.o: In function `view_icon_loaded':
view.c:(.text+0x806): undefined reference to `gtk_image_set_from_pixbuf'
view.o: In function `view_modify_style':
view.c:(.text+0x1450): undefined reference to `gtk_widget_modify_font'
view.o: In function `view_create_web_view_cb':
view.c:(.text+0x2ea5): undefined reference to `g_type_check_instance_cast'
collect2: ld returned 1 exit status

```

So I gather there is something pointing in the wrong direction, but figuring it out is beyond my linux skills.  Someone seems to have gotten it, since someone from the thread made a ppa for it.
[https://launchpad.net/~jomasti/+archive/ppa-dwb](https://launchpad.net/~jomasti/+archive/ppa-dwb)

Bafflingly I had no problems compiling another browser with similar dependencies, [http://sourceforge.net/apps/trac/vimprobable/]("http://sourceforge.net/apps/trac/vimprobable/"), so I have no idea where I've gone wrong.
Listed dependencies:
gtk2
libsoup
libwebkit>=1.1.11

Anyways, while this is now far more trouble than it is worth, I humbly ask for some hints on how to resolve this issue as a learning exercise.  I think I fail to understand exactly which packages I require, but I am not sure.


Thank you in advance.

---

### Post by azmyth on 2012-01-02
My guess would be that soup.h is in a directory that your compile doesn't see. Probably the easiest thing do do is.

```
sudo ln -s /usr/include/libsoup-2.4/libsoup/soup.h /usr/include/libsoup/soup.h

I'd just check first to make sure there isn't a file

ls /usr/include/libsoup/soup.h


```

---

### Post by Minguo on 2012-01-02
Thank you for the quick response!

Adding a symbolic link to that file changes the output:

```
Package javascriptcoregtk-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `javascriptcoregtk-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'javascriptcoregtk-1.0' found
Package javascriptcoregtk-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `javascriptcoregtk-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'javascriptcoregtk-1.0' found
jumanji build options:
CFLAGS  = -std=c99 -pedantic -Wall -Wextra -I. -I/usr/include 
LIBS    = -lc  -lpthread -lm
DFLAGS  = -O0 -g
CC      = cc
Package javascriptcoregtk-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `javascriptcoregtk-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'javascriptcoregtk-1.0' found
CC jumanji.c
In file included from jumanji.c:14:0:
/usr/include/libsoup/soup.h:13:34: fatal error: libsoup/soup-address.h: No such file or directory
compilation terminated.
make: *** [jumanji.o] Error 1
```


So I figured I just needed a symbolic link to the whole libsoup folder.  

```
sudo ln -s /usr/include/libsoup-2.4/libsoup /user/include/libsoup
```

Creating one now yields this output:


```
Package javascriptcoregtk-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `javascriptcoregtk-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'javascriptcoregtk-1.0' found
Package javascriptcoregtk-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `javascriptcoregtk-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'javascriptcoregtk-1.0' found
jumanji build options:
CFLAGS  = -std=c99 -pedantic -Wall -Wextra -I. -I/usr/include 
LIBS    = -lc  -lpthread -lm
DFLAGS  = -O0 -g
CC      = cc
Package javascriptcoregtk-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `javascriptcoregtk-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'javascriptcoregtk-1.0' found
CC jumanji.c
In file included from /usr/include/libsoup/soup-portability.h:9:0,
                 from /usr/include/libsoup/soup-address.h:11,
                 from /usr/include/libsoup/soup.h:13,
                 from jumanji.c:14:
/usr/include/libsoup/soup-types.h:9:21: fatal error: gio/gio.h: No such file or directory
compilation terminated.
```

I'm not sure what gio/gio.h refers to, but would I be heading in the right direction if I started spamming symbolic links to it?

---

### Post by alexfish on 2012-01-02
shows as part of glib2
gio part of input output streaming library

could be in path of /usr/include/glib-2.0/gio/gio.h

may also be in part of the /usr/src/   headers

try a search

---

### Post by Minguo on 2012-01-02
Thanks again for the quick response.

I have now created 20 or so symbolic links, as fixing one complaint would create another.

Now at the end of it all, I've got lots of undefined reference errors, here's the end of it.


```
jumanji.o: In function `main':
jumanji.c:(.text+0xa7e6): undefined reference to `g_thread_init'
jumanji.c:(.text+0xa7f8): undefined reference to `gtk_init'
jumanji.c:(.text+0xa90b): undefined reference to `unique_app_new_with_commands'
jumanji.c:(.text+0xa91b): undefined reference to `unique_app_is_running'
jumanji.c:(.text+0xa92d): undefined reference to `unique_message_data_new'
jumanji.c:(.text+0xa981): undefined reference to `unique_message_data_set_text'
jumanji.c:(.text+0xa99d): undefined reference to `unique_app_send_message'
jumanji.c:(.text+0xa9a9): undefined reference to `unique_message_data_free'
jumanji.c:(.text+0xa9c7): undefined reference to `g_object_unref'
jumanji.c:(.text+0xa9ea): undefined reference to `g_type_check_instance_cast'
jumanji.c:(.text+0xaa16): undefined reference to `g_signal_connect_data'
jumanji.c:(.text+0xaa4b): undefined reference to `g_timeout_add_seconds'
jumanji.c:(.text+0xaa77): undefined reference to `unique_app_is_running'
jumanji.c:(.text+0xaade): undefined reference to `gtk_widget_get_type'
jumanji.c:(.text+0xaaf0): undefined reference to `g_type_check_instance_cast'
jumanji.c:(.text+0xaaf8): undefined reference to `gtk_widget_show_all'
jumanji.c:(.text+0xaafd): undefined reference to `gtk_widget_get_type'
jumanji.c:(.text+0xab0f): undefined reference to `g_type_check_instance_cast'
jumanji.c:(.text+0xab17): undefined reference to `gtk_widget_hide'
jumanji.c:(.text+0xab25): undefined reference to `gtk_widget_get_type'
jumanji.c:(.text+0xab37): undefined reference to `g_type_check_instance_cast'
jumanji.c:(.text+0xab3f): undefined reference to `gtk_widget_hide'
jumanji.c:(.text+0xab4d): undefined reference to `gtk_widget_get_type'
jumanji.c:(.text+0xab5f): undefined reference to `g_type_check_instance_cast'
jumanji.c:(.text+0xab67): undefined reference to `gtk_widget_hide'
jumanji.c:(.text+0xab6c): undefined reference to `gtk_main'
collect2: ld returned 1 exit status
make: *** [jumanji] Error 1

```

Besides being very tedious, the symbolic links didn't fix the issue. I'm still very inexpert at Linux, but isn't this what the packages are supposed to make easy?  Have I configured something wrong? (Unlikely . . . I am running a brand new install.) I am at a loss.

---

### Post by azmyth on 2012-01-02
Probably an issue with the code you're trying to compile. The missing calls come from the /glib/gthread.h file. Guess you add it to the path in the jumanji.c file that complains.

locate gthread.h

then add 

#include </path/to/gthread.h>

You could be in for more issues when compiling though.

---

### Post by oldos2er on 2012-01-02
Moved to Packaging and Compiling Programs

---

### Post by Minguo on 2012-01-02
Thank you for the response.

I tried it, but adding the path to the gthread.h to jumanji.c didn't change the error message.

At this point I guess I have to question whether or not my assumptions of how ubuntu packages work are valid.

Here is the list of includes in jumanji.c:
```
#include <regex.h>
#include <ctype.h>
#include <limits.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <libgen.h>
#include <math.h>
#include <libsoup/soup.h>
#include <unique/unique.h>

#include <gtk/gtk.h>
#include <gdk/gdkkeysyms.h>

#include <glib/gthread.h>

#include <webkit/webkit.h>
#include <JavaScriptCore/JavaScript.h>
```

Now I think I understand why it was failing before. (See Original Post)

I do not have a  /usr/include/libsoup/soup.h on my system, the package places it in /usr/include/libsoup-2.4/libsoup/soup.h

Ok, so creating a symbolic link at /usr/include/libsoup/libsoup pointing to  /usr/include/libsoup-2.4/libsoup/ fixes that complaint. (And then I got others for various bits of libunique, gtk, webkit, etc.  All of which I fixed with more symbolic links) 

So after creating all the links, I get undefined references.  Is this because the code is missing an include statement that it needs, or all the symbolic links I hacked together are confusing things?

Is the software trying to include these libraries in a nonstandard way?  How should it be done?  Why doesn't it 'connect' to the installed packages as written?

Now I'm not sure exactly what the problem is with the includes in jumanji.c.   For example, I successfully built vimprobable whose include statements are quite similar, including the problematic ones.:
```
#include <stdlib.h>
#include <string.h>
#include <ctype.h>
#include <sys/file.h>
#include <unistd.h>
#include <gtk/gtk.h>
#include <gdk/gdkkeysyms.h>
#include <webkit/webkit.h>
#include <libsoup/soup.h>
#include <JavaScriptCore/JavaScript.h>
```

---

### Post by porti on 2012-01-03
Creating symlinks will only break your system. I don't know why jumanji cannot be compiled but i guess it is a similar problem than the problem with dwb. To compile dwb you can simply get a newer version or checkout the latest version with mercurial, the issue was already fixed on October 18.

The problem is that with ubuntu 11.10 the --as-needed flag was enabled by default for gcc, and that causes linker problems if the linker flags are not in the correct order. Putting the linker flags in the Makefile, commonly called LDFLAGS, at the end of the linker command should fix the issue, at least it fixes the issue with dwb.

---

### Post by Minguo on 2012-01-05
Thank you for the response!  Did you register just to help me out? Thank you so much!

Unfortunately, I don't understand makefiles quite yet, so I didn't quite grasp that last bit.
I found a line :
```
# LDFLAGS
LDFLAGS = $(shell pkg-config --libs $(LIBS)) 
```

In dwb's config.mk file, did you mean this should be moved to the makefile itself?

I was not able to compile either the 'stable snapshot' or the 'latest revision of the mercurial depsoitory' distributed on the dwb site.  However, after I installed mercurial and cloned it, I was able to compile that version.   Thank you!

---


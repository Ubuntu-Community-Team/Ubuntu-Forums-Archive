---
title: "Cannot use gsettingsschema.h's functions"
date: 2013-08-14
forum: Programming Talk
---

### Post by hakermania on 2013-08-14
So, I've installed glib2.0-dev [where gsettingsschema.h can be found]("http://packages.ubuntu.com/search?searchon=contents&keywords=gsettingsschema.h&mode=exactfilename&suite=raring&arch=any")

I am using Qt Creator to build my application and I am trying to use the above library's functions. This is my .pro file:

```

[COLOR=#800080]QT[/COLOR]+=core
[COLOR=#800080]QT[/COLOR]-=gui
[COLOR=#800080]TARGET[/COLOR]=gsettings_test
[COLOR=#800080]CONFIG[/COLOR]+=console
[COLOR=#800080]CONFIG[/COLOR]-=app_bundle

[COLOR=#800080]CONFIG[/COLOR]+=link_pkgconfig
[COLOR=#800080]PKGCONFIG[/COLOR]+=gio-2.0

[COLOR=#800080]TEMPLATE[/COLOR]=app

[COLOR=#800080]SOURCES[/COLOR]+=main.cpp
```
As you can see I use this part in order to make the compiler find the necessary libs:

```
CONFIG+=link_pkgconfig
PKGCONFIG+=gio-2.0

```

The command

```
pkg-config --libs gio-2.0
```
reports:
```
-lgio-2.0 -lgobject-2.0 -lglib-2.0
```
which sounds good to me.

I've included both gio/gio.h and gio/gsettingsschema.h into my main.cpp file and my compiler **does** find functions from gio.h, like g_settings_new_full() **but it cannot find the functions that are declared inside gsettingsschema.h** (I get an error like: [SIZE=2]*undefined reference to 'g_settings_schema_source_get_default()'*[/SIZE]).

What's happening here?

---

### Post by r-senior on 2013-08-16
> I get an error like: undefined reference to 'g_settings_schema_source_get_default()'
To be clear: this is a linker error. It's a problem with libs not headers.

Going back to basics:

*test.c*
```
#define _GNU_SOURCE

#include <gio/gio.h>
#include <glib.h>
#include <glib/gprintf.h>
#include <stdlib.h>

int main()
{
    g_type_init();

    GSettings *settings = g_settings_new("com.canonical.indicator.datetime");
    gchar *tz = g_settings_get_string(settings, "timezone-name");
    g_printf("Current timezone is %s\n", tz);

    return EXIT_SUCCESS;
}

```

Then to compile:

```
$ gcc -Wall -Wextra test.c $(pkg-config --cflags gio-2.0 --libs gio-2.0) -o test 
$ ./test
Current timezone is Europe/London London

```

Maybe you could try that to verify you have the correct libraries?

I don't understand the .pro file, but I suspect the '--libs' part of the pkg-config is not being passed correctly. If you drop the '--libs' part from the above, does that reproduce the messages you are getting?

---

### Post by hakermania on 2013-08-16
Thanks a lot for the answer. Qt uses the following command after reading my .pro file:

```
[COLOR=#3C3C3C]g++  -o gsettings_test main.o   -lgio-2.0 -lgobject-2.0 -lglib-2.0 -lQt5Core -lpthread[/COLOR]
```

Please note that I can compile your example code just fine, but you didn't use any library from gio/gsettingsschema.h (which is included by gio/gio.h, after all).

What if you try to use functions like g_settings_schema_source_ref ?

I want to do something similar to the code that you posted, but I want to make sure to do it correctly (checking whether the schema and the corresponding key exist each time)

---

### Post by r-senior on 2013-08-16
Seems OK for me with no changes to includes or compilation:

```
#define _GNU_SOURCE

#include <gio/gio.h>
#include <glib.h>
#include <glib/gprintf.h>
#include <stdlib.h>

int main()
{
    g_type_init();
    
    GSettingsSchemaSource *source = g_settings_schema_source_get_default(); 
    if (source == NULL) {
        g_printerr("Schema source was null\n");
        return EXIT_FAILURE;
    }

    GSettingsSchemaSource *ref = g_settings_schema_source_ref(source);

    GSettingsSchema *schema = g_settings_schema_source_lookup(
        ref, "com.canonical.indicator.datetime", TRUE
    );
    
    if (schema == NULL) {
        g_printerr("Schema was null\n");
        return EXIT_FAILURE;
    }
    
    GSettings *settings = g_settings_new_full(schema, NULL, NULL);
    
    gchar *tz = g_settings_get_string(settings, "timezone-name");
    g_printf("Current timezone is %s\n", tz);

    g_settings_schema_source_unref(ref);

    return EXIT_SUCCESS;
}
```

```
$ gcc -Wall -Wextra test.c $(pkg-config --cflags gio-2.0 --libs gio-2.0) -o test 
$ ./test
Current timezone is Europe/London London
```

---

### Post by hakermania on 2013-08-16
Weird!

This is what I get if I try to compile it the way you suggested it:

```

alex@MaD-pc:~/Qt/gsettings_test2$ gcc -Wall -Wextra main.cpp $(pkg-config --cflags gio-2.0 --libs gio-2.0) -o test 
main.cpp: In function ‘int main()’:
main.cpp:8:5: warning: ‘void g_type_init()’ is deprecated (declared at /usr/include/glib-2.0/gobject/gtype.h:669) [-Wdeprecated-declarations]
main.cpp:8:17: warning: ‘void g_type_init()’ is deprecated (declared at /usr/include/glib-2.0/gobject/gtype.h:669) [-Wdeprecated-declarations]
/tmp/ccMqNP6n.o: In function `main':
main.cpp:(.text+0xf): undefined reference to `g_settings_schema_source_get_default()'
main.cpp:(.text+0x39): undefined reference to `g_settings_schema_source_ref(_GSettingsSchemaSource*)'
main.cpp:(.text+0x59): undefined reference to `g_settings_schema_source_lookup(_GSettingsSchemaSource*, char const*, int)'
collect2: error: ld returned 1 exit status
alex@MaD-pc:~/Qt/gsettings_test2$

```

And this is what I get when I try to build it from inside Qt (which chooses a 2-step way):

```

[COLOR=#3c3c3c]g++ -c -pipe -g -pthread -Wall -W -D_REENTRANT -fPIE -DQT_QML_DEBUG -DQT_DECLARATIVE_DEBUG -I/usr/share/qt5/mkspecs/linux-g++ -I../gsettings_test2 -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I. -o main.o ../gsettings_test2/main.cpp[/COLOR]
[COLOR=#be1414]../gsettings_test2/main.cpp: In function 'int main()':[/COLOR]
[COLOR=#be1414]../gsettings_test2/main.cpp:8:5: warning: 'void g_type_init()' is deprecated (declared at /usr/include/glib-2.0/gobject/gtype.h:669) [-Wdeprecated-declarations][/COLOR]
[COLOR=#be1414]../gsettings_test2/main.cpp:8:17: warning: 'void g_type_init()' is deprecated (declared at /usr/include/glib-2.0/gobject/gtype.h:669) [-Wdeprecated-declarations][/COLOR]
[COLOR=#3c3c3c]g++  -o gsettings_test2 main.o   -lgio-2.0 -lgobject-2.0 -lglib-2.0 -lpthread [/COLOR]
[COLOR=#be1414]main.o: In function `main':[/COLOR]
[COLOR=#be1414]/home/alex/Qt/build-gsettings_test2-Desktop-Debug/../gsettings_test2/main.cpp:10: undefined reference to `g_settings_schema_source_get_default()'[/COLOR]
[COLOR=#be1414]/home/alex/Qt/build-gsettings_test2-Desktop-Debug/../gsettings_test2/main.cpp:16: undefined reference to `g_settings_schema_source_ref(_GSettingsSchemaSource*)'[/COLOR]
[COLOR=#be1414]/home/alex/Qt/build-gsettings_test2-Desktop-Debug/../gsettings_test2/main.cpp:20: undefined reference to `g_settings_schema_source_lookup(_GSettingsSchemaSource*, char const*, int)'[/COLOR]
[COLOR=#be1414]collect2: error: ld returned 1 exit status[/COLOR]
[COLOR=#be1414]make: *** [gsettings_test2] Error 1[/COLOR]

```

THey are the same errors as the above. I used the exact code that you posted without the
```
#define _GNU_SOURCE
```

line because it complained that

```

main.cpp:1: warning: "_GNU_SOURCE" redefined

```

---

### Post by r-senior on 2013-08-16
Weird indeed. I've moved over to my laptop which is running Ubuntu 13.04 (the previous examples were 12.10).

When I compiled, it also said g_type_init() is deprecated. I checked and it's not required in the latest versions of GLIB. So I removed it and it compiles and runs OK for me on 13.04.

It looks like there's a problem with your GLIB. Are you sure you have libglib-2.0-dev installed?

```
$ sudo apt-get install libglib2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglib2.0-dev is already the newest version.
```

For reference, here is the code again, with g_type_init() and _GNU_SOURCE removed:

```
#include <gio/gio.h>
#include <glib.h>
#include <glib/gprintf.h>
#include <stdlib.h>

int main()
{
    GSettingsSchemaSource *source = g_settings_schema_source_get_default(); 
    if (source == NULL) {
        g_printerr("Schema source was null\n");
        return EXIT_FAILURE;
    }

    GSettingsSchemaSource *ref = g_settings_schema_source_ref(source);

    GSettingsSchema *schema = g_settings_schema_source_lookup(
        ref, "com.canonical.indicator.datetime", TRUE
    );
    
    if (schema == NULL) {
        g_printerr("Schema was null\n");
        return EXIT_FAILURE;
    }
    
    GSettings *settings = g_settings_new_full(schema, NULL, NULL);
    
    gchar *tz = g_settings_get_string(settings, "timezone-name");
    g_printf("Current timezone is %s\n", tz);

    g_settings_schema_source_unref(ref);

    return EXIT_SUCCESS;
}

```

The timezone-name was blank for me on 13.04 but that's a different question.

---

### Post by hakermania on 2013-08-16
```
$ sudo apt-get install libglib2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglib2.0-dev is already the newest version.
libglib2.0-dev set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I have 2 systems running Ubuntu 13.04 on the same laptop (for my own reasons), and they both complain about the same reason.

I cannot recall having done something that could destroy glib in some way.

And, if there's something wrong with it, shouldn't I experience more system errors (as it is a vital system library) ?

I will test compiling from a new Ubuntu 13.04 Live USB having only the needed things for the compilation.

As for the datetime being blank, I noticed it too, but I tried with a different schema and key that I knew and it worked just fine (using the initial code that you used, I mean).

---

### Post by r-senior on 2013-08-16
> **hakermania said:**
> And, if there's something wrong with it, shouldn't I experience more system errors (as it is a vital system library) ?
If libglib2.0 was missing, yes. But this is libglib2.0-dev, which is for development.

What about reinstalling it?

---

### Post by hakermania on 2013-08-16
Replying you from the Live USB right now. Opened up a terminal and just run:

```

sudo apt-get update && sudo apt-get --yes upgrade && sudo apt-get --yes install libglib2.0-dev

```
Then I just nano'ed main.cpp and pasted the last code you posted. Then:

```

ubuntu@ubuntu:~$ gcc -Wall -Wextra main.cpp $(pkg-config --cflags gio-2.0 --libs gio-2.0) -o test
/tmp/cc0lVdCm.o: In function `main':
main.cpp:(.text+0xa): undefined reference to `g_settings_schema_source_get_default()'
main.cpp:(.text+0x37): undefined reference to `g_settings_schema_source_ref(_GSettingsSchemaSource*)'
main.cpp:(.text+0x57): undefined reference to `g_settings_schema_source_lookup(_GSettingsSchemaSource*, char const*, int)'
main.cpp:(.text+0xcd): undefined reference to `g_settings_schema_source_unref(_GSettingsSchemaSource*)'
collect2: error: ld returned 1 exit status
ubuntu@ubuntu:~$

```

I don't get how this doesn't work.

---

### Post by r-senior on 2013-08-16
The only thing I can see different between my 13.04 and yours is that I *upgraded* from 12.10 on my laptop.

---


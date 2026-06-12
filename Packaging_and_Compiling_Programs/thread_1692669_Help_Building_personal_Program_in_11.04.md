---
title: "Help Building personal Program in 11.04"
date: 2011-02-21
forum: Packaging and Compiling Programs
---

### Post by GigaRoc on 2011-02-21
It compiles up in 10.10
here's the errors
```

undefined reference to `gtk_init'
undefined reference to `gtk_main'
undefined reference to `gtk_menu_get_type'
undefined reference to `g_type_check_instance_cast'
undefined reference to `gtk_status_icon_position_menu'
undefined reference to `gtk_menu_popup'
undefined reference to `g_slist_free'
undefined reference to `gtk_widget_destroy'
undefined reference to `g_strdup_printf'
undefined reference to `g_signal_connect_data'
undefined reference to `gtk_menu_shell_get_type'
undefined reference to `g_type_check_instance_cast'
undefined reference to `gtk_menu_shell_append'
undefined reference to `g_signal_connect_data'
undefined reference to `gtk_main_quit'
undefined reference to `mysql_close'
undefined reference to `mysql_init'
undefined reference to `mysql_error'
undefined reference to `mysql_real_connect'

```

i'm getting a lot more, this is just a sample

here is my Makefile code
```

DEPS=gtk+-3.0 dbus-1 dbus-glib-1 glib-2.0 libxml-2.0 gconf-2.0
CFLAGS=$(shell pkg-config --cflags $(DEPS))
CFLAGS+=$(shell mysql_config --cflags)
CFLAGS+=-std=c99 -Wall -g -D _DEBUG -D 'PREFIX="$(PREFIX)"'

LDFLAGS=$(shell pkg-config --libs $(DEPS))
LDFLAGS+=$(shell mysql_config --libs )

```

when i pkg-config --list-all the deps are all there.

What could be causing the errors?

Thanks
Kevin Anthony

---

### Post by SevenMachines on 2011-02-23
do you have some sample code that can reproduce some of the errors? It looks like you're using gtk3 and not gtk2, were you using gtk3 in 10.10. Lastly, 11.04 is obviously in heavy development and libraries can be broken, out of sync, and so on at various times. It might just be natty thats broken at the moment after all, its why its there :)

---

### Post by mc4man on 2011-02-23
I've had issues at times since pre A1 w/ some builds in natty and gcc-4.5 (linking issues,switching to 4.4 and all is well, in some cases there were solutions for gcc-4.5

In some cases of a simple binary build (gcc blah, blah ) moving the source ahead of the deps, pkg-config, ect has resolved
It's been mentioned that this may be due to a -as-needed flag though can't see how to change that in a makefile (--no-as-needed or -fno-as-needed

simple example here
[http://ubuntuforums.org/showthread.php?p=10452995](http://ubuntuforums.org/showthread.php?p=10452995)

---


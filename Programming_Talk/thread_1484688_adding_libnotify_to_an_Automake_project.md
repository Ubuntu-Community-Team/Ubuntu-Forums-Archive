---
title: "adding libnotify to an Automake project"
date: 2010-05-16
forum: Programming Talk
---

### Post by ktulu77 on 2010-05-16
Hi,

I am trying to fork Parcellite to make a more gnome HIG compliant clipboard manager. I also would like to add notifications to this.

- The parcellite project uses automake (as a lot of other projects), so I have added libnotify to configure.in :


```
LIBNOTIFY_REQUIRED=0.4.5
PKG_CHECK_MODULES([LIBNOTIFY],[libnotify >= $LIBNOTIFY_REQUIRED],[have_libnotify=yes],[have_libnotify=no])
```

and I added to main.c a new function :

```


#include <libnotify/notify.h>
[...]
static void notify_item(gchar* text_to_display)
{
  NotifyNotification *note;
  gchar *summary;

  /* create a new notification. */
  note = notify_notification_new (text_to_display, text_to_display,
                                              NULL,
                                              NULL);
  /* show the notification. */
  notify_notification_show (note, NULL);

}
```

and then I tried to recompile the project 

```
make clean
./configure
make
```

during the configure, I have "checking for LIBNOTIFY... yes" so it seems right.

But when I try to run "make, I have this error :
```
main.o: In function `notify_item':
/home/theo/workspace/parcellite-0.9.2/src/main.c:71: undefined reference to `notify_notification_new'
/home/theo/workspace/parcellite-0.9.2/src/main.c:75: undefined reference to `notify_notification_show'
```

Note that I don't have an error about the type "NotifyNotification" so the libnotify headers have been found properly I think. Anyway, I tried to watch on Google and it seems that I need to add this argument to gcc : -lnotify

But I don't know how to do that with automake. I don't know automake at all, I tried to read some documentations, and to edit the Makefile myself to add the argument, but it is overwritten when I type make.

I also tried to watch on another projects, and I don't see any other modifications to make to add libnotify to my project.

What did I miss ?

Thank you in advance for your help

---

### Post by UnusedUserNameHere on 2010-05-27
In a project I work on, there's a 'configure.ac' that autoreconf parses to make 'configure'

In it there's a variable called 'LIBS' that contains all the flags that need to be passed to the compiler for libraries.

So I added the following line:
```
LIBS="-lnotify $LIBS"
```

Hopefully you can find something similar, but that's basically how you do it.

---

### Post by MadCow108 on 2010-05-27
PKG_CHECK_MODULES([name] ...
sets $name_LIBS and $name_CFLAGS
in your case
$LIBNOTIFY_LIBS and $LIBNOTIFY_CFLAGS

you should add these the AM_LIBS, AM_LDADD, AM_CFLAGS or AM_CXXFLAGS variables which are, if I remember correctly, added by default to the used flags (unless you override it, like with UnusedUserNameHere suggestion).

---


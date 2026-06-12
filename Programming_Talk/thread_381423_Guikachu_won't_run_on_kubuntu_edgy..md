---
title: "Guikachu won't run on kubuntu edgy."
date: 2007-03-10
forum: Programming Talk
---

### Post by mp035 on 2007-03-10
Greetings all, I have recently installed Guikachu to write palmOS apps, and whenever I add a form resource, it appears on the tree, then right click on the form entry and select edit, and the program terminates.  If i run from a terminal, it exits with this error:

```

mark@linuxbox:~$ guikachu
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 10663 error_code 8 request_code 146 minor_code 3
mark@linuxbox:~$

```

When I aptitude-ed the program I got the following warnings during install:

```

Setting up guikachu (1.4.0-2.1ubuntu3) ...
WARNING: no <list_type> specified for schema of type list
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files' locale `C': Schema specifies type list but doesn't specify the type of the list elements
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files' locale `en_CA': Schema specifies type list but doesn't specify the type of the list elements
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files' locale `pt': Schema specifies type list but doesn't specify the type of the list elements
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files' locale `wa': Schema specifies type list but doesn't specify the type of the list elements
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files' locale `cs': Schema specifies type list but doesn't specify the type of the list elements
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files' locale `sr': Schema specifies type list but doesn't specify the type of the list elements
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files' locale `en_GB': Schema specifies type list but doesn't specify the type of the list elements
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files' locale `sr@Latn': Schema specifies type list but doesn't specify the type of the list elements
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files' locale `nl': Schema specifies type list but doesn't specify the type of the list elements
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files' locale `sv': Schema specifies type list but doesn't specify the type of the list elements
WARNING: no <list_type> specified for schema of type list
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files_mime' locale `C': Schema specifies type list but doesn't specify the type of the list elements
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files_mime' locale `en_CA': Schema specifies type list but doesn't specify the type of the list elements
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files_mime' locale `pt': Schema specifies type list but doesn't specify the type of the list elements
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files_mime' locale `wa': Schema specifies type list but doesn't specify the type of the list elements
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files_mime' locale `cs': Schema specifies type list but doesn't specify the type of the list elements
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files_mime' locale `en_GB': Schema specifies type list but doesn't specify the type of the list elements
WARNING: failed to install schema `/schemas/apps/guikachu/Interface/recent_files_mime' locale `nl': Schema specifies type list but doesn't specify the type of the list elements

```

I am a newbie, so I don't quite understand the errors any help would be appreciated.

Many Thanks.

---


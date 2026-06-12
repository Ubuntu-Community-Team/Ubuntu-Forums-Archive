---
title: "Build errors on PPA; No such file or directory, etc."
date: 2008-12-08
forum: Packaging and Compiling Programs
---

### Post by Sam Lars on 2008-12-08
I finally sorted out my upload issues with my PPA, and my packages began building.  And failing.
The first thing I had to do was change what compiler was specified.  That fixed the first error I was getting.
But that brought more errors.
Right now I'm looking at [this]("http://launchpadlibrarian.net/20314774/buildlog_ubuntu-intrepid-amd64.pidgin-facebookchat_1.43~ppa3_FAILEDTOBUILD.txt.gz") log.

In case you don't want/need to sift through all of that, here's the part that I think has the problem:

```
# Add here commands to compile the package.
/usr/bin/make
make[1]: Entering directory `/build/buildd/pidgin-facebookchat-1.43~ppa3'
gcc -I/usr/include/libpurple -I/usr/local/include/libpurple -DPURPLE_PLUGINS -DENABLE_NLS -DNO_ZLIB -Wall -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/include -I. -g -O2 -pipe libfacebook.h libfacebook.c fb_blist.h fb_blist.c fb_connection.h fb_connection.c fb_info.h fb_info.c fb_managefriends.h fb_managefriends.c fb_messages.h fb_messages.c fb_notifications.h fb_notifications.c fb_search.h fb_search.c -o libfacebook.so -shared -fPIC -DPIC
libfacebook.h:26:18: error: glib.h: No such file or directory
libfacebook.h:30:24: error: glib/gi18n.h: No such file or directory
libfacebook.h:55:24: error: accountopt.h: No such file or directory

```

And they go on.

It also looks like the code is really messed up:

```
libfacebook.c:209: warning: implicit declaration of function '_'
libfacebook.c:212: warning: implicit declaration of function 'g_hash_table_lookup'
libfacebook.c:212: error: 'FacebookAccount' has no member named 'cookie_table'
libfacebook.c:218: warning: implicit declaration of function 'purple_connection_error_reason'
libfacebook.c:218: error: 'FacebookAccount' has no member named 'pc'
libfacebook.c:219: error: 'PURPLE_CONNECTION_ERROR_AUTHENTICATION_FAILED' undeclared (first use in this function)
```

The instructions say that the Pidgin headers need to be installed.  I tried adding them to the build depends, but the log showed that apt-get couldn't find it.

Does this look like a problem with what I'm doing to build the source package, or with the source?

Thanks.

---


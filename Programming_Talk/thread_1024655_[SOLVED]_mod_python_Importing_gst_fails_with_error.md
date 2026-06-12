---
title: "[SOLVED] mod_python: Importing gst fails with error &amp;quot;Error re-scanning registry&amp;quot;"
date: 2008-12-29
forum: Programming Talk
---

### Post by Moses Palmér on 2008-12-29
I have written a mod_python module to provide JSON data to a web application I use to browse my music collection. The mod_python application also provides download capabilities, but since most of my songs are in FLAC format, I cannot really use it when I am away on a slow connection, so I decided to pass the songs through a GStreamer pipeline to convert them on the fly. Previously, I did this by forking gst-launch and set the location property of the final filesink to a pipe, and pass the data from the pipe.

I decided however to implement the conversion in-process using the gst module, and it works flawlessly when tested using the interactive Python interpreter but fails when invoked by mod_python. The error message is:

```

...
  File "/var/www/app/music/filters/gstfilter.py", line 4, in <module>
    import gst

  File "/usr/lib/python2.5/site-packages/gst-0.10/gst/__init__.py", line 179, in <module>
    from _gst import *


RuntimeError: can't initialize module gst: Error re-scanning registry , child terminated by signal

```

When I try to import the gst module when running as the www-data user, I get the following warnings:

```

moses@moses-desktop:~$ LANG=C sudo -u www-data python
[sudo] password for moses: 
Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import gst

(.:16336): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)

(.:16335): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Autolaunch error: X11 initialization failed.
)
>>> 

```

Do you think that the error is somehow related to this? Do I need any special permissions of group memberships for www-data to make GStreamer work properly?

I will attach the specific file causing the error as well. This module is imported using the __import__ function:

```

self.filter_module = __import__('filters.%sfilter' % self.download_filter,
    fromlist = [self.download_filter])

```

---

### Post by Moses Palmér on 2009-01-01
I found the root of the error: when I tried to import gst as user www-data, I forgot to spawn a new shell with a new environment, so $HOME was still /home/moses, and GStreamer could read its configuration, cache and whatnot from there, but when mod_python ran the code, it was using the correct value.

Which is /var/www, which on my system was owned by the group users. www-data did not have write permissions, so it could not create the needed files.

I am not really sure how to mark this as solved, but I will try...

---


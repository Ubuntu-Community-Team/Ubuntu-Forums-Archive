---
title: "Python indicator"
date: 2009-10-18
forum: Programming Talk
---

### Post by ukblacknight on 2009-10-18
Hi all,

I've been thinking about writing a plugin for emesene so that it integrates into the [indicator-applet]("https://wiki.ubuntu.com/MessagingMenu/"), like pidgin, evolution, gwibber etc etc.

Since emesene is in python, I'd give it a go in python, although I have pretty much no experience in the language!

I followed this [article]("http://www.gnomejournal.org/article/67/an-introduction-to-the-message-indicator"), however it won't run:

```

Traceback (most recent call last):
  File "indicate.py", line 31, in <module>
    server = indicate.indicate_server_ref_default()
AttributeError: 'module' object has no attribute 'indicate_server_ref_default'
tom@blacknight:~/Projects/Python$ 

```

So I thought I'd inspect the indicate library in python:
```

>>> import indicate
>>> dir(indicate)
['INTEREST_INDICATOR_COUNT', 'INTEREST_INDICATOR_DISPLAY', 'INTEREST_INDICATOR_SIGNAL', 'INTEREST_NONE', 'INTEREST_SERVER_DISPLAY', 'INTEREST_SERVER_SIGNAL', 'Indicator', 'IndicatorMessage', 'Listener', 'Server', '__builtins__', '__doc__', '__file__', '__name__', '__package__', '__path__', '_indicate', 'ctypes', 'indicate_listener_ref_default', 'indicate_server_ref_default', 'indicate_server_set_dbus_object', 'indicator_id', 'server_dbus_name']

```

So, the "indicate_server_ref_default" attribute (I'm sure it should be a method?) does exist.  Any ideas why python would imply that it does not?

Below is the code that I have:
```

import gobject
import gtk
from time import time
import os

try:
	import indicate
except:
	indicate = None

curdir = os.getcwd()
desktop_file = os.path.join(curdir, "indicate.desktop")

def timeout_cb(indicator):
	print "Modifying properties"
	indicator.set_property_time("time", time())
	return True
	
def display(indicator):
	print "Ah, my indicator has been displayed"
	indicator.hide()
	
def server_display(server):
	print "Ah, my server has been displayed"

print __name__

if __name__ == "__main__":
	
	# Setup the server
	server = indicate.indicate_server_ref_default()
	server.set_type("message.im")
	server.set_desktop_file(desktop_file)
	server.connect("server-display", server_display)
	server.show()
	
	# Setup the message
	indicator = indicate.IndicatorMessage()
	indicator.set_property("subtype", "im")
	indicator.set_property("sender", "Test message")
	indicator.set_property("body", "Test message body")
	indicator.set_property_time("time", time())
	indicator.show()
	indicator.connect("user-display", display)
	
	# Loop
	gobject.timeout_add_seconds(5, timeout_cb, indicator)
	gtk.main()


```

Note: The try: except: statement is something I noticed in the source code for gwibber - I tried that to see if it had any effect.

---

### Post by benj1 on 2009-10-18
youre using indicator rather than indicate

should be indicate.indicate_server_ref_default

otherwise youre essentially trying to use
indicate.IndicatorMessage().indicate_server_ref_default

---

### Post by ukblacknight on 2009-10-18
> **benj1 said:**
> youre using indicator rather than indicate

should be indicate.indicate_server_ref_default

otherwise youre essentially trying to use
indicate.IndicatorMessage().indicate_server_ref_default

It is indicate.indicate_server_ref_default, the problem is on line 31:

```
server = indicate.indicate_server_ref_default()
```

---

### Post by benj1 on 2009-10-18
yes youre correct, my appologies.

im not sure ive never used the module before, it seems correct, certainly your listing of the module seems to suggest its correct. what happens when you get rid of the try except block at the start, at the moment its just hiding any potential import errors you may have, im guessing the problem will lie there, rather than with the function

---

### Post by ukblacknight on 2009-10-18
Exactly the same problem.  When I aasked a friend to inspect the indicate library on his ubuntu box, his results differed to mine, and indicate_server_ref_default wasn't listed.  Could you, or someone else try it on their machine?

---

### Post by benj1 on 2009-10-18
just tested it, works fine for me, im using python 2.6 and standard python-indicate from the repos.

---

### Post by ukblacknight on 2009-10-18
> **benj1 said:**
> just tested it, works fine for me, im using python 2.6 and standard python-indicate from the repos.

By 'it', do you mean the entire script?

---

### Post by Flimm on 2009-10-18
I just tested it, I got the error at first, and then I didn't, and I don't know why. Changing indacate.IndicatorMessage() to indicate.Indicator() on line 38 got rid of all errors.

---

### Post by ukblacknight on 2009-10-18
> **Flimm said:**
> I just tested it, I got the error at first, and then I didn't, and I don't know why. Changing indacate.IndicatorMessage() to indicate.Indicator() on line 38 got rid of all errors.

Tried that, problem still persists :\

I tried inspecting the indicate library again, and now the results are different!!

```
>>> import indicate
indicate
>>> dir(indicate)
['__builtins__', '__doc__', '__file__', '__name__', '__package__', 'curdir', 'desktop_file', 'display', 'gobject', 'gtk', 'indicate', 'os', 'server_display', 'time', 'timeout_cb']
>>> 

```

---

### Post by benj1 on 2009-10-18
full script and that function both fine.

---

### Post by benj1 on 2009-10-18
whats the contents of the library ?
it'll be in /usr/lib/python2.x/dist-packages

---

### Post by ukblacknight on 2009-10-18
> **benj1 said:**
> whats the contents of the library ?
it'll be in /usr/lib/python2.x/dist-packages

If you mean what I think you mean, then this is the result:

```
tom@blacknight:/usr/lib/python2.6/dist-packages/indicate$ ls -lh
total 40K
lrwxrwxrwx 1 root root   41 2009-08-29 11:07 _indicate.la -> /usr/share/pyshared/indicate/_indicate.la
-rw-r--r-- 1 root root  33K 2009-04-09 22:23 _indicate.so
lrwxrwxrwx 1 root root   40 2009-08-29 11:07 __init__.py -> /usr/share/pyshared/indicate/__init__.py
-rw-r--r-- 1 root root 1023 2009-08-29 11:07 __init__.pyc

```

---

### Post by benj1 on 2009-10-18
i was thinking more the contents of your files, your last listing seemed to show all of your functions which i dont think should happen, i just want to make sure all the links etc are ok.

have you tried reinstalling the library ?

---

### Post by unutbu on 2009-10-18
ukblacknight, did you put your own personal code in a file called "indicate.py"?
If so, when you run your personal version of indicate.py, python thinks you've replaced the standard indicate module with your own.

If my guess is correct, then the solution is to rename your file something (anything!) that doesn't conflict with a standard library module name.

---

### Post by ukblacknight on 2009-10-18
I reinstalled the library, no changes :(

```

tom@blacknight:/usr/lib/python2.6/dist-packages/indicate$ cat _indicate.la
# _indicate.la - a libtool library file
# Generated by ltmain.sh (GNU libtool) 2.2.6 Debian-2.2.6a-1ubuntu1
#
# Please DO NOT delete this file!
# It is necessary for linking the library.

# The name that we can dlopen(3).
dlname='_indicate.so'

# Names of this library.
library_names='_indicate.so _indicate.so _indicate.so'

# The name of the static archive.
old_library=''

# Linker flags that can not go in dependency_libs.
inherited_linker_flags=''

# Libraries that this one depends upon.
dependency_libs=' -lpyglib-2.0-python2.6 -L//lib -lindicate /usr/lib/libgtk-x11-2.0.la -ldbus-glib-1 /usr/lib/libgdk-x11-2.0.la /usr/lib/libatk-1.0.la /usr/lib/libpangoft2-1.0.la /usr/lib/libgdk_pixbuf-2.0.la -lm /usr/lib/libpangocairo-1.0.la /usr/lib/libgio-2.0.la /usr/lib/libcairo.la /usr/lib/libpango-1.0.la /usr/lib/libfreetype.la -lz -lfontconfig /usr/lib/libgmodule-2.0.la -ldbus-1 /usr/lib/libgobject-2.0.la /usr/lib/libglib-2.0.la'

# Names of additional weak libraries provided by this library
weak_library_names=''

# Version information for _indicate.
current=0
age=0
revision=0

# Is this an already installed library?
installed=yes

# Should we warn about portability when linking against -modules?
shouldnotlink=yes

# Files to dlopen/dlpreopen
dlopen=''
dlpreopen=''

# Directory that this library needs to be installed in:
libdir='/usr/lib/python2.5/site-packages/indicate'
tom@blacknight:/usr/lib/python2.6/dist-packages/indicate$ 

```

---

### Post by ukblacknight on 2009-10-18
> **unutbu said:**
> ukblacknight, did you put your own personal code in a file called "indicate.py"?
If so, when you run your personal version of indicate.py, python thinks you've replaced the standard indicate module with your own.

If my guess is correct, then the solution is to rename your file something (anything!) that doesn't conflict with a standard library module name.

BOOM! Done :D  I had actually renamed the file much earlier on, to "example-indicate.py", but the "indicator.pyc" and "indicator.py~" files were still there.  I just deleted them, and now it works!

Thanks :)

---


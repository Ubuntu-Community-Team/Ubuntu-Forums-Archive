---
title: "Python error?"
date: 2006-04-10
forum: Programming Talk
---

### Post by Lightmans on 2006-04-10
Hi there, is there anybody out there who nows about python and his error messages? 
I have two errors and i dont now whats the problem or what the system wants or need :) 
I have absolutly no expirience with python.

This is the error when i start for example wifi-radar or msncp (console messenger) 
=========================================================
```
root@lightmans2:/home/harald/Downloads/msncp-0.5.0-beta# ./msncp 
Traceback (most recent call last): 
  File "./msncp", line 30, in ? 
    import curses       # Python 1.6 
  File "/usr/local/lib/python2.4/curses/__init__.py", line 15, in ? 
    from _curses import * 
ImportError: No module named _curses 
root@lightmans2:/home/harald/Downloads/msncp-0.5.0-beta# wifi-radar 
Traceback (most recent call last): 
  File "/usr/sbin/wifi-radar", line 1795, in ? 
    import gtk, gobject 
  File "/usr/local/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 33, in ? 
    import gobject as _gobject 
ImportError: /usr/local/lib/python2.4/site-packages/gtk-2.0/gobject.so: undefined symbol: PyUnicodeUCS2_FromUnicode 
root@lightmans2:/home/harald/Downloads/msncp-0.5.0-beta# 

```
==========================================================

For your Information, 
i have Ubuntu Breezy 5.10 Desktop Gnome installed with Python 2.4.3 self compiled and installed without any errors.


Here is the __init__.py file...

==========================================================
```
root@lightmans2:/home/harald/Downloads/msncp-0.5.0-beta# cat /usr/local/lib/python2.4/curses/__init__.py 
"""curses 

The main package for curses support for Python.  Normally used by importing 
the package, and perhaps a particular module inside it. 

   import curses 
   from curses import textpad 
   curses.initwin() 
   ... 

""" 

__revision__ = "$Id: __init__.py,v 1.5 2004/07/18 06:14:41 tim_one Exp $" 

from _curses import * 
from curses.wrapper import wrapper 

# Some constants, most notably the ACS_* ones, are only added to the C 
# _curses module's dictionary after initscr() is called.  (Some 
# versions of SGI's curses don't define values for those constants 
# until initscr() has been called.)  This wrapper function calls the 
# underlying C initscr(), and then copies the constants from the 
# _curses module to the curses package's dictionary.  Don't do 'from 
# curses import *' if you'll be needing the ACS_* constants. 

def initscr(): 
    import _curses, curses 
    stdscr = _curses.initscr() 
    for key, value in _curses.__dict__.items(): 
        if key[0:4] == 'ACS_' or key in ('LINES', 'COLS'): 
            setattr(curses, key, value) 

    return stdscr 

# This is a similar wrapper for start_color(), which adds the COLORS and 
# COLOR_PAIRS variables which are only available after start_color() is 
# called. 

def start_color(): 
    import _curses, curses 
    retval = _curses.start_color() 
    if hasattr(_curses, 'COLORS'): 
        curses.COLORS = _curses.COLORS 
    if hasattr(_curses, 'COLOR_PAIRS'): 
        curses.COLOR_PAIRS = _curses.COLOR_PAIRS 
    return retval 

# Import Python has_key() implementation if _curses doesn't contain has_key() 

try: 
    has_key 
except NameError: 
    from has_key import has_key 




Code:

        except TypeError, e: 
            msg = str(e).replace(self.name, self.oldname) 
            raise TypeError(msg) 

class _DeprecatedConstant: 
    def __init__(self, value, name, suggestion): 
        self._v = value 
        self._name = name 
        self._suggestion = suggestion 

    def _deprecated(self, value): 
        message = '%s is deprecated, use %s instead' % (self._name, 
                                                        self._suggestion) 
        _warn(message, DeprecationWarning, 3) 
        return value 

    __nonzero__ = lambda self: self._deprecated(self._v == True) 
    __int__     = lambda self: self._deprecated(int(self._v)) 
    __str__     = lambda self: self._deprecated(str(self._v)) 
    __repr__    = lambda self: self._deprecated(repr(self._v)) 
    __cmp__     = lambda self, other: self._deprecated(cmp(self._v, other)) 

# _gobject deprecation 
class _GObjectWrapper(_module): 
    _gobject = _gobject 
    def __getattr__(self, attr): 
        _warn('gtk._gobject is deprecated, use gobject directly instead', 
              DeprecationWarning, 2) 
        return getattr(self._gobject, attr) 

# old names compatibility ... 
idle_add       = _Deprecated(_gobject.idle_add, 'idle_add', 'gobject') 
idle_remove    = _Deprecated(_gobject.source_remove, 'idle_remove', 'gobject') 
timeout_add    = _Deprecated(_gobject.timeout_add, 'timeout_add', 'gobject') 
timeout_remove = _Deprecated(_gobject.source_remove, 'timeout_remove', 'gobject') 
input_add      = _Deprecated(_gobject.io_add_watch, 'input_add', 'gobject') 
input_add_full = _Deprecated(_gobject.io_add_watch, 'input_add_full', 'gobject') 
input_remove   = _Deprecated(_gobject.source_remove, 'input_remove', 'gobject') 

mainloop                 = _Deprecated(main, 'mainloop') 
mainquit                 = _Deprecated(main_quit, 'mainquit') 
mainiteration            = _Deprecated(main_iteration, 'mainiteration') 
load_font                = _Deprecated(gdk.Font, 'load_font', 'gtk.gdk') 
load_fontset             = _Deprecated(gdk.fontset_load, 'load_fontset', 'gtk.gdk') 
create_pixmap            = _Deprecated(gdk.Pixmap, 'create_pixmap', 'gtk.gdk') 
create_pixmap_from_xpm   = _Deprecated(gdk.pixmap_create_from_xpm, 
                                       'pixmap_create_from_xpm', 'gtk.gdk') 
create_pixmap_from_xpm_d = _Deprecated(gdk.pixmap_create_from_xpm_d, 
                                       'pixmap_create_from_xpm_d', 'gtk.gdk') 

TRUE = _DeprecatedConstant(True, 'gtk.TRUE', 'True') 
FALSE = _DeprecatedConstant(False, 'gtk.FALSE', 'False') 

_gobject = _GObjectWrapper('gtk._gobject') 

# Can't figure out how to deprecate gdk.Warning 
gdk.Warning = Warning 

del _Deprecated, _DeprecatedConstant, _GObjectWrapper, _module, 
root@lightmans2:/home/harald/Downloads/msncp-0.5.0-beta# 
.py /usr/local/lib/python2.4/site-packages/gtk-2.0/gtk/__init__. 
# -*- Mode: Python; py-indent-offset: 4 -*- 
# pygtk - Python bindings for the GTK toolkit. 
# Copyright (C) 1998-2003  James Henstridge 
# 
#   gtk/__init__.py: initialisation file for gtk package. 
# 
# This library is free software; you can redistribute it and/or 
# modify it under the terms of the GNU Lesser General Public 
# License as published by the Free Software Foundation; either 
# version 2.1 of the License, or (at your option) any later version. 
# 
# This library is distributed in the hope that it will be useful, 
# but WITHOUT ANY WARRANTY; without even the implied warranty of 
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU 
# Lesser General Public License for more details. 
# 
# You should have received a copy of the GNU Lesser General Public 
# License along with this library; if not, write to the Free Software 
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 
# USA 

from types import ModuleType as _module 
from warnings import warn as _warn 

# this can go when things are a little further along 
try: 
    import ltihooks, sys 
    sys.path.insert(1, 'gobject') 
    del ltihooks, sys 
except ImportError: 
    pass 

import gobject as _gobject 

# load the required modules: 
import sys 
sys_path = sys.path[:] 
from _gtk import * 

# init_gtk calls PySys_SetArgv which calls sys.path.insert(0, ''), 
# which causes problems for pychecker, restore it if modified. 
if sys.path != sys_path: 
    sys.path = sys_path 
del sys, sys_path 

import keysyms 
import gdk # this is created by the _gtk import 

threads_init = gdk.threads_init 
threads_enter = gdk.threads_enter 
threads_leave = gdk.threads_leave 

gdk.INPUT_READ      = _gobject.IO_IN | _gobject.IO_HUP | _gobject.IO_ERR 
gdk.INPUT_WRITE     = _gobject.IO_OUT | _gobject.IO_HUP 
gdk.INPUT_EXCEPTION = _gobject.IO_PRI 

# other deprecated symbols 
class _Deprecated: 
    def __init__(self, func, oldname, module=''): 
        self.func = func 
        self.oldname = oldname 
        self.name = func.__name__ 
        if module: 
            self.module = module 
        else: 
            self.module = 'gtk' 

    def __repr__(self): 
        return '<deprecated function %s>' % (self.oldname) 

    def __call__(self, *args, **kwargs): 
        oldname = 'gtk.' + self.oldname 
        newname = self.module + '.' + self.name 
        message = '%s is deprecated, use %s instead' % (oldname, newname) 
        # DeprecationWarning is imported from _gtk, so it's not the same 
        # as the one found in exceptions. 
        _warn(message, DeprecationWarning, 2) 
        try: 
            return self.func(*args, **kwargs) 
        except TypeError, e: 
            msg = str(e).replace(self.name, self.oldname) 
            raise TypeError(msg) 

class _DeprecatedConstant: 
    def __init__(self, value, name, suggestion): 
        self._v = value 
        self._name = name 
        self._suggestion = suggestion 

    def _deprecated(self, value): 
        message = '%s is deprecated, use %s instead' % (self._name, 
                                                        self._suggestion) 
        _warn(message, DeprecationWarning, 3) 
        return value 

    __nonzero__ = lambda self: self._deprecated(self._v == True) 
    __int__     = lambda self: self._deprecated(int(self._v)) 
    __str__     = lambda self: self._deprecated(str(self._v)) 
    __repr__    = lambda self: self._deprecated(repr(self._v)) 
    __cmp__     = lambda self, other: self._deprecated(cmp(self._v, other)) 

# _gobject deprecation 
class _GObjectWrapper(_module): 
    _gobject = _gobject 
    def __getattr__(self, attr): 
        _warn('gtk._gobject is deprecated, use gobject directly instead', 
              DeprecationWarning, 2) 
        return getattr(self._gobject, attr) 

# old names compatibility ... 
idle_add       = _Deprecated(_gobject.idle_add, 'idle_add', 'gobject') 
idle_remove    = _Deprecated(_gobject.source_remove, 'idle_remove', 'gobject') 
timeout_add    = _Deprecated(_gobject.timeout_add, 'timeout_add', 'gobject') 
timeout_remove = _Deprecated(_gobject.source_remove, 'timeout_remove', 'gobject') 
input_add      = _Deprecated(_gobject.io_add_watch, 'input_add', 'gobject') 
input_add_full = _Deprecated(_gobject.io_add_watch, 'input_add_full', 'gobject') 
input_remove   = _Deprecated(_gobject.source_remove, 'input_remove', 'gobject') 

mainloop                 = _Deprecated(main, 'mainloop') 
mainquit                 = _Deprecated(main_quit, 'mainquit') 
mainiteration            = _Deprecated(main_iteration, 'mainiteration') 
load_font                = _Deprecated(gdk.Font, 'load_font', 'gtk.gdk') 
load_fontset             = _Deprecated(gdk.fontset_load, 'load_fontset', 'gtk.gdk') 
create_pixmap            = _Deprecated(gdk.Pixmap, 'create_pixmap', 'gtk.gdk') 
create_pixmap_from_xpm   = _Deprecated(gdk.pixmap_create_from_xpm, 
                                       'pixmap_create_from_xpm', 'gtk.gdk') 
create_pixmap_from_xpm_d = _Deprecated(gdk.pixmap_create_from_xpm_d, 
                                       'pixmap_create_from_xpm_d', 'gtk.gdk') 

TRUE = _DeprecatedConstant(True, 'gtk.TRUE', 'True') 
FALSE = _DeprecatedConstant(False, 'gtk.FALSE', 'False') 

_gobject = _GObjectWrapper('gtk._gobject') 

# Can't figure out how to deprecate gdk.Warning 
gdk.Warning = Warning 

del _Deprecated, _DeprecatedConstant, _GObjectWrapper, _module, 
root@lightmans2:/home/harald/Downloads/msncp-0.5.0-beta# 


```
=========================================================

I hope anybody can help me with this errors!
Greetings
Lightmans

---

### Post by gord on 2006-04-10
i would guess this error is because you rolled your own version of python, honistally the 2.4.3 version is hardly diffirent from the 2.4.2 version provided with ubuntu, its mainly a bugfix version. but the nice thing about python is that it has been around for so long that the only bugs in it are really obscure ones, iv been using python for years and failed to find a single bug.

so best advice, re-install 2.4.2. failing that i would try changing line 15 to 
from curses import *

---

### Post by Lightmans on 2006-04-10
[QUOTE=gord]i would guess this error is because you rolled your own version of python, honistally the 2.4.3 version is hardly diffirent from the 2.4.2 version provided with ubuntu, its mainly a bugfix version. but the nice thing about python is that it has been around for so long that the only bugs in it are really obscure ones, iv been using python for years and failed to find a single bug.

so best advice, re-install 2.4.2. failing that i would try changing line 15 to 
from curses import *[/QUOTE]


Hi Gord,
i have the same error with original package python2.4.2 form ubuntu ...

what exactly do you mean with? -> > i would try changing line 15 to 
from curses import *

i dont now what i whave to write there... :)

Thanks for your answer and greetings,
Lightmans

---


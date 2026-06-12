---
title: "Switching compiz workspaces in Perl"
date: 2008-05-05
forum: Programming Talk
---

### Post by aaargh486 on 2008-05-05
For a project I'm preparing I need to be able to change the active workspace from Perl or C or whatever language.
Perl seemed best, and I installed libgnome2-wnck-perl.
After a LOT of PROBLEMS, I managed to make this program

```

#!/usr/bin/perl -w

use Gnome2::Wnck;
use Gtk2 '-init';
use strict;

my $screen = Gnome2::Wnck::Screen->get_default();
$screen -> force_update();

my $curspace = $screen->get_active_workspace();
my $newspace = $screen->get_workspace($curspace->get_number + 1);

Gnome2::Wnck::Workspace::activate( $newspace, 0 );

```

Yes I know this doesn't work correctly but I'll finish that later. The problem is that this doesn't work in Compiz, only under Metacity. 
Does anybody know how to change workspaces in Compiz?

Thanks a lot, Kasper.

---

### Post by luisromangz on 2008-05-05
To interact with Compiz you have to use DBus, which is an inter-process communication system.

---

### Post by aaargh486 on 2008-05-06
I know, that's a idea I tried out, but I couldn't find the correct method to have Compiz do this.
Can anybody help me with this?

---

### Post by siouzi on 2008-05-07
> **aaargh486 said:**
> I know, that's a idea I tried out, but I couldn't find the correct method to have Compiz do this.
Can anybody help me with this?

Did you see this [http://forum.compiz-fusion.org/showthread.php?t=178](http://forum.compiz-fusion.org/showthread.php?t=178) - rotating the cube using a shell script? Make sure you've checked the Dbus in compiz settings manager.

---

### Post by aaargh486 on 2008-05-07
Dbus enabled, and all necessary plugins loaded.
It gives me this error.

```

kasper@TARDIS:~$ dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/rotate/allscreens/rotate_right org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`
Error org.freedesktop.DBus.Error.UnknownMethod: Method "activate" with signature "si" on interface "org.freedesktop.compiz" doesn't exist

```

I added the --print-reply myself.

---

### Post by siouzi on 2008-05-08
That command works perfectly on Gutsy's compiz. It should return something like ```
method return sender=:1.664 -> dest=:1.665 reply_serial=2
```

Cause of the error is probably too old or too new compiz? =) Quick search reveals similar problems, e.g. [http://ubuntuforums.org/showthread.php?p=4654244#post4654244](http://ubuntuforums.org/showthread.php?p=4654244#post4654244)

---

### Post by aaargh486 on 2008-05-08
Yes, yes, rotate_right was renamed to rotate_right_key.

Thanks a bunch!

---

### Post by dtmilano on 2008-05-09
I know you were looking for a perl script, but perhaps this python one gives you some starting point:

> 
#! /usr/bin/env python

import sys
import dbus

from Xlib.protocol import display

# default command
cmd = 'rotate_right_key'

proxy = dbus.SessionBus().get_object('org.freedesktop.compiz',
	'/org/freedesktop/compiz/rotate/allscreens/' + cmd)

dpy = display.Display()
wid = dpy.info.roots[dpy.get_default_screen()].root

proxy.activate('root', wid)


---


---
title: "/etc/init.d/xxxxxxxx file format"
date: 2010-01-27
forum: Programming Talk
---

### Post by Barriehie on 2010-01-27
Hey all,  so I had a bash script that would run as a daemon and after having to reinstall ubuntu it's now broken.  That's okay because it was sloppy and I've since discovered **inotifywait**.  Now I want to write the script(s) correctly but can't for any amount of googling/searching find the accepted standard for the files in /etc/init.d/  I've copied some from my squid file and it's like the code block below.  Can anyone please tell me where/what this is defined?  I can remember it had an L in it.  Maybe it was just the code block definition for the init info.

```

#! /bin/sh
#
# squid		Startup script for the SQUID HTTP proxy-cache.
#
# Version:	@(#)squid.rc  2.20  01-Oct-2001  miquels@cistron.nl
#
### BEGIN INIT INFO
# Provides:          squid
# Required-Start:    $local_fs $network
# Required-Stop:     $local_fs $network
# Should-Start:      $named
# Should-Stop:       $named
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Squid HTTP Proxy
### END INIT INFO

```

TIA,
[color="green"]Barrie[/color]

---

### Post by Barriehie on 2010-01-27
The 'L' was the trigger, I found it.  [[color="Blue"]LSBInitscripts[/color]](http://wiki.debian.org/LSBInitScripts).

TIA
Barrie

---


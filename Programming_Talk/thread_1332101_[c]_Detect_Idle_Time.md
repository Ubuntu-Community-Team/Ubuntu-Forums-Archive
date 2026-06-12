---
title: "[c] Detect Idle Time"
date: 2009-11-20
forum: Programming Talk
---

### Post by falconindy on 2009-11-20
I found the following code to return one's idle time by querying activity on the X server:
```
#include <X11/extensions/scrnsaver.h>
#include <stdio.h>

main() {
	XScreenSaverInfo *info = XScreenSaverAllocInfo();
	Display *display = XOpenDisplay(NULL);

	if (display != NULL) 
		XScreenSaverQueryInfo(display, DefaultRootWindow(display), info);
	printf("%u", info->idle);
}
```
It compiles. It runs. It seg faults when run from a tty or in a cron job. Presumably, it does so because querying an X server from outside of it is always awkward. Does anyone know how to fix this? Or some other more reliable method?

---

### Post by johnl on 2009-11-20
try specifying the display when running it:
```

user@host:~$ DISPLAY=:0 ./detect-idle-time

```

Or you might be able to pass the display you want to XOpenDisplay().

---

### Post by falconindy on 2009-11-20
Solved. I have to have XAUTHORITY available before I can specify DISPLAY without getting a protocol error.

For anyone else finding this thread curious about it: I'm using a pair of cron jobs to update my status (away/available) in Pidgin and rotate my message every 30 minutes. I have a Gnome login script that pipes XAUTHORITY and DBUS_SESSION_BUS_ADDRESS into a file in my home directory. Both cron jobs source this file so that they have access to my desktop. One script updates my status by checking X idle time against a preset value, and the other pulls a random line out of my $HOME/.lyrics directory and updates pidgin using purple-remote.

Yes, I'm lazy. Lazy and bored.

---


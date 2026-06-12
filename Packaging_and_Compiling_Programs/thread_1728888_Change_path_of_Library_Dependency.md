---
title: "Change path of Library Dependency"
date: 2011-04-14
forum: Packaging and Compiling Programs
---

### Post by djbushido on 2011-04-14
I apologize if this is in the wrong forum, I thought it was as close as I was going to get:

I am having problems getting Firefox 4 to work - the plugin container ignores LD_LIBRARY_PATH which is set to allow a new version of libstdc++ to be used specifically for firefox. In short, I need to drop in a replacement library and plugin-container isn't using it.
Is there a way to change the way ld finds libraries (can't use ld.conf since I don't want to make a system-wide change) such that instead of ./libstdc++ it looks for /path/to/libstdc++?
I appreciate all help, thank you!

---

### Post by SevenMachines on 2011-04-14
What exactly is it you're trying to do? LD_LIBRARY_PATH should work, i recently used it to pre load a library with memcpy() overridden to workaround a flash bug, and flash uses the plugin-container so it should be no problem. 

Maybe you have a different version but the /usr/bin/firefox script exports LD_LIBRARY_PATH before running the exe here, if yours doesnt maybe you could add something into the script yourself

With a little echo in /usr/bin/firefox for debugging i get
```
$ LD_LIBRARY_PATH=/path/to/some/library firefox
Executing: LD_LIBRARY_PATH=/usr/lib/firefox-4.0:/usr/lib/firefox-4.0/plugins:/path/to/some/library /usr/lib/firefox-4.0/firefox-bin
```With set -x
```
+ LD_LIBRARY_PATH=/usr/lib/firefox-4.0:/usr/lib/firefox-4.0/plugins:/path/to/some/library
+ export LD_LIBRARY_PATH
+ [ 0 -eq 1 ]
+ exec /usr/lib/firefox-4.0/firefox-bin
```

---

### Post by djbushido on 2011-04-14
Just trying to run Firefox 4 (though on RHEL 5.4).
I am running firefox-bin by itself, but when I load a flash movie, it freezes, and the terminal outputs that there was an issue with libstdc++, and gives an incorrect path.
I'll double check scripts, but I am running the firefox-bin without any script, and the plugin-container specifically is having issues.

---


---
title: "SDL wrong version"
date: 2012-02-11
forum: Programming Talk
---

### Post by PeterP24 on 2012-02-11
Hello,

I have a problem related to the wrong version of SDL installed. More specifically, I installed version 1.3 of SDL, sometimes ago, and it messed up the existing 1.2 version (installed from repositories). I have discovered that the system is configured to take the SDL 1.3 version when it comes to compiling and linking any new software that needs SDL. The problem is that most software need version 1.2 and the new version is not compatible with the old one. 

So I searched for a way to remove version 1.3. I did not find any, so I got this dumb ideea and went and delete the include files for version 1.3 (/usr/local/include/SDL). This was useless since 

/usr/local/bin/sdl-config --version 

still returns 1.3.0

I require help in fixing this. I cannot completely remove libsdl1.2 and reinstall it since I would have to remove a large number of my already installed programs and games which would be very unconvenient. I already reinstall it with synaptic but it doesn't help. I think the system (Ubuntu 11.04) is ok, but I cannot compile new programs that depend on SDL. For instance bellow is the output of naev game configure script when searching for SDL:

checking for preferences directory... .naev
checking for sdl-config... /usr/local/bin/sdl-config
checking for SDL - version >= 0.11.0... no
*** Could not run SDL test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means SDL was incorrectly installed
*** or that you have moved SDL since it was installed. In the latter case, you
*** may want to edit the sdl-config script: /usr/local/bin/sdl-config
configure: error: SDL not found

---

### Post by Bachstelze on 2012-02-11
You can remove /usr/local/bin/sdl-config, then configure scripts will pick up the version in /usr/bin (make sure it is still there).

---

### Post by PeterP24 on 2012-02-11
I removed /usr/local/bin/sdl-config (made a backup copy first). I don't have the version in /usr/bin (I don't know from were (or how) to get it) and the error I have when compiling is related to the missing script sdl-config:

checking for preferences directory... .naev
checking for sdl-config... no
checking for SDL - version >= 0.11.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: SDL not found

---

### Post by Bachstelze on 2012-02-11
You need to install [font=monospace]libsdl1.2-dev[/font].

---

### Post by PeterP24 on 2012-02-12
Thank you very much - that fixed it.

---


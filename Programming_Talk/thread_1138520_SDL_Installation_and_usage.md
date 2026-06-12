---
title: "SDL Installation and usage"
date: 2009-04-26
forum: Programming Talk
---

### Post by bigDninja on 2009-04-26
So I recently switched to ubuntu and I've slowly been learning how to use it with this forum answering a lot of my questions.  However, I just bumped up against a problem installing the SDL.  I'm not sure if I don't have the whole program and thats creating problems or what - I downloaded the .tar and when I try to make install it in terminal I get a permission denied.  Its trying to install an sdl-config in /usr/local/bin/ .  I then used the logname command to confirm that I am, indeed, logged in.  There is no prompting for a password to grant privileges.  
The .tar is from [http://www.libsdl.org/](http://www.libsdl.org/)
The walkthrough I've been following is:   [http://sol.gfxile.net/gp/ch01_linux.html](http://sol.gfxile.net/gp/ch01_linux.html)  (I'm at step 9)
Thanks and sorry if this belongs in the beginner's forum.

---

### Post by M4rotku on 2009-04-26
Are you using 'sudo'?

---

### Post by bigDninja on 2009-04-26
No. :(  That got it.  I thought the sudo command was for installing things that were not already present on the computer.  Thanks for the help!

---

### Post by cabalas on 2009-04-26
You should be installing the development libraries from synaptic, doing it this way will cause issues if you install anything that depends on SDL. the package for the development files are libsdl1.2-dev

---

### Post by Neheb on 2009-04-27
> **bigDninja said:**
> No. :(  That got it.  I thought the sudo command was for installing things that were not already present on the computer.  Thanks for the help!

sudo is to run the command as root user and is needed for anything that modifies files outside your home folder

---

### Post by geirha on 2009-04-27
> **cabalas said:**
> You should be installing the development libraries from synaptic, doing it this way will cause issues if you install anything that depends on SDL. the package for the development files are libsdl1.2-dev

+1. Always check the repositories first, before downloading and compiling the source yourself. If you already managed to install sdl from source, run ```
sudo make uninstall
``` from the source code tree to uninstall it again (not all source code provide a means of uninstalling, but sdl probably does)

Once you've installed [libsdl1.2-dev](apt:libsdl1.2-dev), you can get the arguments you need to pass to gcc/g++ to compile and link against the library with
```
pkg-config --cflags sdl
pkg-config --libs sdl
```

---


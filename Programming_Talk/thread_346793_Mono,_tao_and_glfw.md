---
title: "Mono, tao and glfw"
date: 2007-01-26
forum: Programming Talk
---

### Post by Karma_Police on 2007-01-26
I'm trying to use mono.tao, but I have a problem accessing libglfw.
I followed the instructions in the wiki ([http://www.taoframework.com/GLFW_on_Linux](http://www.taoframework.com/GLFW_on_Linux)), ran ldconfig as root several times (even rebooted the computer), changed /etc/mono/config, but I still get this:

```

Unhandled Exception: System.DllNotFoundException: libglfw.so
  at (wrapper managed-to-native) Tao.Glfw.Glfw:glfwInit ()
  at teste.MainClass.Main (System.String[] args) [0x00000] in (...)Main.cs:11
```

Anyone experienced this problem? Anyway to correct it?

---

### Post by Karma_Police on 2007-01-26
:mad: Doh... Should have edited the title before posting... Not very descriptive.

Anyway, I added some flags from here: [http://blog.cgamesplay.com/archives/5-Getting-the-Tao-Framework-to-work-under-Linux.html](http://blog.cgamesplay.com/archives/5-Getting-the-Tao-Framework-to-work-under-Linux.html)

And ended up compiling it like so:
```
gcc *.o -o libglfw.so -shared -L/usr/X11R6/lib -lGL -lGLU -lX11 -lXxf86vm -lpthread -lm
```

And it stopped complaining. I don't have anything working yet, but at least it does not crash.

Also, for anyone trying to use mono.tao, besides adding the ```
<dllmap dll="glfw.dll" target="libglfw.so" />
``` line to /etc/mono/config you should also add ```
<dllmap dll="devil.dll" target="libIL.so" />
``` for libdevil to work (tip from here: [http://www.taoframework.com/forum/index.php?action=recent;start=40](http://www.taoframework.com/forum/index.php?action=recent;start=40))

EDIT: I tried it, and it does indeed work. :D

---


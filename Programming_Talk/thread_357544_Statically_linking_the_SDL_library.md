---
title: "Statically linking the SDL library?"
date: 2007-02-09
forum: Programming Talk
---

### Post by Randomskk on 2007-02-09
I'm trying to release an executable for windows and linux that doesn't need the system to have the SDL libs installed - for instance, on windows I have to bundle the executable with SDL.dll, and on linux I'm just having to assume they have it installed.
I'd rather avoid this if possible, so how can I link the library into the executable such that I can just distribute the slightly larger myfile.exe instead of both my file and the DLL?

Thanks for any help!

(By the way, I'm using mingw to cross-compile for windows).

---

### Post by winch on 2007-02-10
I belive you just pass gcc the -static flag and use sdl-config --static-libs instead of sdl-config --libs.

In order to comply with LGPL license that SDL uses users must be able to replace the SDL library. If you statically link and just provide just the executable users won't be able to replace SDL. If your app is closed source you would probably have to make the .o files available so user can link against an SDL of their choosing. If you app is open source then can just recompile it so nothing to worry about.

---


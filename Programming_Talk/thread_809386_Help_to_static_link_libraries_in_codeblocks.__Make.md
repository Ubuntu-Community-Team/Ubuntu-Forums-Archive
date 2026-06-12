---
title: "Help to static link libraries in codeblocks.  Make executable standalone."
date: 2008-05-27
forum: Programming Talk
---

### Post by papafreebird on 2008-05-27
I need help getting my executable to be self sufficient.  My program will not run on other linux systems without the user first installing an external library libwxgtk2.8-0-ansi.  I would like to include that library into my executable so that the end user will not have to install anything else other than my program. I know I need to static link to my wxwidgets library but I don't know how.

Any help would be appreciated.

---

### Post by nvteighen on 2008-05-27
Just a note: no application is absolutely "self-sufficient", unless you're programming a whole new operating system.

If your program is in C or C++, end user will also need to have the respective Standard Library installed... Yes, also for a simple "Hello World"! The difference is that those libraries are likely to be installed by default.

Static linking may be useful for some contexts, I guess. But the reason to prefer it before dynamic linking will presumably not be "self-sufficiency". Great apps are indeed programmed using scripting languages like Python, thus being absolute "dependent" of another application (the interpreter)...

There's nothing bad to rely on shared libraries... at the end, is what they are for.

Anyway, using gcc, you can static link all needed libraries with:
```

gcc -static (...)

```

---


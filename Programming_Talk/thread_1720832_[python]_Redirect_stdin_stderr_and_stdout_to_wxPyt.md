---
title: "[python] Redirect stdin stderr and stdout to wxPython text box"
date: 2011-04-03
forum: Programming Talk
---

### Post by Crazedpsyc on 2011-04-03
Hello, I would like to make a very very tiny terminal application in wxPython to use with the shell I am making. 
I know I can set sys.stdout to a custom class and have the write method go to a textbox, but that doesn't work with readline, because it apparently requires several other methods. I also don't know how to redirect stdin to a line in a textbox at all. I assume stderr should be about the same as stdout, but I'm not sure.
If there is another wxpython widget that would act more terminal-like, I would be happy to use it, but I'm not sure about using PyGTK for anything.
If you know of an existing wxpython app that has these functions, looking at it would help too.

Thanks!

---

### Post by cgroza on 2011-04-03
Hmm, there is already a library out there for that: [http://sourceforge.net/projects/termemulator/](http://sourceforge.net/projects/termemulator/)

It includes a demo, maybe that will put you on the wheels.

---

### Post by Crazedpsyc on 2011-04-04
Thanks, I'll take a look!

---

### Post by Crazedpsyc on 2011-04-05
That is exactly what I wanted, thanks!

---


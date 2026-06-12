---
title: "Run app without install permissions"
date: 2011-02-15
forum: Programming Talk
---

### Post by Zaycev on 2011-02-15
Hello!
App needs to be run even if there are no permissions for installing or writing on hard disc. So, is it possible to use ActiveX controls and dynamic libraries without installing an application and without  temporary run-time extractions, by simply running EXE file?
Thank you!

---

### Post by nvteighen on 2011-02-15
> **Zaycev said:**
> Hello!
App needs to be run even if there are no permissions for installing or writing on hard disc. So, is it possible to use ActiveX controls and dynamic libraries without installing an application and without  temporary run-time extractions, by simply running EXE file?
Thank you!

In GNU/Linux you can't use ActiveX... If you're into Windows programming, this may not be the best place to ask these questions.

Now, more generally, what you seem to ask is whether you can statically link ActiveX and dynamic libraries. Static linking is the technique by which you include everything into the compiled executable, so that you don't need to install anything but the executable itself. Well, in the first place, "dynamic libraries" and static linking are opposed: usually, you need a special version of the library in other to link it statically. IIRC, Windows static libraries are stored as .OBJ files.

---

### Post by vlaar on 2011-02-15
If your talking about windows, then your going to need a valid security certificate for installing without permission. Those are not easy to come by and that's just mildly spoken.

---

### Post by juancarlospaco on 2011-02-15
In GNU/Linux you can't use ActiveX... In MS Windows you should not use ActiveX...

Try another thing, like Java applets or HTML5

---


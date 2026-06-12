---
title: "glew update"
date: 2014-03-28
forum: New to Ubuntu
---

### Post by sajjadul-islam-bd on 2014-03-28
Hi forum,

I am using the glew version 1.6 and unity 2D package is strongly dependant on glew 1.6.

I want to update the glew so that i can use the recent opengl version (4.4). Now if i remove glew 1.6 from the system , it will remove the unity related software as well resulting the disappearance of the desktop.

How to resolve this isssue ?

I want to update glew to the most recent and stable version and have the unity refer to it as well .


Thanks

---

### Post by grahammechanical on 2014-03-28
How do you intend to install the latest version of glew? If you are using Unity 2D then are you using Ubuntu 12.04? Do you not have Unity 3D? The default Ubuntu user interface of 12.04 is Unity 3D and that uses the Compiz compositor/window manager. Whereas, Unity 2D uses Metacity. So, it should be possible to use a Unity 3D session to remove and re-install glew without breaking the desktop.

You could also install another desktop such as FVWM-Crystal. It should be in the software centre. That will give you a desktop to work from if Ubuntu desktop is removed. I have used FVWM as a fallback UI for when Compiz breaks when I have been testing development branches of Ubuntu. If there is ever a risk of losing or breaking the desktop then I think that it is sensible to have an alternative UI installed just in case.

[http://fvwm-crystal.sourceforge.net/](http://fvwm-crystal.sourceforge.net/)

Regards.

---


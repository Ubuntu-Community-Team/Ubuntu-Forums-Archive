---
title: "elisa media center flashing"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by planemanx15 on 2008-10-29
I just installed 8.10 and set up elisa.  With 8.04 and elisa 0.3.9 it worked fine, but now i dont even get a screen, I get a few flashed and can make out the screen for a second but thats it, if i move the arrow keys and then click enter i see the flash a bit of the screen showing my music or videos, etc, what should I do to fix this?

---

### Post by Andy Armstrong on 2008-11-04
I'm seeing the same thing. I'd be interested to know if anyone is successfully using Elisa on Intrepid.

---

### Post by wolfe on 2008-11-05
I just now installed elisa and it is working great except that I can not access any plugins.

I am assuming that is the gear icon on the initial menu

---

### Post by louman on 2008-11-08
> **Andy Armstrong said:**
> I'm seeing the same thing. I'd be interested to know if anyone is successfully using Elisa on Intrepid.
I'm not seeing the same thing; nothing is working for me at all. :(
Elisa runs, the splash screen displays, and then a black screen sits there and the only way for me to exit is to explicitly kill it.
I believe this is what's responsible:
```
WARN  MainThread      interface_controller        Nov 08 05:04:11  creating frontend frontend1 failed. A full traceback can be found at [Failure instance: Traceback: <type 'exceptions.AttributeError'>: 'NoneType' object has no attribute 'lower'
/usr/lib/python2.5/site-packages/twisted/internet/defer.py:186:addCallbacks
/usr/lib/python2.5/site-packages/twisted/internet/defer.py:328:_runCallbacks
/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py:432:frontend_initialized
/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py:116:create_controller
--- <exception caught here> ---
/usr/lib/python2.5/site-packages/elisa/core/plugin_registry.py:384:create_component
/usr/lib/python2.5/site-packages/twisted/python/reflect.py:426:namedAny
/usr/lib/python2.5/site-packages/twisted/python/reflect.py:377:_importAndCheckStack
/usr/lib/python2.5/site-packages/elisa/plugins/poblesec/main.py:30:<module>
/usr/lib/python2.5/site-packages/elisa/core/utils/i18n.py:92:install_translation
/usr/lib/python2.5/gettext.py:480:translation
/usr/lib/python2.5/gettext.py:437:find
/usr/lib/python2.5/gettext.py:132:_expand_lang
/usr/lib/python2.5/locale.py:298:normalize
] (elisa/core/interface_controller.py:88)
WARN  MainThread      interface_controller        Nov 08 05:04:11  Could not load any frontend (elisa/core/interface_controller.py:123)
```

---

### Post by planemanx15 on 2008-11-09
After some testing I relized that if you turn the graphics down (right click on desktop-visual effects-click the first or second bullet).  Elisa will work after the graphics are turned down.

---

### Post by lbarnes on 2008-11-09
not trying to hijack the thread, but was wondering
if you can you use elisa to send media to a ps3
like you can with windows media player 11?

---

### Post by lbarnes on 2008-11-09
oh yeah, i just used synaptic and it worked fine for 8.10 64

---


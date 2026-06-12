---
title: "Orange screen"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by heldemanpieter on 2013-05-06
I have installed Ubuntu 13.04 on my desktop and it works 100%. Then with the same DVD I installed it on a HP Pavilion laptop. It installed just fine. Booting it loads up to where you sould see the work screen, but turns orange. Somebody told me to press Ctrl + F1 or Ctrl + F7 but nothing happens. If you boot with the disk and click on try and not install it works fine.
Heldeman

---

### Post by Svictor on 2013-05-06
The combination is Ctrl+Alt+F1 This gets you to a text-only terminal. Then Ctrl+Alt+F7 gets you back to the graphics screen. The latter probably doesn't start as expected, hence the orange screen. There may be many causes to that, but most revolve around a faulty graphics driver. Do you know the name of your graphics card?
If not you can find it with 
```
lspci
```
That's to be written in the terminal at ctrl+alt+f1 once you login in text-mode. Look for the lines with "VGA compatible controller". If any of them has NVIDIA or ATI in it, then you can start googling for that. These two graphic card brands have both opensource and proprietary drivers. Ubuntu installs the opensource driver by default but you may need the proprietary one to make your model work properly.

---


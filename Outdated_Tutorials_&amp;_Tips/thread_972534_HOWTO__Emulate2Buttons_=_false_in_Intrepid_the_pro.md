---
title: "HOWTO:  Emulate2Buttons = false in Intrepid the proper way"
date: 2008-11-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Rhubarb on 2008-11-05
When playing games in 8.10 Intrepid Ibex being able to press the left and right mouse buttons without registering as a middle click is rather important.

As the new xorg in 8.10 depends even less on your /etc/X11/xorg.conf (if at all now), functionality for setting options such as the Emulate2Buttons in your xorg.conf has moved into the HAL (Hardware Abstraction Layer).

So, to get it working properly, so your mouse doesn't register a left + right = middle click, but rather just 2 events (left mouse and right mouse):

```
gksu gedit /etc/hal/fdi/policy/mouse.fdi
```

Enter in your password when prompted, then copy and paste this into gedit:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input.mouse">
   <merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
  </match>
 </device>
</deviceinfo>
```

Now all you need to do is to unplug your mouse, then plug it back in again.  Or you can restart your computer.

---


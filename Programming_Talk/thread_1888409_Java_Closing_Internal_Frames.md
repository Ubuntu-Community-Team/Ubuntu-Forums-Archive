---
title: "Java: Closing Internal Frames?"
date: 2011-11-29
forum: Programming Talk
---

### Post by fallenshadow on 2011-11-29
Does anyone know how to close an opened internal frame?

I know the idea is to setVisible to false but first I need some way to find the open frame in order to try and close it.

---

### Post by 11jmb on 2011-11-29
I think it would be better to use the dispose() function to close the frame, unless you plan on making it visible again in the future

JDesktopPane has the functions getAllFrames() and getSelectedFrames() to access its internal frames

---

### Post by fallenshadow on 2011-11-30
I understand how to close all internal frames but I wanna be able to close each of them individually. How would this be done?

---

### Post by 11jmb on 2011-11-30
You will have an array of every subframe returned by getAllFrames() you are then free to do any searching/manipulation that you please. For example, you can iterate through and check each frame for a unique identifier, such as its title, and dispose the frame titled "spam and eggs" leaving the rest open. Or as another example, perhaps you could close any frame that is not the selected frame

---


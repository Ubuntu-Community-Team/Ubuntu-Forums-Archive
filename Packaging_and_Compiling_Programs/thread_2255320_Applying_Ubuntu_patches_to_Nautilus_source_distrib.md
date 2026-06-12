---
title: "Applying Ubuntu patches to Nautilus source distribution"
date: 2014-12-04
forum: Packaging and Compiling Programs
---

### Post by veddox on 2014-12-04
Hello everyone,

I recently downloaded the Nautilus source code from the Ubuntu repository since I wanted to play around with it a little. (I'm still a newbie as far as system programming is concerned, so please bear with me ;-) ) I managed to compile it eventually, but found that the compiled version had the look-and-feel of the normal GNOME desktop; i.e. it had the drop-down menu button instead of the Unity menubar at the top, etc. Then I discovered that the source distribution also included a folder with Ubuntu-specific patches, including some that where quite obviously designed to change the look-and-feel. Unfortunately, I do not know how to apply those patches automatically, and I don't particularly fancy applying a couple of 500-line patches by hand...

Could somebody explain to me how to do that, or point me to a tutorial that does so? Thank you very much!

---

### Post by mikewhatever on 2014-12-04
A patch is usually applied with the **patch** command (see man patch for more info).

---


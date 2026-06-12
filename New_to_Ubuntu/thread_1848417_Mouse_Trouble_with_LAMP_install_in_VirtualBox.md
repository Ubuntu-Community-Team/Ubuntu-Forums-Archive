---
title: "Mouse Trouble with LAMP install in VirtualBox"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by BEEDO on 2011-09-22
I just installed Ubuntu 11.04 Desktop in VirtualBox. In Terminal I ran:

sudo apt-get tasksel

and then, after taskel was "grabbed"(sorry-I don't know the proper term):

sudo tasksel

then I selected LAMP server. I was able to use arrows to select a single item on the list, so I selected LAMP. But I don't know how to click the <Ok> so I can move on. I should have been able to choose multiple selections as well, but that is not the case. The indicator icon in the lower right on the VirtualBox screen for the mouse pointer indicates "pointer is captured" and "Mouse integration is on".

Help!

---

### Post by Lisiano on 2011-09-22
What you see in a terminal is called a ncruses menu. Text based in other words, if you ever installed XP you might remember a menu similar to this. To switch between "areas" just press Tab. Also to mark a item, use Space.

---

### Post by BEEDO on 2011-09-22
Thank you! I did not try the space bar.

---

### Post by Lisiano on 2011-09-22
Btw. Don't use tasksel to remove LAMP, there is a chance it will take down your whole desktop with it. You can remove LAMP with Synaptic though.

---


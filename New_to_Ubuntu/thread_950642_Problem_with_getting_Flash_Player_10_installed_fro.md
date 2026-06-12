---
title: "Problem with getting Flash Player 10 installed from deb"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by laptoplinux on 2008-10-17
I uninstalled the flash player from synaptic, then went to Adobe's site and downloaded the .deb file for flash player 10.  It appeared to install fine, but afterwards, Firefox was not able to see it.  It didn't think it had flash installed at all.  None of the how to articles I found mentioned any other additional steps that were needed.  I also tried downloading the .tar.gz file and running the install script.  Again, it said the installation went though ok, but Firefox still couldn't see it in about:plugins.

I finally had to just go back to the 9.x flash version in synaptic, which Firefox detected without a problem.

Anyone else experience this?  What am I missing here?
(running Ubuntu 8.04.1)

---

### Post by odin1965 on 2008-10-17
I seem to be getting the same thing, following the instructions from Tombuntu. Youtube and such sites simply display the message that additional plugins are required.

---

### Post by nothingspecial on 2008-10-17
Sorry if this is a waste of time because it worked flawlessly for me.

Did you mark flashplugin-nonfree for complete removal (--purge)?

Did you close firefox whilst removing the old flash and installing the new one?

---


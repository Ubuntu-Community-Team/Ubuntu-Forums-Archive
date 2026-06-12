---
title: "how to use .so files??"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by m7md.osma on 2011-12-18
Hi dears,
I am using ubuntu11.04 and I downloaded flash player .tar.gz file. then I extract it to fine that there is .so file "libflashplayer.so". I don't know what to do with this file.

So anyone can give me useful help will be kind.;)

yours,
M.Osama

---

### Post by dargaud on 2011-12-18
To answer your question: .so files are dynamic libraries, like DLLs in Windows. They are normally provided by the system, but can be installed by apps.
Now in your case you should:
- not install manually but use the flash provided by Ubuntu: "sudo aptitude install flashplugin-installer"
- if you want to install manually for some reason, there are probably some instructions in a README file in the tar file. It most likely says something like: type "./configure", then "make", then "sudo make install"

---

### Post by kaldor on 2011-12-18
> **m7md.osma said:**
> Hi dears,
I am using ubuntu11.04 and I downloaded flash player .tar.gz file. then I extract it to fine that there is .so file "libflashplayer.so". I don't know what to do with this file.

So anyone can give me useful help will be kind.;)

yours,
M.Osama

There are a few ways to do this.

If you want to easily install Adobe Flash, use the Software Centre as the above poster said. This will give you the latest stable version of Flash. [Click here]("apt:flashplugin-installer") to do this.

If you want to use a testing version from the Adobe site, then you'll probably want to place the .so file in Mozilla's plugins folder. Drag and drop the file into the *.mozilla/plugins* directory in your home folder. Press Ctrl and H to view hidden folders.

Finally, if you want to install all of the common plugins and codecs, install the Ubuntu Restricted Extras package in the Software Centre. [Click here]("apt:ubuntu-restricted-extras") to do this.

Hope it works out for you :)

---

### Post by oldos2er on 2011-12-18
Copy or move it to /usr/lib/mozilla/plugins/
Easiest way to do this is to run ```
gksu nautilus
``` and drag and drop.

---

### Post by m7md.osma on 2011-12-23
thanx every one for your help
I am really grateful of your answers

yours,
Mohamad Osama

---


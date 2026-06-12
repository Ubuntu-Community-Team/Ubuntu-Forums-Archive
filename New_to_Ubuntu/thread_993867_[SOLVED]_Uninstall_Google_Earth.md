---
title: "[SOLVED] Uninstall Google Earth"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by dawiba on 2008-11-26
Hi

I installed Google Earth using this command

sh GoogleEarthLinux.bin

which I got from following one of various links here on the forums.

Everything installed fine, but the program doesn't run very well.

I'd like to uninstall, but don't see how to using add/remove or the package manager. I see a folder called Google Earth in my home folder. It crossed my mind that I could simply drag Google Earth from here to the recycle bin, as I would do on a Mac.

Can I do this?

---

### Post by philinux on 2008-11-26
[http://ubuntuforums.org/showthread.php?t=991761](http://ubuntuforums.org/showthread.php?t=991761)

---

### Post by bobnutfield on 2008-11-26
It was probably installed in your home directory.  Make sure you are in that directory and try:

> sudo sh /usr/share/google-earth/uninstall 

I believe that Google Earth has an uninstall script.

---

### Post by dawiba on 2008-11-26
Many thanks!

I managed to uninstall using option 5 from this;

[How To Uninstall Google Earth](http://www.ehow.com/how_2279483_uninstall-google-earth-ubuntu.html).

Thanks again and I promise to do a more thorough search before I ask for help next time!

---

### Post by aheckler on 2008-11-26
Be sure to mark this thread as solved by using the **Thread Tools** menu at the top-right. :)

EDIT: [SIZE="1"]Woo, my 200th post! *dances*[/SIZE]

---

### Post by dawiba on 2008-11-26
Done :)

---


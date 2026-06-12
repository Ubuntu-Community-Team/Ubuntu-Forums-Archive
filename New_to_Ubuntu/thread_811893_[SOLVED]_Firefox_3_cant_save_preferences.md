---
title: "[SOLVED] Firefox 3 cant save preferences"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by stevev on 2008-05-29
Hi,

Been running Hardy on 2 PC's fine until the latest updates.

It seems one PC is still fine but on the other I cant change any of the preferences in Firefox, or rather you can change say your home page and it will work fine all the time Firefox is still open but close the window and its back to the default of chrome://ubufox/content/startpage.html

Anyone got any ideas as to whats gone wrong on this PC


Steve

---

### Post by aysiu on 2008-05-29
Try pasting this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R steve:steve /home/steve/.mozilla
``` Substitute in your actual username if it's not *steve*

---

### Post by stevev on 2008-05-30
Cheers for that.

I checked the ownership of the .mozilla files and to my amusement the prefs.js file was owned by root.

This was the only file so I have no idea what happend when upgrading this pc, the first one I did worked fine.

Oh well no problem now as I have changed the owership and it is working fine, so thanks for the pointer.

Steve

---


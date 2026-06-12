---
title: "Place launcher in Gnome Menu"
date: 2009-09-20
forum: Programming Talk
---

### Post by chosenbeans on 2009-09-20
I am making a small script to install another script I made for a friend. This friend of mine is a noob when it comes to terminal. Baically the installer will download my package, decompress it, then move it to /usr/bin though I want to take it a bit further.

What command will create a shortcut to the script and place it in the applications menu under the System Tools category? This way all he has to do is click the icon (which I would also like to include) to start the script.


Thanks for the help!

---

### Post by Reiger on 2009-09-20
To do _that_ you you must supply a dot desktop file; look under /usr/share/applications for examples. Typically you supply 2 things (1) a kickstart script that launches the app; (2) a dot desktop file which instructs the Desktop Environment (Gnome/KDE/w/ever) to launch that script.

AFAIK:

In the interest of keeping the system tidy it is advisable your script installs those things in /usr/local. E.g.:

(1) under /usr/local/bin
(2) under /usr/local/share/applications/

This way system upgrades should leave your script well & alone; /usr/local is basically the personal playground of the administrators; as opposed to the default /usr tree which is for software from the repositories.

---

### Post by chosenbeans on 2009-09-20
> **Reiger said:**
> To do _that_ you you must supply a dot desktop file; look under /usr/share/applications for examples. Typically you supply 2 things (1) a kickstart script that launches the app; (2) a dot desktop file which instructs the Desktop Environment (Gnome/KDE/w/ever) to launch that script.

AFAIK:

In the interest of keeping the system tidy it is advisable your script installs those things in /usr/local. E.g.:

(1) under /usr/local/bin
(2) under /usr/local/share/applications/

This way system upgrades should leave your script well & alone; /usr/local is basically the personal playground of the administrators; as opposed to the default /usr tree which is for software from the repositories.

Thanks I will give it a try and report back.

---

### Post by Can+~ on 2009-09-20
It would be wiser to pack it in a .deb.

[http://www.ibm.com/developerworks/linux/library/l-debpkg.html](http://www.ibm.com/developerworks/linux/library/l-debpkg.html)

---


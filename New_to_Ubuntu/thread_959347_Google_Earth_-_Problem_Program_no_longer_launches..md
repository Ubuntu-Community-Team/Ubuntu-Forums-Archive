---
title: "Google Earth - Problem: Program no longer launches."
date: 2008-10-26
forum: New to Ubuntu
---

### Post by suomalainen on 2008-10-26
Ubunteros,

I'm using Linux Ubuntu 7.10 64 bit. I have Google Earth installed and use it often without any issues.

Today, however, is another story. For whatever reason, Google Earth will not launch fully.

As can be seen from the attached screen shot a Google Earth window appears and program is said to be initializing but nothing happens. :(

If you can help me get Google Earth to work again, I'd sure like to hear from you.

Thanks very much!!!

---

### Post by bwhite82 on 2008-10-26
Perhaps some update broke the installation? Would it be a problem to uninstall and reinstall it?

---

### Post by suomalainen on 2008-10-26
I reinstalled Google Earth via Synaptic Package Manager and saw straight away that the Google Earth boxes were unchecked. But they should have been checked because Google Earth is already installed.

Regardless, I reinstalled Google Earth and then I go to Applications --> Internet and the Google Earth icon appears twice.

When I uninstall Google Earth via Synaptic Package Manager then Google Earth appears just once in Applications --> Internet.

Be it as it may, I still cannot launch Google Earth.

Now I would also like to know how to uninstall Google Earth since it is still appearing in Applications --> Internet BUT NOT IN SYNAPTIC PACKAGE MANAGER.

Thanks for helping me!

---

### Post by bwhite82 on 2008-10-26
How did you originally install it? My guess is not through Synaptic.

---

### Post by suomalainen on 2008-10-26
I installed it 1 year ago and since then it was working perfectly.

If I remember correctly I downloaded the bin file  from Google's web site.

---

### Post by bwhite82 on 2008-10-26
.bin's usually include uninstallers with them. Check a couple directories for it:

/usr/bin/googleearth? (maybe)

or

/home/yourusername/.googleearth?

look in those places for a .bin uninstaller.

Edit: or under /opt

---

### Post by suomalainen on 2008-10-26
Thanks for the advice.

Google Earth was uninstalled and this time re-installed using Synatpic Package Manager.

Again the results are the same. The splash screen appears and program fails to initialize....

I'm using 64 bit machine and Ubuntu 7.10

---


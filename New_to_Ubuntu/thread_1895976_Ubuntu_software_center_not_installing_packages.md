---
title: "Ubuntu software center not installing packages?"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by matronix on 2011-12-15
I am using Ubuntu 11.10. Am trying to install synaptics package manager. I go into Ubuntu software center, search for synaptics, click on install put in my password in the authentication window, but I get the messgae:

Failed to download package files.
Check your internet connection.

But there is nothing wrong with my internet connection. I am able to go to any other website. I tried downloading another software "tuxpaint" from the software center and the same thing happens.

I checked the wireless settings and everything looks fine.

Any idea what might be going on?

---

### Post by Gone fishing on 2011-12-16
What happens if you sudo apt-get update

If it works try sudo apt-get install synaptic

Do you connect through a proxy?

---

### Post by matronix on 2011-12-16
Thanks Gone Fishing. That worked beautifully!!!

---

### Post by Gone fishing on 2011-12-16
Thanks - still wondering if software center and synaptic work?

If they don't let us know I'd guess its a proxy problem

---

### Post by tears of the river on 2011-12-16
if the problem is solved then please mark the thread as solved

:)

---

### Post by matronix on 2011-12-16
Ok Done. Thanks.

---


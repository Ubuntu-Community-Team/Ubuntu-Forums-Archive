---
title: "[SOLVED] help with nvidia driver update problem."
date: 2008-08-04
forum: New to Ubuntu
---

### Post by NeoEIRE on 2008-08-04
hi, i have just installed the new ubuntu 8.04.1 operating system...

i am trying to enable my nvidia drivers but when it trys to download, i get an error message ending in a 404 quote...


any ideas?


plus will the new OS run 3d games like battlefield 2 or BF1942?

thanks
shane

---

### Post by Inxsible on 2008-08-04
A HTTP 404 error occurs when the file you requested does not exist on the server. You should probably try after some time and if that doesn't work, try a different mirror.

Linux is still far behind in the gaming world - not necessarily because of Linux. Do not expect to play the games that you play in Windows. I am not sure about the games you mentioned, but there are a few which can be played using Wine.

Try it out or look up more info at winehq.com

---

### Post by Elfy on 2008-08-04
First check that you have restricted enabled in software sources (sys - admin menu) while you're there main, universe, multiverse and partner on 3rd party tab and after it has reloaded check hardware driver again.

If you still get a 404 - it could be down although yesterday I saw a thread in which the deb it was trying to download no longer existed.

---

### Post by phidia on 2008-08-04
> The 404 or Not Found error message is an HTTP standard response code indicating that the client was able to communicate with the server
-from wiki
Try updating your sources. There's a button in synaptic for that or using apt in terminal > sudo apt-get update and try to get the nivida-glx package again.

---

### Post by NeoEIRE on 2008-08-04
> **phidia said:**
> -from wiki
Try updating your sources. There's a button in synaptic for that or using apt in terminal  and try to get the nivida-glx package again.


thank you this helped it to work right and download and activate the restricted drivers

:guitar:

---


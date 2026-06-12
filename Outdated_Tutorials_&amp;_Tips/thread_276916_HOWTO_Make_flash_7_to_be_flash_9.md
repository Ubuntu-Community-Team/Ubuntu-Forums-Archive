---
title: "HOWTO: Make flash 7 to be flash 9"
date: 2006-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by nookie on 2006-10-13
Some of the homepages are today require flash 9 but linux have for now flash 7. There is a simple way to make your flash 7 player into flash 9.

Open the file **pluginreg.dat** in your home directory meaning **~/.mozilla/firefox/**.

Press **ctrl + h** to see all hidden files and you will see pluginreg.dat there.

Change the line 
**Shockwave Flash 7.0 r63:$**
into
**Shockwave Flash 9.0 r63:$**

Now you should be able to run sites which require Flash 9.
Enjoy! 

//Nookie

---

### Post by PriceChild on 2006-10-13
This may cause problems with some sites.

Flash 9 has more features that Flash 7 so don't be surprised "when" you run into problems.

---

### Post by DC@DR on 2006-10-14
I'd rather waiting for the official Flash 9 release for Linux than hacking like this just in order to display some specific sites :)

---

### Post by coastdweller on 2006-10-15
Doesnt work, causes browser to either crash or fail to render the flash correctly.

---


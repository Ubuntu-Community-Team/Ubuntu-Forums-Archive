---
title: "HPLIP &amp; Cups won't print landscape"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by kneewax on 2008-07-02
HELP!  I cannot get a Landscape print in any application that uses the HPLIP cups driver for my HP Photosmart 2575 PSC. 

All the right options are there, but selecting them makes no difference - every print job comes out in default portrait mode.

Can anyone help -PLEASE!

---

### Post by cmnorton on 2008-07-02
Is this an application using the CUPS library, or did you install HPLIB to work with a printer? 

How are you trying to configure this printer? That is which interface are you using?

This is a longshot, but, even though Ubuntu's printer configuration interface is very good -- and that's not lip service good, but very very good -- I still prefer to configure through CUPS' localhost:631 interface. (Just make sure the username doing this is in the lpadmin group.)

It could be you have to tweak this printer that interface.

---


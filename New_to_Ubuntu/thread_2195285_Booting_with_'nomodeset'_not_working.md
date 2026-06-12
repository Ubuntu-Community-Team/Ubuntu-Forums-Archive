---
title: "Booting with 'nomodeset' not working"
date: 2013-12-23
forum: New to Ubuntu
---

### Post by felipehernandezbarroso on 2013-12-23
Forgive me if I am a bit terse in this post; I have to use my phone to type.

I just used the 'Additional Drivers' tab in system settings to download the nvidia-319 driver, and rebooted to install.  I am getting an error at 'load fallback graphics devices'.  I suspect this has to do with the fact that I had previously installed an nvidia driver from a .run file (for CUDA purposes).  So I am trying to get to a working terminal so that I can revert to nouveau.  

I have tried editing the boot settings in grub, replacing 'quiet splash' with 'nomodeset'.  When I do this a black and white login screen briefly appears (<1 sec) and then I am left with a black screen with a cursor.  Failsafex mode has also failed.  

Let me know what else I should try, and any more information I should provide.

---

### Post by Bashing-om on 2013-12-23
felipehernandezbarroso; Hi !

Instead of 'nomodeset' , remove "quiet splash" and add the term "text" - without the quotes - . This will boot to a text login.
Login here and enter your password,

At this point the jockey-gtk tool may be of benefit .

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by buzzingrobot on 2013-12-24
If you can boot successfully, and still want the Nvida driver, try to backout the install from Nvidia's .run package, then remove the Additional Drivers package, which should revert you to Nouveau. You can then, after rebooting, go for the Additional Drivers install again.  

It's my experience that the Additional Drivers install and the install package from Nvidia do not play at all well with each other.

---

### Post by felipehernandezbarroso on 2013-12-24
Thanks guys!  I did, well, exactly what both of you told me to do and now I have a working computer!

---

### Post by Bashing-om on 2013-12-24
felipehernandezbarroso; Outstanding  !

You do good work.

[INDENT][INDENT]Happy trails to you
[/INDENT][/INDENT]

---


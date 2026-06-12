---
title: "black screen acer lappy"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by fattyz on 2011-10-28
Black screen on boot after upgrade manager ran ubuntu 11.04
.  I can kind of see the login screen.  I used to be able to correct this by running previous versions of Ubuntu.  Now that produces a black screen as well.  I figured Id make a boot disk for 11.1 but I can't get the computer to boot off it.  Now I get a .rar file instead of an .iso file and when I extract I can't make a boot disk.

I'm pretty stuck here, any help appreciated

FattyZ

---

### Post by Rave Gloves on 2011-10-28
I had a similar problem what i did to fix it was. 

When ubuntu is at the boot screen press Esc to get the grub menu up. 
 Find the default ubuntu kernel. It is the top one, instead of hitting enter hit the E key. 
use the arrow keys to get to the area that says ```
Quiet splash
``` go to the end of that line and type ```
nomodeset
```

then press Ctrl+X to boot. 
This will work until you restart. It may be at a terrible resolution though. Once i got it to boot this way i then ran the update manager and it fixed itself. Don't know if it will work with you though.

---

### Post by fattyz on 2011-10-29
Thx!  That worked.  The res looks a bit off but i'm sure it'll be easier now that the system comes up.

I had searched around before and most of the solutions were beyond my limited capacity as a linux user.  I could not even read a lot of them.  There was one other one that said to type in a different code at the same spot but it either did not work or I typed it in wrong.

Lots of replies along these lines assume you understand the syntax required,  I don't.

I'm doing the distro upgrade to 11.1 in hopes all will be well again, then I'll mark this solved.  :  )

Thx again,

FattyZ

---

### Post by fattyz on 2011-10-29
FAIL  Still get black screen at start up p;us now I have to get used to a new thing and try to get my settings back,(classic mode for me) sigh. It says I'm a guest on my own system, oh well.  This is quite a bug.  Thanks for your solution though as it works with both versions and at least I am up and running.

FattyZ

---

### Post by fattyz on 2012-09-21
NOT SOLVED but I have all working by selecting 'previous Linux versions' from bootloader and everything else so good bye.

:guitar:

---


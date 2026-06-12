---
title: "[SOLVED] Flash Videos Not Playing Sound"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Bonzzai on 2008-06-11
I actually just got started on Ubuntu... I've only had a little bit of experience with Linux before, but I know a little bit about getting around and such.

I know that last night sound was working for flash videos, such as YouTube. But now they're not... I'm using Firefox 3.0 (I believe) on the newest version of Ubuntu. Updated last night.

If you need any other information, go ahead and ask. (:

P.S. - I just checked, and it won't work for Homestarrunner.com, so... It's just flash in general.

I updated to the newest version of Flash Player and cleared my cache, but still no help :[

---

### Post by rainwalker on 2008-06-11
Are you using Pulse Audio? If so, you could try installing the libflashsupport package

---

### Post by _sphinx_ on 2008-06-11
You can try the following: 
```
mv ~/.asoundrc .asoundrc_bak
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf_bak

```
and restart firefox

---

### Post by Bonzzai on 2008-06-11
@rainwalker
I... don't know if I'm using that, actually n__n;

@_sphinx_
I tried typing that in, but for both it just said no file or directory.

---

### Post by _sphinx_ on 2008-06-11
[http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb](http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb)
install this pacakage, it should work, as ti worked for me..
good luck..

---

### Post by Bonzzai on 2008-06-11
> **_sphinx_ said:**
> [http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb](http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb)
install this pacakage, it should work, as ti worked for me..
good luck..

Thanks a bunch! That did the work for me n__n
Great, it was really bugging me xD

---

### Post by Vanderdan on 2008-06-11
Is there a version of that package for 64bit? When I tried to install it I was told it was the wrong architecture.

---

### Post by _sphinx_ on 2008-06-11
You can refer to the following post
[http://ubuntuforums.org/showthread.php?t=624769](http://ubuntuforums.org/showthread.php?t=624769)

---

### Post by rainwalker on 2008-06-11
> **Bonzzai said:**
> Thanks a bunch! That did the work for me n__n
Great, it was really bugging me xD

You installed libflashsupport, so you must be using PulseAudio. Just letting you know for future reference :)

---

### Post by Vanderdan on 2008-06-11
> **_sphinx_ said:**
> You can refer to the following post
[http://ubuntuforums.org/showthread.php?t=624769](http://ubuntuforums.org/showthread.php?t=624769)

Thank you. I'll look into it.

---

### Post by Bonzzai on 2008-06-11
> **rainwalker said:**
> You installed libflashsupport, so you must be using PulseAudio. Just letting you know for future reference :)

Ahhh. Thanks for the info (:

---


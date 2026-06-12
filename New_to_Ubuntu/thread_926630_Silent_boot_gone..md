---
title: "Silent boot gone."
date: 2008-09-22
forum: New to Ubuntu
---

### Post by kauboy on 2008-09-22
I reinstalled Ubuntu 8.04 for some reasons and it ended up that my Fedora 9, which used to boot with the cool "progress bar" is now gone and when I choose it from the GRUB, it boots up with all the boot scripts like "Starting xyz ...  [OK]" and so on. I'ld like to have my "Silent boot" back for Fedora 9, Ubuntu boots up "silently" without displaying the scripts. Any suggestions to get back the same for Fedora?? I'm asking this here because its my Ubuntu GRUB which loads Fedora 9. And also, I feel more at home here at Ubuntu Forums. :)

---

### Post by roquefilipe on 2008-09-22
well, to remove the splash screen in Ubuntu, I removed the splash word from the options in the grub menu:

```
kernel          /vmlinuz-2.6.24-19-generic root=UUID=a2b8da91-7267-4016-ac09-e367e572f611 ro quiet splash
```

So my guess is that you just need to add it instead, but beware that Fedora might be different.

---

### Post by kansasnoob on 2008-09-22
Sounds like it could be a uuid problem. Look at coffeecat's posts (especially post #5) here:

[http://ubuntuforums.org/showthread.php?t=857565](http://ubuntuforums.org/showthread.php?t=857565)

But I've never messed with Fedora!

---


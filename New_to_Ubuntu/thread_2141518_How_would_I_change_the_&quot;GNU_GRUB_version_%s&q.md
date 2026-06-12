---
title: "How would I change the &quot;GNU GRUB version %s&quot; title"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by ephillips26 on 2013-05-02
Hello, I am having significant problems modifying the very top title.  NOT the menuentries. have my boot order all set up, renamed the boots, and custom background, and it looks AWESOME! I just wanted to change the top to Ernies Boot Menu. I have done searches. Afterard I went into /boot/grub/locale/ then I converted all of the .mo files to .po file; where applicable, I changed "GNU GRUB version %s", to "Ernies Boot Menu", then I converted the .po back to .mo files and replaced them. Still no luck :-( Really wish I could figure this out. Thank you in advance.

---

### Post by deadflowr on 2013-05-02
I would think you'd have to look into either the header file or the debian_theme file in /etc/grub.d.

---

### Post by ephillips26 on 2013-05-03
I have checked there already. No luck.

---

### Post by grahammechanical on 2013-05-03
I would guess that it is hand coded into the packaging by the Ubuntu developers. If you managed to change it the changes would be lost the next time that packaged was updated.

Regards.

---

### Post by galgalesh on 2013-05-03
Have you tried the "grub customizer" ?

[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

*edit: I don't think it can change the actual top title, they just use "title" for the name of the os...*

---


---
title: "[SOLVED] Funny Characters are little boxen - help pls."
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Mega_Fauna on 2008-06-01
Hi,

Ubuntu is displaying many of the funny characters (i.e. Umlauts and apostrophes) as little square boxes. How do I repair this please?

---

### Post by sayakb on 2008-06-01
You need to install more fonts:
```
sudo apt-get install msttcorefonts
```

You may also download and copy fonts to /home/username/.fonts folder.

---

### Post by Mega_Fauna on 2008-06-01
> **LinuxIsInnovation said:**
> You need to install more fonts:
```
sudo apt-get install msttcorefonts
```

You may also download and copy fonts to /home/username/.fonts folder.


Hi 

I installed **msttcorefonts** and it worked:)

I should note however that the changes will not show up until the user has logged out/in again or regenerated their fonts cache with:

```
sudo fc-cache -fv
```

as found [here]("http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/").

Thanks for the help, and for knowing exactly what I was looking for when facing a problem (for a newb like me).

---

### Post by SunnyRabbiera on 2008-06-01
that is why we are here.

---


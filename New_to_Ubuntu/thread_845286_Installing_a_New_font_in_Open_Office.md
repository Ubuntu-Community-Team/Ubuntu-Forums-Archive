---
title: "Installing a New font in Open Office"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by SusieSA on 2008-06-30
Hi

How do I get Comic Sans font as one of the Open Office fonts?

Thanks
SusieSA

---

### Post by adityakavoor on 2008-06-30
```
sudo apt-get install msttcorefonts
```

---

### Post by silkstone on 2008-06-30
And if you want to install any additional .ttf fonts that aren't in that package, create a new folder called **.fonts** in your home folder, and just copy the .ttf files there. They should then be available to OpenOffice and other applications, although you may have to reboot for the change to take effect.

---


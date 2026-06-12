---
title: "Difficulty burning discs"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by CaptainThunderwolf on 2012-12-08
Hey there, forum. Over the last few days I've made several attempts to burn ISO images to blank DVDs (Attempting to burn my old Star Wars: KoTOR digital backup onto hard copy, if it matters), but every program I've used (Brasero, Xfburn, AcetoneISO) has been unable to identify my computer's CD/DVD device. Now, I might be using a not quite seven year old dinosaur of a Lenovo laptop, but I know it does have CD/DVD burning functionality. The stupid thing has no problem copying files straight from a CD or DVD, but when I actually try to write data ONTO a disk, it's a no-go. So ah, help me? Please?

---

### Post by andrew.46 on 2012-12-08
Try directly from the commandline:

```
growisofs -dvd-compat -Z /dev/dvd=my_file.iso
```

where *my_file.iso* will have to be the path to and name of your own file. If this does not work hopefully there will be a useful error message at least.

---


---
title: "ImportError: No module named PIL"
date: 2007-05-05
forum: Programming Talk
---

### Post by trotur on 2007-05-05
I have a python script named ooo2-thumbnailer (it's copied from post [http://ubuntuforums.org/showpost.php?p=466348&postcount=12)](http://ubuntuforums.org/showpost.php?p=466348&postcount=12)).

When I run script in terminal, I get following error
```
Traceback (most recent call last):
  File "./ooo2-thumbnailer", line 7, in <module>
    from PIL import Image, ImageEnhance
ImportError: No module named PIL
```

Do I have to install something or how do I get PIL?
Please note that I haven't done any programming with Python (but Java instead is quite familiar). I would though like to have thumbnails in OpenOffice-files.

---

### Post by meng on 2007-05-05
Try:
sudo apt-get install python-imaging

(or use whatever package management system you prefer)

---

### Post by trotur on 2007-05-05
Thank you meng.
That solved my problem.

---

### Post by meng on 2007-05-05
Pleased I could help. Good luck with Python.

---


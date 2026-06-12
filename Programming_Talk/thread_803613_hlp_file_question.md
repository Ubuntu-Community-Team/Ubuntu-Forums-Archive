---
title: "hlp file question"
date: 2008-05-22
forum: Programming Talk
---

### Post by totherw on 2008-05-22
Please tell me how to open and modify the hlp file in the isolinux directory in the ubuntu cd image.
Thank you!

---

### Post by mrMango on 2008-05-22
Though I haven't done much looking, it seems that they're plain text files with a few ASCII squences for bold text and the like. The ISOLINUX config file refers to text files like f1.txt, etc. Check isolinux.cfg for more info. I would also look at the documentation for debian-installer; hopefully some useful information would be in there.

---


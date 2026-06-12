---
title: "Put a shortcut to my downloads folder on my desktop?"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by hamstermoon on 2012-02-05
I managed to do this on one laptop but can't seem to do it (or remember how to) since I have set up another. Can someone talk me through it?

---

### Post by Carborundum on 2012-02-05
Create a launcher (by right-clicking) on you desktop and put "thunar Downloads" in the command field.

Edit: On second thought, a better idea would be to use a symbolic link. Open a terminal and run these commands:

```
cd ~/Desktop
ln -s ~/Downloads Downloads
```

---

### Post by hamstermoon on 2012-04-12
Thank you. I have finally got round to doing that and now have my link!

---


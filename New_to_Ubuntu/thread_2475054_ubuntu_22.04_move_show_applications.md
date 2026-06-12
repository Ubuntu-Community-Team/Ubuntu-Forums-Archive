---
title: "ubuntu 22.04 move show applications?"
date: 2022-05-15
forum: New to Ubuntu
---

### Post by greenmeanie2 on 2022-05-15
I want to move **SHOW APPLICATIONS** to the beginning of the bar but I can't seem to find any settings for that in ubuntu. I have also tried finding a shell extensions for moving it and can't seem to find one in there either.
Is there a way to move it in Ubuntu **22.04**?

---

### Post by #&amp;thj^% on 2022-05-15
This should work for you:
```
gsettings set org.gnome.shell.extensions.dash-to-dock show-apps-at-top true

```

You can also remove it with:

```
gsettings set org.gnome.shell.extensions.dash-to-dock show-show-apps-button false
```

---

### Post by greenmeanie2 on 2022-05-15
That worked thank you.

---


---
title: "Desktop Image and Desktop problem!"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Epidemic_HardyBoy on 2008-06-12
I set an image as a desktop background, but now I cant select things or even see them, and on top of all this I can even change my background or right click the desktop. Any help?

(Hardy Heron 8.04)

---

### Post by powerpleb on 2008-06-12
Just a suggestion, have you tried CTL + ALT + BACKSPACE and logging in again?

---

### Post by Epidemic_HardyBoy on 2008-06-12
Well, yea, twice, but third times a charm, thanks man.

---

### Post by iaculallad on 2008-06-12
You could also try changing desktop picture using your terminal:

```
gconftool-2 -t str --set /desktop/gnome/background/picture_filename /path/picture.jpg
```

---

### Post by powerpleb on 2008-06-12
> **iaculallad said:**
> You could also try changing desktop picture using your terminal:

That's hardcore.

---


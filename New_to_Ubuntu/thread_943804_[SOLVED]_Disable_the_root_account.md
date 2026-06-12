---
title: "[SOLVED] Disable the root account"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by technosinner on 2008-10-10
I turn to the community once more as I keep making booboos with my setup...

Because I wanted to log in to SWAT and have access to all the tools, I had to do it via [FONT="Courier New"]root[/FONT].  To achieve this I activated root by setting a password - because I couldn't use [FONT="Courier New"]sudo[/FONT] outside the terminal.

Now I'm realizing the wrongs of my ways and I want to flush it out, but I don't know how.  So, how can I deactivate [FONT="Courier New"]root[/FONT] and return to the default install parameters?

Thanks again.

---

### Post by newlinux on 2008-10-10
```
sudo passwd -l root 
```

should do it.

---

### Post by technosinner on 2008-10-10
Excellent, thanks!!

---


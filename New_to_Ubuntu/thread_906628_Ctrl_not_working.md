---
title: "Ctrl not working"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Jr. on 2008-08-31
Ctrl+c or ctrl+v or ctrl+anything doesn't work. However, ctrl+alt+right does work and switches to the next desktop. But any firefox or open office shortcuts won't work.

---

### Post by Pro-reason on 2008-08-31
> **Jr. said:**
> Ctrl+c or ctrl+v or ctrl+anything doesn't work. However, ctrl+alt+right does work and switches to the next desktop. But any firefox or open office shortcuts won't work.

Does the same thing happen if you start a failsafe session?

---

### Post by mali2297 on 2008-08-31
Try removing the hidden file **.gconf** in your home directory (or move it to a backup if you have made settings that you don't want to lose). Restart.

---

### Post by Jr. on 2008-09-14
Sorry for the late reply, I was out of town for 2 weeks.

I removed the .gconf folder, rebooted and it worked, but of course all my setting were gone. I've replaced the folder. What setting was it that I changed that disabled the ctrl functions?

---

### Post by mali2297 on 2008-09-15
> **Jr. said:**
> Sorry for the late reply, I was out of town for 2 weeks.

I removed the .gconf folder, rebooted and it worked, but of course all my setting were gone. I've replaced the folder. What setting was it that I changed that disabled the ctrl functions?

I don't know. 

You can skim through the settings with the configuration editor. Launch it from the terminal with the command
```

gconf-editor

```

---

### Post by Jr. on 2008-09-15
Fixed it. It was the show mouse option under advanced desktop setting. I had it set to ctrl like on my windows computer. But I guess linux can't differentiate between just ctrl and a ctrl combo.

---


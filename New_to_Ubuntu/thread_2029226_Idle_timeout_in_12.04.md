---
title: "Idle timeout in 12.04"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by r3bol on 2012-07-19
Hi, my 12.04 installation idles (screen fades to black) after about 15 minutes. How can I adjust or turn this off? 
Thanks.

---

### Post by Wirephire on 2012-07-19
Go to System Settings -> Brightness and Lock and increase the time.
If the screen continue going off then it should be screensaver related problem. To fix it type:
```
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
```

---

### Post by InsaneWayne90 on 2012-07-19
Mine always does that during or right after any updates.

---


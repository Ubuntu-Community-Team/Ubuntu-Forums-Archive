---
title: "open in readily running window - web browsers"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by manuleka on 2011-10-19
xubuntu 11.10

i notice that when i click the firefox or chrome icon on quick launch menu i get a new window of firefox or chrome opening up, i want to set this quick launch so that when i click it it opens a new tab if there's an instance of the software currently active

current browsers using - Opera, Firefox, Chromium, and maybe IE under Wine

---

### Post by ankspo71 on 2011-10-20
Hi,
Firefox has this type of feature. Try using this command for the Firefox shortcut on your quick launch menu.

Ubuntu Startpage:
```
firefox about:startpage -new-tab
```

Firefox Startpage:
```
firefox about:home -new-tab
```

Google:
```
firefox www.google.com -new-tab
```

I don't know if the other browsers can do what you need though.
I looked at Chromium's command possibilities but I didn't see anything.

(tested on Xubuntu's panel launchers and run dialog)

---


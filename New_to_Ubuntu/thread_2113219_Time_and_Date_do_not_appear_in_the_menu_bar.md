---
title: "Time and Date do not appear in the menu bar"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by Covalent Bond on 2013-02-06
Ubuntu 12.10 The time and date do not appear in the menu bar and I have the "show time in the menu bar" checked.  I have checked previous posts which suggested going into the Systems Setting, but there is nothing there that I saw regarding time or date.

CB

---

### Post by Frogs Hair on 2013-02-06
You can try the following and logout and back in.  
```
sudo apt-get install indicator-datetime 
```
If the package is installed already.
```
sudo apt-get install --reinstall indicator-datetime
```

---

### Post by Covalent Bond on 2013-02-06
Frogs Hair:

Thanks for the information; it worked.  I did not realize the time was associated with Evolution; I deleted that program because I was getting a constant error message about the program every time I logged in.

TX
CB

---


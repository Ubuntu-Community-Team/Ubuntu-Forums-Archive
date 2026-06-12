---
title: "How do you remove the bluetooth icon from the indicator bar?"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by GumpTron on 2012-02-23
I would like to remove the bluetooth icon from the indicator bar becuase I do not use bluetooth and I would prefer to not have the icon cluttering up. How may this be done?


thank you for your help.

p.s. sorry if its not called the indicator bar but I didn't think it was called the status bar.

---

### Post by sadaruwan12 on 2012-02-23
Just remove the bluez blutooth support.

Use,
```
& sudo apt-get purge --remove bluez
```

this'll remove all the bluetooth stuff if you want to get it back install the bluez pack again.

---

### Post by GumpTron on 2012-02-23
> **sadaruwan12 said:**
> Just remove the bluez blutooth support.

Use,
```
& sudo apt-get purge --remove bluez
```

this'll remove all the bluetooth stuff if you want to get it back install the bluez pack again.

it's gone. thank you! :)

---

### Post by sadaruwan12 on 2012-02-23
Welcome glad to help.

---


---
title: "schema is missing"
date: 2015-08-21
forum: New to Ubuntu
---

### Post by Caril Chasens on 2015-08-21
!4.04, When I try to open the unity tweak tool. I get the following error message:
The following schema is missing
com.canonical.unity.webapps

In order to work properly, Unity Tweak Tool recommends you install the necessary packages

What is the easiest way to do this?

---

### Post by CantankRus on 2015-08-21
Use synaptic.
Install synaptic ...
```
sudo apt-get install synaptic
```

Then search for **unity-webapps** in synaptic and mark for installation **unity-webapps-service** and **unity-webapps-common**

Both packages are installed by default so you must have removed them.

---

### Post by Caril Chasens on 2015-08-21
Worked, good, thanks. CantankRus.

---


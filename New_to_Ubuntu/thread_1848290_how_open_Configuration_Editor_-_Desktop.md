---
title: "how open Configuration Editor - Desktop"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by naikmanoj1991 on 2011-09-22
[B]How open the "configuration editor -Desktop" in ubuntu 11.10. I was try to open using following ways but still not open
1) Hit Alt+ F2
2) Type gconf-editor  & hit Enter

I am beginner
[/B]

---

### Post by seawolf167 on 2011-09-22
That should work, by default it is hidden from the Application menu so

```
gconf-editor
``` should open it.

Do you get any messages when you type it in? Does this work in a terminal?

```
gconf-editor &
```

---

### Post by drs305 on 2011-09-22
To see if it is installed:
```
which gconf-editor
```
It should provide a result, normally "/usr/bin/gconf-editor"

If not, install it:
```
sudo apt-get install gconf-editor
```

---

### Post by naikmanoj1991 on 2011-09-22
> **seawolf167 said:**
> That should work, by default it is hidden from the Application menu so

```
gconf-editor
``` should open it.

Do you get any messages when you type it in? Does this work in a terminal?

```
gconf-editor &
```
[B]hey thx..I just started it.
Are required to install it because by default its not present.[/B]

---

### Post by naikmanoj1991 on 2011-09-22
> **drs305 said:**
> To see if it is installed:
```
which gconf-editor
```
It should provide a result, normally "/usr/bin/gconf-editor"

If not, install it:
```
sudo apt-get install gconf-editor
```
**thxx**

---

### Post by seawolf167 on 2011-09-22
Glad you got it working :)

---


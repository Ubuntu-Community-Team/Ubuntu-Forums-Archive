---
title: "bin installs... It sounds easy however I'm stuck"
date: 2009-12-13
forum: Programming Talk
---

### Post by Purple Mouse on 2009-12-13
Noob, sorry not sure if I should even be in this part, move me if necessary but I'm following 
 [Ubuntu Documentation]("https://help.ubuntu.com/") > [Community Documentation]("https://help.ubuntu.com/community") > [GoogleEarth]("https://help.ubuntu.com/community/GoogleEarth?action=fullsearch&context=180&value=linkto%3A%22GoogleEarth%22") instructions however get stuck when Code: cd ~/desktop 
returns
No such file or directory
I've even tried other directories with same result... What am I doing wrong please?

---

### Post by dwhitney67 on 2009-12-13
Try
```

cd ~/Desktop

```
Linux (Ubuntu) is case-sensitive; so "desktop" and "Desktop" are not the same.

---

### Post by Purple Mouse on 2009-12-13
> **dwhitney67 said:**
> Try
```

cd ~/Desktop

```Linux (Ubuntu) is case-sensitive; so "desktop" and "Desktop" are not the same.

Case sensitive huh... Thank you!

---


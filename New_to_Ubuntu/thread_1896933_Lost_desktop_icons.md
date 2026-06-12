---
title: "Lost desktop icons"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by dep0 on 2011-12-18
I was working with some files when i was asked to choose for a file manager.i Choosed nautilus and then all my desktop icons disappeared and all i have now is a blue screen. I cannot even set a background image.
Later i changed the file manager to thunar (i thought that this might caused the "blue screen" problem) but nothing happend. 
Can anyone help me? I want my desktop icons back.

---

### Post by supercheetah on 2011-12-18
What do you get if you open up a terminal, and run the following?

```

ls Desktop

```

---

### Post by hansdown on 2011-12-18
Hi, dep0.

Could you please tell us, which version of linux you are using?

Thanks.

---

### Post by dep0 on 2011-12-18
```
ls desktop
``` 
gives nothing
```
ls -a desktop 
```
gives " . .. "

I am using xubuntu 11.10

---

### Post by dep0 on 2011-12-18
I would also like to point out that it doesn't pop out the external hard disk when i connect it, as it used to do some hours ago!

---

### Post by supercheetah on 2011-12-22
> **dep0 said:**
> ```
ls desktop
``` 
gives nothing
```
ls -a desktop 
```
gives " . .. "

I am using xubuntu 11.10
Case is actually important.  *ls desktop* won't show anything because ~/desktop likely doesn't exist, whereas you actually want to run *ls Desktop*.

---

### Post by Toz on 2011-12-22
Nautilus, by default, takes over control of the desktop and manages it (background, icons, etc). If you want to use Nautilus in an xfce environment but don't want it to manage the desktop, you will need to run nautilus with the no-desktop option:
```
nautilus --no-desktop
```
..._or_ set it up permanently not to manage the desktop:
```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
```

You will need to log out and back in again to reset it. If that doesn't work and nautilus is still starting and/or xfce is not managing the desktop, you will need to clear out the sessions cache:
```
rm -rf ~/.cache/sessions
```

---

### Post by dep0 on 2011-12-23
Thanks all. I now have them back using the terminal command toz recommended

---


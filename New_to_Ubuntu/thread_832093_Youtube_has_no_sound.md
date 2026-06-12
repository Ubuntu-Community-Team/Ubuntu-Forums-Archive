---
title: "Youtube has no sound"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by ktotheherm on 2008-06-17
i have the latest version of ubuntu and when i try the fixes said in the other forums the file that comes up is blank. thx for your help

---

### Post by stchman on 2008-06-17
> **ktotheherm said:**
> i have the latest version of ubuntu and when i try the fixes said in the other forums the file that comes up is blank. thx for your help

Use the package flashplugin-nonfree.

---

### Post by ktotheherm on 2008-06-17
im srry i dont know what that means

---

### Post by stchman on 2008-06-17
> **ktotheherm said:**
> im srry i dont know what that means

Type the following in a terminal assuming you have internet access.

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by bufsabre666 on 2008-06-17
> **ktotheherm said:**
> im srry i dont know what that means

```
 sudo apt-get install flashplugin-nonfree
```

edit:stchman beat me to the punch

---

### Post by ktotheherm on 2008-06-17
thx i did that but it says i have the latest flash player and it still doesnt have sound

---

### Post by Nepherte on 2008-06-17
Installing libflashsupport often resolves flash problems for users. Try this too:
```
sudo apt-get install libflashsupport
```

Do you have another sound application running while looking to the flash movies?

---


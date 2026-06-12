---
title: "video card?"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by jagdefalke on 2013-03-08
Just a quick stupid question, how do I find out what kind of video card I have?   What's the code for bringing that up in kernal?  Or is there a way to bring it up in interface?

---

### Post by Cheesemill on 2013-03-08
```
lspci | grep VGA
```

---

### Post by ManamiVixen on 2013-03-08
Here:

lspci -v -s `lspci | awk '/VGA/{print $1}'`

copy and paste the entire command into terminal and hit enter.

---

### Post by jagdefalke on 2013-03-08
Thankyou thankyou thankyou!!

---


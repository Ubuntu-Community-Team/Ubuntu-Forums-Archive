---
title: "Boot Splash Screen Alternatives?"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by GUZZLR on 2013-06-15
Hello Everybody, 
Does anybody have suggestions on how to get a choice for different Boot Splash screens, instead of the normal Plymouth Logo?
Thanks

---

### Post by Isamu715 on 2013-06-15
Search the Software Center for *plymouth-theme* and install at least one theme. Then run the following in a terminal:
```
sudo update-alternatives --config default.plymouth
```
You will be presented with available splash themes, you can choose the one you want by entering its coresponding number.

---

### Post by GUZZLR on 2013-06-15
Nice...now I have another way I can break it, and then fix it again!
Thanks!

---


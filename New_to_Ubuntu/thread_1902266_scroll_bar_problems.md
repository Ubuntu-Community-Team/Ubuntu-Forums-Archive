---
title: "scroll bar problems"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-12-30
i have been having this problem since i installed 11.10. when i try to use the scroll bar it goes nuts and auto scrolls by itselfs. for instances when i use the search for files application. tks

---

### Post by BC59 on 2011-12-30
I removed them and my life is better now:
```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0
```

If you like them back:
```
sudo apt-get install overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0
```

---

### Post by rburkartjo on 2011-12-30
tks bc that worked great

---


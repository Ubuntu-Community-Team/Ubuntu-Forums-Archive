---
title: "Can't log in to CUP"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by trutharoundyou on 2013-05-25
I am not able to print from my ubuntu netbook. Actually, pages and pages come out but not the actual document I send to be printed. So, I looked up advice for how to fix that and was directed to CUP. The problem is, I can't log in to CUP. It askes for a username, and I have never been asked for a username before. So, I am really not sure what my username is! Nothing i try works.

---

### Post by steeldriver on 2013-05-25
Hello and welcome to the forum

If your regular user is a member of the lpadmin group, then it should accept your regular login username and password I think

If your user is *not* a member of lpadmin, you can add it with 

```
sudo gpasswd --add *username* lpadmin
```

---

### Post by lethall1 on 2013-05-25
You mean CUPS...
You have to try login with tha same user and password as in your system.
[http://localhost:631](http://localhost:631)

---


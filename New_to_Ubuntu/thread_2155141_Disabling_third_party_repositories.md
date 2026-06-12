---
title: "Disabling third party repositories"
date: 2013-06-17
forum: New to Ubuntu
---

### Post by walliswife on 2013-06-17
I am running ubuntu on a netbook. I want to install iTunes, using wine, but when I tried to install wine it said I needed to disable third party repositories. I have no clue how to do this. Any help would be greatly appreciated. Thanks!

---

### Post by MidnightGrey on 2013-06-17
Hi walliswife,

Could you copy-paste the exact message the install gave you. Also what is your purpose for wanting iTunes? Have you considered linux alternatives, such as Banshee?

---

### Post by varunendra on 2013-06-17
> **walliswife said:**
> when I tried to install wine it said I needed to disable third party repositories. I have no clue how to do this.

Exact error message may really help more.

As for disabling the third party repos -
Ubuntu Software Center > Edit > Software Sources > "Other Software" tab > clear the check-boxes for offending repositories.

However, the installation of wine should be smooth. So if the above doesn't help, it may help us pin-point the cause if you try installing it via terminal and copy-paste the full terminal output here -
```
sudo apt-get update
sudo apt-get install wine
```

---


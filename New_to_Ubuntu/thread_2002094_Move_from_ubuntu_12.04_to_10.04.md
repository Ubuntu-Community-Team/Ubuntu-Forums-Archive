---
title: "Move from ubuntu 12.04 to 10.04"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by Nikki5 on 2012-06-12
Is there a way to change ubuntu 12.04 to 10.04 without uninstalling 12.04 & again installing 10.04?I have dual booting of windows XP and ubuntu 12.04.

---

### Post by wilee-nilee on 2012-06-12
> **Nikki5 said:**
> Is there a way to change ubuntu 12.04 to 10.04 without uninstalling 12.04 & again installing 10.04?

Nope.

You can use the same home though, and separate it from the OS to do so.
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

You don't necessarily have to uninstall 12.04 but delete it or overwrite it, after separating the home.

---

### Post by Elfy on 2012-06-12
Might be better to say why you want to do so - perhaps we can help with that?

---

### Post by Nikki5 on 2012-06-12
I want to do so coz i want to build android source code for my 32-bit machine and i could only find instructions relating 32-bit with ubuntu 10.04.For ubuntu 12.04 a 64-bit machine is required

---

### Post by Derek Karpinski on 2012-06-12
You should be able to run 32 bit applications on 64 bit.

```
sudo apt-get update && sudo apt-get install ia32-libs
```

Will install 32 bit libraries.

[http://developer.android.com/sdk/installing.html#troubleshooting](http://developer.android.com/sdk/installing.html#troubleshooting)

[http://askubuntu.com/questions/131207/android-sdk-cant-be-installed-on-ubuntu-12-04-64](http://askubuntu.com/questions/131207/android-sdk-cant-be-installed-on-ubuntu-12-04-64)

---

### Post by Nikki5 on 2012-06-13
@Derek i think u didn't get my question.My machine is 32-bit not 64-bit and 32-bit machine needs ubuntu 10.04.and i have installed ubuntu 12.04.

---


---
title: "I am not able to Log in to Lubuntu"
date: 2020-06-04
forum: New to Ubuntu
---

### Post by mohsen123 on 2020-06-04
Hello
I have installed Lubuntu 18 on VrtualBox V5.2.12 and working with it without problem. Today I tried to login into it, but when I inserted the password, the page refreshed and it asked me again the password. the password I type is correct and the message 'Incorrect Password' does not appear. What is the problem I can not login in to and what is wrong?
Thank you very much.
Mohsen

---

### Post by jmginer on 2020-06-05
Hello,
what is the message?
Maybe you have the hard drive at 100% capacity

---

### Post by ActionParsnip on 2020-06-05
Press CTRL + ALT + F1
Log in there and run:
```

df -h

```
Are any partitions full? You can also set your password there using
```

passwd

```
and then press CTRL + ALT + F7 to get you back to the GUI login

---

### Post by Impavidus on 2020-06-05
Something is wrong that causes the desktop environment to crash as soon as it starts. It could be a full hard drive, a permissions issue with some file in your home directory, maybe something else. I'm not sure it still applies to Lubuntu 18.04, but a classical cause of this is a root-owned .Xauthority file in your home directory.

---

### Post by TheFu on 2020-06-05
> **Impavidus said:**
> Something is wrong that causes the desktop environment to crash as soon as it starts. It could be a full hard drive, a permissions issue with some file in your home directory, maybe something else. I'm not sure it still applies to Lubuntu 18.04, but a classical cause of this is a root-owned .Xauthority file in your home directory.

For the permissions problem, I’ve seen this caused by users using sudo to run GUi programs.  Permissions in ~/ and ~/.config/ can get screwed doing that.

---

### Post by VMC on 2020-06-05
It appears your in a "login loop". Go here and see if this helps:
[https://satuimrambles.wordpress.com/2016/09/25/how-i-recovered-from-a-login-loop-on-lubuntu-16-04/](https://satuimrambles.wordpress.com/2016/09/25/how-i-recovered-from-a-login-loop-on-lubuntu-16-04/)

---


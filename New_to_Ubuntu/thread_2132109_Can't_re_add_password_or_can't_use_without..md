---
title: "Can't re add password or can't use without."
date: 2013-04-03
forum: New to Ubuntu
---

### Post by Dallas2coolio on 2013-04-03
I made my netbook so you don't have to add password but because of that when I want to update the system or add features from software I can't leave it blank since it says unsuccessful. Is there a way I can add a password again? I tried going to user and change password but it won't let me leave a blank on current password and can't add password. Unless is there a way I can get it to install without having to put password since there isn't one but it acts like there is one.

---

### Post by wildmanne39 on 2013-04-03
Hi, this should do it.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Thanks

---

### Post by Dallas2coolio on 2013-04-03
I keep trying to change password but I get Authentication token manipulation error and says password unchanged. How do I add a password since right now there is nothing. Or is there a way to make it work without having to add a password when trying to install something?

---

### Post by steeldriver on 2013-04-03
That error usually means you are skipping this step:

> In recent versions of Ubuntu, the filesystem is mounted as read-only, so  you need to enter the follow command to get it to remount as  read-write, which will allow you to make changes: 
```
mount -o rw,remount /
```


---

### Post by Dallas2coolio on 2013-04-03
I did try that but it didn't work. Was I just suppose to type that and then press enter and then type passwd dallas2coolio and then it says enter new pass and I enter it twice but it won't work. If I have to I might have to reinstall the OS and start over again.

---


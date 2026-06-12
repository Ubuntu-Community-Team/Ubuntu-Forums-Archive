---
title: "[SOLVED] password recovery?"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by TenHawks on 2008-11-27
Silly me installed Ubuntu tuesday morning just before i went to work, when i got home i could not remember my password.
I have tried several suggested ways to reset my password, but when i get to root@(none)/# and type passwd tenhawks "spud" as soon as i hit the s key it asks me to retype the password. any help would be greatly appreciated.

---

### Post by sisco311 on 2008-11-27
Reboot in recovery mode and reset your password in the root shell:
```
passwd *username*
```

details:[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by TenHawks on 2008-11-27
Odd, I tried that already and it did not work, this time it did. Any idea why it wouldnt have worked the first time?

---

### Post by Dedoimedo on 2008-11-27
Hello,

If you boot into the recovery mode and the fix does not help, then it is possible your root partition is mounted as read-only. You may have to remount it writable.

```
mount -o remount rw /
```

And then, do the passwd change.

Dedoimedo

---

### Post by TenHawks on 2008-11-27
thanks for the fast responce time, i now have access to linux, lets see how fast i can sink/swim.

---


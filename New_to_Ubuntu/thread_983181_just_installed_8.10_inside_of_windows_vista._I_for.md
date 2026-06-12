---
title: "just installed 8.10 inside of windows vista. I forgot my user name and password,help!"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by davzplace38 on 2008-11-15
I installed 8.10 inside of windows vista. It installed fine and is stable. The problem is that when I try to login my user name and password it doesn't seem to recognize it. Can anyone help me please?

---

### Post by camero7 on 2008-11-15
I'm having the same problem. I uninstalled and reinstalled and still have the issue.

---

### Post by taurus on 2008-11-15
Can you boot into recovery mode?  If you can, you can look it up to see what's your login name.  Then, you can change the password to something that you can remember.

This output will tell you your login name, username.
```
ls -la /home
```

You can change the password with, assuming your username is dave

```
passwd dave
```
Now, reboot and see if you can log in with your username and new password.

```
shutdown -r now
```

---

### Post by davzplace38 on 2008-11-15
recovery mode in ubuntu?

---

### Post by taurus on 2008-11-15
When you boot up Ubuntu, do you see a GRUB menu or at leas the word GRUB on the upper left corner?

---

### Post by camero7 on 2008-11-15
can't boot into recovery mode... I'm using it with windows vista. I think there may be a bug because I've uninstalled 2X now and reinstalled with the same problem

---

### Post by davzplace38 on 2008-11-15
It gives me the choices to either boot into windows or ubuntu.

---

### Post by davzplace38 on 2008-11-15
most likely a bug. But I had it installed 2 days ago, and it worked fine. Password and username were the same.
I had to do a recovery of my vista and a reinstall of ubuntu.

---

### Post by camero7 on 2008-11-15
Doesn't ask me for a user name, just a password.

---

### Post by corncob on 2008-11-15
Hit the [ESC] key while you're booting up.

---

### Post by Iowan on 2008-11-15
Probably most of the information [here]("http://www.psychocats.net/ubuntu/resetpassword") has already been covered.

---


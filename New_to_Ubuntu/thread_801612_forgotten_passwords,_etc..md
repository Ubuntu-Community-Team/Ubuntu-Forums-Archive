---
title: "forgotten passwords, etc."
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Zopiac on 2008-05-20
you MIGHT be familiar with my predicament, but here's a similar thing: what if you forget your password to log into Ubuntu...is there a way to reset that or log in another way?

---

### Post by Iowan on 2008-05-20
Got just the link for you...
[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by sdennie on 2008-05-20
I think you should be able to select a recovery mode kernel from grub at boot time (you may have to hit escape when the grub messages appear to select it) and then just type:

```

passwd some_user

```

And it should allow you to reset the password for that user.

---


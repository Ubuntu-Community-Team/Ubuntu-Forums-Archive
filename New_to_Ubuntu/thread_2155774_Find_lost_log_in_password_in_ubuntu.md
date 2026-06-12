---
title: "Find lost log in password in ubuntu"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by parcdulas on 2013-06-19
Hello,

I installed Ubuntu as a dual boot with windows a couple of years ago and now want to start using it but do not remember what password I used. Is there any way I can get to Log In or do I have to remove the the current version and reinstall?

Thanks

Martin

---

### Post by linuxtechguy on 2013-06-19
boot into single user mode and reset the password

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by raja.genupula on 2013-06-19
[http://askubuntu.com/questions/121698/how-do-i-reset-a-lost-password-using-recovery-mode-requires-me-to-type-the-pass](http://askubuntu.com/questions/121698/how-do-i-reset-a-lost-password-using-recovery-mode-requires-me-to-type-the-pass)

---

### Post by Bashing-om on 2013-06-19
parcdulas; Hi !

Should not be necessary to (re-install).
Here are easy instructions to reset your password in Ubuntu:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[INDENT][INDENT]Let us know what other we can assist in[/INDENT][/INDENT]

---

### Post by Impavidus on 2013-06-19
A couple of years ago and now you want to start using it? Your installed Ubuntu is probably already end-of-live. With the links given by the previous posters you can reset your password, but installing a new version may not be such a bad idea. At the moment 12.04, 12.10 and 13.04 are supported.

---

### Post by parcdulas on 2013-06-24
Thanks to every one! I'm now in with a reset password.

However, on the top bar, most extreme right edge, where the symbol that includes shutdown normally resides I have two identical usernames (I only ever set it up as a single user as far as I am aware) and thus there is no room for the shutdown symbol. I had to hold the powerbutton down to shut the system down but as there is no data as yet there should be no problem. Any suggestions as to how to clean this up and have it behave as normal for a single user?

Regards,

Martin

---

### Post by newb85 on 2013-06-24
Aside from security risks, one pitfall of using an EOL system is that the majority of people on the forums are no longer using that system.  I vaguely recall experiencing something like that a couple years ago.  I think it was a bug, and I don't remember a solution.

Perhaps it would help if you told us what release you're using.  If you don't know, you can easily find out by running this in a terminal:
```
lsb_release -a
```

---


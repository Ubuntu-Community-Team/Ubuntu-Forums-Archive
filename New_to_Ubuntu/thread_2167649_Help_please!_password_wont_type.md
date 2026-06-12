---
title: "Help please! password wont type"
date: 2013-08-14
forum: New to Ubuntu
---

### Post by shino2 on 2013-08-14
Whenever I try to type a password in the terminal nothing happens. I first type passwd into the command and it asks for a password, so I try to type in a password but nothing shows up. I cannot download anything either because it keeps asking me for a password I can't put in. If anyone knows what is wrong with this please help. Thanks.:)

---

### Post by deadflowr on 2013-08-14
It's because the password is invisible.
Type it as you remember it and hit enter.

---

### Post by QIII on 2013-08-14
This is normal and expected.  Your keystrokes do not "echo" in the terminal.  Just type the password and press enter.

Cheers!

---

### Post by SweetAurora on 2013-08-14
Thats ok. It's a security feature of Linux. No body will be able to see your password if they look at your screen. Just type it in and hit enter like deadflowr said.

---

### Post by shino2 on 2013-08-14
Thanks!

---

### Post by oldos2er on 2013-08-14
If you *really* want visual feedback from entering your password in the shell, see [https://help.ubuntu.com/community/Sudoers#Enabling_Visual_Feedback_when_Typing_Passwords](https://help.ubuntu.com/community/Sudoers#Enabling_Visual_Feedback_when_Typing_Passwords)
Good idea to make a copy of your sudoers file before changing it though. ```
sudo cp /etc/sudoers /etc/sudoers.backup
```

---

### Post by The-Server-4dmin on 2013-08-14
I would recommend leaving the sudoers as is and pretend like you see it. :)

---

### Post by deadflowr on 2013-08-14
I've never added pwfeedback to that line, but I have added insults.

I like having my terminal mock me for my inability to spell right.;-)

---


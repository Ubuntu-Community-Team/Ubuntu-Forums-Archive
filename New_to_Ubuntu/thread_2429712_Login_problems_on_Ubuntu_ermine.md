---
title: "Login problems on Ubuntu ermine"
date: 2019-10-22
forum: New to Ubuntu
---

### Post by robertscott79 on 2019-10-22
Hello, in the past three days I had to reinstall Ubuntu ermine three times... And I am considering to do it a 4th time. What happened each time was that it would not let me login with my password after a reboot. I tried in every possible way but the password is rejected each time. Any idea how come? My desktop has only one user, which is me. Thank you.

---

### Post by yancek on 2019-10-22
Do you get a message indicating incorrect password, just a login loop after entering your password or something else happens?  The obvious first question is are you sure you have the correct password and passwords being case sensitive they need to be exact in upper and lower case.  

If you can't get it to accept, you can reset the password as explained at the link below.

[https://itsfoss.com/how-to-hack-ubuntu-password/](https://itsfoss.com/how-to-hack-ubuntu-password/)

---

### Post by guiverc on 2019-10-22
Beyond a wrong password, can you login via text terminal? but fail at gui?

  This can occur for many reasons, my most common experienced one is your $HOME directory has insufficient space for gui work-files to be created, so GUI login fails and you're returned to login screen (no error message), however you'll be able to login via text terminal so can fix the issue there.  How much space did you allocate?  (minimum is 25gb [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) though many people do use less; but you have to be careful with what you add to your system etc).

---


---
title: "different password for GUI and SSH logins?"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by feeleep on 2013-03-11
Hello,
I have a following problem.
I changed my password during an SSH session via passwd command. The password has been updated and I am able to log in via SSH using the new password. However, I am currently unable to login to the gui as neither old or new password brings up 'authentication failure'.
the problem only seems to affect my main user as I can log in using a different user using a password updated via passwd just fine

---

### Post by galfly on 2013-03-11
Hi,

You changed your password on the remote machine during the ssh session. If you have physical access to that machine, you'll see that you can log in to the "GUI" just fine.

---


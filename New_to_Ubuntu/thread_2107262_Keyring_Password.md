---
title: "Keyring Password"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by technologicme on 2013-01-21
How do i disable ( enter password to unlock keyring) as it keeps  prompting me to put in the password when i go into password an keys an  delete it there an then restart my computer it still comes up

---

### Post by Nr90 on 2013-01-21
Set it to the same as your user's PW:
[https://one.ubuntu.com/help/faq/how-do-i-get-rid-of-the-keyring-password-prompt/](https://one.ubuntu.com/help/faq/how-do-i-get-rid-of-the-keyring-password-prompt/)

---

### Post by mcduck on 2013-01-21
If you use automatic or passwordless login, set the keyring password to empty one.

(and no, you don't need to delete the keyring or any keys to change the keyring password. Instead open the "Passwords and Keys"-dialog, then from the menu select "View"->"By Keyring" to show different keyrings. After that right-click on the "Login" keyring now visible on the left-hand panel, and select "Change Password".)

---


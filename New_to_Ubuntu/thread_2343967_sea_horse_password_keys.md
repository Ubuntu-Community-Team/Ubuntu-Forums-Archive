---
title: "sea horse password keys"
date: 2016-11-21
forum: New to Ubuntu
---

### Post by irishy2 on 2016-11-21
help please i decided against using password and keys seahorse and i removed it but every time on start up i get a box up asking me to enter password to unlock it,can anyone tell me how to get rid of it
thanks

---

### Post by CantankRus on 2016-11-21
What exactly did you remove?
The application Seahorse is just a front end for GnuPG.
If you use autologin you will still need to enter a password to unlock the login.keyring.

Solution: 
disable autologin
or
reinstall seahorse and set the login.keyring password to be empty.

The login keyring is where browsers and other applications save passwords.
If you set the login.keyring password to be blank your saved passwords will not be encrypted.

---

### Post by irishy2 on 2016-11-22
Thanks for replying
I installed the app from ubuntu software i did not cope with it then I removed it in ubuntu software but as i described the password box appears on every start up
thanks again

---

### Post by CantankRus on 2016-11-22
Seahorse is installed by default, so don't really know what you installed then removed.
What is your output from this terminal command?
```
apt policy seahorse*
```

---


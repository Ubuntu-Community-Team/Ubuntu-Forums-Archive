---
title: "[SOLVED] password and username retreival"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by james parr on 2008-11-12
i have just purchased aelonex webbook when first booting up it asked me to enter a password and username which i did,but after logging off and then later trying to reboot it now asks for username and password but when i enter what i thought i had put in it comes up with incorrect username or password,i may have pressed wrong key when first entering this info,but i have tried different variations but no luck,any suggestions how to retrieve my password/username or how to go back to beginning,nothing else has been done on it as i am unable to login.

---

### Post by james parr on 2008-11-12
i have just purchased aelonex webbook when first booting up it asked me to enter a password and username which i did,but after logging off and then later trying to reboot it now asks for username and password but when i enter what i thought i had put in it comes up with incorrect username or password,i may have pressed wrong key when first entering this info,but i have tried different variations but no luck,any suggestions how to retrieve my password/username or how to go back to beginning,nothing else has been done on it as i am unable to login.

---

### Post by arochester on 2008-11-12
See [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by james parr on 2008-11-12
thank you for your help,i am very gratefull thought i was never going to get in again,as i am a noob to this,everything is now working fine thanks again.

---

### Post by Elfy on 2008-11-12
Boot into recover mode - if you get a root prompt, forget the next bit

If you don't get a root prompt but a menu - choose root prompt from the list

Run this command and it should tell you the username

```
cat /etc/passwd | grep 1000
```

You can change the password to a new one with

```
passwd *whatyouwant*
```change whatyouwant to suit you.

Exit to get back to menu and resume, or reboot from root prompt.

---

### Post by Elfy on 2008-11-12
As you're new - you might like to know not to post duplicate threads - especially on the same forum and page with 10 minutes between them ;)

---

### Post by PartisanEntity on 2008-11-12
Duplicate threads merged.

---


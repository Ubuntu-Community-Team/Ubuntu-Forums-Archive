---
title: "rsync wants admin password - how do you provide it?"
date: 2017-12-17
forum: New to Ubuntu
---

### Post by sterator on 2017-12-17
when I try to run rsync, I'm asked for current user credentials..but it wants **admin** credentials. I am the admin but my everyday user is  standard.

How do I do this? do I somehow tell the terminal "This is admin speaking?"

All I get after typing the admin password is "not correct password for [current user]

I am and possess the credentials for both admin and standard user..it's my computer, my files, in my house, etc.

Thank you!

---

### Post by HermanAB on 2017-12-18
One word: sudo

$ sudo rsync yadda yadda...
yourpassword

---

### Post by mastablasta on 2017-12-18
if you have two users and are usign th enon admin one, then you need to do ```
sudo su *youradminuser*
```, change to it, use the app and then change back.

read more about it here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

and here: [https://www.sudo.ws/man/1.8.3/sudo.man.html](https://www.sudo.ws/man/1.8.3/sudo.man.html)

or run 

```
man sudo
```

for help.

---


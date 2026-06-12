---
title: "[SOLVED] Log into Terminal as a different user?"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by Chesamo on 2008-11-14
Situation:
I am logged into my normal user account (tony), and I want to log into a different account (admin, which is not related to root) under Terminal. I type 'sh', and I'm returned to the $ (as opposed to tony@shoutserver$). I then type 'login', and the Terminal returns```
No utmp entry. You must exec "login" from the lowest level "sh"
```What I need:
I need to be able to log into a Terminal window using the 'admin' account, because I will be doing file work and I want the 'admin' account to be able to modify the files i will be working on. I can't reboot to log in, since I'm working remotely and the server is a streaming Internet radio station. Is this possible under Ubuntu?

---

### Post by Idefix82 on 2008-11-14
You can do
```
sudo su username
```
where username is the - well - username under which you want to login. So I guess in your case it will be something like
```
sudo su admin
```

---

### Post by Chesamo on 2008-11-14
Thank you! I never thought to invoke root privelages... ](*,)
EDIT: Also just saw your signature, but I don't see the 'close thread" option...
EDIT^2: Nevermind.

---


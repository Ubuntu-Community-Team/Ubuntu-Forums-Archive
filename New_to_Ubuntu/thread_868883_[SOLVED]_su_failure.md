---
title: "[SOLVED] su failure"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-24
rick@kubuntu2:~$ su
Password:
su: Authentication failure
rick@kubuntu2:~$
how do i fix this i put in the correct password but it always comes back the same.??
rick

---

### Post by PmDematagoda on 2008-07-24
I don't think su is how you obtain root permissions on K/Ubuntu, I believe you use sudo as:-
```
sudo -i
```

---

### Post by kestrel1 on 2008-07-24
When you use SU you are switching the acount to root. Root doesn't normally get used as to do so could cause security issues.
If you want to run a command use:
```
sudo
```
followed by the command.
What are you trying to do?

---

### Post by ice60 on 2008-07-24
there's more about it here, kubuntu works the same way -
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by stevoo on 2008-07-24
if you want shell access as root 
then you have to do 
sudo -s

su will not work

---


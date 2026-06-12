---
title: "Password at 11.10"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by ella_ on 2011-11-06
Hello, 
I just updated to Ubuntu 11.10 and a problem has occur on both my computers. My root password has changed and I have no idea to what... The updated still work but I can not install anything. I have tried to reset password using following instructions and it does not work, the password does not reset. 
[http://www.linux-radar.net/reset-password-ubuntu.html](http://www.linux-radar.net/reset-password-ubuntu.html)

I tried to find someone else with this problem but failed, does anyone know what to do. As I see it now I need to format my hard drive and do a new installation but I prefer not to. 
Some other problems has occur at the same time, for example I can not move files to a USB from my computers or save files on other computers (read file server) at my network. 

Please... does anyone know what to do. 

/Ella

---

### Post by haqking on 2011-11-06
> **ella_ said:**
> Hello, 
I just updated to Ubuntu 11.10 and a problem has occur on both my computers. My root password has changed and I have no idea to what... The updated still work but I can not install anything. I have tried to reset password using following instructions and it does not work, the password does not reset. 
[http://www.linux-radar.net/reset-password-ubuntu.html](http://www.linux-radar.net/reset-password-ubuntu.html)

I tried to find someone else with this problem but failed, does anyone know what to do. As I see it now I need to format my hard drive and do a new installation but I prefer not to. 
Some other problems has occur at the same time, for example I can not move files to a USB from my computers or save files on other computers (read file server) at my network. 

Please... does anyone know what to do. 

/Ella

There should be no root password as the root account is by default locked in Ubuntu.

You as a user if installed should be a sudo user and so to perform admin (root) task use sudo, read [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")where the password required is your own user password if you are in the sudo group.

also read

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo) for sudo problems

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) for password reset

So can you login to the machine ok, and what happens when you try a sudo task ?

---

### Post by ella_ on 2011-11-06
Sorry, I am still unable to use Sudo... followed the instruction.

---

### Post by ella_ on 2011-11-06
Yes I can log in but when I do a sudo task it ask for authentication and it does not accept my long loved password.

---

### Post by lisati on 2011-11-06
> **ella_ said:**
> Yes I can log in but when I do a sudo task it ask for authentication and it does not accept my long loved password.

When using sudo, type in your password normally. It will not show on the screen as you type: this is normal.

---

### Post by ella_ on 2011-11-06
I am not sure what you mean, I do write my password down as usually and it say that my authentication was unsuccessful, please try again.

---

### Post by haqking on 2011-11-06
> **ella_ said:**
> I am not sure what you mean, I do write my password down as usually and it say that my authentication was unsuccessful, please try again.

the same password you login with yes ?

can you show us the output of

```
groups
```

---

### Post by ella_ on 2011-11-06
OK: 

ella adm dialout cdrom plugdev lpadmin admin nopasswdlogin sambashare

---


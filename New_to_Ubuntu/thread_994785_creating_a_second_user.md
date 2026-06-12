---
title: "creating a second user"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by JUDOHAWK on 2008-11-27
Like the title says, I just want to create a second user account that can do basic stuff on the OS but not have all the access as the root user.  I looked on google but the stuff that came up I don't understand XD

---

### Post by Xiong Chiamiov on 2008-11-27
```

sudo useradd new_user

```
or
```

sudo adduser

```
for an interactive one.

If you don't want them to have root access, don't add them to the "wheel" group.

---

### Post by nothingspecial on 2008-11-27
System > administration > users and groups.

Unlock it with your password

Add user and fill in the boxes.

---

### Post by JUDOHAWK on 2008-11-27
well before I go doing that, I've heard to create a non root account for basic stuff.  This was going to be for that reason. Would I be able to just stick to my root user?

Also nothing, if I had known I could do it there I wouldn't have asked, I thought you had to do something with the terminal lol.   I won't add another user until someone clarifies on the above though. Don't need another user if unnecessary since Im the only one using this computer.

---

### Post by nothingspecial on 2008-11-27
Your user account is not the root account, it is an administrator account so just stick with that.

You can give your self root powers using sudo and your password.

---

### Post by JUDOHAWK on 2008-11-27
Ah ok, that makes sense then. I wasn't sure and didn't know if I was a super or not XD.

---

### Post by Xiong Chiamiov on 2008-11-27
Really, what's happening behind the scenes is that the /etc/sudoers file defines who is allowed to use sudo to get root priviledges.  I'm not sure how it is set up in Ubuntu, but the convention is to give sudo privs to anyone in the user group "wheel".  So, really, your user isn't actually special by itself; if you remove it from that group, then you won't have root privs any more (don't do this!), but creating a new user will not give them super-user privs by default.

---

### Post by hyper_ch on 2008-11-27
actually ubuntu is setup to give root access to all users in the group "admin".

---

### Post by Joeb454 on 2008-11-27
> **hyper_ch said:**
> actually ubuntu is setup to give root access to all users in the group "admin".

I think both groups ("wheel" and "admin") would give sudo permissions to the user :) I'm not sure though, all my systems are single user

---

### Post by zvacet on 2008-11-27
@ **JUDOHAWK**

For everyday work it is good to have second account,and that account will not have admin privileges.So,for install/uninstall,update/upgrade you will have to use your first account(it is your admin account).You can easy switch from onee account to another by click on switch user applet on your top panel.

---

### Post by Xiong Chiamiov on 2008-11-28
> **zvacet said:**
> @ **JUDOHAWK**

For everyday work it is good to have second account,and that account will not have admin privileges.So,for install/uninstall,update/upgrade you will have to use your first account(it is your admin account).You can easy switch from onee account to another by click on switch user applet on your top panel.
Isn't that the point of using sudo?  Just set the sudo timeout low (or ask for password every time), and don't give root privs to anything that you don't trust.

---


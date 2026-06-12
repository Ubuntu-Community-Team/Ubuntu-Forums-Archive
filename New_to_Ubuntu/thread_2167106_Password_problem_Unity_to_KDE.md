---
title: "Password problem Unity to KDE"
date: 2013-08-12
forum: New to Ubuntu
---

### Post by Richard_Slawsky on 2013-08-12
I'm a relative newbie. I had been using Unity for a few months but wanted to try KDE. I typed the command:

sudo apt-get install kubuntu-desktop

Looks like everything worked fine, except now my password no longer works. I can't get beyond the login screen. Any suggestions?

---

### Post by deadflowr on 2013-08-12
Does the login screen look like the same one as before?

If so, can you try logging into Unity(Ubuntu).
Or is the whole thing nuts.(Can't log into any desktop)

---

### Post by Richard_Slawsky on 2013-08-12
It looks like a KDE screen, not the Ubuntu screen that was their previously. I can choose a number of different desktop environments but the password doesn't work for any of them.

---

### Post by Vladlenin5000 on 2013-08-12
> **Richard_Slawsky said:**
> It looks like a KDE screen, not the Ubuntu screen that was their previously. I can choose a number of different desktop environments but the password doesn't work for any of them.


Installing a new DE or any app for that matter doesn't change your user's password. You're either trying to login with a different user or the same user but typing the password incorrectly (Caps Lock, perhaps???) or you actually changed the password and you don't remember now.

---

### Post by deadflowr on 2013-08-12
If you type ctrl + alt + F1,or F2,or F3,or F4 you will see a terminal like interface.
It will have a prompt for login, try entering your username, and then try your password.
If the password doesn't work look here
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
You can get back to the gui login screen with ctrl+alt+F7.

But if you can login in to one of the F#s, then try
```
sudo service kdm stop
```
If you are running kdm then it'll state stopping/waiting.
If so, then try
```
sudo service lightdm start
```
Which should load the Normal login screen.

---

### Post by Richard_Slawsky on 2013-08-12
User error. Once I got into the password change procedure I realized I was using the wrong user name. Oh well. Thanks for your help.

---

### Post by deadflowr on 2013-08-12
Running the ls /home command from the reset password link has saved my skin a few times as well.:)

Good to see you didn't need to go beyond that, I hope.

---


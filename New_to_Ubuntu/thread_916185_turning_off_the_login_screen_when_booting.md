---
title: "turning off the login screen when booting"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by gingerj on 2008-09-10
Hi All,

Within the Kubuntu OS can someone tell me the option to turn off the login screen, so I can boot into the OS directly.

I had this for my Ubuntu setup previously but the KDE interface is completely foreign to me :(

Thanks,
ginge

---

### Post by cb951303 on 2008-09-10
in KDM preferences there should be an auto-login option :popcorn:

---

### Post by gingerj on 2008-09-10
where is KDM located?

---

### Post by Iowan on 2008-09-10
Applications>Settings>Login Window>Security?

---

### Post by gingerj on 2008-09-11
Hi All,

I found the login manager applications>system settings>advance>login manager

But I cannot seem to do anything in it, I have user list which seems to be the screen that the help suggests is the one to use. **Everything** is greyed out :( has anyone seen this problem before? 

When I was running Ubuntu if I wanted to go to such a application it would ask me to login, could this be a permissions thing?

---

### Post by dioltas on 2008-09-11
You are probably running the program as a normal user, not in root. In gnome, the applications are greyed out like that when you havn't got root priviliges, there's usually a button with a key on it in the application window, that lets you type your password and unlock the program.

I dont use KDM so im not sure, but there should be something similiar. Maybe a button to unlock stuff in the panel bar?

---

### Post by gingerj on 2008-09-12
Hi All, I really am stuck I cannot get this working....

---

### Post by Lord DarkPat on 2008-09-12
I think you have to remove kdm from the daemons...not sure how that's done in Ubuntu

---

### Post by pag on 2008-09-12
> **gingerj said:**
> When I was running Ubuntu if I wanted to go to such a application it would ask me to login, could this be a permissions thing?

you could try pressing alt+f2 and typing```
kdesudo systemsettings
```
It should launch System Preferences with root priveledges.

---

### Post by gingerj on 2008-09-19
I still cannot get this to work.

I am logged in as admin now, and have done the following amends.

I have CHECKED  "Enable password less logins" and also checked my user name in the dialogue box.

I have also CHECKED "Enable Auto login" and selected my username" 

When I restart my machine it attempts to log me in, but says "password failed" and I still have to type my login info.

As far as I can see there are no fields to store my password. Except a field called "focus password" which is currently checked.

Am I still doing something wrong?

---


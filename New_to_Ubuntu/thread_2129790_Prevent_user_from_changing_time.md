---
title: "Prevent user from changing time"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by kuldeepbhanja on 2013-03-27
Hi All,

I want that no user can change the system time. Please help me how can i prevent user to change the time and again allow for it.

Thanks in advance...

---

### Post by PhantomTurtle on 2013-03-27
To prevent this, change the other users that you have to standard users rather than admin users. This will make sure that they dont have permission to change any system settings such as the system time. To change a user to a standard user do the following,

Open System Settings, scroll down to System > User Accounts. Click on user accounts, select the account you want to make a standard user. Next click the unlock button at the top and pop in your admin password. next just click on account type, and change it from "Administrator" to "Standard". (Make sure to leave one account as an administrator, Only that admin user can now change the time. Put a good password on it to prevent other users from logging in to it). That's all there is to it.

Hope that helps :)

-Phantom

---

### Post by slickymaster on 2013-03-27
If the users are not members of admin group they should not be able to make any changes to the system other than those settings in their own home, so make sure that users other than yourself are only desktop users, not admin, and keep your admin password secret from them.

---

### Post by kuldeepbhanja on 2013-03-30
Thanks Phantom, 

I tried this but my application and all devices related to this supports only if user is admin user. so please suggest a solution considering user as admin.

---

### Post by PhantomTurtle on 2013-03-30
Unfortunately, I believe this is the only way to prevent a user from changing the time. What application are you trying to run? If you want admin privileges for just that app, then run it from terminal using this command,

```
gksu appname
```

The just pop in your administrator password,  and it will launch the app. Make sure not to close the terminal window while the program is running, but do make sure to close it *after* you exit the program.

Example: 

```
gksu firefox
``` 
will launch firefox as an admin user.

Your sudo password is the password for your administrator user.

-Phantom

---

### Post by kuldeepbhanja on 2013-03-31
Thanks Phantom,

It worked for me. now i able to run it as admin but system user cannot change the tym.

Thanks again....

---


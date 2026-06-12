---
title: "How do I synchronize the superuser password with the login keyring password?"
date: 2013-08-02
forum: New to Ubuntu
---

### Post by 1888software on 2013-08-02
As the forum name suggests, I am an absolute Linux/Ubuntu newbie. Two questions:

1. I changed the superuser password. A dialogue box reports that 'the login keyring no longer matches ..." Is this normal? 
Supplementary: How do I synchronize the superuser password with the login keyring password?

---

### Post by slickymaster on 2013-08-02
> **1888software said:**
> As the forum name suggests, I am an absolute Linux/Ubuntu newbie. Two questions:

1. I changed the superuser password. A dialogue box reports that 'the login keyring no longer matches ..." Is this normal? 
Supplementary: How do I synchronize the superuser password with the login keyring password?...

Go to Applications -> Accessories -> Passwords and Encryption Keys
Right-click on Passwords: login
Select &#8220;Change Password&#8221;
Enter your old login password in the old password bit, and put your current login password in the new password fields.

---

### Post by 1888software on 2013-08-02
Thank you for your response. Where do I find or how do I locate "Applications -> Accessories -> Passwords and Encryption Keys". I have never seen this before. It is not in Settings.

---

### Post by slickymaster on 2013-08-02
The "Passwords & Encryption" application is strangely named seahorse. You can check that it is installed by typing ```
seahorse
``` at the command-line to launch it.
You can install the application via:```
sudo apt-get install seahorse
```

---

### Post by 1888software on 2013-08-02
I do not know the old login keyword password. Thank you for your help.

---

### Post by slickymaster on 2013-08-02
That being the case you can try something which is to remove the old keystore.
In a terminal window enter:```
killall -9 gnome-keyring-daemon
rm -fr ~/.gnome2/keyrings/
```reboot the computer ```
sudo init 6
```and then on the first prompt to enter the new keyring password equal to your superuser password.

---


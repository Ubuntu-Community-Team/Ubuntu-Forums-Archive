---
title: "Administrator password not working"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by Drowz0r on 2011-11-11
Hello all

I am on Ubuntu 11.10

Recently I've had to create a new account on this machine, which I called AdMaster and downgraded the existing account to a standard account.

I created a password for AdMaster, which for example was "Password123" and the existing account had a password of "Pass321".

Now, I find that when I log on with the existing account, I am told my key ring password no longer matches the password with this account. To unlock my key ring I must use the AdMaster "Password123" or it won't unlock. Then when I attempt to log into the AdMaster account, the password "Password123" shows as invalid, but it is clearly valid.

In short, the valid password for the admin account is not working and the regular account is working with "Pass321" but also requires "Password123" to unlock the key ring.

So I attempt to unlock and change the password/account permissions but I'm told both Pass321 and Password123 are incorrect for both accounts.

Passwords above are just examples but concept is the same.

Any ideas?

Thanks

---

### Post by Rodney9 on 2011-11-11
This site maybe of help - [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Drowz0r on 2011-11-13
Hello

Thanks for the link. I followed the instructions step-by-step but it will not allow me to change the password and gives some kind of error... :(

---

### Post by coffeecat on 2011-11-13
Try giving back admin privileges to the original account:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

And then reset the password of the original account back to what is was with the link Rodney9 posted. Hopefully, you will then be able to access your original account keyring and use the original account to investigate the password and privileges on the newer "admin" account.

In 11.10 the default User Accounts application is somewhat feature-poor (to put it politely!) - that's an upstream problem. You can install the older gnome2 "Users and Groups" application in 11.10 by installing the gnome-system-tools package. That gives you a more comprehensive GUI app to administer accounts, but I think you'll need the link above to restore admin privileges to the first account.

---

### Post by Drowz0r on 2011-11-14
> **coffeecat said:**
> Try giving back admin privileges to the original account:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

And then reset the password of the original account back to what is was with the link Rodney9 posted. Hopefully, you will then be able to access your original account keyring and use the original account to investigate the password and privileges on the newer "admin" account.

In 11.10 the default User Accounts application is somewhat feature-poor (to put it politely!) - that's an upstream problem. You can install the older gnome2 "Users and Groups" application in 11.10 by installing the gnome-system-tools package. That gives you a more comprehensive GUI app to administer accounts, but I think you'll need the link above to restore admin privileges to the first account.

Yeah tried that one too but no joy. Just seems to decide I'm not allowed anything admin-related.

Formatted it instead and just left the one admin account on there. Easier than trying to fix the issue heh.

Thanks for the help though. Nice fixes on that psychocats page.

---

### Post by Garland Fox on 2011-11-14
This one worked for me when everything else failed.

[http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/)

If ya wanna try...

We on an old dell but it worked when everything else failed.

---


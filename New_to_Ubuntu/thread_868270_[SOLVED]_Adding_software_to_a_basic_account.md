---
title: "[SOLVED] Adding software to a basic account"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by mczonie on 2008-07-23
I just created a basic account for if someone is over at my house and wants to use my computer. How do I download software to it? I want to download Opera, but it says I don't have that privilege in that account.

Also, is it safe to surf the internet from the superuser account, or should I use a basic account for that?


TIA

---

### Post by Xerp on 2008-07-23
Get an administrator (you) to install the software. That way you get to control what goes on :)

It is also safe to surf from an account that has the administrator role - you'll need to enter your password to do anything that changes the system.

---

### Post by mczonie on 2008-07-23
> **Xerp said:**
> Get an administrator (you) to install the software. That way you get to control what goes on :)

How do I install it to the guest account? I installed it to the superuser account, but when I go to the guest account, it's not there.

---

### Post by AndyCooll on 2008-07-23
And of course you (as an administrator) could increase the privileges of the basic account to give them permission to "administer the system" and hence install software, 

However that's defeating the point of the security conscious "basic" account. The very point is that they can't install anything or make changes to the system. 

As Xerp says, easiest is simply for you as the administrator of the system to login and install it.

:cool:

---

### Post by AndyCooll on 2008-07-23
> **mczonie said:**
> How do I install it to the guest account? I installed it to the superuser account, but when I go to the guest account, it's not there.

It is. If you do ALT+F2 and type opera when in the guest account it should open up. What may not be there is an entry in the start menu, and you might have to create this yourself (System > Preferences > Main Menu).

If you're not sure of the details, log back in to your own account. And under System > Preferences > Main Menu again, check and write down the details for Opera. Go back to the basic account and create a new entry, copying the details you've just written down.

:cool:

---

### Post by mczonie on 2008-07-23
> **AndyCooll said:**
> And of course you (as an administrator) could increase the privileges of the basic account to give them permission to "administer the system" and hence install software, 

However that's defeating the point of the security conscious "basic" account. The very point is that they can't install anything or make changes to the system. 

As Xerp says, easiest is simply for you as the administrator of the system to login and install it.

:cool:

Yes, but how do I install it to the other account from the superuser account?

---

### Post by AndyCooll on 2008-07-23
> **mczonie said:**
> Yes, but how do I install it to the other account from the superuser account?
You don't need to re-install it for each user. Once installed on your system the software application should then become available for all users on that system. 

You don't need to install an application five times if your system has five users. Only the administrator has the privileges to install the application, but by default that application usually becomes available for everybody to then use.

:cool:

---

### Post by mczonie on 2008-07-23
> **AndyCooll said:**
> You don't need to re-install it for each user. Once installed on your system the software application should then become available for all users on that system. 

You don't need to install an application five times if your system has five users. Only the administrator has the privileges to install the application, but by default that application usually becomes available for everybody to then use.

:cool:

For some reason, when I go over to that account, Opera isn't on the panel or desktop.

Also, is it safe to surf the 'net from the superuser account? Isn't that kind of like running as root?

---

### Post by AndyCooll on 2008-07-23
Hence why I explained how to add an entry to the start menu in an earlier reply.

Regarding the Internet. It is perfectly safe. You are not running as root, you are running as a normal (limited) user. What your account has is the privilege to _switch_ to root if required. When that is needed you will be asked for a password. You will then be running in privileged mode for that function. As soon as it is finished you switch back to normal mode again.

Your basic account doesn't have the privilege to switch to root. That is the difference. See [here]("https://help.ubuntu.com/community/RootSudo") for more information about sudo.

:cool:

---

### Post by mczonie on 2008-07-23
> **AndyCooll said:**
> Hence why I explained how to add an entry to the start menu in an earlier reply.

Sorry, I didn't see that post. Thanks.

---


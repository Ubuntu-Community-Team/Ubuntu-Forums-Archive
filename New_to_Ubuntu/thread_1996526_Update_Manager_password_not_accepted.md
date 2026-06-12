---
title: "Update Manager password not accepted"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by VE6EFR on 2012-06-04
Here's an odd one for the group. This morning I noticed there are updates available for my computer. So I open the update manager, click on install updates and then it asks me for the password for root. I enter the password (or at least what I am 99.999% sure is the password) and it comes back with "your authentication attempt was unsuccessful, please try again".

Is there a way to reset this password?

Thanks in advance,

Jeff VE6EFR

---

### Post by bcaperton75 on 2012-06-04
Jeff,

  I'm not sure if you have already tried this, but here is you CLI commands to reset the password for root.

$ sudo passwd root [sudo] password for yourusername: type-your-pass-here New password: type new root pass here

---

### Post by westie457 on 2012-06-04
This is probably the thing you want.
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by VE6EFR on 2012-06-04
bcaperton75 - Do I type that all on one line? When I do I get the following:

[sudo] password for jeff: 
jeff is not in the sudoers file.  This incident will be reported.

No clue what that is about.


westie457 - I'll look through that documentation. Thanks for the link.

---

### Post by wilee-nilee on 2012-06-04
> **VE6EFR said:**
> bcaperton75 - Do I type that all on one line? When I do I get the following:

[sudo] password for jeff: 
jeff is not in the sudoers file.  This incident will be reported.

No clue what that is about.


westie457 - I'll look through that documentation. Thanks for the link.

You need to be in a admin account to use the sudo function, are you?

---

### Post by VE6EFR on 2012-06-04
> **wilee-nilee said:**
> You need to be in a admin account to use the sudo function, are you?

My account is the only account on this computer. When I setup this machine I let it do it's own thing and didn't change any of the defaults.

How would I make sure my account is an admin account instead of a user account? /edit Ok, I went into user accounts and it is telling me that my account is a standard user. However I am unable to change from a standard user to an admin account due to the fact that it isn't accepting my root password.

So, would the link that was given to me by westie457 allow me to reset the root password? Or is that only for user passwords?

By the way, when I log off and back in, it accepts my password no problem.

---

### Post by wilee-nilee on 2012-06-04
> **VE6EFR said:**
> My account is the only account on this computer. When I setup this machine I let it do it's own thing and didn't change any of the defaults.

How would I make sure my account is an admin account instead of a user account? /edit Ok, I went into user accounts and it is telling me that my account is a standard user. However I am unable to change from a standard user to an admin account due to the fact that it isn't accepting my root password.

So, would the link that was given to me by westie457 allow me to reset the root password? Or is that only for user passwords?

By the way, when I log off and back in, it accepts my password no problem.

Somehow, your admin account which is the default on a install has been made into a standard user, not sure of the fix myself.

---

### Post by westie457 on 2012-06-04
By default the root account is locked with an unknown password.
Logging in as root is discouraged on the Forum as is explaining the steps to do this. See here for more information [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The psychocats tutorials are a recognised safe way to do things.

---

### Post by VE6EFR on 2012-06-04
This seems to be an odd one for sure. If all else fails I can do a fresh install of 12.04 LTS however I am wanting to see if I can learn something in the process of solving this issue.

I don't really know what happened to change my user from an admin to a user account. This would explain why I can't install the updates. I don't remember ever being asked for a root password before but maybe the reason is because of my account status.

If I can't restore admin privs to my user account perhaps a fresh install would be the best way to go. The only pain about going this route is that since I don't know how it happened in the first place I won't really know how to avoid this from happening in the future.

---

### Post by linuxman94 on 2012-06-04
In order to add your account to the admin group and allow the use of sudo, follow the Pschocats tutorial that westie linked until it gets to ls /home command.  Then you will want to do run this command.  Replace username with your username.

```
adduser username admin
```

You can then reboot and try running update manager again.

---

### Post by VE6EFR on 2012-06-04
> **linuxman94 said:**
> In order to add your account to the admin group and allow the use of sudo, follow the Pschocats tutorial that westie linked until it gets to ls /home command.  Then you will want to do run this command.  Replace username with your username.

```
adduser username admin
```

You can then reboot and try running update manager again.

Ok, will do. I will post again to let everyone know how it goes. Thanks again for the help.

---

### Post by VE6EFR on 2012-06-04
This just keeps getting better and better. I followed the directions and was given the following as a reply:

The group 'admin' does not exist

Any other ideas? I really appreciate all of the suggestions. Without you guys I would be totally lost.

---

### Post by coffeecat on 2012-06-04
> **VE6EFR said:**
> This just keeps getting better and better. I followed the directions and was given the following as a reply:

The group 'admin' does not exist

Any other ideas? I really appreciate all of the suggestions. Without you guys I would be totally lost.

Are you running 12.04? The admin group is now called sudo in 12.04. If you are running 12.04, try this in recovery mode:

```
adduser username sudo
```

---

### Post by VE6EFR on 2012-06-04
> **coffeecat said:**
> Are you running 12.04? The admin group is now called sudo in 12.04. If you are running 12.04, try this in recovery mode:

```
adduser username sudo
```

That fixed the problem. Thanks for the help everyone. I will change the message status to solved.

---


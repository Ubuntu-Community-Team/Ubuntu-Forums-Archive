---
title: "No Admin Account"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by mighty duck on 2013-01-18
Well, I just downloaded Ubuntu via a Wubi installer onto my Windows Vista system. The only issue is, I can't do much of anything. When I try to do things like connect to the Internet, it asks for a root password. Issue: there is no root password. The only account has standard permissions; there is no administrator account. I can't run su or sudo, obviously. I obviously need to create an administrator account. Is there some command I can run in the grub menu or terminal that would give the account I use admin permissions? I've tried every variation of a password I would use and tons of usual misspellings, but they haven't worked. The password for the account I use works. How can I set it up so the account I use has admin permissions? I would appreciate any help.

---

### Post by helpee on 2013-01-18
To set up your root pw, the terminal command is

sudo passwd

Enter your sudo pw to get the temporary privledges and then enter your new *NIX pw twice as prompted.

You said sudo does not work, and that there are no other accounts on the system? A clean install should let you use sudo *** and then prompt you for the pw that you logged into your regular account with. If that does not work, I'd highly recommend re-installing Ubuntu, as you won't get far without sudo.

---

### Post by brusegadi on 2013-01-18
Also, the password requested by sudo is **your user** password.  For example, in my computer, my user name is **joe**, so when I do sudo, I enter the same password I enter when I log in as joe.  

In ubuntu, the administrator or root account is locked.  There are, however, users who are allowed to temporarily impersonate the administrator or root account.  The users who have permission to do this do it using the **sudo** command.  Since sudo is so sensitive, when you use it, you have to prove that you are indeed the intended user (in my case joe) and this is done by providing your password.  Hope that was not too convoluted.  For a better explanation, check out:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by CharlesA on 2013-01-18
> **mighty duck said:**
> Well, I just downloaded Ubuntu via a Wubi installer onto my Windows Vista system. The only issue is, I can't do much of anything. When I try to do things like connect to the Internet, it asks for a root password. Issue: there is no root password. The only account has standard permissions; there is no administrator account. I can't run su or sudo, obviously. I obviously need to create an administrator account. Is there some command I can run in the grub menu or terminal that would give the account I use admin permissions? I've tried every variation of a password I would use and tons of usual misspellings, but they haven't worked. The password for the account I use works. How can I set it up so the account I use has admin permissions? I would appreciate any help.

It asks for the password of the user who installed Ubuntu. The first user account has sudo privileges.

> **helpee said:**
> To set up your root pw, the terminal command is

sudo passwd

Enter your sudo pw to get the temporary privledges and then enter your new *NIX pw twice as prompted.

You said sudo does not work, and that there are no other accounts on the system? A clean install should let you use sudo *** and then prompt you for the pw that you logged into your regular account with. If that does not work, I'd highly recommend re-installing Ubuntu, as you won't get far without sudo.

There is no need to set a root password when sudo works fine.

---

### Post by izzaboo on 2013-01-26
If I missed something above, I apologize.

What to do if, say, one of your kids, or someone else you know and love, makes a new admin account, changes current admin account to standard account but *doesn't create a password* for the new admin account?

How can one go about either creating another admin account *or* setting a password for the only existing admin account that is currently login disabled?

Grrrrr!

---

### Post by linuxsyst on 2013-01-26
Okayy :-) switch off the computer when switching on right after computer first screen disappears hold Shift and choose Ubuntu recovery mode press enter on it and there will be a box and choose Root command prompt there type ```
mount -o rw,remount /
``` after that type either ```
passwd (username)
```to change the password or to add new user - ```
adduser (username)
``` there it will ask for pass name etc you can ignore something by pressing enter and then when you finish creating new account type ```
passwd root
``` so that won't happen again after that either ```
exit
``` and there press resume orjust type ```
reboot
```

---

### Post by izzaboo on 2013-01-26
Works like a charm.

Found a similar one at [psychocats]("http://www.psychocats.net/ubuntu/resetpassword") just after posting here.

Thanks so much!

---


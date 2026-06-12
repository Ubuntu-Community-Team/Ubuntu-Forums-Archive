---
title: "Having Problem with Sudo"
date: 2017-01-26
forum: New to Ubuntu
---

### Post by ferfykins on 2017-01-26
When i'm on my limited account "ferf", it tries to use sudo with my limited account (ferf)
rather then my root account "Steve"


Anyone know how to fix this?


also having trouble installing clamav
I tried: apt-get install clamav

it seemed to install, but then when i use "Search your computer" it doesn't show up for some reason...

---

### Post by wildmanne39 on 2017-01-26
Root account is disabled by default in ubuntu, it is the user account that uses sudo.
[http://manpages.ubuntu.com/manpages/xenial/man8/sudo_root.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/sudo_root.8.html)

Edit:

Did you edit the sudoer's file?

---

### Post by lisati on 2017-01-26
As well as the page mentioned by wildmanne39, there is [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

To scan your computer with clamav, use the **clamscan** command. To update its database, use the **freshclam** command.

---

### Post by wildmanne39 on 2017-01-26
Please keep the thread to one issue per thread so when people use search terms to find answers they actually find what they are looking for.

---

### Post by ferfykins on 2017-01-26
says "ferf is not in sudoers file. This incident will be reported"


^also steve is my root account

---

### Post by deadflowr on 2017-01-26
^^^ That.
Clamav is a command line only setup.
To get a graphical user interface you need the clamtk package.
Also if using Ubuntu w/unity desktop (or normal Ubuntu) you can install the additional clamtk package clamtk-nautilus, which will give you a right click option to scan file directly in the Files application.
(You can actually just install clamtk-nautilus and it'll automatically bring in the clamtk package)


Also 
> When i'm on my limited account "ferf", it tries to use sudo with my limited account (ferf)
rather then my root account "Steve"


Anyone know how to fix this?

Now, does it actually run if you use a standard user? 
Any user is allowed to try to run as sudo, but only those with sudo rights can.
But typically sudo will try to run with whichever account is current logged in at the time you requested a sudo action.
If that makes sense.

---

### Post by wildmanne39 on 2017-01-26
I am going to back out and let someone else help you because ubuntu disables the root account, I found some research on the error but it does not apply to your situation exactly.

---

### Post by ferfykins on 2017-01-26
> **deadflowr said:**
> ^^^ That.
Clamav is a command line only setup.
To get a graphical user interface you need the clamtk package.
Also if using Ubuntu w/unity desktop (or normal Ubuntu) you can install the additional clamtk package clamtk-nautilus, which will give you a right click option to scan file directly in the Files application.
(You can actually just install clamtk-nautilus and it'll automatically bring in the clamtk package)


Also 


Now, does it actually run if you use a standard user? 
Any user is allowed to try to run as sudo, but only those with sudo rights can.
But typically sudo will try to run with whichever account is current logged in at the time you requested a sudo action.
If that makes sense.  
i installed clamtk-nautilus, i opened clamtk and it says an update is available, but i see no option to actually update


also as far as sudo, it works fine on root account
I try using it on my standard user "ferf" and it gives me the error:

[COLOR=#1D2129][FONT=&quot]ferf is not in the sudoers file. This incident will be reported.[/FONT][/COLOR]

---

### Post by deadflowr on 2017-01-26
There is only one root account, that is root.
Any other user is either an administrator or standard user.

Administrator accounts have sudo rights so they have the ability to run as root.
Standard accounts never have sudo rights so they do not have ability to run as to root.

sudo allows a user to run as root per one command.
And will run as root for the length of time the command needs to be run
If you run *sudo apt update *and the servers are really slow it'll run the command as root until the package index is updated even if it takes ten years to do so, if that make sense.

The first user created, during installation is always an administrator.
All others are default standard users.

you can change this during the creation, or use the administrator account to change it.

You can change it either through the terminal
(you need to login as the admin user to do so)
```
sudo adduser username sudo
```
change username to the user's name.
this will add the user to the sudo group giving the user sudo rights.

Or open the program called User Accounts and change it here
(You do not need to actually login as the admin here as you only need to unlock the settings; this method allows you to choose an admin user to unlock it with)
(The unlock is literal as there will be a lock icon in the top right corner, depending on version of Ubuntu may or may not say unlock)
Then just toggle the account type from standard to administrator.

Hope it helps

---

### Post by ferfykins on 2017-01-27
Thanks so much deadflwr, that clarifies things :)

---


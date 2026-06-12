---
title: "Can't add new users"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by litlfrog on 2008-07-15
I've seen a couple of threads related to this, but nothing quite like the problem I'm having and no real resolution to the problems closest to mine.

I did a fresh install of Ubuntu 8.04 and did all available updates. I realized that the user account I created during initial install was not one I wanted to have admin privileges. I created a new user with administrative privileges with no problems. 

I restarted and logged in to the new account I had just created with no trouble. When I go to System -> Administration -> Users and Groups and click Unlock at the bottom, the system appears to do nothing for several seconds, then pops up an error saying "Could not authenticate. An unexpected error has occurred." Per the suggestion on a different thread, I closed this window, opened the terminal, and typed sudo users-admin. This gave an error message stating 

CRITICAL **: Unable to lookup session information for process '6627'

This does open the Users Settings window, but gives me the same "Could not authenticate" error. All I want to do is change the access privileges of the initial account I created to those of a regular user--am I doing something wrong?

---

### Post by bumanie on 2008-07-15
Not 100% sure on this, but I fancy I read that the first account, must be administrator, who then sets permissions for other accounts. This is not exactly the same as your issue, but try to follow and adapt the guide to change around the users and groups. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by bobnutfield on 2008-07-15
You might want to take of look at this thread.  It seems to be a similar issue:

[http://ubuntuforums.org/showthread.php?t=653921&highlight=unable+find+session+cookie]("http://ubuntuforums.org/showthread.php?t=653921&highlight=unable+find+session+cookie")

---

### Post by litlfrog on 2008-07-15
*nods* It looks like much the same issue, but still doesn't contain anything that solves the problem. Is policykit the software that's running when I select System -> Administration -> Authorizations? If so, can I effectively change the privileges of a given user by individually choosing them that way? It's not as quick as System -> Administration -> User Accounts, Unlock, select account, and changing Properties, but I'm willing to change Authorizations one by one if that'd be a fix for now.

---

### Post by bobnutfield on 2008-07-15
The answer is a qualified "yes" you can change authorizations in this manner.  Unless someone corrects me, Hardy does use policykit this.

Bob

---

### Post by unutbu on 2008-07-15
Edited 2008-09-01: WARNING: It is very hazardous to change the path of your home account. Your home account is filled with configuration files that make reference to /home/olduser. If you change the path to your home account to /home/newuser, the configuration files will still make reference to /home/olduser, and subsequently a lot of applications will start acting weird because the configuration file is broken.



I've never used this before, so you may want to research this to make sure I'm not misleading you.
I'd also appreciate it if others would chime in to either confirm or deny that this works:

 
```
sudo usermod --login NEWNAME --home /home/NEWNAME -m OLDNAME
sudo groupmod --new-name NEWNAME OLDNAME

```

According to the man pages, these commands should rename your OLDNAME account to NEWNAME. It will also move the home directory, and all the contents within it.
The second command alters /etc/group so your group name will also be changed from OLDNAME to NEWNAME.

So, perhaps you can use this to bypass the problem. (Your OLDNAME account has admin privileges, but you can rename it NEWNAME.)

Edit: I tested it and it seems to work.

---

### Post by litlfrog on 2008-07-15
> **unutbu said:**
> I've never used this before, so you may want to research this to make sure I'm not misleading you.
I'd also appreciate it if others would chime in to either confirm or deny that this works:

 
```
sudo usermod --login NEWNAME --home /home/NEWNAME -m OLDNAME
sudo groupmod --new-name NEWNAME OLDNAME

```

According to the man pages, these commands should rename your OLDNAME account to NEWNAME. It will also move the home directory, and all the contents within it.
The second command alters /etc/group so your group name will also be changed from OLDNAME to NEWNAME.

So, perhaps you can use this to bypass the problem. (Your OLDNAME account has admin privileges, but you can rename it NEWNAME.)

Edit: I tested it and it seems to work.

Well, at least I was able to get rid of the initial account. I now have only one account, and that's OK for now. I still need to add a new account with limited authorizations, and I'm not seeing how to do that.

In addition, I've just discovered that I can't seem to install any new programs. Neither Synaptic Package Manager nor Add/Remove Programs shows up in my menu. When I go to System -> Preferences -> Main Menu and select Administration at the very bottom of the left-hand window, I do have an option for Synaptic Package Manager in the right hand window. It's in small, italic type though, and when I put a check in the box next to it, the checkmark goes away after a couple of seconds.

---

### Post by unutbu on 2008-07-15
litlfrog, the original account was part of the admin group. Membership in the admin group is what allows you to use sudo, and do things like install new programs with Synaptic.
You've gotten rid of that account. The second account (the one remaining) does not have membership in the admin group. That's why Synaptic is not working.

To fix: Press ESC during the boot process to get to the GRUB menu. Select Recovery Mode. This should drop you into a root shell. Then type
```

gpasswd -a USERNAME admin
```

replacing USERNAME with your real user name. The command above adds USERNAME to the admin group.

Then type 
```

init 2
```

to get back to a regular boot.

Hopefully, you'll then be able to use Synaptic and create new users the normal way.

---

### Post by litlfrog on 2008-07-16
> **unutbu said:**
> litlfrog, the original account was part of the admin group. Membership in the admin group is what allows you to use sudo, and do things like install new programs with Synaptic.
You've gotten rid of that account. The second account (the one remaining) does not have membership in the admin group. That's why Synaptic is not working.

To fix: Press ESC during the boot process to get to the GRUB menu. Select Recovery Mode. This should drop you into a root shell. Then type
```

gpasswd -a USERNAME admin
```

replacing USERNAME with your real user name. The command above adds USERNAME to the admin group.

Then type 
```

init 2
```

to get back to a regular boot.

Hopefully, you'll then be able to use Synaptic and create new users the normal way.

Yes! Thanks, this worked fine. I'm up and running again.

---


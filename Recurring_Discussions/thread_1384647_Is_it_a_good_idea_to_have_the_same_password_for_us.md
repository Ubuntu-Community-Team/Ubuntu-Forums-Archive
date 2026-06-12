---
title: "Is it a good idea to have the same password for user as root?"
date: 2010-01-18
forum: Recurring Discussions
---

### Post by mamamia88 on 2010-01-18
other distros have separate passwords and wonder what you guys think when ubuntu gives you the same password for user and root?

---

### Post by snowpine on 2010-01-18
Ubuntu does not have "the same password for user as root." The root account is locked in Ubuntu; there is no root password. You can't log in as root directly and have to use sudo instead. Check it out:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Is it a good idea? It has its pros and cons. It can be a little confusing for users coming from different Linux distros, but maybe a little easier for someone using Linux for the first time.

---

### Post by juancarlospaco on 2010-01-18
Theres no root on Ubuntu by default

---

### Post by nothingspecial on 2010-01-18
You have to "pretend" to be root.

---

### Post by mamamia88 on 2010-01-18
ok.  so is it a good idea that ubuntu makes the sudo password the same as the user password?

---

### Post by aysiu on 2010-01-18
> **mamamia88 said:**
> ok.  so is it a good idea that ubuntu makes the sudo password the same as the user password?
*sudo* passwords are, by definition, the same as the user password.

Read the link snowpine put up earlier. It includes a list of pros and cons of the sudo v. root security models.

---

### Post by MoRoBoShi on 2010-01-18
Ciao mamamia..
as far as I know everything related with root privileges is written into the /etc/sudoers..
we all know that ubuntu is a debian derived distro.
Recently I've installed a debian lenny to see how it works.. I can tell you that ubuntu threats user privileges in a easier way.
Maybe that's why it seems that user and root have the same password.:roll:

---

### Post by sisco311 on 2010-01-18
It's a good thing, you don't have to remember two passwords. :)

> **aysiu said:**
> *sudo* passwords are, by definition, the same as the user password.


That's not true. sudo passwords are, _by default_, the same as the user password.

You can change the authentication mode in the sudoers file.

If the rootpw flag is set, then sudo will prompt for the root password & if the targetpw flag is set, sudo will prompt for the target user's password.

---

### Post by dragos240 on 2010-01-18
Yes. It's fine. I do it.

---

### Post by blueshiftoverwatch on 2010-01-18
It depends on what you are doing. Personally, I have different root and user passwords. But I don't think that for most people it would be that much of a security compromise to use the same passwords for both. It depends on how concerned you are about people not getting into your system. If your overly concerned you would probably already be encrypting your /home directory since passwords aren't overly advanced methods of protection. Anyone could crack your password if given enough time. Since most people leave their computers running all day they'd have all the time in the world to attempt to brute force it.

Also, if someone knew your user password, couldn't they just use the sudo command to act as if they were root and would therefore basically have root access to all of your system?

---

### Post by aysiu on 2010-01-18
> **sisco311 said:**
> 
That's not true. sudo passwords are, _by default_, the same as the user password.

You can change the authentication mode in the sudoers file.

If the rootpw flag is set, then sudo will prompt for the root password & if the targetpw flag is set, sudo will prompt for the target user's password. Good to know. Thanks for the correction.

---


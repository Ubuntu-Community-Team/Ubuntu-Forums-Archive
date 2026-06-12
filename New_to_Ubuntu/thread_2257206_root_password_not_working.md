---
title: "root password not working"
date: 2014-12-17
forum: New to Ubuntu
---

### Post by unix-lover-2011 on 2014-12-17
Dear Ubuntu Gurus,

I am not able to login to root as my root password is not working.

All I did was Installed Ubuntu Desktop 14.04 and ran only three commands.

apt-get update        
apt-get dist-upgrade
reboot

After reboot I realized that my Full Screen is not working, I tried to install it but was giving errors therefore tried to double click disc like icon and it was asking my root password. I am giving correct password but it is always saying.

Your authentication attempt was unsuccessful. Please try again.

Would greatly appreciate any help, as I need to install Oracle 11g Database + WebLogic 11g for my own learning.

Thank you very much.

---

### Post by lisati on 2014-12-17
The password for the root account disabled by default in Ubuntu.

If you are logged in using the account created when you installed Ubuntu, using the same password as your user account should be sufficient when prompted for a "root" password.

In some situations you will need to use "sudo" to temporarily get the equivalent of superuser ("root") privileges.

For more information, see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by unix-lover-2011 on 2014-12-17
Doesn't work, that is why I came here. I have a VM and am trying to install Guest Additions that where the problem is. Previously I did su - and sudo su - root and both worked. To keep things easy I kept "oracle" and "root" password same.

---

### Post by nerdtron on 2014-12-17
If you are on ubuntu (logged in as normal user) just run "sudo -i" then input your current account password (not the root password) and you should be root.

---

### Post by unix-lover-2011 on 2014-12-17
I am stuck and I need to come out from trap.

oracle is not in sudoers file. This incident will be reported.

---

### Post by nerdtron on 2014-12-17
> **unix-lover-2011 said:**
> I am stuck and I need to come out from trap.

oracle is not in sudoers file. This incident will be reported.

Is oracle the first account you created? Is this the main account? What did you do before you got this error?

---

### Post by unix-lover-2011 on 2014-12-17
Yes this is the first account which is created.

I can login with oracle and its password but sudo su - or sudo su - root or even simple sudo is not working scary stuff.

---

### Post by unix-lover-2011 on 2014-12-18
I built another vm this time I did exactly same steps.

Installed Ubuntu 14.04
apt-get update
apt-get dist-upgrade
reboot

However I did set password for root, and I could re-install guest additions without any issue. The fact that it is not working on first vm(I didn't not setup root password that's the only difference) is weird. I mean why sudo shouldn't work on first VM after upgrade ?

---

### Post by lisati on 2014-12-18
Setting a password for *root* is often discouraged, because it is very easy to break a system through a simple typo. Many of us would do something like this from their admin account (the one set up during installation):
```

sudo apt-get update
sudo apt-get upgrade

```

The only way I can think of that the admin user was unable to use sudo is if it was disabled on purpose: a "standard" installation of Ubuntu normally comes with sudo access for the admin user.

---


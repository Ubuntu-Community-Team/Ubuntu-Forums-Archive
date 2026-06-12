---
title: "administrator needs permission"
date: 2017-07-18
forum: New to Ubuntu
---

### Post by jaxom98 on 2017-07-18
System : MSI K9M2GM
              2 Gb RAM
              250 Gb barracuda HDD
Sometimes I get an error message (in popup box)  You don't have the required privledges to perform this action
clicking on "details" gets the following   ```
org.freedesktop.PolicyKit.Error.Failed  ('system-bus-name",{'name':':1.84'}):org.debian.apt.install-or-remove-packages
```
There is only one password on the system and that must be entered to startup, effectively I am logging in as administrator I thought.  Why does the administrator not have permission???  The error message pops up after I have re-entered the password to confirm permission to get a program, even when getting off a live disk (Linux Format DVD) or ubuntu repository.

---

### Post by QIII on 2017-07-18
Hello!

That you are logged in to your GUI as the "admin" user who installed the OS does not mean that you can do anything you want without entering your credentials again.  This is a standard security/safety feature.

If you are using the terminal to install new software, for instance, you will need to prepend the command(s) with "sudo" and enter your password when prompted.

---

### Post by Bucky Ball on 2017-07-18
For instance:

```
sudo apt update
```

'sudo' is more or less 'su' = superuser, 'do' = do. In other words, superuser do this, with 'this' being the command that follows.

So sudo gives you admin permissions for the command that follows it. Try running the command above without sudo, as a regular user, and you will receive a bunch of 'permission denied' errors. 

Hope that helps further.

---

### Post by vocx on 2017-07-18
> **jaxom98 said:**
> System : MSI K9M2GM
              2 Gb RAM
              250 Gb barracuda HDD
Sometimes I get an error message (in popup box)  You don't have the required privledges to perform this action
clicking on "details" gets the following   ```
org.freedesktop.PolicyKit.Error.Failed  ('system-bus-name",{'name':':1.84'}):org.debian.apt.install-or-remove-packages
```
There is only one password on the system and that must be entered to startup,** effectively I am logging in as administrator I thought**.  Why does the administrator not have permission???  The error message pops up after I have re-entered the password to confirm permission to get a program, even when getting off a live disk (Linux Format DVD) or ubuntu repository.

Negative. Linux is designed with security in mind, so you are actually not logging in as administrator. You are logging in as a regular user. Your user, however, by default is included in the "adm" and "sudo" groups, so it is able to temporarily gain administrator permissions to do some things, like install programs and modify system files. This is a security feature, which means you have less chance of accidentally modifying and breaking your system.

Run the following commands to confirm that you are in the "adm" and "sudo" groups.
```

groups
id

```

By the way, the specific error that you are getting is puzzling. I've never seen it before. You should not get it if everything works normally.
```

org.freedesktop.PolicyKit.Error.Failed  ('system-bus-name",{'name':':1.84'}):org.debian.apt.install-or-remove-packages

```

According to another thread, this may mean you software center is not correctly installed
[https://askubuntu.com/questions/549896/software-cant-be-installed-or-removed-because-the-authentication-service-is-not](https://askubuntu.com/questions/549896/software-cant-be-installed-or-removed-because-the-authentication-service-is-not)

So maybe try reinstalling it.
```

sudo apt-get --purge --reinstall install software-center software-properties-common software-properties-gtk

```

Or make sure PolicyKit is correctly installed, if you are using KDE.
```

sudo apt install polkit-kde-1

```

Most reports for this error are from 2013 and 2014. Here it seems the error was fixed in the source code of PolicyKit [https://github.com/dnschneid/crouton/issues/784](https://github.com/dnschneid/crouton/issues/784)

What version of Ubuntu are you using? If you have one of the old versions, it's better to upgrade to 16.04 at least, because it's a stable, long term support version.

---

### Post by jaxom98 on 2017-07-19
I forgot to state the OS which is Ubuntu 14.04
I had tried to update to 16.04(failed) immediately prior to using the Linux Format DVD and getting the error mesage.
Bucky Ball, I tried to update via termanil and failed on startup.(password once)
vocx I tried both, purge seemed to run then stopped, I don't know what happened(it did need password twice). The polkit command seemed to work, but on restart I was back to square one.(password once) 
Thank you for your time.
In the end I burned a new 32 bit 16.04 disc and did a clean install instead of an up grade.  Problem eliminated.

---

### Post by Bucky Ball on 2017-07-19
Good news. Presume you have a 32bit processor in that machine? I can find little detail on 'MSI K9M2GM'. If not 32bit, you should go for 64bit, but you probably know that. ;)

Please mark the thread as solved to help others by using Thread Tools at the top right of the page. Enjoy.

---

### Post by jaxom98 on 2017-07-20
Thread now marked solved.
Thanks for the reminder.

---


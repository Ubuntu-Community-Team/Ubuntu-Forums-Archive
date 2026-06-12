---
title: "sudo not updated when user resets password"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by Izziedee on 2014-02-26
Hi All,
I am using Ubuntu 13.10 (upgraded last week). I always use sudo with no problems. I also never changed my password. Today, because of a security breach with an organization of which I am a member, I had to change my password. This is what I did. I can log in and log out. 

Problem: how do I tell sudo that I have a new password. I am still in the sudo list with the old password. I tried changing my password back to the old password. This worked fine. But now, sudo does not ask me for any password. I can do anything I want by just typing sudo. I have been to many "fix sudo" webpages but none of them seem to answer this question.

Rose

---

### Post by TheFu on 2014-02-26
Exactly how did you change your password?

---

### Post by Izziedee on 2014-02-26
I went into System Setttings, users. My account type is administrator. I clicked on the unlock button, entered my sudo password. Then I clicked on the password to change. Hmm. It looks like I did this as administrator (sudo) and not as a normal user. Could this be what is causing the trouble? I confess that I did this without thinking. The only way I can think of to fix it is to create another administrator account, remove my username from the sudo list and then add it again. Or, use "sudo passwd username"?

Using [advice here]("http://askubuntu.com/questions/248853/graphical-authentication-works-why-does-sudo-say-my-password-is-wrong"),
I get:
>pkexec apt-get --purge --reinstall sudo >>>>results in E: Invalid operation sudo

>pkexec grep Defaults /etc/sudoers >>> results in 3 items
env_reset
mail_badpass
secure_path

I think the mail_badpass is an indicator that something is wrong. The pkexec commands all ask for a password and accept the one I give them.

---

### Post by TheFu on 2014-02-26
To change your personal password. Open a terminal and type:
```
passwd
```

To change the root password, open a terminal and type:
```
sudo passwd
```

GUIs get in the way for simple things like this, IMHO.  Also - root really shouldn't have any password on debian/ubuntu/mint systems. It is a security consideration.

Also, by using the terminal for this (and making it a habit), you'll never worry how to do it again. This has worked for 30+ yrs, on all flavors of UNIX (AIX, HP-UX, Linux, Solaris, SunOS, BSD, Digital Unix, OSF/1, Ultrix, Irix, ..... ), desktops and servers. You get the idea.  Some things just shouldn't be made harder by a GUI.

Ok - so I'm not being completely honest here.  In the 1990s, many companies use NIS, so to change the password, it was **yppasswd** instead. ;) Many admins would setup aliases for users, so they didn&#8217;t need to know about the difference.

---

### Post by Izziedee on 2014-02-26
I have got my password working with "passwd". I am not a big fan of gui's, I just got lazy because I usually have to look up the syntax for the command "passwd".  

Once I got used to sudo, I have never intensionally changed or looked for the root password. In my current case, it was sort of an accident. My main worry is that I do not know what the current root password is and it might very well be nothing. This is a worse security. Do you recommend that I change it to some well-designed password and then forget it? 

Also, I was getting errors with package installs using "pkexec apt-get". I re-installed "sudo" using SYnaptec Package Manager, as SPM asked for the sudo password graphically. Now, sudo is asking me for a password. All is well. 
Thanks,
Rose

---

### Post by TheFu on 2014-02-26
sudo and GUI programs should generally be avoided.  Here's why - sudo/gksudo change the effective uid, but not all the environment, so if any configuration files are stored in HOME, they will be owned by root (the effective uid) at the time.  Later, sometimes months later, we will run that program again and get permission denied just becuase the config file is owned by root.  That will spiral into "always use root"-isms which is bad.

**passwd -h** will explain the options. Most commands work that way.
OR there is always the manpage.
**man passwd**
so all the answers are already on your system ... for 99% of the commands on the box.  Better than using google, since the manpage ON-YOUR-SYSTEM will match the version of the command ON-YOUR-SYSTEM too.  

Also - you might prefer aptitude package manager - **sudo aptitude** - is smart about dependencies, provides a CLI interface and is recommended over apt-get by the debian team.  I've had it solve package dependency issues when apt-get and synaptic failed.

I've never heard of **pkexec**, sorry. Only been doing Linux stuff 21 yrs and have much more to learn. ;)

---

### Post by Dave_L on 2014-02-26
> **Izziedee said:**
> Once I got used to sudo, I have never intensionally changed or looked for the root password. In my current case, it was sort of an accident. My main worry is that I do not know what the current root password is and it might very well be nothing. This is a worse security. Do you recommend that I change it to some well-designed password and then forget it? 

This article explains how to disable the root password:
[https://help.ubuntu.com/community/RootSudo#root_account](https://help.ubuntu.com/community/RootSudo#root_account)

To see whether it's enabled (refer to [http://manpages.ubuntu.com/manpages/precise/man5/passwd.5.html](http://manpages.ubuntu.com/manpages/precise/man5/passwd.5.html)):
```
grep root /etc/passwd
sudo grep root /etc/shadow
```

---

### Post by Izziedee on 2014-02-26
Thanks!

---

### Post by Izziedee on 2014-02-26
I learn mostly by making mistakes ....I found pkexec on the stackoverflow Ubuntu forums. I never heard of it either.

---


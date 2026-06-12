---
title: "How to install programs as a standard user?"
date: 2015-09-05
forum: New to Ubuntu
---

### Post by A_Cloudy_Day_In_Ma on 2015-09-05
I am very new to Linux, I just installed it yesterday, and I heard that it is often a good idea not to use an Administrator account as your main account, so I made and Administrator account and a Standard account. Now I want to install Steam using Terminal on my Standard account, but I can't figure out how to do this (I think it's easier to use Terminal because otherwise I'll have some missing libraries later on that I need to install with Terminal anyway). This is what I do:

When I use my own password:
```
summer@trusty-tahr:~$ sudo apt-get install steam
[sudo] password for summer: 
summer is not in the sudoers file.  This incident will be reported.
```

Will I get in trouble for this report? Who does it report to?

When I use the Administrator password:
```
summer@trusty-tahr:~$ sudo apt-get install steam
[sudo] password for summer: 
Sorry, try again.
```

Does anyone know how to help me?

---

### Post by cdh79 on 2015-09-05
yes, you will be reported to the FBI and NSA automatically (just kidding ;) )

normally in Unix/Linux you have the user "root", which is basically the highest administrator account.. while many sysadmins have (and still) used this user "root" as a regular user, it is not recommended, as often you can break things unintentionally when you're not exactly aware of what you're doing.. 
i'm still rather new to Ubuntu myself (however having had some Linux experience on other distributions over the past 15 years) in Ubuntu "root" is not a "regular" user that you just log in with, so i personally believe that it would not have been necessary to create a second user (others might feel different about this)

the "is being reported" means that the administrator (which in your case is you as well, however in other systems it might be someone else enforcing for instance company policies), will be informed that the user "summer" tried to do something that was not permitted..

the reason you cannot "sudo" is that your user seems to not be in the group of users that are allowed to do use the command "sudo"..
with the command "sudo" you are giving yourself administrational permissions for the command that follows it (i.e needed when you're trying to install something), and therefore have to enter an administrational password

what you can do in this case, is log in with your administrator user, and add the user "summer" to the group of sudoers by issuing the command "sudo adduser summer sudo"
as your administrator-user is allowed to get root-permission (which is actually needed to add the user to this group) this should work..

then again, you wouldn't really have needed a plain user-account next to your account with administrator permissions, if you add this normal user to the sudoer-group

---

### Post by grahammechanical on 2015-09-05
Unlike other distributions Ubuntu has the so-called root account disabled by default. So, unlike some other distributions we cannot run Ubuntu as root or administrator but we can accomplish all the administrator tasks that we need to.

When we try to do something that requires root or administrator privileges we get a dialog that asks us to authenticate. We put in the password that we created during the installation process and for the period that the task is active we are working as administrator/root. And then, when the task is completed our administrator privileges lapse and we continue working as a standard user.

There was no need to create an administrator account because you were already listed as administrator. If you were not administrator you would not have been able to create another administrator account or even a standard user account.

When, a standard user runs a command that only an administrator should be running we get an error message that says we are not root. We get the same message if we run the command without the "sudo" prefix.

Using the prefix of "sudo" triggers as request for a password. Standard users do not have the necessary privileges to run what we might call "sudo commands." That is why they are standard users. It is to stop a standard user from wrecking the OS. And so, the OS puts up that warning.

There will be a log somewhere that records the attempt and which a system administrator can access. This is useful in a business environment to check if employees are misusing the trust of the employer. Such as downloading and watching videos.

Regards.

---

### Post by SeijiSensei on 2015-09-05
Short answer:  the account you created during installation has "root" (administrative) privileges.  If you log in with that account and use "sudo" as you did in your post, you will be prompted for your login password.  Once you enter it, you will have admin privileges and can install software.

Details here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Geoffrey_Arndt on 2015-09-05
Let's make it real simple:   In any variant or version of Ubuntu - the FIRST and only user that is actually allowed to be created [U][B]during the install is the admin (e.g., has ability to run commands using sudo)

[/B][/U]After install, the first user often creates the rest of the user pool.   These new users can also have admin privileges by adding them to the sudo'er group (using command line or in other [B][U]gui methods in xubuntu, mate, etc.)

[/U][/B]That's the right way to install, and have a stable, working system.

---


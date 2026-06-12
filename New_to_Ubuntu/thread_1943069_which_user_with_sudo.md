---
title: "which user with sudo?"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by lance bermudez on 2012-03-18
I was reading the sudo man I dont know how to do this but lets say I'm on a desktop user and does not have sudo perviges and want to use a user that does

sudo -u adminUser command

I get "user is not in the sudoers file.  This incident will be reported." 

how is my sintax wrong? Or did i miss read the man and you cant do this?

---

### Post by cortman on 2012-03-18
If you're not in sudoers, there's no way to work as root unless you log in to a root account or a sudoers account. This would involve logging out of your current account and into another.
Not sure I understand the nature of your question. If you need to use sudo, why not add the user to sudoers?

---

### Post by lance bermudez on 2012-03-18
I read that and was thinking of windows like how you can use a admin user account in a desktop user to do things. I thought you had to be part of the sudo user to do that thank you for info.

what man say
Note: the following examples assume a properly configured security policy.

To get a file listing of an unreadable directory:

 $ sudo ls /usr/local/protected

To list the home directory of user yaz on a machine where the file system holding ~yaz is not exported as root:

 $ sudo -u yaz ls ~yaz

To edit the index.html file as user www:

 $ sudo -u www vi ~www/htdocs/index.html

what i get
lubuntu@bermudezl:~$ sudo -u admin apt-get update
[sudo] password for lubuntu: 
lubuntu is not in the sudoers file.  This incident will be reported.

want to change sudo user to admin not leave lubuntu user

---

### Post by HiImTye on 2012-03-19
you can log in to the shell as another user such as:
```
su <user>
```and then issue commands as that user, including escalated commands using sudo

note: you will need to know that users' password

---

### Post by lance bermudez on 2012-03-19
thank you HiImTye

su <user>

was what I was thinking about

---


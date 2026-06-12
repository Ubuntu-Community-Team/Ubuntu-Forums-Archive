---
title: "Root account login results in loop"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by BlueScientist on 2012-03-27
I recently installed Xubuntu on an old laptop to use as netbook. Since it is be the first time I use a different OS, I run it alongside windows. After installing, I set up a root account with a generated password and gave up the administrative right of my regular account. (not being logged in the root account) Now I want to access the root account to install some firewall software, however when I give the password the screen turns black and loops back to the login screen with: 

-the mouse not responding to clicks on the login frame; 
-the power button in the taskbar not working (drops down behind the background);
-no further messages...

What did I do wrong and most of all, how do I fix it.

---

### Post by JC Cheloven on 2012-03-27
Hi, in ubuntu you get administrative privileges by means of the 'sudo' command, not by the use of the root account. Please [read this]("https://help.ubuntu.com/community/RootSudo").

JC

---

### Post by roger_1960 on 2012-03-27
Its not really a good plan to do what you did and not how Ubuntu is designed to work!  Suggest you read carefully the two articles linked below.  You have removed your admin account from the admin group list and you will have to fix it I think.

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by anewguy on 2012-03-27
Indeed, sudo or gksudo (for graphical things like an editor) are used to grant temporary super user status.  In Ubuntu, we shy away from enabling a root account - and we don't don't discuss on this forum how to enable a root account - so, we really won't be allowed to discuss "fixing" the root account.  If this is your first look at a different OS as you indicate, might I suggest you just start over again and use sudo when you need to do something as root - like installing what you are mentioning. 

In this way you'll be following the ubuntu standard, we won't have to get into a discussion of messing with the root account, and all should be well with the world.  At a later point in time, after you gain more experience, if you feel you must enable the root account you can do so on your own then.  For now, just stick with the norm and you'll avoid problems as you are having now.

For those who may want to reply here but don't know:  we don't discuss anything dealing with enabling, "fixing", etc., a root account here.

I would just reinstall, then ask questions if you need help.  Don't do anything with a root account, and don't change your default account after you reinstall.

Dave ;)

---

### Post by NaN010101 on 2012-03-27
I found this
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
in this post
[http://ubuntuforums.org/showthread.php?t=1947482](http://ubuntuforums.org/showthread.php?t=1947482)
in a reply by oldfred 

You can tell by my beancount I'm probably not even sure it's what you're looking for (but it talks about undoing something like you describe).

HTH

---

### Post by zombifier25 on 2012-03-27
This is definitely redundant, but keep in mind that **NEVAH EVAH USE THE ROOT ACCOUNT EVAH AGAIN!**

---

### Post by ranger1021994 on 2012-03-27
> **BlueScientist said:**
> I recently installed Xubuntu on an old laptop to use as netbook. Since it is be the first time I use a different OS, I run it alongside windows. After installing, I set up a root account with a generated password and gave up the administrative right of my regular account. (not being logged in the root account) Now I want to access the root account to install some firewall software, however when I give the password the screen turns black and loops back to the login screen with: 

-the mouse not responding to clicks on the login frame; 
-the power button in the taskbar not working (drops down behind the background);
-no further messages...

What did I do wrong and most of all, how do I fix it.

I guess you entered root password wrong.
U need to change ROOT account password.
It aint d same as ur user password.
Google on how to change ROOT password

---

### Post by BlueScientist on 2012-03-27
Ok it seems that I didn't access the root account after all. I just deleted myself as administrator. I tried to get myself in with the adduser command roger gave me. It returned an error about the password.
However after accessing the account where I revoked the admin rights, I was able to set my account among the admin again. (by means of the admin password I set) but somehow the screen became blurry, so since it was just a try-out and I had no essential files I will just go for the reinstalling...

---

### Post by sffvba[e0rt on 2012-03-27
In SUDO we trust...

*Thread **closed**.*


404

---


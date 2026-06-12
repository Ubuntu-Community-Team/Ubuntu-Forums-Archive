---
title: "login as root issues"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by 007casper on 2008-09-15
How come I cant login as root. 

I have installed an application through the terminal and cant access it through the browser.  

browser says "dont have permission to view this page"  Because all the files are sitting on root, and cant put it on any users till I login to the application from the browser and change its settings.

I log out and try to log back in as root... ubuntu says "the system administrator is not allowed to login from this screen" ???  

How come I cant login as root?  Thank you

---

### Post by niccholaspage on 2008-09-15
You don't want to login as root my friend.
Try this instead:
> 
terminal apps(No GUI)
```
sudo <insert app here>
```GUI apps:
```
gksudo <insert app here>
```

---

### Post by bodhi.zazen on 2008-09-15
To obtain a root shell :

```
sudo -i
```

---

### Post by k33bz on 2008-09-15
Logging in as ROOT has been disabled. Security reasons. You are however able to use SUDO, or in the "Terminal" become ROOT. (su root) or using any one of the commands listed above. But unless there is a script out there, give up on trying to login as ROOT at the login screen.

---

### Post by Tatty on 2008-09-15
You should probably have a read of this page in the community wiki:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by scorchgeek on 2008-09-15
There's really no reason to do it, the sudo command is much simpler and better.

---

### Post by RequinB4 on 2008-09-15
> **scorchgeek said:**
> If you really wanted to log in as root for some reason, you could enable the account with:
xxxxxxxxxxxxxxxxxxxx

Then you can type a password and thereafter log on as root. But there's really no reason to do it, the sudo command is much simpler and better.

[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by billgoldberg on 2008-09-15
> **007casper said:**
> How come I cant login as root. 

I have installed an application through the terminal and cant access it through the browser.  

browser says "dont have permission to view this page"  Because all the files are sitting on root, and cant put it on any users till I login to the application from the browser and change its settings.

I log out and try to log back in as root... ubuntu says "the system administrator is not allowed to login from this screen" ???  

How come I cant login as root?  Thank you


Use sudo or gksudo.

--

If you have to ask on how to enable it, you are not able to yield it's mighty sword by yourself yet. Sudo still needs to hold your hand.

---

### Post by 007casper on 2008-09-15
thank you everyone... thats what I have been doing and all of the comments helped out a lot... I am still having permission issues... I am going to look into it further what it could be... I did gksudo firefox and it still didnt work.  I have installed the application as user root... but it isnt in group root... it is a different user group alto...

so, I tried to change the group to root... so far I am not having much luck... a bit rusty with unix... it has been a while I used one... tired 

$cd /usr/local/spring then tried sudo chgrp root alto... then tired
$cd /usr/local then tried sudo chgrp root alto... no luck... 

hopefully I can figure this out... is there any other way to change the group name?

---

### Post by 007casper on 2008-09-15
sudo chown root:root spring 
was able to change the group name... still cant view the page 'cause of permissions.

---

### Post by dpolehn on 2008-09-15
here is a nice knol on this 

[http://knol.google.com/k/graham-robson/how-to-enable-root-account-in-ubuntu/29fuoz600zxvu/2#]("http://knol.google.com/k/graham-robson/how-to-enable-root-account-in-ubuntu/29fuoz600zxvu/2#")

but having a root account is pretty much useless because of sudo.

---

### Post by scorchgeek on 2008-09-16
Sorry everyone. I'm new and didn't know that I wasn't supposed to post that. Thanks for letting me know.

---


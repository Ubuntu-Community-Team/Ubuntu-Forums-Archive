---
title: "How do you log out a specific instance of a user"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by nam_hee on 2014-01-14
Hi guys,

I know you can log out the user with the command

sudo pkill -KILL -u username

But I don't want to log out every instance of the username.  Just specific one.  For example, I have username logged in twice like this.

username     pts/0        2014-01-14 12:22
username     pts/1        2014-01-14 12:28 


Lets say I want to log out only pts/1.  How would I go about doing this?

---

### Post by deadflowr on 2014-01-14
exit

---

### Post by nilla78ro on 2014-01-14
maybe this will help you : [http://ubuntuforums.org/showthread.php?t=1225880](http://ubuntuforums.org/showthread.php?t=1225880)

---

### Post by ian-weisser on 2014-01-14
A programmatic way is to tell systemd-logind to terminate their session using dbus.

---


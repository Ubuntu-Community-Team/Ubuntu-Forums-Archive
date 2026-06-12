---
title: "How to use SU, is there a defult password?"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by HomesteadMommy on 2012-02-16
Hi I'm really new to Ubuntu, I just set it up yesterday.  I'm trying to install my printer drivers and they can't be loaded through the software installer or found by searching under printer drivers.  Brother has a "tool" to install it with but it has to be run with SU.  When trying to do this it keeps asking me for a password.  But I have no idea what that would be!

I setup Ubuntu with the windows installer and it had me create my user account and pass.  I was never asked for a root or admin password.  How do I find out what this is, or set a new one?  I can't get my printer working until I can figure this out.  I've tried searching and I couldn't find anything that made sense to me...

Thanks,
Kim

---

### Post by sisco311 on 2012-02-16
Hi and welcome to the forums!

By default, the root account password is locked. You have to use sudo instead of su. sudo will prompt you for your user password.


See: [uhelp]community/RootSudo[/uhelp]

---

### Post by oldfred on 2012-02-16
In Ubuntu there is not a SuperUser as default, but as Admin you give yourself temporary superuser rights with sudo. So just use sudo and your password.

Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://xkcd.com/149/](http://xkcd.com/149/)
[https://help.ubuntu.com/community/WikiGuide](https://help.ubuntu.com/community/WikiGuide)

---

### Post by drmrgd on 2012-02-16
Welcome to Ubuntu and the Ubuntu Forums!

When you created your account, likely you were made a system administrator.  This allows you to make system-wide changes using the 'sudo' command.  By default the 'Root' account in Ubuntu is disabled and not necessary. 

The password you're being asked for is likely the one you provided when you set the account up.  Try that one, and keep in mind that the password will not be echoed to the screen (i.e. you can see it when you're typing it).  Rest assured, though, that it is being sent to the system and when you hit enter, the password will have been sent.

So, when you're running your tool, you would just type:

```
sudo <name_of_tool_here>
```

Also have a look at this Community Documentation for more info on 'sudo' and Root:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Wow! I type slow...these guys beat me to it!

---

### Post by HomesteadMommy on 2012-02-16
Thanks everyone!  I finally figured out what I was doing wrong.  Typing SU instead of sudo and since I couldn't see my password being typed I thought it wasn't doing anything. lol  Printer is setup and working, now I'm off to explore the links you all shared. :D

---


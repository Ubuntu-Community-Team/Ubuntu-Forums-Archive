---
title: "[SOLVED] Reboot and Halt commands disabled in Admin/Login Window."
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Ballistixx on 2008-05-24
Hello folks,

I have been using Hardy Heron for less than a week. Somehow I managed to disable the Reboot and Halt commands in Administration/Login Window/Edit Commands and I don't know the correct path to the command to enable it once again. So I can't reboot with the restart icon in the notification area or the reboot button on the Log Off, Switch User, etc window. Please help.

Regards,

Jason

---

### Post by Patb on 2008-05-24
Jason, in a terminal, the command in Ubuntu for that is "shutdown" usually as root.  Look at "man shutdown".  To reboot or halt, the following respective commands should work:
```
sudo shutdown -r now
sudo shutdown -h now
```
Hope this helps.

Cheers, Pat.

---

### Post by Ballistixx on 2008-05-24
Hello Guys,

I tried posting this question and others in the beginners section with no help. I have been using Hardy Heron for less than a week, so I figured that was the appropriate place to post my query. This is my first stab at any version of Linux. 

In trying to figure out a boot error problem I stupidly erased the path for both the Reboot and Halt commands in Administration/Login Window/edit command. I can not re-enable it because I don't remember the proper path to the commands. So now I can't reboot using the restart icon in the notification area say after an update or from the login,switch user,shut down menu.

I tried searching on these forums and the web in general with no luck.
I can't imagine that this is a big problem for someone familiar with Hardy Heron, but judging from the absence of replies I got, it just may be.

I will be very grateful for any help? Maybe a nice forum member could simply look on the system under Administration/Login Window press the edit command button and tell me the path to the Reboot and Halt commands. Please???

Thanks,
Jason

---

### Post by Ballistixx on 2008-05-24
Hello Pat,

Yes I can still reboot in the terminal using the commands you posted.

What I need is for some helpful forum member to look in Administration/Login Window hit the edit command button and post the paths for the reboot and halt commands.

Please???

Thanks,

Jason

---

### Post by N.N. on 2008-05-24
Go to "System" > "Administration" > "Login screen", click the "local" tab, and check the option called "Show action menu" in the section called "Menu line".

EDIT: Oops, that wasn't what you asked for.

The command for shutdown (halt) is as follows: ```
/sbin/shutdown -h now "Shut Down via gdm."
``` The command for rebooting is as follows: ```
/sbin/shutdown -r now "Rebooted via gdm."
```

---

### Post by chrisccoulson on 2008-05-24
Halt:
```
/sbin/shutdown -h now "Shut Down via gdm."
```
Reboot:
```
/sbin/shutdown -r now "Rebooted via gdm."
```
Suspend:
```
/usr/sbin/pm-suspend
```
Hibernate:
```
/usr/sbin/pm-hibernate
```

Hope that helps:)

---

### Post by Ballistixx on 2008-05-24
Thanks for the reply,

The buttons are there. I need to know the path to the commands.

If someone would be kind and go to Administration/Login Window hit the edit commands button on thier system.
Then post what is listed as the path for the Reboot and Halt commands. This is what I need.

Regards,
Jason

---

### Post by N.N. on 2008-05-24
Check my update.

---

### Post by Ballistixx on 2008-05-24
Hi Chris,

Thank You! That was what I needed.

Regards,
Jason

---

### Post by Ballistixx on 2008-05-24
Thanks N.N. Just what I needed.

Strange though, I booted of the live cd and went to Admin/Login Window found the same commands you posted above. When I changed the path to match what was on the live cd account (which also matched what you posted above) it said the was no such file.

I just typed the same path in again and it's fine. Wierd!

Thanks Again,
Jason



Cheers!
Jason

---


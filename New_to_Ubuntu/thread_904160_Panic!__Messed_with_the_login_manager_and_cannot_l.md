---
title: "Panic!  Messed with the login manager and cannot login"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by Stabback on 2008-08-29
Hey all, I had Ubuntu working nice for roughly a month but just tried to enable the login manager.  The system was single user and automatically logged into my account however I recently tried to make it a bit more secure by enabling the manager.  

Something went wrong.

I could not tell you the exact steps that I followed to enable the login screen, however it worked - kind of.  When I turn on the computer the login manager shows up but I get a constantly repeating 'Authentication failed' message.  Is there any way to reset the login manager settings to default from terminal (I can still log in from ctrl-alt-f[1-6])?

Thanks all

---

### Post by RequinB4 on 2008-08-29
on one of the control+alt+f1 f2 etc, login and type ```
/etc/init.d/gdm start
```

Then go and try and undo whatever you did ;P

---

### Post by Stabback on 2008-08-29
I'm sorry, you might have misunderstood what I had said or I was not clear.  The login manager appears (I assume this is GDM - Gnome Display Manager?) and everything is as is should be - except there is an error message saying authentication failed.  If I dismiss the message by clicking it's one button it appears again, in an infinite loop.  Starting GDM does nothing but leave me where I currently am.

---

### Post by swoll1980 on 2008-08-29
in your cli terminal type startx then add a user under system adminastration users I don't think gdm will let you log in as root I am not sure if this is the problem but it's worth a shot

---

### Post by Stabback on 2008-08-29
@swoll
I'm not trying to login as root.  startx does nothing as GDM is already up and running (or I may be misunderstanding what exactly startx does).  The gnome login screen pops up and I get a gnome error message (stating authentication failed), everything has started correctly but it seems as if it is trying to auto-logon when it shouldnt.  Closing the error message just opens another one.

---

### Post by swoll1980 on 2008-08-29
> **Stabback said:**
> @swoll
I'm not trying to login as root.  startx does nothing as GDM is already up and running (or I may be misunderstanding what exactly startx does).  The gnome login screen pops up and I get a gnome error message (stating authentication failed), everything has started correctly but it seems as if it is trying to auto-logon when it shouldnt.  Closing the error message just opens another one.

kill gdm

```
sudo /etc/init.d/gdm stop
```

then start the x server
```
startx
```
it should take you into your Desktop if I'm not mistaken then you can add a user

---

### Post by Stabback on 2008-08-29
Alright, I'm not posting from within Ubuntu.  Thanks for the help so far!  Now I need to get it to stop saying 'authentication failed'.  I've been using gdmsetup to configure my login and can't seem to figure out where to go from here.  Any further ideas?

---


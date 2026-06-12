---
title: "Only Account has lost admin rights"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by ssdurn on 2012-11-02
Hello

Last night I installed hplip to support my printer/scanner.

All seemed well until this morning I couldn't print and now I discover that I am a standard user and no longer an admin.

Mine is the only account on the machine.

Any suggestions on how to recover my admin rights?

---

### Post by steeldriver on 2012-11-02
Do you mean that the user account has actually been removed from the appropriate group (either sudo or admin depending on what version you are running)? if so it should just be a matter of booting into the recovery console and re-adding,  e.g.

```
gpasswd --add *user* sudo
```(or you could use usermod)

OTOH if something has gone wrong with the whole sudo mechanism (bad permissions on the sudoers file for example) that's going to take a bit more investigation

---

### Post by Gone fishing on 2012-11-02
I just want to be clear you can no longer open a terminal and run sudo -i and your password be accepted as a sudo user?

If it is no problem open a terminal run gksu gnome-control-center go to users accounts and change the account to administrator.

If you can't sudo it can be fixed but with a little more effort.

---

### Post by jroa on 2012-11-02
You could boot to a live CD or USB and change the admin rights there.

---

### Post by newb85 on 2012-11-02
If you can no longer use sudo, please follow the following instructions.

[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by ssdurn on 2012-11-02
Thanks everyone:

1. The issue isn't a forgotten password - it's that the only user has lost admin rights and is a now standard user.

2. I have tried to use the recover console but an getting the following error: gpasswd: cannot lock etc/group;try again later

3. I can boot from a live CD but would appreciate instructions on what to do once I've booted.

Thanks
Steve

---

### Post by westie457 on 2012-11-02
newb85 was very close with the link posted.

Try this one instead [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by steeldriver on 2012-11-02
> **ssdurn said:**
> 
2. I have tried to use the recover console but an getting the following error: gpasswd: cannot lock etc/group;try again later


Sounds like you are missing this step:

>  In recent versions of Ubuntu, the filesystem is mounted as read-only, so  you need to enter the follow command to get it to remount as  read-write, which will allow you to make changes: 
```
mount -o rw,remount /
```

---

### Post by newb85 on 2012-11-02
Please check a couple things while not booted from Live media

If you issue the command
```
cat /etc/passwd | grep *username*
```
the output should look like this:
```
[color=red]***username*[/color]**:x:1000:1000:*Full Name*,,,:/home/[color=red]***username*[/color]**:/bin/bash
```

Also, if you issue
```
cat /etc/group | grep
```
the output should be
```
[color=red]**adm[/color]**:x:4:*username*
lp[color=red]**adm[/color]**in:x:109:*username*
```

---

### Post by ssdurn on 2012-11-02
Thanks guys - all resolved.

---


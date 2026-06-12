---
title: "Can not log in after run init command"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by ngubk on 2012-05-29
I just learned about runlevel in Linux. When I tried some command like:
```
sudo init 5
sudo init 3
sudo init 0
```

or st like that. The system started up and can not pass the log in screen (I typed in the password and hit enter, it returned back to the log in screen)
I'm using 12.04 LTS

---

### Post by steeldriver on 2012-05-29
can you still log in to one of the virtual terminals (Ctrl-Alt-F1, Ctrl-Alt-F2, ... )?

if so, do that and then

```
ls -al ~/.*authority

```and post the results here

---

### Post by ngubk on 2012-05-29
32 -rw------- 1 ngu ngu 25118 .ICEauthority
 4. -rw------- 1 root root 53.     .Xauthority

---

### Post by ngubk on 2012-05-29
Also i can log in as the guest.
Thanks for your reply

---

### Post by ngubk on 2012-05-29
I deleted the file .Xauthority (just lucky) and it works.
Can anyone tell me why that can solve the problem?
Thanks very much for your help, [steeldriver]("http://ubuntuforums.org/member.php?u=1627500")

---

### Post by steeldriver on 2012-05-29
well done! that's actually exactly what I was going to suggest  i.e. sudo rm ~/.Xauthority (I just wanted to check that *was* the problem before telling you to try it)

it's quite a common issue - the X server needs to write to that file (as you) as part of the session startup - and it can't if root owns the file - that likely happened in your case because 'sudo init 5' started X with a mix of root permissions and your user environment

---

### Post by Cheesemill on 2012-05-29
> **ngubk said:**
> I just learned about runlevel in Linux. When I tried some command like:
```
sudo init 5
sudo init 3
sudo init 0
```or st like that. The system started up and can not pass the log in screen (I typed in the password and hit enter, it returned back to the log in screen)
I'm using 12.04 LTS

Ubuntu doesn't use init and runlevels anymore and hasn't done for quite some time.
Instead it uses [upstart]("http://upstart.ubuntu.com/").

---


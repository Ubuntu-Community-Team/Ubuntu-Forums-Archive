---
title: "Terminal command is not working any more........."
date: 2016-11-23
forum: New to Ubuntu
---

### Post by hasan5599 on 2016-11-23
Hello helpful guys..................

I am new ubuntu user and installed Ubuntu 16.04 LTS. After using 2 days  now  I am facing a problem . I don't know what wrong I have done , When I put this command  "apt-get update"  as a non-root user then my terminal reply me .....

```
hasan@Anaymous-Pc:~$ apt-get update
W: chmod 0700 of directory /var/lib/apt/lists/partial failed - SetupAPTPartialDirectory (1: Operation not permitted)
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
hasan@Anaymous-Pc:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
hasan@Anaymous-Pc:~$ 
```








but I know that I used this command before it was working then but today it is not working any more . How can I solve this problem ???

Thanks

---

### Post by kpatz on 2016-11-23
Add "sudo" to the front to have it run with root privileges:
```
sudo apt-get update
```

You'll be asked for your password, once you provide it, the command will run.

---

### Post by hasan5599 on 2016-11-23
Yes It is working then but my question is why it is not working as a non-root user because It was working before but not working now.......

---

### Post by kpatz on 2016-11-23
It never worked as a non root user.  At least it's not supposed to.  Most apt commands require root to run.

Maybe you were in a root shell when you ran it one time?

---

### Post by QIII on 2016-11-23
That should not have been working without elevated privileges.  If it was, something was wrong unless you made some pretty specific changes to allow it.  Are you sure you were running apt as a non-privileged user?

---

### Post by hasan5599 on 2016-11-23
I can not say 100% sure because I am a new user here and trying harder to learn it more but as far as I can remember , It was working then.......what's about your terminal  ??? Can "apt-get update" working your terminal as a non-root user  ???

---

### Post by QIII on 2016-11-23
apt will not work without elevated privileges.

That means that you must prefix any commands with "sudo" and enter your password.

The user you created when you installed Ubuntu is by default in the sudoers group, which allows you to do that.

---

### Post by pugstah on 2016-11-23
Same thing happens to me too when I exclude "Sudo" from the command. Weird thing is, I didn't change anything. Is there any possible ways to allow the root user to exclude "sudo" from getting updates?

---

### Post by hasan5599 on 2016-11-23
Yeah !! ........thanks all guys I think I can understand the situation of the problem....Good Luck.

---

### Post by oldos2er on 2016-11-23
Hi hasan5599, if your question has been answered to your satisfaction, please mark your thread 'Solved' under Thread Tools at the top of the page. Thanks!

@pugstah, please create your own thread for your question, it's less confusing for everyone that way.

---

### Post by Habitual on 2016-11-23
> **hasan5599 said:**
> Yes It is working then but my question is why it is not working as a non-root user because It was working before but not working now.......

sudo has a timeout feature set to 10m by default.
If I used
```
sudo apt-get update 
```
and provide my password,
and If I use
```
sudo apt-get upgrade
```
within 10 minutes of the first successful sudo should mean that no password will be required.

It is possible you ran out of the 10m timeout feature provided by sudo.

---


---
title: "apt-get keeps saying to check Internet, while I have a good connection"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by phoenix90005 on 2013-03-25
[TABLE]
[TR]
[TD="class: votecell"]      

              [/TD]
              [TD="class: postcell"]               I need to check if I have updates for Ubuntu. I am using 12.10 version , but either keeps telling me to check my internet connection while my connection works just fine or telling me this : 


E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable) E: Unable to lock the administration directory (/var/lib/dpkg/) 

what should I do ?


[/TD]
[/TR]
[/TABLE]

---

### Post by araks on 2013-03-25
Here may be the solution for your question
[http://askubuntu.com/questions/15433/how-do-i-fix-a-could-not-get-lock-var-lib-dpkg-lock-problem](http://askubuntu.com/questions/15433/how-do-i-fix-a-could-not-get-lock-var-lib-dpkg-lock-problem)

---

### Post by El Tito on 2013-03-25
If you are typing your password correctly after:
```
sudo apt-get update
```
maybe some program is using that file simultaneously, impeding its use.
If this was the case, have you tried to update right after start up?

---

### Post by phoenix90005 on 2013-03-26
> **El Tito said:**
> If you are typing your password correctly after:
```
sudo apt-get update
```
maybe some program is using that file simultaneously, impeding its use.
If this was the case, have you tried to update right after start up?

I typed the PWD correctly, and yeah sometimes the first thing I do after start ups is checking for the Updates

---

### Post by ibjsb4 on 2013-03-26
Are you saying it updated?  You did not get the error message?

---

### Post by phoenix90005 on 2013-03-27
most of times just giving me these error messages ( you may say 90% of updating trials fails)

---

### Post by El Tito on 2013-03-27
You could try the lock part of this post
[http://ubuntuforums.org/showthread.php?t=1858466](http://ubuntuforums.org/showthread.php?t=1858466)

---

### Post by pfeiffep on 2013-03-27
You might find this [trouble shooting aid helpful]("https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure")

---


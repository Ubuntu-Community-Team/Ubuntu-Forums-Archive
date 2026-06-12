---
title: "Create a second root account"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by technosinner on 2008-10-15
So lets say I need a root account access, but I don't want to give root a password, can I create a second account with root-like privileges?

Thanks.

---

### Post by penguinpi.com on 2008-10-15
You have a few options here. But with Ubuntu I would just take advantage of sudo since it is already installed. After creating a new user edit /etc/sudoers 

under User privilege Section add

username    ALL=(ALL) ALL


you can also control exactly what the user can do here. So if you wanted them to have access to just a specific command you can do something like:

username ALL=/sbin/iptables , /sbin/kill     or whatever. Check sudo man pages (man sudo).


Hope this is what you were looking for!

---

### Post by overdrank on 2008-10-15
The forums policy on root accounts 
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by technosinner on 2008-10-16
> **overdrank said:**
> The forums policy on root accounts 
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

Oh my... I didn't realize I was breaking the rules :(

I wish not to circumvent the security model - I like the sudo method - but I believed that having a temporary user with root powers, and then deleting it would be more secure than activating root password.  I might very well be wrong, but in any case penguinpi.com pointed me towards an alternative that might be more secure (thanks!).

Getting to the level of knowledge I'm used to in Windows is a long and hard path...

---

### Post by Kellemora on 2008-10-16
Hi TS

I haven't tried it on Ubuntu yet, but some Distro's like CentOS (which is Red Hat Enterprise) lets you set up users, Administrators and Root and you can set times when Administrators have access to certain features.
In essence, they have Root access, but only to files they would need access too.  
An example is, allowing them to create a Directory within the Archive section to store todays accounting records.  Open time to do this is from like 5PM to 6PM then they are locked out of the Archives again.

I'm pretty certain things like this can be done in all Debian distro's as well.  I just haven't learned how to do much yet.  Just started a month and a half ago myself.

TTUL
Gary

---

### Post by technosinner on 2008-10-20
Hmmm that's interesting.  I'll have a look out to see if I can't find some info.  Thanks!!

---


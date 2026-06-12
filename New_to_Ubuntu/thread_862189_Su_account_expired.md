---
title: "Su account expired"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Paradoxfox93 on 2008-07-17
I really need to login to root for one quick second to make two really quick commands but I get this:

c@D:~$ sudo passwd root
[sudo] password for chakravanti: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
c@D:~$ su
Password: 
Your account has expired; please contact your system administrator
su: User account has expired
c@D:~$ sudo su
Your account has expired; please contact your system administrator
su: User account has expired
(Ignored)
root@D:/home/c# 


SO i guess I can log in with sudo su but wtf is this account expired stuff?  I've never run into this on ubuntu before.  I just upgraded to hardy from feisty.

---

### Post by snowpine on 2008-07-17
Hi there, you don't need to (and in fact, shouldn't) enter a root password, ever! Just preface whatever command needs superuser rights with 'sudo'.

Hope that helps.

---

### Post by Sef on 2008-07-17
Read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by snowpine on 2008-07-17
Also the original poster said "I just want to be root for a minute to execute a couple of quick commands," and that is pretty much the definition of what 'sudo' does. :)

---

### Post by liquidcable on 2008-09-03
snowpine, there are times when being root is the best/only choice.  Such as using the Cups web interface.

---

### Post by Shazaam on 2008-09-03
> **liquidcable said:**
> snowpine, there are times when being root is the best/only choice.  Such as using the Cups web interface.

I can run the cups web interface just fine without being root. Not required.

EDIT- sorry for the hijack.

---

### Post by liquidcable on 2008-09-04
Trying running the the cups web interface from a remote machine (not the machine with cups installed).

---

### Post by RgnKjnVA on 2008-09-17
To answer your question without condescending lectures on what you should and shouldn't do, once you've created a password for root then locked it (passwd -l root) you simply need to unlock it (passwd -u root). Be sure to put root back on lockdown when you're done.

For the peanut gallery, there ARE times when you need root. I found this thread because some tunneling software I'm trying to install from my office needs root to install the network connector and I was getting the same 'expired' message.

---

### Post by Riverside on 2008-11-02
> **RgnKjnVA said:**
> To answer your question without condescending lectures on what you should and shouldn't do, once you've created a password for root then locked it (passwd -l root) you simply need to unlock it (passwd -u root). Be sure to put root back on lockdown when you're done.

For the peanut gallery, there ARE times when you need root. I found this thread because some tunneling software I'm trying to install from my office needs root to install the network connector and I was getting the same 'expired' message.The cause of this is that the effect of running password -l has recently changed, from Hardy onwards.

From man passwd:

```
-l, --lock
           Lock the named account. This option disables an account by changing
           the password to a value which matches no possible encrypted value,
           and by setting the account expiry field to 1.
```
Why is this an issue?  Because due to "and by setting the account expiry field to 1" (a recent change), cron jobs owned by root (almost all system wide cron jobs are owned by root) can no longer run and return an error "account root has expired".

This will of course in all probability affect other processes on a system whose administrator has enabled root then subsequently disabled it using sudo passwd -l root also.

It may, I suspect, be responsible for a number of the issues which are apparently affecting Hardy and Intrepid users, some of whom are reporting odd issues and problems with their machines which appear otherwise unrepeatable and inexplicable.

Of course, usage of password -l is documented (at present incorrectly in respect of Ubuntu versions from Hardy onwards) in this often referred to Ubuntu document:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The password -l behaviour change is a known bug though, which apparently originated upstream in Debian:

[https://bugs.launchpad.net/ubuntu/hardy/+source/shadow/+bug/238755](https://bugs.launchpad.net/ubuntu/hardy/+source/shadow/+bug/238755)

---

### Post by bodhi.zazen on 2008-11-02
Thank you, yes this is (one) of the reasons we do not support setting a root password.

The other is that if you need to boot to recovery mode, you will then be asked for a root password. Although some may see that as a "security feature" I would point out. like a BIOS or grub password, it is easily defeated.

I agree there are (rare) times when it is necessary, in particularly the web administration applications.

In general please use :

```
sudo -i
``` to get a root shell.

---


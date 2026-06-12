---
title: "[SOLVED] Is it safe to rename my computer?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by garyed on 2008-08-21
I want to rename my computer name; " username@computer name "
I've been researching this a little & so far every one I've found whose renamed their computer has had to name it back because of problems.
Mostly having to do with not being able to become root using sudo anymore.
Is there a way to rename the computer where it will have absolutely no effect 
on the system?

---

### Post by iaculallad on 2008-08-21
> **garyed said:**
> I want to rename my computer name; " username@computer name "
I've been researching this a little & so far every one I've found whose renamed their computer has had to name it back because of problems.
Mostly having to do with not being able to become root using sudo anymore.
Is there a way to rename the computer where it will have absolutely no effect 
on the system?

On your terminal, Open/Edit the Network Settings:

```
gksudo network-admin
```

Select the General tab, and change the hostname.

There will be no side-effects if done the right-way.

---

### Post by yabbadabbadont on 2008-08-21
```
/home/daffy $ cat /etc/hostname 
yoiks
/home/daffy $ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       yoiks.and.away  yoiks

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
/home/daffy $ hostname -f
yoiks.and.away
/home/daffy $ dnsdomainname 
and.away

```
Just be sure to backup /etc/hostname and /etc/hosts before changing them.  Also be sure that you have a live CD/DVD from which you can mount your Ubuntu root partition so that you can undo your changes if problems occur.  Although, you should be able to use the recovery boot option to do the same in this case.

---

### Post by garyed on 2008-08-22
Thanks for the info.
I changed the name in both /etc/hostname & /etc/hosts  then rebooted
& everything works fine.
I tried to use sudo afterwards & it worked as usual so no problems there.
I was just nervous after reading about all those who change their computer name had couldn't use sudo any more & had to go back to their original name.

---

### Post by Oldsoldier2003 on 2008-08-22
> **garyed said:**
> Thanks for the info.
**I was just nervous after reading about all those who change their computer name had couldn't use sudo any more & had to go back to their original name**.

Usually that is caused by attempting to have a suffix on the computername

like [email]bob@bob.com[/email]:~$

---

### Post by lswest on 2008-08-22
I also know of a few cases where it was because users forgot to make the same change in the hostname file, which led to a conflict, but other than that I tend to agree with what was said above.  If done right, it will work (nicely).

---


---
title: "Drop To Root Shell Prompt not asking for password"
date: 2011-08-17
forum: Recurring Discussions
---

### Post by beew on 2011-08-17
Hi,

Just logged into recovery mode to fix something, I picked "drop to root shell prompt with network" and completed the task rather easily. But it occurs to me that I was never asked for my password. I don't think this is the way it should be, I probably forgot to set something when I installed the system. Please advise. Thanks.

---

### Post by LowSky on 2011-08-17
you are in root shell. Ubuntu doesn't set root up by default so it has no password. Your first user account is a sudo powered account so it makes up for the lack of root.

in other words: don't worry it is normal.

---

### Post by Paqman on 2011-08-17
> **beew said:**
> I don't think this is the way it should be

Nope, that's how it's supposed to work. Bear in mind that anybody with physical access to your machine can do likewise.

---

### Post by beew on 2011-08-17
Thanks for the reply. But if anyone can boot into root shell and perform administrative tasks without password wouldn't that be a security loophole?

---

### Post by pqwoerituytrueiwoq on 2011-08-17
google grub password
also check for a power on password in your bios
also a root password is not set sine that enables root login via gui

---

### Post by bodhi.zazen on 2011-08-17
> **beew said:**
> Thanks for the reply. But if anyone can boot into root shell and perform administrative tasks without password wouldn't that be a security loophole?

This has been discussed many many times, thus I moved your thread.

[https://wiki.ubuntu.com/SecurityTeam/FAQ#Rescue_Mode](https://wiki.ubuntu.com/SecurityTeam/FAQ#Rescue_Mode)

> **pqwoerituytrueiwoq said:**
> google grub password
also check for a power on password in your bios

Physical access is root access, setting a password on your bios or grub adds very little security, but you can do that if it makes you feel better.

A better solution is to encrypt the installation with LUKS.

---

### Post by jwbrase on 2011-08-17
> **beew said:**
> Thanks for the reply. But if anyone can boot into root shell and perform administrative tasks without password wouldn't that be a security loophole?

It is somewhat, but as has been said, a bigger security breach has already happened if an untrusted person gains physical access to your machine. Password protecting physical access will stop an ignorant or casual attacker, but won't do more than slow down someone who really wants to break in (and anyone who really wants to break in will steal the machine so that they have all the time they need without you interrupting). The ignorant or casual attacker (For example, a curious 5-year-old or an overly nosy guest who starts messing with your computer while you're in another part of the house) is unlikely to try rebooting to get into recovery mode. The determined attacker won't be stopped by finding that you've password protected your root account.

---

### Post by Paqman on 2011-08-17
> **beew said:**
> Thanks for the reply. But if anyone can boot into root shell and perform administrative tasks without password wouldn't that be a security loophole?

Not particularly. Anybody with physical access to your machine can circumvent most kinds of security. As bodhi.zazen says: "Physical access _is_ root".

---

### Post by Thewhistlingwind on 2011-08-17
> **bodhi.zazen said:**
> this has been discussed many many times, thus i moved your thread.

[https://wiki.ubuntu.com/securityteam/faq#rescue_mode](https://wiki.ubuntu.com/securityteam/faq#rescue_mode)



physical access is root access, setting a password on your bios or grub adds very little security, but you can do that if it makes you feel better.

A better solution is to encrypt the installation with luks.

+1

---

### Post by pi.boy.travis on 2011-08-17
> **bodhi.zazen said:**
> Physical access is root access,

This should be a poster. Or a t-shirt.

---

### Post by beew on 2011-08-18
Thanks for all the replies. I was puzzled because according to the Ubuntu Wiki it will ask for the password. See point 8

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

But the explanations make sense.

---

### Post by beew on 2011-08-18
> **bodhi.zazen said:**
> This has been discussed many many times, thus I moved your thread.




Well I was not really discussing the philosophical issue of  whether it should or shouldn't ask for password. I was asking the technical question of whether I should expect a prompt for password or not if I have set things up correctly so it shouldn't be in the recurring section.

But anyway the issue is solved. Thanks to everyone who has replied.

---

### Post by aysiu on 2011-08-20
> **beew said:**
> Thanks for all the replies. I was puzzled because according to the Ubuntu Wiki it will ask for the password. See point 8

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

But the explanations make sense.
Yes, that's incorrect. I don't know who wrote that. It's never prompted for a password unless you set a root password, and the root account is disabled for login in Ubuntu by default and always has been.

---

### Post by cariboo on 2011-08-20
If you have a launchpad account, you can log in and change the content of most Ubuntu wiki pages.

I would encourage anyone that finds an error to login and fix it, instead of not doing anything about it.

---


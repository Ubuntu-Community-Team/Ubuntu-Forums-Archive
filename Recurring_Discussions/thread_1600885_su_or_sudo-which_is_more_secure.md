---
title: "su or sudo-which is more secure?"
date: 2010-10-19
forum: Recurring Discussions
---

### Post by dogdo on 2010-10-19
Read this article [http://blogs.techrepublic.com.com/security/?p=4619&tag=nl.e036](http://blogs.techrepublic.com.com/security/?p=4619&tag=nl.e036)

According to this sudo is not as secure as su-are they wrong?

---

### Post by OpSecShellshock on 2010-10-19
The argument being advanced in the article has less to do with more/less secure than it has to do with more/less useful to administrators of enterprise environments (which is what Tech Republic is more geared to). I notice that the article leaves out the possibility of "sudo -i" entirely, so maybe they just aren't aware that you can use that to get a root shell. In the end, I'm not really sure how having the root account disabled could make a system *less* secure.

They seem to be saying that allowing certain users to elevate on the fly rather than switching to root is somehow bad because it reduces the number of passwords that have to be compromised (or something??) in order for an attacker to get privileged access. However, by the time that's happened, so many other things have already either gone wrong or been implemented improperly that selecting one or the other approach would cease to make a difference. For example, why would remote access be achieved through passwords rather than keys? And in the case of physical access, attackers wouldn't even need to compromise any account in the first place.

Provocative articles that spawn pages of arguments are sure good for advertisers, though.

---

### Post by WinstonChurchill on 2010-10-19
Whoever wrote that article clearly doesn't understand the way Ubuntu implements 'sudo': the default configuration is that any member of the 'admin' group can enter his/her user password and execute commands with root privileges, which is very nearly identical to the way a standard Unix su/wheel implementation would work - the only exception being that generally with 'su' you would enter the root user's password, and with sudo you enter YOUR user password. While there is some validity to his SSH argument, if your password is secure, you don't have to worry about it; plus, sudo allows you to change it's behaviour to accept the root password instead of your password if you really want it to. And if you're security-minded at all, you'll be using public key authentication exclusively anyway...

Sudo also allows a system administrator a much greater control over the system - instead of everybody knowing the root password who needs to help administer the system, they all just use their own passwords, and by editing the 'sudoers' file, the sysadmin can specify exactly what each individual user (or groups of users) can and cannot execute as root. And, as an added bonus, sudo logs everything a user does, while 'su' simply logs a "so-and-so became root" message.

If you have a lot of work to do as root, you can get a root shell (just like su) very easily with sudo:
```
sudo -i
```sudo and su are equivalent - the only difference is that sudo is much more flexible.

---

### Post by bodhi.zazen on 2010-10-20
*Thread moved to **Recurring Discussions**.*

This discussion goes round and round.

su and sudo are of equally secure / insecure. They have the same vulnerabilities and faults.

If an administrative account is compromised (one with su or sudo access) then root access is close behind via any number of methods some crude and some sophistocated (root kits are on the sophistocated end of the spectrum).

At the end of the day, these are both tools. Best understand how they work and select the best tool for the job.

Personally I stay with the defaults, when I run Ubuntu, sudo, with Fedora su. You get to choose when you install Debian.

Better to read about these tools then debate them.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---


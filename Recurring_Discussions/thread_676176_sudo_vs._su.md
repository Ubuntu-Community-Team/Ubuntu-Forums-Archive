---
title: "sudo vs. su"
date: 2008-01-23
forum: Recurring Discussions
---

### Post by lespaul_rentals on 2008-01-23
Do you think the root account should be enabled?  I know that by default Ubuntu disables it, but I have been doing some thinking and to be honest I think there is an advantage to having it enabled.

I have an SSH server, and obviously I've configured it to not allow root login.  Thus, my username is the only one that is valid.  If a cracker were to try and bruteforce my username and got the password, he also has the password to gain superuser rights because they are one and the same.

However, if you look at a distro like openSUSE (and many others, I've noticed that RPM distros do this a lot), they allow and encourage you to set a different password for the root account.  Therefore, a properly configured SSH server such as mine, where "root" is not a valid login name, would be harder to break into.  Once they cracked my main username, they would have to run a server-side bruteforce to try and crack the completely different root password.

Once again, I know there are ways to change this, but it could make for an interesting discussion.  There advantages and disadvantages to both ways.

---

### Post by p_quarles on 2008-01-23
Disabling root login on SSHD isn't much of a security measure, imho. You might try disabling password based logins, using denyhosts, or throttling incoming new connections. 

Honestly, I've used both su and sudo, and the only difference I see is one password vs. two.

---

### Post by Namtabmai on 2008-01-23
I think once someone has got access to your machine, getting root access one way or another is only a minor step, basically if your machine is that easy to brute force you have big problems either way.

Personally I prefer not having a root account enabled (or at least a having a known password set) by default, I sudo when I need to do something quickly as root, or sudo su if I want to switch to root for a long period. I've never seen any reason to log straight in as root, either via the gui or command line.

I've also never seen a reason to allow remote root logins, and if this was the case I'd probably take further steps by segregating the machine physical and also isolating it's access from the outside network.

---

### Post by Xbehave on 2008-01-23
If you setup sudoers correctly it will require both your password and your root password to get root.

i think sudo can easily emulate any function of su, and encourages safety, although in the hands of somebody who knows what theyre doing both are fine!

---

### Post by aysiu on 2008-01-23
Why would it be easier for someone to brute force your username and password than root's username and password? They already know **A)** what the root username and **B)** what privileges the root username has. All they would need to brute force at that point would be the password.

---

### Post by SunnyRabbiera on 2008-01-23
I have used both sudo and root based systems and find both to have their advantages and disadvantages.
The advantage of a sudo system is that you dont have to have two separate passwords for administration, but this also means that by default the first user of the system is technically the root user and you would need to change the password more often if you are a security maniac.
My biggest argument against sudo is that it behaves too much like a Microsoft system, acting like every user can just download something without monitoring, while this is good for a ease of use standpoint its bad from a security standpoint.
the advantage of a root based system is that the root user and the first user of the system are separate, that you have the master password and the user passwords separate.... the administrator is the administrator and the user is the user.
From a ease of use standpoint this does not sound that good as it means more passwords to remember... but for me in this matter I prefer root systems.
However if you have a real newb at work who has no idea what he or she is doing they could mess up a root based system too.

---

### Post by saulgoode on 2008-01-23
> **aysiu said:**
> Why would it be easier for someone to brute force your username and password than root's username and password? 

If you disable root logins on SSH then an external intruder can not brute force root's password. In this case, there is no advantage to SUDO over SU. Also, given that most systems do disable root logins from outside, it is becoming increasingly common for hackers to brute force *usernames* given a set of typical passwords.

If the attacker has access to the machine, but no account, then he could theoretically brute force root's password; but this would have to be performed manually from the keyboard. Assuming even a weak 8-character password, the relatively weak MD5 encryption scheme, and typing a password every five seconds, it would take about 8,000 years to try all combinations. NOTE: this is the **only** situation for which a SUDO-only system provides any security advantage; all other cases provide either equal or less security. 

If the attacker has an account on the machine, a simple examination of /etc/group reveals the administrative accounts and negates any advantage that SUDO may hold regarding root's anonymity.

One advantage of a separate root account is that the admin user only needs to log in when it is necessary to perform administration. If no administration needs performing, he doesn't log in and there is no opportunity for his password to be discovered (by scripting, mechanical interception, or by physical observation). An Ubuntu user who would typically log into his admin account for normal usage provides more opportunities for the password entry to be intercepted and less time between admin logins to discover suspicious activities. A corollary to this advantage of fewer logins is that a more secure password can be chosen for the root account without having an adverse effect on ease of use for unprivileged users. 

Of course an Ubuntu user *could* limit usage of his admin account (and choose a strong password for it), but evidence indicates this to be a rather rare occurrence -- and if such security measures are employed then all of the usability benefits of Ubuntu's SUDO-only methodology are completely negated.

Probably the most critical aspect of Ubuntu's disabling the root account is that the account isn't really disabled; all that is disabled is password-based root logins. IF your machine is ever compromised, the intruder would be able to provide himself with password-less root access and make it extremely difficult (theoretically impossible) for administrators to discover his presence. Far more damaging than having someone gain administrator privileges and trashing your data would be having someone maintaining access and control of your installation for months on end without your being aware of it.

---

### Post by aysiu on 2008-01-23
> **SunnyRabbiera said:**
> I have used both sudo and root based systems and find both to have their advantages and disadvantages.
The advantage of a sudo system is that you dont have to have two separate passwords for administration, but this also means that by default the first user of the system is technically the root user and you would need to change the password more often if you are a security maniac.
My biggest argument against sudo is that it behaves too much like a Microsoft system, acting like every user can just download something without monitoring, while this is good for a ease of use standpoint its bad from a security standpoint.
the advantage of a root based system is that the root user and the first user of the system are separate, that you have the master password and the user passwords separate.... the administrator is the administrator and the user is the user.
From a ease of use standpoint this does not sound that good as it means more passwords to remember... but for me in this matter I prefer root systems.
However if you have a real newb at work who has no idea what he or she is doing they could mess up a root based system too.
I disagree completely.

A user with *sudo* powers is not "technically the root user" any more than a limited user is who knows the root password. *admin* users, unless they are *sudo*ing a particular command, have limited privileges and can't modify much outside their home folders.

And, no, it doesn't act as if any user can do stuff without monitoring. As a matter of fact, *sudo* has much better security auditing than root does, and not all users have to have *sudo* access--only *admin* users.

If you have users know the root password to get root access, it also means that if you ever want to demote those users, you have to change the root password, and notify all users who know the root password of the change. Kind of annoying. If you use the *sudo* model, all you have to do is take the demoted user out of the *admin* group.

---

### Post by -grubby on 2008-01-23
Well I think if you need to do some root terminal work very quick sudo is best. But if you are going to do a lot of root terminal work it becomes annoying to type "sudo" in front of every command. So I vote "other" even though there isn't that option

---

### Post by aysiu on 2008-01-23
> **nathangrubb said:**
> Well I think if you need to do some root terminal work very quick sudo is best. But if you are going to do a lot of root terminal work it becomes annoying to type "sudo" in front of every command. So I vote "other" even though there isn't that option
If you need to do a lot of root terminal work, just type ```
sudo -i
```

---

### Post by SunnyRabbiera on 2008-01-23
> **aysiu said:**
> I disagree completely.

A user with *sudo* powers is not "technically the root user" any more than a limited user is who knows the root password. *admin* users, unless they are *sudo*ing a particular command, have limited privileges and can't modify much outside their home folders.

And, no, it doesn't act as if any user can do stuff without monitoring. As a matter of fact, *sudo* has much better security auditing than root does, and not all users have to have *sudo* access--only *admin* users.

If you have users know the root password to get root access, it also means that if you ever want to demote those users, you have to change the root password, and notify all users who know the root password of the change. Kind of annoying. If you use the *sudo* model, all you have to do is take the demoted user out of the *admin* group.

well in either case both work better in the long run then how windows manages things.
But I do sort of like how OSX works, it takes the sudo approach but its not that easy to mess up a apple system.
OSX walks the fine line of security and ease of use, something both linux and windows can learn from.

---

### Post by aysiu on 2008-01-23
> **SunnyRabbiera said:**
> well in either case both work better in the long run then how windows manages things.
But I do sort of like how OSX works, it takes the sudo approach but its not that easy to mess up a apple system.
OSX walks the fine line of security and ease of use, something both linux and windows can learn from.
I don't know why Ubuntu's *sudo* is so fragile, but I agree. Apple made a good choice in using *sudo* but somehow made it harder to break.

---

### Post by SunnyRabbiera on 2008-01-23
> **aysiu said:**
> I don't know why Ubuntu's *sudo* is so fragile, but I agree. Apple made a good choice in using *sudo* but somehow made it harder to break.

well ubuntus sudo is fine, its what people do with it that can make it breakable...
but the same can be said about root in the long run.
But then again I am liking what Mandriva is doing now, it uses a semi sudo like system in keeping the system up to date but you need to be administrator to install things

---

### Post by mringer on 2008-01-27
The document on rootsudo says:

Anything you need to do as administrator of an Ubuntu system can be done via sudo or gksudo. 

I dont believe this. Examples: these all assume I have an admin user called admin 

1. Boot in recovery mode: admin's password is rejected

2. umount /home  Fails with "device is busy". I am advised that this is because the system has 1 or more files open in /home/admin

3. This example may be bad. Some months ago I tried to udate from
XUB 6 to 7 . The local Unix experts told me that the error messages meant that only root could do this upgrade. I had to burn a CD.
Unfortunately I cannot now recall exactly what command I gave, but
I am sure that after 1 failure I would have taken care to retry with exactly what the document on updating said.

1 and 2 are recent, 3 might have been fixed in the meantime.

---

### Post by Xbehave on 2008-01-27
mringer thats completly of topic for all intense and purposed sudo and su are the same, its just a different way of acheiving security.

> But I do sort of like how OSX works, it takes the sudo approach but its not that easy to mess up a apple system.
with root access it should be easy to mess up a system!

with sudo you can have 2 passwords to get root, so unless this is possible with su, a properly configured sudo is more secure. While long passwords do offer good protection, cant a server be configured to block an IP for a set of time if they get 3 wrong passwords making brute forcing incredibly slow anyway!

---


---
title: "sudo privilege escalation flaw?"
date: 2009-01-26
forum: Recurring Discussions
---

### Post by newkirk on 2009-01-26
Is this just me, or is there a problem here?

I log into a ubuntu server as sudo-permitted user 'alfred'.  I try "touch /root/test" and it gives the expected permissions error.  I "sudo touch /root/test" and it prompts for password, and after correct password is entered it touches the specified file as user root, again as expected.

Then I log out of the ubuntu server, and log into it as user 'alfred' again, but from a different machine and source IP.  As long as I have the same TTY, it seems, I still have root privileges WITHOUT PROMPT.  I can "sudo touch /root/test" or anything else and it happily grants me root privs.

Now in the most common scenario, login and sudo are achieved with the same typed password, but that's not always the case.  And there's a reason that " ALL=NOPASSWD: ALL" is NOT the default setting in /etc/sudoers...

j

---

### Post by bodhi.zazen on 2009-01-26
this is configured with the timestamp / time out variable.

If you do not like this behavior change it. Take care when configuring sudo, especially on remote machines.

> **timestamp_timeout** 
Number of minutes that can elapse before **sudo** will ask for a passwd again. The default is 5. Set this to 0 to always prompt for a password. If set to a value less than 0 the user's timestamp will never expire. This can be used to allow users to create or delete their own timestamps via sudo -v and sudo -k respectively.
 
[http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)


The alternate is to run sudo -k before you log out.

---

### Post by pdtpatrick on 2009-01-26
huh? anyway if you are using the same terminal, when you use sudo, it retains that authorized session for a bit. so lets say you ran sudo apt-get install something and then afterwards you tried sudo -s -H. It will only ask you for your password the first time you ran sudo. However, if you wait sometime and tried to run sudo again then it will prompt you for your password.

---

### Post by e1mer on 2009-01-26
I am still learning, but I read that there is a hosts
part of the specification in the sudoers file
that currently says "(ALL)" which could be
changed to allow only from certain hosts.

Otherwise it means that you have elevated your
rights until the timeout.

---

### Post by newkirk on 2009-01-26
> **pdtpatrick said:**
> huh? anyway if you are using the same terminal, when you use sudo, it retains that authorized session for a bit. so lets say you ran sudo apt-get install something and then afterwards you tried sudo -s -H. It will only ask you for your password the first time you ran sudo. However, if you wait sometime and tried to run sudo again then it will prompt you for your password.
Yes, I was aware of that.  What I wasn't aware of, and questioned the wisdom of, is that it lets one person run 'sudo apt-get install something' then a minute later a different remote user logged in with the same username and TTY can run 'sudo -s -H' without password challenge.  Distinctly NOT the "same terminal" in most senses of the phrase.

I'm just suggesting that it makes no sense that the temporary privileges (until the timeout expires, granted) can apply to a different, subsequent, login session from a different source IP.  It seems that should be restricted to the PID of the shell as well as the userid and TTY, instead of just the latter two.

As bodhi.zazen suggests, I'll be utilizing sudo -k in the future...

j

---

### Post by pdtpatrick on 2009-01-26
I guess i didnt make myself clear .. that only works (as far as i know) for the same user. 

lets say im jdoe and im part of the sudoers group. I need to update something on my laptop. so i type sudo apt-get install something or sudo apt-get -y update

and then i realize afterwards that there a several things i will need to install, so i decide to just become root (sudo -s -H).. since i had already ran sudo apt-get install something, it still has the authenticated session open, so once I (the same user, using the same terminal) types sudo -s -H, it will automatically make me root without asking for the password because i just recently authenticated.

I dont know what the time limit is or yours is set to but it stops working after some time and you will have to reauthenticate. 

Hopefully this clears up what i was trying to say. I wasn't saying that once he put his password in, another totally new user can use that same terminal and get root access from the previous user's session.

---

### Post by newkirk on 2009-01-26
> **pdtpatrick said:**
> I guess i didnt make myself clear .. that only works (as far as i know) for the same user. 

lets say im jdoe and im part of the sudoers group. I need to update something on my laptop. so i type sudo apt-get install something or sudo apt-get -y update

and then i realize afterwards that there a several things i will need to install, so i decide to just become root (sudo -s -H).. since i had already ran sudo apt-get install something, it still has the authenticated session open, so once I (the same user, using the same terminal) types sudo -s -H, it will automatically make me root without asking for the password because i just recently authenticated.

I dont know what the time limit is or yours is set to but it stops working after some time and you will have to reauthenticate. 

Hopefully this clears up what i was trying to say. I wasn't saying that once he put his password in, another totally new user can use that same terminal and get root access from the previous user's session.

But that is exactly what I'm seeing, though I presume you're referring to "userid" where I'm referring to physical users.  The privilege escalation sans password applies to a DIFFERENT session if it has the same uid and TTY.  Let me outline a scenario.

As admin of a particular server I SSH to it as user 'abe', the only ordinary user account on the box, using a key to authenticate.  I'm in as TTY pts/2.  I 'sudo' something, then subsequently log out.

One of our techs comes along behind me and logs into that same server via SSH from a different source IP, different workstation, also using user 'abe' and a keyfile for authentication - and ends up with TTY pts/2 from which I recently logged out.  The tech can now utilize sudo even though he does NOT know the password, as long as he's there with the same username and TTY, within 5mins of when I entered the password. (which only I know)

I realize there are a dozen ways (at least) to avoid this circumstance, and I'm not claiming it's a critical security flaw, but nevertheless I believe it IS a flaw if any transient security changes (IE, sudo without re-entering password) persist across different sessions.

j

---

### Post by cdenley on 2009-01-27
I agree. If an attacker gains shell access as your admin user, he can wait for you to use sudo, then re-use your sudo timestamp (valid for 15 minutes by default) to gain root. If he compromised your admin account by somehow discovering your password, he already has root, but there are other ways to compromise an account without a password.

Edit bodhizazen: This post was reviewed by the staff and it was felt that the script was inappropriate for these forums. We realize this is a security discussion and that there was no malicious intent.

---

### Post by newkirk on 2009-01-29
Given the script that was posted and purged, it seems this is in fact exploitable.

So what should be done now?

j

---

### Post by SeanHodges on 2009-01-29
> **newkirk said:**
> Given the script that was posted and purged, it seems this is in fact exploitable.

So what should be done now?

j

As bodhi.zazen explained, you can disable the timestamp behaviour in sudo if you want. I suggest you do this if you sometimes hand out your user account to others.

See this related thread: [http://ubuntuforums.org/showthread.php?t=1045209](http://ubuntuforums.org/showthread.php?t=1045209)

---

### Post by newkirk on 2009-01-29
Thanks for the related thread, somehow I'd missed it when searching, before I started this thread.

I've already altered setup on all the boxes I administer, the question was more one of whether ubuntu, or debian, or sudo, or who should close this hole - by default this appears exploitable on any ubuntu box, for example.  Desktop systems in particular would seem vulnerable to this - IE the system could be rootkitted this way if a browser exploit provided access as a sudoer.  Not saying it's the easiest or only way, just that if a hole exists it seems it ought to be plugged by default, not left open.

j

---

### Post by SeanHodges on 2009-01-30
> **newkirk said:**
> the question was more one of whether ubuntu, or debian, or sudo, or who should close this hole - by default this appears exploitable on any ubuntu box, for example.  Desktop systems in particular would seem vulnerable to this - IE the system could be rootkitted this way if a browser exploit provided access as a sudoer.  Not saying it's the easiest or only way, just that if a hole exists it seems it ought to be plugged by default, not left open.

j

I think you'll need someone qualified in system security to answer these kind of questions for you.

Check the [security-announce]("http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce") list archive to ensure the vulnerability has not already been reported. If it is a new vulnerability, you may want to contact the [devel-discuss]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss") list to find out the procedure for obtaining a CAN identifier and logging the vulnerability officially. I believe Ubuntu use Debian's security CVE tracking, but I'm not sure on the details.

If someone can point to a HOWTO on vulnerability reporting, I'd be interested how the actual process works...

---

### Post by cdenley on 2009-01-30
[[IMG]http://brainstorm.ubuntu.com/idea/17754/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/17754/)

---

### Post by kpatz on 2009-01-30
If you don't want your sudo authentication to persist after logging out, just add **sudo -k** to your .bash_logout script.  Easy as pie. :)

---

### Post by cdenley on 2009-01-30
> **kpatz said:**
> If you don't want your sudo authentication to persist after logging out, just add **sudo -k** to your .bash_logout script.  Easy as pie. :)

Doesn't really help much, since you're going to be logged in immediately after running sudo, and the attacker will already have root before you get a chance to log out.

---

### Post by kpatz on 2009-01-30
> **cdenley said:**
> Doesn't really help much, since you're going to be logged in immediately after running sudo, and the attacker will already have root before you get a chance to log out.The flaw manifests itself on a subsequent login by the same user on the same pty.  If you're still logged in, the attacker will get a different pty, and the sudo will ask for the password even before the timeout runs out.

But, running sudo -k on logout will clear the timeout, so the next person logging in with the same user/pty will get the password prompt on sudo.

---

### Post by cdenley on 2009-01-30
> **kpatz said:**
> The flaw manifests itself on a subsequent login by the same user on the same pty.  If you're still logged in, the attacker will get a different pty, and the sudo will ask for the password even before the timeout runs out.

But, running sudo -k on logout will clear the timeout, so the next person logging in with the same user/pty will get the password prompt on sudo.

I tested this:
[LIST=1]
[*]added "/usr/bin/sudo -k" to .bash_logout
[*]started a new shell
[*]used sudo
[*]killed the shell
[*]started a new shell
[*]used sudo
[/LIST]
The timestamp was still valid. It was not killed by the .bash_logout script. I think the script is only run when the shell started by login exits.

I think if you're **not** using a GUI, your solution will work. However, most users use a GUI.

---

### Post by The Cog on 2009-01-30
It is only an issue if you are sharing one username between multiple users. And even then, it's only really an issue if sudo has also been modified so that it requires a password other than their login password. I would suggest that as part of modifying sudo, the administrator should also disable the sudo timer. The effect on the users convenience is small. I normally use **sudo -i** anyway, so I wouldn't notice any extra inconvenience with the timer disabled.

The issue is really one of the admin having modified the sudo configuration without having understood all the implications of his actions. I had noticed myself a while ago that the sudo timer was still active if I disconnected and logged back in quickly. Of itself I don't think that is a big deal. Like I say, it might become one if you unwittingly make it one when changing away from the default setup.

---

### Post by koenn on 2009-01-30
> **The Cog said:**
> It is only an issue if you are sharing one username between multiple users. And even then, it's only really an issue if sudo has also been modified so that it requires a password other than their login password. 

my thoughts exactly.
in a default ubuntu config where account password = sudo password (for users in admin group) and with the normal practise of 1 user account = 1 person, this problem doesn't exist. 

> **newkirk said:**
> I
Now in the most common scenario, login and sudo are achieved with the same typed password, but that's not always the case. It is in Ubuntu, so if you've modified that, The Cog is right in that you have created this so-called escalation flaw yourself.

> **newkirk said:**
> Is this just me, or is there a problem here?
it's just you.

---

### Post by cdenley on 2009-01-30
There are ways to compromise a user without knowing their password, such as a web browser exploit. Just because they can execute code as your admin user doesn't mean they have your password or root. I guess your suggestion is that privilege escalation from admin to root isn't possible since the two are basically the same, but the user privilege separation exists for a reason.

---

### Post by koenn on 2009-01-30
> **cdenley said:**
> There are ways to compromise a user without knowing their password, such as a web browser exploit. Just because they can execute code as your admin user doesn't mean they have your password or root. I guess your suggestion is that privilege escalation from admin to root isn't possible since the two are basically the same, but the user privilege separation exists for a reason.
This is arguably an entirely different scenario than what the OP is about, but, basically, an admin user account  already has the right to escalate its privileges to root, by design, so how can the fact that this account can escalate be considered a flaw ? 
The flaw is in the (lack of) user account management and the (mis-)use of passwordless ssh to be able to keep the admin password secret, i.e. in the solution designed and implemented by the admin/OP :  The sudo timeout creates an unforeseen and undesired side-effect, that should be remedied by the admin, as part of his solution. I don't consider that a flaw in sudo or in the way ubuntu sets up the sudo mechanism. 

If I understand your browser exploit example correctly, that would be a problem for any sudoer, not just in the scenarios the OP describes. Then again, isn't FF sandboxed ?

---

### Post by cdenley on 2009-01-30
> **koenn said:**
> This is arguably an entirely different scenario than what the OP is about, but, basically, an admin user account  already has the right to escalate its privileges to root, by design, so how can the fact that this account can escalate be considered a flaw ? 
The flaw is in the (lack of) user account management and the (mis-)use of passwordless ssh to be able to keep the admin password secret, i.e. in the solution designed and implemented by the admin/OP :  The sudo timeout creates an unforeseen and undesired side-effect, that should be remedied by the admin, as part of his solution. I don't consider that a flaw in sudo or in the way ubuntu sets up the sudo mechanism. 

If I understand your browser exploit example correctly, that would be a problem for any sudoer, not just in the scenarios the OP describes. Then again, isn't FF sandboxed ?

Now that I re-read the original post, he had a different issue, although they are sort of related. If sudo were to check the shell's process information running sudo in addition to the TTY, then it would fix both of our issues.

I already demonstrated how this can be a flaw, but my code was removed. Basically, an attacker manages to run their code as the admin user. Their code waits for the user to run sudo, waits 10 seconds for that user to enter their password, kills the shell the user ran sudo with, create new shells until you get the same TTY the user had, then the attackers code can run any command with sudo without knowing the password.

It would be a problem for any sudoer who uses sudo while the attacker's code is executing as that user. It doesn't appear there is an apparmor profile for firefox, but if it is sandboxed in another way, then I guess that would be a bad example. If you want examples for how attackers may manage to execute arbitrary code, check [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn).

---

### Post by koenn on 2009-01-30
> **cdenley said:**
> Now that I re-read the original post, he had a different issue, although they are sort of related. If sudo were to check the shell's process information running sudo in addition to the TTY, then it would fix both of our issues.

I already demonstrated how this can be a flaw, but my code was removed. Basically, an attacker manages to run their code as the admin user. Their code waits for the user to run sudo, waits 10 seconds for that user to enter their password, kills the shell the user ran sudo with, create new shells until you get the same TTY the user had, then the attackers code can run any command with sudo without knowing the password.

It would be a problem for any sudoer who uses sudo while the attacker's code is executing as that user. It doesn't appear there is an apparmor profile for firefox, but if it is sandboxed in another way, then I guess that would be a bad example. If you want examples for how attackers may manage to execute arbitrary code, check [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn).

the exploit you describe depends on arbitrary code execution in the context of the admin user, so what you are really trying to do is protect sudo from security flaws in any other program. While a few extra checks like the ones you describe in your brainstorm idea probably wouldn't hurt, we're essentially talking about flaws in other programs than sudo. Although, granted, privilege escalation would be the next step, and in this case escalation may be facilitated by ubuntu's sudo timeout.

I had a quick look through [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn) but didn't see much that would allow 'arbitrary code execution' exploits, and even then only of the 'if a user were tricked into [doing this or that], the attacker could run code ..." kind.

All in all, I don't think this is the huge security flaw some people make it out to be.


re browsers, what I meant was that FF sandboxes javascript so that code has no access to the system (and therefore can't invoke a shell or execute local programs or scripts)

---

### Post by cdenley on 2009-01-30
It's not a big security hole, and protecting yourself from attackers who already have local access is an uphill battle, but I think it's a valid security concern, and the default /etc/sudoers needs to be changed. I suppose some people would complain if they had to type in their password every time they use sudo, but there is probably just as many people now who get alarmed and confused when their password isn't required.

Of course it wouldn't be a concern unless the attacker gained local access, but that is true of all privilege escalation vulnerabilities. I guess the difference is most privilege escalation vulnerabilities don't require the attacker to have access to an admin account.

---

### Post by newkirk on 2009-01-30
> **cdenley said:**
> It's not a big security hole, and protecting yourself from attackers who already have local access is an uphill battle, but I think it's a valid security concern, and the default /etc/sudoers needs to be changed. I suppose some people would complain if they had to type in their password every time they use sudo, but there is probably just as many people now who get alarmed and confused when their password isn't required.

Of course it wouldn't be a concern unless the attacker gained local access, but that is true of all privilege escalation vulnerabilities. I guess the difference is most privilege escalation vulnerabilities don't require the attacker to have access to an admin account.

Agreed it's not 'big', and that it can be circumvented.  My original post presented a scenario based on how I first noticed it - sudo, provide password, logout ssh, login ssh, sudo still password-free - not the likely way this would be exploited if it were, just the circumstance in which I'd observed it.  I agree that the multiple-users-as-one-username scenario is (or should be in the name of security) uncommon and generally a bad idea.

My comments regarding a browser exploit weren't specifically about firefox or any browser, but just pointing out that on a default desktop installation where the 'everyday' account is probably an administrator, anything that could be used to achieve malicious access as that user could subsequently be used to gain root this way.

I wondered if a solution mightn't be to tie the timestamp to the PID as well as user and TTY, but that just makes it (far) less likely, doesn't close it. (and represents significant coding effort IMHO)  Unfortunately, as you pointed out, if the intruder kills the sudo-invoking shell, it never processes .logout so sudo -k there is just convenience, not security.  So I'm thinking that either disabling timestamps by default OR significant efforts recoding sudo's timestamp handling are the only options that effectively close this hole.

The irritation of needing to key in the password every time I invoke 'sudo' is a pretty easy sacrifice to make in the name of improved security, and now that I know how to close it (and that it's there!) I'll always do so. I'm just concerned if it's left exposed by default solely in the name of convenience.

j

---


---
title: "Set up a new user, now can't log in as root"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by jps2012 on 2012-04-25
I'm getting an "authentication error" message after setting up a new user. I'd appreciate help figure out what went wrong, and how to fix it. 

I used the following command to create a new account: 

"sudo useradd -d joelbackup"

I then used the following command to ATTEMPT to set the password for the new account (which is for me, not another user; I was creating it as a backup in case I screwed up profiles on my regular account). 

I used: 

"usermod -p THEPASSWORD" 

The password is the same as I use to login as root. 

Arrrgh! I have no idea what went wrong. I was following the instructions for "add new user" on this site:  [http://www.computerhope.com/unix/useradd.htm](http://www.computerhope.com/unix/useradd.htm)

Thanks! (not **you**, computerhope, you--**experts**)

---

### Post by jps2012 on 2012-04-25
Whew! I think I'm OK. I got a confusing (to me, a noob) response from Terminal, and panicked. 

If anyone can explain why I would get the following message, saying there was an authentification failure, and THEN, when I executed "sudo su" I would be allowed to assume root privileges WITHOUT BEING ASKED FOR A PASSWORD, I'd love to hear it. 

Here's the script (the commands I executed, followed by responses; for other noobs, the "#" indicates I was switched to my root account) from bash: 

joel@JPS:~$ su
Password: 
su: Authentication failure
joel@JPS:~$ sudo su
root@JPS:/home/joel#

---

### Post by houseworkshy on 2012-04-25
Perhaps setting the same password for two differant users, even if they are you, could be the problem.  Sudo has a timer, the default is 15 minets; so after  a sudo task, if within 15 minets one issues another admin task in the same terminal one doesn't need to enter sudo again as the earlier one is still running.  One can end this early with "sudo -k".  
The manual pages are a first point of call for me when feeling around commands.  To invoke them just enter "man" in front of any comand in the terminal, "man man" tells you how it works.  To leave the manual page press "q".  
"man sudo" and "man usermod" could be informative right now.    

What I do is have one terminal open for man pages and another for whatever I'm doing. You probably know all this anyway.  I can't give advice as I haven't seen this before but if you were to man the commands you used, and any others this web guide asks you for, you may find the answer.

Anyway, it'd be something to do while waiting for this bump to pull results.

 
P.S. 
This thread is packed with good links to good command line resources too.
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

---

### Post by sandyd on 2012-04-26
> **jps2012 said:**
> Whew! I think I'm OK. I got a confusing (to me, a noob) response from Terminal, and panicked. 

If anyone can explain why I would get the following message, saying there was an authentification failure, and THEN, when I executed "sudo su" I would be allowed to assume root privileges WITHOUT BEING ASKED FOR A PASSWORD, I'd love to hear it. 

Here's the script (the commands I executed, followed by responses; for other noobs, the "#" indicates I was switched to my root account) from bash: 

joel@JPS:~$ su
Password: 
su: Authentication failure
joel@JPS:~$ sudo su
root@JPS:/home/joel#
[COLOR=Red]su[/COLOR] uses the password of the root user.
[COLOR=Red]sudo su[/COLOR] uses the password of the user that is running sudo. Sudo escalates you to the root user, so naturally, the root user would not require you to login, because you are already logged into root.

---

### Post by jps2012 on 2012-04-27
Houseworkshy: Good advice. I hadn't thought of having one terminal for issuing commands, and another for reading man pages. That will save me from having to clear constantly. 

Sandyd: That's what I was really looking for: understanding the logic of su and sudo. Makes perfect sense (now that it makes sense, period). Pyrotechnics! Funnnnnnnnnnnnn! (Tried to look at the website. Maybe somebody blew it up? It's down.)

---

### Post by grahammechanical on 2012-04-27
You call yourself this

> (to me, a noob)

So, what is wrong with using System Settings>User Accounts to set up new users, to assign administrator privileges and to change passwords?

By doing things this way and getting it wrong it gives the impression to new users of Ubuntu that these things are complicated. Ubuntu is designed to be used by ordinary people and not only by "experts" as you call them.

Regards.

---

### Post by jps2012 on 2012-04-27
Yes, I'm sure you're right. There was a better way to do it. I'm learning. Slowly.

---

### Post by jps2012 on 2012-04-27
Grahammechanical: I didn't realize the setup could be done through System Accounts. Thank you.

---

### Post by jps2012 on 2012-04-27
I just finished the setup in System Settings (not Accounts--sorry). Again, many thanks. Much easier doing there than via the command line.

---


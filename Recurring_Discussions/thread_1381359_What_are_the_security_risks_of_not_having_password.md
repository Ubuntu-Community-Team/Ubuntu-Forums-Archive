---
title: "What are the security risks of not having password promts?"
date: 2010-01-14
forum: Recurring Discussions
---

### Post by viktorzk on 2010-01-14
Hello,

I am annoyed by having to enter my password whenever I want to install software or change the time or set CPU frequency, etc... After searching a bit about this, I have come across tens of warnings about security risks, but none of them persuaded me.

If we assume that nobody else will physically use my computer (due to the login password), why does the system insist on asking me again and again to prove my identity?

Thank you.
Viktor

---

### Post by garryknight on 2010-01-14
There shouldn't be any problem with running your system with no password. As long as you ***don't*** ***ever*** connect it to the Internet. I have a reasonably good password and my logs show anywhere from half a dozen to many dozens of attacks every day from other machines on the net - and not just from China (;)). My PC is behind a router with a built-in firewall and the router has a password and my PC has a password and its own firewall and I know that it's still not safe so I do a regular check for break-ins.

And it would be a big mistake to assume that no one else will have physical access to your machine, whether because of the login password (I can probably get around that in seconds) or because of someone breaking into your house (which has a good chance of happening) or through social engineering (if you don't know what that is, you without any doubt ***definitely need*** a root password).

Of course, if you *were* to run your computer without a password, you might never know who got access to it and uploaded all of your personal files to a server in Eastern Europe, or who it was that downloaded a large amount of extremely nasty pictures onto a not-very-well hidden directory on your hard drive, or who it is that accesses those files through a back-door port in your PC.

Or rather, you might find out too late...

---

### Post by sailthesea on 2010-01-14
As above and more, because the security of the OS has to be maintained at every level if possible. Not just your system but everyone else's. 
 People will try and attack Linux systems if a flaw shows. The built in protection has been pretty sufficient so far.
 It is not such a bad thing if you have be prompted for a password occasionally ;)

---

### Post by Agent ME on 2010-01-14
He doesn't want to remove his password completely, just the authentication prompts. You should be able to edit /etc/sudoers to do this, but I don't know the specific setting.

---

### Post by d3v1150m471c on 2010-01-14
"SRC:  221.xxx.xxx.xx, DL: 2, Dsts: 1, Pkts: 7, Unique sigs: 1, Email alerts: 2

    DST: 68.xx.xxx.xxx, Local IP
        Scanned ports: TCP 1080-8080, Pkts: 7, Chain: INPUT, Intf: eth0
        Signature match: "BACKDOOR sub seven file upload attempt"
            TCP, Chain: INPUT, Count: 1, DP: 3128, SYN, Sid: 2375"

This is why not to make alterations to root files you have passwords. PSAD detected this yesterday. Totally unprovoked, just some jerk trying to make a zombie out of my computer. I **do not** recommend changing this, and I'd also recommend using something like **firestarter** for a firewall manager. The password protected root file system in linux is also a great antivirus/antimalware system. **It does not make it impossible to get viruses and the like, just much more difficult for someone to override your authority.**

check this out : [http://ubuntuforums.org/showthread.php?t=1375324](http://ubuntuforums.org/showthread.php?t=1375324)

---

### Post by slowth5 on 2010-01-14
A great example is Windows XP. What a disaster. 

Is entering a password really such a hardship?

---

### Post by slowth5 on 2010-01-14
> **Agent ME said:**
> He doesn't want to remove his password completely, just the authentication prompts. You should be able to edit /etc/sudoers to do this, but I don't know the specific setting.

What's the point of a password if you're never asked to enter it?

---

### Post by sailthesea on 2010-01-14
> **Agent ME said:**
> He doesn't want to remove his password completely, just the authentication prompts. You should be able to edit /etc/sudoers to do this, but I don't know the specific setting.

  He is asking what the risks are
 He is getting some answers
 It's easy enough to log into root if you look. But I applaud the OP's original inquiry before just doing it
 Sudo su should be enough for adminining your own system. Why leave it open?

---

### Post by zipperback on 2010-01-14
> **viktorzk said:**
> I am annoyed by having to enter my password whenever I want to install software or change the time or set CPU frequency, etc... 


The computer is asking you to verify that you have permission to make a system wide change on the computer.

Normal user level accounts should never be allowed to make system wide changes to an account without a very good reason.

And besides... It only takes what? 1 perhaps 2 seconds to type your password into the prompt? I'd hardly call that a problem.



> **viktorzk said:**
> 
After searching a bit about this, I have come across tens of warnings about security risks, but none of them persuaded me.


How about not allowing your computer to become a zombie spam machine sending out millions of spam mails 24 hours a day?

How about not allowing hackers to attack other computer systems from your IP address?

The list goes on, but those two alone should be enough to convince you it's a bad idea to allow user level accounts root level access.

> **viktorzk said:**
> 
 If we assume that nobody else will physically use my computer (due to the login password), why does the system insist on asking me again and again to prove my identity?

One word: "SECURITY"

- zipperback
:popcorn:

---

### Post by Agent ME on 2010-01-14
> **slowth5 said:**
> What's the point of a password if you're never asked to enter it?
By authentication prompts I meant the prompt given by sudo/gksu, not the login prompt.

Removing the sudo prompt would only lead to bad things if you ran an untrusted program as a user in the admin group (which isn't a good idea even if you do have the sudo prompt enabled).

---

### Post by markp1989 on 2010-01-14
see my thread, [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1381467](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1381467) 

if i didnt have a password then the 13313 would of been successfull, (i dont know yet if any attemps were successfull)

just so you know my install was 2 days old.

---

### Post by Agent ME on 2010-01-14
Removing the sudo password authentication does not remove your account password!

---

### Post by markp1989 on 2010-01-14
> **Agent ME said:**
> Removing the sudo password authentication does not remove your account password!

well removing the sudo prompt is worse then removing the acount password, if some one gets in to a user account they can just damage that account/files , but with no sudo password, anything can be done to your system, any any one elses account .


you can edit you sudo file to sudo without password for some programs, i use it for hdtemp

---

### Post by Agent ME on 2010-01-15
If a malware programs gets into your account while you have a sudo password, there's numerous ways it can hijack your next sudo session. It could call sudo shortly after you do, while the session is still open. It could change your PATH variable so that typing "sudo" actually calls a script which calls the real sudo and another malware program. The malware could edit your menus so that an option that needs sudo also calls a malware program.

---

### Post by slowth5 on 2010-01-15
> **Agent ME said:**
> If a malware programs gets into your account while you have a sudo password, there's numerous ways it can hijack your next sudo session. It could call sudo shortly after you do, while the session is still open. It could change your PATH variable so that typing "sudo" actually calls a script which calls the real sudo and another malware program. The malware could edit your menus so that an option that needs sudo also calls a malware program.

Are you talking about removing permission from the sudoers file?

---

### Post by Techsnap on 2010-01-15
> A great example is people not configuring Windows XP properly with correct user profiles.

Fixed.

---

### Post by Grifulkin on 2010-01-15
In Arch I edited my sudoers file so that it gives everyone in the wheel group sudo access without a password.  Sure it might not be smart but I really don't care, it is easier for me.  As far as I'm concerned it is my PC and if I want to do something I am going to do it, not like anyone else uses it and besides if I screw something up I'll figure out how to fix it.  So for me it's worth the risk besides with the set up I have I am pretty sure I can figure out if someone is doing something on my computer, the ram usage or cpu or even the network usage will spike and it will alert me to something is going on.

---

### Post by garryknight on 2010-01-15
> **markp1989 said:**
> well removing the sudo prompt is worse then removing the acount password, if some one gets in to a user account they can just damage that account/files , but with no sudo password, anything can be done to your system, any any one elses account .

+1

---

### Post by viktorzk on 2010-01-16
Thank you all for the replies!

Would it be safe if I give root rigts only to certain trusted applications? Agent Me mentioned the /etc/sudoers file, I tried adding "viktor ALL=NOPASSWD:/usr/lib/gnome-applets/cpufreq-applet" but it didn't work. Does anybody know why? Also is there a way to find out what process owns a window, like in Windows Task Manager?

The problem with entering a password often is that the password prompt sometimes does not steal the keyboard focus, so if I don't look at the screen, I might enter my password in gedit for example. Is there any fix for this?

---

### Post by sliketymo on 2010-01-16
> **Grifulkin said:**
> In Arch I edited my sudoers file so that it gives everyone in the wheel group sudo access without a password.  Sure it might not be smart but I really don't care, it is easier for me.  As far as I'm concerned it is my PC and if I want to do something I am going to do it, not like anyone else uses it and besides if I screw something up I'll figure out how to fix it.  So for me it's worth the risk besides with the set up I have I am pretty sure I can figure out if someone is doing something on my computer, the ram usage or cpu or even the network usage will spike and it will alert me to something is going on.

And thus,spambots are made.The purpose of security is not to stop you from doing whatever you want with your machine,it is to stop UN-AUTHORIZED intities from doing something to,or with your machine without your knowledge.

---


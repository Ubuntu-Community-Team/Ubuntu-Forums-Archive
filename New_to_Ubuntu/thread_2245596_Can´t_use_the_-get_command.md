---
title: "Can´t use the -get command"
date: 2014-09-24
forum: New to Ubuntu
---

### Post by lennart4 on 2014-09-24
I try to install the latest VLC to Lubuntu.
When typing the command: apt-get install vlc  in terminal mode, the -get command  is unknown. Typing the HELP-command, I cant find the -get command.

Doesn't the -get command exist in Lubuntu??

---

### Post by steeldriver on 2014-09-24
Hello and welcome to the forums 

There is no "-get command" - the command is **apt-get** (all one word - no space)

---

### Post by lennart4 on 2014-09-24
Many thanks for your help!  That was the problem!

Now I got another problem,
when typing the command: apt-get install vlc,

 I got the message: Could not open /var/lib/dpkg/lock -open (13:Access denied)
Could not lock (/var/lib/dpkg)   Are you in root?

What is the reason for this?

---

### Post by yancek on 2014-09-24
> Could not lock (/var/lib/dpkg)   Are you in root?


The reason for that is you are doing it as a user and you need root privileges to install  software and make system changes.  Preface the command with sudo and when prompted enter your primary user password:

sudo apt-get install vlc

---

### Post by CantankRus on 2014-09-24
> **lennart4 said:**
> Many thanks for your help!  That was the problem!

Now I got another problem,
when typing the command: apt-get install vlc,

 I got the message: Could not open /var/lib/dpkg/lock -open (13:Access denied)
Could not lock (/var/lib/dpkg)   Are you in root?

What is the reason for this?
Might I suggest that you use the software center for installations if your not 
familiar with terminal usage.

---

### Post by kira-yamato-2008 on 2014-09-25
you do have to use a root access command like Sudo or gksu(I think that's correct) then you'll be asked for your password(if applicable) to install a program via terminal.

---

### Post by lennart4 on 2014-09-25
Hello all of you and many thanks for your help!

Now, I have learned new things about Linux Terminal mode. As you understand, I'm new on Linux and Lubuntu.
As suggested, I used the software center for this installatione, and all worked perfect.

Case closed!
Many thanks!
/Lennart

---

### Post by kira-yamato-2008 on 2014-09-25
> **lennart4 said:**
> Hello all of you and many thanks for your help!

Now, I have learned new things about Linux Terminal mode. As you understand, I'm new on Linux and Lubuntu.
As suggested, I used the software center for this installatione, and all worked perfect.

Case closed!
Many thanks!
/Lennart

Remember the Lubuntu Software Center, it's in the "start menu" under "System Tools" and has a lot of good stuff in it. You shouldn't need to terminal install something unless it's unavailable in the Lubuntu Software Center, or you're getting it from a different PPA Repository... In that case make sure it's a well known PPA repository with a good reputation.

---


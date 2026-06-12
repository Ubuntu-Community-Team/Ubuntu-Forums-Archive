---
title: "Need security 101"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Chainek on 2008-08-18
I'm just checking if there is anything I should or shouldn't do on a fresh install of ubuntu that a super noob should know. 

Should I make a single user account with admin rights, password it and never use it? Then make a separate user without admin rights?

Just, anything I should know? heh. 


I guess the reason I ask is because I had something quirky happen when setting up evolution mail with gmail. After putting in the pop and smtp server and password info.. I pushed send/receive for the first time and got a pop-up message saying something about connecting to [www.blabla.premiumservices.com](www.blabla.premiumservices.com) bla bla bla. Signature: bad..

I hit 'no'. Than after several times trying to get it to work. (im fairly familiar with setting up a mail account) I started getting irritated and hit yes once. It didn't do anything. I closed evolution down and re-opened then it worked fine. But then an hour later I got ridiculously written spam message in my mail. My mail NEVER gets spam. 

That was like within 30 minutes of a fresh install. I can't imagine that I got hacked. But it kind of weirded me out. I'm behind a router as well if that means anything.

Appreciate it.

---

### Post by pjones0404 on 2008-08-18
you do not need to create a separate admin account in ubuntu. the user that you create during the install is all that you need. you do not have root level privileges on the user accounts in ubuntu. there are not any virus or malware that you have to worry about either. 

chances are the email situation was a fluke. i am not aware of a way that it would connect you to a different mail server unless you accidentally misspelled the server and it happened to be a spam server. the firewall is built into the kernel as well so there is no need for an additional firewall. i think that it was just bad luck that you received the spam as there is nothing in ubuntu that would have allowed an attacker into your machine.

---

### Post by DGortze380 on 2008-08-18
> **pjones0404 said:**
> you do not need to create a separate admin account in ubuntu. the user that you create during the install is all that you need. you do not have root level privileges on the user accounts in ubuntu. there are not any virus or malware that you have to worry about either. 


Depending on what you do with your system, I would recommend creating a secondary user with full sudo access (should be able to achieve this by placing the user in the admin group). I actually would recommend something else, but I can't express what here.

You DO essential have root level privileges on an administrative user account. Use the sudo command to perform tasks with root privileges. You can edit what users have access to the sudo command, and what they are allowed to do with sudo. This is controlled by the sudoers file. Be VERY careful when editing this file, do some extensive research first.

Don't worry about virus or malware. Just be smart about what you download/install, but it's pretty hard to find a virus that will effect linux.

---


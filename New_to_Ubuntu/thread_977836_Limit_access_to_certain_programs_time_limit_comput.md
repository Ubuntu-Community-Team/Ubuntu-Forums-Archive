---
title: "Limit access to certain programs/ time limit computer"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by brandoncolorado on 2008-11-10
I have a lack of willpower.  Finals are approaching.  Is there an easy way in Ubuntu to limit access to certain programs, to time programs, or to do anything else like that?  Any programs that would help that could be installed via repository?

---

### Post by anewguy on 2008-11-10
Use the standard access rights - owner/group/world to limit access.  Put people who can access in a group - set the priviledges accordingly.

I know in standard Unix there is a way to time limit access.  I have never looked into this in Linux.

---

### Post by Allochtoon on 2009-01-15
> **brandoncolorado said:**
> I have a lack of willpower.  Finals are approaching.  Is there an easy way in Ubuntu to limit access to certain programs, to time programs, or to do anything else like that?  Any programs that would help that could be installed via repository?

I'm interested in this as well!
Did some searching on the web, apparently i cant browse or howtos are not available.

---

### Post by HermanAB on 2009-01-15
Look at Cyborg and Cybercafe.

Cheers,

Herman

---

### Post by Allochtoon on 2009-01-16
> **HermanAB said:**
> Look at Cyborg and Cybercafe.

Cheers,

Herman

> **HermanAB said:**
> Look at Cyborg and Cybercafe.

Cheers,

Herman

Thanks, but i was looking for something more small-scale.

I tried configuring pam_time, as to limit the login time of user 'gamer'. Say i want 'gamer' to only login* between 20:00 and 21:00 everyday. I made these changes to /etc/security/time.conf and /etc/pam.d/kdm. 

Also, only user 'gamer' has 'chown' rights to run games. 

*This means 'gamer' can keep on playing after 21:00. Someone spoke of a cron script to logout the user at 21:00 precisely. Also, is it possible to block http for user 'gamer'?

I used pam before succesfully, but now i cant get it started :(

---

### Post by Allochtoon on 2009-01-17
> **Allochtoon said:**
> Thanks, but i was looking for something more small-scale.

I tried configuring pam_time, as to limit the login time of user 'gamer'. Say i want 'gamer' to only login* between 20:00 and 21:00 everyday. I made these changes to /etc/security/time.conf and /etc/pam.d/kdm. 

Also, only user 'gamer' has 'chown' rights to run games. 

*This means 'gamer' can keep on playing after 21:00. Someone spoke of a cron script to logout the user at 21:00 precisely. Also, is it possible to block http for user 'gamer'?

I used pam before succesfully, but now i cant get it started :(

Anyone?

---

### Post by johnhoward68 on 2009-03-15
Anything ever come of this?
As a parent, I seek a password protected time limit control, that I can specify the hours of each day user can go online. If my kid is using the word processor, ok... but I want to limit online access to certain hours and to a certain total amount each day.
But I don't want to have to use Windows to get this. Were about to order 4 laptops for our 4 kids, but deciding between XP and Linux comes down to this factor.

---

### Post by Allochtoon on 2009-03-15
> **johnhoward68 said:**
> Anything ever come of this?
As a parent, I seek a password protected time limit control, that I can specify the hours of each day user can go online. If my kid is using the word processor, ok... but I want to limit online access to certain hours and to a certain total amount each day.
But I don't want to have to use Windows to get this. Were about to order 4 laptops for our 4 kids, but deciding between XP and Linux comes down to this factor.

[https://launchpad.net/timekpr](https://launchpad.net/timekpr)

---


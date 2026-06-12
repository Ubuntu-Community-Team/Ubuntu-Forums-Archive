---
title: "User Logon issues"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by lile001 on 2012-03-06
I have two users on my system, me and me better half.  

Up to a minute or two ago, we could both log on.  

But just now, when I try to log onto her account, the screen goes blank for a bit, then returns to the logon screen with everyone's name, as if I didn't log on.  I can log on normally.  I've powered down and it still happens.

It isn't a fatfingered password, which generates an error message.  It acts as if it is starting the user's session or whatever you call it, and then decides "Nah."

I can create a new user "test", logon as test, and log off.  I can log on as myself or as guest.  However me sweetie is going to be steamed that the new computer is inaccessible. 

Not much has changed since I could log onto her account, just a scant few minutes ago.  I have been sitting here, nobody has changed the passowrd (which would have generated an error message).  I added a few icons to the top bar (I am running gnome classic, so is she, under Ubuntu11.10.  The heck with that Unity crap.) Computer is quite new, just got it a week ago.  

How can we troubleshoot what is happening?

---

### Post by winh8r on 2012-03-07
try logging in  to her account using the console tty1, 

press control + alt + F1

login as normal with username and password and see if that works.

---

### Post by Neckrow on 2012-03-07
I am having this same issue. I was trying to get floppy disk to read in 10.10, went through loops to get the old version of udisks 1build1. I then noticed she couldn't access her downloads folder and the the Users privileges, seemed to not be setup correctly.  I enabled some options  to allow her to use the floppy disk. I logged out of the account so changes could be made if needed and went to log back in and this is where I am now. Any suggestions ? I did the terminal login and was able too atleast pwd says im in /Home/Customer . Thanks in advanced!!

---

### Post by Neckrow on 2012-03-09
I did adduser made a "customer" account. Same issue as the main account if that helps anyone. I saw something on the forums about the nvidia kernal had root permissions or something setup wrong. I am going to see if  can find that fix and give it a go. If anyone has any more suggestions please share your ideas.

---

### Post by thomsebastin on 2012-03-09
> **Neckrow said:**
> I did adduser made a "customer" account. Same issue as the main account if that helps anyone. I saw something on the forums about the nvidia kernal had root permissions or something setup wrong. I am going to see if  can find that fix and give it a go. If anyone has any more suggestions please share your ideas.
...why dint u try adding a user with gui interface way??try that n check it if it works.

---

### Post by Neckrow on 2012-03-09
> **thomsebastin said:**
> ...why dint u try adding a user with gui interface way??try that n check it if it works. How can you from the login screen make a new account. I thought this was not possible.... And as far as I can tell is still not possible.

---

### Post by thomsebastin on 2012-03-09
> **Neckrow said:**
> How can you from the login screen make a new account. I thought this was not possible.... And as far as I can tell is still not possible.
no i tell mean it that way....so r u not even able to log in to even a single account ???if u r able to,then test it the way i told.

---


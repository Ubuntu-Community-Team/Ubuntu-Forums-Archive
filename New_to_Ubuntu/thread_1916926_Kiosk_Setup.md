---
title: "Kiosk Setup"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by tcguys on 2012-01-29
I am a newbie to Linux and I am setting up an internet kiosk from instructions posted on instructables.com.  It basically has two users set up on the computer, one a standard or administrative user and the other a restricted user.  The restricted user only has a browser that can access the internet full screen and nothing else.  This part works fine, what my problem is that the standard or administrative usert also only has the browser as well.  There isn't any way to make any changes to the setup because it is using the altered Kiosk set up.  The restricted user is setup without a automatic login.  The instructions said to select the Kiosk Mode as the default session in the Login Screen Settings.
 
I need a way for it to use a different session setup for the two different users.  I am using Ubuntu 11.04.
 
Any assistance will be greatly appreaciated.
 
Thanks in advance.

---

### Post by mikewhatever on 2012-01-29
Select a non-kiosk session when you login as admin user.

---

### Post by Rodney9 on 2012-01-29
This link has many tips and other links to use Ubuntu as a kiosk -

[http://ubuntuforums.org/showthread.php?t=1891594&highlight=kiosk](http://ubuntuforums.org/showthread.php?t=1891594&highlight=kiosk)

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by tcguys on 2012-01-29
> **mikewhatever said:**
> Select a non-kiosk session when you login as admin user.
 
Thanks for the reply.  My problem is I don't know how and don't see where I can select a session at login, it appears to just use the session selected as default. What I see if I cancel at the autologin is I can choose another user and can enter the password, but not a session selection.  Again, I am new to Ubuntu/Linux so I don't know if I have a setting set incorrectly or maybe a script needs to be changed.

---

### Post by mikewhatever on 2012-01-29
The Lubuntu login manager, lxdm, looks something like this:

[IMG]http://www.tuxjournal.net/wp-content/uploads/2010/08/lubuntu10.10-lxdm.png[/IMG]

The left box at the bottom is where you select the session.

---


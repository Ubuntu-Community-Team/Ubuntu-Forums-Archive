---
title: "Reasons for not using auto-logon?"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by digitaldac on 2008-06-09
I see a lot of threads relating to using auto-logon so that no user name or password has to be input.  Looks easy enough, but I also see people saying that it's never a good idea to use this feature.  On a home PC where all users are trusted, what would be the reasons not to use auto-logon?  Thanks.

---

### Post by quickk on 2008-06-09
As long as you trust everyone that has physical access to the machine, I don't see a problem.  

The worse case scenario: someone breaks into your apartment and steals your computer.  You have all sorts of passwords saved in your web browser, and so the thief pretends he's you and could possibly buy some stuff off of the internet (if your browser happened to save passwords to, for example, amazon).  I guess that it is for this reason that you always have to manually enter your password for the really important sites like your bank's online banking page.   

I have enabled auto-logon.  I figure if anyone steals my computer, I'll find out about it pretty quick enough.

---

### Post by lisati on 2008-06-09
> **quickk said:**
> As long as you trust everyone that has physical access to the machine, I don't see a problem.
+1: And anyone who might have access through whatever networking you might have organized at home.

It largely boils down to personal choice and what constitutes and "acceptable risk".

---

### Post by digitaldac on 2008-06-09
Obviously I'm real new to this... how will auto-logon affect access through the network?  Does auto-logon take away some network level security as well?

---

### Post by JoshuaRL on 2008-06-09
The main thing is that you **don't ever want to enable auto-login as root.**  That is disabled on Ubuntu, and it is forum policy to not explain to anyone how to do that.  If you do that, you're severely vulnerable to attack.  It's one of the layers of defense that makes GNU-Linux one of the most secure OS in existence.

---

### Post by Paqman on 2008-06-09
Depends who you assess as being a "risk".

A genuinely malicious person who has physical access to your machine is going to smoke you whether you've got a password on your login screen or not. If you're just worried about the kids looking through your bookmarks, then yes, a login password is a good idea.

---

### Post by quickk on 2008-06-10
> **Paqman said:**
> A genuinely malicious person who has physical access to your machine is going to smoke you whether you've got a password on your login screen or not. 

And that's the truth.  I was flabergasted to find out about that you could have full control of a machine by rebooting and specifying "run level 1" in the grub screen... Gave me a new perspective on security!

---

### Post by ubuntu27 on 2008-06-10
> **JoshuaRL said:**
> The main thing is that you don't ever want to enable auto-login as root.  That is disabled on Ubuntu, and **it is forum policy to not explain to anyone how to do that**.  If you do that, you're severely vulnerable to attack.  It's one of the layers of defense that makes GNU-Linux one of the most secure OS in existence.


Really? I didn't know that there was such a policy in this Forum. :shock:

---

### Post by Kronie on 2008-06-10
u could do auto login? O_O thats great! ima look for manuals right away.. i am the only one using this machine anyway..

---

### Post by lisati on 2008-06-10
> **digitaldac said:**
> Obviously I'm real new to this... how will auto-logon affect access through the network?  Does auto-logon take away some network level security as well?

Ubuntu (more specifically the Gnome desktop, possibly others) have an option where you can log on remotely. It's up to you to decide who you let in and how.

---

### Post by JoshuaRL on 2008-06-10
> **ubuntu27 said:**
> Really? I didn't know that there was such a policy in this Forum. :shock:

Yeah.  Log in as root is not discussed here anymore.

[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by markbuntu on 2008-06-10
When I was having trouble with my video driver and x, autologin was not helpful. Be sure to set a time like 30 seconds before autologin so you can get to safe mode if you have to.

---


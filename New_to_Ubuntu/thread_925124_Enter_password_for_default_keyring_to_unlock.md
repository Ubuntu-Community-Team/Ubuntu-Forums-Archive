---
title: "Enter password for default keyring to unlock"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by crowhill on 2008-09-20
Hi there

Yesterday, I enabled automatic login for my user account (so that I don't have to type in my password anymore). However, since then, I get a window popping up each time after logging in. It says "Enter password for default keyring to unlock" (it has to do with the nm-applet which is locked, as it says). I type in my user password and everything is fine.

How can I tell the nm-applet to stop asking me about the password?

Thanks a lot in advance,
best regards,
crowhill.

---

### Post by aysiu on 2008-09-20
There's no solution to this. Believe me--I've looked.

The workaround is to use WICD instead of Network Manager.

---

### Post by SunnyRabbiera on 2008-09-20
To be honest automatic logins are a bad idea anyway, I know its an annoying concept to type in a password each time you log in but its for the better even if you are the only user of you computer.

---

### Post by aysiu on 2008-09-20
> **SunnyRabbiera said:**
> To be honest automatic logins are a bad idea anyway, I know its an annoying concepet to type in a password each time you log in but its for the better even if you are the only user of you computer.
Can you explain why?

---

### Post by steveneddy on 2008-09-20
My machine used to do that.

After a reinstall (due to my negligence) I don't have to input my password.

In the nm applet, there is a place for me to enter my password for my home network.

Since entering my password there I haven't been asked for my password ever again.

---

### Post by SunnyRabbiera on 2008-09-20
> **aysiu said:**
> Can you explain why?

security practice really, I never liked the idea that windows XP never prompted for a password unless you set it up to have one (thus is the reason for most its issues).

---

### Post by garyed on 2008-09-20
Is this just a Hardy problem?
I have 4 machines running Gusty & Feisty & they all do automatic log on with
no password request.

---

### Post by aysiu on 2008-09-20
> **SunnyRabbiera said:**
> security practice really, I never liked the idea that windows XP never prompted for a password unless you set it up to have one (thus is the reason for most its issues). Anyone who has physical access to my computer has root access anyway, so I don't view it as a security issue.

---

### Post by nkri on 2008-09-20
> **aysiu said:**
> Anyone who has physical access to my computer has root access anyway, so I don't view it as a security issue.

Does this mean you log in as root instead of a regular user with sudo privileges?  I've heard this is a pretty big security risk:(

---

### Post by crowhill on 2008-09-20
A reinstall is no option (too much tweaking I'd have to redo). Also, I like the nm-applet of gnome. It's kind of straight forward and it never let me down (until now). In conclusion, I guess, I go back to typing in my password again.

Thanks anyway,
cheers,
crowhill.

---

### Post by aysiu on 2008-09-20
> **nkri said:**
> Does this mean you log in as root instead of a regular user with sudo privileges?  I've heard this is a pretty big security risk:(
No. It means if someone is in the physical presence of my computer and has any small bit of know-how, she can gain root access to it easily. Such is the case with any computer (Windows, Mac, Linux, etc.) you have physical access to.

---


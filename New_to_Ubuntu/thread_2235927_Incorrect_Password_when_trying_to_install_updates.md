---
title: "Incorrect Password when trying to install updates"
date: 2014-07-23
forum: New to Ubuntu
---

### Post by etep513 on 2014-07-23
I have 14.04 lts.  When installing it, I opted for encryption.  I made my login password the same as the other password.  However, when I try to do updates, it tells me my password is wrong.  How do I solve this problem?

---

### Post by ajgreeny on 2014-07-23
Does this problem show for updating only or for all commands that need your password?

What about **sudo blkid**; does that work?
If it gives you some output, with your partitions listed, then your password is correct, and it must therefore be something else about updating that is causing your difficulty

---

### Post by etep513 on 2014-07-23
> **ajgreeny said:**
> Does this problem show for updating only or for all commands that need your password?

What about **sudo blkid**; does that work?
If it gives you some output, with your partitions listed, then your password is correct, and it must therefore be something else about updating that is causing your difficulty

I copied and pasted the password you gave me, but it still did not work.  It keeps telling me the password was wrong and that it was unable to authenticate.

---

### Post by etep513 on 2014-07-24
What else could be causing this problem?  I am unable to perform updates to ubuntu because of this.

---

### Post by yancek on 2014-07-24
> I copied and pasted the password you gave me

If you are referring to the earlier post suggesting:  sudo blkid, that is not a suggested password but a command you would enter, hit the Enter and be prompted for your password.  During the installation, you were prompted to create a user and a password for that user.  That user/password should have root/admin rights.

---

### Post by ajgreeny on 2014-07-24
> **yancek said:**
> If you are referring to the earlier post suggesting:  sudo blkid, that is not a suggested password but a command you would enter, hit the Enter and be prompted for your password.  During the installation, you were prompted to create a user and a password for that user.  That user/password should have root/admin rights.
Yes, sorry if you misunderstood, but yancek is correct.

I repeat, is it just for updating that your password does not work or is it for any command that needs root permissions?

---

### Post by etep513 on 2014-07-26
> **yancek said:**
> If you are referring to the earlier post suggesting:  sudo blkid, that is not a suggested password but a command you would enter, hit the Enter and be prompted for your password.  During the installation, you were prompted to create a user and a password for that user.  That user/password should have root/admin rights.

> **ajgreeny said:**
> Yes, sorry if you misunderstood, but yancek is correct.

I repeat, is it just for updating that your password does not work or is it for any command that needs root permissions?

I understand now.  I opened up terminal and I typed in the command you gave.  A line came up asking for the password.  I typed it in and it still said it was wrong.  What else should I try?

---

### Post by kira-yamato-2008 on 2014-07-26
I'm unsure if this is the best suggestion, but you might want to try a Reinstall from the CD, if possible one that keeps your current data. Also before any reinstall back up everything that's irreplaceable on your hard drive. Other than that I'm not sure exactly what you can do.

---

### Post by Vladlenin5000 on 2014-07-26
Your password is actually wrong. The usual culprit is a caps lock on during the installation (when you were asked to type in a password twice you might have done it with the caps lock on) and an auto login setting (no password required). In this scenario/situation users aren't aware they got the password wrong until it's needed.

---

### Post by open2reason on 2014-07-26
I had something like a couple of days ago.  I could singon using my normal account but not perform updates or indeed anything thet needed a sudo passphrase. It seemes that I had changed from EN1 (English UK) to EN2 (English US) whilst clicking about on the top line of the screen and once reset to EN1  all worked as expected.  The " and @ changed places.

---

### Post by Vladlenin5000 on 2014-07-26
> **open2reason said:**
> I had something like a couple of days ago.  I could singon using my normal account but not perform updates or indeed anything thet needed a sudo passphrase. It seemes that I had changed from EN1 (English UK) to EN2 (English US) whilst clicking about on the top line of the screen and once reset to EN1  all worked as expected.  The " and @ changed places.

That too... :|

---

### Post by bapoumba on 2014-07-26
Wow. We should share a wiki page or something with the common (or less common) troubleshooting tips from the forums. I have a cheat sheet that I update from time to time.

---

### Post by open2reason on 2014-07-27
> **Vladlenin5000 said:**
> That too... :|

I was just a click away from installing a fresh 14.04 when I noticed the En1 vs En2 indicator. 
I confirmed things by opening a new text file on the desktop, writing my  passphrase, reading it back (with lip movements), noticing the errors,  resetting the En1, retyping and rereading the  now correct passphrase:grin:.

Saved a lot of time.

---


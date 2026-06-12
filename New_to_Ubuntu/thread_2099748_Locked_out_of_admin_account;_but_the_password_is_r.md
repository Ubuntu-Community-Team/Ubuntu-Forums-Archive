---
title: "Locked out of admin account; but the password is right in shell; password changed too"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by klimtelfe on 2012-12-30
I have a dual boot, win7 and the lts 12.04 64bit. I tried  logging into my regular account but it keeps refusing to open. There is  no message saying anything was incorrect, but that message still comes  up if I type in gibberish as a password. 



  I initially thought that changing password would help, even though I  could access my files by using the correct one in shell through recovery  mode. **So I did change using 'passwd'.** But the result  is the same. I cannot open my desktop, just shell which I dont know too  much about when it comes to transferring files between partitions


  SIDE NOTE: I made a guest account for people to use when I am not around without a  password. But decided to put in a simple password later through the  'users'(i think thats the name) program in the settings menu. But the  changes did not take place and I am still unable to add the password  even though everything runs fine while adding and adjusting priveleges.  Maybe the two things are related???

---

### Post by Andy45 on 2012-12-30
If you have root access, use type "sudo passwd" into the shell/terminal instead of just "passwd" and try again. If that doesn't work either, try "su" to switch to root and then just use "passwd".

---

### Post by steeldriver on 2012-12-30
Just to be clear, are you locked out of the **account **(i.e. unable to log in even at a CTRL-ALT-F1/F2 virtual terminal) or just unable to start a GUI desktop session?

---

### Post by Sef on 2012-12-30
Read Psychocats'[How to reset your password]("http://www.psychocats.net/ubuntu/resetpassword") to reset your password

---

### Post by klimtelfe on 2012-12-30
I am unable to login to the GUI desktop session, for what I ASSUME is the admin account, since thats the only one I created during install and I use the same password for other updates, program installs; also shared partitions get mounted automatically

---

### Post by klimtelfe on 2012-12-30
> **Sef said:**
> Read Psychocats'[How to reset your password]("http://www.psychocats.net/ubuntu/resetpassword") to reset your password


Thats the method I used - Initially it gave me a token authenication manupilation error but then I corrected it with the first line and it worked..in ONLY changing the already correct password, not the gui desktop session

more specifically -> 

> mount -rw -o remount /
> passwd *username*

---

### Post by klimtelfe on 2012-12-30
> **steeldriver said:**
> Just to be clear, are you locked out of the **account **(i.e. unable to log in even at a CTRL-ALT-F1/F2 virtual terminal) or just unable to start a GUI desktop session?

Yes,Not able to log in just the GUI desktop session.  Not tried the CTRL-ALT-F1/F2 (When should I hit that..at the login screen..or at the bootmenu ?) virtual terminal, but am able to login to my home folder using my pw through 'drop to root shell prompt' in the recovery menu during boot.

---

### Post by squakie on 2012-12-30
Remember that your password is the same for terminal or the Gui - it's just a log in.  So, if you can get to a terminal window ctrl/alt/F1 and can do something like sudo ls -al, put in your password, and it runs, then it's not a password problem.
 
I would be more inclinded to think it is a video driver problem -just my opinion.  So, you could try something like adding nomodeset to the boot line and see if it helps.  There are other options to be tried as well.

---

### Post by klimtelfe on 2012-12-30
> **squakie said:**
> Remember that your password is the same for terminal or the Gui - it's just a log in.  So, if you can get to a terminal window ctrl/alt/F1 and can do something like sudo ls -al, put in your password, and it runs, then it's not a password problem.
 
I would be more inclinded to think it is a video driver problem -just my opinion.  So, you could try something like adding nomodeset to the boot line and see if it helps.  There are other options to be tried as well.

Actually currently I am trying to install a 6870 in crossfire - so I stuck in the new card instead of the old one just to test it out, before putting in both of them (old psu didnt have enough pci-e connectors). **I dont remember **if this happened at the same time, but I will try that too. Although since the card was the same model should it really be a problem since it worked ok before?:-?

---

### Post by klimtelfe on 2012-12-30
> **klimtelfe said:**
> Actually currently I am trying to install a 6870 in crossfire - so I stuck in the new card instead of the old one just to test it out, before putting in both of them (old psu didnt have enough pci-e connectors). **I dont remember **if this happened at the same time, but I will try that too. Although since the card was the same model should it really be a problem since it worked ok before?:-?
 
So I did try it but it didnt do anything. AIso it shouldnt work, since the guest session with limited rights works fine..i think:-({|=

---

### Post by steeldriver on 2012-12-30
If you get to a GUI login screen and/or can login to a desktop session as guest, then I think what that's telling you is it's something specific about YOUR (i.e. admin user's) X session startup

Some common problems are (1) your user's home directory not writeable (because of permissions/ownership or disk space - I think we can count out disk space since the guest session starts OK, presumably that's on the same partition) (2) the user's ~/.Xauthority (or more rarely ~/.ICEauthority) files being unwriteable because of permissions/ownership (3) something else in that particular user's startup (possibly in an non-default .xsession or .xinitrc file or a user-specific desktop application / service)

If you can get access to the user's home dir (either by logging in normally in a virtual terminal, or from the root console) you can try to find the problem e.g.

```
ls -ld /home/*user*

ls -l /home/*user*/.{ICE,X}authority

less /home/*user*/.xsession-errors
```

---


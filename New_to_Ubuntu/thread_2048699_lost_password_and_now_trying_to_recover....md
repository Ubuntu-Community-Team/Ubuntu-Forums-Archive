---
title: "lost password and now trying to recover..."
date: 2012-08-27
forum: New to Ubuntu
---

### Post by heyyy on 2012-08-27
i tried to recover my password following the instructions from [here]("http://naveenubuntu.blogspot.gr/2012/05/recover-login-password-of-ubuntu-1204.html") 
(entering also the command: "mount -rw -o remount /") and eveything went smoothly until i rebooted.
when i boot up now and the login screen appears i enter my (new) password as usual and then the screen blanks for a moment and "redirects" me back to the login screen.
any ideas? 

im using this laptop both for my work and personal matters so i would be really thankful i someone help me figure this out.

---

### Post by Zimmer on 2012-08-27
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Always used this, myself. But the command to mount newer versions as read/write is new to me, but logic says you perform that command BEFORE you try to make changes. Have another go, use the mount command first..then change the password ..?

---

### Post by heyyy on 2012-08-27
the password was changed successfully,my problem has appeared afterwards

---

### Post by steeldriver on 2012-08-27
Can you log in at a non-graphical session in one of the virtual terminals (Ctrl-Alt-F1 and so on)?

If so then it sounds like your desktop session cannot start for some reason - could be your filesystem is full or your home dir not writable but often it's because the .Xauthority or .ICEauthority files are not writable (usually because they've become root owned)

```
ls -l ~/.{X,ICE}authority
```If so remove them and try again

---


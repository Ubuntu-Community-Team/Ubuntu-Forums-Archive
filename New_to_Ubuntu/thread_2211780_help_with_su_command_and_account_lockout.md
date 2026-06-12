---
title: "help with su command and account lockout"
date: 2014-03-17
forum: New to Ubuntu
---

### Post by sniper8752 on 2014-03-17
I have an Ubuntu server, and disabled remote sudo login.  But I try logging in from another account, with su.  I enter the password, that I would normally for sudo, and it tells me that it is invalid.  That is my first problem.  I can usually run sudo commands from my other account (administrator account).  it also then tells me that the account is temporary locked for over 3000 seconds.  what is this, and how do I change this?  Is this PAM?

---

### Post by deadflowr on 2014-03-17
su needs root's password, not your password.
(sudo and su are different)
Did you make a root password?

---

### Post by mansonfan78 on 2014-03-17
Are you trying to log in to root from a terminal?  The user account you're using would have to have administrator rights and you'd have to use the same password you would normally use for that account.  And, yes, you would have to use sudo or gksu depending on what you're trying to do.

---

### Post by sniper8752 on 2014-03-17
I figured it out, partially.  I have to do "su admin", then enter the password for admin, so then I can do sudo stuff.  
I don't remember setting a password for root.  I read somewhere that ubuntu automatically creates a root password, and it shouldn't be used - sudo should be used.  
And what is the lockout associated with?

---

### Post by mansonfan78 on 2014-03-17
The lockout is probably a security measure.  According to the system you tried accessing the root account with an invalid password.  I've never done this before so I don't know for certain, but it just be locking you out to prevent brute-force hacks.

---

### Post by deadflowr on 2014-03-17
How beneficial would Ubuntu making a root password for you be, if you don't know it.
I guess from a technical point, there is a root password, but it is disabled and locked by default.
If you happen to know it you could re-enable it.
But the chances of that are on par with winning the lottery(or higher odds)

You can set a root password though, if you wanted.

---


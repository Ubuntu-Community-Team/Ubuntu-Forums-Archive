---
title: "Unable to shut down after creating new user account"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by allanhildon on 2012-01-29
I'm an absolute beginner with Ubuntu so embarrassed that I'm having to ask such a basic question. But, here goes.....
 
I installed v11 of Ubuntu last week on a spare PC and have been exploring without any drama. Today I created an additional user account after installing all the recommended downloads.
 
I gave the account a name but not a password. It is showing as an administrator account although I didn't realise I set it as this.
 
I now can't shut down through the onscreen options. When I try to shut down I just get a message that another user is logged on, and get a new screen which has the two user accounts visible. I tried to remove the new account but keep getting a message that this would destabilise the system. I just go around in circles, unable to find a way to power down, so have had to resort to switching off the power supply. A bit crude, but at least it switched off the machine!
 
Could someone explain how I can remove this second administrator account (I'm hoping this will solve the second problem of not being allowed to shut down).
 
thanks, Al

---

### Post by 2F4U on 2012-01-29
Do you have this problem even after the machine has been started?

---

### Post by grahammechanical on 2012-01-29
Imagine that you are using the machine and then you hand over to another user. You log out. The other user logs in. Then the other user tries to shut down. If the other user is allowed to do that then he will shut down your session. That is not nice.

So, we get the log in screen where you should log in and then shut down will give you the option to restart or actually shut down. That is how it works. The first user logged in is the user that shuts down the system. The other users can log out and if they shut down they get logged out.

You need to log in as the first administrator user. And then remove the other user that you set up. If you are logged in as that second user and you try to remove that user then that would destabilize the system. We cannot remove ourselves. We have to be another user who has an administrator account.

Regards.

---


---
title: "Is it compulsory to log out before shutting down machine?"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by arroy_0209 on 2012-10-04
When I finish my work, should I first log out of the session and then shut down the machine or is it allowable (i.e., not harmful) to directly shut down the machine with out logging out of the session?

A related doubt: is there any problem if I log in to say some email account and just close the browser with out logging out after checking my emails? Any security issues related to this? I alone use my computer.

---

### Post by nsturdev on 2012-10-04
Arroy_0209,

I routinely shutdown, or reboot my ubuntu desktop without logging out.  I have yet to see any problems arrise from it.

---

### Post by ppv on 2012-10-04
Logout is usually used if there are multiple users and when one user has finished they can logout and other users can then login.

If you intend to shut down it is ok to not logout and directly shutdown.

For your email question, it depends on how you like it, since you say you are the only user.

But, if you do not explicitly logout, chances are one may be able to directly reach your inbox by just opening the browser and going to the email website without having to provide the login credentials. If you do not want that, you should explicitly use logout.

---

### Post by Wim Sturkenboom on 2012-10-04
> 
When I finish my work, should I first log out of the session and then shut down the machine or is it allowable (i.e., not harmful) to directly shut down the machine with out logging out of the session?

If it was harmful, it would not be an option ;)

And in a console it's not even possible to first log out and next shutdown (you need to be logged in to be able to shutdown) :D

---

### Post by offgridguy on 2012-10-06
> **arroy_0209 said:**
> When I finish my work, should I first log out of the session and then shut down the machine or is it allowable (i.e., not harmful) to directly shut down the machine with out logging out of the session.

I rarely log out, usually just suspend, or shutdown.  However if you have more than one user account you cannot shutdown unless the other user is logged out.
Probably not an issue now as you are the only user,  something to keep in mind
if you do add another user.:p

---

### Post by mcduck on 2012-10-06
> **offgridguy said:**
> I rarely log out, usually just suspend, or shutdown.  However if you have more than one user account you cannot shutdown unless the other user is logged out.
Probably not an issue now as you are the only user,  something to keep in mind
if you do add another user.:p

well, you *can* shutdown even iwhen there are other users signed in, as long as you do it from a terminal. Logged in users will simply get a warning that the machine is going to shut down in a certain amout of time and they should save their work.. (if you do that, you might want to tell the shutdown to use bit longer delay than the default ten seconds, just to give people more time to react.)

---


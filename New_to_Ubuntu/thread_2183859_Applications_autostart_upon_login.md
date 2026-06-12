---
title: "Applications autostart upon login"
date: 2013-10-26
forum: New to Ubuntu
---

### Post by bethnesbitt on 2013-10-26
I have applications that have been automatically opening everytime I relogin to my system.  For example, about two weeks ago I was doing something in the user settings.  Now everytime I restart my system, users and groups reopens along with a few other programs.  How can I disable this from happening?

---

### Post by ian-weisser on 2013-10-26
In the logout dialog, do you see the checkbox "save session for future logins?"

When you logged out one time, you checked it. Perhaps not intentionally.
So it saved the applications and windows for future logins.

There are a couple ways to fix it.
One way is to close all windows and applications, and then logout again. Check the box this time only.

---

### Post by pqwoerituytrueiwoq on 2013-10-26
open the "settings manager" go to "session and startup" look in the session tab
that is where the issue some thing need to be set to never

---

### Post by bethnesbitt on 2013-10-26
No, it's unchecked, which is stranger because I keep closing the programs that are automatically opening everytime I restart my computer but they keep still opening up anyways.  So...they aren't opened when I shut down/logout/reboot so even if that was check they shouldn't be reopening every time.  Actually it's under general, the first tab but I just noticed something under sessions that says:

"These applications are a part of the currently-running session, and can be saved when you log out.  Changes below will only take effect when the session is saved.  Below that is a buttong to clear saved cached sessions, so now I'll reboot and see what happens

---

### Post by bethnesbitt on 2013-10-26
> **bethnesbitt said:**
> No, it's unchecked, which is stranger because I keep closing the programs that are automatically opening everytime I restart my computer but they keep still opening up anyways.  So...they aren't opened when I shut down/logout/reboot so even if that was check they shouldn't be reopening every time.  Actually it's under general, the first tab but I just noticed something under sessions that says:

"These applications are a part of the currently-running session, and can be saved when you log out.  Changes below will only take effect when the session is saved.  Below that is a buttong to clear saved cached sessions, so now I'll reboot and see what happens

That seemed to do the trick but did not really solve the problem completely, it only means that everytime I restart this will be an issue unless I remember to clear the cache each and every time

---

### Post by The Cog on 2013-10-26
I had this problem once. I fixed it in a two-step process:
1: close every application and while logging out, check the box to save sessions - this saves <nothing running>.
2: log in and out again, this time un-checking the save sessions box so that it won't save sessions in future.

---

### Post by bethnesbitt on 2013-10-26
> **The Cog said:**
> I had this problem once. I fixed it in a two-step process:
1: close every application and while logging out, check the box to save sessions - this saves <nothing running>.
2: log in and out again, this time un-checking the save sessions box so that it won't save sessions in future.

Cool thanks! :)

---

### Post by BlinkinCat on 2013-10-26
> **bethnesbitt said:**
> Cool thanks! :)


Hi,

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by bethnesbitt on 2013-10-26
> **The Cog said:**
> I had this problem once. I fixed it in a two-step process:
1: close every application and while logging out, check the box to save sessions - this saves <nothing running>.
2: log in and out again, this time un-checking the save sessions box so that it won't save sessions in future.

Actually it did not work.  After trying this, I unchecked saved sessions opened firefox, loged out and when I loged back in firefox opened up where I left off, so it is actually still an issue.  Another words, the only way to get applications to sop from opening up everytime I log into my system I have to make sure it is closed, for whatever reason it is saving my session, even though the session box is not checked.

---

### Post by bethnesbitt on 2013-10-26
> **bethnesbitt said:**
> Actually it did not work.  After trying this, I unchecked saved sessions opened firefox, loged out and when I loged back in firefox opened up where I left off, so it is actually still an issue.  Another words, the only way to get applications to sop from opening up everytime I log into my system I have to make sure it is closed, for whatever reason it is saving my session, even though the session box is not checked.

As an after thought, as for the first issue if the application does not close, the only way is to clear the cache, so this appears to be more a bug issue, unless somebody knows a work around.  Ill close it as solved anyways

---


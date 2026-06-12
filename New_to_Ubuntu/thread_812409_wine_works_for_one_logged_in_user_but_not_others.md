---
title: "wine works for one logged in user but not others"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by ant2ne on 2008-05-29
I can execute exe programs when logged in as one user, but wont execute for other users. Of course, this one user who can execute is the sudo user who installed wine via apt-get. I don't want to give the second user sudo. What gives?

---

### Post by iaculallad on 2008-05-29
> **ant2ne said:**
> I don't want to give the second user sudo. What gives?

You could use System->Administration->Users and Groups, "User Settings". Select your second user, click on its Properties and select the "User Priveledge" tab, remove the check mark for "Administer the System" to remove second user from sudoer.

---

### Post by anjilslaire on 2008-05-29
Wine apps are generally installed in one's /home directory. Are these windows apps installed in the 2nd user's directory? The 2nd user can't run anything that's installed into the 1st user's/home location.

---


---
title: "Facebook not working on Firefox"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by btedm on 2012-08-31
The problem seems to be with scripts.  For example normally to log out, you move the mouse to an arrow in the top right and a drop-down menu appears with a logout option.  Now, no menu appears.  Or when I click on "Like" it just brings up a message saying that Facebook has a problem.  I have tried Chromium and it works fine so this is not a big problem for me.  I just wondered if anyone knew of a fix.  I tried disabling NoScript, and also Adblock, but this did not help.  I had had the same problem several months ago and when I updated to Ubuntu 12.04 the problem was gone for a few months.

---

### Post by cariboo on 2012-09-01
What firefox add-ons are you using?

---

### Post by holycow131415 on 2012-09-01
In FF, click on Help > Restart with add-ons disabled.

Does that make fb work?

---

### Post by btedm on 2012-09-02
I tried restarting with all Firefox Add-ons disabled and still have the same problem.  The addins I have are:
  Adblock Plus
  Global Menu bar integration (for Unity)
  NoScript
  Open about:permissions
  printPDF
  Reminder fox
  Ubuntu firefox modifications
  User agent switcher
  Web2PDF converter

---

### Post by nyamina on 2012-09-03
> **btedm said:**
> The problem seems to be with scripts.  For example normally to log out, you move the mouse to an arrow in the top right and a drop-down menu appears with a logout option.  Now, no menu appears.  Or when I click on "Like" it just brings up a message saying that Facebook has a problem.  I have tried Chromium and it works fine so this is not a big problem for me.  I just wondered if anyone knew of a fix.  I tried disabling NoScript, and also Adblock, but this did not help.  I had had the same problem several months ago and when I updated to Ubuntu 12.04 the problem was gone for a few months.
Type ```
firefox -p
``` into a terminal and try a new profile.

---

### Post by btedm on 2012-09-10
Thanks nyamina.  I tried a new profile and with the new profile the situation is much better -- I can log out of Facebook.  Now I need to see what I can recover from the old profile (bookmarks, add-ons etc.).  For now I can start Firefox with the new profile for Facebook and with the old profile for everything else.  I still have some work to do but I am going to list this thread as solved.

---


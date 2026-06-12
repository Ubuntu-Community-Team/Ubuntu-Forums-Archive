---
title: "Firefox security alert"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by cressrt on 2012-11-19
Firefox will not work, am getting a message saying

"could not initialize the applications security component ....and to check the directory has no read/write restrictions...and that the hard disk is not full"

I cannot see any restrictions and the hard drive has plenty of space. I have removed and re installed but the alert remains, any suggestions?

---

### Post by plucky on 2012-11-19
> **cressrt said:**
> Firefox will not work, am getting a message saying

"could not initialize the applications security component ....and to check the directory has no read/write restrictions...and that the hard disk is not full"

I cannot see any restrictions and the hard drive has plenty of space. I have removed and re installed but the alert remains, any suggestions?

From a terminal ```
firefox --safe-mode
``` and see if you get the same error.

Good luck

---

### Post by cressrt on 2012-11-19
I get the same message, in full it is
> Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.
Any other suggestions?

---

### Post by plucky on 2012-11-19
> Any other suggestions?


Try deleting the .mozilla hidden folder in your /home directory.

Make sure Firefox is closed before you delete the .mozilla folder.


Good Luck

---

### Post by cressrt on 2012-11-19
That worked, obviously something was wrong with a file in that folder, I thought removing and re-installing would have done that but obviously it does not remove everything.
Thanks

---

### Post by cressrt on 2012-11-19
I think there may be a problem with Firefox as it the Alert has come back. It may be caused by a site or something I have done but I was not noting this before it occurred. I have deleted the .mozilla folder and it works again but this deletes all my bookmarks, saved passwords etc. which is a not of a pain.
What should I do, do i need to report this elsewhere, suggestions please?

---

### Post by alphacrucis2 on 2012-11-19
Googling your error message comes up with some hits like this:

[http://support.mozilla.org/en-US/kb/couldnt-initialize-applications-security-component](http://support.mozilla.org/en-US/kb/couldnt-initialize-applications-security-component)

Since you have already erased your profile and the problem has recurred I would be suspicious of any add ons.

---

### Post by cressrt on 2012-11-20
I had reinstalled and had not yet got and add ons, the only exception being to sync the bookmarks with another PC. I have looked at the suggestions on the Firefox page but all is well at the moment, I'll have to wait and see if it happens again.
Thanks

---


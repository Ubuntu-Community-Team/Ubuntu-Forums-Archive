---
title: "No authentication requested on Update Manager"
date: 2012-01-08
forum: New to Ubuntu
---

### Post by Dennis N on 2012-01-08
Ubuntu 11.10:

After clicking the install button, Update Manager proceeds to download and install without asking for authentication. Not what I expected. I have not used any sudo operations in the session. Is this now normal behavior?

Also noticed: no more indication of download speed, remaining time estimate, or count of packages as they are downloaded.

---

### Post by Elfy on 2012-01-08
This is normal behaviour now - if update manager needs to install something new though it should prompt for password.

---

### Post by Dennis N on 2012-01-08
> **forestpiskie said:**
> This is normal behaviour now - if update manager needs to install something new though it should prompt for password.

Thanks. 

What about the other indicators I mentioned: download speed, remaining time estimate, count of packages as they are downloaded.

Has this information now been removed from the Update Manager display?

---

### Post by Elfy on 2012-01-08
I'm sure I see those things - can't double check though as I've no updates. Is there an arrow somewhere to expand the box.

---

### Post by Dennis N on 2012-01-08
All I saw is the progress bar. Previously, superimposed on the progress bar it would say "downloading package 23 of 100" or something close to that. Below the progress bar used to be the download speed and time remaining.

---

### Post by wigout on 2012-01-08
Before 11.10 users were asked for passwords when using update manager.
As of 11.10, update manager updates without authentication.

Under 11.10, I see an update, click ok, and the process gets "backgrounded" (minimized) If I click on the process I can bring it to the foreground- else it just completes updating and closes itself (unless a restart is required).

-wigout

---

### Post by Dennis N on 2012-01-08
> **Dennis N said:**
> All I saw is the progress bar. Previously, superimposed on the progress bar it would say "downloading package 23 of 100" or something close to that. Below the progress bar used to be the download speed and time remaining.

OK, Confirmed on another machine:

Basic Update Manager window now only displays a progress bar without other information for the user.

Details (if opened by user) will show progress of each **individual** file as it downloads, but not overall progress or any speed indication: 

Example:

Firefox
"78%  - Downloaded 13.7mB of 17.4mB"


This appears to be the new normal behavior for Update Manager.

---


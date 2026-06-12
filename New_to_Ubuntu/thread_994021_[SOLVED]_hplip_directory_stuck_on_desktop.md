---
title: "[SOLVED] hplip directory stuck on desktop"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by fxtr on 2008-11-26
I installed the hplip-2.8.10 in the Desktop directory. I used Synaptic to remove all HP items but the directory remains on the desktop and I don't know how to set the permissions to remove it.

The next problem is how to find the Download directory and get the hplip-2.8.10.run into a directory to install it.:confused:

---

### Post by gn2 on 2008-11-26
To delete the directory from your desktop, press Alt+F2 then type ```
gksudo nautilus
```

This will open a nautilus file browser **[COLOR="Red"]with admin privileges[/COLOR]**.
Delete the directory then close nautilus.

The highest supported version of hplip is 2.8.7 and it's in the Ubuntu 8.10 repositories.
You also need the hplip-gui package which is not installed by default.

---

### Post by fxtr on 2008-11-26
Solved - Thanks. Did manage todelete the directory using <rm -r> . Found an old Unix System V.4 command summary from 15 years ago. I installed hplip in Public. the ...10 version seem to work OK so far. Good to know about Nautilus!

---


---
title: "Update Error Message"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by Rex Bouwense on 2011-10-08
I checked for updates this morning using the update manager and got the error in the attachment.  Any ideas?

---

### Post by thefasterblueone on 2011-10-08
```
sudo rm -r /var/lib/apt/lists
sudo mkdir -p /var/lib/apt/lists/partial
sudo aptitude update
```

---

### Post by Rex Bouwense on 2011-10-08
Thanks for the quick reply.  What exactly am I removing with the command and what effect is that going to have on my system?

---

### Post by MrSpike16 on 2011-10-08
You are removing files that contain information for the repositories like directories, files etc.. and PGP keys.  There will be no effect on your system as these files are only used for getting updates
and programs.

Next aptitude update, the files will be downloaded and the PGP key files will be reinstalled.

However, using sudo rm -r can be disastrous if sudo already has the password and you accidentally hit the Enter key while typing the command in. 

Therefore use Copy & Paste for these commands.

---

### Post by Rex Bouwense on 2011-10-08
Sorry for the late reply but I had a WIFI problem.  Thanks all.  The code worked perfectly.  I am bookmarking that because it could come in handy.  Never too old to learn and proud of it.

---


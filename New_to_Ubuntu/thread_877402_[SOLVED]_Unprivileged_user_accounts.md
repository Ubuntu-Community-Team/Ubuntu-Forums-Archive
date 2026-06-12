---
title: "[SOLVED] Unprivileged user accounts"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by mczonie on 2008-08-01
If a hacker (or someone else) were to get into an unprivileged user account, what could he do from there? I'm asking because I just created an unprivileged guest account in case someone is over at my house and wants to check their email or do some casual web surfing, and I'd like to make the password something that's obvious and easy to remember, if that's safe to do. 

TIA.

---

### Post by issih on 2008-08-01
They couldn't do anything that requires root privileges essentially.

Couldn't alter or modify any file owned by another user (typically they can read them, but it really all depends on how the permissions are set up).

Couldn't add remove any packages/.

Couldn't alter any of the core system at all.

Basically they can play all they want in the sand box that is their home directory, create files delete them, run any installed apps that don't need root access. Noramlly they can also view the rest of the files on the system, but can't do anything to them at all.

Its pretty safe

---

### Post by chris09 on 2008-08-01
Sorry I'm totally of topic but i cand seem to find where to post comments

---

### Post by ad_267 on 2008-08-01
> **chris09 said:**
> Sorry I'm totally of topic but i cand seem to find where to post comments

You mean you want to start a new thread? Go to the forum you want to post in like [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326) and click on "New Thread" which is above the red heading.

---

### Post by louieb on 2008-08-01
You might be interested in: [HowTo: Create a Passwordless / Guest Login (Simple Method) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=513820")

---


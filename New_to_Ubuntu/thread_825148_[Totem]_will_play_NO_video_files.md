---
title: "[Totem] will play NO video files"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by oldrocker99 on 2008-06-10
I've been using Totem to show .avi, .mpg, .wmv, .divx etc just fine until today, when Totem returned this error:

An error occurred

Failed to connect stream: invalid argument

I am completely updated, have reinstalled all the restricted packages and still get this error. It happens after a reboot as well.

Any ideas? I'm baffled.

:guitar:

---

### Post by gr4nf on 2008-06-10
try reinstalling totem:
```
sudo apt-get remove totem
sudo apt-get install totem
```

---

### Post by Bubba64 on 2008-06-10
> **oldrocker99 said:**
> I've been using Totem to show .avi, .mpg, .wmv, .divx etc just fine until today, when Totem returned this error:

An error occurred

Failed to connect stream: invalid argument

I am completely updated, have reinstalled all the restricted packages and still get this error. It happens after a reboot as well.

Any ideas? I'm baffled.

:guitar:

I like totem due to being able to open a media file and have it open each part individually. Have you checked with any other media players to see if this is a system wide problem.

---

### Post by oldrocker99 on 2008-06-10
> **gr4nf said:**
> try reinstalling totem:
```
sudo apt-get remove totem
sudo apt-get install totem
```

That did the trick. THANKS * 10^6!

:guitar:

---

### Post by chaplinux on 2008-09-01
Bug related in [https://bugs.launchpad.net/~desktop-bugs](https://bugs.launchpad.net/~desktop-bugs) -> [Link to Search!]("https://bugs.launchpad.net/~desktop-bugs?field.searchtext=Failed+to+connect+stream&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")

---


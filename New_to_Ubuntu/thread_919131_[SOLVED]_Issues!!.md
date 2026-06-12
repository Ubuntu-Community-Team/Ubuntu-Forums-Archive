---
title: "[SOLVED] Issues!!"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by doctorbighands on 2008-09-13
Issue #1
I try to execute OpenOffice Writer, and it gives me the following message:

"The application cannot be started.
OpenOffice.org user installation could not be processed due to missing access rights. Please make sure that you have sufficient access rights for the follwing location and restart OpenOffice.org:

/home/<user>/.openoffice.org2"


Issue #2
I tried to download Songbird, but it wouldn't open the .tar.gz file because of something about a helper application. I didn't make note of the message before I closed it, unfortunately.

Any ideas??

---

### Post by ptn107 on 2008-09-13
> Issue #1
I try to execute OpenOffice Writer, and it gives me the following message:

"The application cannot be started.
OpenOffice.org user installation could not be processed due to missing access rights. Please make sure that you have sufficient access rights for the follwing location and restart OpenOffice.org:

/home/<user>/.openoffice.org2"


Try this at the command line:
```
chown -R $USER /home/$USER/.openoffice.org2
```
(prefix the command with **sudo** if it complains about permissions)

> 
Issue #2
I tried to download Songbird, but it wouldn't open the .tar.gz file because of something about a helper application. I didn't make note of the message before I closed it, unfortunately.

Any ideas??

It's a firefox problem.  I sometimes have that problem with .torrents.  You can just right-click the link in firefox and 'Save Link As'.  Then open it with archive manager.

---

### Post by doctorbighands on 2008-09-13
> **ptn107 said:**
> Try this at the command line:
```
chown -R $USER /home/$USER/.openoffice.org2
```
(prefix the command with **sudo** if it complains about permissions)



It's a firefox problem.  I sometimes have that problem with .torrents.  You can just right-click the link in firefox and 'Save Link As'.  Then open it with archive manager.

Issue 1: Worked like magic. Thank you!!

Issue 2: I'm about *this* close to giving up on FF permanently. The more I use it and hear about it, the more it seems Mozilla really screwed the pooch on v.3.

Thank you again!

---


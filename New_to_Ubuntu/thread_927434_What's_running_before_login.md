---
title: "What's running before login"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Ian Toner on 2008-09-23
Hi there

A quick, but dumb, question.  I'm setting up an ubuntu box on my home network, with the goal of making some / all of the disk available for storage, and of making a printer that I'm planning to attach to it available to other machines on the network.  The other machines will be various flavors of Windows.  I'm planning to use the desktop version of ubuntu, although it'll be more like a server than anything.

So, the question is as follows.  Do I need to have a user continuously logged on on the Ubuntu box to make these services available, or will the sharing details that I set up when logged in remain up even when I log out that user?  What's actually running and/or available when I get the graphical login screen (if anything)?

Is there somewhere available that would cover this?  I've tried to do the usual digging, but I guess this question is SO dumb that it's not obviously covered...

Thanks for your help in advance.

---

### Post by jerome1232 on 2008-09-23
> **Ian Toner said:**
> Hi there

A quick, but dumb, question.  I'm setting up an ubuntu box on my home network, with the goal of making some / all of the disk available for storage, and of making a printer that I'm planning to attach to it available to other machines on the network.  The other machines will be various flavors of Windows.  I'm planning to use the desktop version of ubuntu, although it'll be more like a server than anything.

So, the question is as follows.  Do I need to have a user continuously logged on on the Ubuntu box to make these services available, or will the sharing details that I set up when logged in remain up even when I log out that user?  What's actually running and/or available when I get the graphical login screen (if anything)?

Is there somewhere available that would cover this?  I've tried to do the usual digging, but I guess this question is SO dumb that it's not obviously covered...

Thanks for your help in advance.

Since the other machines are all windows you will probably be going with samba for the file/printer serving and once it's installed and configured you would not have to log in to get the service actually started, the samba daemon is started during the initial bootup process.

---

### Post by Ian Toner on 2008-09-23
Thanks.  Any suggestions on where I can read up on what's started on boot, and what waits for user login?
Thanks again for the quick response.

---


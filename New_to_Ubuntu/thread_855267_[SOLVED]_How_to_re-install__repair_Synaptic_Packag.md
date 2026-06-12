---
title: "[SOLVED] How to re-install / repair Synaptic Package Manager"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Tim Silver on 2008-07-10
Hi,

Me again!

Since my re-install of Ububtu 8.04, Synaptic Package Manager no longer works although Add/Remove does. When I click on Synaptic Package Manager, the icon changes to the 'whirly' thing for a few seconds, then nothing. Not even an error message I could post.

Thought I'd un-install then re-install using Add/Remove but it won't let me.

I've looked through some posts and have come across a couple of commands to try - 

dpkg-reconfigure -a        or
sudo apt-get install -f    which apparently repairs packages.

Which do you think would be best in my case?

---

### Post by plucky on 2008-07-10
> Which do you think would be best in my case? 


None,Open a terminal and ```
gksudo synaptic
``` see what errors you get in the terminal window an post output here.

Good Luck

---

### Post by philinux on 2008-07-10
Try this, copy and paste.

sudo apt-get update && sudo apt-get upgrade


Post any errors.

---

### Post by Tim Silver on 2008-07-10
Thanks for replies.

I got 198 updates/upgrades using philinux's apt-get method (don't ask me why I worked from the bottom up!). Then I tried plucky's 'gksudo synaptic' - this started Synaptic Package Manager and will now open when I access through System/Administration.

However, still a problem - the Update Manager is showing that I still have 20 updates available but hangs when I click Install Updates!

No errors from either course of action.

---

### Post by plucky on 2008-07-10
> **Tim Silver said:**
> Thanks for replies.

I got 198 updates/upgrades using philinux's apt-get method (don't ask me why I worked from the bottom up!). Then I tried plucky's 'gksudo synaptic' - this started Synaptic Package Manager and will now open when I access through System/Administration.

However, still a problem - the Update Manager is showing that I still have 20 updates available but hangs when I click Install Updates!

No errors from either course of action.


Try a different server **System > Administration > Software Sources**
and select another server.Exit and select "Reload" and then see if you can update.

Good Luck

---

### Post by baig2k9 on 2010-01-10
> **plucky said:**
> Try a different server **System > Administration > Software Sources**
and select another server.Exit and select "Reload" and then see if you can update.

Good Luck
please help me i want to reinstall my synaptic packet manager because it is showing these error what i have to do iam new to linux please help me 
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
what i have to do now please help me

---

### Post by plucky on 2010-01-10
> **baig2k9 said:**
> please help me i want to reinstall my synaptic packet manager because it is showing these error what i have to do iam new to linux please help me 
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
what i have to do now please help me

Your Synaptic package manager is probably ok,but the playonlinux.list is incorrect is the reason you are getting the error.

Open a terminal **Applications > Accessories > Terminal** and copy and paste this command into it and post the output to the forum ```
cat etc/apt/sources.list.d/playonlinux.list
```

You can either repair the file or delete it and the error should go away.

Good Luck

p.s You should start your own thread to get help quicker as this thread has the **[SOLVED]** added to the title.

---


---
title: "How to create a Live USB Iso from Ubuntu Builder?"
date: 2015-08-17
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-08-17
Hello guys 
I'm currently customizing Ubuntu Mini Remix ISO using Ubuntu Builder and I want to know how to create a Live USB directly from the software after I finish building the customized ISO?

---

### Post by Ben_Shaver on 2015-08-17
The Ubuntu Builder project was abandoned in early 2014, I wouldn't be too hopeful that it'd still be functional a year later. However, the Ubuntu Customization Kit is still an active project and does the same things as Ubuntu Builder, I believe.

---

### Post by remmas-sido on 2015-08-17
> **Ben_Shaver said:**
> The Ubuntu Builder project was abandoned in early 2014, I wouldn't be too hopeful that it'd still be functional a year later. However, the Ubuntu Customization Kit is still an active project and does the same things as Ubuntu Builder, I believe.

Do you know where I can find a guide of a PDF tutorial about it? because the last time I use it it was not very user-friendly if you know what I mean?

---

### Post by oldfred on 2015-08-17
I regularly see users wanting to customize an ISO, but do not have a good suggestion.

Unless installing to many users and limited Internet download, or install will be to a system without Internet access, then I think just running a script to two to make updates/changes to system after install is easier to configure & run.

---

### Post by remmas-sido on 2015-08-17
> **oldfred said:**
> I regularly see users wanting to customize an ISO, but do not have a good suggestion.

Unless installing to many users and limited Internet download, or install will be to a system without Internet access, then I think just running a script to two to make updates/changes to system after install is easier to configure & run.

Where can I find some scripts?

---

### Post by oldfred on 2015-08-18
I have this in my notes, it seems a bit more complex.
 Install script from Minimal - Paqman
[http://ubuntuforums.org/showthread.php?t=1460870](http://ubuntuforums.org/showthread.php?t=1460870)
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

I think I posted my scripts ages ago, but they mostly are unique as UUIDs, partitions, and list of software that I install is what I want, not necessarily what you may want.
Found this which is part of my script for editing fstab, but has my UUIDs & mount points:
[http://ubuntuforums.org/showthread.php?t=1892417](http://ubuntuforums.org/showthread.php?t=1892417)

Attached are some of my old scripts, you would have to greatly customize for your use.
Note that much is commented out as either it is obsolete or I am testing it but have not fully included it. I normally run the link script first then the new install script.

---


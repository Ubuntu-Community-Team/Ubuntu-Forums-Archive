---
title: "Update Manager - no password request"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by jim4wb on 2011-10-21
I did my weekly check of updates [there were no automatic updates indicated] and when the Update Manager loaded the list of changes and I clicked on <install updates> the "Applying changes" window appeared started loading without requesting my password for authentication.

Has the process changed or has this last line of defence been cut out in 11.10?

Jim

---

### Post by BlinkinCat on 2011-10-21
Same thing happens to me -

---

### Post by llamabr on 2011-10-21
You never know with ubuntu, and their crazy user friendly policy what weird change they'll make.  But my guess is that, since you ran sudo once to begin the process, and sudo remembers your authorization for 5 minutes or so, then it will not ask you again until that time has run out.

---

### Post by heresam on 2011-10-21
11.10
Happened to me without any sudo inputs -- booted up (automatic login), ran update manager, clicked install and ran without any password request. Very strange indeed.

---

### Post by lolpenguin on 2011-10-22
I think they removed the root requirement to install updates in oneiric. You should be able to change it though.

---

### Post by roger_1960 on 2011-10-22
Definitely doesn't need password to run updates on my 11.10 install.  Still needs password for installs from Software center......?

---

### Post by gsmanners on 2011-10-22
Looks to me like it was (probably) designed this way:

[https://blueprints.launchpad.net/ubuntu/+spec/security-m-easier-security-updates](https://blueprints.launchpad.net/ubuntu/+spec/security-m-easier-security-updates)

Might be related:

[https://blueprints.launchpad.net/ubuntu/+spec/what-do-non-geeks-want](https://blueprints.launchpad.net/ubuntu/+spec/what-do-non-geeks-want)

---

### Post by plasmafusion on 2011-10-22
i've got this problem too...posted here about it...filed a launchpad bug about it. software centre asks for a password as does apt-get via the command line.

---

### Post by philinux on 2011-10-22
> **jim4wb said:**
> I did my weekly check of updates [there were no automatic updates indicated] and when the Update Manager loaded the list of changes and I clicked on <install updates> the "Applying changes" window appeared started loading without requesting my password for authentication.

Has the process changed or has this last line of defence been cut out in 11.10?

Jim

This is the new default behavior for UM in oneiric. Reason being it is only updating user  installed packages.
Edit. Found the link.
 [http://ubuntuforums.org/showpost.php?p=11320387&postcount=12](http://ubuntuforums.org/showpost.php?p=11320387&postcount=12)

---

### Post by plasmafusion on 2011-10-22
if that's the case i'd say it is a step backwards. all updates are not good updates. best let the administrator decide...not the regular user.

---

### Post by philinux on 2011-10-22
> **plasmafusion said:**
> if that's the case i'd say it is a step backwards. all updates are not good updates. best let the administrator decide...not the regular user.

It has to be the admin user.  See my previous post.

---

### Post by plasmafusion on 2011-10-22
duly noted. cheers.

---

### Post by gsmanners on 2011-10-22
Okay, so: [https://lists.ubuntu.com/archives/oneiric-changes/2011-June/003881.html](https://lists.ubuntu.com/archives/oneiric-changes/2011-June/003881.html)

Explains why I didn't find it. I was looking through update manager.

---

### Post by IamInnocent on 2011-10-29
Well, yesterday I updated all my system from a freshly created, simple user account. No software has ever been installed from that account, just as it shouldn't be possible. This is most certainly not good. 

This version of Ubuntu is the first which truly disappoint me. Hopefully they'll start listening to their users, instead of hiding behind behind "aphorisms" like: "It's the leaders in a battle who takes the most arrows.". These are really just clichés which need an update. Maybe they lost their password ?

---


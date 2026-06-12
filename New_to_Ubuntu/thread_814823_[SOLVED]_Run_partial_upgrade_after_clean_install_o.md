---
title: "[SOLVED] Run partial upgrade after clean install of hardy"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by talsemgeest on 2008-06-01
I've just done a clean install of Ubuntu Hardy using the cd I got from shipit.

The install seems to go fine, I can boot into Ubuntu, but when I try to install updates, it give me the following: 
```
Not all updates could be installed

Run a partial upgrade, to install as many updates as possible.

This could be caused by:
*A previous upgrade which didn't complete.
*Problems with some of the installed software.
*Unofficial software packages not provided by Ubuntu.
*Normal changes of a pre-release version of Ubuntu
```

When I tell it to do a partial upgrade it gives me the following:
```
Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later.
```

Any ideas about what is causing this? And how to fix it?

Thanks in advance...

---

### Post by rockerphil on 2008-06-01
if yu've still got the Gutsy Gibson CD i'd suggest installing that and then running

sudo apt-get dist-upgrade

or running an upgrade through the update manager, which does the same thing. cus it sounds to me like you got one of the few bad disks

---

### Post by talsemgeest on 2008-06-01
So I guess I should run a cd check just to be sure. Would that detect all the problems with the cd?

---

### Post by cheesypoof on 2008-06-01
I have been receiving partial upgrade errors for openoffice and python lately for hardy. How many updates can't you install? I'm not sure why you are so quick to point the finger at the cd.

---

### Post by sayakb on 2008-06-01
This is a problem due to the OpenOffice 3 (Beta?) in the proposed repos. If you want to do an update anyway, Goto System->Administration->Software Sources->Updates tab and **disable** the Proposed and Unsupported updates from there. You might later **enable **the proposed updates, but it's better to keep the unsupported portion (backports) **disabled.**

---

### Post by talsemgeest on 2008-06-01
> **cheesypoof said:**
> I have been receiving partial upgrade errors for openoffice and python lately for hardy. How many updates can't you install? I'm not sure why you are so quick to point the finger at the cd.
Just the fact that it is from a clean install, and the only thing that has had access to my computer is just that.

---

### Post by talsemgeest on 2008-06-01
> **LinuxIsInnovation said:**
> This is a problem due to the OpenOffice 3 (Beta?) in the proposed repos. If you want to do an update anyway, Goto System->Administration->Software Sources->Updates tab and **disable** the Proposed and Unsupported updates from there. You might later **enable **the proposed updates, but it's better to keep the unsupported portion (backports) **disabled.**
And you are absolutely brilliant. I am pretty sure that is what it is, but I have to wait a little while to test it out. I will report back once I've tried.

---

### Post by talsemgeest on 2008-06-01
Ok, everything is good, it is just a problem with OO.org

---

### Post by Joeb454 on 2008-06-01
I'm guessing you have hardy-proposed enabled? That was what caused a partial upgrade message for me last :)

---

### Post by talsemgeest on 2008-06-01
Yeah, I did. But all is well now...

---

### Post by Joeb454 on 2008-06-01
:) It's something you should expect with that repo enabled ;)

---


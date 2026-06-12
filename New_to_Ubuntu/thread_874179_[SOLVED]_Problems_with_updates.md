---
title: "[SOLVED] Problems with updates"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by mczonie on 2008-07-29
I recently did a complete reinstall from the CD because my computer was acting buggy, and after I installed the updates, I got a pop up saying "not all updates and changes succeeded. For further details of the failure, please expand the terminal panel below." Then in the panel below, there was all types of mumbo-jumbo, which I have no idea the meaning of. I can't close the pop-up, either.

Anyone know what this means?

---

### Post by perlluver on 2008-07-29
Could you write down some of the errors, or take a screenshot of the problem?  That would help diagnosing the problem.

---

### Post by northern lights on 2008-07-29
Please post the mumbo-jumbo
;)

---

### Post by mczonie on 2008-07-29
> **northern lights said:**
> Please post the mumbo-jumbo
;)

I can't. I tried to copy and paste it, but it wouldn't let me.

---

### Post by mczonie on 2008-07-29
I just went into the update manager again after restarting my computer, and it says it's up to date.

---

### Post by mczonie on 2008-07-29
Now it won't let me close the update manager again.

---

### Post by mczonie on 2008-07-29
OK, I did it again, and this is what it says:

E: gnome-applets-data: subprocess post-installation script returned error exit status 134
E: gnome-applets: dependency problems - leaving unconfigured

---

### Post by steveneddy on 2008-07-29
> **mczonie said:**
> OK, I did it again, and this is what it says:

E: gnome-applets-data: subprocess post-installation script returned error exit status 134
E: gnome-applets: dependency problems - leaving unconfigured

Open up Synaptic, after youclose the update manager, and look for

gnome-applets

and

gnome-applets-data

and right click them and select to totally reinstall.

See if that fixes the issue.

---

### Post by mczonie on 2008-07-29
> **steveneddy said:**
> Open up Synaptic, after youclose the update manager, and look for

gnome-applets

and

gnome-applets-data

and right click them and select to totally reinstall.

See if that fixes the issue.

OK, I opened synaptic, and looked those things up. The box next to them is green, so it looks like they're installed. 

Should I reinstall them just to make sure?

---

### Post by hansdown on 2008-07-29
Yes.

---


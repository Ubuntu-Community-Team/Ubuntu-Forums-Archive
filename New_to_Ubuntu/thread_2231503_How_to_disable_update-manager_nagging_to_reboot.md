---
title: "How to disable update-manager nagging to reboot"
date: 2014-06-26
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-06-26
What happens with 14.04? After a kernel update there is this green thing (the update-manager) keeps popping up nagging me to reboot. Taken a cue from Vista? :)

Is there a way to disable it? Thanks.

---

### Post by newb85 on 2014-06-26
Not sure why yours is green (perhaps you're using a variant of Ubuntu or a different theme), but having Update Manager ask you to reboot after kernel upgrade is certainly not new to 14.04.  Your system can't start using the new kernel (finish upgrading) until you restart.

---

### Post by bapoumba on 2014-06-26
+1, there were kernel upgrades this morning (UTC +2). Kernel upgrades should prompt for a password to install though, so you know.

---

### Post by LastDino on 2014-06-26
Not unless you stop kernel update. Though, like newb85 mentioned, it is not green or even repeating message as if I can't do it immediately, I simply keep it in background. 

Perhaps, you're not using update manager to update?

---

### Post by vasa1 on 2014-06-26
I use the terminal to update and dist-upgrade: I sometimes see things like "ureadahead will be processed on reboot" or something like that (mostly after a kernel update). But that's it. No other cues (or nagging).

---

### Post by Frogs Hair on 2014-06-26
I too had a reboot prompt and on occasion they occur with a new kernel , but not for updates to the currently installed kernel. I was also in the Gnome Shell when I ran the update manager.

---

### Post by monkeybrain20122 on 2014-06-26
Well I know I need to reboot for the kernel update to take effect, but I don't need the thing to popup nagging me every 5 minutes or so. :)

---

### Post by bapoumba on 2014-06-26
> **monkeybrain20122 said:**
> Well I know I need to reboot for the kernel update to take effect, but I don't need the thing to popup nagging me every 5 minutes or so. :)

Do you have the option to "reboot later" ?

---

### Post by philinux on 2014-06-26
Right click software updater icon and click exit.

---

### Post by monkeybrain20122 on 2014-06-26
> **bapoumba said:**
> Do you have the option to "reboot later" ?

Yes, so it nags again later. :)

---

### Post by bapoumba on 2014-06-26
> **monkeybrain20122 said:**
> Yes, so it nags again later. :)
Aww. Had that yesterday, told it I would reboot later and it stayed quiet :)
lubuntu, maybe that makes a difference.

---

### Post by Paulgirardin on 2014-06-26
I get one notification after a kernel update to restart.If I close that I get no further "nags".Running Unity.

---

### Post by LastDino on 2014-06-26
> **bapoumba said:**
> Aww. Had that yesterday, told it I would reboot later and it stayed quiet :)
lubuntu, maybe that makes a difference.

It is same on Unity, gnome and XFCE (my memory about last one there is little blurry).

---

### Post by monkeybrain20122 on 2014-06-26
Hmm.. The latest kernel update nags only once. But I remember all the previous ones, the green thing came up every 5 minutes to nag me to reboot.. Maybe they fix that. I will just mark this as solved

---


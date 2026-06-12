---
title: "Is the gnome-power-manager really needed?"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by dnns123 on 2008-05-18
Is the gnome-power-manager really needed for a desktop?
Desktops don't use batteries...so can the manager be killed from the proccesses?
I don't want to experiment... it might have consequences :P

---

### Post by shifty_powers on 2008-05-18
heh, no it's not needed, got rid of it plenty of times ;)

---

### Post by Happy_Man on 2008-05-18
For better results, go to System --> Admininstration --> Services and uncheck it there. That way, it won't start on boot, either.

---

### Post by Norm24 on 2008-05-18
I noticed that there are two listing for Power Management (acpid) and (ampd).

Uncheck one or both?

---

### Post by Happy_Man on 2008-05-18
> **Norm24 said:**
> I noticed that there are two listing for Power Management (acpid) and (ampd).

Uncheck one or both?
Crap, my bad, I didn't mean in there. I mean the power management daemon in System --> Preferences --> Sessions. Dang, I'm stupid.

---

### Post by Norm24 on 2008-05-18
> **Happy_Man said:**
> Crap, my bad, I didn't mean in there. I mean the power management daemon in System --> Preferences --> Sessions. Dang, I'm stupid.

Thanks for the clarification.

---

### Post by mister_pink on 2008-05-18
I may be wrong, but I was under the impression it was needed. On gutsy I removed it from sessions assuming it wasn't needed, and it had the odd side effect of making it so when I clicked on the shutdown button on my panel, it look over a minute for the dialog to appear. I googled at the time and it seemed to be a common thing.

Edit: I think it was a bug. Probably fixed now - I guess just try it and see - if it causes an issue just turn it back on. Bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078)

---

### Post by Happy_Man on 2008-05-18
Huh. It does the same thing for me. Well, there you have it, I guess you really can't remove it. Unless you don't use the shutdown dialog.

---

### Post by RockinRob2258 on 2008-09-17
Could you shut down from the command line instead of using the shutdown dialog?  Would that fix the problem?  Is this even an issue for people running 8.04, or is it just with 7.10?

---


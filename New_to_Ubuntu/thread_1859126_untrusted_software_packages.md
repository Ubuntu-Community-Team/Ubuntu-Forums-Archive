---
title: "untrusted software packages?"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2011-10-13
Hello,
I'm running 11.10 (via upgrade) and some issues have cropped up:

1 is the update issue. I keep getting an untrusted package error for Adobe Reader.

2. I can't open up any mounted external hard drives or my trash bin via launcher because Ubuntu keeps wanting to open in Ubuntu Software Center.

Any help would be appreciated.

---

### Post by skyzthelimit230 on 2011-10-13
Here's a screen shot

---

### Post by sadaruwan12 on 2011-10-13
I think you have to enable the Ubuntu partner repositories from the synaptic thats why you're getting this.

For the second one I don't know the answer 'cos nerver have come accros such a issue.

---

### Post by mc4man on 2011-10-13
Upgrades will be liable to issues - 

For adobe maybe try this, a bit convoluted but..
In update manager click on 'settings' which will open software sources > Other software
If Canonical Partners is is enabled (likely) then disable it (uncheck

Then because software sources no longer has a reload  back in update manager click on 'check' to reload your sources.
When that completes go back to software sources & re-enable the partners repo, & then again in update manager click on check

Don't know about your other issue, you could try this-
go to ~/.local/share/applications & delete mimeapps.list

---


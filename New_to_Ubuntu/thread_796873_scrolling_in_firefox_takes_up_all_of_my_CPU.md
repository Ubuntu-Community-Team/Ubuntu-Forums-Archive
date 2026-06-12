---
title: "scrolling in firefox takes up all of my CPU"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by holdie on 2008-05-16
So occasionally my computer starts to slow down considerably, so I opened up the system monitor to see how much resources are being used and such.  Basically, everything I do takes up a significant chunk of CPU %, but one thing in particular I noticed is that all of it (100%) is taken up when I'm scrolling in firefox

does anyone have any idea as to why this is happening to my whole comp/just with firefox?

I'm using Hardy with compiz enabled if that makes a difference

---

### Post by jimmy the saint on 2008-05-16
Try this:



There is an easy workaround.

This workaround is successful:
1. Open Firefox 3
2. Disable phishing/attack detection in the security section of the Preferences
3. Close Firefox
4. Make hidden files visible (Locations - Personal folder - View - show hidden files)
5. Delete /home/user/.mozilla/firefox/blahblahblah.default/urlclassifier*.sqlite
6. Open Firefox.
7. There is no next step. You're done. :-)

Greetz, Pjotr.
  It is a fix at bugzilla for a firefox bug that is wellknown and causes firefox to slow wayyy down.  Let me know if this works for you.

---

### Post by oliviacond on 2008-05-16
perhaps is this bug causes this problem.
[https://bugs.launchpad.net/ubuntu/+bug/215728](https://bugs.launchpad.net/ubuntu/+bug/215728)

but the bug has been fixed weeks ago. try to check for update.

if u still have that problem, there's a temporary workaround:
disable phishing/attack detection, close Firefox, delete /home/*user*/.mozilla/firefox/[*profile*].default/urlclassifier*.sqlite , opene Firefox

---

### Post by holdie on 2008-05-17
hmmm, I tried the workaround and it didn't seem to make any significant changes...it seems like this is a problem with other programs as well as firefox, though.  It's just the most obvious with firefox...

ps hmmm just checked my temp during out of these slowdowns and it says it's running at like 70 C right now....damn....

---


---
title: "[SOLVED] Firefox 3 automaticly goes to a url"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by GotNoLife on 2008-06-24
Hi. I started using Ubuntu a couple of months ago - just upgraded Firefox to version 3.

Some times when i scroll pages, via the mouse pad, Firefox tries to open whatever I've got in the copy/paste-memory.

Lets say I have copied "ubuntuforums.org" and I'm reading a news site. If i then scroll down or up the page Firefox will automatically connect to "ubuntuforums.org".

Any ideas on why, and how to solve this issue? :)

---

### Post by jordanmthomas on 2008-06-24
It happens when you middle click your mouse.
Of course, it seems to happen to me when I KNOW I didn't click it.  The best solution I've found is to go to Edit --> Preferences --> Advanced and turn on Autoscrolling.

I'm sure there's a better way, but this stops firefox from loading up new pages on accident.

---

### Post by squaregoldfish on 2008-06-24
This action is bound to clicking the middle mouse button, so you're either being over-zealous with finger pressure on the mouse wheel, or there's a very weak spring in the button, so you're clicking the button when you scroll.

To stop this happening, you can either (a) be more gentle with the mouse wheel, or (b) disable the middle mouse click.

To disable the click, enter about:config in the address bar, and enter middlemouse in the Filter at the top of the page. You should see an option named middlemouse.contentLoadURL - double click the entry to disable it.

Steve.

Kind of beaten to it, but this should help both of you!

---

### Post by jordanmthomas on 2008-06-24
> **squaregoldfish said:**
> middlemouse.contentLoadURL

Ha, I even looked at middlemouse.* before posting and somehow missed that one.  Thanks a bunch, as this fully solves the problem I was having (which seems to be the exact same as OP)

---

### Post by GotNoLife on 2008-06-24
Great!

Thank you for the fast replay! Both of you.

:)

- René

---


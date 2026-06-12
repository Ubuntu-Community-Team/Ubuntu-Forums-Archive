---
title: "Outlook Web Access, Exchange 2007 in IEs4Linux"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by yipperzz on 2008-06-18
Hi, I tried searching and didn't see anything about this.  But I have IEs4Linux installed in Wine so that I can access OWA.  When we were on Exchange 2003, it was using OWA premium fine.  

We recently upgraded to Exchange 2007 and now it's only working in light mode.  It won't let me uncheck the box to use premium.  Anyone else experiencing this?  

If I can't get this fixed, there isn't much of a difference between Firefox and IE since I'm both in light mode.  I tried the User Agent Switcher but it still loads light mode even though I am able to uncheck the box.  Thanks.

---

### Post by steve101101 on 2008-06-18
> **yipperzz said:**
> Hi, I tried searching and didn't see anything about this.  But I have IEs4Linux installed in Wine so that I can access OWA.  When we were on Exchange 2003, it was using OWA premium fine.  

We recently upgraded to Exchange 2007 and now it's only working in light mode.  It won't let me uncheck the box to use premium.  Anyone else experiencing this?  

If I can't get this fixed, there isn't much of a difference between Firefox and IE since I'm both in light mode.  I tried the User Agent Switcher but it still loads light mode even though I am able to uncheck the box.  Thanks.

im not sure, but ies4linux is really only used to test websites in IE.

---

### Post by yipperzz on 2008-06-19
Nevermind I found a solution to it.  I understand what it's for but there are plenty of people out there using IEs4Linux for OWA because there isn't an alternative unless you want to use light mode.  Pretty much it's a crippled Outlook.  

For those of you who may find this on search (keywords: OWA, Exchange 2007, Exchange 07, ies4linux, wine, user-agent )
I had to modify the registry to make it not report Windows 98 which it does by default.  Switching the user-agent to Windows NT 5.1 resolved the issue.  Here is a link that I found:
[http://www.flatmtn.com/article/wine-ie-and-owa-premium](http://www.flatmtn.com/article/wine-ie-and-owa-premium)

---


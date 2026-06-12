---
title: "Prepare for Shipping to End User (oem-config)"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by wyclif on 2008-11-15
Ack!  While doing routine administrative tasks, I made the mistake of scrolling over the menu item "Prepare for shipping to end user" and mistakenly clicked it.

Now, I did not know this, but that runs a script called oem-config.  Before I knew what happened, a pop-up window informed that oem-config would run at next boot (with no option to cancel).  NOT good!

Sure enough, oem-config ran upon reboot after I had to turn the laptop off.  Now I'm terrified I'm going to lose all my settings.  I do not want oem-config to run, nor do I want "oem" as user...

But the System Config memu runs, and I can't back out.  I'm running Hardy on an IBM Thinkpad T40.  I tried dropping into the boot menu at startup, that didn't help.  Anybody?

P.S. I really think it's a bad idea to enable that menu option by default.  It's too easy to run this script by mistake.

---

### Post by shifty_powers on 2008-11-15
afaik it just creates a temporaey "oem" account which would let you create the user account.

i shouldn't have any affect on your already created account and settings...

---

### Post by wyclif on 2008-11-15
Yes, in the shiny UI there are about 4 windows you have to fwd through.  Then I saw that the oem account was only temporary.  But thank you for responding!

I think I'm gonna drop that from the menu anyway.  Should I need to run oem-config intentionally, I can do it from the command line. :)

---

### Post by shifty_powers on 2008-11-15
np, glad to help :D

---


---
title: "Email links non-functional"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by philk949 on 2008-08-31
Hi,
I've just reverted to Firefox 2.0.0.16 from Firefox3, which was hanging and freezing, and now find that links in my emails (Evolution mail client) will not open in my browser.
I've attempted to find something in my settings to remedy the problem, but have so far been unsuccessful.
Would anyone be able to help me with this please?

Thanks

Phil

---

### Post by mevets on 2008-08-31
May want to check your settigns under the Internet tab in System > Preferences > Preferred Applications

---

### Post by philk949 on 2008-08-31
Did that and include screenshot of results. Can't see anything there out of order.

---

### Post by philk949 on 2008-08-31
Had a thought.
Could it be that FF2 is not being recognised as the default browser after uninstalling FF3?

---

### Post by mevets on 2008-08-31
Well see what happens when you type 'firefox' into the terminal. If it says it doesnt exist, run FF2 and see what the name of the process is under gnome-system-monitor (skip this if you already know). Then change the command field appropriately.

---

### Post by philk949 on 2008-08-31
I have sent screenshots of terminal and system monitor.

As you can see, the Sysmon says FF2 is sleeping, yet I am using it to post on this forum.

The terminal , well, you can see what that tells me.
Not sure how to proceed from here.

Phil

---

### Post by mevets on 2008-08-31
The name for it is 'firefox-2' (with the dash). See if that works. If you dont have FF2 installed you can install it by clicking [here]("apt://firefox-2")

---

### Post by philk949 on 2008-08-31
Yes, that worked (firefox-2) and launched the browser, but email links remain inactive.

Phil

---

### Post by philk949 on 2008-09-01
Thanks for your help, mevets, but I've bitten the bullet and gone back to FF3. Had to have those email links.

Thanks again,

Phil

---


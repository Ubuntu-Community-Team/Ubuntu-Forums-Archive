---
title: "[SOLVED] 12.10 64-bit Suddenly Firefox isn't working"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by squakie on 2013-03-23
I know some updates where installed earlier this week - perhaps they have something to do with this:  I try to start Firefox and all that happens is my disk knocks around for 30 seconds or so, and then nothing.  Try it again - same result.  Try from terminal - says another Firefox is already running.  Killed all of those, and just for kicks rebooted, and the problem persists.  Anyone else having this problem and know what I'm either doing wrong or what I need to do?  I haven't installed anything except from the repositories, and I know viruses are pretty much a no-go.  However,  a friend of mine for over 40 years and I recently had it out.  I've been catching heck from his family on Facebook.  One of his brother in-laws is , without going into specific details, works for a large corp and is known nationally for his computer expertise.  I have found some instances on some of my yahoo posts that look like him, and he'd have to have done a lot of work to find my id there.  These problems with Firefox started when all this came to a head.  Hopefully it's just coincidence, but, and I know I'm sounding REALLY stupid here because of how Linux works - the various "rings" if you will of execution and protection, but surely I would have been asked to ok somebody doing something to my Ubuntu install, right?  I'm probably just being paranoid and it's probably just something stupid I'm doing wrong, but I have to ask.

---

### Post by ManamiVixen on 2013-03-23
What you are experiencing is normal. Firefox will do this sometimes and can be annoying. Your best bet is to open it, then kill it if it fails to load and then open it again till it works. If that sounds tedious, there are a few other Web Browsers in the Software Center that work well. Like Epiphany and Chromium.

---

### Post by squakie on 2013-03-23
After many years of use, never had this happen until now.  I've killed it, restarted it, etc., over and over with no luck - it just won't come up even though it claims the process is running.

---

### Post by ManamiVixen on 2013-03-23
It's been happening ever since FF17. Nobody knows why. You might just be unlucky in how long it took to affect you.

---

### Post by squakie on 2013-03-23
also was running fine prior to an update this week.  I would have to assume the update loaded a new update for Firefox  - now at 19.0.2 -  and that new update affected me, but thanks for the thoughts.

---

### Post by squakie on 2013-03-24
To anyone who may be interested:

tonight I went to synaptic package manager and completely removed everything associated with firefox, including firefox itself.  I then used terminal and did sudo apt-get install firefox.  Since having done so, I haven't had any problems yet (knock on wood).  I suspect that one of the updates I got last week wasn't "tested" wtith what ever I had for Firefox previously, so it ended up not allowing Firefox to open the GUI (the app was running, but no GUI).  

At any rate, so far at least, this has solved the problem for me (who knows, I may be back - it may start up again yet).

---


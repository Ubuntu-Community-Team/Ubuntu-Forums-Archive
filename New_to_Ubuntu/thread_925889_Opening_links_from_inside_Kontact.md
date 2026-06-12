---
title: "Opening links from inside Kontact"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-09-21
Hi, all:

I can't seem to open firefox links from inside Kontact.  When someone sends me an email that I'm reading in KMail, I click on it, and I get a bouncing icon, but firefox never actually opens.  It's holding me back from using RSS Akregator.  Any ideas?

---

### Post by tarahmarie on 2008-09-22
bump

---

### Post by tarahmarie on 2008-09-24
This seems to be something that is a matter of settings.  Is it a serious problem?  A bug?

---

### Post by little_penguin on 2008-10-22
This happened to me when I deinstalled Firefox 3 and reverted back to Firefox 2. 

the following workaround might not be the official fix but it seems to do the trick.

Solution: Create a Symbolic Link to the Firefox binary

Assuming you're using Firefox 2:
```
sudo ln -s /usr/bin/firefox-2 /usr/bin/firefox
```

Or if you're using Firefox 3, it would be
```
sudo ln -s /usr/bin/firefox-3 /usr/bin/firefox
```

Hope it works for you.

---

### Post by tarahmarie on 2008-10-26
Well, I no longer get a bouncing icon of nothingness; instead, Kontact tries to open Quanta instead of Firefox.  What do I do?

---

### Post by little_penguin on 2008-10-26
Sorry, I've really no idea about that, but it sounds like some links are screwed up somewhere.
Since this thread is older, not many people will be looking at it, so I suggest you open up a new thread called "Help: Links in Kontact (kmail) trying to open Quanta instead of Firefox" or something similar, to catch attention and hopefully someone can help.

Good luck!

---


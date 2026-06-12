---
title: "How to make flash auto load"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Draw2much on 2008-09-14
Hello there! I've done searches for this and I can't seem to find an answer. 

I currently use Firefox 3 and have flash installed. My problem is that flash will not run automatically. I have to click an ugly gray "start" button where ever there is flash. This gets very annoying in some websites where every page has a lot of flash in it. 

How do I make flash load automatically in my browser?

---

### Post by aloshbennett on 2008-09-14
Do you have flash blocker or similar plugin installed?

---

### Post by Draw2much on 2008-09-15
I have Adblock Plus and Firestarter installed. As far as I know that's it. I'm pretty sure neither of them are the problem. I was thinking there must be a setting some where (maybe in a config file?) that's making it require a manual start. I just don't know where to look.

---

### Post by FuturePilot on 2008-09-15
You most likely have gnash or swfdec installed. Try to remove them if they are installed. You can remove them from the command line if you like
```
sudo apt-get remove --purge mozilla-plugin-gnash swfdec-mozilla
```
Then install the Adobe Flash Player
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Draw2much on 2008-09-15
Thank you! I actually already had nonfree flash installed, which is why I was so confused nothing was working right. I didn't have gnash but I did have swfdec and I guess it was interfering with nonfree-flash.

Once again, thanks! This solved my problem perfectly!

:KS:KS:KS:KS:KS

---

### Post by rbp on 2010-06-03
thanks! Was facing the same problem (almost 2 years later) and that fixed it.

---


---
title: "Spyware?"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by figi22 on 2008-09-27
While surfing a guitar tabs site, clicking on a fake video link (allegedly Steve Earle, but obviously not!) has led to Firefox being locked with pop-up windows: "This page at http:xxl-tube.net says: Please install new version of Video ActiveX Object".  Closing or cancelling just puts it in a loop of getting these messages.  Is it OK to click on "OK", as I assume ActiveX can't get installed on Linux anyway?   Or is there some other way that I can deal with this?   Rebooting doesn't work, as Firefox goes straight back to the same page.  Thankfully I was able to open another instance of Firefox to go to this forum, but I still can't close the other one!

Any help gratefully received.:confused:

---

### Post by mc4100 on 2008-09-27
So the problem is just that you are unable to close Firefox?
Try Alt+F2, type:
```
killall firefox
```
Hit return/enter.
**This will, of course, end the program, so make sure you're not going to lose any unsaved data.**

Edit: If you've rebooted, and it's still happening, then I suppose the above won't help. However, what you can do, is open the file browser, (by going to Places -> Home) press Ctrl+H, and delete (or rename) the .mozilla folder; this allows you to "start fresh", but you will lose bookmarks, saved passwords, etc.,

---

### Post by figi22 on 2008-09-27
That worked great - thanks!! :):)

---

### Post by Northsider on 2008-09-27
I actually had that last night.  Just endless popups that loop when you close one.  Annoying little thing.  Althought it keeps prompting you in a loop, no spyware is being installed.  You just need to kill firefox as stated.

---

### Post by lukjad on 2008-09-27
Try installing adblock in firefox. Also NoScript. When a page gets upity on my I just trun it off. ;D

---

### Post by ready4thebreak on 2008-09-27
> **lukjad007 said:**
> Try installing adblock in firefox. Also NoScript. When a page gets upity on my I just trun it off. ;D

+1. I cannot live without Ad-Block Plus and very little people know that Ad-Block has an additional script blocker that works just like it, except it easier. It's called Ad-Block Plus Element Hiding Helper, just search for it in Firefox Add-Ons.

---

### Post by egwest on 2008-09-27
I've had that happen before, I usually just open the terminal and type in xkill and then click on the browser.
Those sites are very annoying, though funny, the one I usually end up at tells me I have windows xp/vista and that it has detected (x)number of spyware/trojan horses on my computer and I need to install anti-spyware right away and scan my computer.

---

### Post by Nepherte on 2008-09-27
> **figi22 said:**
> Is it OK to click on "OK", as I assume ActiveX can't get installed on Linux anyway?
No harm done, ActiveX only works with internet explorer... As suggested before, with the noscript firefox extension you'll get rid of this in the future.

---

### Post by aimpau on 2008-09-27
+1 Adblock Plus. Enough said. :)

---

### Post by frankleeee on 2008-09-27
> **lukjad007 said:**
> Try installing adblock in firefox. Also NoScript. When a page gets upity on my I just trun it off. ;D

You can also down load toolbar buttons from FF add ons (Mozilla) in the added buttons are noscript accept java on page and rescind it, these are temporary, and don't go into the white list in noscript

---


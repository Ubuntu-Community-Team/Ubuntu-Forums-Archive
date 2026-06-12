---
title: "Firefox Problem"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by gallam on 2008-07-23
All,

I'm new, so if I've miscategorized this post, my apologies.

I've noticed a problem with Firefox 3.0.1 (or at least for me).

It is most prevalent when I am at Yahoo.com, on their main page.  At times, I notice that Yahoo may be slow sending the advertising data to the page, as I can see in the status window at the bottom of Firefox (Reading or Waiting For l.yimg.com, or some other feed).

While it occurs most often on that page, it has happened on others.

Here is the real problem:  Firefox, while waiting for data, then "grays out" and changes the window from color to black & white.  It then goes into a freeze state and I cannot press the back button, the stop button, the reload button.  Nothing.  It is as if Firefox has frozen.

I then have to go to System Monitor and kill Firefox in order to get it to come back online (note that after this has happened, system monitor reports that Firefox is sleeping).

Is there a way to prevent Firefox from getting into this state, so that if it happens again, I can at least press the stop & reload buttons?

Thanks for any help you have!

---

### Post by LowSky on 2008-07-23
try these firefox hacks to try to speed up delivery
[http://netforbeginners.about.com/od/understandyourbrowser/ht/firefoxhack.htm](http://netforbeginners.about.com/od/understandyourbrowser/ht/firefoxhack.htm)
also the is a progrma tha tblocks ads from even showing up called adblock. Its availible in synaptic as well
[https://addons.mozilla.org/en-US/firefox/addon/1865](https://addons.mozilla.org/en-US/firefox/addon/1865)

---

### Post by vikramaditya on 2008-07-23
Not relative to your issue, but here's another tweak (specific to FF3) that may address downloading problems reported by some users.
> Firefox 3...by default scans all downloaded files with any anti-virus software installed on the host machine. Mozilla notes that "in some cases, this may cause a substantial delay in saving the downloaded file."

Firefox 3 users can disable the automatic virus scanning of downloads in Firefox 3 by typing "about:config" in the address bar, scrolling down to the "browser.download.manager.scanWhenDone" listing and setting it [double-click the line] to "false".

---

### Post by billgoldberg on 2008-07-23
Block out those nasty websites in your etc/hosts file.

I think adblock plus can also do that.

The graying out is a compiz fusion thing. It just means the app hasn't responded for a while.

If you just try to close firefox then, a box will pop up asking you to force quit the app.

---


---
title: "firefox flash issues with hardy"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Nephus on 2008-05-16
well, I recently gave up on my ill fated experiment with the LinuxMCE project and went for a clean install of the newest release.  All is well, except for a strange issue with flash in firefox.  If I go to a site, youtube for instance, all flash content is greyed out with a play button in the middle.  If you click it, it loads the flash content, but I've been running into issues where the flash file seemingly breaks because of this.

My question is this: Is this a setting in firefox 3 that can be disabled, or when I was presented the choice to install a few different flash plugins, did I install the wrong one?  Also, how would I go about fixing this.

---

### Post by macaholic on 2008-05-16
What flash plugin do you have installed? Check in either synaptic or firefox.

---

### Post by Nephus on 2008-05-16
all it says in firefox is Shockwave Flash 9.0 r124

I tried installing the restricted extras, but that didn't change anything.  Might still be using the old one.  I've been removing anything that came up in the search for flash in synaptic, but no luck yet.

---

### Post by Nephus on 2008-05-16
Holy crap I fixed it myself!

I found one last thing in synaptic I missed, then told it to reinstall the nonfree plugin.  Bam.  It works now.  You telling me to look into it more got the creative juices flowing.

---

### Post by macaholic on 2008-05-16
> **Nephus said:**
> Holy crap I fixed it myself!

I found one last thing in synaptic I missed, then told it to reinstall the nonfree plugin.  Bam.  It works now.  You telling me to look into it more got the creative juices flowing.
Congratulations, it's always better to figure it out for yourself, even if you do have some help for the forums. The more you troubleshoot yourself, the more you learn about linux and you can even help other people too!

---

### Post by crf on 2008-05-17
There is a pre-release version of the (non free) flash 10 player from adobe -->
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

I tried it, and I think it works much better than the other plugins I've tried.

Put the .so file in your plugins directory (perhaps rename the new plugin, if there is already a file of the same name there) in the .mozilla directory in your home directory. Open firefox, and go to "add-ons" in the "tools" menu and disable your other flash plugin. 

Go to about:plugins and it should say Shockwave Flash 10.0 b218

---


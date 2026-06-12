---
title: "Graphical issues on Facebook.com using Chrome"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by adobrakic on 2012-10-10
I'm using Ubuntu 12.04, 64-bit. This issue does not appear on Windows 7, or Firefox under Ubuntu 12.04, only Google Chrome.

My Google Chrome version is 22.0.1229.94. [Here](http://i.imm.io/HrNu.png) is a photo of some of the graphical issues. I apologize for blurring so much of the photo, I'd like to keep my profile private. Hopefully it gives you guys a good enough idea of the problem. Another issue that happens is when I type, nothing shows up in the text boxes for about 5 seconds or so, and then it finally comes up.

This doesn't happen on any other website, only Facebook.

---

### Post by mac0s9user on 2012-10-10
I just ran it on mine and no problems. My chrome is sightly out of date. version.79 as opposed to your .94. I just updated my chrome and still have had no issues. Try removing and reinstalling chrome in case the install somehow got messed up. Otherwise, I havent a clue

---

### Post by andreeew on 2012-10-11
I have the same problem. (ubu 12.04, chrome 22.0.1229.94)
I tried to clean the cache, remove the extensions, make a whole new user profile, and finaly reinstall the chrome, but i still have this very annoying issue.

I am ran out from ideas.. :(

---

### Post by shaktiman1234 on 2012-10-11
You should try a fresh install of chrome.

---

### Post by adobrakic on 2012-10-11
How would I go about making sure everything is removed when uninstalling Chrome? Would purge remove everything?

--edit--

I reinstalled Chrome, and the problem still persisted. I noticed it on YouTube this time as well. I gave up, and installed Chromium. It seems to work just as well as Chrome should work, and neither Facebook nor YouTube display the graphical glitches anymore. Andreeew, I'd try installing Chromium as well.

---

### Post by andreeew on 2012-10-11
Chromium is working perfectly.
Thanks!

---

### Post by Hell_Keeper on 2012-10-12
Same issue (ubuntu 64bit 12.04 chrome 22.0.1229.94 and ATI video card ;) ) !

---

### Post by Daniel15 on 2012-10-14
I'm experiencing the same issue, with 22.0.1229.94 on Ubuntu 12.04 64-bit using an ATI graphics card. 

I'll try Chromium out. Are you using Chromium from packages, or just building it yourself?

---

### Post by andreeew on 2012-10-15
I installed Chromium from software center.

---

### Post by matthewkris on 2012-10-15
I'm having the same issue. Uninstall/reinstall did nothing. I think it started right when I updated to Version 22.0.1229.92.

---

### Post by gonzalez.rod.a on 2012-10-23
Hi everyone,
I don't know why the status is "solved", the problem still persist, as alternative solution we're using Chromium, really, Chromium is perfect, but the problem is there.

So I join the list.

---

### Post by mode7 on 2012-10-27
Yeah, this isn't solved.
In fact, I've had this problem for quite some time. A few months, at least. I looked a while ago when I first experienced it, but there were no threads about the overall broken-ness.

Chrome works fine under Windows 7 and OSX. But I use Ubuntu 12.04 by far the most, and Facebook is completely broken. Many other sites (Logging into my bank account, for instance) have the empty text box issue. The text never shows up in the text field after any amount of time. I just press enter hoping I typed in the correct username/etc...

I've been using Firefox under Ubuntu, but I much prefer Chrome. I have not used Chromium in some time, which I probably will do so here soon, but I imagine it is also broken.

---

### Post by amadis2009 on 2012-10-28
I've been having this problem with Chrome ever since the upgrade to 22.0.1229.94. Just tried Chromium and it works fine. Tired of all these formatting issues with Chrome. It's happened before where a website updates something and Chrome can't handle the changes so I have to switch to Firefox. I can't say any of these browsers really impress me. It seems I change browsers weekly now for some reason or another problem.

---

### Post by _salem_ on 2012-11-02
I also have this problem. I also get patches of graphics missing on [http://www.smbc-comics.com/](http://www.smbc-comics.com/)

I'd assumed it was a java or flash issue, and tried installing and uninstalling various versions of flash and java with no luck.

If I switch tabs, and then back to the glitching tab, it seems to fix up the graphics and text I have typed will be there.

Glad to know I'm not alone. I guess I'll install chromium for now.

Had/have it on Ubuntu 12.04 and 12.10 64 bit, AMD graphics card, Chrome Version 22.0.1229.94

---

### Post by memzak on 2012-11-03
I know this might be a slightly late response, but using Ubuntu 12.10 (32bit) with an ATI graphics card and I am experiencing the same issues on chrome. Textboxes not showing text typed into them and facebook becoming a complete nightmare. I experience no such issues on firefox or chromium, but it still would be nice to use my default browser without glitches...

---

### Post by SpikeMeister on 2012-11-06
Apparently this is a Flash plugin problem. This fix worked for me:

[http://www.ubuntuvibes.com/2012/07/how-to-fix-rendering-issues-in-google.html](http://www.ubuntuvibes.com/2012/07/how-to-fix-rendering-issues-in-google.html)

---

### Post by bizz101 on 2012-11-09
From: [http://code.google.com/p/chromium/issues/detail?id=135341](http://code.google.com/p/chromium/issues/detail?id=135341)

> Confirm bug on Ubuntu 12.04 x64 with ATI driver 8.96.4 for an ATI Mobility Radeon HD 5000 card using Chrome Stable 22.0.1229.94.

Confirm that using about:flags to disable accelerated compositing does not mitigate bug.

**Confirm that launching via 'google-chrome --disable-accelerated-compositing' does mitigate the bug.**

I'd suggest there's a problem with both the automated blacklist and the about:flags switch.

Also it appears that chrome version 24 has this fixed:

> assuming that FGLRX refers to the version of the driver then the issue should be fixed for you in Chrome 24 (dev channel and soon to be beta).  In the meantime you should be able to bypass the problem by starting chrome with --disable-accelerated-compositing (or installing a newer driver if there is one available).

---

### Post by jasonofx on 2012-12-03
Glad to find this post. Just built a new machine thanks to some NewEgg black friday deals. Quad-core AMD with built-in gpu, 8 gb ram. Thought the problem might have been with 64-bit Ubuntu, haven't used it in years and I remember in it's infancy there were a few bugs to work out, as to be expected. Just glad it's a minor Chrome issue and not a problem with the OS. Using Opera in the meantime, but might use Chromium or the .24 dev release.

---

### Post by sperlyjinx on 2013-01-25
I'm running google-chrome-stable 24.0.1312.56 on Ubuntu 12.04 and can confirm that it is NOT fixed in this version.  However, the workaround (specifiying --disable-accelerated-compositing) mitigates the issue.

---


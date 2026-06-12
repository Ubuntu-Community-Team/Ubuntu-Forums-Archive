---
title: "Firefox back/forward buttons not working"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by zhinker on 2008-11-02
Hi,

I just did a clean install of intrepid on my laptop, and for some reason firefox's back/forward buttons are not working.  Furthermore, all the smart folders in the bookmarks toolbar have dissapeared as well.  I haven't installed any add ons, so I'm not sure why this is happening.

Any help will be really appreciated.

Thanks

---

### Post by darkvampire on 2008-11-02
Maybe try another clean install?
A problem might of occurred during the installation.
If that fails; burn a new Ubuntu CD; there could be a problem with the CD.
If that fails: Use Opera (:

---

### Post by zhinker on 2008-11-02
I'm not sure how I did it, but somewhere in my tweaking I managed to fix it.  Thanks anyways

---

### Post by Onno_vdS on 2009-03-25
I have the same problem rendering FireFox basically unusable. Back, forward not working, location in address bar is not updated while surfing the web (can't see where you are) and while switching between tabs. I lost all my shortcuts on the toolbar. Otherwise it seems functional.

I tried to reinstall but that didn't work. Then I tried to remove and add again that also didn't work. When I tried to remove, it removed only Java which I don't understand. FireFox was still working although Synaptic reported status as deinstalled. It deinstalled Java saying it was necessary but afterwards FireFox was still working but Java was not, which I need for Eclipse and other stuff.

I also tried tweaking, restarting etc but to no avail. For me this is the first big, BIG disappointment after switching from Windows to Ubuntu. To get my favorite browser I have to reinstall Ubuntu it looks like.

I'm not going to do that any time soon so this basically means I will be using Opera next few months until FireFox decides to start working again as suddenly as it stopped working again or until I reinstall Ubuntu.

Another thought I'm having with this, is that it could mean that there is some man-in-middle hacking going on. Anyway I don't trust a browser that cannot report my location in the status bar so I'm switching to Opera?

FireFox on Ubuntu? It might work. :confused:

---

### Post by HammerHed on 2011-10-17
I just encountered the same problem on my Ubuntu 11.10.

The Forward Back buttons would not work, nor the Address bar (shows an older domain name and no other info in the address bar for the url), also cursor shows the Highlight tool no arrowhead.

I went into my home directory then .mozilla/firefox/randomnumber.default/ folder and deleted the following files: places.sqlite and all the files with extensions to that name places.sqlite* 

Then rebooted my computer and restarted FireFox and all is good again.

Strange bug, I never seen it before.

---

### Post by oldos2er on 2011-10-17
Closed, necromancy.

---


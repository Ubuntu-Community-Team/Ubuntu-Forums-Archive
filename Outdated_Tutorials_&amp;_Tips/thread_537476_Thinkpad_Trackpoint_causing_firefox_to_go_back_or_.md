---
title: "Thinkpad Trackpoint causing firefox to go back or forward (Solved)"
date: 2007-08-28
forum: Outdated Tutorials &amp; Tips
---

### Post by fpwind on 2007-08-28
I recently started using firefox again after trying out Epiphany for awhile. Upon returning to Firefox I was frustrated to learn that when i used my Thinkpad T23's trackpoint+middle mouse to scroll up and down as I had it previously configured it was now also causing the brower to jump to the next or previous web page depending on which way I scrolled. After some searching  and was finally able to fix the behavior.  I still haven't determined what caused this to start happening.  I found the fix [here]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint").

Here is the fix
> Vertical Scrolling seems to work out of the box in firefox if you followed the steps above. Anyway, there is a problem when you don't scroll exactly vertical, because horizontal scrolling turns into browser BACK/FORWARD commands. You can avoid this by typing about:config + ENTER in the address bar of firefox. You have to adjust the following options:

mousewheel.horizscroll.withcontrolkey.action = 3;
mousewheel.horizscroll.withcontrolkey.numlines = 1; 
mousewheel.horizscroll.withcontrolkey.sysnumlines = true;

mousewheel.horizscroll.withnokey.action = 0;
mousewheel.horizscroll.withnokey.numlines = 1;
mousewheel.horizscroll.withnokey.sysnumlines = true;

mousewheel.horizscroll.withshiftkey.action = 1;
mousewheel.horizscroll.withshiftkey.numlines = 1;
mousewheel.horizscroll.withshiftkey.sysnumlines = true;


Hope this helps

---


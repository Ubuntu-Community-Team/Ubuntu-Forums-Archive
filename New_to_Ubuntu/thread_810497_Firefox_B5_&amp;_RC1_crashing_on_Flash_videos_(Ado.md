---
title: "Firefox B5 &amp; RC1 crashing on Flash videos (Adobe Flash 9 &amp; 10B)"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by OZFive on 2008-05-28
Well the title says it all.  Ever since upgrading to Hardy I find that Firefox is crashing every once in a while (not all the time) when I open a page with Flash video.

I have tried out....

Hardy, i386
Firefox3 B5 w/ Flash 9
Firefox3 B5 w/ Flash 10B
Firefox3 RC1 w/ Flash 10B

On gutsy with Firefox2 I never had an issue.

Any clues?

---

### Post by spiderbatdad on 2008-05-28
Yes. It does.
Use a different browser?

---

### Post by OZFive on 2008-05-28
Seeing that I have seen many happy people using Firefox3 without this issue (at least no one is complaining about it I have seen) here in the forums.  I figure there might be a different solution than using a diferent browser.

---

### Post by DJ_Peng on 2008-05-28
There are some known issues in the Flash plugin (both version 9 and the beta of 10) with Firefox. I've seen several posts on the MozillaZine Forums (see my sig, check under Firefox Builds as that's where they discuss Firefox 3 until it's officially released) about it, and it seems to be more of an issue with Adobe Flash rather than with Firefox.

---

### Post by philinux on 2008-05-28
It's really weird. I had this and libflashsupport got the blame a while back

I'm still on B5 with flash 10 and libflashsupport installed and it does not crash now.

---

### Post by spiderbatdad on 2008-05-28
> **OZFive said:**
> Seeing that I have seen many happy people using Firefox3 without this issue (at least no one is complaining about it I have seen) here in the forums.  I figure there might be a different solution than using a diferent browser.

[http://ubuntuforums.org/showthread.php?t=734176&highlight=ff3+beta5](http://ubuntuforums.org/showthread.php?t=734176&highlight=ff3+beta5)

[http://ubuntuforums.org/showthread.php?t=759504&highlight=ff3+beta5](http://ubuntuforums.org/showthread.php?t=759504&highlight=ff3+beta5)

[http://ubuntuforums.org/showthread.php?t=788843&highlight=ff3+beta5](http://ubuntuforums.org/showthread.php?t=788843&highlight=ff3+beta5)

[http://ubuntuforums.org/showthread.php?t=808606](http://ubuntuforums.org/showthread.php?t=808606)

[http://ubuntuforums.org/showthread.php?t=794700&highlight=firefox+beta](http://ubuntuforums.org/showthread.php?t=794700&highlight=firefox+beta)

Could keep this up for an hour or so....
Not to mention the ridiculous waste of resources.

---

### Post by ubuntu-freak on 2008-05-28
> **philinux said:**
> It's really weird. I had this and libflashsupport got the blame a while back

I'm still on B5 with flash 10 and libflashsupport installed and it does not crash now.

 
I don't think libflashsupport interacts with v10 beta, as v10 fully supports PulseAudio.
 
To the OP, remove libflashsupport, disable any add-ons and disable the security options in Firefox's preferences. Also, delete the "urlclassifier" files in /home/.mozilla/firefox/default.  
 
Nathan

---

### Post by markbuntu on 2008-05-28
I am using RC1 with flash 9 and having no problems at all. Firefox was unusable to me before getting RC1 because it crashed all the time, flash or no flash. Now, no crash, ever, flash or no flash. Firefox3RC1 and flash9 also now work with compiz no problem.

But I do not have libflashsupport so that is probably your problem.

I really don't want flash 10 now because everything is finally working!!!

---

### Post by jbcano on 2008-06-08
Hi.

Im in firefox RC2 with flash 9.0 and im having the same problem, firefox crashes randomly loading flash videos.... Its bad signal than in RC2 they dont have solved this issue, maybe its a flash problem..........

---

### Post by OZFive on 2008-06-13
I found what seems to be a soultion to the issue!  

It rolls you back to Flash 9, but what the hey, nothing too special about 10 I saw.

it is posted here...


[http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html](http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html)

In a terminal.
> wget [http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb](http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb)

> sudo dpkg -i nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb
> 
sudo apt-get remove --purge flashplugin-nonfree
> 
sudo apt-get install flashplugin-nonfree

Seems to have worked for me so far.  Hope it does for others!

---


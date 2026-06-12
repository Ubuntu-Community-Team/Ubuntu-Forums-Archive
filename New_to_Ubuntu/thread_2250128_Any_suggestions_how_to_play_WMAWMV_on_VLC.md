---
title: "Any suggestions how to play WMA/WMV on VLC"
date: 2014-10-26
forum: New to Ubuntu
---

### Post by Leon_Fernando on 2014-10-26
I have a 32bit Ubuntu 14.04. Can't play WMA/WMV on VLC Crashes on click. Any advice?

---

### Post by Bucky Ball on 2014-10-26
Have you got ubuntu-restricted-extras installed and the third-party software repo enabled? (Software & Updates>Ubuntu Software>Software restricted by copyright or legal issues (multiverse repo).)

---

### Post by papibe on 2014-10-26
Hi Leon_Fernando. Welcome to the forum ):P

You may be missing the CODECS. Open the 'Software Center' and look for the package 'Ubuntu Restricted Extras' and install it.

Hope it helps. Let us know how it goes.

Come here often and have fun.
Regards.

---

### Post by Alireza_Zamani on 2014-10-27
sudo apt-get install [COLOR=#000000]ubuntu-restricted-extras[/COLOR]

---

### Post by mc4man on 2014-10-27
The vlc package(s) will install all vlc needs (exception would be some rare files that require w32codecs
So as far as wmv/wma most should playback, obvious exception would be protected wmv/a

Try from terminal - 
vlc -vv /path/to/problem vid

---

### Post by Rob Sayer on 2014-10-29
I agree ... vlc comes with its own codec libraries, though if you haven't installed ubuntu-restricted-extras you should do it anyway even if it doesn't affect vlc.

Have you installed another media program from an untrusted ppa and removed some of vlc's codecs in the process?  Try purging and reinstalling vlc.

Also, there's a flag in vlc to ignore drm.

You should also install mediainfo-gui and open one of those problem files and use the text mode.  POst results in code tags.  Just because the file extension is .wmv doesn't mean the format of the actual media is any one thing.  The file extension is just a container.

---

### Post by mc4man on 2014-10-29
> **Rob Sayer said:**
> I agree ... vlc comes with its own codec libraries, though if you haven't installed ubuntu-restricted-extras you should do it anyway even if it doesn't affect vlc.
.
Actually for codec support better to suggest ubuntu-restricted-addons or just list the individual gst plugins if user doesn't want flash

---

### Post by andrew.46 on 2014-11-04
> **Leon_Fernando said:**
> I have a 32bit Ubuntu 14.04. Can't play WMA/WMV on VLC Crashes on click. Any advice?

There have been many excellent suggestions and I will add yet another :). The 'crash on click' symptom could represent a bad config file so a good first step is to reset your config to default. From a terminal window:

```

cvlc --reset-config && cvlc --reset-plugins-cache

```

This might be enough to kick start vlc....

---


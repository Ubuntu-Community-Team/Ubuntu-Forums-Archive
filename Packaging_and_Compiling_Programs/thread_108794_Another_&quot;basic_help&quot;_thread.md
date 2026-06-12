---
title: "Another &quot;basic help&quot; thread"
date: 2005-12-27
forum: Packaging and Compiling Programs
---

### Post by TheAnonymousx on 2005-12-27
Okay, so I was on myspace loading pages when I noticed that xmms couldn't play wmv files. No idea how to GET IT to play wmv files (or make firefox notice a different browser...any help there is appreciated) but I did find some plugins on xmms' website to play avi files.

So I downloaded the plug in, and got the buildessentials package and ran ./configure (from the directory that I extracted the files into) only to face this error:
configure: error: *** GLIB >= 1.2.2 not installed - please install first
I've seen this a LOT and read a lot of forums about it but none of them seemed to come to a resolution that helped me. Anyone got an idea on this?
Thankx guys

---

### Post by 23meg on 2005-12-27
Why do you want to play wmv files with XMMS? Did you [install the multimedia codecs]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs")? Also install the mozilla-mplayer package to view videos inside the browser.

---

### Post by timfrost on 2005-12-27
Ubuntu (like most Linux dirstibutions) separates development libraries from the run-time system.

This error indicates that you need to install the development package that glib is associated with.  Ubuntu has both 1.2 and 2.0 installed. The development libraries can be installed with
```

 apt-get install libglib1.2-dev libglib2.0-dev

```

NOTE:  There are bound to be other libraries for which you need the development versions.  Check the documentation for the plugin, to see what it needs, and install the "-dev" version of each such library.

---

### Post by TheAnonymousx on 2005-12-28
Okay so that much is working, and now I'm getting this error: "configure: error: *** GTK+ >= 1.2.2 not installed - please install first ***"

Which packages do I need for this here? Is there an easier way to tell for the future other than posting on here?  Basically I did an apt-cache search for gtk 1.2 and other miscellaneous GTK searches and got a whole lotta results that dinnae help.

---

### Post by Lord Illidan on 2005-12-28
Why XMMS???? Mplayer, Xine and the like are all better suited to playing video files...and more modern too. XMMS is using GTK 1.2, years old.

---

### Post by TheAnonymousx on 2005-12-28
Well that's one of the questions I had as well, how DO I change the default video/file player for firefox? I was trolling through myspace one day and noticed that firefox was trying to load xmms to play the wmv files some people have embedded in their profiles.

---


---
title: "Dell Chromebook, freshly installed ubuntu 14.04 LTS, Anki won't launch"
date: 2014-10-04
forum: New to Ubuntu
---

### Post by alex272 on 2014-10-04
Hi guys,

Just bought a Dell Chromebook and installed ubuntu 14.04 LTS.  However, after I downloaded Anki for ubuntu I can't get the program to open.  The icon appears next to the others, but when I click on it nothing happens... I'm new to ubuntu so was wondering if I am missing something obvious here...?

Thanks!

---

### Post by TheFu on 2014-10-04
[http://blog.jdpfu.com/2013/08/23/common-answers-for-ubuntu-and-linux-issues](http://blog.jdpfu.com/2013/08/23/common-answers-for-ubuntu-and-linux-issues) might be helpful. Lots of links for troubleshooting.

---

### Post by alex272 on 2014-10-04
Thanks for the resource; I checked however and couldn't find anything useful.  Does anyone have any other leads?

---

### Post by chris347 on 2015-02-11
I'm having the same issue.  Samsung Chromebook Ubuntu 14.04.1 LTS

Tried removing and re-installing.  I've had Anki running on this platform previously.  Now it's causing me a bit of grief, as it's the only access to the software I have outside my android phone, which isn't ideal.

---

### Post by TheFu on 2015-02-11
So what are the errors?

I loaded the "anki" package today then started it on my C720 Chromebook running 14.04.1.  Most dependencies than I liked, but still - it works.  Took a few minutes to realize that I had to import anki decks manually, not through the interface. Here's the version I got through aptitude:
```

$ dpkg -l |grep anki
ii  anki                2.0.20+dfsg-2         all          extensible flashcard learning program
```

So far, it is working. Only 20 min of use.

Oh .... and if you aren't seeing any errors on startup - open a terminal and manually run the program. That should provide some sort of feedback that we can used.

---

### Post by chris347 on 2015-03-05
Here's the version:

$ dpkg -l |grep anki
ii  anki                                        2.0.20+dfsg-2                         all          extensible flashcard learning program
ii  libzvbi-common                              0.2.35-2                              all          Vertical Blanking Interval decoder (VBI) - common files
ii  libzvbi0:armhf                              0.2.35-2                              armhf        Vertical Blanking Interval decoder (VBI) - runtime files

And the error on startup:

$ anki
Traceback (most recent call last):
  File "/usr/bin/anki", line 7, in <module>
    import aqt
  File "/usr/share/anki/aqt/__init__.py", line 12, in <module>
    from aqt.qt import *
  File "/usr/share/anki/aqt/qt.py", line 7, in <module>
    from anki.utils import isWin, isMac
  File "/usr/share/anki/anki/__init__.py", line 14, in <module>
    raise Exception("Anki requires a UTF-8 locale.")
Exception: Anki requires a UTF-8 locale.



I checked up on the error and found this:
[https://bbs.archlinux.org/viewtopic.php?id=155883](https://bbs.archlinux.org/viewtopic.php?id=155883)

The issue is solved in that thread, but I'm lost as to how it was solved.

I ran this:
$ localectl set-locale LANG="en_US.utf8"

But still get the same error message.

---

### Post by chris347 on 2015-03-05
I pulled a Homer.

If I had to guess, I'd say the problem was solved by editing /etc/default/locale to include the line:
LANG=en_US.UTF-8

Then run 'sudo update-locale'.  Then log out and back in.

Anki works for me now.  Hope this helps anyone having the same problem.  Thanks TheFu.

---

### Post by bookcrazy on 2016-01-17
I know this is an old thread but I am having the same problem: Anki won't launch. When I try to launch it from the terminal I get the following

> Traceback (most recent call last):
  File "/usr/local/bin/anki", line 5, in <module>
    import aqt
  File "/usr/share/anki/aqt/__init__.py", line 12, in <module>
    from aqt.qt import *
  File "/usr/share/anki/aqt/qt.py", line 6, in <module>
    import sip, os
ImportError: No module named sip




Does anyone have any thoughts?

---


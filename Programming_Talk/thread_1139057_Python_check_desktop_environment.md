---
title: "Python check desktop environment"
date: 2009-04-26
forum: Programming Talk
---

### Post by VCoolio on 2009-04-26
Hi all. I'm having a problem with a python script that is supposed to find out the users desktop environment and act accordingly. To keep it simple I reduced it to this:
```
#!/usr/bin/env python
import sys, os

desktoptype = os.environ.get('DESKTOP_SESSION')

if 'gnome' in desktoptype:
   print 'Gnome!'
if 'kde' in desktoptype:
   print 'KDE!'
else:
   print 'Failed!'
```
It should (in my case) print 'Gnome'! but it doesn't. Any ideas on this? Thanks in advance. Btw, I have python 2.6 and 3.0 on Jaunty.

---

### Post by Namtabmai on 2009-04-26
I believe DESKTOP_SESSION only gets set if a person is running gdm, but I guess you are. ( I'm not and it isn't set for me )

Other than that I think that DESKTOP_SESSION can also be set to default, which your code doesn't catch.

---

### Post by cabalas on 2009-04-26
Have you manually checked what the result is from running

```
os.environ.get('DESKTOP_SESSION')
```

I just tested it on ubuntu 8.10 and it returned 'default', I assume that it will do the same when running it inside KDE on Kubuntu.  So you will also have to take into account what distro you are running.

---

### Post by Namtabmai on 2009-04-26
As I said, I believe that is only set by gdm, so people running Kubuntu probably won't have it set ( they use kdm instead ).

Personally I launch straight into my desktop without using gdm/kdm/etc so I won't have it set either.

Not sure if there is a cleaner way of detecting this info, perhaps checking the process list who be more accurate?

---

### Post by VCoolio on 2009-04-26
Yes, default it is. Thanks, I should have thought of checking the output first. Not sure how to do things now, but this is solved. Thanks for the quick replies. 
Another question: where does it get the 'default' from? Why does it not return gnome or compiz or whatever?
Ah, I see the remark about only gdm setting this. Well, back to the drawing table.

---

### Post by imdano on 2009-04-27
I came across this a while ago ```
def detect_desktop_environment():
    desktop_environment = 'generic'
    if os.environ.get('KDE_FULL_SESSION') == 'true':
        desktop_environment = 'kde'
    elif os.environ.get('GNOME_DESKTOP_SESSION_ID'):
        desktop_environment = 'gnome'
    else:
        try:
            info = getoutput('xprop -root _DT_SAVE_MODE')
            if ' = "xfce4"' in info:
                desktop_environment = 'xfce'
        except (OSError, RuntimeError):
            pass
    return desktop_environment
```Back when I was looking for a way to do it I couldn't find anything out there that was completely reliable, but this has worked pretty well.

---

### Post by Darkblood on 2011-09-05
GNOME_DESKTOP_SESSION_ID is deprecated in recent versions.
Anyone knows a good alternative?

I came up with something, but i don't know how reliable it is.

```

from subprocess import Popen, PIPE
proc = Popen(["pidof", "gnome-session"], stdout=PIPE, stderr=PIPE)
if proc.communicate()[0]:
  desktop_environment = 'gnome'

```

---

### Post by Bodsda on 2011-09-06
I think you may be hitting a dead end here. There is no environment variable that lists exactly what DE/WM you are using. The best you could do is query the process list and use a case statement with the 10 most common ones.
 
For example, you don't currently take into consideration that I might be running something other than KDE or Gnome (with or without compiz) - I could be running IceWM or Fluxbox
 
I cant see anything from the LSB on this - [http://refspecs.freestandards.org/LSB_3.1.1/LSB-Core-generic/LSB-Core-generic/book1.html](http://refspecs.freestandards.org/LSB_3.1.1/LSB-Core-generic/LSB-Core-generic/book1.html)

---


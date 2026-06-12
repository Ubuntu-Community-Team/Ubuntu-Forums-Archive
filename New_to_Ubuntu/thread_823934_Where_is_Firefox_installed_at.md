---
title: "Where is Firefox installed at?"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Psythik on 2008-06-09
I'm trying to add some stylesheets to a few websites I frequent, but in order to do that I need to get to the proper directory.  In Windows, it would be:

*C:\Documents and Settings\<user name>\Application Data\mozilla\firefox\profiles\<profile name>\chrome\*

(That's actually not where Firefox is installed in windows, but where all the data such as extensions and themes go.)

Where would this directory be in Ubuntu?


And while we're on the topic of file structures, why is */mnt/* empty?  My only prior experience with Linux was with Linspire way back when, but if I remember correctly, that was the directory where all the hard drives, partitions, removable media, and optical drives were listed...?  *Computer* doesn't list everything I need...

---

### Post by crossedout on 2008-06-09
> I'm trying to add some stylesheets to a few websites I frequent, but in order to do that I need to get to the proper directory. In Windows, it would be:

C:\Documents and Settings\<user name>\Application Data\mozilla\firefox\profiles\<profile name>\chrome\

ctrl+h to reveal hidden folders.
Then navigate to: /home/.mozilla

> And while we're on the topic of file structures, why is /mnt/ empty? My only prior experience with Linux was with Linspire way back when, but if I remember correctly, that was the directory where all the hard drives, partitions, removable media, and optical drives were listed...? Computer doesn't list everything I need...

Check in /media.

-Xout

---

### Post by Paqman on 2008-06-09
Er, your browser will automatically cache the stylesheets of any sites you visit. Why are you doing it by hand?

EDIT: Unless i've read that wrong and you just want to recover cached stylesheets to have a peek? Which is fair enough. Personally i'd just pull the link out of the page's header and point my browser to it. That way you'll see any CSS they've put in the header, too.

Anyway, all your settings and user data (such as cache) live in your /home folder. In the case of Firefox it'll be /home/.mozilla. Go to your home folder and hit ctrl-H to see hidden files (ie: all the ones starting with a .something)

---


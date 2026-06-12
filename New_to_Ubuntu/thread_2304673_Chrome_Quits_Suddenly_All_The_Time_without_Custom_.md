---
title: "Chrome Quits Suddenly All The Time without Custom Ulimit"
date: 2015-11-28
forum: New to Ubuntu
---

### Post by Jason_Hunter on 2015-11-28
Chrome suddenly just exits all the time and I figured I needed to raise open files with ulimit, referenced here: 

[http://askubuntu.com/questions/162229/how-do-i-increase-the-open-files-limit-for-a-non-root-user](http://askubuntu.com/questions/162229/how-do-i-increase-the-open-files-limit-for-a-non-root-user)

The major question is why should I be editing text files to get this done?

Isn't 1024 quite low default value?

I can't imagine I'm in the few who has to do this?

Chrome has a limit on open tabs and even with that limit, I manage to hit that limit. 

What gives?

---

### Post by Geoffrey_Arndt on 2015-11-29
Editing text files in /etc. (and other dirs in Linux) was deemed to be a more reliable and working solution to a central db of config files and pointers such as in the Windows registry.

Have your seen this?    [https://code.google.com/p/chromium/issues/detail?id=169802](https://code.google.com/p/chromium/issues/detail?id=169802)

---


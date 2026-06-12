---
title: "Misbehaving runleve"
date: 2015-08-23
forum: New to Ubuntu
---

### Post by sam32 on 2015-08-23
I'm working on a fresh install of Ubuntu 14.04.3 and have gotten my runlevel messed up. I set it to 2 temporarily, then went to change it back, and found that my system no longer respected the default value.

I set the default to "quiet splash" following the directions here: [http://ubuntuforums.org/showthread.php?t=1688953](http://ubuntuforums.org/showthread.php?t=1688953) (a little more than half way down the page) and rebooted, but got a command-line interface.

Then I tried to use the old way, and created a file /etc/inittab and added "id:5:initdefault:", rebooted and got the same result.

The mysterious part is that running "who -r" tells me the runlevel is 5, but I'm still getting a command-line interface. Any suggestions for where to start with this issue?

---

### Post by sam32 on 2015-08-24
I just decided to reinstall.

---


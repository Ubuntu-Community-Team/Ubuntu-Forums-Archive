---
title: "rc.local keyboard fix"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by vcinaba on 2014-03-06
Hi guys, I`m a newbie ubuntu user and I need some help to make a fix.

Its simple, I have only one keyboard configuration (br), but when I boot my computer my keybourd changes back to US config.

If I use ```
setxkbmap -layout br
```, the problem is solved. But when I add this code to rc.local, nothing happens.

My rc.local:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/bin/setxkbmap -layout br

exit 0
```

how can I do this?

Thank for all help, and sorry for my english.

---

### Post by phidia on 2014-03-06
In CLI > sudo sysv-rc-conf is rc.local enabled? If not [see this]("http://askubuntu.com/questions/9853/how-can-i-make-rc-local-run-on-startup"). Good luck.

---

### Post by steeldriver on 2014-03-06
Isn't the problem likely to be that the X server has not started at the time that the rc.local file gets executed? You might want to look at executing setxkbmap from elsewhere - such as the user's desktop startup applications.

---


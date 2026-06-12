---
title: "Close Firefox automatically after idling for 10 minutes."
date: 2013-12-04
forum: New to Ubuntu
---

### Post by matthew.walker on 2013-12-04
Hi All,

I have searched extensively for an answer to this but nothing I have found has quite worked how I want it to.

Basically i'm currently setting up a public access machine using Ubuntu 12.04 LTS and want to set Firefox to close automatically if it is left idling for 10 minutes, I have found various Kiosk add-ons for Firefox but none of them actaully close down Firefox they only revert back to the set homepage and close any open tabs but I want the user to be able to see the desktop icons I have setup. 

I did read into scripts that could be set to do something like this but I wouldn't know where to start. :?

Thanks

---

### Post by Impavidus on 2013-12-04
One suggestion (and maybe not the best): use a script to listen to the screen saver (xsceensaver-command -watch) and use kill to send firefox the SIGTERM whenever xscreensaver-command outputs BLANK.

---

### Post by vasa1 on 2013-12-04
I think a solution may be difficult. Who knows what browsers do when *we* think they're idling.

---

### Post by matthew.walker on 2013-12-04
> **Impavidus said:**
> One suggestion (and maybe not the best): use a  script to listen to the screen saver (xsceensaver-command -watch) and  use kill to send firefox the SIGTERM whenever xscreensaver-command  outputs BLANK.

I was thinking along the lines of this too but i'm a total scripting n00b, could someone give me pointers on how I could do this please?

---

### Post by jimmyh1972 on 2013-12-05
watch this link [http://forums.gentoo.org/viewtopic-t-609062-start-0.html](http://forums.gentoo.org/viewtopic-t-609062-start-0.html)
you can switch the shutdown to kill firefox if idle time is true

---

### Post by stinkeye on 2013-12-05
Install xautolock....
```
sudo apt-get install xautolock
```

> xautolock - fire up programs in case of user inactivity under X

**-time**
 Specifies the primary timeout interval. The default is 10 minutes, the minimum is 1 minute, and the maximum is 1 hour. 

**-locker**
 Specifies the locker to be used. The default is xlock. Notice that if locker contains multiple words, it must be specified between quotes. In order to use your PATH to locate the program, xautolock feeds the locker command to /bin/sh, so it should be understandable for whatever shell your /bin/sh is. Because this typically is a Bourne shell, ~ expansion most likely will not work.

```
#!/bin/bash

xautolock -notify 10 -notifier 'notify-send -i firefox "Firefox will close in 10 seconds"' **-time 10** -locker "pkill firefox"
```

For a quick 1 minute idle time test use **-time 1**

---


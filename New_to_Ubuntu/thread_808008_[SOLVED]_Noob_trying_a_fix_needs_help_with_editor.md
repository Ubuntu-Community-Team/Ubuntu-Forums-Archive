---
title: "[SOLVED] Noob trying a fix needs help with editor"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by ndo on 2008-05-26
Hi.
I've installed HH 8.04 64-bit on my Acer Aspire 5100-5840 with AMD Turion 64x2, and have been trying to get my Atheros AR5007EG Wireless card to work. I've googled the **** out of this, found and followed a few guides, still no luck but one last thing I'd like to try:
[http://ubuntuforums.org/showthread.php?t=490800](http://ubuntuforums.org/showthread.php?t=490800)

Problem is, I don't know wtf this guy is talking about - I open up the text editor (default one), load up boot/grub/menu.lst, make the changes, but when I go to save the file I get an error message:

"Could not save the file /boot/grub/menu.lst.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again"

How am I not "allowed" to save this file? Can you not make changes to menu.lst in 8.04? Any help is appreciated - I'm learning this as I go along, and getting desperate to get my wireless working. Thanks

---

### Post by Joeb454 on 2008-05-26
From a terminal run ```
gksudo gedit /boot/grub/menu.lst
``` and make the changes, then you should be able to save it :)

---

### Post by Maestro23 on 2008-05-26
That file is owned by root, so you need root priveleges to edit it.  Using gedit, it would be as follows:

> gksudo gedit /boot/grub/menu.lst

More about RootSudo: [https://help.ubuntu.com/community/RootSudo?highlight=(RootSudo](https://help.ubuntu.com/community/RootSudo?highlight=(RootSudo))

---

### Post by n0wje on 2008-05-26
Not an expert but try this link for your wireless card it might help if you haven't been there before. [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

---

### Post by ndo on 2008-05-26
thanks guys, for the answer and for the link to info - I managed to trial and error my way through by opening "joe" as a su and bumbling through the horrid interface, your way is so much better!

To the other guy, I appreciate the link- I've followed all those steps (even some in the comments, also) and still nothing. I'll just keep trying, I guess - should be educational.

---


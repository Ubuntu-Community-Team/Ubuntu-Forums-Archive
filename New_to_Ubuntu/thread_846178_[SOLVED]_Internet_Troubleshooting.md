---
title: "[SOLVED] Internet Troubleshooting"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Louis de Broglie on 2008-07-01
Hello,

I am having internet problem. When I open firefox and type the address, it seems to wait forever:confused:

I don't have such problem if i restart the pc and type again. But after using the pc for sometime, the problem happens again:confused:

So it seems that if I keep the internet idle for some time, this problem happens:(

I used to have this problem in fedora 9 too.

Thanks.

---

### Post by Canis familiaris on 2008-07-01
Try disabling IPv6.
This may help:
[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

---

### Post by Louis de Broglie on 2008-07-01
Thanks.:D

One more information, I pinged and i get echo. But no page loads.:confused:

I am gonna try that.

---

### Post by Louis de Broglie on 2008-07-01
Hey, that one is quite confusing:confused:

Can u be a bit more specific about disabling ipv6 ?:)

---

### Post by zakirs on 2008-07-01
have you tried this > There's an easy way: instead of changing aliases file, create fie named bad_list in /etc/modprobe.d containing this line:
Code:

alias net-pf-10 off

Now reboot and voila, no IPv6 on your system!

This method will work even if /etc/modprobe.d/aliases get replaced at some update.

---

### Post by Louis de Broglie on 2008-07-01
How to create that file?:)

When I write click to create documents, it greys out. Meaning i don't have permission to write here.:confused:

---

### Post by Tatty on 2008-07-01
```
gksu gedit
``` will open up gedit with sudo privilages

---

### Post by Louis de Broglie on 2008-07-01
Thank you man:D It worked. Ubuntu rocks.:D:D

---

### Post by Tatty on 2008-07-01
Excellent, Its great when things work.

I recommend you read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for information on permissions and sudo.  Good luck!

---

### Post by Louis de Broglie on 2008-07-01
Nice.:)

I created the bad_list then i queried for ipv6 in the terminal and it still showed some output. Then I commented out the line in aliases and then it worked.:D

Should I delete the bad_list file now?:)

---

### Post by zakirs on 2008-07-02
great to know it worked .... if it is working now then leave it alone :D try reading ubuntuguide :D

---

### Post by Louis de Broglie on 2008-07-15
Well, the problem persisted and i have figured out the key reason. Check it out for solution :

[http://ubuntuforums.org/showthread.php?t=860155](http://ubuntuforums.org/showthread.php?t=860155)

Enjoy!:popcorn:

---


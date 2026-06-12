---
title: "Lost CHARSET for English"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by misterfixit on 2008-06-20
After last update, Ubuntu 8, I rebooted and everything after the initial Ubuntu splash screen came up with those rectangular boxes which represent unknown character set.

I dropped to command line and did sudo charset 431 and all the others I could find, but no joy.

I tried apt-get to repair, rebuild, update, upgrade, with negative results;

I used apt-get to load and install kde and then tried to reboot with kde as choice; same results.

Need help as follows; I will do all of this from the command line:

1.  Correct chmod settings for /home/user;

2.  Rebuilt entire character set or fix broken character sets;

3.  Somehow X has become unstable; I've tried the rebuild option from the "rescue" selection from grub, with negative results; how to rebuild/replace?

4.  Splash screen now is the KDE4 screen which is OK, and menu shows various start up selections per usual.  When I get charset back and x fixed, I'll go back to Ubuntu.  This is NOT a kde problem, IMHO

All of my files are backed up, of course and reside on another separate /dev/sda anyway; I've copied /home/user complete over to the other drive to preserve it.

Sure hate to think that I would need to do a complete reinstall like windows -- somehow I don't think this is required and I can fix from within system.

I wish there was a kind of "apt-get 'rebuild the system with choices" option.

This problem is not urgent, since I have other Ubuntu boxes I am using;  but would like to get in there and fix things asap.  

Thanks for help,

Dave

---

### Post by misterfixit on 2008-06-21
Bump ne-one?

---

### Post by nowshining on 2008-06-21
in the terminal sudo /bin/bash and type out ur pw as normal - don't worry it won't show as u type and issue the following:

pango-querymodules > '/usr/local/etc/pango/pango.modules'

---

### Post by misterfixit on 2008-06-21
> **nowshining said:**
> in the terminal sudo /bin/bash and type out ur pw as normal - don't worry it won't show as u type and issue the following:

pango-querymodules > '/usr/local/etc/pango/pango.modules'


Hi, thanks for the reply.  I had already tried that and results were no pango.modules exist.  Hummmm now that might be a problem ...

Ideas?

Thanks again for your courtesy,

Dave

---

### Post by unutbu on 2008-06-21
Perhaps use the command
```
tail -n100 /var/log/dpkg.log
```
to see what were the last few packages upgraded, installed, removed or purged.

Perhaps the needed package was removed?

---

### Post by nowshining on 2008-06-22
try re-installing pango.

edit:

try re-installing the language base of ur country.

once done

sudo locale-gen

logout and backin.

---


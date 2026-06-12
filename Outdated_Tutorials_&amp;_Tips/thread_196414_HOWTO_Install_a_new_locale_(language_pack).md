---
title: "HOWTO: Install a new locale (language pack)"
date: 2006-06-14
forum: Outdated Tutorials &amp; Tips
---

### Post by miahfost on 2006-06-14
**HOWTO install language support for Dapper**

I installed Swedish language support on my Dapper Server (LTS), here is how I did it. First I went to the /usr/share/locales directory;

$ cd /usr/share/locales

In that directory is a script to add a new locale or language pack. I knew I wanted sv_SE which is the pack for Swedish. If you want to find out which language pack to install you can look at the /etc/locale.alias file. To install Swedish language support on Dapper I ran this command;

$ ./install-language-pack sv_SE

Then I ran dpkg-reconfigure like this;

$ dpkg-reconfigure locales

It saw that I added the Swedish language pack and support for Swedish was enabled on my server.

---

### Post by radddi on 2010-07-21
Thank you, Thank you, Thank you, Thank you!! :D:D

PS: why isn't this sticky? :popcorn:

---

### Post by lisati on 2010-07-21
> **radddi said:**
> Thank you, Thank you, Thank you, Thank you!! :D:D

PS: why isn't this sticky? :popcorn:

Perhaps because it's a 4-year old tip relating to a 4-year old release of Ubuntu.

---


---
title: "Upgrade distribution via webmin"
date: 2014-01-23
forum: New to Ubuntu
---

### Post by Sapph1r3 on 2014-01-23
Hi there,
I am learning to look after an ubuntu box and it has been decided to upgrade it from the current version.
This box is accessed remotely via webmin and there is an option in System | Software Packages > Upgrade mode.
Does this upgrade the version/release, e.g. 11.10 to 12.04?
Excuse me if I'm not using the correct terminology...I am really an Ubuntu noob.

---

### Post by justleen on 2014-01-23
No, this wil only update the webmin packages (like apache etc), not your OS (ubuntu).

See [http://www.webmin.com/updates.html](http://www.webmin.com/updates.html) for a list of updates/versions

---

### Post by Sapph1r3 on 2014-01-24
Thanks for the response.
I found this on the Webmin Wiki...which is a bit old:
When this option is set to Yes, your Debian system will be upgraded to the latest distribution release when the form is submitted.
When Yes is selected, the command apt-get upgrade-dist will be run. 
Doesn't that command do the OS version upgrade?

---

### Post by justleen on 2014-01-24
ehmm. Yes, it does..

Funny you digged that up, I was looking at the same Webmin docs..

Keep in mind it will need to upgrade through all versions though. 11.04 -> 11.10 -> 12.04 etc.

---

### Post by Sapph1r3 on 2014-02-07
Went with the upgrade via terminal, to be safe.
All went well except for one incident when the machine became unresponsive 2 days after dist upgrade.
It has been stable since apache updated, but monitoring.
This can be closed :)

---


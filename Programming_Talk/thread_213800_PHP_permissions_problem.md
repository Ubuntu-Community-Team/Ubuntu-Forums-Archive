---
title: "PHP permissions problem"
date: 2006-07-11
forum: Programming Talk
---

### Post by bieber on 2006-07-11
Okay, so I have PHP and Apache installed on my machine.  Problem is, I can get PHP pages working fine if I put them in /var/www, but if a file is in a user's public_html directory, trying to load it always gives a 403 (permission denied) error, even with all permissions on the file and directory set to their lax-est.  Am I missing something in a configuration file or something to that effect?

---

### Post by ifokkema on 2006-07-12
> **bieber said:**
> Okay, so I have PHP and Apache installed on my machine.  Problem is, I can get PHP pages working fine if I put them in /var/www, but if a file is in a user's public_html directory, trying to load it always gives a 403 (permission denied) error, even with all permissions on the file and directory set to their lax-est.  Am I missing something in a configuration file or something to that effect?
Hi,

Problems like these are always caused by little things you overlooked. Don't worry, I've had this a million times, too.
Check out the apache error logs. If it's not in the file, it's in one of the upstream directories. If the file is readable by all, is the directory it's in? And the directory above that one? Check all directories, all up to the permissions of /home.

Good luck!

---


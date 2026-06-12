---
title: "PHP with CURL in cli mode"
date: 2007-09-21
forum: Programming Talk
---

### Post by jonathon on 2007-09-21
I have a php script that works perfectly under apache, and phpinfo() shows curl available, which is required by the script.  However, running this:

> php -r 'phpinfo()'

from the command line does *not* show curl as being available.  That section is skipped.  I tried adding curl.so to /etc/php5/cli/php.ini, but it didn't seem to make a difference.  curl_init() is still undefined when my script is run from the command line.

Thanks in advance!

---


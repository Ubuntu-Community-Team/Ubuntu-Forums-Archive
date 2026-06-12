---
title: "need to use php 5.6 on 16.04 but can't get it to stop using 7.0"
date: 2016-05-02
forum: New to Ubuntu
---

### Post by soaringeagle2 on 2016-05-02
i'm pretty new to ubuntu and trying to get a server online with a very near deadline
(should really have test sites working tonight)
i think many sites are not likeing php 7 in fact even the phpinfo script wont run!
i saw many tuturials for running 7 and 5.6 and switching back and forth
but even though it says  7.0 is disabled and 5.6 enabled php -v still shows 7.0 as the active php

---

### Post by gnusci on 2016-05-02
Did you try removing/purge both and then install 5.6.

---

### Post by soaringeagle2 on 2016-05-02
actually now I'm not sure that is the issue i get this error in web console
 Invalid tag start: "<?". Question marks should not start tags
like its just not processing php at all

but what would be the best way to remove php entirely
then reinstall 5.6 i do know a couple sites are not yet 7.0 ready
but that doesn't explain why even phpinfo fails

---

### Post by mcduck on 2016-05-03
If even phpinfo() fails, then it really can't be a problem with PHP7, sounds more like some issue with Apache configuration. Try running *a2dismod* to disable PHP, and then *a2enmod* to enable it again. Also of course make sure you have the *libapache2-mod-php* installed and not just the command-line PHP...

When you get the phpinfo to work correctly, if you still have issues check Apache logs. I did notice some things were moved to separate packages so when upgrading my server from 15.10 to 16.04 I had to install some things separately (for example simpleXML support which now requires separate *php-xml* package.)

---

### Post by tdawgf on 2016-05-05
Check your apache or nginx configurations. It is entirely possible that your bash profile is set to php 7 but your webserver is using php 5.6. I deal with this all the time on my Mac only in reverse. If you need help with it let us know so we can get back to you.

---


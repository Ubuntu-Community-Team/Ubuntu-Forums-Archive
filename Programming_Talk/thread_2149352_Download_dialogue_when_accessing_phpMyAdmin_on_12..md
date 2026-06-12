---
title: "Download dialogue when accessing phpMyAdmin on 12.04"
date: 2013-05-28
forum: Programming Talk
---

### Post by untarded on 2013-05-28
I just performed a clean install of 12.04, Virtualmin 4.0 GPL and phpMyAdmin.  Everything runs fine except when I try to access mydomain/phpmyAdmin i'm getting the download dialogue prompt.  
 
I've tried the solution proposed here [http://ubuntuforums.org/showthread.php?t=1531416](http://ubuntuforums.org/showthread.php?t=1531416):

> [COLOR=#000000]*Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5. It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php.*[/COLOR]

[COLOR=#000000]*You may also need to actually enable it, by doing sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart. If sudo a2enmod php5 returns "$ This module does not exist!", you should purge (not just remove) the libapache2-mod-php5 package and reinstall it.*[/COLOR]

[COLOR=#000000]*Be sure to clear your browser's cache before testing your site again.*[/COLOR]

but this is not the cause of the issue.

Any ideas how to fix this?

---


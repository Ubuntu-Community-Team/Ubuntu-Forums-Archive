---
title: "chown command, what it means"
date: 2015-11-11
forum: New to Ubuntu
---

### Post by houmingc on 2015-11-11
sudo chown -R :www-data /var/www/html/wp-content/uploads

understand chown command is used to change owner and grou
Can someone explain the command for the above?
owner:group

---

### Post by SeijiSensei on 2015-11-11
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Users can belong to groups.  

The version of the command you give, with only ":www-data" and not "user:www-data" changes only the group ownership to www-data.  (It is then equivalent to the chgrp command.) The "-R" means "recursive" and tells chown to change the ownerships on all file and directories below /uploads/.  In WordPress these directories are dated by year and month.

Hopefully wherever you found this command also says to turn off write privileges for the www-data group.  The primary member of that group is the "www-data" user.  The Apache web server runs with that user's permissions.  If the www-data user can write into the WordPress tree, a rogue script can trick the application into writing arbitrary content onto the site and defacing it.

My WordPress implementations are owned by an ordinary user and group www-data, with only the user having write permissions.  This method will block updates and add-ons from being installed however.  So I wrote a simple script to change the permissions before I run updates like this:
```

#!/bin/sh
chmod g+w wp-admin wp-includes wp-content -R
chmod g+w *
echo "Run update now"

```
I run this at the top of the wordpress tree which would be /var/www/html in the example you give.  After I've completed the update I run
```

#!/bin/sh
chmod g-w wp-admin wp-includes wp-content -R
chmod g-w *

```
to restore the site's security. The one exception is the uploads directory.  On my server that is owned by the www-data user so I can upload images and other media.  I've manually turned off write permissions in the sub-directories prior to 2015 as an added security measure.

---


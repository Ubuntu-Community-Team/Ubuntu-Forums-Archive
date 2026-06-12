---
title: "apache www-data permissions and PHP &quot;failed to open stream&quot; error"
date: 2012-05-25
forum: Programming Talk
---

### Post by arrynflynn on 2012-05-25
LAMP lovers, HELP! I'm confused. This works fine with my apache2/PHP config:

```
% pwd
% /srv/www
% chown www-data:webmins index.php
% chmod u=r,g=,o= index.php
% ls -l | grep index*
-r--------  1 www-data webmins   19 2012-05-24 20:05 index.php  // runs on localhost
```

BUT, if I add the user www-data (apache2 user, I think?) to the group webmins and change permissions to allow group read, like this:
```

% chown root:webmins index.php
% chmod 040 index.php
% usermod -aG webmins www-data
% groups www-data
www-data : www-data webmins
% ls -l | grep index*
----r-----  1 root     webmins   19 2012-05-24 20:05 index.php  // fails
```

The whole thing fails and I get a PHP "failed to open stream: Permission denied" error. What am I missing? I thought that by adding the www-data user to the group webmins, and then giving webmins read access would be essentially equivalent to the previous config. Where did I go wrong? I must just have a misunderstanding. Please help!

PS: It might be worth noting that I have the SGID bit set on /srv/www so that the group of any folder created under it is by default set to webmins.

```
% ls -l /srv | grep www
drwsrwsr-x 5 www-data subversion 4096 2012-05-20 08:03 svn
drwxrws--- 4 www-data webmins    4096 2012-05-25 12:34 www
```

---

### Post by Bachstelze on 2012-05-25
What's in the script?

(Also, 040 is ridiculous. You do know that there is no point in setting the owner permissions to 0 because the owner can always change the permissions back, right?)

---


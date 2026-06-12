---
title: "[SOLVED] Script works but NOT in bash script file."
date: 2008-11-14
forum: New to Ubuntu
---

### Post by niiklas on 2008-11-14
Hello!

this is my script file:
```

#!/bin/sh
#run testlink
php -f /path/to/file/index.php
#sync live folder.
sudo rsync -av /path/to/file/playlists /path/to-file/playlists

```

When i run: 
```

php -f /path/to/file/index.php

``` 
in termninal it works but in the script i get following error:
```

root@server:/home/niklas# ./scriptname.sh
Warning: include_once(include/classes/database.class.php): failed to open stream: No such file or directory in /path/to/file/include/config.php on line 15

Warning: include_once(): Failed opening 'include/classes/database.class.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /path/to/file/include/config.php on line 15


Fatal error: Class 'Database' not found in /path/to/file/include/config.php on line 17



```

---

### Post by kpkeerthi on 2008-11-14
Change Line#1 to
```

#! /bin/**bash**

```
and try again.

---

### Post by niiklas on 2008-11-14
> **kpkeerthi said:**
> Change Line#1 to
```

#! /bin/**bash**

```
and try again.

i tried that but it gives the exact same error. :S

---

### Post by olejorgen on 2008-11-14
Are you sure "php -f /path/to/file/index.php" works when you run it from eg. you home folder?

If "database.class.php" is in "/path/to/file/include/classes/database.class.php" it will only work if current directory is "/path/to/file/"

You could try to add "cd /path/to/file/" at the beginning of your script

---

### Post by niiklas on 2008-11-14
it was something wrong with my php script that has never caused problems before now. SOLVED

Olejorgen, kpkeerthi. Thank you both for your time.

---


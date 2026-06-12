---
title: "who should own files."
date: 2013-12-05
forum: New to Ubuntu
---

### Post by wlraider70 on 2013-12-05
I have a group of php files. I copied them from one server to another. 

On the new server they are all owned by "root".
```

-rw-r--r--  1 root root   3164 Nov 17 08:51 GroupDelete.php
-rw-r--r--  1 root root  11517 Nov 17 08:51 GroupEditor.php

```


However on the old server most of them have a number
```

-rw-r--r--  1 255790  600  3164 Jun  7  2010 GroupDelete.php
-rw-r--r--  1 255790  600 11088 Jun  7  2010 GroupEditor.php

```


So my questions, who should own files in general, who should own php files.
What difference does it make in the end?
I am the only person using the machine.

---

### Post by newbie-user on 2013-12-06
Those permission sets and ownerships look about right for php files. I'm assuming these are on a web server somewhere? 

In general, the owner of the file should be the only one who can read/write/execute a file, so rwx------. In the case of web documents, those files need to have read access for everyone, so rw-r--r-- is generally what you would see, since anonymous users accessing your web server need to be able to view the web documents. If those php files should not be visible by the general public, then you might want to change the permissions to 640 instead of 644.

---


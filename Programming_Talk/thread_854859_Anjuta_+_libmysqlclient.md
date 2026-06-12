---
title: "Anjuta + libmysqlclient"
date: 2008-07-09
forum: Programming Talk
---

### Post by patryk77 on 2008-07-09
Hello,

I am trying to get Anjuta to include MySQL client libraries, but I can't get it working.

```
#include <my_global.h>
#include <mysql.h>
#include <my_getopt.h> 
#include <mysql_com.h> 

```

Like this it can't find the libraries... If I change it to <mysql/my*.h> it finds the correct files, but has problems locating the files that these headers also include.

If I switch into the Project view on the right side (where the list of files is), and I right-click on the executable that is created, I can add libraries, and change some of the other flags.

Is that where I should be adding the include directories, and the libraries? Thanks

---


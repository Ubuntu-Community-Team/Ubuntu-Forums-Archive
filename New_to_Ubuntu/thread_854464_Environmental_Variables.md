---
title: "Environmental Variables"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by skylar.sutton on 2008-07-09
All right... where did I goof this up? 

I'm trying to nest env. variables in Ubuntu 8 and getting no where with it. I'm essentially trying to replicate this functionality from windows:

SET APPS_ROOT = /apps
SET MY_APPLICATION = %APPS_ROOT%/MyapplicationsLocation

echo %MY_APPLICATION%
/apps/MyapplicationsLocation

I've modified the etc/environment file to have the following:

export ANT_HOME=/projects/common/env/apache-ant-1.7.0
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:$ANT_HOME/bin:

If I open a terminal and echo ANT_HOME I get what I'm expecting, but if I echo PATh I get the literal string listed above. It is not evaluating the $ANT_HOME part of the string. 

Thanks for the help

---

### Post by sdennie on 2008-07-09
Rather than use /etc/environment for this, you may want to add it to the bottom of /etc/bash.bashrc (if you want all users to have that in their path) or ~/.bashrc.  Also, you may want to do it like this:

```

export ANT_HOME=/projects/common/env/apache-ant-1.7.0
export PATH=${PATH}:${ANT_HOME}/bin

```

That's sort of building on the idea you were trying by setting the path to $PATH and appending your new directory.

---

### Post by skylar.sutton on 2008-07-09
Works like a charm. Thanks vor.

---


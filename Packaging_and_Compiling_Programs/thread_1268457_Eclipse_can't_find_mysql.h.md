---
title: "Eclipse can't find mysql.h"
date: 2009-09-17
forum: Packaging and Compiling Programs
---

### Post by zjunkie on 2009-09-17
I'm having a bit of trouble building some source code that uses mysql. Eclipse is saying that it has an "unresolved inclusion: <mysql.h>"

I have installed libmysqlclient-dev and the .h file is under /usr/include/mysql/mysq.h

Is there an environment variable that I am missing?

---

### Post by dinxter on 2009-09-27
one of the default paths included is /usr/include so the line would be
#include <mysql/mysql.h>
or you can add the directory /usr/include/mysql to eclipse in project->properties->c/c++ build->settings
to the various compilers/linkers in which case your previous line would work

---

### Post by mayankjoin on 2013-01-28
Thanks!!!

---

### Post by nothingspecial on 2013-01-28
Old thread.

Closed.

---


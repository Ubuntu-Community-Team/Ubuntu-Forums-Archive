---
title: "Shell scripting help"
date: 2006-02-04
forum: Programming Talk
---

### Post by spyke01 on 2006-02-04
hi guys, im new to shell scripting, and i was wanting to know if someone can show me how to make a script to automated doing some apt-get installs

i want to make a script that will automatticly install apache, php, ftp, and mysql
and automatticly anser the "do you really want to unpack and install this program?" question

---

### Post by jerome bettis on 2006-02-04
sudo apt-get -y install apache ftp php4 mysql-server .. should be all the script you need

---

### Post by spyke01 on 2006-02-04
how can i make a shell script usiong this but doing multiple ine ones at a time

sudo apt-get -y install apache ftp php4 mysql-server
sudo apt-get -y install phplib

---

### Post by diebels on 2006-02-04
[QUOTE=spyke01]how can i make a shell script usiong this but doing multiple ine ones at a time

sudo apt-get -y install apache ftp php4 mysql-server
sudo apt-get -y install phplib[/QUOTE]
I don't think apt cares how many lines you use.

But you can do it just like that, when the first line is finished execution of the next starts..

---

### Post by spyke01 on 2006-02-04
ok, but what im asking is how do i make a shell script ^^
i have no clue

---

### Post by Jessehk on 2006-02-04
```

gedit webtoolsinstall.bash

```

**webtoolsinstall.bash**
```

#!/bin/bash
sudo apt-get install -y *stuff to install*

```

**make executable...**
```

chmod +x webtoolsinstall.bash

```

**run...**
```

./webtoolsinstall.bash

```

99.99% sure :)

---


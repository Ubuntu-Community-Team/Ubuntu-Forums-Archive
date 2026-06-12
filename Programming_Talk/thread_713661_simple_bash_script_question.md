---
title: "simple bash script question"
date: 2008-03-03
forum: Programming Talk
---

### Post by buddhasmak on 2008-03-03
I really don't know much about bash scripting, but I've written a small script that copies a project from it's workspace, removes all the svn metadata, compresses it, then sends it to the server.

Only thing about it is, I have to edit the script each time and set the project variable. Is it possible to send a variable to the script like:
./script.sh -var=value

Either that, or it would be just as easy on me to create a copy of the script for each project, but it's not as nice. Figured you smart folks would know =)

Thanks

---

### Post by amingv on 2008-03-03
I don't know much about bash scripting myself, but you can use command line arguments like this:

[PHP]#!/bin/bash

echo "The arguments 1, 2 & 3 are: " $1 $2 $3[/PHP]

and run like this:

```
$ ./script.sh one two three
```

---

### Post by ghostdog74 on 2008-03-03
> **buddhasmak said:**
> I really don't know much about bash scripting, but I've written a small script that copies a project from it's workspace, removes all the svn metadata, compresses it, then sends it to the server.


how about showing the code, and how you get that project file into your script.

---

### Post by buddhasmak on 2008-03-03
I just started messing with it from an example script a friend posted elsewhere. this is what I've got...


#!/usr/bin/env bash

PROJECT='exampleProject'
WORK_DIR='/var/www/'
PREP_DIR='/var/www/prep/'

# Remove old prep dir stuff
rm -rf ${PREP_DIR}${PROJECT}

# Copy working directory to prep area
chown -R myuser:www-data ${WORK_DIR}${PROJECT}
cp -R ${WORK_DIR}${PROJECT} ${PREP_DIR}${PROJECT}

# Remove svn and eclipse stuff
find ${PREP_DIR}${PROJECT} | grep .svn | xargs rm -rf
find ${PREP_DIR}${PROJECT} | grep .project | xargs rm -rf
find ${PREP_DIR}${PROJECT} | grep .cache | xargs rm -rf
find ${PREP_DIR}${PROJECT} | grep .settings | xargs rm -rf

echo ${PROJECT}' has been prepped!'



At the end I'll run a tar cmd, and then scp it to the server.

On the server, I'll write a simpler script to extract, and place the project into it's home.

Thanks very much for tip amingv, I'll give that a go in a min.

---

### Post by buddhasmak on 2008-03-03
here's what I got now...still missing the transfer, I probably won't get to that tonight since I've never worked with scp, but from my understanding installing keys isn't difficult. Anybody have a link to get me started quick?

#!/usr/bin/env bash

# Project is passed as arg1
PROJECT=$1
WORK_DIR='/var/www/'
PREP_DIR='/var/www/prep/'

# Remove old project if exists
rm -rf ${PREP_DIR}${PROJECT}

# Copy working directory to prep area
cp -R ${WORK_DIR}${PROJECT} ${PREP_DIR}${PROJECT}
chown -R mattl:www-data ${PREP_DIR}${PROJECT}

# Remove svn and eclipse metadata
find ${PREP_DIR}${PROJECT} | grep .svn | xargs rm -rf
find ${PREP_DIR}${PROJECT} | grep .project | xargs rm -rf
find ${PREP_DIR}${PROJECT} | grep .cache | xargs rm -rf
find ${PREP_DIR}${PROJECT} | grep .settings | xargs rm -rf

echo ${PROJECT}' has been copied to prep area'

tar -czf ${PREP_DIR}${PROJECT}.tar.gz ${PREP_DIR}${PROJECT}
echo ${PROJECT}' has been compressed!'

tar tells me to remove the leading /'s but the archive appears fine.

Thanks again!:guitar:

---

### Post by Martin Witte on 2008-03-03
The getopts builtin is the tool for commnandline processing, see [http://tldp.org/LDP/abs/html/internal.html](http://tldp.org/LDP/abs/html/internal.html) (find getopts on this page) for an example

---


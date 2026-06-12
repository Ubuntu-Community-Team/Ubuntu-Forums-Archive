---
title: "Updater script with wget"
date: 2006-05-02
forum: Programming Talk
---

### Post by [S|G] on 2006-05-02
Hi, I wrote a simple updater script that uses wget to retrieve new information from a certain url. It works fine under normal circumstances, but I'm having some trouble when the connection is down for some reason or it can't reach the website. 

Even when unable to retrieve the files (due to not being able to resolve the host, connection time out, etc) wget still creates the file "u1.swf" as a 0-byte file on my drive. This causes the script to corrupt the old files


```

#!/bin/bash

wget --retry-connrefused http://url/1.swf -O /home/inttegra/case/u1.swf
if [ -f u1.swf ] then
then
 mv /home/inttegra/case/1.swf /home/inttegra/case/1_old.swf
 mv /home/inttegra/case/u1.swf /home/inttegra/case/1.swf
else
 wget --retry-connrefused http://AlternativeURL/1.swf -O /home/inttegra/case/u1.swf
 if [ -f u1.swf ]
   then
     mv /home/inttegra/case/1.swf /home/inttegra/case/1_old.swf
     mv /home/inttegra/case/u1.swf /home/inttegra/case/1.swf
 fi
fi

```

How can I prevent wget from writing the file if it can't download? :confused: 
Thanks!

---

### Post by darth_vector on 2006-05-02
you could always check the return value of wget and bail out if the wget failed. alternatively you could check the size of u1.swf before moving it, and not move it if its size is 0.

---


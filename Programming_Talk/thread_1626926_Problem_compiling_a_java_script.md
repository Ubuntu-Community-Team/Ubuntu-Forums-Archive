---
title: "Problem compiling a java script"
date: 2010-11-20
forum: Programming Talk
---

### Post by AVatch on 2010-11-20
Hi,

I am trying to get the following standalone version of an LSST ETC simulation to work on my computer, but i keep getting the following error: 
(See attachment for screen crop)

Exception in thread "main" java.lang.NoClassDefFoundError: cletc/csh

I am not experienced with any of this to be perfectly honest, I was only following the documentation from the developer website:

[http://dls.physics.ucdavis.edu:8080/etc4_3work/servlets/standalone/setup.html](http://dls.physics.ucdavis.edu:8080/etc4_3work/servlets/standalone/setup.html)

I downloaded and uncompressed all the files, and when I try to run the example command

java cletc.csh -o "Test" instrumentFilter=y

I get the above error. I would greatly appreciate some assistance in getting this thing to work!

Thanks for all your time

---

### Post by lykeion on 2010-11-23
Ok, just some clarifications. The program is written in Java not Javascript (they're completetly different). 
The program is already compiled, so what you're having problems with is to run it.

According to the homepage you should run it via the script cletc.csh in Linux. But this is a csh script, in Ubuntu the default shell is bash, so you need to make some small changes to the file. 
1. Open cletc.csh in an text editor and change the contents to this:
[PHP]#!/bin/bash
echo "java -cp ./itcweb.jar:./itcdata.jar edu.gemini.itc.lsst.UnitTest $1"
java -cp ./itcweb.jar:./itcdata.jar edu.gemini.itc.lsst.UnitTest $1[/PHP]
2. Save it and close editor. Then start a terminal and go to the dir where the file is, and make the script executable:
```
chmod +x cletc.csh
```
3. Then you can run it like this (don't forget the quotes):
```
./cletc.csh "-t Test instrumentFilter=y"
```

---

### Post by Reiger on 2010-11-23
I would use a slightly different script:
```

#!/bin/sh
java -cp ./itcweb.jar:./itcdata.jar edu.gemini.itc.lsst.UnitTest "$@"

```

This allows you to invoke the script like you want to:
```

./cletc.csh -t Test instrumentFilter=y

```

---

### Post by AVatch on 2010-11-26
You guys were so helpful! Thank you so much, I greatly appreciated the help. I got the thing working with the default values, now the next step is figuring out how to change the parameters of the calculator using the batch file they talked about on the website o.O

---


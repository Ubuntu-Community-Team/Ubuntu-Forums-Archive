---
title: "bash: delete archive that is a month old"
date: 2009-02-12
forum: Programming Talk
---

### Post by PryGuy on 2009-02-12
Hello there!
I'm writing a simple shell script that would delete previous archive that is a month old. The soulution is pretty awkward:```
#!/bin/bash

name=/home/sysadmin/bases/
archive=/home/sysadmin/folder/

zip -r $name"_"`date +%d-%m-%Y`.zip $archive

if [ $((`date +%m`-1)) -lt 10 ]
then
    prevmonth=`date +%d-`0$((`date +%m`-1))-`date +%Y`
else
    prevmonth=`date +%d-`$((`date +%m`-1))-`date +%Y`
fi

if [ `date +%m` = 01 ]
then
    prevmonth=`date +%d-`12-$((`date +%Y`-1))
fi

rm -f $name"_"$prevmonth.zip

exit 0
```I hope you could propose a better solution... Thanks!

---

### Post by scragar on 2009-02-12
Hmn. I'm wondering, would it not be easier to select all files matching a filepattern within a given time period? **find** is built for that purpose...

---

### Post by PryGuy on 2009-02-12
LOL... Found a google article... Linux is TOO easy sometimes... ;)
[http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/]("http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/")

---

### Post by Neural oD on 2009-02-12
> **PryGuy said:**
> LOL... Found a google article... Linux is TOO easy sometimes... ;)
[http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/]("http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/")

Yes - linux is great - we can always find better ways of doing something

---

### Post by scragar on 2009-02-12
> **PryGuy said:**
> LOL... Found a google article... Linux is TOO easy sometimes... ;)
[http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/]("http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/")

Erm, quick note on that code, to prevent any chance of the {} being interpreted by a shell you should enclose it in quotes:
```
'{}'
```

Other than that the code should work perfectly fine.

---


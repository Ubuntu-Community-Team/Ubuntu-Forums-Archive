---
title: "I am in deep trouble please help"
date: 2008-11-21
forum: Programming Talk
---

### Post by aliahsan81 on 2008-11-21
Hi all

I have a script that run fine ,Actually if find 777 directory and take its count and report,There is no problem with the script.But our reporting system have some limitation that dont allow more then 1000 directory to report,Now i want some way i can break this up and then report to the reporting system,My code is below,At the moment there are like 5000 777 directories.Please help i am blanked.Please its very urgent
```

#!/bin/bash

check=/var/www/html


res=$(find $check -type d -perm 777 2>/dev/null )
count=$(find $check -type d -perm 777 | wc -l)

echo $count
#echo $res

Reporting system command. 



```

---

### Post by pmasiar on 2008-11-21
5000+ directories? That's obviously bad design

create 2 level structure, instead of directory /abcd have /ab/abcd - and you are fine

---

### Post by aliahsan81 on 2008-11-21
I cant do thid becz its a dev server for programmer

---

### Post by akvino on 2008-11-21
> **aliahsan81 said:**
> Hi all

I have a script that run fine ,Actually if find 777 directory and take its count and report,There is no problem with the script.But our reporting system have some limitation that dont allow more then 1000 directory to report,Now i want some way i can break this up and then report to the reporting system,My code is below,At the moment there are like 5000 777 directories.Please help i am blanked.Please its very urgent
```

#!/bin/bash

check=/var/www/html


res=$(find $check -type d -perm 777 2>/dev/null )
count=$(find $check -type d -perm 777 | wc -l)

echo $count
#echo $res

Reporting system command. 



```

Use an output file. Try something like:
#!/bin/bash

check="/var/www/html"


find $check -type d -perm 755 > junk
res=`cat junk | wc -l`

printf "\nThe number of directories with 755 permisions is $res.\n";

rm -f junk

---

### Post by pp. on 2008-11-21
> **aliahsan81 said:**
> I cant do thid becz its a dev server for programmer

Whatduzþismean?

---


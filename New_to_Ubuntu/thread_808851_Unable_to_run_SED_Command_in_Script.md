---
title: "Unable to run SED Command in Script"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by markbusu on 2008-05-26
Hi guys,

Its my 1st attempt at scripting and trying to print a certain amount of lines from a file called xxx.dat..

Now... running the following command directly in terminal works

```
sed -n "$i,$v p" $doy.dat > newspots.dat
```

However, when trying to execute it in a script...

```

i=1

doy=`date +%j`
v=`cat $doy.dat |wc -l`
sed -n "$i,$v p" $doy.dat > newspots.dat 
i=`expr $i + $v` mysql -u root -p -e "load data infile '/spider/data/spots/2008/newspots.dat' into table dxcluster.spots fields terminated by '^' lines terminated by '\n';"
```

The following error is generated:

```
sed: -e expression #1, char 1: unknown command: `,'
```

Any idea guys?

Thanks!

Mark

---

### Post by cdtech on 2008-05-26
My bad that is the command, sorry. Give me a sec

did you try single quotes? I think I may have had issues with doubles

---

### Post by markbusu on 2008-05-26
Sorted :D

Thanks just the same

---


---
title: "Permission denied during bzcat"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by nirmalj on 2012-06-22
sudo [COLOR=Black][curl ]("http://stat-computing.org/dataexpo/2009/2004.csv.bz2")[http://stat-computing.org/dataexpo/2009/2004.csv.bz2](http://stat-computing.org/dataexpo/2009/2004.csv.bz2)[|bzcat ]("http://stat-computing.org/dataexpo/2009/2004.csv.bz2")| head-1000>2004-1000.csv

I'm trying to read 1000 lines from that file in the link and extract it to 2004-1000.csv. I just get an error message:

bash: 2004-1000.csv Permission denied. 

I'm really new to linux, so am trying to get some help to figure this out. Any help is appreciated. Thanks.
[/COLOR]

---

### Post by codemaniac on 2012-06-22
> **nirmalj said:**
> sudo [COLOR=Black][curl ]("http://stat-computing.org/dataexpo/2009/2004.csv.bz2")[http://stat-computing.org/dataexpo/2009/2004.csv.bz2](http://stat-computing.org/dataexpo/2009/2004.csv.bz2)[|bzcat ]("http://stat-computing.org/dataexpo/2009/2004.csv.bz2")| head-1000>2004-1000.csv

I'm trying to read 1000 lines from that file in the link and extract it to 2004-1000.csv. I just get an error message:

bash: 2004-1000.csv Permission denied. 

I'm really new to linux, so am trying to get some help to figure this out. Any help is appreciated. Thanks.
[/COLOR]

Seems like you dont have necessary read privileges on the mentioned file 2004-1000.csv .
please enable read bits on the file .

```
chmod +r 2004-1000.csv
```


To know more about unix filesystem permissions read the below link .

[http://www.dartmouth.edu/~rc/help/faq/permissions.html](http://www.dartmouth.edu/~rc/help/faq/permissions.html)

---

### Post by papibe on 2012-06-22
Hi famebu.

The sudo is being applied only to the first part of the pipe. The rest is being executed as your regular user. Probably you are executing it in a directory that your user doesn't have write permissions.

One way to solve it could be 'became' root for a while:
```
sudo -i

curl http://...bz2 | bzcat | head -n 1000 > 2004-1000.csv
```
Don't forget to go back to be "you" (exit or Ctrl+D).

Another option is take the pipe structure and use it in one command:
```
sudo bash -c 'curl http://...bz2 | bzcat | head -n 1000 > 2004-1000.csv
```

I hope that helps, and tell us how it goes.
Regards.

---

### Post by steeldriver on 2012-06-22
one way I've done this in the past is to use a pipe to 'sudo tee' in place of the final '>' redirect

```
 ... | head -1000 | sudo tee 2004-1000.csv
```[COLOR=Black]
or 
[/COLOR]```
 ... | head -1000 | sudo tee 2004-1000.csv >/dev/null
```[COLOR=Black]

if you don't want to see the tee'd output - likewise you can use 'tee -a' in place of a '>>' 
  
[/COLOR]

---


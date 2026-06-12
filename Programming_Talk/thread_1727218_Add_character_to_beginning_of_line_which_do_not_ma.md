---
title: "Add character to beginning of line which do not match regexp"
date: 2011-04-12
forum: Programming Talk
---

### Post by deathadder on 2011-04-12
At the moment I'm trying to write a script that'll add a '#' to the beginning of each line from fcrontab. With the exception of lines which have the servicestatus or rotatelogs strings present. 

I know these are on the 1st and 2nd lines (but can't always guarentee they will be). So I've been looking at improving the block of code below to use regular expressions instead of line numbers. 

Does anyone have any suggestions?
```
#!/bin/bash

FCRONTAB=/usr/bin/fcrontab
FCRONTAB_TEMP=/root/fcron.tmp

function disableCron() {
    $FCRONTAB -l > $FCRONTAB_TEMP
    sed -i '3,$ s/^/#/' $FCRONTAB_TEMP
    $FCRONTAB $FCRONTAB_TEMP
    rm $FCRONTAB_TEMP
}

disableCron
```

---

### Post by deathadder on 2011-04-12
So more Googling found a [stackoverflow]("http://stackoverflow.com/questions/5488352/adding-characters-to-the-beginning-and-end-of-a-line-starting-with-a-specific-str") post that seems to do what I want.

Although I can't seem to get it right
```
sed -i 's/\(.*servicestatus|rotatelogs*.\)/#\1/' $FCRONTAB_TEMP
```
I know that's not going to ignore the lines I want (I'm just playing around atm).

---

### Post by sisco311 on 2011-04-12
```
sed '/servicestatus\|rotatelogs/! s/.*/# &/' file
```

---

### Post by deathadder on 2011-04-12
Fantastic! Thanks sisco311, to stop multiple #'s getting added to the line I changed it slightly to:
```
sed -i '/servicestatus\|rotatelogs/! s/^[^#]/# &/' $FCRONTAB_TEMP
```

---

### Post by dethorpe on 2011-04-12
A quick perl version if that helps:
 
```
 
#! /usr/bin/perl -w
use strict;
 
while (<>) {
        print "#" if ($_ !~ m/servicestatus|rotatelogs/);
        print;
}
 
 

```
 
Run as "script.perl filename"
 
 
or as a 1 line command:
 
```
 
$ perl -p -e 'print "#" if ($_ !~ m/servicestatus|rotatelogs/)' filename

```

---


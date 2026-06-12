---
title: "Python script to crontab."
date: 2012-11-19
forum: Programming Talk
---

### Post by mafi127 on 2012-11-19
I need to make a little python script what I want to run on crontab, but I cant get the last part to work on it. I have tryed to put the -exec cp -r path to "" and even '' but I cant get the script to work. can some1 pont me a bug what is wrong in here.


```

#!/usr/local/bin/perl
find /home/tamps/test/ -maxdepth 3 -mindepth 2 -type d -mtime -1 -not -name sorted -exec cp -r {} /media/-Arhiiv-/=\ stuff\ \=/=\ folder\ \=\/to/=\ path\ \=\/{{ now|formatdate('%Y/%m-%B')}}/ \;

```

---

### Post by mafi127 on 2012-11-19
Solved the problem whit bash script

```
#!/bin/bash
NOW=$(date +"%Y/%m - %B")
find /home/tamps/test/ -maxdepth 3 -mindepth 2 -type d -mtime -1 -not -name sorted -exec cp -r {} /media/-Arhiiv-/=\ stuff\ \=/=\ folder\ \=\/to/=\ path\ \=\/"$NOW" \;

```

---


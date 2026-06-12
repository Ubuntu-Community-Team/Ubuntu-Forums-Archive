---
title: "unix script that handles dates"
date: 2012-10-14
forum: New to Ubuntu
---

### Post by rudy1094 on 2012-10-14
I have a comma delimited text file that has a date field that looks like: 
12/1/2011 04:00:00 PM

I only want to include  records that are 10-40 days from now. So in this example, I'd want to include dates between 12/10/2011 and 1/10/2012. Is there a linux command or a scripting language that can easily handle this type of situation? Thanks.

---

### Post by steeldriver on 2012-10-14
The GNU 'date' function can do some pretty clever things - you could certainly pull in the date strings and convert them to some unambiguous format (e.g. +%s seconds since 1970-01-01 00:00:00 UTC) and then do a direct integer comparison

```
$ start=$(date --date="$date +10 days" +%s); stop=$(date --date="$date +40 days" +%s); echo $start $stop;
1351093388 1353685388
``````
$ inputdate=$(date --date="12/1/2011 04:00:00 PM" +%s)
$ if [[ $inputdate > $start && $inputdate < $stop ]]; then echo "yes"; else echo "no"; fi
no
``````
$ inputdate=$(date --date="11/1/2012 04:00:00 PM" +%s)
$ if [[ $inputdate > $start && $inputdate < $stop ]]; then echo "yes"; else echo "no"; fi
yes

```

---


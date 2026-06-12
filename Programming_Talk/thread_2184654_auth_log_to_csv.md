---
title: "auth log to csv"
date: 2013-10-30
forum: Programming Talk
---

### Post by ikki_72 on 2013-10-30
hi,

I want to get output of failed login attempt, get its time & user in below format

time,username,

e.g.: 19:19:44,ikki_72,

how would i do that from output of grep -i fail /var/log/auth.log

I tried doing for loop getting output of few lines but it will only inseted to file in one line

---

### Post by drmrgd on 2013-10-30
Maybe something along the lines of this:

```

$ perl -ane '($user) = $_  =~ /user=(\w+)\b/; print join( ",", @F[0,1,2], $user ), "\n" if /authentication failure/' /var/log/auth.log

```

For me, it logged two fat fingered login attempts today (I type fast, but super sloppy!)

```

Oct,27,15:06:08,dave
Oct,29,19:00:37,dave

```

You could also remove the month and day from the output by changing '@F[0,1,2]' to just '$F[2]':

```

 perl -ane '($user) = $_  =~ /user=(\w+)\b/; print join( ",", $F[2], $user ), "\n" if /authentication failure/' /var/log/auth.log
15:06:08,dave
19:00:37,dave

```

---

### Post by btindie on 2013-10-30
With sed you can do it as follows
```
sed -e '/: [Ff]ailed/!d;s/^.* \([0-9:]\{8\}\) .* Failed password for \(invalid user \)\?\(\w*\) from \([0-9]\{1,3\}\(\.[0-9]\{1,3\}\)\{3\}\) .*$/\1,\3,\4/' /var/log/auth.log
```
which will also give you the offending IP address.
```
23:25:36,ucpss,70.182.150.108
04:35:39,PlcmSpIp,212.83.149.231
04:35:41,support,212.83.149.231
04:35:44,admin,212.83.149.231
08:06:37,root,95.163.143.140

```

---

### Post by ikki_72 on 2013-10-31
my mistake, I forgot to mention of Bash script

thanks for those perl examples though

---

### Post by drmrgd on 2013-10-31
You could call that perl one liner from a bash script.  Also, with the perl solution and btindie's sed solution, you don't have to grep the auth.log file first; you can just directly query the file.  

If you'd prefer something a just a little closer to bash, maybe do it with awk?

```

$ awk 'BEGIN{ OFS=","; } /authentication failure/{ print $3,substr($15,6) }' /var/log/auth.log
15:06:08,dave
19:00:37,dave

```

As I said, though, you can call either from a bash script if you wanted:

```

#!/bin/bash


auth_log="/var/log/auth.log"
result=$(perl -ane '($user) = $_ =~ /user=(\w+)\b/; print join( ",", $F[2], $user ), "\n" if /authentication failure/' $auth_log)


result2=$(awk 'BEGIN{OFS=","} /authentication failure/{print $3, substr($15,6)}' $auth_log)


echo -e "result1: \n$result\n"
echo 
echo -e "result2: \n$result2\n"

```

This results in:

```



$ bash failed_user.sh 
result1: 
15:06:08,dave
19:00:37,dave




result2: 
15:06:08,dave
19:00:37,dave

```

---


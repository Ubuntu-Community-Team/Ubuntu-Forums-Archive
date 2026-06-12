---
title: "Date comparison with 'string date having slashes and time zone' in Bash only"
date: 2009-10-08
forum: Programming Talk
---

### Post by TariqYousaf on 2009-10-08
_**The problem statement**_:
I have a standard thttpd web server log file. It contains different columns (like IP address, request result code, request type etc) including a date column with the format [31/Mar/2002:19:30:41 +0200].

I have developed a command line log analyzer that displays different statistics from the log (e.g. 1- IP with most connection attempts, 2- the most common result codes etc.). In fact to view every stat the user will have to give a specific switch to my utility (like -i and -c respectively with the above examples).

Now comes the problem; with every stat the user can ask to limit the results for either 1. previous n hours. or 2. previous n days. ***I am unable to use the date from the file with format [31/Mar/2002:19:30:41 +0200] and make a comparison*** with the timestamp of previous n hours or previous n days.

**_Constraint_**: I have to attempt this only in bash.

---

### Post by DaithiF on 2009-10-08
One way: manipulate the timestamp into a format which the date command will accept as a value for its -d parameter, convert this into seconds since the epoch (+%s format specifier), and compare against now less n hours, or n days, etc. also in seconds since the epoch.

step 1:
assuming you have a parameter holding the number of hours, calculate a threshold timestamp being now less 3600 seconds * number of hours ago
THRESHOLD=$(($(date +%s) - 3600 * $HOURS ))

step 2: 
the date command will accept a -d parameter in the format
dd-mmm-yyyy hh:mm:ss+0000, so we'll use sed to extract the timestamp from the file and munge it into this format.  we convert this to seconds since the epoch using the date command and compare it to the threshold.  If its > than threshold then do something with it...


```
while read line
do
  MUNGED_TIMESTAMP=$(echo "$line" | sed 's/^\[\([0-9]\+\)\/\([A-Za-z]\+\)\/\([0-9]\{4\}\):\([^ ]*\) \(+[-0-9]\{4\}\)\].*$/\1-\2-\3 \4\5/')
  SECONDS=$(date -d "$MUNGED_TIMESTAMP" +%s)
  if [[ $SECONDS -gt $THRESHOLD ]]; then
     echo "Do something with $line here"
  fi
done < logfile

```

good luck

---

### Post by TariqYousaf on 2009-10-25
Thanks alot DaithiF,

I really appreciate your reply. Actually, I had already tried this solution and the problem was that I had about 15000 records in the log and traversing 15000 records and running the test for each line was getting quite slow.

Fortunately, I got to know it was my own mistake... since all the logs are sorted by TimeStamp in ascending order. So, all that I had to do is reverse the log and traverse only the records that were within my threshold limit. And this saved me from being in-efficient.

Thanks to you again.
Tariq

---


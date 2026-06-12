---
title: "Number of hours between two dates?"
date: 2011-09-23
forum: Programming Talk
---

### Post by honeybear on 2011-09-23
Hello,

I would like to log and calculate the nbr of hours between 2 dates, independent that it is of not the same day.
```

DATE1="$(date +%Y%m%d-%H%M%S)"
sleep $anygiventimeordays
DATE2="$(date +%Y%m%d-%H%M%S)"
Numberofhours="???"
echo "$Numberofhours"
```

Any ideas or code would be helpful ... thank you !

---

### Post by papibe on 2011-09-23
I would recommend using the %s option to get the date as a time stamp (seconds since 1970-01-01 00:00:00 UTC), then the arithmetic shouldn't be a problem.

Here's an example [script]("https://forum.transmissionbt.com/viewtopic.php?f=2&t=11029") that I wrote long time ago to remove 5-day-old torrents from transmission-daemon.

I hope it helps,
Regards.

---

### Post by Habitual on 2011-09-23
some additional examples I worked out.
```
echo "$(date +'%s' -d 2007-09-02)/86400"-"$(date +'%s' -d 2007-09-01)"/86400 | bc

echo $(date --date='2007-09-01 18:30:00' +%s)/60-$(date --date='2007-09-01 17:30:00' +%s)/60 | bc
```

FWIW:
[http://www.unix.com/shell-programming-scripting](http://www.unix.com/shell-programming-scripting) is full of this kind of code. ;)

but pabipe is accurate:
date +%s to get epoch and 
date -d @<epoch_stamp> to decode.
```
for i in `date +%s` ; do date -d @$i ; done
```

---

### Post by stylishpants on 2011-09-23
Ruby's date parsing flexibility does well with stuff like this.

One solution using ruby:
  ruby -rtime -e 'a,b=ARGV.map{|s| Time.parse(s) }; puts (a-b).abs / 3600' "Sep 23 2010" "Sep 22 2010" 

# Works in either direction (with the latest date specified first or second)
bob@cob:~$ ruby -rtime -e 'a,b=ARGV.map{|s| Time.parse(s) }; puts (a-b).abs / 3600' "Sep 22 2010" "Sep 23 2010" 
24.0

bob@cob:~$ ruby -rtime -e 'a,b=ARGV.map{|s| Time.parse(s) }; puts (a-b).abs / 3600' "Sep 23 2010" "Sep 22 2010" 
24.0


# Some easy-to-verify calculations
bob@cob:~$ ruby -rtime -e 'a,b=ARGV.map{|s| Time.parse(s) }; puts (a-b).abs / 3600' "Sep 23" "Sep 21" 
48.0

bob@cob:~$ ruby -rtime -e 'a,b=ARGV.map{|s| Time.parse(s) }; puts (a-b).abs / 3600' "Sep 23" "Sep 16" 
168.0

bob@cob:~$ ruby -rtime -e 'a,b=ARGV.map{|s| Time.parse(s) }; puts (a-b).abs / 3600' "Sep 23" "Sep 16 2010" 
8928.0

# works with more precise times
bob@cob:~$ ruby -rtime -e 'a,b=ARGV.map{|s| Time.parse(s) }; puts (a-b).abs / 3600' "Sep 23 10:00am" "Sep 23 8:00am" 
2.0

# works with less precision too
bob@cob:~$ ruby -rtime -e 'a,b=ARGV.map{|s| Time.parse(s) }; puts (a-b).abs / 3600' "Mar 2010" "Mar 2011"
8760.0

# The result is precise in fractions of an hour ...
bob@cob:~$ ruby -rtime -e 'a,b=ARGV.map{|s| Time.parse(s) }; puts (a-b).abs / 3600' "Sep 23 10:16am" "Sep 23 8:55am" 
1.35

# If you want an integer result instead, then you can modify it this way:
bob@cob:~$ ruby -rtime -e 'a,b=ARGV.map{|s| Time.parse(s) }; puts (a-b).abs.to_i / 3600' "Sep 23 10:16am" "Sep 23 8:55am" 
1

---


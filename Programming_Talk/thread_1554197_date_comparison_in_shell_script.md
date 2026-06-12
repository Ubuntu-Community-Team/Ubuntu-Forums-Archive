---
title: "date comparison in shell script"
date: 2010-08-16
forum: Programming Talk
---

### Post by qmqmqm on 2010-08-16
Hi everyone

In shell scripts, is there any way to compare two dates (e.g. Sun Aug 15 09:58:30 EDT 2010 < Mon Aug 16 10:52:12 EDT 2010)?

Or is there a way to convert a date to a number, to allow for the comparison?

Thanks a lot.

Tom

---

### Post by geirha on 2010-08-16
Depends on what commands you have available, and what you actually want to do. If you just want to know if one file is newer than another, in a bash script:
```

if [[ file1 -nt file2 ]]; then 
  echo "file1 is newer than file2" 
fi

```

---

### Post by DaithiF on 2010-08-16
yes, pass the date string to the date command via the -d param, and convert the date to seconds since 1970-01-01 using the %s format specifier.

e.g.
```
(( $(date -d "Sun Aug 15 09:58:30 EDT 2010" +%s) < $(date -d "Mon Aug 16 10:52
:12 EDT 2010" +%s) )) && echo "earlier" || echo "later"
earlier

```

---

### Post by qmqmqm on 2010-08-20
> **DaithiF said:**
> yes, pass the date string to the date command via the -d param, and convert the date to seconds since 1970-01-01 using the %s format specifier.

e.g.
```
(( $(date -d "Sun Aug 15 09:58:30 EDT 2010" +%s) < $(date -d "Mon Aug 16 10:52
:12 EDT 2010" +%s) )) && echo "earlier" || echo "later"
earlier

```

Thanks so much for your reply DaithiF and geirha.

I treid the command that DaithiF suggested, however apparently the "date" function on my machine does not have the "-d" option:
"date: illegal option -- d"

Could anyone please advise?

Thanks a lot.

Tom

---

### Post by geirha on 2010-08-20
The -d option is only available on GNU's implementation of date; it's not standard. What system are you scripting on, and more importantly, why do you need to compare these dates?

---

### Post by qmqmqm on 2010-08-26
Thanks for your reply Geirha.

I am using Solaris operating system.

The goal is:
I have a file with some records that contain time stamps in the format of "Sun Aug 15 09:58:30 EDT 2010". I would like to have a way to filter the records in the file such that I only get records within a certain time range.

If anyone could advise how I may achieve this, that would be wonderful.

Thanks,

Tom

---

### Post by geirha on 2010-08-26
Might have been a good idea to mention you're on solaris right away when asking at the ubuntuforums. Otherwise people will assume you're on Ubuntu and give you Ubuntu/GNU/Linux specific answers, which is likely not to work on Solaris.

There aren't any command line tools (that I know of) that can do date comparison on solaris. perl or python could do it, but I don't remember if any of those are installed by default on Solaris.

sed/awk might be what you need though. Assuming the lines are sorted by date, this should output all lines from Aug 15 09:13 to Aug 17 10:00:
```
sed -n '/^Sun Aug 15 09:13/,/^Tue Aug 17 10:00/p' logfile
```

---


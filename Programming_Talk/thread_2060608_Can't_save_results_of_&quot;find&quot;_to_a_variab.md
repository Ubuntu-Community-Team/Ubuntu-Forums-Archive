---
title: "Can't save results of &quot;find&quot; to a variable"
date: 2012-09-20
forum: Programming Talk
---

### Post by LoneStar++ on 2012-09-20
I am trying to save the results of a find command into a variable. If I run the commands manually in the terminal they work as expected:

```

site=123
job=456
file=`find /dir1/dir2/${site}_XML -type f -name ${job}\*`
echo $file
/dir1/dir2/123_XML/456_abc.XML

```

However inside my bash script I have basically the same thing, but it isn't working the same way:

```

for site in $list_of_sites ; do
  # Loop through each XML file
  for job in $list_of_jobs ; do
    # Find the file for each job
    file=`find /dir1/dir2/${site}_XML -type f -name ${job}\*`
    echo $file
  done
done

```

When I run the above the $file variable is empty.

I have been working on this for a few hours now. Every variation I have tried won't work, but works when I do them in the terminal manually.

I am using CentOS if that is relevant information. Thanks!

---

### Post by LoneStar++ on 2012-09-20
I have since fixed my problem. Turns out that my $list_of_jobs variable had some windows carriage returns that I had to remove.

---

### Post by Vaphell on 2012-09-20
are you sure you get correct $site and $job in these loops?
echo everything that moves, otherwise you are left in the dark with no idea what the loop does exactly.

besides drop backticks, they are deprecated and use $( ) instead

---


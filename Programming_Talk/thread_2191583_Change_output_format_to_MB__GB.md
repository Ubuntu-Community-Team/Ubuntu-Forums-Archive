---
title: "Change output format to MB / GB ?"
date: 2013-12-03
forum: Programming Talk
---

### Post by termvrl on 2013-12-03
Hi all,

I found this code to sum byte of access.log file in apache.

```

cat access.log | perl -e 'my $sum=0; while(<>) { my ($traffic) = m/\[.+\] ".+" \d+ (\d+)/; $sum += $traffic}; print "$sum\n"'

```

Here is the output:

```

root@ubuntu:/var/log/apache2# cat access.log | perl -e 'my $sum=0; while(<>) { my ($traffic) = m/\[.+\] ".+" \d+ (\d+)/; $sum += $traffic}; print "$sum\n"'
333323

```

How can i change the format to MB or GB?

Thanks

---

### Post by ofnuts on 2013-12-03
Use bash arithmetic to divide by 1024*1024 (after perhaps adding half a meg/gig for rounding up) if you want integer megs/gigs. Otherwise use the 'bc' command for floating point values.

---


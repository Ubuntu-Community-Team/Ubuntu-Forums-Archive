---
title: "Script: Remove all files in a given directory that are older than 1 year old"
date: 2013-07-08
forum: Programming Talk
---

### Post by morecw on 2013-07-08
Hi all

I'm a Ubuntu newbie and although I've used a bit with the find/locate command I now need to do the follow:

Find and remove all files in a given directory that are older than 1 year old. 

Can someone help me with this? I want to put it into crontab either as a command or script

Thanks in advance.

---

### Post by Vaphell on 2013-07-08
```
find /some/dir -mtime +365 -type f **-printf '%Tc %p\n'**  # print out modification times and names
find /some/dir -mtime +365 -type f **-delete** # delete
```

---

### Post by Vaphell on 2013-07-08
> ```
for i in $(find . -type f -mtime +365);do echo rm "$i";done
```

this is wrong because [http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29](http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29)

---

### Post by morecw on 2013-10-23
Thanks for the help. Sorry I couldn't reply sooner. In the end I went for:

```
find /some/dir -mtime +365 -type f -printf '%Tc %p %k KB\n'
```

%k KB - a useful switch for displaying the size of the file!

---

### Post by hailholyghost on 2013-10-24
Hi morecw,

perhaps you could try something like this in the directory which you wish to clean up:

```
#!/usr/bin/env perl

use strict;
use warnings;

foreach my $file (glob("*")) {#for all files in current directory, each file labeled $file
   my $file_age = -M $file;#save the age of the file in the scalar $file_age
   if ($file_age > 365) {#if the file age is > 365 days
      print "Deleting $file...\n";#print that you are about to delete $file
#      system("rm $file");#delete $file. I've commented this out so you can check if there are any files > 365 days you may wish to keep
   }
}
```

---

### Post by alan9800 on 2013-10-24
> **hailholyghost said:**
> Hi morecw,

perhaps you could try something like this in the directory which you wish to clean up:

```
#!/usr/bin/env perl

use strict;
use warnings;

foreach my $file (glob("*")) {#for all files in current directory, each file labeled $file
   my $file_age = -M $file;#save the age of the file in the scalar $file_age
   if ($file_age > 365) {#if the file age is > 365 days
      **print "Deleting $file...\n";**#print that you are about to delete $file
#      **system("rm $file");**#delete $file. I've commented this out so you can check if there are any files > 365 days you may wish to keep
   }
}
```
IMHO the two lines I have highlighted in bold might be simplified in a single line as follows:```
system("rm -iv $file");#where "i" means "interactive" and "v" means "verbose"
```

---


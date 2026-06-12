---
title: "Perl newbie trying to figure out regexp"
date: 2009-10-23
forum: Programming Talk
---

### Post by dmsynck on 2009-10-23
Hi all,

I am a Perl newbie trying to do something beyond my current level and am having a hard time getting a regular expression correctly built. The text I am trying to match is a range of lines out of log file like so:

[B]10/20/2009 9:59:43 AM
Time in minutes: 53
Total Number of Locations Synced: 70
Number of locations passed: 70
Number of locations failed: 0[/B]

Here is the relevant piece of my Perl script:

```
my $log_in_file = "C:/Logs/Synchronize_log.txt";
my $log_out_file = "C:/Logs/Synchronize_summary.txt";

open(FILE_IN, "<", $log_in_file) || die "Could not open file $log_in_file";
open(FILE_OUT, ">", $log_out_file) || die "Could not open file $log_out_file";

my @date = (localtime)[3..5];
my $current_month = $date[1] + 1;
my $current_year = $date[2] + 1900;
my @data = [];

while(<FILE_IN>) {
    if(m/$current_month"//"(\d+)"//"$current_year\s*(\d+)":"(\d+)":"(\d+)\s*"AM"/ .. m/Number of locations failed:/) {
        push(@data, "$_ \n");
    }
}

```

Thanks in advance

---

### Post by H4F on 2009-10-23
What exactly are you trying to match ?

all lines which contains 
DATE
Time in minutes: 
Total Number of Locations Synced: 
Number of locations passed: 
Number of locations failed:

---

### Post by dmsynck on 2009-10-23
> **H4F said:**
> What exactly are you trying to match ?

all lines which contains 
DATE
Time in minutes: 
Total Number of Locations Synced: 
Number of locations passed: 
Number of locations failed:

I am trying to match the "date" line and the "Number of locations failed:" line, so I can grab those lines and everything in between and pop them into another file. Basically, I only want to grab the current months data summary out of a fairly large log file.

---

### Post by H4F on 2009-10-23
"^[0-1][0-9]/[0-3][0-9]/2009 " this will match any date month 2009. 
the easy way to do regex is by increasing compexity one by one. 
firs try to match first word. then second till you get all what you need.

other question is whether 
"Time in minutes: 53
Total Number of Locations Synced: 70
Number of locations passed: 70
Number of locations failed: 0"
are straight after the date . or can be other info in between

---

### Post by H4F on 2009-10-23
"^[0-1][0-9]/[0-3][0-9]/2009 " this will match any date month 2009. 
the easy way to do regex is by increasing compexity one by one. 
firs try to match first word. then second till you get all what you need.

other question is whether 
"Time in minutes: 53
Total Number of Locations Synced: 70
Number of locations passed: 70
Number of locations failed: 0"
are straight after the date . or can be other info in between

---

### Post by ghostdog74 on 2009-10-23
if  you are doing multi line matches, you should use the 'g', 'm' (or 's') modifier. see perldoc perlre for more info.

that aside, i will show you a simpler method , without much regex. here's a pseudocode 
```

set flag=0
while (<>) {
  if ( Number of locations failed is found ) { set flag=0 }  
  if ( found last 3 chars of the line is a space followed by "AM|PM" ) {
    # this shows the line where date is
    set flag=1
    print line
  }
  if (flag is set){
    print line
  }
}


```

---


---
title: "show only 30 minutes of log file"
date: 2013-10-01
forum: Programming Talk
---

### Post by learnbash on 2013-10-01
Hi,

I want to see only last 30 minutes of log file, discard previous logs, only show latest 30 minutes log file. How it could possible.

---

### Post by Lars Noodén on 2013-10-01
Which logs?  The specific format probably matters.  I'm guessing awk will figure in the answer.

---

### Post by tgalati4 on 2013-10-01
You can use the *tail* command to display the last *n* lines:

```
tail -100 /var/log/syslog
```

I don't know of a clean way to do it by time.  You would have to write a script that parses the file and picks out the end time and computes 30 minutes previous then display that point forwards.  This would not be trivial because each log file has a slightly different format.

An easier, but clumsy method would be to make a distinctive log entry (or the log that you are interested in) every 1/2 hour then use grep/sed/awk to find that mark and display the file from the last mark to the end.  Set up the script in a cronjob to run every 1/2 hour to add the mark.

For example, *syslogd* puts a mark every 20 minutes, just to show that a system is still alive and running:


       -m interval
              The syslogd logs a mark timestamp regularly.  The default interval between two -- MARK -- lines is 20 minutes.  This can be  changed  with  this  option.
              Setting the interval to zero turns it off entirely.  Depending on other log messages generated these lines may not be written consecutively.


In /var/log/messages:

Oct  1 08:32:38 tpad-Gloria7 syslogd 1.5.0#5ubuntu3: restart.
Oct  1 09:02:28 tpad-Gloria7 -- MARK --
Oct  1 09:22:28 tpad-Gloria7 -- MARK --

This is helpful if your name is Mark, otherwise it is less useful if your name is Tim, or Bob, or Jim.

---

### Post by learnbash on 2013-10-01
> **tgalati4 said:**
> You can use the *tail* command to display the last *n* lines:

```
tail -100 /var/log/syslog
```

I don't know of a clean way to do it by time.  You would have to write a script that parses the file and picks out the end time and computes 30 minutes previous then display that point forwards.  This would not be trivial because each log file has a slightly different format.

i want to check /var/log/messages for only last 30 minutes, wants to discard previous log. I also tried below command but no luck

```

sed -n "/^$(date --date='30 minutes ago' '+%b %d %H:')\\|^$(date --date='0 minutes ago' '+%b %d %H:')/p" logfile

```

```

Oct  1 19:20:18 server1 kernel: [ 4187.150615] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Oct  1 19:21:10 server1 kernel: [ 4238.860148] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
Oct  1 19:21:10 server1 kernel: [ 4238.862415] sd 6:0:0:0: [sdb] Asking for cache data failed
Oct  1 19:21:10 server1 kernel: [ 4238.862421] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Oct  1 19:22:02 server1 kernel: [ 4290.572145] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
Oct  1 19:22:02 server1 kernel: [ 4290.574250] sd 6:0:0:0: [sdb] Asking for cache data failed
Oct  1 19:22:02 server1 kernel: [ 4290.574256] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Oct  1 19:22:54 server1 kernel: [ 4342.284094] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
Oct  1 19:22:54 server1 kernel: [ 4342.286210] sd 6:0:0:0: [sdb] Asking for cache data failed
Oct  1 19:22:54 server1 kernel: [ 4342.286216] sd 6:0:0:0: [sdb] Assuming drive cache: write through




```

---

### Post by Lars Noodén on 2013-10-01
Ok.  Here's a guess at syslog.

```

awk -v date=$(date -d "30 minutes ago" +"%T") '$3 >= date { print $0 }' /var/log/syslog 

```

We use -v to set a variable in awk before we start based on the output of "date".  From there it's just a simple comparison of the 3rd field/column.

---

### Post by learnbash on 2013-10-01
It is showing log from 29 september till now.

---

### Post by Lars Noodén on 2013-10-01
It gets tricky as the time rolls over at midnight.

---

### Post by learnbash on 2013-10-01
What about below command, can you please advise, it is also not working

```

sed -n "/^$(date --date='30 minutes ago' '+%b %d %H:')\\|^$(date --date='0 minutes ago' '+%b %d %H:')/p" /var/log/syslog

```

---

### Post by Lars Noodén on 2013-10-01
sed won't really do it, I think.  It would have to be something more complex.  I initially though awk, but with the problem of the clock rolling over at midnight and syslog not using numeric months, the solution is probably a small perl script.  The module Date::Calc does proper time differences.

---

### Post by learnbash on 2013-10-01
so can you help me in that @perl

---

### Post by Lars Noodén on 2013-10-01
Here's a whack at it.  You pass the name of the log file on the command line or else feed it as stdin.  It uses Date::Calc

```

#!/usr/bin/perl

use strict;
use warnings;
use Date::Calc( 'Decode_Month', 'Delta_YMDHMS' );

# read from file passed as argument or else read stdin
my $logfile = shift || "-";

my ( $sec1, $min1, $hour1, $day1, $month1, $year1 );
my ( $sec2, $min2, $hour2, $day2, $month2, $year2 );

# get the current local time and date
( $sec1, $min1, $hour1, $day1, $month1, $year1, undef, undef, undef ) 
    = localtime( time () );
$year1 += 1900;
$month1++;

# start reading the log

open( LOG, "$logfile" ) 
    or die( "Could not open '$logfile': $!\n");

while ( my $line = <LOG> ) {
    my $year2 = $year1;
    my ( $month2, $day2, $time2, undef ) = split( /\s+/, $line );

    $month2 = Decode_Month( $month2 );			# get numeric month
    $year2 = $year1 - 1 if ( $month2 > $month1 );	# last year's logs?

    ( $hour2,$min2,$sec2 ) = split( /:/, $time2 );

    my ($D_y,$D_m,$D_d, $Dh,$Dm,$Ds) =
             Delta_YMDHMS($year2,$month2,$day2, $hour2,$min2,$sec2,
			  $year1,$month1,$day1, $hour1,$min1,$sec1 );

    print qq($line) if ( $Dm <= 30 && !$Dh && !$D_d && !$D_m && !$D_y );

}

close( LOG ); 

```

You'll have to check for bugs.  If it does what I intend, it should also take care of the cases where the month rolls over at midnight or the year rolls over at midnight.  you can make some fake logs with 2 or 3 lines to test these cases.  

If you have any questions about any of the lines, ask.  There is detailed material in the manual pages - [man Date::Calc](http://manpages.ubuntu.com/manpages/raring/en/man3/Date::Calc.3pm.html) and [man perlfunc](http://manpages.ubuntu.com/manpages/quantal/en/man1/perlfunc.1.html).

---

### Post by learnbash on 2013-10-01
Thank buddy it is working, can you please explain your code so i can understand...........

---

### Post by Lars Noodén on 2013-10-01
Here's more annotation, be sure to look up the function names in the manual pages.  There are three - Decode_Month and Delta_YMDHMS from Date::Calc and localtime

```

#!/usr/bin/perl

use strict;
use warnings;
use Date::Calc( 'Decode_Month', 'Delta_YMDHMS' );

# read from file passed as argument or else read stdin
# syslog format expected - month, day, time in 1st 3 columns
my $logfile = shift || "-";

# reserve the variables for use later,
# 1 is for the current date, 2 is for the one in the logs
my ( $sec1, $min1, $hour1, $day1, $month1, $year1 );
my ( $sec2, $min2, $hour2, $day2, $month2, $year2 );

# get the current local time and date using function localtime()
( $sec1, $min1, $hour1, $day1, $month1, $year1, undef, undef, undef ) 
    = localtime( time () );
$year1 += 1900;		# normalize the year
$month1++;		# normalize the month 1= jan

# start reading the log
open( LOG, "$logfile" ) 
    or die( "Could not open '$logfile': $!\n");

# keep reading until nothing is left in the file or input stream
while ( my $line = <LOG> ) {
    $year2 = $year1;		# assume that the log year is this year

    my $time2;			# temp holder for log entry time

    # grab month, day and time from the first three columns of the log
    ( $month2, $day2, $time2, undef ) = split( /\s+/, $line );

    $month2 = Decode_Month( $month2 );			# get numeric month
    $year2 = $year1 - 1 if ( $month2 > $month1 );	# last year's logs?

    ( $hour2,$min2,$sec2 ) = split( /:/, $time2 );	# get h:m:s from log

    # read Delta_YMDHMS in Date::Calc man page
    my ($D_y,$D_m,$D_d, $Dh,$Dm,$Ds) =
             Delta_YMDHMS($year2,$month2,$day2, $hour2,$min2,$sec2,
			  $year1,$month1,$day1, $hour1,$min1,$sec1 );

    # if the difference in time is less than 30 minutes
    print qq($line) if ( $Dm <= 30 && !$Dh && !$D_d && !$D_m && !$D_y );

}

# done let's close the file or stream we were reading
close( LOG ); 

```

Do you have any questions about specific lines?

---

### Post by learnbash on 2013-10-01
awesome, i just need to understand the code, please if you could explain some lines so i can understand it.

---

### Post by Lars Noodén on 2013-10-01
localtime is in the perlfunc manual page that gets the hour, minute, second, etc 

Decode_Month converts written months to numerical months.   Delta_YMDHMS takes two sets of date+time and returns the difference.  Both are in the manual page for Date::Calc

Even if you've not used them before, I do recommend looking at them in this case.  Over time they will become more familiar and thus a more useful resource.

---

### Post by Lars Noodén on 2013-10-01
Also, perl works a lot with lists. So you could assign the values 11, 22, and 33 to $a, $b, and $c like this:

```

( $a, $b, $c ) = ( 11, 22, 33 );

```

A function could return a list.  localtime() does that. So does Delta_YMDHMS(), so does split()

The strength of perl is in regular expression pattern matching.  You've probably already heard of Perl-Compatible Regular Expressions ([pcre](http://www.pcre.org/)), this is where it comes from.  The function split is also in perlfunc, it takes a pattern between //  as the first argument and uses that to split up a string into a list.

---

### Post by learnbash on 2013-10-01
One little request, when i run this against logfile when find a word "prod: pro" then show lines containing word, discard rest lines from 30 minutes of log.

---

### Post by Lars Noodén on 2013-10-01
Can you paste the whole offending line here so I can test it against the code?  Maybe with the line before it and after it.

---

### Post by learnbash on 2013-10-01
line added, after after pro, i deleted the text, actually showing some personal detail, but lines start like that.
```

Oct  1 10:20:21 server1 prod: pro: somedetail-deleted

```

---

### Post by Lars Noodén on 2013-10-01
Unfortuantely, I'm not able to see any errors when running that string through the script.  I put it on its own line, but it is handled like any others.  The script only works with the first part, "Oct  1 10:20:21", and should be ignoring the rest.  Year, month, day, etc should be getting reset with each line read and those are the only things that would cause a line not to get printed.

---

### Post by learnbash on 2013-10-01
Can you paste the code, so i can check at my local.

---

### Post by Lars Noodén on 2013-10-01
The code is above in #13, you can add and remove extra print statements as you need to help with debugging.  That is one method I often use.

---

### Post by learnbash on 2013-10-01
But text searching part [prod: pro: ] is not there? Can you please put that.

---

### Post by Lars Noodén on 2013-10-01
Or are you wanting the script to change its output when encountering that string?

---

### Post by Lars Noodén on 2013-10-01
> **learnbash said:**
> But text searching part [prod: pro: ] is not there? Can you please put that.

Can you explain a little more about what is supposed to happen when that line is encountered?  Is it supposed to find log entries less than 30 minutes old and print them only if they come after the line containing "prod:pro" ?

---

### Post by learnbash on 2013-10-01
Actually When script run that first find last 30 minutes of log file, so for example it greps 200 lines which have last 30 minutes of log. After that i wants to search "prod: pro:" in 200 lines, let suppose that text exist in 10 lines so only show those 10 lines discard 190 lines.

---

### Post by Lars Noodén on 2013-10-01
Would it work to pipe the output through grep then?

```

./last30minoflogs.pl /var/log/syslog | grep "prod: pro:"

```

---

### Post by learnbash on 2013-10-01
Yes Thanks so much, it is working :) you are cool. You are guru in perl, can you please suggest me so i can write perl scripts.

---

### Post by Lars Noodén on 2013-10-01
Perl is fun and very, very useful for running a system.  I picked up just the basics some years ago with books using it at work, but it should be easy to pick up from a lot of sources.  

If your college library has the book "Programming Perl" aka the Camel Book or the book "Learning Perl", that will help.  

There are online sources.  "Beginning Perl" is online free: [http://www.perl.org/books/beginning-perl/](http://www.perl.org/books/beginning-perl/) and then there are some tutorials : [http://learn.perl.org/tutorials/](http://learn.perl.org/tutorials/)

But above all, be comfortable looking up stuff in "man perlfunc" and the other builtin man pages.   See "man perl" for the full list, divided by subject.

---

### Post by Lars Noodén on 2013-10-01
By the way, the module Date::Calc is from the archive [CPAN](http://www.cpan.org/) which has many thousands of modules.  If there is a function or activity you want,  there is probably a module for it.  A good portion of the CPAN modules are already available in Ubuntu via the repositories, so you can add them using the package manager.

---

### Post by ofnuts on 2013-10-01
In practice, you use log rollover so you have only 24 hours or less of logging in any file. Otherwise, whatever the technique (awk, perl, whatever) you will end up doing a lot of file I/O  just to look at the last lines. An application worth its salt will also let you format the time in the logs so that they can be processed (or read) more easily. It could just be a matter of setting the right locale somewhere before starting the thing that produces the log.

---


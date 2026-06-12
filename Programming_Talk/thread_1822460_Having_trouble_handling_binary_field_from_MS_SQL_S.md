---
title: "Having trouble handling binary field from MS SQL Server"
date: 2011-08-10
forum: Programming Talk
---

### Post by 00turtle on 2011-08-10
Hi,

I'm having trouble gathering binary data from a table in MS SQL server from an Ubuntu 10.10 client.  We have software that generates an archive file daily and we have another process that needs to use that file.  I'm using perl to retrieve the file from the database and I can connect just fine with my ODBC connection using the libtdsodbc driver but fields containing more than 4kb are truncated to 4kb.  We are trying to consolidate some tasks from various servers (Windows and Linux) to a single machine and this is the first one that has given me trouble.  I have a perl script that I have used on a Windows client with active perl that does  not truncate the fields but when I run it on Ubuntu, the problem  occurs.  I have tried setting the LongReadLen in perl dbi to byte sizes much larger than the file sizes I'm trying to retrieve and I've tried turning LongTruncOk on and off but I don't think it's the LongTruncOk setting.  The reason being If I have the LongReadLen setting set to a number lower than 4096, and LongTruncOk is off, I get the ever popular error shown below.
DBD::ODBC::st fetchrow_array failed: [unixODBC][FreeTDS][SQL Server]Data truncated (SQL-01004). 

And if I have LongReadLen set to say 5000 (knowing good and well fields being returned by my query will top out over 45 kb, I don't get the truncation error.  So its as if its not producing the error because something else is limiting what is returned before it's length can be evaluated and they get cut off at the 4096 mark.  Prior to that, I thought it might be a problem occurring when writing the binary files to disk after capturing the field so I added a line to check the length of the field being captured before an attempt to write the field to a file and it is definitely being truncated before I try to write it.  I'm really at a loss.  I'm not sure if this a driver limitation problem, some sort of setting in odbc.ini that I'm not aware of, or what.  Below is my script (edited to hopefully be somewhat more viewer friendly).

```
#!/usr/bin/perl 
 
use strict; 
use warnings; 
use DBI; 
use DBD::ODBC;
use bytes; 
 
# Format date range for the query

# This will be yesterday 
my $minusoneday = time - 24 * 60 * 60; 
my ($day, $month, $year)=(localtime($minusoneday))[3,4,5]; 
$month += 1; 
$year += 1900; 
my $yesterday = (($month).'/'."$day".'/'.($year)); 
my $searchdaystart = "\'".$yesterday."\'";

# This will be today 
($day, $month, $year)=(localtime)[3,4,5]; 
$month += 1; 
$year += 1900; 
my $today = (($month).'/'."$day".'/'.($year)); 
my $searchdayend = "\'".$today."\'";

# Now put them together 
my $searchrange = "rdatetime ".'>='." $searchdaystart AND rdatetime ".'<'." $searchdayend"; 

# And now the full query is ready 
my $myquery = "SELECT * FROM table_name WHERE $searchrange";
 
my @results; # To hold the results of the query 
my $outfile = 'arcfile.zip';  # The file name we will write the result to
my $fieldlen;  # To hold the field length for testing 
 
# Set, prepare, and execute the connection 
my $dbh = DBI->connect('DBI:ODBC:my_odbc_connection', "user", "password") or die "Unable to connect"; 
$dbh->{LongReadLen}   = 104857600; #100 MB 
$dbh->{LongTruncOk}   = 0; #turn truncation off 
my $sth = $dbh->prepare($myquery); 
$sth->execute; 

# Find our file in the results and write it to disk 
while(@results = $sth->fetchrow_array) { 
    if($results[4] =~ m/archive_file/i) { 
        $fieldlen = bytes::length $results[5];
        print "$fieldlen\n";  # Print the field length in the terminal 
        open(OUTPUT, ">>$outfile"); 
        binmode OUTPUT; 
        print OUTPUT "$results[5]"; 
        close(OUTPUT); 
    }
} 
```

---

### Post by 00turtle on 2011-08-12
I haven't found a solution to this yet.  :(  Does anyone have any suggestions I could try?

---

### Post by karlson on 2011-08-12
> **00turtle said:**
> Hi,

I'm having trouble gathering binary data from a table in MS SQL server from an Ubuntu 10.10 client.  We have software that generates an archive file daily and we have another process that needs to use that file.  I'm using perl to retrieve the file from the database and I can connect just fine with my ODBC connection using the libtdsodbc driver but fields containing more than 4kb are truncated to 4kb.  We are trying to consolidate some tasks from various servers (Windows and Linux) to a single machine and this is the first one that has given me trouble.  I have a perl script that I have used on a Windows client with active perl that does  not truncate the fields but when I run it on Ubuntu, the problem  occurs.  I have tried setting the LongReadLen in perl dbi to byte sizes much larger than the file sizes I'm trying to retrieve and I've tried turning LongTruncOk on and off but I don't think it's the LongTruncOk setting.  The reason being If I have the LongReadLen setting set to a number lower than 4096, and LongTruncOk is off, I get the ever popular error shown below.
DBD::ODBC::st fetchrow_array failed: [unixODBC][FreeTDS][SQL Server]Data truncated (SQL-01004). 

And if I have LongReadLen set to say 5000 (knowing good and well fields being returned by my query will top out over 45 kb, I don't get the truncation error.  So its as if its not producing the error because something else is limiting what is returned before it's length can be evaluated and they get cut off at the 4096 mark.  Prior to that, I thought it might be a problem occurring when writing the binary files to disk after capturing the field so I added a line to check the length of the field being captured before an attempt to write the field to a file and it is definitely being truncated before I try to write it.  I'm really at a loss.  I'm not sure if this a driver limitation problem, some sort of setting in odbc.ini that I'm not aware of, or what.  Below is my script (edited to hopefully be somewhat more viewer friendly).

```
#!/usr/bin/perl 
 
use strict; 
use warnings; 
use DBI; 
use DBD::ODBC;
use bytes; 
 
# Format date range for the query

# This will be yesterday 
my $minusoneday = time - 24 * 60 * 60; 
my ($day, $month, $year)=(localtime($minusoneday))[3,4,5]; 
$month += 1; 
$year += 1900; 
my $yesterday = (($month).'/'."$day".'/'.($year)); 
my $searchdaystart = "\'".$yesterday."\'";

# This will be today 
($day, $month, $year)=(localtime)[3,4,5]; 
$month += 1; 
$year += 1900; 
my $today = (($month).'/'."$day".'/'.($year)); 
my $searchdayend = "\'".$today."\'";

# Now put them together 
my $searchrange = "rdatetime ".'>='." $searchdaystart AND rdatetime ".'<'." $searchdayend"; 

# And now the full query is ready 
my $myquery = "SELECT * FROM table_name WHERE $searchrange";
 
my @results; # To hold the results of the query 
my $outfile = 'arcfile.zip';  # The file name we will write the result to
my $fieldlen;  # To hold the field length for testing 
 
# Set, prepare, and execute the connection 
my $dbh = DBI->connect('DBI:ODBC:my_odbc_connection', "user", "password") or die "Unable to connect"; 
$dbh->{LongReadLen}   = 104857600; #100 MB 
$dbh->{LongTruncOk}   = 0; #turn truncation off 
my $sth = $dbh->prepare($myquery); 
$sth->execute; 

# Find our file in the results and write it to disk 
while(@results = $sth->fetchrow_array) { 
    if($results[4] =~ m/archive_file/i) { 
        $fieldlen = bytes::length $results[5];
        print "$fieldlen\n";  # Print the field length in the terminal 
        open(OUTPUT, ">>$outfile"); 
        binmode OUTPUT; 
        print OUTPUT "$results[5]"; 
        close(OUTPUT); 
    }
} 
```

First off  I would suggest you use DBD::Sybase rather then DBD::ODBC as your driver.  

Second.  You might have to recompile FreeTDS and Reinstall DBD::Sybase from CPAN in order to get the fields properly.  With Sybase Driver it was a known issue with TDS default build.  This was the case on 8.04, 8.10, 9.04, 10.04, I haven't tested higher versions of Ubuntu but it stands to reason that this is still there.

---

### Post by 00turtle on 2011-08-15
Hi Karlson,

Thanks for the reply.  I tried your suggestions.  To be honest, I don't think I've ever had a need to use the sybase module.  I gave it a try though and didn't have much success.  Possibly just a novice error on my part.  I uninstalled freetds and the libdb-sybase-perl module.  I recompiled from downloaded tars making sure to provide the correct freetds directory in the export config before running the perl Makefile.PL.  I have the correct settings in my freetds.conf file for my SQL connection and I double checked to make sure I added the correct user, password, server, and database defaults when running the make install of the sybase module.  Now my perl script resembles this.

```

#!/usr/bin/perl

use strict;
use warnings;
use DBI;
use DBD::Sybase;
use bytes;

# Format date range for the query

# This will be yesterday
my $minusoneday = time - 24 * 60 * 60;
my ($day, $month, $year)=(localtime($minusoneday))[3,4,5];
$month += 1;
$year += 1900;
my $yesterday = (($month).'/'."$day".'/'.($year));
my $searchdaystart = "\'".$yesterday."\'";

# This will be today
($day, $month, $year)=(localtime)[3,4,5];
$month += 1;
$year += 1900;
my $today = (($month).'/'."$day".'/'.($year));
my $searchdayend = "\'".$today."\'";

# Now put them together 
my $searchrange = "rdatetime ".'>='." $searchdaystart AND rdatetime ".'<'." $searchdayend";

# And now the full query is ready
my $myquery = "SELECT * FROM table_name WHERE $searchrange";

my @results; # To hold the results of the query
my $outfile = 'arcfile.zip';  # The file name we will write the result to
my $fieldlen;  # To hold the field length for testing

# Set, prepare, and execute the connection
$dbh = DBI->connect('DBI:Sybase:server=dbserver', 'user', 'password') or die "Unable to connect";

$dbh->{LongReadLen}   = 104857600; #100 MB
$dbh->{LongTruncOk}   = 0; #turn truncation off
$dbh->do("use my_default_database");
my $sth = $dbh->prepare($myquery);
$sth->execute;

# Find our file in the results and write it to disk
while(@results = $sth->fetchrow_array) {
    if($results[4] =~ m/archive_file/i) {
        $fieldlen = bytes::length $results[5];
        print "$fieldlen\n";  # Print the field length in the terminal
        open(OUTPUT, ">>$outfile");
        binmode OUTPUT;
        print OUTPUT "$results[5]";
        close(OUTPUT);
    }
}

# Terminate the connection

$sth->finish;
$dbh->disconnect();
```

But I get an error which looks to me like I'm either passing invalid login information to the database server or a communication problem with the database server itself.  Both of which I have determined to be false.  Here is the error.

```
DBI connect('server=dbserver','user',...) failed: Server message number=18456 severity=14 state=1 line=0 text=Login failed for user 'user'. OpenClient message: LAYER = (0) ORIGIN = (0) SEVERITY = (78) NUMBER = (34)
Server dbserver, database 
Message String: Adaptive Server connection failed
```

Any thoughts?  I really think I just made an error of some sort when I switched over to the sybase method but I haven't the foggiest idea as to what that might be.

---

### Post by 00turtle on 2011-08-24
I still haven't resolved this.  Does anyone have any further thoughts or suggestions?  If I have to stick with the existing process on our Windows server for this task I will but that would be unfortunate.  :(

---


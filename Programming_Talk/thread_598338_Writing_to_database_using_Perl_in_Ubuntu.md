---
title: "Writing to database using Perl in Ubuntu"
date: 2007-10-31
forum: Programming Talk
---

### Post by wagnermw on 2007-10-31
I am am attempting to write to a MySQL database table. I am coding in Perl. This is what I have so far:

#!/usr/bin/perl -w
use DBI;

$fname=<STDIN>;
chomp $fname;
#$user = "wagnermw";
#$password = "*****"

$dbh = DBI->connect("DBI:MYSQL:dev.mis.uwec.edu;database=wagn er", "wagnermw", "*****");
$dbh->do("insert into test(name) values('$fname')");
$dbh->disconnect;
exit (0);

When I try to run this from the command line, I dont get an error, but the debuging does not complete either. Does anyone have any idea where Im going wrong?? 

Thanks,
-Mitch

---

### Post by slavik on 2007-10-31
Here's a tutorial: [http://www.perl.com/pub/a/1999/10/DBI.html](http://www.perl.com/pub/a/1999/10/DBI.html)

you need to prepare the statement and then execute it.

---

### Post by carlosjuero on 2007-10-31
> **wagnermw said:**
> I am am attempting to write to a MySQL database table. I am coding in Perl. This is what I have so far:

#!/usr/bin/perl -w
use DBI;

$fname=<STDIN>;
chomp $fname;
#$user = "wagnermw";
#$password = "*****"

$dbh = DBI->connect("DBI:MYSQL:dev.mis.uwec.edu;database=wagn er", "wagnermw", "*****");
$dbh->do("insert into test(name) values('$fname')");
$dbh->disconnect;
exit (0);

When I try to run this from the command line, I dont get an error, but the debuging does not complete either. Does anyone have any idea where Im going wrong?? 

Thanks,
-Mitch
Yep, so change your SQL line to
```

$sth = $dbh->prepare("insert into test(name) values(\"$fname\")");
$sth->execute();
$dbh->disconnect;

```
and you should see the results work as expected.

Edit:

Note - if you still are having issues, then reformat the $sth & execute as follows:
```

$sth = $dbh->prepare("insert into test(name) values(?)");
$sth->execute($name);

```

---

### Post by carlosjuero on 2007-10-31
Instead of editing again, I will post how I normally do queries with DBI

I first define the SQL statement as its own string, and use QQ to do the whole thing without escape chars, for example:

```

my $query = qq/ SELECT madd FROM validmails WHERE mid = ? /;

my $sth = $dbh->prepare($query);

$sth->execute($nid);

```

The data linked above has lots of good info too.

---


---
title: "Import log flie data - shell script"
date: 2012-10-28
forum: Programming Talk
---

### Post by 1cookie on 2012-10-28
hi

Can anyone start me off or point me in the right direction as to:

Create a command-line script that will import log file data into the application.  The application will be a PHP/MySQL one.

An example log line:

```

VOTE 1168241980 Campaign:ssss_uk_01B Validity:during Choice:Tupele CONN:MIG00VU MSISDN:00088866655598 GUID:A34-FDS87-FHDHDH-DHDHDHD0 Shortcode:63334

```

I've been very brief here for obvious reasons and there's a lot more to it than I've let on.  

It's an assignment and I don't want to ask "Will you do it for me?" rather, start me off or direct me to a good tutorial for #!/bin/bash beginners. That's assuming #!/bin/bash is the best solution; as of yet I don't even know this much.

---

### Post by Lars Noodén on 2012-10-28
That's the kind of thing I would use perl for.  The package libdbd-mysql-perl gives you the module DBD::mysql which allows you to work with MySQL via an API.  Nothing is better than perl at parsing log files.  

There are other modules for other languages which will provide you an API for MySQL, but this is the kind of task I would use perl for.

---

### Post by 1cookie on 2012-10-28
> **Lars Noodén said:**
> That's the kind of thing I would use perl for.  The package libdbd-mysql-perl gives you the module DBD::mysql which allows you to work with MySQL via an API.  Nothing is better than perl at parsing log files.  

There are other modules for other languages which will provide you an API for MySQL, but this is the kind of task I would use perl for.

Interesting Lars....:)

---

### Post by 1cookie on 2012-10-30
hi

I need to read data in from a file, parse it, then insert each record into a mysql database in Perl. 

So far I have:

```

 #!/usr/bin/perl 

# perl_test.pl

  use warnings;
  use strict;
  use DBI();

 # Connect to the database.
 my $dbh = DBI->connect("DBI:mysql:database=demo;host=localhost",
                        "cookie", "*********",
                        {'RaiseError' => 1});

open (LOGFILE, '/home/cookie/Desktop/data.txt') or die("Could not open log file.");

 foreach my $line (<LOGFILE>) {

    my $name = $1;
    my $age = $2;
    
    ($name, $age) = split(' ', $line);
    
    my $query = 'INSERT INTO perl_test (name, age) VALUES ("$name","$age")';
    my $sth = $dbh->prepare( $query );
    $sth->execute();

    #print "$name $age\n";  debugging - works!

 }

close (LOGFILE);

```// data.txt
```

Peter 34
Andy 23
Steven 29
Jane 67
Laura 17

```When I check the database the script doesn't insert the dynamic ($name, $age) values - rather the actual variables themselves:

```

mysql> select * from perl_test;
+----+---------+------+
| id | name    | age  |
+----+---------+------+
|  1 | Peter   |   76 |
|  2 | $name   |    0 |
|  3 | $name   |    0 |
|  4 | $name   |    0 |
|  5 | $name   |    0 |
|  6 | $name   |    0 |
|  7 | $name   |    0 |
+----+---------+------+
13 rows in set (0.01 sec)

```Ignore the first value in the table below; I did that manually.

I'm pretty sure to interpolate values in strings we use double quotes within MySQL or am I missing a Perl syntax quirk?




A clue would be good?

---

### Post by Lars Noodén on 2012-10-30
It is the single quotes that are throwing off your statement.  For that reason, qq,qw and q operators are preferred around the base statement.  That allows you to use single and double quotes inside the statement without trouble.

Try this line instead:
```

my $query = qq(INSERT INTO perl_test (name, age) VALUES ("$name","$age"));

```

Nice that you picked up prepare/execute already.  That helps in several areas.  If you take it further, you can also use place holders for the variables in the prepared statement.

---

### Post by Lars Noodén on 2012-10-30
Here are two examples of placeholders.  

[http://stackoverflow.com/questions/1994408/perl-update-multiple-rows-with-one-mysql-call](http://stackoverflow.com/questions/1994408/perl-update-multiple-rows-with-one-mysql-call)

[http://stackoverflow.com/questions/11246427/placeholder-use-in-perl-dbi](http://stackoverflow.com/questions/11246427/placeholder-use-in-perl-dbi)

The query only needs to be created / prepared once then, but it has other advantages a far as string management goes.

---

### Post by 1cookie on 2012-10-30
> **Lars Noodén said:**
> 
Try this line instead:

Thanks Lars :)

---

### Post by 1cookie on 2012-10-31
OK, now I need to scale it up a little. This part is a small part of a bigger problem - full details here: [http://acookson.org/sms-voting-campaign/](http://acookson.org/sms-voting-campaign/) 

My elementary script now loops through a file and picks out selected field values with the use of the substr construct:

```

 #!/usr/bin/perl 

  use warnings;
  use strict;
  use DBI();

 # Connect to the database.
 my $dbh = DBI->connect("DBI:mysql:database=voting_campaigns;host=localhost",
                        "cookie", "*********",
                        {'RaiseError' => 1});

open (LOGFILE, '/var/www/voting/votes.txt') or die("Could not open log file.");

 foreach my $line (<LOGFILE>) {

    my $vote; 
    my $epoch; 
    my $campaign; 
    my $validity; 
    my $choice; 
    my $CONN; 
    my $MSISDN; 
    my $GUID; 
    my $Shortcode;    
    
    ($vote, $epoch, $campaign, $validity, $choice, $CONN, $MSISDN, $GUID, $Shortcode) = split(' ', $line);

    # parse the field:value entries...
    $campaign = substr $campaign, 9, 11, ''; # ssss_uk_01C
    $validity = substr $validity, 9, 6, ''; # during
    $choice = substr $choice, 7, 10, ''; # Brown

    my $sth = $dbh->prepare("INSERT INTO voting (vote, epoch, campaign, validity, choice, 
    CONN, MSISDN, GUID, Shortcode) VALUES (?,?,?,?,?,?,?,?,?)");

    $sth->execute($vote, $epoch, $campaign, $validity, $choice, $CONN, $MSISDN, $GUID, $Shortcode);
    
    # debug
    print "$campaign $validity $choice \n"; # ssss_uk_01B during Green 

 }

close (LOGFILE);


```All good so far, the script executes successfully.  Now I need to focus on:

Any lines that are not well-formed should be discarded.  Your script should assume the data is in uncompressed plain text.

A brief explanation of what we would need to consider if we wanted to import a large number of similar files (millions of votes)

- ‘Choice:’ indicates the candidate the user is voting for. In every campaign there will be a limited set of candidates that can be voted for. If Choice is blank, it means the system could not identify the chosen candidate from the text of the SMS message. 

All such messages should be counted together as ‘errors’, irrespective of their Validity values. There is a limited set of values for ‘Choice’, each of which represents a candidate who can be voted for.

I'm thinking a regular expression is the way forward:

```

    my $MSISDN; 
    my $GUID; 
    my $Shortcode;

  # Skip lines that have empty field values... 

    next if !~ /^VOTE\sCampaign:\w{11,}\sValidity:\w{6,}\sChoice:\w{2,30}\s $/;
    
    # Keep count of errors or malformed lines
    my $errors++;

($vote, $epoch, $campaign, $validity, $choice, $CONN, $MSISDN, $GUID, $Shortcode) = split(' ', $line);

    # parse the field:value entries...
    $campaign = substr $campaign, 9, 11, ''; # ssss_uk_01C

```I've not ran it yet. How bad is it? I have my doubts over the

```

next if
my $errors++;

```construct, It's not going to fly is it? I'd expect $errors to increment regardless of the next statement. A more logical way for me would be:

```

my $regex = /^VOTE\sCampaign:\w{11,}\sValidity:\w{6,}\sChoice:\w{2,30}\s $/;
if(!$regex){
  # bad line, increment $errors..
 $errors++;
# skip to next line
 next
}
 #continue loop

```but I'm not using Perl now, I'm using psuedo code.

---

### Post by Lars Noodén on 2012-10-31
I think the prepare statement can probably go outside the loop in principle.  

Also, the multiple my declarations can be applied when the variables are first used.  But that's more a style thing.  Both are "right"

```

my ($vote, $epoch, $campaign, $validity, $choice, $CONN, $MSISDN, $GUID, $Shortcode) = split(' ', $line);

```

If none of the values will be blank or zero (0), then you could check like this:

```

if ($vote && $epoch && $campaign && $validity && $choice && $CONN && $MSISDN && $GUID && $Shortcode) {
  $errors++;
  next;
}

```

Remember that 'my' can make a variable local to a loop or statement.  So errors should probably be declared at the beginning of the program so it can be used at the end of the program.

```

my $a = 1;
print qq(a1=$a\n);
if ( $a ) {
 my $a = 2;
 print qq(a2=$a\n);
}
print qq(a3=$a\n);

```

---

### Post by 1cookie on 2012-11-01
> **Lars Noodén said:**
> I think the prepare statement can probably go outside the loop in principle. 
Indeed it's better there me thinks.

> 
Also, the multiple my declarations can be applied when the variables are first used.  But that's more a style thing.  Both are "right"
It certainly makes the code less bloated.

> 
Remember that 'my' can make a variable local to a loop or statement.  So errors should probably be declared at the beginning of the program so it can be used at the end of the program.
Thanks, I'll have to keep my eyes on scope. I'm finding Perl has syntax very similar to PHP. 

My revised code now looks like:

```

 #!/usr/bin/perl 

  use warnings;
  use strict;
  use DBI();

 # Connect to the database.
 my $dbh = DBI->connect("DBI:mysql:database=voting_campaigns;host=localhost",
                        "cookie", "*********",
                        {'RaiseError' => 1});

    my $sth = $dbh->prepare("INSERT INTO voting (vote, epoch, campaign, validity, choice, 
    CONN, MSISDN, GUID, Shortcode) VALUES (?,?,?,?,?,?,?,?,?)");

    open (LOGFILE, '/var/www/voting/votes.txt') or die("Could not open log file.");

    my $errors = 0;
    
 foreach my $line (<LOGFILE>) {    
    
        my ($vote, $epoch, $campaign, $validity, $choice, $CONN, $MSISDN, $GUID, $Shortcode) = split(' ', $line);

    # parse the field:value entries...
    $campaign = substr $campaign, 9, 11, ''; # ssss_uk_01C
    $validity = substr $validity, 9, 6, ''; # during
    $choice = substr $choice, 7, 10, ''; # Brown

    if ($vote && $epoch && $campaign && $validity && $choice && $CONN && $MSISDN && $GUID && $Shortcode) {

          $sth->execute($vote, $epoch, $campaign, $validity, $choice, $CONN, $MSISDN, $GUID, $Shortcode);
        # debug
        print "$campaign $validity $choice \n"; # ssss_uk_01B during Green
        next;
    } 

    $errors++;

 }

close (LOGFILE);


# debug
print qq(errors=$errors\n);

```And if I edit votes.txt with null values - the script reports them:

```

ssss_uk_01B during Tupele 
ssss_uk_01B pre Joseph 
ssss_uk_01B during Balls 
ssss_uk_06B during Balls 
ssss_uk_01B during Brown 
ssss_uk_01D pre Boring 
ssss_uk_01B during Green 
errors=3


```I think I'm pretty close to the deliverables required (for this part of assignment). Thanks again Lars.

---

### Post by 1cookie on 2012-11-30
hi

If I can just stay on topic a little while longer. I made this part of the assignment a little more complicated with a normalised database.
My database is now as : [http://acookson.org/wp-content/themes/cookie_23112012/img/sms_voting.png](http://acookson.org/wp-content/themes/cookie_23112012/img/sms_voting.png)

And I'm trying to insert records into the voting table; making use of a switch statement to dynamically define foreign keys in order to populate the table. My new Perl script is:

```

 #!/usr/bin/perl 

  use warnings;
  use strict;
  use Switch;
  use DBI();

 # Connect to the database.
 my $dbh = DBI->connect("DBI:mysql:database=sms_voting;host=localhost",
                        "cookie", "**********",
                        {'RaiseError' => 1});

    my $sth = $dbh->prepare("INSERT INTO voting (epoch, validity, choice, campaigns_id, candidates_id ) VALUES (?,?,?,?,?)");

    open (LOGFILE, '/var/www/voting/votes.txt') or die("Could not open log file.");

    my $errors = 0;
    
 foreach my $line (<LOGFILE>) {    
    
        my ($vote, $epoch, $campaign, $validity, $choice, $CONN, $MSISDN, $GUID, $Shortcode) = split(' ', $line);

    # parse the field:value entries...
    $campaign = substr $campaign, 8, 11, '';
    $validity = substr $validity, 9, 6, ''; # during
    $choice = substr $choice, 7, 10, ''; # Brown

    # case statements to define correct foreign keys...

    my $campaign_id = 0;
    my $candidate_id = 0;

     switch ($campaign) {
            case ("ssss_uk_01B")     { $campaign_id = 1 } 
            case ("ssss_uk_01C")     { $campaign_id = 2 } 
            case ("ssss_uk_01D")     { $campaign_id = 3 } 
            case ("ssss_uk_01E")     { $campaign_id = 4 } 
            case ("ssss_uk_01F")     { $campaign_id = 5 } 
            case ("ssss_uk_01G")     { $campaign_id = 6 } 
    }
    
    switch ($choice) {
            case ("Brown")         { $candidate_id = 1 } 
            case ("Cameron")     { $candidate_id = 2 } 
            case ("Balls")         { $candidate_id = 3 } 
            case ("Green")         { $candidate_id = 4 } 
            case ("Boring")     { $candidate_id = 5 } 
            case ("Tupele")     { $candidate_id = 6 } 
    }

    if ($epoch && $validity && $choice && $campaign_id && $candidate_id ) {

          $sth->execute($epoch, $validity, $choice, $campaign_id, $candidate_id);
        # debug
        print "$epoch $validity $choice \n"; # 1161048980 during Green
        next;
    } 

    $errors++;

 }

close (LOGFILE);


# debug
print qq(errors=$errors\n);


```The script should now insert records into 'voting' table like so:

```
INSERT INTO voting (epoch, validity, choice, campaigns_id, candidates_id ) VALUES ('1161048980', 'during', 'Brown', 1, 1 )
``` It doesn't!

```

mysql> select * from voting;
Empty set (0.00 sec)

```confirms this.


The script has effectively just looped through the votes.txt file without inserting records?

No errors are reported so it isn't a syntax error. Where has my logic gone amiss?

---

### Post by 1cookie on 2012-12-02
Edit and solved:

[http://stackoverflow.com/questions/13659928/import-log-file-data-into-an-application](http://stackoverflow.com/questions/13659928/import-log-file-data-into-an-application)

---


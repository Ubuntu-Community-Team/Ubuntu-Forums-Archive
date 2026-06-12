---
title: "Shell script to loop through data in MySQL (array troubles!)"
date: 2007-04-24
forum: Programming Talk
---

### Post by feenster on 2007-04-24
Hi all,
I am trying to write a shell script that will gather some rows from MySQL, and loop through (doing other commands, but that bit isn't important). However, i'm struggling to work out how to do multi-dimensional arrays. 

Say my table has 3 fields:
```
id
username
password

```
And there are 10 rows in there at the moment. I want to loop get all rows from MySQL, then loop through, slotting the different fields into different commands. My code thus far looks like this:
```
users=(`echo 'SELECT * FROM users;' | mysql -u ${USERNAME} -h ${HOST} --password=${PASSWORD} -D ${DATABASE}`)

for d in "${users[@]}"; do
        echo ${d}
done

```
But as you might imagine, this just presents me with a big long list of data from each field (ie., it prints 30 lines). Can anyone help me out as to how to have it in a 2D array so that I can refer to ${d["username"]} or something like that?

Cheers,
  Matt

---

### Post by yaaarrrgg on 2007-04-24
I don't think mysql will actually return a multidimenional array inside a shell script like that... more than likely it will just be a giant chunk of text.  It might be possible to cut this into pieces (on newlines, feild delimters).  

Although IMO a much better approach would just be to use another language (like Perl, Python, or Ruby) that's more suited for database interaction.

Edit: also, here's another way to execute pure sql from a command line script, without mixing it with bash scriptiing:
```

#!/bin/sh
--/. &> /dev/null; exec mysql -u root -ppassword -D test "$@" < $0

SELECT * from  test2;


```

---

### Post by feenster on 2007-04-25
Hi there,
I'm fairly decent with PHP, so I think then it might be better to install PHP and do it that way. Thanks for taking the time to reply :-)

Cheers,
  Matt

---

### Post by phossal on 2007-04-25
Install PHP? For something you were trying to attack with a shell script?

Why not use perl (or python)? They're so well suited for tasks like this. Here is a perl example of a database connection: 


```
#/usr/bin/perl
use DBI;

dbiConnect();
dbiQuery();
dbiGetRS();



print @field1;
print @field2;




# Issue SQL
sub dbiQuery() {
	$sql = "SELECT Field1, Field2 FROM <TABLE>";
	$sth = $dbh->prepare($sql);
	$sth->execute();
}


# Get Result Set
sub dbiGetRS() {
	$counter = 0;
	while (@row = $sth->fetchrow_array) {
		push(@field1, $row[$counter]);
		push(@field2, $row[$counter ++]);

		$counter ++;
	}
}



# Database Connection
sub dbiConnect() {
	$dsn = 'DBI:mysql:<DATABASE>:localhost';
	$db_user_name = 'root';
	$db_password = '';
	$dbh = DBI->connect($dsn, $db_user_name, $db_password);
}
```

---


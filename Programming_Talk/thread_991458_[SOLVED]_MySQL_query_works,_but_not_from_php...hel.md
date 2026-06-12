---
title: "[SOLVED] MySQL query works, but not from php...help?"
date: 2008-11-23
forum: Programming Talk
---

### Post by Griff on 2008-11-23
from php it looks like this:
$query = "UPDATE Flight F SET F.seats = F.seats-$rseats WHERE (F.fid = $fid)";
$result = mysql_query($query);

I tested it from the mysql command prompt first though like so:
UPDATE Flight F SET F.seats = F.seats-1 WHERE (F.fid = 1);

The bottom one works, but it won't from php and it's driving me crazy!  I'm not receiving an error message either!

Thanks,
Griff

---

### Post by Dr Small on 2008-11-23
For one, that type of query should have no usable result (besides true or false).
Try this:
[php]$query = "UPDATE Flight F SET F.seats = F.seats-$rseats WHERE (F.fid = $fid)";
mysql_query($query) or die(mysql_error());[/php]

---

### Post by Griff on 2008-11-23
> **Dr Small said:**
> For one, that type of query should have no usable result (besides true or false).

Try this:
[php]$query = "UPDATE Flight F SET F.seats = F.seats-$rseats WHERE (F.fid = $fid)";
mysql_query($query) or die(mysql_error());[/php]
I was looking for a change in the database itself.

mysql_error() doesn't give me anything for this query.

Thanks,
Griff

---

### Post by Dr Small on 2008-11-23
> **Griff said:**
> I was looking for a change in the database itself.

mysql_error() doesn't give me anything for this query.

Thanks,
Griff
Oh, then in that case, you would probably want to use:
[php]$query = "UPDATE Flight F SET F.seats = F.seats-$rseats WHERE (F.fid = $fid)";
$result = mysql_query($query);

if($result){
    echo 'The database has been updated. Preform whatever you choose in this area.';
} else {
    echo 'There was nothing to update in the database.';
}[/php]

---

### Post by Griff on 2008-11-23
$query = "UPDATE Flight F SET F.seats = F.seats-1 WHERE (F.fid = 3)";
$result = mysql_query($query);

if($result){
    echo 'The database has been updated. Preform whatever you choose in this area.';
} else {
    echo 'There was nothing to update in the database.';
}

I changed my variable to constants above, and no matter what I get the 'There was nothing to update in the database.' response.  Why would that query not work?  If I copy and paste than into the mysql cli it works fine.

---

### Post by Griff on 2008-11-23
This is what I'm trying to do.  The user is reserving so many seats for a given flight.  I'm wanting to subtract this number from the number of total seats on the plane.  I.E. $total_seats = $total_seats - $reserved_seats.  Maybe there's another way to do this? I really cannot see why this works on the mysql cli and not under php.

Thanks,
Griff

---

### Post by s.fox on 2008-11-24
You are actually connecting to your Database aren't you?
If not use something like this: 
[PHP]
$conn = mysql_connect("localhost", "username", "password");
// Select the database
$db = mysql_select_db("database");
// Query the table
$query = 'SELECT * from tableName';
$result = mysql_query($query) or die(mysql_error());
[/PHP]

Hope this helps :)

---

### Post by ufis on 2008-11-24
try:
[php]
$query = "UPDATE `Flight` AS F SET F.`seats` = F.`seats` - " . $rseats . " WHERE F.`fid` = " . $fid;
echo($query); //just to see how it comes out on the other side 
[/php]
Note all the ``s ... thats ` not '

---

### Post by Griff on 2008-11-24
> **Ash R said:**
> You are actually connecting to your Database aren't you?
If not use something like this: 
[PHP]
$conn = mysql_connect("localhost", "username", "password");
// Select the database
$db = mysql_select_db("database");
// Query the table
$query = 'SELECT * from tableName';
$result = mysql_query($query) or die(mysql_error());
[/PHP]

Hope this helps :)

Yep, I have a query above this one that does execute.

---

### Post by Griff on 2008-11-24
OK. Solved.  Everyone may now yell at for not applying Occam's Razor to this problem.  The user I was testing the webpage under did not have permission to access or update the Flight table.  This is somewhat troubling though, because according to the php wiki: 

mysql_query() will also fail and return FALSE  if the user does not have permission to access the table(s) referenced by the query.

Which it didn't or at least didn't pass anything to mysql_error().

Thanks all for the help.  I'll be applying 'thanks' for all your time spent trying to be helpful. :)

Thank you,
Griff

---


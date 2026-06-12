---
title: "MySQL error on simple insert into single table"
date: 2011-05-19
forum: Programming Talk
---

### Post by cdaringe on 2011-05-19
Hi all:

Maybe it just late.  Maybe this is my first experience with MySQL***.  I'm trying to write a BOM/PLC web-based mgr for the RepRap project (cdaringe.net).

Can't figure out this error i get when trying to simply add a record to the "item" table.  This is from executing the form I have posted @ [http://cdaringe.net/createPN.php](http://cdaringe.net/createPN.php) .

```
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'DESC,source,uom,rev,lifecycle)VALUES ('ABCD123','ABCD123ABCD123ABCD123','ROUTABL' at line 1

```


The relevant code that is gen'in the error is ~ the very bottom of this!  See $insertNewQuery.
```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
<html>
   <head>
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
      <title></title>
   </head>
   <body>
      <?php
      
/*GRAB POSTED VALUES FROM PN FORM SUBMIT, createPN.php*/
      //strtoupper converts all letters to uppercase!
$pn = strtoupper($_POST['pn']);
$description = strtoupper($_POST['description']);
$source = strtoupper($_POST['source']); //i.e. procurement
$uom = strtoupper($_POST['uom']);
$lifecycle = strtoupper($_POST['lifecycle']);

/*DB connect parameter*/
...
$database="cdarin5_bom";
$conn = mysql_connect($host,$username,$password);
/*connet to BOM DB*/
mysql_select_db($database, $conn);

   //Validate data
   /// - 1 - PN requested doesn't already exist
      //query to see if that PN already exists
      $countPNsQuery = "SELECT PN, COUNT(PN) FROM item WHERE item.PN='".$pn."'";
      $numberPNsResult= mysql_query($countPNsQuery) or die(mysql_error());
      while($row = mysql_fetch_array($numberPNsResult)){              //review results of PN query.  if results return a single PN, we know that the PN already exists.  fail it.
       if ($row['COUNT(PN)']>0){
         $failureText = "There is currenlty already ". $row['COUNT(PN)'] ." PN already in the item table.  You must create a unique part number";
       }
      }
   /// - 2 - DESCRIPTION length
      if (strlen($description)<10){
         $failureText = "Your description is too short.  It must be @ least 10 characters long.  By following the standard PN DESCRIPTION FORMAT, your description should easily be longer than this!";
      }
      
      /// - 3 - Source check
      if ($source=="BUY" OR $source=="ROUTABLE" OR $source=="PHANTOM"){
      }
      else{
         $failureText = "Why are you hacking?  Hacking is for a$*holes.  Get real, dawg! [source]";
      }

      /// - 4 - Lifecycle input check
      if ($lifecycle=="STANDARD" OR $lifecycle=="RD"){
      }
      Else{
         $failureText = "Why are you hacking?  Hacking is for a$*holes.  Get real, dawg! [lifecycle]";
      }
     /// - 5 - Lifecycle auto-assign
     switch ($lifecycle) {
       case "STANARD":
           $rev = "A";
       case "RD":
           $rev = "1";
      } 
      
      
   //Update item's table with new PN
   if (strlen($failureText)>0){
      echo $failureText . "</br>";
      echo "Part creation has failed.  Please resolve issues & reattempt.";
   }
   else{
      $insertNewQuery = "INSERT INTO item (PN,DESC,source,uom,rev,lifecycle) VALUES ('".$pn."','".$description."','".$source."','".$uom."','".$rev."','".$lifecycle."')";
      mysql_query($insertNewQuery) or die(mysql_error());
      ECHO "NEW PN CREATED! YAHOO!";
   }
      ?>
   </body>
</html>


```

Copied straight out of phpMyAdmin on the 'item' table...
```

Field	Type	Collation
PN	varchar(7)	ascii_bin
DESC	varchar(30)	ascii_bin
source	varchar(8)	ascii_general_ci
uom	varchar(5)	ascii_general_ci
rev	varchar(2)	utf8_general_ci
lifecycle	varchar(7)	ascii_general_ci

```

Any tips?  What is wrong with my syntax?

Thanks!

-CD

---

### Post by Barrucadu on 2011-05-19
"desc" is a reserved word.

---

### Post by prohp on 2011-05-19
but you CAN use desc, just put it inside ` - `DESC`.

---

### Post by Some Penguin on 2011-05-19
```

"INSERT INTO item (PN,DESC,source,uom,rev,lifecycle) VALUES ('".$pn."','".$description."','".$source."','".$uom."','".$rev."','".$lifecycle."')";

```

On a related note, **don't do this**.  Specifically, don't assemble a query via string concatenation of non-escaped user input.  What if, say, $description happened to be

```

'); DROP TABLE item;--

```

for instance?

[http://www.php.net/manual/en/function.mysql-real-escape-string.php]("http://www.php.net/manual/en/function.mysql-real-escape-string.php") exists for a reason.

---

### Post by Barrucadu on 2011-05-19
Even better, use prepared statements to completely nullify a possibility of SQL injection.

---

### Post by indytim on 2011-05-19
Additional hint:

If you're getting an error on a sql statement, do an "echo" or print on the sql statement before processing.  99.5% of the time, the snytax error will jump out at you.

-IndyTim DataMan

---

### Post by satanselbow on 2011-05-19
> **prohp said:**
> but you CAN use desc, just put it inside ` - `DESC`.

That is just stunning bad practice and asking for trouble. Reserved words are there for a reason...

I knew  a guy who created a mySQL table with a field called "FORMAT" and populated it with letters of the alphabet... why don't you give that a try ;)

---

### Post by cdaringe on 2011-05-24
what a bummer!  who woulda thought 'desc' was a reserved word.
well, i tried 'poor syntax' just as a TEST, and it still didn't roll.  interesting.  when i have some free time this weekend i'll update the field in the table to the full word, description.

a follow up question--i have successfully read descriptions OUT of the table.  does it make sense that i only have issues INSERTING data into this field?

---

### Post by cdaringe on 2011-07-12
2 months later!  patched it up. thanks guys!

---


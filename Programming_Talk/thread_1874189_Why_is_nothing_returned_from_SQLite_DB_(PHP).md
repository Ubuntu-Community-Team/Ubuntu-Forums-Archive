---
title: "Why is nothing returned from SQLite DB? (PHP)"
date: 2011-11-02
forum: Programming Talk
---

### Post by kevinharper on 2011-11-02
When I run the follwing via a php file
```

$query = "SELECT * FROM lead_info
                ORDER BY ROWID DESC LIMIT 1";
 
$result = sqlite_query($query, $db) or die("Retrieve Query Failed");
$row = sqlite_fetch_array($result);
print("ID: " . $row['rowid'] . "<br />");
print("Name: " . $row['name'] . "<br />");
print("E-mail: " . $row['email'] . "<br />");
print("Phone: " . $row['phone'] . "<br />");
print("Phone Type: " . $row['phonetype'] . "<br />");
print("Country: " . $row['country'] . "<br />");
print("Date: " . $row['date'] . "<br />");
print("Comment: " . $row['comment'] . "<br />");

```

nothing prints out on the webpage. Printing $result give me a blank ObjectID.

I've tested the query and that works.
Using PHP4 and SQLite3 on Monkey web-server (hosted on Damn Small Linux).

---

### Post by Arndt on 2011-11-02
> **kevinharper said:**
> When I run the follwing via a php file
```

$query = "SELECT * FROM lead_info
                ORDER BY ROWID DESC LIMIT 1";
 
$result = sqlite_query($query, $db) or die("Retrieve Query Failed");
$row = sqlite_fetch_array($result);
print("ID: " . $row['rowid'] . "<br />");
print("Name: " . $row['name'] . "<br />");
print("E-mail: " . $row['email'] . "<br />");
print("Phone: " . $row['phone'] . "<br />");
print("Phone Type: " . $row['phonetype'] . "<br />");
print("Country: " . $row['country'] . "<br />");
print("Date: " . $row['date'] . "<br />");
print("Comment: " . $row['comment'] . "<br />");

```

nothing prints out on the webpage. Printing $result give me a blank ObjectID.

I've tested the query and that works.
Using PHP4 and SQLite3 on Monkey web-server (hosted on Damn Small Linux).

What happens if you run the code in a terminal window?

---

### Post by kevinharper on 2011-11-02
that's what I meant by tested the query...

I ssh'd to server
$sqlite leads
>SELECT * FROM lead_info ORDER BY ROWID DESC LIMIT 1;

It works. I get the row w/ the highest ROWID - the last record entered.

EDIT: This is the second query of the script. The first also uses $query and $results. I thought it may be a problem. So, JUST NOW, I changed vars to $query2 and $results2. Made no difference. :(

---

### Post by Some Penguin on 2011-11-02
[http://php.net/manual/en/function.sqlite-fetch-array.php]("http://php.net/manual/en/function.sqlite-fetch-array.php")

Judging from that, I have to wonder whether you swapped the order of the database handle and the query.

---

### Post by kevinharper on 2011-11-03
Yeah.. I thought that also at one point. But if there is no second argument, it defaults to SQLITE_BOTH... I have also explicitly indicated SQLITE_BOTH & SQLITE_ASSOC (in separate tries) and nothing.

Is that what you were referring to?

---

### Post by kevinharper on 2011-11-03
@Arndt is this:
> **kevinharper said:**
> 
I ssh'd to server
$sqlite leads
>SELECT * FROM lead_info ORDER BY ROWID DESC LIMIT 1;

It works. I get the row w/ the highest ROWID - the last record entered.

Is this what you meant by "run the code in a terminal"?

---

### Post by kevinharper on 2011-11-03
Here's the whole thing:
```

      1 <?
      2 // Inserts lead info into lead_info table. Info coming from add_new_lead        .php
      3 
      4 include_once "header.php";
      5 
      6 $month = $_POST['month'];
      7 $day   = $_POST['day'];
      8 $year  = $_POST['year'];
      9 $date  = $year . "-" . $month . "-" . $day;
     10 
     11 $name  = $_POST['name'];
     12 $email = $_POST['email'];
     13 $phone = $_POST['phone'];
     14 $phonetype = $_POST['phonetype'];
     15 $country = $_POST['country'];
     16 $comment = $_POST['comment'];
     17 
     18 /*print("Date: " . $month . "/" . $day . "/" . $year . "<br />");
     19 print("Name: " . $name . "<br />");
     20 print("E-mail: " . $email . "<br />");
     21 print("Phone: " . $phone . "<br />");
     22 print("Country: " . $country . "<br />");
     23 print("Phone Type: " . $phonetype . "<br />");
     24 print("Comments: <br />" . $comment);*/
     25 
     26 // INSERT LEAD INFORMATION
     27 $query = "INSERT INTO lead_info(name,email,phone,phonetype,country,date,        comment)
     28                 VALUES('" . $name               . "'," .
     29                         "'" . $email            . "'," .
     30                         "'" . $phone            . "'," .
     31                         "'" . $phonetype        . "'," .
     32                         "'" . $country          . "'," .
     33                         "'" . $date             . "'," .
     34                         "'" . $comment          . "')";
     35 
     36 sqlite_query($query, $db) or die("Query Failed");
     37 
     38 // RETRIEVE INFO FROM LAST ENTRY
     39 $query = "SELECT * FROM lead_info
     40                 ORDER BY ROWID DESC LIMIT 1";
     41 
     42 $result = sqlite_query($query, $db) or die("Retrieve Query Failed");
     43 $row = sqlite_fetch_array($result);
     44 print("ID: " . $row['rowid'] . "<br />");
     45 print("Name: " . $row['name'] . "<br />");
     46 print("E-mail: " . $row['email'] . "<br />");
     47 print("Phone: " . $row['phone'] . "<br />");
     48 print("Phone Type: " . $row['phonetype'] . "<br />");
     49 print("Country: " . $row['country'] . "<br />");
     50 print("Date: " . $row['date'] . "<br />");
     51 print("Comment: " . $row['comment'] . "<br />");
     52 
     53 include_once "footer.php";
     54 ?>

```
The script gets info from an HTML form.

The first query... the one that inserts data works fine. The server times out often when submitting the form but that's just the computer this is all running on. I simply go back and resubmit the info. But when it goes through, the data is inserted into the table but nothing is retrieved.

Hope this helps in providing additional cues as to what is going on. I've used mySQL quite a bit but this is my first time with SQLite. But it doesn't seem like I should be having this problem.

---

### Post by kevinharper on 2011-11-03
This may help...

I added
```

     43 if($result)
     44         print('$result is blank');

```
And it prints out "$result is blank" on the web page. So it looks like the query is executing, otherwise it would die & err w/ "Retrieve Query Failed", right?

To me, at least, it looks like nothing is being assigned to $result.

---

### Post by Arndt on 2011-11-04
> **kevinharper said:**
> @Arndt is this:

Is this what you meant by "run the code in a terminal"?

No, I meant run the php code.

---

### Post by kevinharper on 2011-11-04
I commented out the everything related to inserting data and ran. So it should have simply returned the last row.

From SQLite, this is what I get (and what I am expecting to get):

EDIT: The following columns are messed up on the page, but the first row is a header, not results.

sqlite> SELECT * FROM lead_info ORDER BY ROWID DESC LIMIT 1;
name        email       phone       phonetype   country     date        comment        
----------  ----------  ----------  ----------  ----------  ----------  ---------------
fritest     email       phone       home        country     2011-01-01  1st Friday test

I commented everything out from the script except for what is essential for the SELECT statement. Here is what was left:
```

1 <?

5 include_once "db_config.php";

42 // RETRIEVE INFO FROM LAST ENTRY
43 $query = "SELECT * FROM lead_info
44                 ORDER BY ROWID DESC";
45 
46 $result = sqlite_query($query, $db) or die("Retrieve Query Failed");
47 print('$result: ' . $result);
48 
49 $row = sqlite_fetch_array($result);
50 print("ID: " . $row['rowid'] . "<br />");
51 print("Name: " . $row['name'] . "<br />");
52 print("E-mail: " . $row['email'] . "<br />");
53 print("Phone: " . $row['phone'] . "<br />");
54 print("Phone Type: " . $row['phonetype'] . "<br />");
55 print("Country: " . $row['country'] . "<br />");
56 print("Date: " . $row['date'] . "<br />");
57 print("Comment: " . $row['comment'] . "<br />");

60 ?>

```
I ran it as:
dsl@0[bin]$ vim ../../monkey-0.9.2/htdocs/insert_lead.php.php

And got:
Content-type: text/html
X-Powered-By: PHP/4.3.7

$result: ObjectID: <br />Name: <br />E-mail: <br />Phone: <br />Phone Type: <br />Country: <br />Date: <br />Comment: <br />

So, exactly the same result.

---

### Post by kevinharper on 2011-11-05
WOW... I'm even more confused now! This script continues to display NOTHING. I did, however, enclose lines 43-51 inside a while loop and had along w/ a counter. The counter only goes up to the # of results! So it is pulling the results, I'm just unable to print them out.

But what is just COMPLETELY giving me a headache is that I decided to skip this script for now and go on to another one. Here is the code for that one:
```

      1 <?
      2 $pg_title = "Home";
      3 
      4 include_once "header.php";
      5 
      6 $query = "SELECT date, name, country, phone, phonetype FROM lead_info";
      7 $result = sqlite_query($query, $db) or die("Select Query Failed");
      8 ?>
      9 
     10 <table width="1000" align="center" border="1">
     11 
     12 <?
     13 while($row = sqlite_fetch_array($result))
     14 {
     15         print("<tr>");
     16         print("  <td>" . $row["date"]                   . "</td>");
     17         print("  <td>" . $row["name"]                   . "</td>");
     18         print("  <td>" . $row["country"]                . "</td>");
     19         print("  <td>" . $row["phone"]                  . "</td>");
     20         print("  <td>" . $row["phonetype"]              . "</td>");
     21         print("</tr>");
     22 }
     23 ?>
     24 
     25 </table>
     26 
     27 <?
     28 include_once "footer.php";
     29 ?>

```
THIS PAGE WORKS! IT DISPLAYS EVERYTHING! Does anyone see any difference in the query or the way that the retrieved vars are handled and printed?

EDIT: PS: Before posting this last reply, I went back to the original script and changed $row['foo'] to $row["foo"], but the problem continued.

---

### Post by Arndt on 2011-11-06
> **kevinharper said:**
> WOW... I'm even more confused now! This script continues to display NOTHING. I did, however, enclose lines 43-51 inside a while loop and had along w/ a counter. The counter only goes up to the # of results! So it is pulling the results, I'm just unable to print them out.

But what is just COMPLETELY giving me a headache is that I decided to skip this script for now and go on to another one. Here is the code for that one:
```

      1 <?
      2 $pg_title = "Home";
      3 
      4 include_once "header.php";
      5 
      6 $query = "SELECT date, name, country, phone, phonetype FROM lead_info";
      7 $result = sqlite_query($query, $db) or die("Select Query Failed");
      8 ?>
      9 
     10 <table width="1000" align="center" border="1">
     11 
     12 <?
     13 while($row = sqlite_fetch_array($result))
     14 {
     15         print("<tr>");
     16         print("  <td>" . $row["date"]                   . "</td>");
     17         print("  <td>" . $row["name"]                   . "</td>");
     18         print("  <td>" . $row["country"]                . "</td>");
     19         print("  <td>" . $row["phone"]                  . "</td>");
     20         print("  <td>" . $row["phonetype"]              . "</td>");
     21         print("</tr>");
     22 }
     23 ?>
     24 
     25 </table>
     26 
     27 <?
     28 include_once "footer.php";
     29 ?>

```
THIS PAGE WORKS! IT DISPLAYS EVERYTHING! Does anyone see any difference in the query or the way that the retrieved vars are handled and printed?

EDIT: PS: Before posting this last reply, I went back to the original script and changed $row['foo'] to $row["foo"], but the problem continued.

The only thing that seems relevant is that the working code has the columns named explicitly in the query, while you have *. But there ought to be a way to get at the individual columns. Just an idea: maybe they can be accessed this way: $row['lead_info.date']. There is a function print_r or something which displays a whole array, so do print_r($row), too.

---

### Post by kevinharper on 2011-11-07
Kudos, Arndt!

The issue does in fact ONLY come up when I "SELECT *...".

I ended up having to redo the table and a lot of the scripts that wrote to it and retrieved from it.

After looking at your response, I tested it out and eliminated "*" from my SELECT's. :S Looks like I'm going to stick to this. I almost certain that I am having these issues because I am using a PHP4x version and the system isn't really equipped to handle anything newer. I also had to break up my emails to username and domain entries because I was unable to use php functions to convert to literal string. Those required some plugins and, well... not worth it for what I'm doing.

Seriously though... thank you for the response. It would have taken me a long time to see that.

---


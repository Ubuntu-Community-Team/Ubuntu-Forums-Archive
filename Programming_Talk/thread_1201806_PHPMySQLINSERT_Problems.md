---
title: "PHP/MySQL/INSERT Problems"
date: 2009-07-01
forum: Programming Talk
---

### Post by dhtseany on 2009-07-01
Hi guys,
I've been pulling my hair out for the last 3 hours trying to see what I'm missing. I think I might need to somehow execute **$result** but I could be wrong. It'd be great if someone could take a look :) I'm getting the following error:
```

You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ' , , , , , , , , , ,' at line 1

```

Here is my code:
```

<?
session_start();

if (!isset($_SESSION['username'])) {

	echo "<meta http-equiv='refresh' content='0;URL=http://www.131blacksheep.com/secure/login.php' />";
	echo "Please log in...";
} elseif (!isset($_SESSION['priv']) OR $_SESSION['priv'] != '1') {

	echo "You are not authorized to view this page. Please wait.";
	echo "<meta http-equiv=refresh content=2;URL=http://www.131blacksheep.com/secure/members.php />";
} else {
// Begin Secured Page //
include('dbconnect.php');
include('../include/1.php');
echo "<p><h2>Admin CPanel > Events Management > Add Event</h2><br></p>";

$result = mysql_query("INSERT INTO events (edate, etitle, etimes, etimee, eaddmq, eadd1, eadd2, ecitst, eaddzip, euod, edet, ecaptrans) VALUES ($fixeddate, $etitle, $etimes, $etimee, $eaddmq, $eadd1, $eadd2, $ecitst, $eaddzip, $euod, $edet, $ecaptrans") or die(mysql_error());

$edate = $_POST["edate"];
$etitle = $_POST["etitle"];
$etimes = $_POST["etimes"];
$etimee = $_POST["etimee"];
$eaddmq = $_POST["eaddmq"];
$eadd1 = $_POST["eadd1"];
$eadd2 = $_POST["eadd2"];
$ecitst = $_POST["ecitst"];
$eaddzip = $_POST["eaddzip"];
$euod = $_POST["euod"];
$edet = $_POST["edet"];
$ecaptrans = $_POST["ecaptrans"];
$fixeddate = date('Y-m-d', strtotime($edate));



echo "
<table width='75%'>
<form action='admin_eventadd.php' method='post' name='main'>

<tr><td>Date:</td><td><input type='text' name='edate' size='35' />

<A HREF=\"#\"
   onClick=\"cal.select(document.forms['main'].edate,'anchor1','MM/dd/yyyy'); return false;\"
   NAME=\"anchor1\" ID=\"anchor1\"><img src='http://www.131blacksheep.com/img/calendar.jpg' width='30px' height='30px' alt='Select Date'></A>




</td></tr>

<tr><td>Title:</td><td><input type='text' name='etitle' size='35' /></td></tr>

<tr><td>Start Time:</td><td><input type='text' name='etimes' size='35' /></td></tr>

<tr><td>End Time:</td><td><input type='text' name='etimee' size='35' /></td></tr>

<tr><td>Mapquest URL:</td><td><input type='text' name='eaddmq' size='35' /></td></tr>

<tr><td>Address 1:</td> <td><input type='text' name='eadd1' size='35' /></td></tr>

<tr><td>Address 2:</td><td><input type='text' name='eadd2' size='35' /></td></tr>

<tr><td>City, State:</td><td><input type='text' name='ecitst' size='35' /></td></tr>

<tr><td>Zip:</td><td><input type='text' name='eaddzip' size='35' /></td></tr>

<tr><td>UOD:</td><td>

<select name='euod'>
<option value='Civies'>Civies</option>
<option value='BDU'>BDU</option>
<option value='PT'>PT</option>
<option value='SA'>Summer A's</option>
<option value='SB'>Summer B's</option>
<option value='WA'>Winter A's</option>
<option value='WB'>Winter B's</option>
</select></td></tr>

<tr><td>Details:</td><td>
<textarea rows='5' cols='30' name='edet' wrap='physical'></textarea>
</td></tr>

<tr><td>CAP Trans Availabe?</td><td>
<input type='radio' name='ecaptrans' value='Yes' /> Yes
<input type='radio' name='ecaptrans' value='No' checked='checked' /> No</td></tr>

<tr><td><input type='submit' value='Add'></td></tr>
</table>
</form>";
include('../include/2.php');

// End Secured Page //
}
?>

```

---

### Post by Wim Sturkenboom on 2009-07-01
You set your variables that are used in the query after the query.

---

### Post by credobyte on 2009-07-01
[PHP]$result = mysql_query("INSERT INTO events (edate, etitle, etimes, etimee, eaddmq, eadd1, eadd2, ecitst, eaddzip, euod, edet, ecaptrans) VALUES ('$fixeddate', '$etitle', '$etimes', '$etimee', '$eaddmq', '$eadd1', '$eadd2', '$ecitst', '$eaddzip', '$euod', '$edet', '$ecaptrans'") or die(mysql_error());
[/PHP]

---

### Post by wojox on 2009-07-01
Do you have short tags enabled?
If not <?php  on first line

Blacksheep Cadet Squadron
Civil Air Patrol
United States Air Force Auxiliary

---

### Post by simeon87 on 2009-07-01
> **wojox said:**
> Do you have short tags enabled?
If not <?php  on first line

The fact that the PHP code is being executed should be enough of a hint to see that this is not the cause of the problem...

---

### Post by dhtseany on 2009-07-01
Sorry, but replacing my query with
```
 $result = mysql_query("INSERT INTO events (edate, etitle, etimes, etimee, eaddmq, eadd1, eadd2, ecitst, eaddzip, euod, edet, ecaptrans) VALUES ('$fixeddate', '$etitle', '$etimes', '$etimee', '$eaddmq', '$eadd1', '$eadd2', '$ecitst', '$eaddzip', '$euod', '$edet', '$ecaptrans'") or die(mysql_error());  

```
...did not alleviate the problems; same error message.

---

### Post by wojox on 2009-07-01
The fact that the PHP code is being executed should be enough of a hint to see that this is not the cause of the problem...

Where do you see php code being executed?????
It says the error is on line 1

---

### Post by dhtseany on 2009-07-01
Well, I'd imagine that at least part of the code is starting to execute then dies after the SQL query fails. If I comment out the line containing **$result**, it loads fine. So I'm inclined to believe it's a problem with said line. I tried the following but it failed just the same.

```

$result = mysql_query("INSERT INTO events (edate, etitle, etimes, etimee, eaddmq, eadd1, eadd2, ecitst, eaddzip, euod, edet, ecaptrans) VALUES ('".$fixeddate."', '".$etitle."', '".$etimes."', '".$etimee."', '".$eaddmq."', '".$eadd1."', '".$eadd2."', '".$ecitst."', '".$eaddzip."', '".$euod."', '".$edet."', '".$ecaptrans."'") or die(mysql_error());  

```

Any other thoughts?

---

### Post by wojox on 2009-07-01
Take $result =  out.

mysql_query("INSERT INTO events (edate, etitle, etimes, etimee, eaddmq, eadd1, eadd2, ecitst, eaddzip, euod, edet, ecaptrans) VALUES ('".$fixeddate."', '".$etitle."', '".$etimes."', '".$etimee."', '".$eaddmq."', '".$eadd1."', '".$eadd2."', '".$ecitst."', '".$eaddzip."', '".$euod."', '".$edet."', '".$ecaptrans."'") or die(mysql_error());

---

### Post by dhtseany on 2009-07-01
Nevermind, I got it. I had ") missing towards the end of the line.

Thanks anyways,
Sean

---

### Post by simeon87 on 2009-07-01
> **wojox said:**
> The fact that the PHP code is being executed should be enough of a hint to see that this is not the cause of the problem...

Where do you see php code being executed?????
It says the error is on line 1

> You have an error **in your SQL syntax**; check the manual that corresponds to your MySQL server version for the right syntax to use near ' , , , , , , , , , ,' at line 1

In other words, it runs the PHP and the query but there's an error in the query.

If PHP did not run, the above can't be seen because no query (correct or not) would be queried to the database system.

---


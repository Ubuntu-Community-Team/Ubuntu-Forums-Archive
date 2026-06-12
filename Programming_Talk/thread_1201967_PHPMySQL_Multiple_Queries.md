---
title: "PHP/MySQL Multiple Queries"
date: 2009-07-01
forum: Programming Talk
---

### Post by dhtseany on 2009-07-01
Hi guys,
What I'm trying to do is use an HTML based form for edit information already stored in a MySQL database. So far, I've successfully called the information from the database but now I'm kinda lost on how to actually update it.

Here is my current, working code:
```

<?
$eid = $_GET["eid"];
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
echo "<p><h2><a href='http://www.131blacksheep.com/secure/admin.php'>Admin CPanel</a> > <a href='http://www.131blacksheep.com/secure/admin_eventsmgt.php'>Events Management</a> > Event Details</h2><br></p>";

$

$result = mysql_query("SELECT * FROM events WHERE eid='".$eid."' ORDER BY edate ASC");
while($row = mysql_fetch_assoc($result)){
$edate = $row["edate"];
$etitle = $row["etitle"];
$etimes = $row["etimes"];
$etimee = $row["etimee"];
$eaddmq = $row["eaddmq"];
$eadd1 = $row["eadd1"];
$eadd2 = $row["eadd2"];
$ecitst = $row["ecitst"];
$eaddzip = $row["eaddzip"];
$euod = $row["euod"];
$edet = $row["edet"];
$ecaptrans = $row["ecaptrans"];

echo "
<table width='75%'>
<form action='admin_eventedit.php' method='post' name='main'>

<tr><td>Date:</td><td><input type='text' name='edate' size='35' value='".$edate."' />

<A HREF=\"#\"
   onClick=\"cal.select(document.forms['main'].edate,'anchor1','MM/dd/yyyy'); return false;\"
   NAME=\"anchor1\" ID=\"anchor1\"><img src='http://www.131blacksheep.com/img/calendar.jpg' width='30px' height='30px' alt='Select Date'></A>




</td></tr>

<tr><td>Title:</td><td><input type='text' name='etitle' size='35' value='".$etitle."'/></td></tr>

<tr><td>Start Time:</td><td><input type='text' name='etimes' size='35' value='".$etimes."'/></td></tr>

<tr><td>End Time:</td><td><input type='text' name='etimee' size='35' value='".$etimee."'/></td></tr>

<tr><td>Mapquest URL:</td><td><input type='text' name='eaddmq' size='35' value='".$eaddmq."'/></td></tr>

<tr><td>Address 1:</td> <td><input type='text' name='eadd1' size='35' value='".$eadd1."'/></td></tr>

<tr><td>Address 2:</td><td><input type='text' name='eadd2' size='35' value='".$eadd2."'/></td></tr>

<tr><td>City, State:</td><td><input type='text' name='ecitst' size='35' value='".$ecitst."'/></td></tr>

<tr><td>Zip:</td><td><input type='text' name='eaddzip' size='35' value='".$eaddzip."'/></td></tr>

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
<textarea rows='5' cols='30' name='edet' wrap='physical'>".$edet."</textarea>
</td></tr>

<tr><td>CAP Trans Availabe?</td><td>
<input type='radio' name='ecaptrans' value='Yes' /> Yes
<input type='radio' name='ecaptrans' value='No' checked='checked' /> No</td></tr>

<tr><td><input type='submit' value='Update'></td></tr>
</table>
</form>";


}

include('../include/2.php');

// End Secured Page //
}
?>

```

Where would I go from here? I'm sure somewhere I'll need a MySQL query to update the records but how would I only allow one MySQL to work vs. the other present?

If I'm not making sense, let me know and I'll explain further.

Thanks,
Sean

---

### Post by predator on 2009-07-01
hmm. your login procedure is a little insecure. I would recommend a header('location:xxx'); style redirect rather than a HTML one that relies on browser level. But anyhow, I digress.. 

The fact that one query has executed (the "select" one), does not preclude you doing another one on the same page, or afterwards. 

I would update your submit button to have something like <input type="submit" name="action" value="Submit" /> or the like, and then in you page have an <input type="hidden" name="eid" value="<?=$eid; ?>" />... and then at the top of your page you could have

```

if($_POST['action'] == 'Submit' && !empty($_POST['eid'])) {

$update_q = mysql_query("UPDATE events SET etitle = ".$_POST['etitle'].", xxx = ".$_POST['xxx']." WHERE eid = ".mysql_real_escape_string($_POST['eid']));

if($update_q)
$status = 'entry has been updated';

}

```

There is probably other security code that needs to be in there, but to keep it simple.

---

### Post by dhtseany on 2009-07-01
Question:
What purpose would the hidden form field serve? I've been fooling around with your ideas but I'm not really getting why that needed to be there. One thing I may not have said is that the $eid is passed in the URL and the at the top of the code is the $_GET['eid'];

---

### Post by Wim Sturkenboom on 2009-07-02
I mostly use a hidden field to remember the primary key of a record.

**step 1)**
*Page 1*
Read a record from database (the PK is passed in $_GET).
Present record to user for editing.
When user clicks button, POST record to next page
**step 2)**
*Page 2*
Run an update query with the data from the POST

If you make the primary key visible, the user can change it and you will write a (possible) incorrect value into the database (specially when you use MyISAM tables and relationships between records in tables may change). If you don't store it at all, you don't know which record the updated data applies to.
There are other ways to do it (session variables come to mind)

---

### Post by dhtseany on 2009-07-02
Well, I've been working with your IF statments, however I get keeping an error about an unexpected...
```

Parse error: syntax error, unexpected '{' in /home7/onethro3/public_html/secure/admin_eventedit.php on line 21

```
...error and I'm getting a headache staring at the same line of code over and over :)
```

if($_POST['action'] == 'Submit' && !empty($_POST['eid']) {
$update = mysql_query("UPDATE events (edate, etitle, etimes, etimee, eaddmq, eadd1, eadd2, ecitst, eaddzip, euod, edet, ecaptrans) VALUES ('".$fixeddate."', '".$etitle."', '".$etimes."', '".$etimee."', '".$eaddmq."', '".$eadd1."', '".$eadd2."', '".$ecitst."', '".$eaddzip."', '".$euod."', '".$edet."', '".$ecaptrans."')") or die(mysql_error());}

```

---

### Post by Wim Sturkenboom on 2009-07-02
You're missing a closing ')' at the end of your if statement.

---

### Post by bodselecta on 2009-07-02
If you're having problems with php/mysql syntax, have you been looking at the api pages of those official sites?
Both sites:
[http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)
[http://www.php.net/manual/en/](http://www.php.net/manual/en/)

are excellent resources with lots of contributed examples
I saw you had other syntax problems the other night, but you'd found the problem before I could reply, Netbeans php ide might be useful for you.
It's free and very easy to use and debug with.... 


> **dhtseany said:**
> Well, I've been working with your IF statments, however I get keeping an error about an unexpected...
```

Parse error: syntax error, unexpected '{' in /home7/onethro3/public_html/secure/admin_eventedit.php on line 21

```
...error and I'm getting a headache staring at the same line of code over and over :)
```

if($_POST['action'] == 'Submit' && !empty($_POST['eid']) {
$update = mysql_query("UPDATE events (edate, etitle, etimes, etimee, eaddmq, eadd1, eadd2, ecitst, eaddzip, euod, edet, ecaptrans) VALUES ('".$fixeddate."', '".$etitle."', '".$etimes."', '".$etimee."', '".$eaddmq."', '".$eadd1."', '".$eadd2."', '".$ecitst."', '".$eaddzip."', '".$euod."', '".$edet."', '".$ecaptrans."')") or die(mysql_error());}

```

---

### Post by dhtseany on 2009-07-02
Forgive my ignorance, but I don't see it. 

From what I see I think I have all the ('s there....

---

### Post by dhtseany on 2009-07-02
So does Netbeans IDE actually check your code for problems? I've been using Dreamweaver for sometime now but I've always desired something that could check my code for me in stupid situations such as this :)

---

### Post by bodselecta on 2009-07-02
Yeh it's great for code completion and highlighting syntax problems.
Debugging is also pretty slick
If you don't need the java/j2ee/c++ etc etc ide's, you can download the php only bundle and it's quite small.

you'll eventually find that it's quicker to write php in a text editor though

see
[http://www.netbeans.org/downloads/index.html](http://www.netbeans.org/downloads/index.html)

---

### Post by dhtseany on 2009-07-02
What do you mean? 
> you'll eventually find that it's quicker to write php in a text editor though

What? Versus a dedicated program for coding?

I'm downloading it now

---

### Post by Wim Sturkenboom on 2009-07-03
> **dhtseany said:**
> Forgive my ignorance, but I don't see it. 

From what I see I think I have all the ('s there....

:D The '(' are indeed there, but the ')' are not :D

I have marked the matching ones with colours, working from the outside inwards

```

if[COLOR="Red"]**_(_**[/COLOR]$_POST['action'] == 'Submit' && !empty[COLOR="Blue"]**_(_**[/COLOR]$_POST['eid'][COLOR="Red"]**_)_**[/COLOR] {
  ^                                      ^             ^
  +1                                     +1            -1

```

You need to add another blue ')' before the red ')'.

I usually start counting when I run into this type of errors. Start at 0 and when you get to an '(' add 1; when you get an ')', subtract 1. The result should be 0 when you have done the whole condition.

---

### Post by smartbei on 2009-07-03
**About Hidden Form Data**
> **Wim Sturkenboom said:**
> I mostly use a hidden field to remember the primary key of a record.
If you make the primary key visible, the user can change it and you will write a (possible) incorrect value into the database (specially when you use MyISAM tables and relationships between records in tables may change). If you don't store it at all, you don't know which record the updated data applies to.
There are other ways to do it (session variables come to mind)

Using a hidden field is fine for some purposes, but remember that users CAN change it, causing you to update the wrong row in a database (dangerous). For example, say I have the following html page:
```

<html>
<head><title>AAAA</title></head>
<body>
<form>
<input type="hidden" value="CANNOT BE CHANGED!">
<input type="button" onclick="alert(document.forms[0].elements[0].value);" value="Check hidden Value">
</form>
</body>
</html>

```
[LIST=1]
[*]Browse to the page.
[*]Click the button to see the value of the hidden element.
[*]Run the following code in the url bar:
```

javascript:alert(document.forms[0].elements[0].value = "IT IS CHANGED!")

```
[*]Click the button again to see if the value has changed.
[/LIST]
So it is quite possible to change hidden html input elements.

**About Securing the Login**
> **predator said:**
> hmm. your login procedure is a little insecure. I would recommend a header('location:xxx'); style redirect rather than a HTML one that relies on browser level. But anyhow, I digress.. 
This is problematic as well - the header('location:') header is also at the browser level! For example, if I use a non-browser to try to get the web page, I will be able to even if you stick headers that I am supposed to follow in the HTTP headers. For example, wget I believe (I have not tested this) can choose not to follow the headers. Therefore, the secure thing to do is:
```

header('location:xxx');
exit()

```
So that no matter what browser/downloader, etc. the users are using, they will not have access to the sensitive data.

---

### Post by jtdeloach10 on 2009-07-04
> Where would I go from here?
Your code is extremely messy, organize it, indent it. Write a framework class for it.

---

### Post by Can+~ on 2009-07-04
> **jtdeloach10 said:**
> Your code is extremely messy, organize it, indent it. Write a framework class for it.

Plus, move the style aspect to a .css like those width=x. And move the javascript to a .js.

[PHP]$edate = $row["edate"];
$etitle = $row["etitle"];
$etimes = $row["etimes"];
$etimee = $row["etimee"];
$eaddmq = $row["eaddmq"];
$eadd1 = $row["eadd1"];
$eadd2 = $row["eadd2"];
$ecitst = $row["ecitst"];
$eaddzip = $row["eaddzip"];
$euod = $row["euod"];
$edet = $row["edet"];
$ecaptrans = $row["ecaptrans"];[/PHP]

There are two wierd things there:
1. Why are you recreating variables with the exact same name? When using the $row["key"] is exactly the same minus all that baggage.
2. Why your row names are so unhelpful and plenty? Could you show some of the tables you're creating?

---

### Post by dhtseany on 2009-07-04
> **jtdeloach10 said:**
> Your code is extremely messy, organize it, indent it. 

I think extremely is a tad harsh, don't you think? :)

> **jtdeloach10 said:**
> 

Write a framework class for it.

Aren't framwork classes something to do with .NET? I'm using PHP.


> **Can+~ said:**
> 
There are two wierd things there:
1. Why are you recreating variables with the exact same name? When using the $row["key"] is exactly the same minus all that baggage.
2. Why your row names are so unhelpful and plenty? Could you show some of the tables you're creating?

1. Because for the 2-ish years that I've been messing around with PHP that's always been the way I've known how to use mysql_fetch_arrays. Plus, there have been other instances where it made it simply easier to use a $aaa vs. $_ROW['aaa'];.
2. The rows are helpful to me as I know what each field stores and what they're short for. Basically, this is a calendar/events page that will inform members about upcoming events and specific details about said events.

---

### Post by dhtseany on 2009-07-04
OK guys,
I got off track with the other stuff. There following isn't returning any errors but when I try to use the script to update the database it submits to itself like it's supposed to, but doesn't do anything with the changes I made.

[PHP]if($_POST['action'] == 'Submit' && !empty($_POST['eid'])){
$update = mysql_query("UPDATE events (edate, etitle, etimes, etimee, eaddmq, eadd1, eadd2, ecitst, eaddzip, euod, edet, ecaptrans) VALUES ('".$fixeddate."', '".$etitle."', '".$etimes."', '".$etimee."', '".$eaddmq."', '".$eadd1."', '".$eadd2."', '".$ecitst."', '".$eaddzip."', '".$euod."', '".$edet."', '".$ecaptrans."')") or die(mysql_error());
header("Location: http://www.131blacksheep.com/secure/admin_eventsmgt.php");}
else {[/PHP]

And from there it is the rest of the page, mostly HTML.

Anyone see something wrong here?

Peace
Sean

---

### Post by Mirge on 2009-07-04
Why are you not putting the variables in the quotes as well to increase readability?

'".$var."' vs '$var'

Put in a print/echo at the beginning of the if and else blocks... so you can make sure execution is going where you think it's going.

---


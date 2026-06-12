---
title: "PHP / MySql"
date: 2010-01-09
forum: Programming Talk
---

### Post by sprouty on 2010-01-09
Hi

I'm trying to log IP-Address into a table through php. I have written the below code, but theres got to be a better way of doing it. I'm new to php/mysql so i would be very grateful for any pointers and ways to improve the code.

Many Thanks,

Sprouty

```
$query = "SELECT count(id) FROM IPS where IP = '$ip' limit 1";
$result = mysql_query($query) or die ("Could not check ip");
$row = mysql_fetch_array($result);
$count = $row[0];
if ($count == 0 ){
	//Insert into database
	$query = "INSERT INTO IPS (IP,FirstDate) VALUES ('$ip','$date')";
	mysql_query($query) or die ("Could not insert ip");
}
//Return IP Id
$query = "SELECT id FROM IPS where IP = '$ip' limit 1";
$result = mysql_query($query) or die ("Could not check IP id");
$row = mysql_fetch_array($result);
$Idip = $row[0];
print "ip id == $Idip";
```

---

### Post by Finalfantasykid on 2010-01-09
Why do you check to see if the IP is already in the table?

Is this for a unique hits tracker?

---

### Post by sprouty on 2010-01-09
Yes, the table is for logging unique IPs

---

### Post by Finalfantasykid on 2010-01-09
If you are tracking the unique IP's per day, should you then not have the first query also check the date?

---

### Post by sprouty on 2010-01-10
I'm not tracking unique ips over a day. I'm tracking them over the life time of the website

cheers,

Sprouty

---

### Post by The Secret on 2010-01-10
Why do you need the IPs ID ?

[PHP]$ip = $_SERVER['REMOTE_ADDR'];
$date = time();

$query = mysql_query("SELECT * FROM tracker WHERE ip='$ip' LIMIT 1") or die(mysql_error());
if (mysql_num_rows($query) == 0) {
    $insert = mysql_query("INSERT INTO tracker (ip, date) VALUES ('$ip', '$date')") or die(mysql_error());    
}

echo "IP: $ip <br />";[/PHP]

---

### Post by Hellkeepa on 2010-01-10
HELLo!

You need to validate the IP address, before using it for anything. Seems like most people does not realize that this is a value that is generated and sent by the client, and as such can be made to contain anything an attacker would like it to.

Also, in the example given by **The Secret**, I would do the following changes:
[php]if (!$ip = Val_ip ($_SERVER['REMOTE_ADDR'])) {
    die ("Invalid ID, hacking attempt?");
}

// Use "sprintf ()" and "quote_smart ()" to escape user input, to avoid SQL-injections.
$query = "SELECT * FROM tracker WHERE ip=%s LIMIT 1"
$query = mysql_query(sprintf ($query, quote_smart ($ip)) or die(mysql_error()); // Remove "mysql_error ()" from production code, for security.
if (mysql_num_rows($query) == 0) {
    // Use "sprintf ()" and "quote_smart ()" to escape user input, to avoid SQL-injections.
    $query = "INSERT INTO tracker (ip, date) VALUES (%s, %d)";
    $insert = mysql_query(sprintf ($query, quote_smart ($ip), time ()) or die(mysql_error());    // See above comment.
}

// Escape to make output HTML-safe.
echo "IP: ".htmlspecialchars ($ip)." <br />";[/php]

You'll find my validation functions here: [http://norskwebforum.no/pastebin/7609](http://norskwebforum.no/pastebin/7609)
And **Stadskle**'s "quote_smart ()" here: [http://norskwebforum.no/viewtopic.php?p=243716](http://norskwebforum.no/viewtopic.php?p=243716)

Happy codin'!

---

### Post by The Secret on 2010-01-10
> **Hellkeepa said:**
> HELLo!

You need to validate the IP address, before using it for anything. Seems like most people does not realize that this is a value that is generated and sent by the client, and as such can be made to contain anything an attacker would like it to.

Also, in the example given by **The Secret**, I would do the following changes:
[php]if (!$ip = Val_ip ($_SERVER['REMOTE_ADDR'])) {
    die ("Invalid ID, hacking attempt?");
}

// Use "sprintf ()" and "quote_smart ()" to escape user input, to avoid SQL-injections.
$query = "SELECT * FROM tracker WHERE ip=%s LIMIT 1"
$query = mysql_query(sprintf ($query, quote_smart ($ip)) or die(mysql_error()); // Remove "mysql_error ()" from production code, for security.
if (mysql_num_rows($query) == 0) {
    // Use "sprintf ()" and "quote_smart ()" to escape user input, to avoid SQL-injections.
    $query = "INSERT INTO tracker (ip, date) VALUES (%s, %d)";
    $insert = mysql_query(sprintf ($query, quote_smart ($ip), time ()) or die(mysql_error());    // See above comment.
}

// Escape to make output HTML-safe.
echo "IP: ".htmlspecialchars ($ip)." <br />";[/php]You'll find my validation functions here: [http://norskwebforum.no/pastebin/7609](http://norskwebforum.no/pastebin/7609)
And **Stadskle**'s "quote_smart ()" here: [http://norskwebforum.no/viewtopic.php?p=243716](http://norskwebforum.no/viewtopic.php?p=243716)

Happy codin'!

IP validation .. how could someone change his IP to something more dangerous, like HTML or even JavaScript ? :-s

---

### Post by Hellkeepa on 2010-01-10
HELLo!

Well... I don't know, but I have a few ideas on how it *might* be possible. Though, would you take the risk that no-one else on the entire planet knows how to do it?

Don't underestimate the Dark side, after all.

Happy codin'!

---

### Post by sprouty on 2010-01-10
Hi,

The code i post was a extract of the php. Before the page even make a connection to the database or input is validated. Although i'm all about makeing my code more better and smaller. I currently validate the ip address like the below. Would Hellkeepa method be better?
[PHP]$octet = explode(".", $target);
if ((is_numeric($octet[0])) && (is_numeric($octet[1])) && (is_numeric($octet[2])) && (is_numeric($octet[3])))[/PHP]

I also need the Id returned because there is anorther insert done on a different table to match the ip up with some addtional information.

Many Thanks,

Sprouty

---

### Post by Hellkeepa on 2010-01-10
HELLo!

The method I used checks for a valid IP, and only valid IPs.
Your method only checks that the first four members of the resulting array is a numerical value. That means, the following would be accepted:
[php]$test = "1000.0.0.1. And a lot of text that has nothing to do in an IP-address. Includes more dots, too.";[/php]
Since you don't save the result of the validation, this string will be passed unmodified to the script. Even if it contained SQL-injection code, or HTML/JS.

For the ID of the newly created row, just to use "mysql_insert_id ()" after the INSERT query.

Happy codin'!

---

### Post by sprouty on 2010-01-10
Sorry i was being lazy, i should have copied the whole code. At the moment i was trying to focus on trying to make the mysql insert and returns better. 
[PHP]$octet = explode(".", $target);
if ((is_numeric($octet[0])) && (is_numeric($octet[1])) && (is_numeric($octet[2])) && (is_numeric($octet[3]))) {
	$ip = $octet[0].'.'.$octet[1].'.'.$octet[2].'.'.$octet[3];

}else{
	print "No data on ip";

}[/PHP]

---

### Post by Hellkeepa on 2010-01-10
HELLo!

OK, but it'll still accept and use an IP address of "10000.4e2.-15.0" without complaining.

Happy codin'!

---

### Post by sprouty on 2010-01-10
Wow i really didn't reliase that...
Just to run me through this: -15 because it a negative number but i'm now sure about the e. ( i think i remeber seen a e on the calculater is it to the power of something (sorry not really good with numbers)). apart from makeing the data for that line invalid, is there a dark side that could get pass the validation i'm using?

---

### Post by Hellkeepa on 2010-01-10
HELLo!

The "e" is the scientific notation, and it means "times (ten to the power of)" (*10^). So, 4e2 is the same as 4*10², which equates to 400. Check the PHP manual on "is_numeric ()" for more details on what it accepts.

There are a number of possible exploits this could trigger in supporting systems, buffer/int overflows being one of them. However, asking "if" there is is the wrong way to go about this, from a security standpoint. Always assume that there *is* an exploit that could be used by an invalid IP (or anything else), and take the necessary steps to ensure that the input is valid by all the rules you can find.
You'll thank yourself later when the exploit is found, and you don't have to race to update every single system you've used that bit of code in. ;-)

Happy codin'!

---

### Post by Shiam on 2010-06-26
Hello,
 
I am doing a video tutorial on PHP & MySQL in creating a guestbook. Data are stored correctly in the database but when I launch guestbook.php on a browser, I am getting the following message:
"**Notice**: Undefined index: txt_name in **C:\wamp\www\VIDEO_TUTORIAL\guestbook.php** on line **7"**
 
**My php code is:**
 
<?php
    require ($_SERVER["DOCUMENT_ROOT"]."/VIDEO_TUTORIAL/config/db_config.php");
    $connection = @mysql_connect($db_host, $db_user, $db_password) or die ("Error in connecting to DB.");
    mysql_select_db ($db_name, $connection);
    
[COLOR=red]**    $name = $_POST['txt_name'];  ***** Line 7 ******[/COLOR]
    $len = strlen($name);
    if ($len > 0)
    {
        $email = $_POST["txt_email"];
        $comment = $_POST["txt_comment"];
        $date = time();
        $query = "INSERT INTO guestbook (autoID, name, email, comment, date_auto)
        VALUES (NULL, '$name', '$email', '$comment', '$date')";
        mysql_query($query, $connection) or die (mysql_error());
      
    }
           
?>
 
 
<html>
<head>
    <title> GuestBook</title>        
</head>
<body>
<center>
<form action="<?php echo $_SERVER['PHP_SELF']; ?>" method = "POST">
    <font face="arial" size = "1">
        Name: <input type= "text" name = "txt_name">&nbsp;
        Email: <input type= "text" name = "txt_email"><br><br>
        Comments:<br>
        <textarea style ="width: 75%" rows = "10" name = "txt_comment"></textarea>
        <center><input type="submit" value = "Submit"></center>
    </font>
    <table bgcolor = "#AAAAAA" border= "0" width= "75%" cellspacing="1" cellpadding="2">
<?php
?>
</form>
</center>
</body>
</html>
 
I have another question concerning another file named tracker.php. 
When I launch tracker.php, I am getting the error:
"**Warning**: mysql_result() expects parameter 1 to be resource, boolean given in **C:\wamp\www\VIDEO_TUTORIAL\tracker.php** on line **17;**
 
**My code ressembles very much that you wrote on the FORUM and I am asking for your help.**
**Data are correctly saved and retrieved from the database "buzzdb" .**
 
**The php code is:**
 
<?php
    require ($_SERVER     
    ["DOCUMENT_ROOT"]."/VIDEO_TUTORIAL/config/db_config.php");
    $connection = @mysql_connect($db_host, $db_user, $db_password) or die ("Error in connecting to DB.");
    mysql_select_db ($db_name, $connection);
    $this_page = $_SERVER["PHP_SELF"];
    $ip = $_SERVER["REMOTE_ADDR"];
    $date_auto = time();
    
    $query = "INSERT INTO tracker (page, IP, date_auto) VALUES ('$this_page', '$ip', '$date_auto')";
    mysql_query($query, $connection);
    
    $query = "SELECT count (*) FROM tracker WHERE page = '$this_page'";
    $result = mysql_query($query, $connection);
[COLOR=red]**    $views = mysql_result($result, 0, "count(*)");  **** Line 17 ******[/COLOR]
    echo $views;
    
?>
 
 Is it possible to get your help? 
Thanks for your reply and your help.
 
Regards,
Daniel.

---

### Post by iMisspell on 2010-06-27
This will get rid of the notice.
Change
[php]$name = $_POST['txt_name']; ***** Line 7 ****[/php]
To
[php]$name = isset($_POST['txt_name']) $_POST['txt_name'] : '';[/php]

_

---

### Post by Hellkeepa on 2010-06-28
HELLo!

You're missing half of the ternary operator, **iMisspell**. Living true to your name, I see. :-P

**Shiam**: Please use the [****php][/php] tags around your PHP-code, to make the post easier to read.
Also, the notices are given because the $_POST array haven't been created by the first time you run the script, and as such the "txt_name" index does not exist. This isn't an error, just a notification that PHP gives you in case you've forgotten anything.
Undefined indexes and variables *could* lead to security issues, or be because of mispellings which would lead to bugs. Thus PHP lets you know about it, if they're turned on in the "php.ini".

The correct version of **iMisspell**'s fix is thus:
[php]$name = isset($_POST['txt_name']) ? $_POST['txt_name'] : '';[/php]

PS: You'll also need to validate the input, and escape the output, to protect yourself against attacks. Your code is open to both SQL injections and XSS. Latter via "PHP_SELF"

As for your second question: The MySQL query doesn't return a result, but "false". Which tells me that the query is wrong. Printing out the results from "mysql_error ()" will let you know what the error message from MySQL is.

Always remember to remove the output from "mysql_error ()" from your script, when publishing it on a production server (going live). As attackers could use this to gain additional information about your system, which can then in turn be used to attarck it successfully.

Happy syncin'!

---


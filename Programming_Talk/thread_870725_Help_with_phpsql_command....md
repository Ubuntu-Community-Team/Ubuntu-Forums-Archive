---
title: "Help with php/sql command..."
date: 2008-07-26
forum: Programming Talk
---

### Post by viciouslime on 2008-07-26
I am using the following php script to process a form:
```
<?
$deword=$_POST['deword'];
$detype=$_POST['detype'];
$enword=$_POST['enword'];
#Set english noun type to neuter regardless of german noun type
if ( $detype = 2 ) {
	$engtype = 10;
}
if ( $detype = 3 ) {
	$entype = 10;
}else {
	$entype=$_POST['detype'];
}


#write to database
mysql_connect("localhost", "root", "PASSWORD") or die(mysql_error());
mysql_select_db("vdict") or die(mysql_error());


	#Check if german word exists
	if(mysql_num_rows(mysql_query("SELECT * FROM deutsch_word WHERE word='$deword'")) == 0){
		#german word does not exist, add it, then retrieve its id
		mysql_query("INSERT INTO `deutsch_word` VALUES ('', '$detype', '$deword')");
		$deid=mysql_insert_id();
	}else{
		#german word exists already, retrieve its id
		$deid=mysql_query("SELECT id FROM deutsch_word WHERE word='$deword'");
	}



	#check if english word exists
	if(mysql_num_rows(mysql_query("SELECT * FROM english_word WHERE word='$enword'")) == 0){
		#english word does not exist, add it, then retrieve its id
		mysql_query("INSERT INTO `english_word` VALUES ('', '$entype', '$enword')");
		$enid=mysql_insert_id();
	}else{
		#english word exists already, retrieve its id
		$enid=mysql_query("SELECT id FROM english_word WHERE word='$enword'");
	}


mysql_query("INSERT INTO `deutsch_english` VALUES ('', '$deid', '$enid')");
Print "Thank you for your submission. It has been successfully added to the database.";
Print "Vielen Dank fuer Ihre Eingabe. Sie wurde erfolgreich eingegeben.";
?> 
```

Basically, the form contains a german word, an english word and an integer that represents a word type. When the form is submitted, the script must check to see if the german word is in the database already, if not it must add it and retrieve its newly assigned id, if so, it must simply retrieve its exsisting id. The form then repeats this for the english word before inserting a line in the deutsch_english table with both of the word ids in.

As it stands, the script is inserting 0 in this final table instead of the existing id. The line that retrieves an existing id is as follows:

```
else{
		#english word exists already, retrieve its id
		$enid=mysql_query("SELECT id FROM english_word WHERE word='$enword'");
	}

```

Presumably there's something wrong with that line, but I only started learning php/mysql yesterday, so if anyone can help me out here, it'd be very much appreciated :D

---

### Post by drubin on 2008-07-26
> mysql_query("INSERT INTO `english_word` VALUES ('', '$entype', '$enword')");


Do all your tables have an Auto Increment Id field? but even if they do not I would HIGHLY recommend using this syntax for insert statements makes them easier to read and you you allot more control.

```
INSERT INTO `english_word`(enword,entype) VALUES( '$enword','$entype')
```

The brackets directly after `english_word` tell you the column names and the order that they will appear in the VALUES bracket. :) 

see i can also change the order. 

As far as i know autoincrement only works if you do not specifier a value if you use a value(any value) it will try and use that first.

In this case if the value was '' -> a string or varchar it would not be compatible with a autoincrement ID number.

Give that a shot and let us know.  

Ps lastly please take a look at mysql_real_escape_string() to provent SQL injection.

---

### Post by viciouslime on 2008-07-26
Hi Rubinboy, thanks very much for your help. Actually, the autoincrement part was working fine, but i've updated it as you suggest as you clearly know far more about this than me! I've also managed to fix my main problem, the ids not being retrieved correctly for words already in the database. My code is now as follows for anyone with the same problem. It turns out that mysql_query doesn't actually return values from within a table. I will also look into mysql_real_escape_string() as you suggest :) Thanks again!

```
<?
$deword=$_POST['deword'];
$detype=$_POST['detype'];
$enword=$_POST['enword'];
#Set english noun type to neuter regardless of german noun type
if ( $detype = 2 ) {
	$engtype = 10;
}
if ( $detype = 3 ) {
	$entype = 10;
}else {
	$entype=$_POST['detype'];
}


#write to database
mysql_connect("localhost", "root", "PASSWORD") or die(mysql_error());
mysql_select_db("vdict") or die(mysql_error());


	#Check if german word exists
	if(mysql_num_rows(mysql_query("SELECT * FROM deutsch_word WHERE word='$deword'")) == 0){
		#german word does not exist, add it, then retrieve its id
		mysql_query("INSERT INTO `deutsch_word`(word,type) VALUES( '$deword','$detype')");
		$deid = mysql_insert_id();
	}else{
		#german word exists already, retrieve its id
		$queryde = mysql_query("SELECT id FROM deutsch_word WHERE word= \"$deword\""); 
		$finddeid = mysql_query($queryde);
		while($finddeid=mysql_fetch_array($queryde)) {
                 $deid=$finddeid["id"];}
	}



	#check if english word exists
	if(mysql_num_rows(mysql_query("SELECT * FROM english_word WHERE word='$enword'")) == 0){
		#english word does not exist, add it, then retrieve its id
		mysql_query("INSERT INTO `english_word`(word,type) VALUES( '$enword','$entype')");
		$enid = mysql_insert_id();
	}else{
		#english word exists already, retrieve its id
	$queryen = mysql_query("SELECT id FROM english_word WHERE word= \"$enword\""); 
		$findenid = mysql_query($queryen);
		while($findenid=mysql_fetch_array($queryen)) {
                 $enid=$findenid["id"];}
	}


mysql_query("INSERT INTO `deutsch_english` VALUES ('', '$deid', '$enid')");
Print "Thank you for your submission. It has been successfully added to the database.";
Print "Vielen Dank fuer Ihre Eingabe. Sie wurde erfolgreich eingegeben.";

?> 
```

---

### Post by drubin on 2008-07-26
You are correct mysql does not return an array you would need to run 
mysql_fetch_assoc($res) OR mysql_fetch_array($res)  where $res is: $res=mysql_query('MY query');

---


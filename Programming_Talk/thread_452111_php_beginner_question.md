---
title: "php beginner question"
date: 2007-05-23
forum: Programming Talk
---

### Post by woodsonoversoul on 2007-05-23
why would I get :

Parse error: syntax error, unexpected T_STRING, expecting ',' or ';' in /var/www/current.php on line 5

with a file that contains :

<?php
$user = admin;

if($user == admin){
	echo ¨hello admin¨;
}
elseif($user == guest)
	echo ¨hello guest¨;
else
	echo ¨improper entry¨;

?>

Thanks in advance!

---

### Post by atoponce on 2007-05-23
'admin' and 'guest' need to be either a string or variable.. Try this code:

```

<?php
$user = "admin";

if($user == "admin"){
    echo "hello admin";
}
elseif($user == "guest")
    echo "hello guest";
else
    echo "improper entry";

?>

```Also, something is funny with your double-quotes.  Are they Unicode?  PHP should have no trouble with Unicode, but could be problematic, at any event.  Maybe it was the forums parsing that did it.

---

### Post by woodsonoversoul on 2007-05-23
Thanks man, That worked perfectly. What´s more is that I see the difference in the code and understand why your code worked and mine didn´t. Thanks again.

---

### Post by barmazal on 2007-05-23
usually you declare such things as array when you check current $user with integer when integer sets level of permission inside database or external file include();

---

### Post by woodsonoversoul on 2007-05-25
Hey thanks again guys. One more question; from the previous example, I would think code like this would work:

<?php
function capitalize( $str, $each = TRUE)
{
	$str = strlower($str);
	if ($each === TRUE)
	{	
		$str = ucwords ($str);
	}
	else 
	{
		$str = strupper($str);
	}
	echo (¨$str <br>¨);
}
capitalize(¨hElLo WorLD!¨);
echo ¨Now with false¨;
capitalize(¨hELLo WORld!¨, FALSE);

?>

But I´m still having problems with the quotations. I keep getting error messages like:

Parse error: syntax error, unexpected T_VARIABLE in /var/www/current.php on line 13

which is:

echo (¨$str <br>¨);

but I&#314;l take those quotes away and get other messages...

Thanks again guys

---

### Post by tszanon on 2007-05-25
I don't know PHP, but it seems that you're using ¨ instead of " and I think that is your first problem to be solved.
> echo (¨$str <br>¨);
If this is right, I don't know. But, again, I think it should be:
> echo ("$str <br>");

---

### Post by araz on 2007-05-25
I guess this is what u want
```

<?php
function capitalize( $str, $each)
{
$str = strtolower($str);
if ($each == TRUE)
{
$str = ucwords ($str);
}
else
{
$str = strtoupper($str);
}
echo $str.'<br/>';
}
capitalize("hElLo WorLD!",TRUE);
echo "Now with false";
capitalize ("hELLo WORld!", FALSE);
?>

```

---

### Post by barmazal on 2007-05-25
do you want $str to be rendered on HTML page or content of $str which you pass as parameter?


you need to separate <br /> from string like echo $str . "<br />";

it's like you trying to put html tags along with php variable as echo string while imho it should be concatenation aka '.' between variable and html tag in order to view it's content.

---

### Post by woodsonoversoul on 2007-05-31
Alright what about this, I´m getting an unable to connect message with the code:

// set database server access variables:
$host = "localhost";
$user = "dan";
$pass = "mypass";
$db = "testdb";

// open connection
$connection = mysql_connect($host, $user, $pass) or die ("Unable to connect!");

when I´ve just created the database. I´m using my root name and password. I didn´t set up any user privliges so I assumed access would be granted under root, is this incorrect or is there a problem with my code?

---


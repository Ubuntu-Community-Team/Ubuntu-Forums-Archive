---
title: "Simple PHP shell_exec question."
date: 2012-04-07
forum: Programming Talk
---

### Post by thewho1050 on 2012-04-07
I am working on a webpage that allows me to manage my remote server (which is running ubuntu server) without having to ssh into it just to start it up.  Right now im running MAMP off of a Macbook and testing the page locally.  My problem: I cannot get the following script to run the .jar for Minecraft_Server, even though I can get it to work by typing into terminal.

the snip of code is really basic:

```
 $output = shell_exec('java -jar minecraft_server.jar');
echo "<pre>$output</pre>";
```

the whole page is here.  Its pretty rough so sorry about that.

```
<?php 
//declare common variables for later use.

$pass = $_POST["passwd"];
$name = $_POST["username"];

$loacation = "localhost";
$SQLname = "_______";
$SQLpass = "________";
$dbname = "User Login";
$dbtable1 = "Members";

//open MySQL connection.

$con = mysql_connect($location,$SQLname,$SQLpass);
if (!$con)
  {
  die('Could not connect: ' . mysql_error());
  }

//looks in the "Members" table in "User Login" database for all failds based on username.

mysql_select_db($dbname, $con);

$result = mysql_query("SELECT * FROM $dbtable1
WHERE username='$name'");

$row = mysql_fetch_array($result);

//checks for login information, and checks that the feilds are not blank.

if ($pass==$row['password'] && $name==$row['username'] && $pass != ''){
	
	echo " <br /><br /><center><font size='10'>Welcome ".$_POST["username"]."</font></center>";
	
	echo "<br /><br /><center><font size='10'>You have logged in successfully.  
	<a href='http://localhost:8888/MAMP/?language=English'>MyPhpAdmin</a></font></center>";

	$output = shell_exec('java -jar minecraft_server.jar');
	echo "<pre>$output</pre>";
	
	if ($row['security']=='3'){
	
	echo
	"<center><font size='5'><br /><br />Because you are amazing, you may add new users.  
	Enjoy your own awesomeness.<br /><br /></font>";
	
	$sql0 = "SELECT MAX(userid) FROM `Members` ";
	
	$result1 = mysql_query($sql0);
	
	$row1 = mysql_fetch_array($result1);
	
	echo "There are " . $row1['0'] . " total users.<br />";
	
	echo "<br /><form action='processing.php' method='get'>
	Name: <input type='text' name='newusername' /> <br />
	Password: <input type='text' name='newpassword' /><br />
	User ID : <input type='text' name='userid' /><br />
	Security Level: <input type='text' name='security' />
	<br /><input type='submit' />
	</form></center>";	

}
else { 

echo "<center><font size='6'><br /><br />You are not awesome.  Bummer man.</center></font>";

}
	
	
}

// if the user is not in the database, print:

else { 

	echo " <br /><br /><center><font size='10'>NO</font></center>";
	
	echo "<center><img src='kitten.jpeg' alt='this is a kitteh for your fail'/>";

	echo	"<br /><br /><center><font size='10'>You Lose.</font></center>
	<br /><br />
	<center><form action='welcome.php' method='post'>
	Name: <input type='text' name='username' /> <br />
	Password: <input type='password' name='passwd' /><br />
	<input type='submit'/>
	</form></center>";

}

?>
```

finally, the output for the segment I am having trouble with is here:

Error occurred during initialization of VM
Unable to load native library: libjava.jnilib

Any advice at all would be appreciated.

---

### Post by SeijiSensei on 2012-04-07
Make sure the application can be read and executed by the pseudo-user that the web server runs as.  On Ubuntu using Apache that's the "www-data" user.

---

### Post by thewho1050 on 2012-04-07
used chmod to give RWX to everyone.  Still same output.  Good idea though.

---


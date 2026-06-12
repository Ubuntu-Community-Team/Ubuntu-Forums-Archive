---
title: "save HTML Text Box to txt file"
date: 2009-11-13
forum: Programming Talk
---

### Post by gypsumwolf on 2009-11-13
On my Ubuntu Server Edition I have a HTML website. I want to use a text box.

```
<form method="post" action="">
<textarea name="comments" cols="40" rows="5">
Enter your comments here...
</textarea><br>
<input type="submit" value="Submit" />
</form>

```

Thats the easy part. Now I want to know how to store it when some one pushes "submit". I would like to store the info in a text file on my server.

---

### Post by StunnerAlpha on 2009-11-13
Here is a start: [http://www.hosting.vt.edu/tutorials/phpmysql/#about](http://www.hosting.vt.edu/tutorials/phpmysql/#about)

---

### Post by Barriehie on 2009-11-14
Here's a working example from my machine.  I use this to access my machine from the laptop at work and update the customer database.  The first file, getcustomer.php, gets the form info via html wrapped in php tags and the second file, savecustomer.php writes the data to an SQL database.  To save the info to a flat text file you'll have to explore the php file functions.  An SQL database lends itself to querying, sorting, and all types of useful functions.

getcustomer.php
```

<?php

session_start();

$usertechno = $_SESSION['techno'];
$usertechname = $_SESSION['techname'];
if( $usertechno == "" ) {
	include 'logout.php';
	exit(1);
}



echo "<html>";
echo "<head>";
echo "<title>Add Customer</title>";
echo "</head>";

echo "<body background=\"./images/precisionhvac.jpg\">";
/*
            Begin input form
*/
echo "<form method=\"POST\" action=\"savecustomer.php\">";
echo "<font color=\"black\">";

echo "<br /><p align=\"center\"><font color=\"black\"><strong>Adding to $usertechname's customers.</font></p>";

//                          First Name
echo "<table><tr>";
echo "<td valign=\"center\">";
echo "<font color=\"black\"><strong>First</strong> ";
echo "<input type=\"text\" size=\"30\" name=\"fname\">";
echo "</td>";

//						Last Name
echo "<td  valign=\"center\">";
echo "&nbsp;&nbsp;&nbsp;&nbsp;<font color=\"black\"><strong>Last</strong> ";
echo "<input type=\"text\" size=\"30\" name=\"lname\">";
echo "</td>";
echo "</tr></table><br>";

//                          Street
echo "<strong>Street</strong> ";
echo "<input type=\"text\" size=\"30\" name=\"street\"><br><br>";

//                          City
echo "<table>";
echo "<tr>";
echo "<td valign=\"center\">";
echo "<font color=\"black\"><strong>City</strong> ";
echo "<input type=\"text\" size=\"30\" name=\"city\">";
echo "</TD>";

//                          State
echo "<td valign=\"center\">";
echo "&nbsp;&nbsp;<font color=\"black\"><strong>State</strong> ";
echo "<input type=\"text\" size=\"2\" name=\"state\">";
echo "</td>";

//                          Zip
echo "<td valign=\"center\">";
echo "&nbsp;&nbsp;<font color=\"black\"><strong>Zip</strong> ";
echo "<input type=\"text\" size=\"10\" name=\"zip\">";
echo "</td></tr></table><br>";

//                          hPhone
echo "<strong>hPhone</strong> ";
echo "<input type=\"text\" size=\"12\" name=\"hphone\">&nbsp;&nbsp;";

//                          cPhone
echo "<strong>cPhone</strong> ";
echo "<input type=\"text\" size=\"12\" name=\"cphone\"><br><br>";

//						Email
echo "<strong>Email</strong> ";
echo "<input type=\"text\" size=\"30\" name=\"email\"><br><br>";

//						Notes
echo "<strong>Notes</strong> ";
echo "<textarea rows=\"2\" name=\"notes\" cols=\"80\"></textarea><br><br>";

//						Location
echo "<strong>Location</strong> ";
echo "<input type=\"text\" size=\"10\" name=\"unitlocation\">";

//						Type
echo "&nbsp;&nbsp;&nbsp;&nbsp;<strong>Type</strong> ";
echo "<input type=\"text\" size=\"10\" name=\"unittype\">";

//						Qty
echo "&nbsp;&nbsp;<strong>Quantity</strong> ";
echo "<input type=\"text\" size=\"2\" name=\"qty\">";

//                                              Manager
echo "&nbsp;&nbsp;<strong>&nbsp;&nbsp;&nbsp;Property Manager 1=yes / 0=no</strong> ";
echo "<input type=\"text\" size=\"2\" name=\"mgr\">";

//						Techno
//echo "&nbsp;&nbsp;&nbsp;&nbsp;<strong>Your Tech. No.</strong> ";
//echo "<input type=\"text\" size=\"3\" name=\"techno\">";

//						Buttons
//							Submit
echo "<p align=\"center\"><table><tr>";
echo "<td><input type=\"submit\" name=\"Submit\"
value=\"Submit\"></td>";

//							Clear Form
echo "&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;";
echo "<td><input type=\"reset\" name=\"Reset\" value=\"Clear
Form\"></td>";

//                                                      Done
echo "&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;";
echo "<td><input type=\"button\" value=\"Done\" onclick=\"window.location='./index-go.php'\"/></td>";
echo "</tr></table></p>";

//							End of input form
echo "</form>";
echo "</body>";
echo "</html>";

?>

```


savecustomer.php
```

<?php

session_start();
$usertechno = $_SESSION['techno'];

$fname = $_POST['fname'];
$lname = $_POST['lname'];
$street = $_POST['street'];
$city = $_POST['city'];
$state = $_POST['state'];
$zip = $_POST['zip'];
$hphone = $_POST['hphone'];
$cphone = $_POST['cphone'];
$email = $_POST['email'];
$notes = $_POST['notes'];
$unitlocation = $_POST['unitlocation'];
$unittype = $_POST['unittype'];
$qty = $_POST['qty'];
$mgr = $_POST['mgr'];

/*										                            Connect To Database
*/

$hostame="xxxxxxxxxx";
$username="xxxxxxxxxx";
$password="xxxxxxxxxx";
$dbname="xxxxxxxxxx";

mysql_connect($hostname,$username, $password) OR DIE ("Unable to connect to database! Please try again later.");

	mysql_select_db($dbname);

/*
Check for a duplicate entry
*/

$sql = "SELECT * FROM customers WHERE Street = '$street'";

 $result = mysql_query($sql) or die("Error: ". mysql_error(). " with query ". $sql);

        while($row = mysql_fetch_row($result)) {

        $ndxout = $row[0];

        $fnameout = $row[1];

        $lnameout = $row[2];

        $streetout = $row[3];

        $cityout = $row[4];

        $stateout = $row[5];

        $zipout = $row[6];

        $hphoneout = $row[7];

        $cphoneout = $row[8];

        $emailout = $row[9];

        $notesout = $row[10];

        $locationout = $row[11];

        $typeout = $row[12];

        $qtyout = $row[13];

	$techno = $row[14];

        }



if( $ndxout == NULL ) {



//			Write the data

	$sql = "INSERT INTO customers (Fname, Lname, Street, City, State, Zip, hPhone, cPhone, email, Notes, location, type, qty, techno, mgr) VALUES ('$fname', '$lname', '$street', '$city', '$state', '$zip', '$hphone', '$cphone', '$email', '$notes', '$unitlocation', '$unittype', '$qty', '$usertechno', '$mgr')";



$result = mysql_query($sql) or die("Error: ". mysql_error(). " with query ".

$sql);



$errno = mysql_errno();

$sql = mysql_close();



echo "<p align=\"center\"><i><b><font size=\"5\" color=\"darkblue\"><br><br><br>...Database    Updated.    ..</font></b></i></p>";

echo "<font size=\"4\"><form><p align=\"center\" style=\"margin-top: 0; margin-bottom: 0\">";

echo "<a target=\"_self\" href=\"./index-go.php\">Done</a>";

echo "&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;";

echo "<a target=\"_self\" href=\"./getcustomer.php\">Again</a>";

echo "</p></form></font>";



/*	$ndxout was null so we wrote the data to customers table.

*/



							} else {





/*	$ndxout is not null so we have a duplicate record

*/

echo "<p align=\"center\"><i><b><font size=\"5\" color=\"darkblue\"><br><br><br>Duplicate Address</font></b></i></p>";

echo "<font size=\"4\"><form><p align=\"center\" style=\"margin-top: 0; margin-bottom: 0\">";

echo "<a target=\"_self\" href=\"index.php\">Done</a>";

echo "&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;";

echo "<a target=\"_self\" href=\"getcustomer.php\">Again</a>";

echo "</p></form></font>";

									}



?>


```

Barrie

---


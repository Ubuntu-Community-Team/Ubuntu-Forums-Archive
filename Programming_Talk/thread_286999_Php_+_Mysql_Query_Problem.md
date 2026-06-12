---
title: "Php + Mysql Query Problem"
date: 2006-10-28
forum: Programming Talk
---

### Post by drpepper on 2006-10-28
I'm creating a website with a number of catagorys, and each catagory has a large number of items. In php, I have the page showing all the catagorys, and when the user clicks on a catagory all the items in that catagory are shown, this is where the problem is. When the catagory is show, only the first entry appears, and its repeated all the way down the page, over and over. So I think its a loop problem but, i can't find it. 

this is the broswe page(browse.php)..

CODE:
/[COLOR=Red]/Conecting to the database and pulling down the list of catagorys in ascending order[/COLOR]

[B]<?
$username="myusername";
$password="mypassword";
$database="mydatabase";

mysql_connect("mydomain.com",$username,$password);
@mysql_select_db($database) or die( "Database Error");
$query="SELECT * FROM table1 ORDER BY catagory ASC";
$result=mysql_query($query);[/B]

[B]$num=mysql_numrows($result);

mysql_close();
?>[/B]
[COLOR=Red]
// going thru the variable and placing each catagory on the list using a loop[/COLOR]

[B]<?
$i=0;
while ($i < $num) 
{$catagory_temp=mysql_result($result,$i,"catagory");
    if ($catagory != $catagory_temp) 
    {$catagory = $catagory_temp;
?> [/B]   
[COLOR=Red]//html code to display[/COLOR]
[B]    <p align="left" class="menuheader"><a     href="catagory.php?cat=<? echo $catagory ?>"><? echo $catagory; ?></a></p>
<?[/B]    
[COLOR=Red]// loop cont[/COLOR]
    }
[B]$i++;
}

?>
[/B]CODE END

This all works fine, creates a dynamic link to catagory.php and sends the catagory variable forward to the script on catagory.php

The line used to query the data base in catagory.php is

catagory.php...
CODE:
[B]$query="SELECT * FROM table1 WHERE catagory='$cat'";
 
[/B]and then im using this loop to display the catagory items..[B]

<?
$i=0;
while ($i < $num) 
{
$colum1value=mysql_result($result,$i,"colum1");
$colum2value=mysql_result($result,$i,"colum2");
    
echo "<p align='left' class='menuheader'> $colum1value - $colum2value<a href='open.html' target='popUpWin' 
onclick='popUpWin(this.href,'console',430,150);return false;'>Open</a></p>";

}
$i++;
?>
[/B]CODE END[B]
and it appears to be getting stuck in this loop, just displaying the first record over and over.What am I doing wrong?!

Thanks

Nick

[/B]

---

### Post by gjones on 2006-10-29
the $i++ is outside the loop

---

### Post by invalid on 2006-10-29
You have the $i++ just outside the loop, try moving it up a line.

---

### Post by drpepper on 2006-10-29
Thanks guys, I can't believe I missed that! Its all working now. 

Nick

---


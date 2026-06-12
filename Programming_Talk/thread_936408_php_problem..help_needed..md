---
title: "php problem..help needed."
date: 2008-10-02
forum: Programming Talk
---

### Post by hockey97 on 2008-10-02
Hi I just took a php test for a company.

I want to know if I done anything wrong in the code provided??

the code is supposed to make a html forum that will put infomation into the database  that is the person first name last name and phone number.
Then onced you submit the info it would then make sure their isn't a record already in the database that matched that info once knowing it hasn't been created then it would create a new record and then display the new record info onto the screen/browser.

here is the code:[php]<?php



//Database Connection

$msdb = mysql_connect("localhost", "root", "");

mysql_select_db("test", $msdb) or die(mysql_error());



/*

GENERAL INFORMATION:

	Below is the current table structure for 'members':

=====

ID: id (autoincrement)

First Name

Last Name

Phone Number

=====



PUT YOUR NAME HERE PLEASE:My name



PART 1:

-------

	* Below, write the PHP code to insert a first name, last name, and phone number

into the 'members' table.  Use an HTML form to collect this information, then store it to the 'members' table.

// 

*/
if (!isset($_POST["submit"])) { 

        echo "<html><head><link rel=\"stylesheet\" type=\"text/css\" href=\"/test.css\"/><form action=\"test.php\" method=\"POST\">";

        echo "<table>";

        echo "<tr>";

        echo "<td id=\"first\" width=\"50%\">First Name:</td><td width=\"50%\"><input id=\"one\" name=\"firstname\" size=\"18\" type=\"text\" />";

        echo "</tr>";

        echo "<tr>";

        echo "<td id=\"last\" width=\"50%\">Last Name:</td><td width=\"50%\"><input id=\"two\"name=\"lastname\" size=\"18\" type=\"text\" />";

        echo "</tr>";

        echo "<tr>";

        echo "<td id=\"phone\"width=\"50%\">Phone Number:</td><td width=\"50%\"><input id=\"three\" name=\"phone_number\" size=\"18\" type=\"text\" />";

        echo "</tr>";

        echo "<tr>";

        echo "<td colspan=\"2\"><input id=\"submit\" type=\"submit\" name=\"submit\" value=\"submit\"</td>";

        echo "</tr>";

        echo "</table>";

        echo "</form><img id=\"output\" src=\"lightblue.jpg\">";}

if(isset($_POST["submit"])){
   $first_name=$_POST["firstname"];
   $last_name=$_POST["lastname"];
   $phone_number=$_POST["phone_number"];
   $q = mysql_query("SELECT * FROM members WHERE firstname ='$first_name' AND phone = '$phone_number'");
   $r = mysql_num_rows($q);
if($r==0){
   $q2=mysql_query("INSERT INTO `members` (firstname,lastname,phone) VALUES ('$first_name','$last_name','$phone_number')");}


 /*Part one that I made shows first a html forum where you can input the first name and last name and phone number. Then once the person clicks the submit button it will then store that info into the mysql database.Also $q2 this would run only if the record doesn't exist in the database.*/





/*

PART 2:

-------

	* Below, write the PHP code to retrieve the previously inserted record from the

'tests' table and display it in the browser.*/

 $q3 = mysql_query("SELECT * FROM `members` WHERE firstname ='$first_name' AND phone = '$phone_number'") or die (mysql_error());
 $row = mysql_fetch_assoc($q3);
 $first_name2=$row["firstname"];
 $last_name2=$row["lastname"];
 $phone_number2=$row["phone"];
echo"<html><title>Output</title><head><link rel=\"stylesheet\" type=\"text/css\" href=\"/test.css\"/></head><a id=\"first\">First Name:  $first_name2</a><br>
<a id=\"last\">Last Name:  $last_name2</a><br>
<a id=\"phone\">Phone Number: $phone_number2</a>
<img id=\"output\"src=\"lightblue.jpg\"></html>";}

/*This code would print out to the screen with html. It would only show the record that was just inserted(meaning part 1 code)*/

?>[/php]

I also put css code to help make it better looking.

They however only allowed one file to be uploaded to them.

So I bet the css dosen't work.

Also is using echo not professional??? does it matter if I use print or not??

I just want to know what's wrong with the script and how I can imporve on it.

Now I know the above script gives me info about the table but I assumed it was wrong since they gave me a sql file.

this squl file they gave me is : [php]-- phpMyAdmin SQL Dump
-- version 2.8.0.3
-- http://www.phpmyadmin.net
-- 
-- Host: localhost
-- Generation Time: Jan 17, 2007 at 05:24 PM
-- Server version: 4.0.26
-- PHP Version: 4.4.2
-- 
-- Database: `test`
-- 

-- --------------------------------------------------------

-- 
-- Table structure for table `members`
-- 

CREATE TABLE `members` (
  `id` int(11) NOT NULL auto_increment,
  `firstname` varchar(50) default NULL,
  `lastname` varchar(50) default NULL,
  `phone` varchar(50) default NULL,
  PRIMARY KEY  (`id`),
  UNIQUE KEY `id` (`id`),
  UNIQUE KEY `firstname_2` (`firstname`),
  UNIQUE KEY `lastname` (`lastname`),
  KEY `firstname` (`firstname`)
) TYPE=MyISAM AUTO_INCREMENT=14 ;

-- 
-- Dumping data for table `members`
-- 

INSERT INTO `members` (`id`, `firstname`, `lastname`, `phone`) VALUES (3, 'moo', 'moo', 'moo'),
(4, 'mooo', 'moooo', 'moooo'),
(5, 'jjj', 'jjj', 'jjj'),
(6, 'hh', 'h', 'hhh'),
(7, 'ggg', 'gg', 'gggg'),
(8, '', '', ''),
(9, 'uity', 'uityuit', 'iuty'),
(10, 'hhh', 'hh', 'hhh'),
(11, 'll', 'll', 'lll'),
(12, 'jimmy', 'dickinson', '123234142'),
(13, 'jjjj', 'jjjjjjjj', 'jjj');[/php]

---

### Post by CptPicard on 2008-10-02
If you're qualified, you should know if anything is wrong.

It's a test for a reason, you know.

---

### Post by LaRoza on 2008-10-02
> **hockey97 said:**
> Hi I just took a php test for a company.

I want to know if I done anything wrong in the code provided??


Code reviews are fine, unless they are for assignments or employment. Sorry. Who knows? If I help you, and you get hired, I may end up working with you?

To quote [http://www.parashift.com/c++-faq-lite/how-to-post.html#faq-5.2:](http://www.parashift.com/c++-faq-lite/how-to-post.html#faq-5.2:)
> 
*If I help... * You might become a professional programmer without knowing how to write a program like this. Someday you might work on a project with me without knowing how to write a program like this. Then I would have to do you serious bodily harm.

---

### Post by mssever on 2008-10-02
You've only been programming since sometime this year, if I recall correctly. Your history of posts shows that you still have a lot to learn about the basics of programming. I don't think that you have enough experience to go hunting for a programming job. If you do land a programming job, you risk ending up being featured on [thedailywtf.com]("http://thedailywtf.com").

I suggest that you learn at least one other language besides PHP, that you explore the why's of the more popular frameworks, that you learn and understand MVC, and more. Your PHP (I'm not referring to just this post, but to all your threads that I've seen) looks like my PHP when I was first learning. Any company that would have hired me at that time would have been foolish. Frankly, I'd be embarrassed to admit that I wrote my early code.

---

### Post by ghostdog74 on 2008-10-02
guys, relax. i think he already took the test and just asking for advice.
@OP, i am not PHP expert..just $0.02
```

<?php

// turn on errors...eg error_reporting().. check the manual

if(isset($_POST["submit"])){
    // define your database stuff after valid submit
    // or you could put your database connections etc in an include file and call require(), require_once() etc 
    define("DBUSER","root");
    define("DBPASS","");
    define("DBHOST","localhost");
    define("DBNAME","test");
    $dbc = @mysqli_connect(DBHOST,DBUSER,DBPASS,DBNAME) or die("cannot connect: ".mysqli_connect_error());
    if ($dbc){
        mysqli_set_charset($dbc, 'utf8');
        echo '<p>Connected</p><br>';    
        // you would want to put in extra check for invalid fields by using empty() or isset()...
        $first_name=$_POST["firstname"];
        $last_name=$_POST["lastname"];
        $phone_number=$_POST["phone_number"];
        // you might want to use prepared  statements....
        $query = "SELECT * FROM members WHERE firstname ='$first_name' AND phone = '$phone_number'";
        $r = @mysqli_query($dbc,$query);    
        if( mysqli_num_rows($r) ==0){            
            $query = "INSERT INTO `members` (firstname,lastname,phone) VALUES ('$first_name','$last_name','$phone_number')";
            echo "query: $query";
            //$q2=mysql_query($query);
            //....continue...
            //....
        }
    }
    
}else{
?>
    <!-- show form -->
    <!-- though html doesn't care about spaces/newlines,,better to indent -->
    <html><head>
            <link rel="stylesheet" type="text/css" href="/test.css" />
          </head>
    <body>
            <form action="test5.php" method="POST">
                <table>
                <tr>
                    <td id="first" width="50%">First Name:</td>
                    <td width="50%"><input id="one" name="firstname" size="18" type="text" />
                </tr>
                <tr>
                    <td id="last" width="50%">Last Name:</td>
                    <td width="50%"><input id="two" name="lastname" size="18" type="text" />
                </tr>
                <tr>
                    <td id="phone"width="50%">Phone Number:</td>
                    <td width="50%">
                        <input id="three" name="phone_number" size="18" type="text" />
                    </td>
                </tr>
                <tr>
                    <td colspan="2">
                        <input id="submit" type="submit" name="submit" value="submit"
                    </td>
                </tr>
                </table>

            </form><img id="output" src="lightblue.jpg">    
    
    </body>
    </html>
    
<?php
}
?>

```

---


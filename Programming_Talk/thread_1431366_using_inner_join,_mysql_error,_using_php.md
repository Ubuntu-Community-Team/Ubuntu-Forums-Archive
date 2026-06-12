---
title: "using inner join, mysql error, using php"
date: 2010-03-16
forum: Programming Talk
---

### Post by w0296094 on 2010-03-16
Hey guys I'm having big trouble trying to make a webpage work. I am using one webpage to access another one that is supposed to join two tables from my database. The first webpage simply contains a hyperlink that will lead me to the same webpage, but it is supposed to have 3 additional columns. This is the code for my second webpage,

mysql_select_db("communityliaison") or die(mysql_error()); 
 
// Get all the data from the "example" table 
$course = $_POST['course'];
$sections = $_POST['sections'];  
$result = mysql_query(" SELECT courses.course, courses.department, sections.course, 
                                         sections.section, sections.term, sections.days, 
                                         sections.beginning, sections.ending 
                                FROM `courses` INNER JOIN `sections` 
                                ON courses.course = sections.course 
                                WHERE courses.course = ". $course ." 
                               AND sections.course = ". $sections."") 
or die(mysql_error());   
 
echo "<table border='1'>";  
echo "<tr> <th>Department</th> <th>Course Number</th> <th>Section</th> <th>Term</th> <th>Days of Week</th> <th>Time</th> </tr>"; 
// keeps getting the next row until there are no more to get 
while($row = mysql_fetch_array( $result )) { 
// Print out the contents of each row into a table 
echo "<tr><td>"; 
echo $row['department']; 
echo "</td><td>"; 
echo $row['course']; 
echo "</td><td>"; 
echo $row['section']; 
echo "</td><td>"; 
echo $row['term']; 
echo "</td><td>"; 
echo $row['days']; 
echo "</td><td>"; 
echo $row['beginning']; 
echo "-"; 
echo $row['ending']; 
echo "</td></tr>"; 
} 
 
echo "</table>"; 
?> 
<br /><a href="http://localhost/index.html">Go back to Database Administration Homepage</a><br /> 
</body> 
</html>

i will post the first webpage code in the post below, in case you need it.
This is what happens, when I select the hyperlink, I get the following error:

You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'AND sections.course =' at line 7

I believe line 7 corresponds to               AND sections.course = ". $sections."")

I changed INNER JOIN to CROSS JOIN and i still get the same error message. Any ideas?

---

### Post by w0296094 on 2010-03-16
This is the code for the first webpage


<body>
Click on Course Number to view Course Sections
<br />
<br />
<table border='1'><tr> <th>Department</th> <th>Course Number</th> <th>Course Title</th> <th>Course Description</th> <th>Credit Hours</th> </tr><tr><td>statistics</td><td><a href='http://localhost/viewsectioninformation.php?course=102'>102</a></td><td>macroeconomics</td><td>class about economics</td><td>3</td></tr><tr><td></td><td><a href='http://localhost/viewsectioninformation.php?course='></a></td><td></td><td></td><td></td></tr></table><br /><a href="http://localhost/index.html">Go back to Database Administration Homepage</a><br />
</body>
</html>

---

### Post by Xyro on 2010-03-16
[PHP]
WHERE courses.course = ". $course ."
AND sections.course = ". $sections."")
or die(mysql_error());
[/PHP]

Try:
[PHP]
WHERE courses.course = '". $course ."'
AND sections.course = '". $sections."'")
or die(mysql_error()); 
[/PHP]

Edit:

Sorry, I might be out to lunch with that suggestion.

Tip: I find that when working with PHP/MySQL, doing the following helps to resolve most bad MySQL queries. Try something like this first:

[PHP]

...

$query = "SELECT courses.course, courses.department, sections.course, sections.section, sections.term, sections.days, sections.beginning, sections.ending FROM `courses` INNER JOIN `sections` ON courses.course = sections.course WHERE courses.course = ". $course ." AND sections.course = ". $sections."";

echo $query;

// $result = mysql_query($query) or die(mysql_error()); 

...

[/PHP]

Then, after you're satisfied with the query that is going to be submitted, remove the echo and un-comment the mysql_query() line.

---

### Post by Hellkeepa on 2010-03-16
HELLo!

I've taken the liberty to clean the script up a bit, added some security and other comments to it as well:
[php]<?php

// TODO: Remove "or die(mysql_error())" when putting the script into production.
mysql_select_db ("communityliaison") or die (mysql_error ());

// Get all the data from the "example" table
// TODO: Validate input, to make sure it follows the expected pattern for legal input!
$course = $_POST['course'];
$sections = $_POST['sections'];

// Edited by Hellkeepa: Added the use of sprintf() and aliases to clean the query up a bit
$query = "SELECT
	c.course, c.department, s.course, s.section, s.term, s.days, s.beginning, s.ending 
FROM `courses` AS c
INNER JOIN `sections` AS s ON c.course = s.course 
WHERE c.course = %s AND s.course = %s";

// Edited by Hellkeepa: Added "quote_smart ()" to escape the user-generated data. See SQL injections.
$query = sprintf ($query, quote_smart ($course), quote_smart ($sections));

// TODO: Remove "or die(mysql_error())" when putting the script into production.
$result = mysql_query ($query) or die (mysql_error ());

// Edited by Hellkeepa: Changed to HereDOC syntax for readability.
$output = <<<OutHTML
<table border="1">
	<tr>
		<th>Department</th>
		<th>Course Number</th>
		<th>Section</th>
		<th>Term</th>
		<th>Days of Week</th>
		<th>Time</th>
	</tr>

OutHTML;

// Edited by Hellkeepa: Added sprintf-template for inner loop, for readability and performance.
$template = "\t<tr>\n\t\t<td>%s</td>\n\t\t<td>%s</td>\n\t\t<td>%s</td>\n".
	"\t\t<td>%s</td>\n\t\t<td>%s</td>\n\t\t<td>%s</td>\n\t</tr>\n";

// keeps getting the next row until there are no more to get 
while ($row = mysql_fetch_array ($result)) {
	// Print out the contents of each row into a table
	// Edited by Hellkeepa: Used htmlspecialchars () to prevent issues with XSS and other
	//		problems related to unescaped HTML meta characters being added to the HTML code.
	$output .= sprintf ($template,
		htmlspecialchars ($row['department']),
		htmlspecialchars ($row['course']),
		htmlspecialchars ($row['section']),
		htmlspecialchars ($row['term']),
		htmlspecialchars ($row['days']),
		htmlspecialchars ($row['beginning']."-".$row['ending']));
}

echo $output."</table>";

?>

<p></p><a href="http://localhost/index.html">Go back to Database Administration Homepage</a></p>

</body>
</html>[/php]
This one should, hopefully, work a bit better. If not, let me know, along with the error messages you're getting.
To get this to work you'll need Stadskle's "quote_smart ()" function, and you can find it here: [http://norskwebforum.no/viewtopic.php?p=243716](http://norskwebforum.no/viewtopic.php?p=243716)

Happy codin'!

---

### Post by w0296094 on 2010-03-19
hey man thx for fixin the code. I still have this problem:

You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '%s AND s.course = %s' at line 5

i straight copypasted your code on the webpage. 

any ideas, it seems like it has the same problem as before. i even put quotes on c.course = s.course, but to no results

---

### Post by Hellkeepa on 2010-03-19
HELLo!

That error message tells me that this line did not execute:
[php]$query = sprintf ($query, quote_smart ($course), quote_smart ($sections));[/php]
If you have a look at in the PHP manual, for "sprintf ()" then you'll see what I mean. The query syntax is correct, or rather will be after the above line has been executed.

Happy codin'!

---

### Post by w0296094 on 2010-03-26
THIS IS MY ERROR MESSAGE

**Fatal error**:  Call to undefined function quote_smart() in **/var/www/viewsectioninformation.php** on line [B]29


[/B]

---

### Post by Hellkeepa on 2010-03-26
HELLo!

Re-read post #4 in this thread.

Happy codin'!

---


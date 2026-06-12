---
title: "[SOLVED] help with php"
date: 2008-02-13
forum: Programming Talk
---

### Post by bsharp on 2008-02-13
I'm trying to create a web application to manage grades for a FBLA contest at my school.  Everything is working fine so far, but I'm having problems with entering grades into a MYSQL database.  The form to do this has to be dynamically generated, and to do this I made a loop that takes a number that they entered, $gradenum, and loops that many times to create the form.  I have created a function to generate the form, which is this:
[PHP]function enter_grade_form($gradenum,$id)
{
	if(!isset($gradenum)) //checks to see if the user entered a number for the form generation
	{
		echo "<div align='center'><form action='grades.php' method='GET'>
		How many grades do you want to add?<br>
		<input type='hidden' name='action' value='add'>
		<input type='text' name='num'>
		<input type='hidden' name='id' value='{$id}'>
		<input type='submit' value='Continue'>
		</form>";
		exit();
	}
	echo "<h2 align='center'>Add Grades</h2>
	<form action='grades.php?action=grade&id={$id}' method='POST'>
	<input type='hidden' name='id' value='{$id}'><!--carries info to the next page for proper redirection--!>
	<input type='hidden' name='function' value='addgrades'><br>
        <b>Enter your grade and class name and class ID number below:</b>
	<table border='0'><th>Class Name</th><th>Class ID</th><th>Credit Hours</th>
	<th>Semester</th><th>Final Grade</th>
	<tr><td align='center'><i>Class Name</i></td>
	<td align='center'><i>4-digit Class ID<br>Number</i></td>
	<td align='center'><i>Possible Credit<br>Hours</i></td>
	<td align='center'><i>Spring or Fall<br>Semester</i></td>
	<td align='center'><i>Quality Points<br>earned</i></td></tr>";
	//loop that generates the form		
	$class_name_array[0]='';
	$class_id_array[0]='';
	$credit_hrs_array[0]='';
	$semester_array[0]='';
	$grade_array[0]='';

	while($gradenum > 0)
	{
                $i = 0;
		echo "<tr><td><input type='text' name='$class_name_array[$i]' maxlength='30'></td>
		<td><input type='text' name='$class_id_array[$i]' maxlength='4'></td>
		<td><input type='text' name='$credit_hrs_array[$i]' maxlength='2'</td>
		<td><input type='text' name='$semester_array[$i]' maxlength='6'></td>
		<td><input type='text' name='$grade_array[$i]' maxlength='1'></td>";
		$gradenum--;
		$i++;
	}
	echo "</table>
	<input type='hidden' name='count' value='$i'>
	<input type='submit' value='Submit'></form>";
}[/PHP]
And here is the part of grades.php that processes the form:
[PHP]elseif($_GET['action'] == "grade")
{

	$cxn = mysqli_connect($host,$user,$pass,$db);
	$count = $_POST['count'];
	while($count > 0)
	{
		$i=0;
		$id = mysqli_real_escape_string($cxn,$_POST['id']);
		$_name = mysqli_real_escape_string($cxn,$_POST['class_name_array']['{$i}']);
		$_id = mysqli_real_escape_string($cxn,$_POST['class_id_array']['{$i}']);
		$_grade = mysqli_real_escape_string($cxn,$_POST['grade_array']['{$i}']);
		$_credit_hrs = mysqli_real_escape_string($cxn,$_POST['credit_hrs_array']['{$i}']);
		$_semester = mysqli_real_escape_string($cxn,$_POST['semester_array']['{$i}']);
		$add_grade = "INSERT INTO grades
		(grade, id, class, credithrs, semester, classid) 
		VALUES('$_grade','$id','$_name','$_credit_hrs','$_semester','$_id')";
		mysqli_query($cxn,$add_grade) or die('Error adding info to db: '.mysqli_error($cxn));
		$count--;
		$i++;
	}
	if(mysqli_affected_rows($cxn) == $i)//checks to see if the correct number was added to db
	{
		echo "<meta http-equiv='refresh' content='3; URL=index.php?id={$id}'>
		<h2 align='center'>Grades added successfully!</h2>
		<h3 align='center'>Redirecting....</h3>
		<p align='center'>If your browser does not redirect you, <a href='index.php?id={$id}>
		click here</a> to continue.</p>";
	}
	else
	{
		echo "There was an error adding grades to db: ".mysqli_error($cxn);
	}
	exit();
}[/PHP]

The form is generated properly, it directs to grades.php and is processed, and enters the correct number of rows into the database.  The problem is that nothing except the student id, $id, is being entered correctly.  I have narrowed down the problem to the arrays, and the more and more i try to figure out the problem, the more and more I can't see why it doesn't work. This is my first php project, so please understand the sloppiness of my code, and also if there is an easier way to do this please let me know ;)

---

### Post by bsharp on 2008-02-13
I found the problem...For some reason, I looked at the source of the page after it is sent to the browser. When the form is generated, there is no value for the name attribute on the <input> tags.  I can see why it is doing this, but I don't know how to fix it.  

How do you set the name of a <input> tag to be the name of an array?

Please make me feel stupid...then the fix will be easy :)

---

### Post by bsharp on 2008-02-13
solved the <input> tag problem myself too... I just did away with arrays altogether. Instead I am using this:
[php]	while($gradenum > 0)
	{

		echo "<tr><td><input type='text' name='class_name.$gradenum' maxlength='30'></td>
		<td><input type='text' name='class_id.$gradenum' maxlength='4'></td>
		<td><input type='text' name='credit_hrs.$gradenum' maxlength='2'></td>
		<td><input type='text' name='semester.$gradenum' maxlength='6'></td>
		<td><input type='text' name='grade.$gradenum' maxlength='1'></td>";
		$gradenum--;
[/php]

But now I am back to my original problem... everything being added to the database except $id is 0. I have modified the script that processes to look like:
[php]	$cxn = mysqli_connect($host,$user,$pass,$db);
	$count = $_POST['count'];
	while($count > 0)
	{
		$id = mysqli_real_escape_string($cxn,$_POST['id']);
		$_name = mysqli_real_escape_string($cxn,$_POST['class_name_array.$count']);
		$_id = mysqli_real_escape_string($cxn,$_POST['class_id.$count']);
		$_grade = mysqli_real_escape_string($cxn,$_POST['grade.$count']);
		$_credit_hrs = mysqli_real_escape_string($cxn,$_POST['credit_hrs.$count']);
		$_semester = mysqli_real_escape_string($cxn,$_POST['semester.$count']);
		$add_grade = "INSERT INTO grades
		(grade, id, class, credithrs, semester, classid) 
		VALUES('$_grade','$id','$_name','$_credit_hrs','$_semester','$_id')";
		mysqli_query($cxn,$add_grade) or die('Error adding info to db: '.mysqli_error($cxn));
		$count--;
	}
[/php]

---

### Post by bsharp on 2008-02-13
figured it out, marking as solved.

---


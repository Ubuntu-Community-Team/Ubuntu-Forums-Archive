---
title: "PHP select field where one entry equals entry in another field in same table"
date: 2011-06-20
forum: Programming Talk
---

### Post by gillespiea on 2011-06-20
Hi folks

I'm currently making a new website and using a mysql database from a CMS i am currently using on my operating website.

I know its a bad idea to use someone elses data base but i would like to so that i can keep all the data the way it is.

my problem is that on my forums page i need to organise the topics under parent topics.

i.e i have the parent topic "General" and the sub topic "General chit chat" then the parent topic "admin" and the sub topic "only admins can see this" etc etc.

the problem i have with this is that i have no idea how the CMS managed to order these from the same part of a database.

The Parent fields have a forum_parent = 0 and the sub topic forum_parent = the forum_id of the forum_parent.

make sense? probably not.

all i need to figure out is, how do i select a field where the forum_parent = forum_id of a different field?

i'm coding in php

thanks in advance for your help

---

### Post by Petrolea on 2011-06-20
I'm not even sure if I understand this question correctly as it is a bit confusing. 

But, how about making a loop that will compare the sub forum's value to every other entry in that table and see where the entries are equal. 

Something like this:

1. Count all rows in table that could match, make a loop that will repeat row-times (if there are 10 rows, loop will loop 10 times).

2. Compare values from one query to another (because I really can't think of a SQL way to do this). For example: One query (or some value) will be set to 10, now compare all results from query to that value and see if there will be a hit.

3. When found, save the value somewhere (if you even need to) and break the loop.

This is a way on how to do it, I don't know if it is correct in your case, but it should work if you implement it correctly in your code.

Hope this cleared things up at least a bit. (if it didn't, you can post a small section out of your database so it will be easier for us to find a real solution).

---

### Post by gillespiea on 2011-06-20
This is what i've got at the moment.
I've set it to only select the fields where forum_parent = 0 at the moment so that i only get the parents. This was so that i could then make another page to display the sub topics. But i don't want to keep it this way. i'd rather show the sub topics (where forum_parent = forum_id of parent) under the parent.

[PHP]<?php session_start(); ?>

<?php

include "theme.php";


doDB();

//gather the topics
$get_topics_sql = "SELECT * FROM forum WHERE forum_parent = 0 ORDER BY forum_order ASC";
$get_topics_res = mysqli_query($mysqli, $get_topics_sql) or die(mysqli_error($mysqli));

if (mysqli_num_rows($get_topics_res) < 1) {
	//there are no topics, so say so
	$display_block = "<table id=\"news\"><tr><td><p><em>No topics exist.</em></p></table>
";
} else {
	//create the display string
	$display_block = "
	<table>
	";

	while ($topic_info = mysqli_fetch_array($get_topics_res)) {
		$parent_id = $topic_info['forum_id'];
		$topic_title = stripslashes($topic_info['forum_name']);
		$brief = $topic_info['forum_description'];
		$lastpost = stripslashes($topic_info['forum_lastpost_user']);
		$posts_no = stripslashes($topic_info['forum_threads']);
		$parent = $topic_info['forum_parent'];
		
		
	 


		//add to display
		
	$display_block .= "
		<tr>
<td id=\"news\">

		<strong>".$topic_title."</strong></a><br>
".$brief."
</td><td>".$lastpost."</td></tr>

";}
	//free results
	mysqli_free_result($get_topics_res);


	//close connection to MySQL
	mysqli_close($mysqli);

	//close up the table
	$display_block .= "</table>";
}
?>


<?php echo $mainb;?>
<?php echo $display_block;?>
<?php echo $maine;?>[/PHP]

---

### Post by gillespiea on 2011-06-20
Ok, to make it clearer i need to display the information as follows

Parent name
---Sub topic with $forum_parent = parent $forum_id
---Sub topic with $forum_parent = parent $forum_id
---Sub topic with $forum_parent = parent $forum_id
---Sub topic with $forum_parent = parent $forum_id

Parent name
---Sub topic with $forum_parent = parent $forum_id
---Sub topic with $forum_parent = parent $forum_id
---Sub topic with $forum_parent = parent $forum_id

parent name
---Sub topic with $forum_parent = parent $forum_id
---Sub topic with $forum_parent = parent $forum_id

parent name
---Sub topic with $forum_parent = parent $forum_id

and so on

---

### Post by LoneWolfJack on 2011-06-20
are you by chance confusing the terms "topic" and "forum"?

consider this pseudocode:

```

$forumids = (SELECT forum_id FROM forums WHERE forum_id_parent=0);
foreach($forumids as $fid)
	{
	$subforumids = (SELECT forum_id FROM forums WHERE forum_id_parent=$fid);
	foreach($subforumids as $sfid)
		{
		$subforum = (SELECT * FROM forums WHERE forum_id=$sfid);
		echo $subforum['forum_title'];
		}
	}

```

---

### Post by pnewbie on 2011-06-21
I think you don't need, the third query. Only the first two queries in the pseudocode provided by LoneWolfJack will meet your requirements.

---

### Post by LoneWolfJack on 2011-06-21
you can combine the second and third query. I separated them to better demonstrate the basic logic.

---

### Post by gillespiea on 2011-06-21
thanks for the help folks, i'll give it a shot and let you know how it goes.

---

### Post by gillespiea on 2011-06-21
OK, little confused. where am i putting this code...in place of what? and, it doesnt seem to be valid... there are ( in the place where i'd use a "
Just a different way of coding?

---

### Post by gillespiea on 2011-06-21
ok i have it working.

Here is what i ended up with.
i know there is some funny names for things in there like $subttt
but it makes sense to me.

[PHP]<?php session_start(); ?>

<?php

include "theme.php";


doDB();

//gather the topics
$get_topics_sql = "SELECT * FROM forum WHERE forum_parent = 0 ORDER BY forum_order ASC";
$get_topics_res = mysqli_query($mysqli, $get_topics_sql) or die(mysqli_error($mysqli));



if (mysqli_num_rows($get_topics_res) < 1) {
	//there are no topics, so say so
	$display_block = "<table id=\"news\"><tr><td><p><em>No topics exist.</em></p></table>
";
} else {
	//create the display string
	$display_block = "
	<table>
	";

	while ($topic_info = mysqli_fetch_array($get_topics_res)) {
		$parent_id = $topic_info['forum_id'];
		$parentname = $topic_info['forum_name'];
		$brief = $topic_info['forum_description'];
		$lastpost = stripslashes($topic_info['forum_lastpost_user']);
		$posts_no = stripslashes($topic_info['forum_threads']);
		$parent = $topic_info['forum_parent'];
			if ($parent=="0")
		$par = $topic_info['forum_id'];
		
		
		$subt = "SELECT * FROM forum WHERE forum_parent = $par ORDER by forum_order";
		$subtt = mysqli_query($mysqli, $subt) or die(mysqli_error($mysqli));
			$sub = "<br>";
			while($subttt = mysqli_fetch_array($subtt)) {
				$su = $subttt['forum_name'];
				$id = $subttt['forum_id'];
				$brief = $subttt['forum_description'];
				$lastpost = stripslashes($subttt['forum_lastpost_user']);
				
				
			$sub .= "<a href=\"topiclist.php?forum_parent=$id\"><h1>".$su."</h1></a>".$brief."<br>last post by ".$lastpost."";
	 		$sub .= "";}


		//add to display
		
	$display_block .= "
		<tr><td id=\"forum\">
<h1>".$parentname."</h1>";

	$display_block .= "

		".$sub."
</td>


";}
	//free results
	mysqli_free_result($get_topics_res);


	//close connection to MySQL
	mysqli_close($mysqli);

	//close up the table
	$display_block .= "</table>";
}
?>


<?php echo $mainb;?>
<?php echo $display_block;?>
<?php echo $maine;?>[/PHP]

---


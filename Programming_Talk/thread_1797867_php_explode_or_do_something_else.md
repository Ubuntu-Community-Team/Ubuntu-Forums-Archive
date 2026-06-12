---
title: "php explode? or do something else?"
date: 2011-07-05
forum: Programming Talk
---

### Post by gillespiea on 2011-07-05
Hi folks,
i have a table in my msql database where more than one piece of information is stored in the one place. i.e. members attending = 1,2,3,4
each number is the user_id
anyway!
i can explode the data ok, the only thing is...i want to show all the people attending an event...not just the one of them.

Anyone know how i can do this?

---

### Post by SeijiSensei on 2011-07-05
Harder but better solution is to redesign the database.

Create a table (called "attendance" below) with two fields, the event ID and the user ID of each attendee.  (For extra credit, make sure that "referential integrity" is maintained by using foreign key references.)  That gives you a one-to-many relationship between events and attendees.  Then write a query like

```
select * from attendance left join attendees using (attendee_id) left join events using (event_id) where event_id='12345';
```

Otherwise use explode() as you suggest.  Running 

```

$attendees=explode(",",str_replace(" ","",$attendee_list));

```

will return an array of attendee IDs.  Just iterate over that with a for() loop.

---

### Post by roccivic on 2011-07-05
> **gillespiea said:**
> Anyone know how i can do this?
Do what?

You want to print all members that are attending the party? Ok, but why would explode() leave you with only one? Explode will merely make an array for you from a string, it's your job to use the array. E.g.:

[PHP]
<?php
// assuming that we are already connected to mysql and that we
// already got the 'members attending' data and that it is
// stored in $attending = '1,2,3,4,5'

echo "People attending this party:<br />";

$party_people = explode(',', $attending);
foreach ($party_people as $key => $person) {
    $res = mysql_query("SELECT `firstname`, `lastname` FROM `users` WHERE uid=$person");
    $data = mysql_fetch_assoc($res);
    echo "{$data['firstname']} {$data['lastname']} <br />";
}

die('That would be everyone so far!');
?>
[/PHP]

I think that you are asking the wrong question anyway. You should have stored the IDs of the attending members in a separate table, so that you can join this table onto the `users` table and be done with it in just one query and avoid being in the situation that you find yourself in. E.g.:

[PHP]
<?php
$partyid = getPartyId();
$res = mysql_query("SELECT `firstname`, `lastname` FROM `users_attending` AS a INNER JOIN `users` AS b ON a.uid = b.uid WHERE partyid=$partyid");
echo "People attending this party:<br />"; 
while ($data = mysql_fetch_assoc($res)) {
    echo "{$data['firstname']} {$data['lastname']} <br />";
}
?>
[/PHP]


[EDIT]: I guess that SeijiSensei beat me to it :D

---

### Post by gillespiea on 2011-07-05
Hmm i suppose you guys are right. It will be much easier just to make a new database than use all this. Only reason i was trying it that way was is to learn more about php and to try stop making numerous databases.

Cheers for the help :D

---

### Post by gillespiea on 2011-07-06
For anyone interested this is the page i came up with. I first created a database called attending with the following tables, att_id, usr_id and event_id.

[PHP]<?php

include "theme.php";

doDB();
//check for required info from the query string
if (!isset($_GET["event_id"])) {
	header("Location: ../");
	exit;
}
//gather the topics
$get_topics_sql = "SELECT * FROM Events, user WHERE Events.event_id = '".$_GET["event_id"]."' AND user.user_id = Events.event_creator ";
$get_topics_res = mysqli_query($mysqli, $get_topics_sql) or die(mysqli_error($mysqli));

if (mysqli_num_rows($get_topics_res) < 1) {
	//there are no topics, so say so
	$display_block = "<table><tr><td><em>No comments exist.</em></td></tr></table>";
} else {
	//create the display string
	$display_block = "
	<table id=\"news\">
	";

	while ($topic_info = mysqli_fetch_array($get_topics_res)) {
		$news_id = $topic_info['event_id'];
		$news_title = stripslashes($topic_info['event_name']);
		$news_text = nl2br(strip_tags($topic_info['event_text']));
		$nowner = stripslashes($topic_info['user_name']);
		$id = $topic_info['user_id'];
		$start = $topic_info['event_date'];
		$end = $topic_info['event_enddate'];
		$location = stripcslashes($topic_info['event_location']);
		$getatt = $topic_info['event_attending'];
		$attsep = explode(".", $getatt);
		
		
		
		//get attendees
$get_att_sql = "SELECT * FROM attending, user WHERE attending.event_id = '".$_GET["event_id"]."' AND attending.usr_id = user.user_id";
$get_att_res = mysqli_query($mysqli, $get_att_sql) or die(mysqli_error($mysqli));

if (mysqli_num_rows($get_att_res) < 1) {
	//there are no topics, so say so
	$display_block = "<table><tr><td><em>No comments exist.</em></td></tr></table>";
} else {
	//create the display string
	$attendees = "
	
	";

	while ($att_info = mysqli_fetch_array($get_att_res)) {
		$att = $att_info['user_name'];

		
		$attendees .= "$att,";
		}
		
		
		}
		
		$attendees .= "";
		
		
		
		

		//add to display
		$display_block .= "
		<tr>
<td id=\"forum\">
<h1>".$news_title."</h1>
		".$news_text."<br><br>
		Starts on : $start<br>
		Ends on : $end<br>
		Happening in : $location<br>
		People attending : $attendees
		<p id=\"link\">Created by <a href=profile.php?id=$id>".$nowner."</a> 
</td></tr>";}
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
<? include("comments.php"); ?>
<?php echo $maine;?>


[/PHP]

---


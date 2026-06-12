---
title: "Nested mysql_query's ?"
date: 2010-02-07
forum: Programming Talk
---

### Post by PartisanEntity on 2010-02-07
Hi all,

I am trying to make my own rating script.

I have a gallery of images, and have assigned a vote to each one from different user accounts in my CMS.

My script is supposed to run a mysql_query and get the image meta-data (i.e. src, username of the user who created the image, the id of the image)

Then another mysql_query takes each image's id and checks to see if the currently logged in user has voted for an image.

For example using my "admin" account I only voted for 1 of the images, yet my script is displaying my username and vote below all the images.

I guess its a logic error, but I can't get my head around it, any ideas?

[PHP]
<?php

//include our db data to make the connection
include ('db.php');

	$content = mysql_query("SELECT * FROM cars ORDER BY id DESC");
	
	
	while($row = mysql_fetch_array($content))
  {
  
  	$mainImage = $row['mainImage'];
	$oid = $row['oid'];
	$thumbImage = $row['thumbImage'];
	$car_username = $row['username'];
	$username = $_SESSION['username'];
	$date = $row['date'];
	
	//get sitename from config table
		$content2 = mysql_query("SELECT * FROM votes WHERE oid = '$oid' AND username = '$username'");
		
		while($row2 = mysql_fetch_array($content2))
		  {
			$voter = $row2['username'];
			$vote = $row2['vote'];
		  }
	
  	echo '<div class="gallimg"';
	echo '<a href="'.$mainImage.'" name="'.$oid.'" rel="lightbox[cars]"><img src="'.$thumbImage.'" title="'.$car_username.'s car"/></a><br />';
	echo 'by <span class="fat">'.$car_username.'</span> on '.$date.'<br />';
	echo $voter;
	echo $vote;
	echo "</div>";	  
	
  }

?>
[/PHP]

---

### Post by Bachstelze on 2010-02-07
For starters, you want to use [mysql_fetch_assoc()]("http://fr.php.net/manual/en/function.mysql-fetch-assoc.php") instead of [mysql_fetch_array()]("http://fr.php.net/manual/en/function.mysql-fetch-array.php").

---

### Post by PartisanEntity on 2010-02-07
Thanks for your response, that doesn't solve the logic issue however I am afraid. Any ideas ?

---

### Post by Some Penguin on 2010-02-07
If you don't want it echoing after every image, you might want to check a conditional on the echos instead of actually echoing after every image.

---

### Post by PartisanEntity on 2010-02-07
I thought that if an image has no vote associated with it, then nothing should be echoed? (instead its taking the vote that is associated with say, image 1, and echoing it under all other images, this is the problem i dont understand)

---

### Post by Bachstelze on 2010-02-07
> **PartisanEntity said:**
> I thought that if an image has no vote associated with it, then nothing should be echoed?

What makes you think that?

[php]<?php

//include our db data to make the connection
include ('db.php');

$content = mysql_query("SELECT * FROM cars ORDER BY id DESC");
        
while($row = mysql_fetch_assoc($content))
{
    $mainImage = $row['mainImage'];
    $oid = $row['oid'];
    $thumbImage = $row['thumbImage'];
    $car_username = $row['username'];
    $username = $_SESSION['username'];
    $date = $row['date'];

    echo '<div class="gallimg"';
    echo '<a href="'.$mainImage.'" name="'.$oid.'" rel="lightbox[cars]"><img src="'.$thumbImage.'" title="'.$car_username.'s car"/></a><br />';
    echo 'by <span class="fat">'.$car_username.'</span> on '.$date.'<br />';
    
    //get sitename from config table
    $content2 = mysql_query("SELECT * FROM votes WHERE oid = '$oid' AND username = '$username'");
        
    while($row2 = mysql_fetch_array($content2))
    {
        $voter = $row2['username'];
        $vote = $row2['vote'];
        echo $voter;
        echo $vote;
    }

    echo "</div>";      
}
[/php]

This should do what you want. First display the image, then fetch the voters' names and display them if there is any. I also fixed your indentation and removed the PHP closing tag (it is not required, so you should only put it if you have a very good reason to, which is not the case here).

---

### Post by PartisanEntity on 2010-02-07
> **Bachstelze said:**
> What makes you think that?

[php]<?php

//include our db data to make the connection
include ('db.php');

$content = mysql_query("SELECT * FROM cars ORDER BY id DESC");
        
while($row = mysql_fetch_assoc($content))
{
    $mainImage = $row['mainImage'];
    $oid = $row['oid'];
    $thumbImage = $row['thumbImage'];
    $car_username = $row['username'];
    $username = $_SESSION['username'];
    $date = $row['date'];

    echo '<div class="gallimg"';
    echo '<a href="'.$mainImage.'" name="'.$oid.'" rel="lightbox[cars]"><img src="'.$thumbImage.'" title="'.$car_username.'s car"/></a><br />';
    echo 'by <span class="fat">'.$car_username.'</span> on '.$date.'<br />';
    
    //get sitename from config table
    $content2 = mysql_query("SELECT * FROM votes WHERE oid = '$oid' AND username = '$username'");
        
    while($row2 = mysql_fetch_array($content2))
    {
        $voter = $row2['username'];
        $vote = $row2['vote'];
        echo $voter;
        echo $vote;
    }

    echo "</div>";      
}
[/php]

This should do what you want. First display the image, then fetch the voters' names and display them if there is any. I also fixed your indentation and removed the PHP closing tag (it is not required, so you should only put it if you have a very good reason to, which is not the case here).

Thanks a lot!, this worked, even though I am still not quite sure what the main difference is between mysql_query and mysql_fetch_array.

---

### Post by Bachstelze on 2010-02-07
> **PartisanEntity said:**
> Thanks a lot!, this worked, even though I am still not quite sure what the main difference is between mysql_query and mysql_fetch_array.

mysql_query returns the result of a query, but in a format that is not usable by other functions. In order to actually use the data, you have to extract it from the object returned by mysql_query, using mysql_fetch_array or suchlike.

*EDIT: mysql_query can also refurn FALSE if the query failed, which allows to detect failure before attempting to use data from a query.*

---

### Post by Some Penguin on 2010-02-07
If you're still confused, ask yourself this:

Your original code looks like:

for each image
    set the voting variables to the LAST matching vote, if there is one
    print out stuff even if the voting variables weren't changed

---

### Post by PartisanEntity on 2010-02-08
Hi again,

Just to give you an idea of what I am trying to achieve:

The script should check to see if the current user has voted for an image, if they have, then it should show them the current rating for the image. This works.

If they have not voted for an image, it should display the vote box. This is not working.

The problem is that my part of the script that should display the vote box is not being carried out for all images, but only as many times as the number of results returned by the script. I have attached a screenshot.

i.e. if only two images have been voted for, then the vote box is displayed for only two images that have not been voted for. So the number of times the vote box is displayed, is based on how many images have been voted for, but I want it to display for any image that has not been voted for.

I hope I have managed to explain it somewhat.

[PHP]<?php

//include our db data to make the connection
include ('db.php');

$content = mysql_query("SELECT * FROM cars ORDER BY id DESC");
        
while($row = mysql_fetch_assoc($content))
{
    $mainImage = $row['mainImage'];
    $oid = $row['oid'];
    $thumbImage = $row['thumbImage'];
    $car_username = $row['username'];
    $username = $_SESSION['username'];
    $date = $row['date'];

    echo '<div class="gallimg"';
    echo '<a href="'.$mainImage.'" name="'.$oid.'" rel="lightbox[cars]"><img src="'.$thumbImage.'" title="'.$car_username.'s car"/></a><br />';
    echo 'by <span class="fat">'.$car_username.'</span> on '.$date.'<br />';
    
    //get sitename from config table
    $content2 = mysql_query("SELECT * FROM votes WHERE oid = '$oid' AND username = '$username'");
        
    while($row2 = mysql_fetch_array($content2))
    {
        $voter = $row2['username'];
        $vote = $row2['vote'];
    }
	
		//if the user has voted for an image
		if (strlen($voter) > 1) {
			//show the average vote
				$content3 = mysql_query("SELECT SUM(vote) FROM votes WHERE oid = '$oid'");
				
					  while($row3 = mysql_fetch_array($content3))
						{
							$totalVotes = $row3['SUM(vote)'];
						}
						
				$content4 = mysql_query("SELECT * FROM votes WHERE oid = '$oid'");
						
						$numbVoters = mysql_affected_rows();
						
						if (strlen($totalVotes) > 0 && strlen($numbVoters) > 0) {
							echo 'Rating: <span class="fat">' . $totalVotes / $numbVoters . '</span> Votes: ' . $numbVoters;
						}
						
				
		} else {
			//show the vote box, and for testing purposes display the words: no vote
echo 'no vote';

		}

    echo "</div>";      
} [/PHP]

---

### Post by tomchuk on 2010-02-08
You should be able to do this in a single query. If you ever find yourself writing one (let alone three) queries inside a loop, take a step back and try to do it in SQL.

Also, always use mysql_real_escape_string on every variable you're passing into a query. Depending on your session storage and username vaildation, your query could have lead to some nice SQL injection, à la [Bobby Tables](http://xkcd.com/327/).

Try something like this:

[php]
<?php

include ('db.php'); 
$result = mysql_query(
  "SELECT 
    c.oid, 
    c.mainImage, 
    c.thumbImage, 
    c.username,
    c.date,
    AVG(v.vote) AS avg_vote,
    COUNT(v.vote) AS num_votes,
    (SELECT COUNT(vote) FROM votes WHERE username='" . 
      mysql_real_escape_string($_SESSION['username']) . "' AND oid=c.oid) AS voted
   FROM 
     cars c 
    LEFT JOIN 
     votes v 
    USING(oid) 
   GROUP BY c.oid
   ORDER BY c.oid DESC");

while ($r = mysql_fetch_object($result)){
    echo '<div class="gallimg">';
    echo '<a href="' . $r->mainImage . '" name="' . $r->oid . '" rel="lightbox[cars]">';
    echo '<img src="' . $r->thumbImage . '" title="' . $r->username . '\'s Car"/></a><br/>';
    echo 'by <span class="fat">' . $r->username . '</span> on ' . $r->date . '<br />'; 

    if ($r->num_votes && $r->voted){
        echo 'Rating: <span class="fat">' . $r->avg_vote . '</span> Votes: ' . $r->num_votes;
    }
    else {
        echo 'no vote';
    }

    echo '</div>';
}
  
?>

[/php]

---

### Post by PartisanEntity on 2010-02-09
Thank you so much tomchuk, this is an amazingly elegant solution in comparison to my rather primitive approach :)

Can I add "ORDER BY ID DESC" to the end of the query? (Am at the office right now so can't test it).

---

### Post by Hellkeepa on 2010-02-09
HELLo!

If that id is "c.oid", then yes.

Happy codin'!

---

### Post by tomchuk on 2010-02-09
> **PartisanEntity said:**
> Thank you so much tomchuk, this is an amazingly elegant solution in comparison to my rather primitive approach :)

Can I add "ORDER BY ID DESC" to the end of the query? (Am at the office right now so can't test it).

Yup, as Hellkeepa said: "ORDER BY c.oid DESC". I've updated my post above.

---

### Post by PartisanEntity on 2010-02-09
Thanks to the both of you, when I posted earlier I actually meant c.oid but my brain was off by then.

Once again, thank you very much.

---


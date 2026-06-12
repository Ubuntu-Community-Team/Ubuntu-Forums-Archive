---
title: "PHP basic help, need to connect a form and a script"
date: 2009-10-18
forum: Programming Talk
---

### Post by Lukas1 on 2009-10-18
Hi all,

I am trying to break up one piece of code that I got from a programming book (Sam's PHP, MySQL, and Apache all in one) into two scripts, one a form which tells the other to act. 

The concept is that this is a forum and if you show a thread and then click a link on a particular post, it will bring you to a form to fill in a reply to the post. Here is the code that I need to split up:


<?php
include("ch21_include.php");
doDB();

//check to see if we're showing the form or adding the post
if (!$_POST) {
	//showing the form; check for required item in query string
	if (!isset($_GET["post_id"])) {
		header("Location: topiclist.php");
		exit;
	}
	
	//still have to verify topic and post
	$verify_sql = "SELECT ft.topic_id, ft.topic_title FROM forum_posts
		AS fp LEFT JOIN forum_topics AS ft ON fp.topic_id =
		ft.topic_id WHERE fp.post_id = '".$_GET["post_id"]."'";
		
	$verify_res = mysqli_query($mysqli, $verify_sql)
		or die(mysqli_error($mysqli));
		
	if (mysqli_num_rows($verify_res) < 1) {
		//this post or topic does not exist
		header("Location: topiclist.php");
		exit;
	} else {
		//get the topic id and title
		while($topic_info = mysqli_fetch_array($verify_res)) {
			$topic_id = $topic_info['topic_id'];
			$topic_title = stripslashes($topic_info['topic_title']);
		}
	
	//add to display
	$display_block = "	
	
	<html>
	<head>
	<title>Post Your Reply in ".$topic_title."</title>
	</head>
	<body>
	<h1>Post Your Reply in $topic_title</h1>
	<form method=\"post\" action=\"".$_SERVER["PHP_SELF"]."\">
	<p><strong>Your E-Mail Address:</strong><br/>
	<input type=\"text\" name=\"post_owner\" size=\"40\"
	maxlength=\"150\"></p>
	<p><strong>Post Text:</strong><br/>
	<textarea name=\"post_text\" rows\"8\" cols=\"40\"
	wrap=\"virtual\"></textarea>
	<input type=\"hidden\" name=\"topic_id\" value=\"$topic_id\">
	<p><input type=\"submit\" name=\"submit\" value=\"Add Post\"></p>
	</form>
	</body>
	</html>";
		
}

//free result
mysqli_free_result($verify_res);

//close connection to mysql
mysqli_close($mysqli);

} else if ($_POST) {
	//check for required items from form
	if ((!$_POST["topic_id"]) || (!$_POST["post_text"]) ||
	(!$_POST["post_owner"])) {
		header("Location: topiclist.php");
		exit;
	}
	
	//add the post
	$add_post_sql = "INSERT INTO forum_posts (topic_id, post_text,
		post_create_time, post_owner) VALUES
		('".$_POST["topic_id"]."', '".$_POST["post_text"]."',
		now(), '".$_POST["post_owner"]."')";
	$add_post_res = mysqli_query($mysqli, $add_post_sql)
		or die(mysqli_error($mysqli));
		
	//close connection to mysqli
	mysqli_close($mysqli);
	
	//redirect user to topic
	header("Location: showtopic.php?topic_id=".$_POST["topic_id"]);
	exit;
}
?>


Now since I want to use a form to input from a separate script, I don't understand how I can get the information I need to populate my database.

Here is my new form:

<form method="post" action="do_addpost.php">
<p><strong>Your E-mail Address:</strong><br/>
<input type="text" name="post_owner" size="40" maxlength="150"/></p>
<p><strong>Post Text:</strong><br/>
<textarea name="post_text" rows="8" cols="40" wrap="virtual"></textarea></p>
<p><input type="submit" name="submit" value="Add Post"/></p>
</form>

Thank you for your time, and programming has never been my strongest subject so I do appreciate it.

---

### Post by NoaHall on 2009-10-18
The form, on the click of "submit", will send the data $_POST['post_owner'] and $_POST['post_text'] to do_addpost.php, and then perform the script, using the given values.

You need to add another box for $_POST["topic_id"], with the name topic_id. I believe, although not quite sure what you want, that you should also redirect the user to the html page with the form on if it's not set.

---

### Post by Lukas1 on 2009-10-20
I know that I need that variable, but is there any way to get that from the information we have? For example, when you click "reply to post" and it brings you to the addpost.php form, it has the post_id in the URL, like localhost/addpost.php?post_id=26 

In my database I have two tables, forum_posts and forum_topics. The forum_posts table has 5 fields; post_id, topic_id, post_text, post_create_time, and post_owner. This is where my script should be placing the information from the addpost.php form. The post_owner and post_text are from the form, the post_create_time is in the code, the post_id should be the next number. 

Since this is a forum where posts need to relate to a topic, using the post_id number, how could I get the topic_id from the post I am responding to and carry that into my do_addpost.php script?

Thank you

---

### Post by NoaHall on 2009-10-20
Well, it'd be

```

$variable=mysql_query("Select post_id from *); (or whatever code you have)

```
Then replace $post_id with $variable. If you see what I mean.

---

### Post by Lukas1 on 2009-10-20
Thank you for helping, NoaHall.

As you can see, I have something kind of like that (or so I think) but it must not be passing the verify_res test because it keeps redirecting me back to topiclist.php. I wonder why my select statement is not picking up what I need from the tables.
BTW I have this online at [www.globalcapeesh.com/topiclist.php]("http://www.globalcapeesh.com/topiclist.php")

```
<?php
include("ch21_include.php");
doDB();

//check for required fields from the form
if ((!$_POST["post_owner"]) || (!$_POST["post_text"])) {
	header("Location: addpost.php");
	exit;
}
	
//still have to verify topic and post
	$verify_sql = "SELECT ft.topic_id, ft.topic_title FROM forum_posts
		AS fp LEFT JOIN forum_topics AS ft ON fp.topic_id =
		ft.topic_id WHERE fp.post_id = '".$_GET["post_id"]."'";
		
	$verify_res = mysqli_query($mysqli, $verify_sql)
		or die(mysqli_error($mysqli));
		
	if (mysqli_num_rows($verify_res) < 1) {
		//this post or topic does not exist
		header("Location: topiclist.php");
		exit;
	} else {
		//get the topic id and title
		while($topic_info = mysqli_fetch_array($verify_res)) {
			$topic_id = $topic_info['topic_id'];
			$topic_title = stripslashes($topic_info['topic_title']);
		}
	
			
}

//free result
mysqli_free_result($verify_res);

//close connection to mysql
mysqli_close($mysqli);


	
	//add the post
	$add_post_sql = "INSERT INTO forum_posts (topic_id, post_text,
		post_create_time, post_owner) VALUES
		('".$_POST["topic_id"]."', '".$_POST["post_text"]."',
		now(), '".$_POST["post_owner"]."')";
	$add_post_res = mysqli_query($mysqli, $add_post_sql)
		or die(mysqli_error($mysqli));
		
	//close connection to mysqli
	mysqli_close($mysqli);
	
	//redirect user to topic
	header("Location: showtopic.php?topic_id=".$_POST["topic_id"]);
	exit;

?>
```

---

### Post by NoaHall on 2009-10-20
I assume you've set up all your variables in ch21_include.php. If not, you need to define some variables.

Hm, and are you sure "post_id" is set as $_GET on the previous page?

---

### Post by Lukas1 on 2009-10-21
As you can see below, my ch21_include.php file declares the $mysqli variable.

```
<?php

function doDB() {
	global $mysqli;

	//connect to server and select database; you may need it
	$mysqli = mysqli_connect("localhost", "****", "****", "****");

	//if connection fails, stop script execution
	if (mysqli_connect_errno()) {
		printf("Connect failed: %s\n", mysqli_connect_error());
		exit();
	}
}
?>
```

I don't know that post_id is set as $_GET, but the showtopic.php page is the page leading in to the form and it looks like this:

```
<?php
include("ch21_include.php");
doDB();
//check for required info from the query string
if (!isset($_GET["topic_id"])) {
	header("Location: topiclist.php");
	exit;
}

//verify the topic exists
$verify_topic_sql = "SELECT topic_title FROM forum_topics
	WHERE topic_id = '".$_GET["topic_id"]."'";
$verify_topic_res = mysqli_query($mysqli, $verify_topic_sql)
	or die(mysqli_error(Smysqli));
	
if (mysqli_num_rows($verify_topic_res) < 1) {
	//this topic does not exist
	$display_block = "<p><em>You have selected an invalid topic.<br/>
	Please <a href=\topiclist.php\">try again</a>.>/em></p>";
} else {
	//get the topic title
	while ($topic_info = mysqli_fetch_array($verify_topic_res)) {
		$topic_title = stripslashes($topic_info['topic_title']);
	}
	
	//gather the posts
	$get_posts_sql = "SELECT post_id, post_text, DATE_FORMAT(post_create_time,
		'%b %e %y at %r') AS fmt_post_create_time, post_owner
		FROM forum_posts
		WHERE topic_id = '".$_GET["topic_id"]."'
		ORDER BY post_create_time ASC";
	$get_posts_res = mysqli_query($mysqli, $get_posts_sql)
			or die(mysqli_error($mysqli));
	
	//create the display string
	$display_block = "
	<p>Showing posts for the <strong>".$topic_title."</strong> topic:</p>
	<table width=\100%\" cellpadding=\"3\" cellspacing=\"1\" border=\"1\">
	<tr>
	<th>AUTHOR</th>
	<th>POST</th>
	</tr>";
	while ($posts_info = mysqli_fetch_array($get_posts_res)) {
		$post_id = $posts_info['post_id'];
		$post_text = nl2br(stripslashes($posts_info['post_text']));
		$post_create_time = $posts_info['fmt_post_create_time'];
		$post_owner = stripslashes($posts_info['post_owner']);
		
		//add to display
		$display_block .= "
		<tr>
		<td width=\"35%\" valign=\"top\">".$post_owner."<br/>
		[".$post_create_time."]</td>
		<td width=\"65%\" valign=\"top\">".$post_text."<br/><br/>
		<a href=\"addpost.php?post_id=".$post_id."\">
		<strong>REPLY TO POST</strong></a></td>
		</tr>";
	}
	
	//free results
	mysqli_free_result($get_posts_res);
	mysqli_free_result($verify_topic_res);
	
	//close connection to mysql
	mysqli_close($mysqli);
	
	//close table
	$display_block .= "</table>";
}
?>
<?php echo $display_block; ?>
<a href="topiclist.php">Show Topics</a>

```

---

### Post by NoaHall on 2009-10-21
Right, at the top of your pages, enter 
```
<?php session_start();
$_SESSION['topic_id']=$post_id;
?>
```
Then you can use ```
$_SESSION['topic_id']
``` in the other pages as topic_id. Note, you'll need session_start on every page.

---

### Post by Lukas1 on 2009-10-31
Thank you, I have been dieing to try this but haven't found the time. I hope to get to it early this week and I'll let you know how it goes.

---

### Post by Lukas1 on 2009-11-03
I've been thinking about this and have decided to install an elgg rather than try to fix the code. I'll close this thread, thank you anyways.

---


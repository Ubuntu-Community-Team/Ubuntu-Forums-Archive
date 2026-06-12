---
title: "dynamic php forum user info"
date: 2010-01-20
forum: Programming Talk
---

### Post by gillespiea on 2010-01-20
Hi folks. i've posted up a few times about a few problems i've had with my php and mysql coding and received alot of help (especially some that showed how vulnerable my site was to XSS).

I thought i would ask on here again about a problem i'm having. My coding has came on quite a bit in the last few months but now i am looking to make parts of my forums dynamic and i'm not too sure how to do it.
The parts i want to make dynamic are user's avatars and signatures, so that they change when the user changes them in the CP. Currently the users signatures are stored in their session cookie and avatars are not currently used (although i dont think it will take me too long to apply it). The details from the sessions are then used to post the data into the mysql database and then the forum reads it from there thus making it "static" (as on i can't change it without going into the users post and changing it from there.

So my question is. How can i adapt the following script to make the signature dynamic, reading from the "users" table rather than the "forum_posts" table. cheers.

[PHP]<?php session_start(); ?>
<?php

include("../includes/config.php");

doDB();



//check for required info from the query string

if (!isset($_GET["topic_id"])) {

	header("Location: topiclist.php");

	exit;

}



//verify the topic exists

$verify_topic_sql = "SELECT topic_title FROM forum_topics WHERE topic_id = '".$_GET["topic_id"]."'";

$verify_topic_res =  mysqli_query($mysqli, $verify_topic_sql) or die(mysqli_error($mysqli));



if (mysqli_num_rows($verify_topic_res) < 1) {

	//this topic does not exist

	$display_block = "<p><em>You have selected an invalid topic.<br/>

	Please <a href=\"topiclist.php\">try again</a>.</em></p>";

} else {

	//get the topic title

	while ($topic_info = mysqli_fetch_array($verify_topic_res)) {

		$topic_title = stripslashes($topic_info['topic_title']);

	}

$topic_id=$_GET["topic_id"];
$page=$_GET['page'];
$resultsPerPage=5;
$startResult=($page-1) * $resultsPerPage; 
$mysqli_query = "COUNT * FROM forum_posts WHERE topic_id = '".$_GET["topic_id"]."'" ;
$result = mysqli_query($mysqli, "COUNT * FROM forum_posts WHERE topic_id = '".$_GET["topic_id"]."'");

	//gather the posts

	$get_posts_sql = "SELECT signature, post_id, post_text, 

                  DATE_FORMAT(post_create_time, '%b %e %Y at %r') 

                  AS fmt_post_create_time, post_owner 

                  FROM forum_posts 

                  WHERE topic_id = '".$_GET['topic_id']."' 

                  ORDER BY post_create_time ASC LIMIT $startResult,$resultsPerPage";

	$get_posts_res = mysqli_query($mysqli, $get_posts_sql) or die(mysqli_error($mysqli));



	//create the display string

	$display_block = "

	<h2>Showing posts for the ".$topic_title." topic:</h2>

	<table width=\"90%\" cellpadding=\"3\" cellspacing=\"0\" border=\"0\">

	<tr>

	<th>AUTHOR</th>

	<th>POST</th>

	</tr>";



	while ($posts_info = mysqli_fetch_array($get_posts_res)) {

		$post_id = $posts_info['post_id'];

		$post_text = nl2br(strip_tags($posts_info['post_text']));

		$post_create_time = $posts_info['fmt_post_create_time'];

		$post_owner = stripslashes(strip_tags($posts_info['post_owner']));
		$signature = stripslashes(strip_tags($posts_info['signature']));



		//add to display

	 	$display_block .= "

		<tr>

		<td width=\"35%\" valign=\"top\"><h1>".$post_owner."</h1><strong>Posted on:</strong><br>".$post_create_time."</td>

		<td width=\"65%\" valign=\"top\">".$post_text."<hr><h3>".$signature."</h3>

		</td>

		</tr>";

	}



	//free results

	mysqli_free_result($get_posts_res);

	mysqli_free_result($verify_topic_res);







	//close up the table

	$display_block .= "</table>";

}

?>

<html>

<header>

<title>The Yarp</title>

<link rel="stylesheet" type="text/css" href="../styles/style.css">

</header>

<body>

<table width="90%" height="320" border="0" align="center" cellpadding="5" cellspacing="0">

  <tr> 

    <td height="141" colspan="3" align="center"><img src="../images/title.gif"></font></div> <div align="center"></div></td>

  </tr>

  <tr> 

    <td width="15%" height="160" valign="top"> 
      <?$root = $_SERVER['DOCUMENT_ROOT'];include $root . '/includes/login.php';?>

      <?$root = $_SERVER['DOCUMENT_ROOT'];include $root . '/includes/nav.php';?>
      <?$root = $_SERVER['DOCUMENT_ROOT'];include $root . '/includes/adminmenu.php';?>
      <?$root = $_SERVER['DOCUMENT_ROOT'];include $root . '/includes/adminadd.php';?>

    </td>

    <td width="843" height="160"> <table width="90%" border="0" align="center">

        <tr> 

          <td><?php echo $display_block; ?>
<?php if ($_SESSION["adminauth"] == "1" or $_SESSION["adminauth"] == "0")  echo "<a href=\"replytopost.php?post_id=".$post_id."\"><img src=\"reply.gif\" border=\"0\"></a>"; ?><br>

<?php $previous=$page-1;

if($previous > 0){
echo "<a href=\"showtopic.php?topic_id=".$topic_id."&page=$previous\">Previous </a>";
}
//Current page - no link
echo "Page $page";

$next=$page+1;
echo "<a href=\"showtopic.php?topic_id=".$topic_id."&page=$next\"> Next </a>"; 

if ( ($result/$resultsPerPage) > $page) {
$next=$page+1;
;
	//close connection to MySQL

	mysqli_close($mysqli);
}
else

?>
</td>

        </tr>

      </table></td>

    <td width="24"></td>

  </tr>

  <tr> 

    <td height="19"></td>

    <td></td>

    <td></td>

  </tr>

</table>

<footer><div align="center">Copyright &copy; Alastair Gillespie 2009<div></footer>

</body>

</html>[/PHP] 

PS you might also notice that i have a problem with my next page buttons. any help with that would be appreciated too.
Thanks for looking and taking the time to read through my lengthy post.

Alastair.

---

### Post by hessiess on 2010-01-20
This is vulnerable to SQL injection:
```

WHERE topic_id = '".$_GET['topic_id']."' 

```

NEVER include anything in SQL statements without running it through mysql_real_escape_string() first.

Also do not in-line HTML code in PHP, It is a one way ticket to messy, hard to read,  unmaintainable code. Use an MVC framework, or as a minimum, a templating language (which can just be plain PHP, i.e. [http://thephppro.com/articles/pte.php](http://thephppro.com/articles/pte.php)).

---

### Post by gillespiea on 2010-01-20
thanks for pointing out my security flaw mate :)
appreciated.

---

### Post by pers3vs on 2010-01-20
> **gillespiea said:**
> Hi folks. i've posted up a few times about a few problems i've had with my php and mysql coding and received alot of help (especially some that showed how vulnerable my site was to XSS).

So my question is. How can i adapt the following script to make the signature dynamic, reading from the "users" table rather than the "forum_posts" table. cheers.

[PHP]
// ...
	//gather the posts

	$get_posts_sql = "SELECT signature, post_id, post_text, 

                  DATE_FORMAT(post_create_time, '%b %e %Y at %r') 

                  AS fmt_post_create_time, post_owner 

                  FROM forum_posts 

                  WHERE topic_id = '".$_GET['topic_id']."' 

                  ORDER BY post_create_time ASC LIMIT $startResult,$resultsPerPage";

	$get_posts_res = mysqli_query($mysqli, $get_posts_sql) or die(mysqli_error($mysqli));



	//create the display string

	$display_block = "

	<h2>Showing posts for the ".$topic_title." topic:</h2>

	<table width=\"90%\" cellpadding=\"3\" cellspacing=\"0\" border=\"0\">

	<tr>

	<th>AUTHOR</th>

	<th>POST</th>

	</tr>";



	while ($posts_info = mysqli_fetch_array($get_posts_res)) {

		$post_id = $posts_info['post_id'];

		$post_text = nl2br(strip_tags($posts_info['post_text']));

		$post_create_time = $posts_info['fmt_post_create_time'];

		$post_owner = stripslashes(strip_tags($posts_info['post_owner']));
		$signature = stripslashes(strip_tags($posts_info['signature']));



		//add to display

	 	$display_block .= "

		<tr>

		<td width=\"35%\" valign=\"top\"><h1>".$post_owner."</h1><strong>Posted on:</strong><br>".$post_create_time."</td>

		<td width=\"65%\" valign=\"top\">".$post_text."<hr><h3>".$signature."</h3>

		</td>

		</tr>";

	}



	//free results

	mysqli_free_result($get_posts_res);

	mysqli_free_result($verify_topic_res);







	//close up the table

	$display_block .= "</table>";

}

?>
// ...
[/PHP] 

PS you might also notice that i have a problem with my next page buttons. any help with that would be appreciated too.
Thanks for looking and taking the time to read through my lengthy post.

Alastair.

Assuming your users table is in the same database as your forum_posts table, and that they have a common field through which a forum post can be JOINed to a specific user, adding a JOIN to your sql query gives you what you require. (There is an excellent SQL tutorial at [http://sqlzoo.net/]("http://sqlzoo.net/")) The example below assumes that *post_owner* is unique key to the users table and a common field (foreign key) between the two tables.

[PHP]
$get_posts_sql = "SELECT f.signature, f.post_id, f.post_text, 

                  DATE_FORMAT(f.post_create_time, '%b %e %Y at %r') 

                  AS fmt_post_create_time, u.post_owner, u.avatar 

                  FROM forum_posts f JOIN users u ON u.post_owner = f.post_owner

                  WHERE f.topic_id = '".mysql_real_escape_string($_GET['topic_id'])."' 

                  ORDER BY f.post_create_time ASC LIMIT $startResult,$resultsPerPage";
[/PHP]

Good Luck!

---

### Post by Hellkeepa on 2010-01-20
HELLo!

I've taken the liberty of cleaning up the code a bit. Fixing a couple of potential security issues, and made it generally more readable & clean:
[http://pastebin.com/f2d9a251](http://pastebin.com/f2d9a251)

Notice how I've reduced the two queries to one, using LEFT JOIN? As **pers3vs** said this is what you want to do with the users table as well, to fetch the signature from it. Should be quite easy to add it, in the code I've pasted above.

Also, I recommend using proper and semantic HTML for marking up content, and let CSS deal with the style issues. Tables should not be abused for layout purposes, but used only when there is actual tabular data to be displayed.

*Edit, added:*
Just noticed that I made a slight mistake in that script, using "topic_id" instead of "topic_title". Minor issue which is easy to fix, just wanted to make let you know as I can't be arsed to fix it myself. :-P

Happy codin'!

---

### Post by iMisspell on 2010-01-21
I too would create a template system for displaying the out-put along with a "cleaner" class for sql stuff.

[PHP]

class cleanStuff{

	private $val;
	
	function __construct(){
		
		if(isset($_POST)){
			foreach($_POST as $k => $v){
				
				/* if your consistent with your ID naming and end with _id */
				if(substr($k, -3) == '_id'){
					$this->val[$k] = intval ($v);
				} else {
					$this->val[$k] = self::clean($v);
				}
				
			}
		}
		
		if(isset($_GET)){
			foreach($_GET as $k => $v){
			
				/* if your consistent with your ID naming and end with _id */
				if(substr($k, -3) == '_id'){
					$this->val[$k] = intval ($v);
				} else {
					$this->val[$k] = self::clean($v);
				}
				
			}
		}
	
	}
	
	private function clean($data){
		
		$data = stripslashes($data);

		# http://php.net/manual/en/function.mysql-real-escape-string.php
		$data = mysql_real_escape_string($data);
	
	}
	
	
	public function get($what){
		return $this->val[$what];
	}
	

}

[/PHP]
Thats just an example, un-tested and still alot more work would be needed.

Call that on any page which you deal with any $_GET or $_POST.
[PHP]
$cleaned = New cleanStuff();

// Then to get a varibule:
$newPostTitle = $cleaned->get('Post_Title');

// Would be a safer way compared to...
$newPostTitle = $_POST['Post_Title'];

// or

$topic_id = $cleaned->get('topic_id');

[/PHP]


**Hellkeepa**, why do you initialize your variables with '' and not NULL ( $Pagination = ''; ) ?
Just wondering.

_

---

### Post by Hellkeepa on 2010-01-21
HELLo!

For the first '' is shorter, and for the second that way PHP does not have to cast the NULL to an empty string before concatenating. ;-)
Also helps on the readability, as you can clearly see what kind of content goes/should go into the variable; A string in this case.

Happy codin'!

---

### Post by iMisspell on 2010-01-21
Thanks...
> **Hellkeepa said:**
> For the first '' is shorter, and for the second that way PHP does not have to cast the NULL to an empty string before concatenating. ;-)
I know there is a little difference ;) between PHP and VB6, in VB6 we would use nullstring (or stringnull, i forget its been a long time) so not to use up memory (if your declaring a lot of variables) because '' would hold the weight of a character, null would not.
In PHP, the resources used for casting would out-way the memory used ? Or does it not work the same ?

_

---

### Post by Hellkeepa on 2010-01-21
HELLo!

For all intents and purposes, it's the same. I haven't studied the internals of PHP, nor done any benchmarking on this, so I can't say anything about what the usage is in either case. All I know is that it's not  noticeable, and there are about a million other things one can do to optimize an application before deciding whether to use NULL or an empty string. ;-)
My primary reasons for using that particular convention stems from it being similar to C, and the quickness of writing it.

Happy codin'!

---

### Post by gillespiea on 2010-01-26
thanks everyone for your time and effort. It's very appreciated!

---

### Post by gillespiea on 2010-01-26
hey hellkeepa,
thanks for all the work you put into helping me. I've been looking over it and i can tell you're pretty dam good at your php, the only thing is that you're too good for me and alot of it is confusing me when i'm trying to debug lol. i've extracted your pagenation part and i'm currently trying to figure out why the next page button isn't showing up. But i have no clue becuase your abilities are far beyond mine.

Hope that doesn't sound like i'm having a dig at you, because i'm not (i'm very happy that you helped). I'm just unable to figure out your code because i'm such an amature.

cheers,
Alastair

---

### Post by Hellkeepa on 2010-01-27
HELLo!

Hehe, no worries; No "dig" percieved. :-)
Also, if there's something that you don't quite understand, and the manual isn't helping, don't be shy in asking for help. If not me, then I'm sure there are lots of people here that's willing to help you with it.

When it comes to your problem, I've spotted an issue when looking over that code again. Add a "var_dump ($result)" right before the IF-test, and you'll see it yourself. ;-)

Happy codin'!

---


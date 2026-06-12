---
title: "Programming Help: PHP &amp; MySQL"
date: 2006-10-01
forum: Programming Talk
---

### Post by Brahman on 2006-10-01
I am using this tutorial to create my own forum software. The tutorial is: [http://www.tutorialized.com/tutorial/Discussion-Forums-with-PHP/609](http://www.tutorialized.com/tutorial/Discussion-Forums-with-PHP/609)

I did everything. Uploaded the files, created the tables using phpMyAdmin. 

But I get this error when I try to access the board: 

```
 

Parse error: syntax error, unexpected T_STRING, expecting T_VARIABLE or '$' in /home2/linuxmf/public_html/board/functions.php3 on line 105


``` 

Here's the functions.php3 code: 

```
 

<?php

mysql_connect("localhost","linuxmf_board1","012089");
mysql_select_db("linuxmf_board");

function showheader($title) {
?>
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">
<HTML>
<HEAD>
<TITLE> <?php echo $title ?> </TITLE>
</HEAD>

<BODY BGCOLOR="#FFFFFF">
<?php
}

function showfooter() {
?>
</BODY>
</HTML>
<?php
}

function viewpost ($topicID) { 

$topic_query = mysql_query("SELECT TopicName FROM topics WHERE (ID=$topicID)");
$topic = mysql_fetch_array($topic_query);
?>
<TABLE BORDER=0 WIDTH=100% CELLSPACING=3 CELLPADDING=5>
	<TR>
		<TD>
		<FONT COLOR="#000000" FACE="Arial,Verdana,Helvetica" size=-1>
		<b>Topic: </b>
		<BR><?php echo $topic['TopicName'] ?>
		<P>
		<a href="index.php3"><FONT COLOR="#000000">Return Back to Topic Listing</a>
		<P>
		<a href="add-post.php3?topicID=<?php echo $topicID ?>"><FONT COLOR="#000000">Make a Post</a>
		</TD>
	</TR>
</TABLE>
<P>
<TABLE BORDER=0 CELLSPACING=0 CELLPADDING=0 WIDTH=100%>
	<TR VALIGN=TOP ALIGN=LEFT>
		<TD WIDTH=100%>
			<TABLE BORDER=0 BGCOLOR="#000000" CELLSPACING=1 CELLPADDING=1 WIDTH=100%>
				<TR>
					<TD COLSPAN=3 BGCOLOR="#C0C0C0" WIDTH=100%>
						<TABLE BORDER=0 CELLSPACING=0 CELLPADDING=5 WIDTH=100%>
							<TR>
								<TD>
								<P><B><FONT COLOR="#000000" FACE="Trebuchet MS,Arial,Helvetica">Topic Posts</FONT></B>
								</TD>
							</TR>
						</TABLE>
					</TD>
				</TR>
<?php
$post_query = mysql_query("SELECT * FROM posts WHERE (TopicID='$topicID') ORDER BY TimeStamp");
	while ($post = mysql_fetch_array($post_query)) {
?>
	<TR>
	<TD WIDTH=82% BGCOLOR="#FFFFFF" HEIGHT=28 VALIGN=TOP>
		<TABLE BORDER=0 CELLSPACING=0 CELLPADDING=5 WIDTH=100%>
			<TR>
				<TD>
				<P><FONT SIZE="-1" FACE="Trebuchet MS,Arial,Helvetica"><?php echo $post['Post'] ?></FONT> 
				</TD>
			</TR>
		</TABLE>
	</TD>
	<TD WIDTH=18% BGCOLOR="#C0C0C0" VALIGN=TOP>
		<TABLE BORDER=0 CELLSPACING=0 CELLPADDING=5 WIDTH=100% >
			<TR>
				<TD>
				<P ALIGN=center><FONT SIZE="-1" FACE="Trebuchet MS,Arial,Helvetica" color=#000000>Posted By: <A HREF="mailto:<?php echo $post['Email'] ?>"> <FONT COLOR=#000000><?php echo $post['Name'] ?></A>
				<BR><BR>
				<A HREF="edit-post.php3?postID=<?php echo $post['ID'] ?>"><FONT COLOR=#000000>Edit Your Post</FONT>
				<BR><BR>
				<A HREF="delete-post.php3?postID=<?php echo $post['ID'] ?>"><FONT COLOR=#000000>Delete Your Post</FONT>
				</TD>
			</TR>
		</TABLE>
	</TD>
</TR>
<?php
} 
if (mysql_num_rows($post_query) < 1) {
?>
<TR height=300>
	<TD WIDTH=100% BGCOLOR="#FFFFFF" HEIGHT=28 VALIGN=TOP colspan=2>
	<CENTER><FONT SIZE="-1" FACE="Trebuchet MS,Arial,Helvetica">
	<BR><B>There Are No Posts Currently For This Topic</B><BR><BR></CENTER>
	</TD>
</TR>
<?php } ?>
</TABLE>
</TD></TR>
</TABLE>
<?php
}

function addpost () {
global hj3lsm/bf[@,$email,$name,$post,$topicID;
	$timestamp = time();
	$new_password = addslashes($password); 	$new_email = addslashes($email);
	$new_name = addslashes($name);
	$new_post = addslashes(nl2br(htmlspecialchars($post)));
	$insert = mysql_query("INSERT INTO posts VALUES ('NULL','$topicID','$new_name','$new_email','$new_password','$timestamp','$new_post')");
	if (mysql_error() != "") {
		showheader("MySQL Error ".mysql_error());
		?>
		<br><p><center><b>There was a MySQL Error -- <?php echo mysql_error() ?></b></center></p>
		<?php
		showfooter();
		exit;
	}
}

function editpost () {
global $postID,$post;
	$new_post = addslashes(nl2br(htmlspecialchars($post)));
	$insert = mysql_query("UPDATE posts SET post='$new_post' WHERE (ID='$postID')");
	if (mysql_error() != "") {
		showheader("MySQL Error ".mysql_error());
		?>
		<br><p><center><b><FONT SIZE="-1" FACE="Trebuchet MS,Arial,Helvetica">There was a MySQL Error -- <?php echo mysql_error() ?></b></center></p>
		<?php
		showfooter();
		exit;
	}
}

function deletepost () {
global $postID;
$post_query = mysql_query("DELETE FROM posts WHERE (ID='$postID')");
	if (mysql_error() != "") {
		showheader("MySQL Error ".mysql_error());
		?>
		<br><p><center><b><FONT SIZE="-1" FACE="Trebuchet MS,Arial,Helvetica">There was a MySQL Error -- <?php echo mysql_error() ?></b></center></p>
		<?php
		showfooter();
		exit;
	}
}

function addtopic () {
global $topicname;
$new_topicname = addslashes($topicname);
$topic_query = mysql_query("INSERT INTO topics VALUES ('NULL','$new_topicname')");
	if (mysql_error() != "") {
		showheader("MySQL Error ".mysql_error());
		?>
		<br><p><center><b><FONT SIZE="-1" FACE="Trebuchet MS,Arial,Helvetica">There was a MySQL Error -- <?php echo mysql_error() ?></b></center></p>
		<?php
		showfooter();
		exit;
	}
	return mysql_insert_id();
}


?>


``` 

Could someone help me?

---

### Post by kidders on 2006-10-01
That's just a parse error. Line 105 appears to be ...

```
global hj3lsm/bf[@,$email,$name,$post,$topicID;
```

... which doesn't really make any sense. What's supposed to come before "$email"?

---

### Post by Brahman on 2006-10-01
Hmm...the tutorial says something about: $topicID 

maybe thats it...

---

### Post by reynoldlariza on 2006-10-08
what are you trying to do with this line?
```

global hj3lsm/bf[@,$email,$name,$post,$topicID; 

```

it doesn't make any sense at all

what i saw from the snippet is like this
```
global $password,$email,$name,$post,$topicID;
```

It's very different.


[COLOR="Red"]hj3lsm[/COLOR] is an invalid variable name.
The division symbol '[COLOR="Red"]/[/COLOR]' is valid, however using it this way is not.

Last,

[COLOR="Red"]bf[@,$email,$name,$post,$topicID; [/COLOR]
is also not valid. Also, '[COLOR="Red"]@[/COLOR]' which variable you intend to refer to? you didn't specify a name.

Notice too that you're trying to create an associative array but there's no closing bracket at all.

---


---
title: "PHP MYSQL noobie with no idea as to error"
date: 2009-11-26
forum: Programming Talk
---

### Post by gillespiea on 2009-11-26
Hi folks. I've been working on, and learning php scripting to make a website for *breathes in* my brothers mrs work...
because they need a new one.

ANYWAY! i've been coding in HTML for about 10 years but only just started to learn PHP and mysql. I got a book (sams teach yourself PHP, MYSQL and APACHE) and went from there. So far i've had a few problems and managed to work through it, and i've learned alot. But after making all my own database (and having all pages bar this one working) i cant get my "Edit propery" page to work.

Here is my list of tables in my mysql database called "forlease"

ID
OWNER
TEXT
CREATE_TIME
ADDRESS
PRICE
IMG
TITLE
PAYMENT
LOCATION
BRIEF

Here is my edit page "editforlease.php"
[php]<?php

include("lcoincludefs.php");

doDB();





//verify the topic exists

$verify_topic_sql = "SELECT ID, TEXT, TITLE, OWNER, ADDRESS, PRICE, PAYMENT, LOCATION, IMG, BRIEF FROM forlease WHERE ID = '".$_GET["ID"]."'";

$verify_topic_res =  mysqli_query($mysqli, $verify_topic_sql) or die(mysqli_error($mysqli));



if (mysqli_num_rows($verify_topic_res) < 1) {

	//this topic does not exist

	$display_block = "<p><em>You have selected an invalid property.<br/>

	Please <a href=\"userlogin.php\">try again</a>.</em></p>";

} else {

	//get the topic title

	while ($topic_info = mysqli_fetch_array($verify_topic_res)) {

		$TITLE = stripslashes($topic_info['TITLE']);



	}



	//gather the posts

	$get_posts_sql = "SELECT TITLE, ADDRESS, ID, TEXT, PRICE, PAYMENT, IMG, OWNER, LOCATION, PAYMENT, BRIEF FROM forlease WHERE ID = '".$_GET["ID"]."' ";

	$get_posts_res = mysqli_query($mysqli, $get_posts_sql) or die(mysqli_error($mysqli));



	//create the display string

	$display_block = "

	<p>Editing the news post <strong>".$TITLE."</strong> topic:</p>
<p>topic id: ".$ID."</p>

	<table width=\"100%\" cellpadding=\"3\" cellspacing=\"1\" border=\"0\">

	
";



	while ($posts_info = mysqli_fetch_array($get_posts_res)) {

		$TITLE = nl2br(stripslashes($posts_info['TITLE']));

		$TEXT = stripslashes($posts_info['TEXT']);
		$OWNER = stripslashes($posts_info['OWNER']);
		$ADDRESS = stripslashes($posts_info['ADDRESS']);
		$PAYMENT = stripslashes($posts_info['PAYMENT']);
		$IMG = stripslashes($posts_info['IMG']);
		$BRIEF = stripslashes($posts_info['BRIEF']);
		$PRICE = stripslashes($posts_info['PRICE']);



		//add to display

	 	$display_block .= "
<td width=\"160\"><p><h3>Edit a Lease Property</h3>
<form method=\"post\" action=\"do_editlease.php\">

    <p>Property Title:<br/>

     <textarea name=\"TITLE\" rows\"8\" cols=\"40\" wrap=\"virtual\">".$TITLE."</textarea></p>

    </p>

    <p>

  <label>Cost:<br>&pound;

  <input type=\"text\" name=\"PRICE\" id=\"PRICE\">

  </label>
<select name=\"PAYMENT\">
<option value=\"Per month\">Per Month</option>
<option value=\"Per calender month\">Per calender Month</option>
<option value=\"Total\">Total</option>
<option value=\"Offers over\">Offers over</option>
</select>

</p>
<p>Location:
<select name=\"LOCATION\">
<option value=\"Aberdeen city\">Aberdeen city</option>
<option value=\"Aberdeen Suburbs\">Aberdeen Suburbs</option>
<option value=\"Surrounding Areas\">Surrounding Areas</option>
</select></p>

<p>Property Address:<br>

      <textarea name=\"TITLE\" rows\"8\" cols=\"40\" wrap=\"virtual\">".$ADDRESS."</textarea></p>

</p>
<p>Property Breif:<br>

      <textarea name=\"BRIEF\" rows\"8\" cols=\"40\" wrap=\"virtual\">".$BRIEF."</textarea></p>

</p>

<p>Property Main Text:<br/>

<textarea name=\"TEXT\" rows\"8\" cols=\"40\" wrap=\"virtual\">".$TEXT."</textarea></p>

</p>

<p>Add an Image: <br>

    <input type=\"file\" name=\"IMG\" id=\"IMG\" value=\"Submit\">

</p>

<p><input type=\"submit\" name=\"submit\" value=\"Edit Property\">

</p>

</form>

</p>

</td>"
;

	}



	//free results

	mysqli_free_result($get_posts_res);

	mysqli_free_result($verify_topic_res);



	//close connection to MySQL

	mysqli_close($mysqli);



	//close up the table

	$display_block .= "</table>";

}

?>

<html>

<head>

<title>Laurie &amp; Co</title>

<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">

<link rel="stylesheet" type="text/css" href="styles/style.css">

</head>



<body>

<table width="900" height="727" cellpadding="5" cellspacing="0">

  <tr> 

    <td height="41" colspan="4"><img src="styles/images/0002.gif" width="900" height="150"></td>

  </tr>

  <tr> 

    <td width="21" height="234"></td>

    <td width="160" height="459" valign="top"><img src="styles/images/0003.gif" alt="navigation" width="160" border="0" usemap="#Map"> 

      <map name="Map">

        <area shape="rect" coords="13,13,90,42" href="index.html">

        <area shape="rect" coords="13,46,138,71" href="legal.html">

        <area shape="rect" coords="13,75,105,99" href="property.html">

        <area shape="rect" coords="11,105,112,133" href="firm.html">

        <area shape="rect" coords="14,137,94,164" href="people.html">

        <area shape="rect" coords="14,169,115,195" href="contact.html">

        <area shape="rect" coords="14,196,94,221" href="links.html" alt="navigation">

      </map> <a href="fynh.html"><img src="styles/images/0004.gif" width="160" height="50" border="0"></a><br> 

      <a href="syp.html"><img src="styles/images/0014.gif" width="160" height="50" border="0"></a><br> 

      <a href="byp.html"><img src="styles/images/0024.gif" width="160" height="50" border="0"></a><br> 

      <a href="rl.html"><img src="styles/images/0034.gif" width="160" height="50" border="0"></a> 

    </td>

    <td width="14" colspan="2" rowspan="2"><div align="center">

<table width="639" border="0">

          <tr> 

            <td width="616">&nbsp;</td>

          </tr>

          <tr> 

            <td><h3 align="justify"><? echo $display_block; ?></h3>

              <h3 align="justify">&nbsp;</h3>

              </td>

          </tr>

        </table>

      </div>

      </td>

  </tr>

  <tr> 

    <td height="160">&nbsp;</td>

    <td width="160">&nbsp;</td>

  </tr>

  <tr> 

    <td height="85" colspan="4"><div align="center"><img src="styles/images/0005.gif" width="900" height="75"></div></td>

  </tr>

</table>

</body>

</html>

[/php]

And here is my do_editlease.php page:

[php]<?php

include("lcoincludefs.php");

doDB();



//check for required fields from the form

if ((!$_POST["TITLE"]) || (!$_POST["TEXT"]) || (!$_POST["ID"]) || (!$_POST["ADDRESS"]) || (!$_POST["PRICE"]) || (!$_POST["PAYMENT"]) || (!$_POST["LOCATION"]) || (!$_POST["IMG"]) || (!$_POST["BRIEF"])) {

	header("Location: editforlease.php");

	exit;

}



//create and issue the first query

$add_topic_sql = "REPLACE INTO forlease (ID, TEXT, TITLE, ADDRESS, PRICE, PAYMENT, LOCATION, IMG, BRIEF) VALUES ('".$_POST["ID"]."','".$_POST["TEXT"]."','".$_POST["TITLE"]."','".$_POST["ADDRESS"]."','".$_POST["PRICE"]."','".$_POST["PAYMENT"]."','".$_POST["LOCATION"]."','".$_POST["IMG"]."','".$_POST["BRIEF"]."')";

$add_topic_res = mysqli_query($mysqli, $add_topic_sql) or die(mysqli_error($mysqli));



//get the id of the last query

$topic_id = mysqli_insert_id($mysqli);



//close connection to MySQL

mysqli_close($mysqli);



//create nice message for user

$display_block = "<P>The <strong>".$_POST["TITLE"]."</strong> topic has been created.</p>";

?>

<html>

<head>

<title>Laurie &amp; Co</title>

<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">

<link rel="stylesheet" type="text/css" href="styles/style.css">

</head>



<body>

<table width="900" height="727" cellpadding="5" cellspacing="0">

  <tr> 

    <td height="41" colspan="4"><img src="styles/images/0002.gif" width="900" height="150"></td>

  </tr>

  <tr> 

    <td width="21" height="234"></td>

    <td width="160" height="459" valign="top"><img src="styles/images/0003.gif" alt="navigation" width="160" border="0" usemap="#Map"> 

      <map name="Map">

        <area shape="rect" coords="13,13,90,42" href="index.html">

        <area shape="rect" coords="13,46,138,71" href="legal.html">

        <area shape="rect" coords="13,75,105,99" href="property.html">

        <area shape="rect" coords="11,105,112,133" href="firm.html">

        <area shape="rect" coords="14,137,94,164" href="people.html">

        <area shape="rect" coords="14,169,115,195" href="contact.html">

        <area shape="rect" coords="14,196,94,221" href="links.html" alt="navigation">

      </map> <a href="fynh.html"><img src="styles/images/0004.gif" width="160" height="50" border="0"></a><br> 

      <a href="syp.html"><img src="styles/images/0014.gif" width="160" height="50" border="0"></a><br> 

      <a href="byp.html"><img src="styles/images/0024.gif" width="160" height="50" border="0"></a><br> 

      <a href="rl.html"><img src="styles/images/0034.gif" width="160" height="50" border="0"></a> 

    </td>

    <td width="14" colspan="2" rowspan="2"><div align="center">

<table width="639" border="0">

          <tr> 

            <td width="616">&nbsp;</td>

          </tr>

          <tr> 

            <td><h3 align="justify">&nbsp;</h3>

              <h3 align="justify">&nbsp;</h3>

              </td>

          </tr>

        </table>

      </div>

      </td>

  </tr>

  <tr> 

    <td height="160"><?php echo $display_block; ?></td>

    <td width="160">&nbsp;</td>

  </tr>

  <tr> 

    <td height="85" colspan="4"><div align="center"><img src="styles/images/0005.gif" width="900" height="75"></div></td>

  </tr>

</table>

</body>

</html>
[/php]

Anyone got any ideas as to why i just get returned to editforlease.php?

---

### Post by CyberJack on 2009-11-26
Just scanning your code I see that you have 2 fields named TITLE.
One of them contains the address. And I can't find the ID field in your form.

The code will redirect you because ID and ADDRESS are required and missing after the submit.

---

### Post by gillespiea on 2009-11-26
which page which line sorry?

---

### Post by gillespiea on 2009-11-26
FOUND IT!
Thanks so much! cant believe it was such a small silly error...if i had a pound for every time that happend lol.

Thanks again.

---

### Post by myrtle1908 on 2009-11-26
Just a tip.  Instead of all the escaping eg.

[PHP]
$display_block = "

    <p>Editing the news post <strong>".$TITLE."</strong> topic:</p>
<p>topic id: ".$ID."</p>

    <table width=\"100%\" cellpadding=\"3\" cellspacing=\"1\" border=\"0\">

    
"; [/PHP]

You can use a heredoc (or I suppose you could have used single quotes).

[PHP]$display_block = <<<EOF
<p>Editing the news post <strong>"$TITLE"</strong> topic:</p>
<p>topic id: "$ID"</p>
    <table width="100%" cellpadding="3" cellspacing="1" border="0">
EOF;[/PHP]

Note: EOF is just used as an example, it could be any word. The important rule to remember is that you finish a heredoc using the same word you started, and it must be by itself on the line (hard-left)

Further reading: [http://www.php.net/manual/en/language.types.string.php#language.types.string.syntax.heredoc](http://www.php.net/manual/en/language.types.string.php#language.types.string.syntax.heredoc)

---


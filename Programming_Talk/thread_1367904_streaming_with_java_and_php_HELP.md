---
title: "streaming with java and php HELP"
date: 2009-12-30
forum: Programming Talk
---

### Post by Dex14 on 2009-12-30
Hello everyone,

I have a question that i cant find the solution to, I tried googling it but havent found anything, mainly because i dont know what am doing or how to word the problem.

Ok.

I have a website on my Xubuntu LAMP server that i want to stream flash videos off. (the flash videos are stored on the server)
I want there to be a listing of all the movies/videos on a webpage, and when a movie link is clicked it would goto another page that has an embeded flash player that will play the movie.

I already have a theory of how to do this but i dont know how to implement it.

What i think should be done is this: create a MySQL database with a table that lists the movie, the file name and the folder that the movie exists in.

-------------------------------------
|ID | MovieName | FileName | Location|
-------------------------------------
|1  |movie      |movie.flv |media/   |      (table in database)
-------------------------------------

if that table doesnt work out:
ID = 1
MovieName = movie
FileName = movie.flv
Location = media/

Then,
create a webpage that has the embeded flash player on it
Example of the flash player on the webpage:
> <p id='preview'>The player will show in this paragraph</p>
<script type='text/javascript' src='swfobject.js'></script> 
<script type='text/javascript'> 
var s1 = new SWFObject('player.swf','player','400','300','9'); 
s1.addParam('allowfullscreen','true'); 
s1.addParam('allowscriptaccess','always'); 
s1.addParam('flashvars','file=[COLOR="Lime"]media/[/COLOR][COLOR="Red"]movie.flv'[/COLOR]); 
s1.write('preview'); 
</script>

where the tex is coloured indicates are to be substituted for the movies in the data base, the text here will probably be made into variables

Are you lost yet?

so, the person presses the link to the movie [COLOR="Yellow"]-->[/COLOR] php script requests the Location that the movie is at and the FileName from the table in the database [COLOR="yellow"]-->[/COLOR] requested information is inserted into the variables (see above) [COLOR="yellow"]-->[/COLOR] movie is played.

That is it. 

I dont know how to go about this.
any answers would be muchly apreciated. From help with the PHP sript to putting the php variavles into the javascript.

Thanks in advance,
Declan

---

### Post by kahumba on 2009-12-30
Are you confusing Java with JavaScript? (the title says java, the contents mention javascript..)

---

### Post by Dex14 on 2009-12-30
no im not, that script is the part of the flash player "JW FLV"
that goes into the html on the webpage. the script is 'putting' the plash player onto the page. it tells what movie/video to play and where to find it.

---

### Post by Dex14 on 2009-12-30
ohh yeah sorry

---

### Post by kahumba on 2009-12-30
Before anything:
- afaik a "normal" server & database can't fetch video/flash data/bytes from a given time position, it's a pretty complicated solution that requires knowledge of the codecs etc etc, thus, the user won't be able to "scroll" further without having to download the whole movie (from the start till the scroll position), which on your localhost you might not notice since the testing server and the browser would be on same computer, but which would be a pain for normal web users when putting your website online. The solution  to this is getting a (pretty expensive) media server to do the job, maybe there are better/cheaper solutions, but I haven't heard of them. This alone could discourage you from going further with your project.
- are you planning to put the videos (the raw bytes) into the mysql database or into filesystem folders? I haven't noticed in your "table" a field for the raw data.

---

### Post by Hellkeepa on 2009-12-30
HELLo!

The table seems sound, and should work well. Your theory of how this script should work is simple and concise, just like it should be, and correct to boot. ;-) It's just a bit shy on the technical details, so let me help you out a bit with those.

[list=1][*]First you need to have the script retrieve and validate the ID of the movie. Since we're working on integer IDs, "intval ($_GET['id'])" is adequate validation.
[*]Then you need to check the DB if the given ID is valid, do this by pulling out the data from the row with said ID.
[*]If row returns content:
[list=1][*]Build the path to the file, with the data returned, and store it in a variable. 
[php]$Path = $Row['Location'].$Row['FileName'];[/php]
[*]Add the code from above to the output, using the following to insert the path at the correct place. (And to make sure it there are no errors with HTML-entities or the URL.)
[php]$Output .= sprintf ($PlayerTemplate, htmlspecialchars (rawurlencode ($Path)));[/php]
[/list]
[*]If the ID is not valid:
[list=1][*]Add an error message to the output.[/list]
[*]Then retrieve all the rows from the database, fetching the ID and name of all movies.
[*]Loop through the results, and build up a list of all the movies. Use this to make the links:
[php]$Output .= <<<OutHTML
    <a href="?id={$Row['ID']}">{$Row['MovieName']}</a>
OutHTML;[/php]
[*]Print all of the output to the browser.[/list]
Also, remember that PHP is executed on the server, before any content is sent to the browser. That means, that you can use PHP to generate both HTML and JavaScript. Heck, you can even use it in your CSS scripts if you want to. ;-)

*Edit, added:*
I think you might need to read his post again, **kahumba**, as I don't see any mention about being able to jump to specific times in the stream. Also, I found it quite obvious that he's stored the files on disk, in a sub-folder to the HTTP root.

Happy codin'!

---

### Post by Dex14 on 2009-12-30
oh, i didnt specify that the server isnt open to the internet, it is only for use at home.
indeed the database only stores the filename and location, these feilds will get inserted into the javascript and then the script does the rest.
I have a flash player called JW FLV which plays the movie that gets emmbeded into the webpage.
does this help at all.

---

### Post by Dex14 on 2009-12-30
Thank you both kuhumba and hellkeepa for your insights.
im working on it now, hoping to be finished tonight.
thanks again.

---

### Post by kahumba on 2009-12-30
In this case I wouldn't use a database at all.
The "movie name" would be the "file name" (without the extension obviously) which would also be the id since there can't be 2 files with same name/path + a bit of house keeping in case of using relative paths.
Accessing the files directly using PHP File I/O would be slightly faster (and maybe easier) than doing it through the typical php->mysql->filesystem->mysql->php routine.
But since you're doing it for yourself it really doesn't matter much.

---

### Post by Dex14 on 2009-12-30
ok hellkeepa i tried and failed
 
> **Hellkeepa said:**
> 
Then you need to check the DB if the given ID is valid, do this by pulling out the data from the row with said ID.

 what do i do? script-wise. or rather how do you pull out the data.
 
this is what i have so far
 
[PHP]
$dbcnx = @mysql_connect(<192.168.1.6>, <root>, <######>);
if (!$dbcnx) {
echo( "<P>Unable to connect to the " .
"database server at this time.</P>" );
exit();
}
mysql_select_db("movies") or die(mysql_error());
intval ($_GET['id'])
[/PHP]
 
After that i get lost. i should have told you that im not very good at PHP/SQL yet.
 
can you help 
or
can you point me in the direction of some recources (websites preferably).
 
 
declan

---

### Post by Hellkeepa on 2009-12-30
HELLo!

You need to make an SQL query, that fetches the rows you want from the table. Use "[mysql_query ()](http://no.php.net/mysql_query)" to execute said query. Then you can use "mysql_num_rows ()", for instance, to check how many rows the query returned. (Should be one row, if you wrote the query correctly.)
If you follow that link, it'll take you to the PHP manual. The best source there is on the different PHP functions, I recommend reading through it.

To look up specific functions in the PHP manual, just use the following URL pattern:
php.net/<function name>

PS: You need to store the result of the "intval ()" function, in order to be able to use it. Look it up in the manual. ;-)

PPS: Remove the less than & bigger than signs from the first line in your code. They're just used to signal that the text within them is a placeholder text. You need to use quotation marks instead, to tell PHP that the data is text.

Happy codin'!

---

### Post by Dex14 on 2009-12-30
ok thank you hellkeepa,
 
I'll definately read through the manual. I probably wont write back till i've finished this little project. thank you for you for your contributions.
 
declan

---

### Post by Dex14 on 2010-01-04
well this is what i have come up with, but it still needs fixing.:(
 
[php]$dbcnx = @mysql_connect(<ipaddress>, <user>, <password>);
  if (!$dbcnx) {
   echo( "<P>Unable to connect to the " .
    "database server at this time.</P>" );
   exit();
  }
                                mysql_select_db("movies") or die(mysql_error()); 
  $result = mysql_query("SELECT id FROM movies WHERE id = 1");  
  $id=intval ($_GET['id']):
  $num_rows = mysql_num_rows($result);
   if ($num_rows = mysql_num_rows($result) {
    $Path = $Row['Location'].$Row['FileName'];  
    $Output .= sprintf ($PlayerTemplate, htmlspecialchars (rawurlencode ($Path)));  
   } else {
      echo(<P>cant retrive records</P>):
  $Output .= <<<OutHTML 
      <a href="?id={$Row['ID']}">{$Row['MovieName']}</a> 
  OutHTML; [/php]
 
:confused: like i said im not very good a PHP/MySQL yet, but im trying

---

### Post by Hellkeepa on 2010-01-04
HELLo!

First off, you need to use correct indenting. That way the script gets a whole lot easier to read, which again makes it a lot easier to spot certain mistakes you've made. After fixing the indenting in the script you pasted above, I was presented with the following:
[php]$dbcnx = @mysql_connect(DB_HOST, DB_USER, DB_PASSWORD);
if (!$dbcnx) {
	echo ("<P>Unable to connect to the database server at this time.</P>");
	exit ();
}

mysql_select_db ("movies") or die (mysql_error ());
$result = mysql_query ("SELECT id FROM movies WHERE id = 1");  
$id=intval ($_GET['id']):

$num_rows = mysql_num_rows ($result);
if ($num_rows = mysql_num_rows($result) {
	$Path = $Row['Location'] . $Row['FileName'];
	$Output .= sprintf ($PlayerTemplate, htmlspecialchars (rawurlencode ($Path)));
} else {
      echo(<P>cant retrive records</P>):
      $Output .= <<<OutHTML 
      <a href="?id={$Row['ID']}">{$Row['MovieName']}</a> 
OutHTML;[/php]
A result which shows us that we have some logical issues in this code. Also, my editor complained about syntax errors as well. More specifically in lines 10, 13, and 17 (2 errors in that last line). Lastly, note that the else-block is not closed yet.

The above errors should be easy to pick out and correct, as all syntax errors are. The logical errors, however, is slightly different as there is no set rule for how to write the logic; It all comes from you, and your understanding of what the code should do.
I've made a list, with a little explanation of what's wrong.
[list=1][*]Lines 12 & 13:
You've asked the script to fetch an ID from the URL the user sent, but you haven't done anything with it. What you have done, is to use a fixed ID in your MySQL-query, to fetch out the rows from the DB. Now, since you're setting the $ID variable *after* creating (and running, mind you) the SQL query, it has no way of knowing about the ID the user requested.
[*]Line 12 & 13:
Here you're fetching the number of rows returned, twice. Both times saving the result into the same variable. Completely unnecessary, once is enough. Don't even need to save the result into a variable, if you don't have plans to use said result later on.
[*]Lines 14 & 15:
Here you're clearly trying to add the data from the database into some variables, but with two major errors. First one is that you have not fetched the returned content from the resource link, the "$Row" variable simply does not exist.
Second one is that you are not using a loop, to fetch all of the content retrieved. So even if you had fetched the content correctly, you'd still only get the first row added to the output.
[*]Line 15:
$PlayerTemplate is not defined, which means that "spritf()" does not have anything to work with. End result is nothing gets added to the output.
[*]Line 18:
You have not closed the else-block properly here, meaning that this line (and everything after it) will only be executed if "mysql_num_rows()" returns 0. In other words, only if no records are found in the database. Considering how lines 19-20 reads, I highly doubt this was the intention.
[*]Lines 19-20:
Here you're lacking a lot of code. What that piece of code should have done, is to be a part of the code that created a list over all the movies in the DB. What you have here, is just the inner part of the loop that adds the retrieved data to the output.[/list]
In short: You've skipped point 5 and 7 on my list completely, added point 6 as point 4.2, reversed the order of point 1 and 2, skipped most of the code in point 3.2, and the loop in point 6.

To be fair, I should probably have mentioned that you should add a loop in point 3 as well.

However, I recommend you find yourself a MySQL & PHP tutorial, and follow it first. That way you'll learn about the order of things, and what's necessary (and why) to do when working with databases.

Happy codin'!

---

### Post by theDaveTheRave on 2010-01-05
I'm going to add in a quick word to this as it seems like a good topic.

My solution would have been similar to that being suggested by hellkeepa, but with a few minor changes.

so here are my suggestions.

when you send your mysql query, get all the data from the table, At least that way you can then "adjust" what you retrieve later on, as required.

the table structure is to look like the following.
> 
|ID | MovieName | FileName | Location|


to get the lot use this mysql code, assuming the OP is using a table called 'movies', which he seems to be.

[php]
$result = mysql_query("select * from movies");
[/php]

The advantage here is that you will know instantly if you are collecting all the rows of data from your table by calling the get_rows() 

Now personally I would wrap the whole of the result up to be displayed in an html table, or maybe a drop down list of some form? But first you want to be sure you are collecting the data from the table, you can tweak away at it later on.

also make use of the mysql_fetch_row() function, to get each of the data fields, one at a time (the fields are zero indexed).

Once you get your table correct you will then be albe to autmatically add in a link to a new page with the embeded movie in it. Or maybe even open it inside a "frame" on the current page.

Good luck with this, is should be a nice little project to get to grips with php and mysql.

David

---

### Post by Hellkeepa on 2010-01-05
HELLo!

I would recommend against fetching all columns when not needed. Not only is this a waste of memory, but it'll also take longer to retrieve all the data from the DB server. Granted, on such a small script the extra resource and time used is not noticeable, but it's still good form to only pick what you need. Makes the intention of the code easier to understand too, and forces the developer to be more aware over what he's doing. (Only a good thing, if you ask me.)
Good coding practises are best learned at once, instead of having to unlearn bad ones first.

Also, I would recommend using "mysql_fetch_array ()" instead of "_row ()", reasons are explained in the PHP manual.

Happy codin'!

---

### Post by theDaveTheRave on 2010-01-06
hellkeepa

> 
I would recommend against fetching all columns when not needed


I was only recomending this as a first port of call, so as the OP can quickly and easily check that the data was being gathered correctly.

Otherwise I agree with your comments.

My development procedure normally works by the following.
- get the big picture, just to be sure you are doing it right.
- now work to get the stuff you need, and drop the rest.

you may try to go straight into just getting the name of the video you want to collect. But if you put in a typo and get no results you may spend an age trying to figure out why.

A 'quick and dirty' select statement will at least tell you that the data you are after exists. So you know that there must be a problem in your code.

It's then not a big problem to comment out the "dirty statement" but leave it in place in case you need it later on for troubleshooting.

David

---

### Post by Dex14 on 2010-01-26
this is what ive done it all works exept one thing, when i try to put the php variable into the object it doesnt work. i dont know what to do.
[PHP]<?php

$thisfile = $_SERVER['PHP_SELF'];

$dbcnx = @mysql_connect("localhost", "user", "pass");
  if (!$dbcnx) {
  echo( "<P>Unable to connect to the " .
  "database server at this time.</P>" );
  exit();
  }
mysql_select_db("movies") or die("<p>cant connect to database at this time</p>"); 
$sql="SELECT id, FileName, MovieName, MovieLocation FROM movies";
$result=mysql_query($sql);

$options="";

while ($row=mysql_fetch_array($result)) {

    $id=$row["id"];
    $moviename=$row["MovieName"];
    $options.="<OPTION VALUE=\"$id\">".$moviename.'</option>';  
}

if ($_POST['Submit'] == 'Submit') {
  $query1="SELECT Location, Filename FROM movies WHERE ID = $id and MovieName = $moviename";
  $Path = $Row['Location'].$Row['FileName'];
}else{
  error_log(mysql_error());
  $error_msg = '<p>something wemt wrong</p>';
}

?>
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
    <title>Movies</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="description" content="" />
    <meta name="keywords" content="" />
    <link rel="stylesheet" type="text/css" href="style.css" />
    <link rel="stylesheet" type="text/css" href="blue.css" />
    <script type='text/javascript' src='swfobject.js'></script>
</head>

<body>
<div id="container">
    <div id="menu">
        <span class="logo1">Ser</span><span class="logo2">ver</span>
        <ul>
            <li><a href="index.html">home</a></li>
            <li><a href="games.html">games</a></li>
            <li><a href="pictures.html">pictures</a></li>
            <li><a href="downloads.html">downloads</a></li>
            <li><a href="movies.php">movies</a></li>
        </ul>
        
    </div>
    <div id="content">
    <h1>Movies</h1>
    

<object classid="clsid:d27cdb6e-ae6d-11cf-96b8-444553540000" codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/ swflash.cab#version=9,0,0,0" width="640" height="375" id="FlvPlayer" align="middle">
<param name="allowScriptAccess" value="sameDomain" />
<param name="allowFullScreen" value="true" />
<param name="movie" value="http://flvplayer.com/free-flv-player/FlvPlayer.swf" />
<param name="quality" value="high" />
<param name="bgcolor" value="FFFFFF" />
<param name="FlashVars" value="flvpFolderLocation=http://flvplayer.com/free-flv-player/flvplayer/&flvpVideoSource=<?php echo $Path ?>&flvpWidth=640&flvpHeight=375&flvpInitVolume=50&flvpTurnOnCorners=true&flvpBgColor=FFFFFF"
<embed src="http://flvplayer.com/free-flv-player/FlvPlayer.swf" flashvars="flvpFolderLocation=http://flvplayer.com/free-flv-player/flvplayer/&flvpVideoSource=<?php echo $Path ?>&flvpWidth=640&flvpHeight=375&flvpInitVolume=50&flvpTurnOnCorners=true&flvpBgColor=FFFFFF" quality="high" bgcolor="FFFFFF" width="640" height="375" name="FlvPlayer" align="middle" allowScriptAccess="sameDomain" allowFullScreen="true" type="application/x-shockwave-flash" pluginspage="http://www.adobe.com/go/getflashplayer" />
</object>

            

    <FORM METHOD="get" ACTION="<?php echo $thisfile ?>">
    <SELECT NAME="row[]" size=5 SINGLE>
    <?php echo $options ?>
    </SELECT>
    <BR><BR>
    <INPUT TYPE="submit" NAME="submit" VALUE="Submit">
    </FORM>
    </div>
</div>
<div id="footer">Design: <a href="http://www.dannisbet.com/">DanNisbet.com</a> | &copy; 2008 YourSite.com</div>
</body>
</html>
[/PHP]

---

### Post by Hellkeepa on 2010-01-27
HELLo!

Cleaned your code up a bit, and added some comments.
[http://pastebin.com/f304ac91b](http://pastebin.com/f304ac91b)

Also, I recommend on being a bit more consistent on the indenting. This will make it much easier for yourself and others to read your code, and thus avoid errors and make it that much more maintainable.
You've come a long way since you started this thread, and it's just a few minor steps more until completion now. :-)

Happy codin'!

---

### Post by Dex14 on 2010-01-28
Wow thanks heaps.

But

alright  i replaced

[PHP]if ($_POST['Submit'] == 'Submit') {
    // FIXME: Neither $id nor $moviename is set.
    // TODO: Execute the query against the database server.
    $query1 = "SELECT Location, Filename FROM movies WHERE ID = $id and MovieName = $moviename";
    $path = $row['Location'] . $row['Filename'];
// FIXME: This doesn't make sense. Should be changed to an IF-test around the query above,
//        once the missing code is added.
} else {
    error_log (mysql_error ());
    $error_msg = '<p>something went wrong</p>';
}[/PHP]

with

[PHP]if ($_POST['Submit'] == 'Submit') { 
    $id = $_POST[$row['ID']]; 
    $moviename = $_POST[$row['MovieName']]; 
    $query = mysql_query("SELECT Location, Filename FROM movies WHERE ID = $id and MovieName = $moviename", $dbcnx);
    $num_rows = mysql_num_rows(query); 
} else { 
    error_log (mysql_error ()); 
    $error_msg = '<p>something went wrong</p>'; 
} 
while ($num_rows == 1) {
    $row1 = mysql_fetch_row($query); 
    $path = $row1['Location'] . $row1['Filename'];
}[/PHP]

its still not correct.
have i got the general gist of it?
what can be done?

thanks

---

### Post by Hellkeepa on 2010-01-28
HELLo!

You're getting closer, but you're not quite there. I would recommend readin a bit more up on the control structures of PHP, and the other basics, as it seems you're not quite on top of this.

Let me run down quickly on what this code does now:
[php]
// Check if the input field named "Submit" has been sent the value "Submit".
// This will not work in your code, as you named the input-field "submit". Case-sensitive.
if ($_POST['Submit'] == 'Submit') { 
    // Use the contents of the $row['ID'] as the index of the POST array, to try and retrieve the ID
    // This won't work because $row['ID'] is not set, and in any case will not point to the correct name of the input-field where this value has been set. Same for the movie name.
    $id = $_POST[$row['ID']]; 
    $moviename = $_POST[$row['MovieName']]; 

    // Runs the query against the server, to retrieve the selected movie.
    // This is correct, but you only need the ID to identify the movie.
    $query = mysql_query("SELECT Location, Filename FROM movies WHERE ID = $id and MovieName = $moviename", $dbcnx);

    // Return the number of rows found by the mysql-query, and store it in the variable $num_rows
    $num_rows = mysql_num_rows(query); 
// Execute this block if the matching IF-test returned false.
// This doesn't work properly, as it matches the POST-check, not the (missing) check on the MySQL result.
} else { 
    error_log (mysql_error ()); 
    $error_msg = '<p>something went wrong</p>';
} 

// Run this block if the $num_rows variable is equal to 1.
// This will end up in an endless loop, as $num_rows is not altered in the code below.
// Effectively making the code read: "while (1==1)"
while ($num_rows == 1) {
    // Fetch the row from the query, and store create the pathname from it.
    // Code is correct, but not necessary to use a new $row variable. Just overwrite the one above, as it is not needed anymore.
    $row1 = mysql_fetch_row($query); 
    $path = $row1['Location'] . $row1['Filename'];
}[/php]
Thus I'd write the code as follows:
[php]if (isset ($_POST['submit']) && $_POST['submit'] == 'Submit') { 
    // Retrieve and validate the ID, to make sure it's an integer and to disallow SQL-injections.
    $id = intval ($_POST['id']); 

    // Execute the query, and check if succeeded.
    if (!$query = mysql_query("SELECT Location, Filename FROM movies WHERE ID = $id", $dbcnx)) {
        // Show error messages in case the above query failed.
        error_log (mysql_error ()); 
        $error_msg = '<p>something went wrong</p>';
        // Do something to stop the parsing POST-enabled code here.
    }

    // Fetch the first row from the SQL result.
    $row = mysql_fetch_row($query); 
    $path = $row['Location'] . $row['Filename'];
}[/php]
The reason the IF-test around the MySQL query works, is because the "$result = mysql_query ()" is evaluated first. If the query fails, "mysql_query ()" will return false. "if (!false)" evaluates to "true", causing the block containing the error messages to be executed.

Happy codin'!

---

### Post by Reiger on 2010-01-28
Actually you did not get the control flow right either: on error you should abort but your code would happily go on to fetch no existing results:
[php]
if (isset ($_POST['submit']) && $_POST['submit'] == 'Submit') {  
    // Retrieve and validate the ID, to make sure it's an integer and to disallow SQL-injections. 
    $id = intval ($_POST['id']);  

    // Execute the query, and check if succeeded. 
    if (!$query = mysql_query("SELECT Location, Filename FROM movies WHERE ID = $id", $dbcnx)) { 
        // Show error messages in case the above query failed. 
        error_log (mysql_error ());  
        $error_msg = '<p>something went wrong</p>';  
    } 
    else { // actually abort on error!
        // Fetch the first row from the SQL result. 
        $row = mysql_fetch_row($query);  
        $path = $row['Location'] . $row['Filename']; 
    }
}
[/php]

And you should probably check if $id is the same as $_POST['id'] because you do not want to return random (cast) results but instead an error message if it is not an integer:

```

$post_id = isset($_POST['id']) ? $_POST['id']: "";
$id = intval ($post_id);
if($id == $post_id) {
  // ok go ahead with query!
}
else {
  // log the error?
  $error_msg = "<p>Oops! This ID is not valid: an ID consists of a number only (found something else).</p>";
}

```

---

### Post by Hellkeepa on 2010-01-28
HELLo!

The ID-check is done automatically by the SQL-query. "intval ()" returns "0" for all non-integer parsable results, and auto_increments are never 0 (unless specifically set to this, after the data has been added to the table). So in the case of a non-integer being passed, it'd return the error message of "no rows found".

Good catch on the missing control flow, though. Missed out on that one in the edits I did.

Happy codin'!

---

### Post by Reiger on 2010-01-28
You would do this $id == $post_id checking not for the benefit of the query/error message: you would do it because it enables things like auditing your website.

There is a distinction between not finding movie id=9999 and not finding movie id=9' 

This distinction is what makes explicit error detection/messages in queries that fail interesting for many purposes. You could for instance use it to blacklist IP's that mount SQL injection attacks; or use it to solve problems with broken links. It is more a matter of making a point of robust implementation, I guess.

---

### Post by Hellkeepa on 2010-01-29
HELLo!

Good point. Guess I'm too used to have such things automatically logged for me. ;-)

Happy codin'!

---

### Post by Dex14 on 2010-01-30
grrr. i still cannot make it work. oh well i think that i will put this project away till im a bit further along in my scripting/programming.

hey thanks for all your help hellkeepa, davetherave and reiger.

---


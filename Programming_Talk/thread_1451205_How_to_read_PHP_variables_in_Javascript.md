---
title: "How to read PHP variables in Javascript"
date: 2010-04-10
forum: Programming Talk
---

### Post by Tomtom5 on 2010-04-10
Here is what I'm trying to do and how I'm going about it.  I have an include file that contains all of the outputs of a program, this is to facilitate translation.  This file looks something like this:

<?php
$lblTitle="Language Setup";
$lblStr1="From Language:";
$lblStr2="To Language:";
$lblStr3="Create a New Language";
$lblStr4="Close with no update";
$lblStr5="Create Based On";
$lblStr6="New Language:";
$lblStr7="Create New Language";
$cmdSave="Save";
$msg1="What language should be used to create the new language.";
$msg2="Which language would you like to create.";
$msg3="This language is already defined.";
?>

I'm including this file doing the following in the first line of a PHP file:

<?php 
session_start();
$x=split("/", $_SERVER['PHP_SELF']);
include($_SESSION['SystemDirectory']."/language/".$_SESSION['LanguageCd']."/".$x[count($x)-1]);
?>

I can read the variables fine in HTML by simply doing <?php print $lblStr5 ?> but when it comes to reading the variables in a JavaScript, it gives me blank.  I try alert("<?php print $msg1 ?>"); and it gives ma a blank.  Is this something that is possible?  How?

Thank you

---

### Post by Compyx on 2010-04-10
Simple answer: you can't.

Javascript and PHP cannot directly communicate with each other, Javascript lives on the client-side of things, while PHP resides on the server-side.
You can however use AJAX to communicate with PHP via Javascript, you basically set up an HTTP-request and send that to the server, PHP can then parse the request and send back either a simple string or an XML document. You can then parse the resulting string or XML document in Javascript to see what PHP sent back.

Google for AJAX, it may look intimidating at first, but it's actually quite simple.

Another way to pass data from PHP to Javascript is to have PHP spit out chunks of Javascript embedded in the HTML output. But I strongly suggest you don't do that, it violates the concept non-obtrusive javascript, and is a nightmare to debug/maintain.

Both Javascript and PHP have access to cookies, so you could use that to pass data around. I myself have never done that, I prefer AJAX, but you could look into that.


So, in my opinion, AJAX is the way to go, but you're of course free to do what you like.

---

### Post by BackwardsDown on 2010-04-10
> I can read the variables fine in HTML by simply doing <?php print $lblStr5 ?> but when it comes to reading the variables in a JavaScript, it gives me blank. I try alert("<?php print $msg1 ?>"); and it gives ma a blank. Is this something that is possible? How?


Press ctrl-u and post your generated javascript here. <?php echo $msg1; ?> should work. Do you have php errors/warnings enabled?

---

### Post by djoxyk on 2010-04-10
yet another way is to print your javascript from php. someting like

[PHP]
<?php

$data = '
<script .... >
var message = '.$message.';
.....
</script>
';

echo $data;

?>
[/PHP]

or use heredocs to keep it clean. basically ajax can do the same in more elegant way.

---

### Post by Tomtom5 on 2010-04-11
Thank you all.  I opted for session variables that are loaded like the following:

<?php
$_SESSION['nVars']="11";
$_SESSION['sLabel1']="Language Setup";
$_SESSION['sLabel2']="From Language:";
$_SESSION['sLabel3']="To Language:";
$_SESSION['sLabel4']="Create a New Language";
$_SESSION['sLabel5']="Close with no update";
$_SESSION['sLabel6']="New Language:";
$_SESSION['sLabel7']="Create New Language";
$_SESSION['sLabel8']="Save";
$_SESSION['sLabel9']="What language should be used to create the new language.";
$_SESSION['sLabel10']="Which language would you like to create.";
$_SESSION['sLabel11']="This language is already defined.";
?>
 That's the simplest way I could find.

Thanks again

---


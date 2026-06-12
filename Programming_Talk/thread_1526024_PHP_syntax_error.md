---
title: "PHP syntax error"
date: 2010-07-07
forum: Programming Talk
---

### Post by epicoder on 2010-07-07
I have a php page to add a game to my custom chess 'database'. I keep getting this syntax error:

PHP Parse error:  syntax error, unexpected '}' in /var/www/chess/addgame.php on line 44

I have thoroughly checked it for brace count and other syntax errors to no avail. Here is the page, line 44 has a --> in front of it:

[PHP]<html><head>
<title>Add a game to the database</title>
<link rel="stylesheet" type="text/css" href="files/chess.css"></link>
<style type="text/css">
h3 {position:relative;top:-35px;}
</style>
</head>
<body>
<a href="addgame.php?action=help">Help</a>
<h3 class="center">Add a game to the database</h3>
<?php
if ($_GET["action"] == "help") {
?>
<p>You can enter "-" in any field to signify that it is unknown.<br /><br />
In the text area, enter your game in algebraic notation with annotations and appelations, like so:<br /><br />
21...Kg3 Helps protect black&rsquo;s king.<br />
37.Bb7!</p><br />
<p><a href="javascript:history.go(-1)">Back</a></p>
<?php
} elseif ($_GET["action"] == "add") {
$whitefirst = $_POST["whitefirst"];
$whitelast = $_POST["whitelast"];
$blackfirst = $_POST["blackfirst"];
$blacklast = $_POST["blacklast"];
$whitename = strtolower($whitefirst.";".$whitelast);
$blackname = strtolower($blackfirst.";".$blacklast);
$year = $_POST["year"];
$opening = $_POST["opening"];
$result = $_POST["result"];
$game = explode(" ", $_POST["game"]);
$pgn = array(0 => "[White \"".$whitefirst." ".$whitelast."\"]\n", 1 => "[Black \"".$blackfirst." ".$blacklast."\"]\n");
$wrating = $_POST["wrating"];
$wratingmod = $_POST["wratingmod"];
$brating = $_POST["brating"];
$bratingmod = $_POST["bratingmod"];
$wfinalrate = "[White".$wratingmod." \"".$wrating."\"]\n";
array_push($wfinalrate, $pgn);
$bfinalrate = "[Black".$bratingmod." \"".$brating."\"]\n";
array_push($bfinalrate, $pgn);
$incomment = "false";
if ($result == "white") {
$rwhite = "[Result \"1-0\"]\n";
array_push($rwhite, $pgn);&#8207;
/* --> */} elseif ($result == "draw") {
$rdraw = "[Result \"1/2-1/2\"]\n";
array_push($rdraw, $pgn);&#8207;
} else {
$rblack = "[Result \"0-1\"]\n";
array_push($rblack, $pgn);
}
foreach($game as $move) {
if(preg_match("/[0-9]*\.*[knbqr]*[a-g][1-8][!?]*/i", $move)) {
if ($incomment == "true") {
$incomment = "false";
$tmp = "} ".$move
array_push($tmp, $pgn);
} else {
array_push($move, $pgn);
}
} else {
if ($incomment == "false") {
$incomment = "true";
$tmp"{".$move
array_push($tmp, $pgn);
} else {
array_push($move, $pgn);
}
}
}
$finalpgn = implode(" ", $pgn);
file_put_contents("./files/games/".$whitename."{".$blackname."[".$opening."]".$result.",".$year.".txt", $finalpgn);
?>
<p>Your game has been added!</p>
<?php
} else {
require("./files/opening.php");
?>
<form action="addgame.php?action=add" method="post" name="game">
<p>White&rsquo;s first name: <input type="text" name="whitefirst" /> Last name: <input type="text" name="whitelast" /></p>
<p>Black&rsquo;s first name: <input type="text" name="blackfirst" /> Last name: <input type="text" name="blacklast" /></p>
<p>White&rsquo;s rating: <input type="text" name="wrating" />&nbsp;&nbsp;<select name="wratingmod">
<option value="USCF">USCF</option>
<option value="Elo">FIDE</option></select></p>
<p>Black&rsquo;s rating: <input type="text" name="brating" />&nbsp;&nbsp;<select name="bratingmod">
<option value="USCF">USCF</option>
<option value="Elo">FIDE</option></select></p>
<p>Year: <input type="text" name="year" /></p>
<p>Opening: <select name="opening">
<option value="xxx">Unknown</option>
<?php
foreach($openout as $openname) {
echo "<option value=\"".$openin[$openname]."\">".$openname."</option>\n";
}
?>
</select></p>
<p><select name="result">
<option value="white">White wins</option>
<option value="draw">Draw</option>
<option value="black">Black wins</option>
</select></p>
<textarea rows="20" cols="50" name="game"></textarea>
<p><input type="submit" value="Add Game" />&nbsp;&nbsp;<input type="reset" value="Reset" /></p>
</form>
<!--[if lte IE 7]> 
<script src="http://ieai.pieroxy.net/ieai.js"></script>
<![endif]--> 
<?php
}
?>
</body></html>[/PHP]Any help would be appreciated.

---

### Post by dapperdanny77 on 2010-07-07
there is no closing } within the first <?php ..?> section - why did you split the php code?
I'm quite sure you cannot span if ... then ... else statement (or ony other) over multiple <?php ..?> blocks

---

### Post by GreenN00b on 2010-07-07
Remove & # 8207 ; and similar stuff from the file.

---

### Post by epicoder on 2010-07-07
To answer my own question: I had copied an Right-to-left Unicode control character to my clipboard earlier and accidentally pasted it in there.

Oops.

---

### Post by dapperdanny77 on 2010-07-07
you are not the first guy having such an accident ;)

---


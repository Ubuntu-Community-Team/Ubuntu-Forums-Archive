---
title: "PHP array question"
date: 2010-12-05
forum: Programming Talk
---

### Post by johnmay on 2010-12-05
I have a small php script that does what I want ... except... 

it iterates through an array and compares it to a value. 

everything works fine unless the first value in the array ends with .php

Then it breaks... in the following that script works fine until I remove the 't' from the 

.tphp then nothing... Does it have something to do with the keys? 

<?php 
function curPageName() {
 return substr($_SERVER["SCRIPT_NAME"],strrpos($_SERVER["SCRIPT_NAME"],"/")+1);
}
//init array
$myphp=array("phptest.tphp","about.php","programs.php","rastation.php","shaeling.php","soul.php","water.php","contact.php");
$myPages = array ("Home","About","Programs","Rastation","Shaeling Singers","Soul, Soul, Soull","Underwater Basket Weaving","Contact");
$sPage = curPageName();
$i=0;
foreach($myPages as $ens)
   {
if ($myHtml[$i] != $sPage){
echo '<a href="http://mysite.com/notsites/' . $myHtml[$i] .'" target="_SELF">' . $myPages[$i] .'</a><br />';
   //echo $myPages[$i]."<br />";
$i++; }
}

---

### Post by secondstage on 2010-12-29
It appears that you're making a list of links to parts of your site, excluding the one the user is currently on. I can't really troubleshoot your code, but I'll give an alternative.

Instead of iterating through every element manually to check if it's not the current one, construct two arrays: One for all of the links, and one of the current page. Take these two arrays and output the difference. 

NOTE: This code was not tested. But I've looked over it a few times and am fairly sure it will work as intended.

[php]
<?php
function currentPage() {
   return substr($_SERVER["SCRIPT_NAME"],strrpos($_SERVER["SCRIPT_NAME"],"/")+1);
}

$links = array("Home"=>"index.php", "About"=>"about.php", "Questions"=>"answers.php", "Apples"=>"oranges.php");
$current = array("Current"=>currentPage());// it really doesn't matter what the index is.
$output = array_diff($links, $current);// is $links, excluding any elements of $links that have the same value as any element of $current
foreach ($output as $out->$put) {
   echo '<a href="http://mysite.com/"' . $put . ' target="_SELF">' . $out . '</a><br />';
}
?>
[/php]

I got the fancy coloring by wrapping the code in [noparse][php] and [/php][/noparse]

---

### Post by johnmay on 2010-12-30
secondstage, 

I will let you know when I am able to test the code you suggested. 

I have found other workarounds, I am really curious as to why the code didn't work initially...


Thanks!

---


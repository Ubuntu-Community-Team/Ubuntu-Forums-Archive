---
title: "a nice working test for javascript on or off with PHP"
date: 2011-01-31
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-31
found this works well and is easy, anyone have something even better?

I found that my sessions were being erased since this javascriot test reposts the form
so to check that, put the post test here also. Otherwise when the javascript 
echo 'document.jsform.submit();';
runs, the form is reloaded and all my var results were blanked.

> 
if (isset($_POST['jstest'])) {
unset($_SESSION['ws1']);
session_unset();
session_destroy();
$_SESSION = array();
}

[PHP]<?php

session_start();
unset($_SESSION['javaonoff']);

if (isset($_POST['jstest'])) {
  $nojs = FALSE;
  } else {
  // create a hidden form and submit it with javascript
  echo '<form name="jsform" id="jsform" method="post" style="display:none">';
  echo '<input name="jstest" type="text" value="true" />';
  echo '<script language="javascript">';
  echo 'document.jsform.submit();';
  echo '</script>';
  echo '</form>';
  // the variable below would be set only if the form wasn't submitted, hence JS is disabled
  $nojs = TRUE;
}
//$on is on means javascript is on, off means it is off
if ($nojs){
  echo "NO JS";
$_SESSION['javaonoff']='off';
}
else
{
echo "YES JS";
$_SESSION['javaonoff']='on';
}
?>

put this little bit on another page, I simply called it '$on'
//test carried from mysearch2first.php for javatest on or off
$on = $_SESSION['javaonoff'];[/PHP]

---


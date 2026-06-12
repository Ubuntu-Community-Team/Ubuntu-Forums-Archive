---
title: "[SOLVED] Odd php/mysql output"
date: 2007-08-20
forum: Programming Talk
---

### Post by rock freak on 2007-08-20
Right on this (Linked Removed) if you just hit register withotu putting any inputs in it does its job fine it checks and sees there is nothing and pops out the apporpiate error messages.  

But look at the top of the page and you will see:
  "RESULTS:: Resource id #5 RESULTS:: Resource id #7"

None of that is in any of my source code!!  It's been doing my nut in for the last couple of days!! does anybody know why in hell it might be doing it!!  Ive checked recheck and rechecked the source again and even got another person to check through and nothing!!

Cheers
Ollie

EDIT: Ok dont worry quite yet!! Just seen that the xhtml is everywhere ill sort that first!!

---

### Post by endersshadow on 2007-08-20
Generally this happens when you assign a variable as a resource and mistake it for the data you want.  See [here](http://www.aprelium.com/forum/viewtopic.php?t=9679).

Anything more than that, and I at least need to see the relevant source code (please don't post username/passwords!!).

---

### Post by rock freak on 2007-08-20
Ill just sort out this XHTML errors I have in it tthen ill check for what you sugegsted!! if that fails ill post the source code up!!

Cheers for the response!!

Ollie

EDIT: I hate working with other peoples code XD even more so when its as messed up as this is!!

---

### Post by endersshadow on 2007-08-20
Not a problem.  Just comb through your echo statements and make sure you're not echoing a result set.

---

### Post by rock freak on 2007-08-20
> **endersshadow said:**
> Not a problem.  Just comb through your echo statements and make sure you're not echoing a result set.

Have done that about 4 times already!!  Not a single echo statement in any of the source that has that in it!!  That’s why I’m completely confused and bewildered!!

Cheers
Ollie

---

### Post by rock freak on 2007-08-20
I know i had an debug statement liek that when i was developing the script but I removed them long ago. 

The strange thing is the output only started to happen when I inserted it into the page its self.
 
Here is the (Link Removed)
If you do the same no output :S

Is throughly confused and I will just sort out the source code for it!

---

### Post by rock freak on 2007-08-20
Right ehre is the source code for test.php
```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<link rel="stylesheet" type="text/css" href="reg.css" />
<title>Belcom</title>
<?
$cName = NULL;
$email = NULL;
if (isset($_POST['sent'])){
  $val = 1;
  require 'validate.php';
  $dups = 1;
}
else{
  $val =0;
  $dups = 0;
}

if ($val == 1 && $dups == 1){
  if (db_dupl("cName", $cName) == 0){
    $error["cNameDup"] = 0;
  }
  else{
    $error["cNameDup"] = 1;
  }
  if (db_dupl("email", $email) == 0){
    $error["emailDup"] = 0;
  }
  else{
    $error["emailDup"] = 1;
  }
  if ($error["cNameNull"] == 0 && $error["cNameDup"] == 0 && $error["emailNull"] == 0 && $error["emailVal"] == 0 && $error["emailDup"] == 0){
    dbc();
    $querytr = "SELECT `tr` FROM `users` WHERE `cName`='$cName'";
    $resultstr = mysql_query($querytr) or die ('Error checking database: ' . mysql_error() );
    $tr = mysql_fetch_array($resultstr, MYSQL_ASSOC);
    mysql_close();
    echo $tr["tr"] . '<br />';
    if ($tr["tr"] == NULL){
      $tr["tr"] = 1;
    }
    else{
      $tr["tr"]++;
    }
    /* Insert Into Database */
    /* Define varible to Insert record into the mysql database */
    $query = "INSERT INTO `users` (`id`, `email`, `cName`, `pWord`, `status`, `ban`, `tr`, `dr`) VALUES (NULL, '$email', '$cName', '1234', 0, 0, '$tr', NOW() )";
    dbc();
    /* Insert the record into the database */
    @mysql_query($query) or die('Error Inserting Record. Error: ' . mysql_error() );
    mysql_close();
    echo '<SCRIPT TYPE="text/javascript">' . "parent.location='reg_done.php' //-->" . '</SCRIPT>';
  }
  else{
    $insert = 0;
  }
}
?>
</head>

<body>
<form id="form_con" action="<? echo $_SERVER['PHP_SELF']; ?>" method="post">
  <fieldset>
      <legend>Please Enter Your Details</legend>
    <div id="reg_left">
      <p id="reg_p">Company Name:<br />Email Address:</p>
    </div>
    <div id="reg_right">
      <input type="text" name="cName" value="<? echo $cName; ?>" size="30" maxlength="100" /><br />
      <input type="text" name="email" value="<? echo $email; ?>" size="30" maxlength="100" /><br />
    </div>
    <div id="reg_errors">
      <p id="reg_p_error">
        <?
           if ($val == 1 or $dups == 1){
             if($error["cNameNull"] == 1){
               echo 'You havn\'t entered your company name.<br />';
             }
             if($error["cNameDup"] == 1){
               echo 'Your company name is already registered.<br />';
             }
             if($error["emailNull"] == 1){
               echo 'You havn\'t entered your email.<br />';
             }
             if($error["emailNull"] == 0 && $error["emailVal"] == 1){
               echo 'Your email is not valid(eg you@example.com).<br />';
             }
             if($error["emailDup"] == 1){
               echo 'Your email has already been registered.<br />';
             }
           }
           ?>
         </p>
       </div>
  </fieldset>
  <div id="reg_sub">
    <input type="hidden" name="sent" value="1" />
    <input type="submit" name="submit" value="Register" />
  </div>
</form>
</body>
</html>

```

Here is the source for validate.php
[PHP]
<?
require 'lib.php';
$cName = $_POST['cName'];
$email = $_POST['email'];
$error = array("cNameNull" => 0, "emailNull" => 0, "emailVal" => 0, "cNameDup" => 0, "emailDup" => 0);
if (chk_null($cName) == 0){
  $error["cNameNull"] = 0;
}
else{
  $error["cNameNull"] = 1;
}

if (chk_null($email) == 0){
  $error["emailNull"] = 0;
}
else{
  $error["emailNull"] = 1;
}

if (email_vald($email) == 0){
  $error["emailVal"] = 0;
}
else{
  $error["emailVal"] = 1;
}
[/PHP]

And here is the source for the functions it calls:
chk_null
[PHP]
/* Check for Null value */
function chk_null($var){
  if(!empty($var)){
    return 0;
  }
  else{
    return 1;
  }
}
[/PHP]

and db_dupl
[PHP]
/* Check for Duplicates in database */
function db_dupl($col, $val){
  dbc();
  $query = "SELECT * FROM `users` WHERE $col='$val'";
  $results = mysql_query($query) or die ('Error checking database: ' . mysql_error() );
mysql_close();
  if (mysql_num_rows($results) == 0){
    return 0;
  }
  else {
     return 1;
  }
}
[/PHP]

and email_vald
[PHP]
/* Check Email Validilaty */
function email_Vald($email){

  if (eregi ('^[[:alnum:]][a-z0-9_\.\-]*@[a-z0-9\.\-]+\.[a-z]{2,4}$', $email)){
   
    return 0;
  }
  else{
   
    return 1;
  }
}
[/PHP]

dbc is the database connection script I know thats fine!

They are all called from lib.php int he validate.php script!!  
If i have missed any off say and ill get them!
Hope this helps!!

---

### Post by endersshadow on 2007-08-20
Well, test.php works for me, as well, so I'm in the dark.  Did you cut and paste code to test.php?

---

### Post by rock freak on 2007-08-20
> **endersshadow said:**
> Well, test.php works for me, as well, so I'm in the dark.  Did you cut and paste code to test.php?

Yup as am I!! I can only assume it has to do with the complete bodge job the original person has made of the code lol!!

So I&#8217;m now currently recoding the page getting rid of those bloody tables and pop it into xhtml with css to see if that sorts it out!!!(In an act of desperation)

Cheers for the help!  If I figure it out ill post the reply!

Ollie

EDIT: yes i did cut and paste and ive tried typign it all out as well and trying it is a require/include in as well!!

---

### Post by rock freak on 2007-08-20
*deleted*

---

### Post by rock freak on 2007-08-21
SOLVED IT!!!
Every week I go through the files on the PC/Web servers that I control too check for any erroneous scripts!!

Low and behold this week it paid off as I was looking through the root HTML directory I found a stray and may I add old lib.php of which for some unknown reason the register script was calling!! 

That old lib.php had the debugging scripts in of which I new that’s what the "RESULTS:: etc.." was.  Removed it now works like a charm!

Not a clue how it found its way out of the scripts folder but o well found another load as well.

Anyways all good cheers for the help much appreciated!

Cheers 
Ollie

---


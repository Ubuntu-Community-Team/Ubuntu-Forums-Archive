---
title: "Possible PHP coding problem"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by arizonanoob on 2012-08-14
I've been wrestling with getting Apache2, PHP & MySQL working and am nearly all the way there. I'm not certain whether a PHP error is the culprit or whether I'm just not connecting to the MySQL server, so first, the error in my Apache2 error log

```
PHP Notice:  Undefined variable: report in /var/www/MyFolder/reports.php on line 231, referer: http://localhost/MyFolder/reports.php
```This is the PHP code... there are other instances referring to other tables, but they all are basically the same db call

```
<? if ($report == "students") { 
        ?>
``````
if ($report=="affiliates"){ 
    echo("<META HTTP-EQUIV='refresh' content='0;URL=aff_report.php'>\n");          
    exit; 
}
``````
<? 
            } 
            elseif ($report == "employers") { 
            ?>
```$reports is not defined in any other way except to refer to a db table.

Any ideas? This code works just fine on a commercial web host but not on my Ubuntu box at home.

---

### Post by spjackson on 2012-08-14
It's not possible to say from these fragments what is wrong. The $report variable is never set. Possible causes:

[LIST]
[*]It is set in an if branch that isn't entered.
[*]It's retrieved from a database but either no row is returned, an error occurs, or the relevant column is null.
[/LIST]
If the php script is handling database errors, you'd expect a relevant message either in the apache error log, or reported to the user.

---

### Post by arizonanoob on 2012-08-14
> **spjackson said:**
> It's not possible to say from these fragments what is wrong. The $report variable is never set. Possible causes:

[LIST]
[*]It is set in an if branch that isn't entered.
[*]It's retrieved from a database but either no row is returned, an error occurs, or the relevant column is null.
[/LIST]
If the php script is handling database errors, you'd expect a relevant message either in the apache error log, or reported to the user.

Well, not any error messages being displayed in the browser. Here is a more complete outlay of the code:

```

include("connectdb.inc");
if ($fromyear && $frommonth &&fromday) { 
    $fromdate = "$fromyear-$frommonth-$fromday";
}
if ($toyear && $tomonth && $today) {
    $todate = "$toyear-$tomonth-$today";
}


function show_classes($class) 
{ 
    $result=mysql_query("SELECT * FROM class"); 
    while($array=mysql_fetch_array($result)) 
    {
        $classid = $array["classid"];
        $classname = $array["classdesc"];
        if ($classid == $class) {
            printf("<option value=%s SELECTED>Class %s</option>",$classid, $classid);
        }
        else {
            printf("<option value=%s>Class %s</option>",$classid, $classid);
        }
    }
} 




function show_topics($topicid) 
{ 
    $result=mysql_query("SELECT * FROM topic"); 
    while($array=mysql_fetch_array($result)) 
    {
        $topic = $array["topicid"];
        $topicdesc = $array["topicdesc"];
        if ($topic == $topicid) {
            printf("<option value=%s SELECTED>Topic %s</option>",$topic,$topic);
        }
        else {
            printf("<option value=%s>Topic %s</option>",$topic,$topic);
        }
    }
} 


function show_employers($tableName,$eid) 
{ 
    $result=mysql_query("SELECT * FROM $tableName ORDER BY company"); 
    while($row=mysql_fetch_array($result)) 
        { 
            if ($row["eid"] == $eid) {
            
                printf("<option value=%s SELECTED>%s, %s, %s</option>",$row["eid"],$row["company"],$row["city"],$row["state"]);
            } 
            else {
                printf("<option value=%s>%s, %s, %s</option>",$row["eid"],$row["company"],$row["city"],$row["state"]);
            }
        } 
} 
?>
<html>
<head>
<title>Administration</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
</head>


<body bgcolor="#FFFFFF" text="#000000">

<table width="100%" border="0" cellspacing="0" cellpadding="0">
  <tr> 
    <td> <a href="admin.php"><b>[Admin]</b></a>&nbsp;<a href="<? echo $_SERVER['PHP_SELF']; ?>"><b>[Reports]</b></a> 
      <? if ($report == "students") {
        ?>
      &nbsp;<b>[Students]</b> 
      <form action="<? echo $_SERVER['PHP_SELF']; ?>" method="post">

        <input type="hidden" value="students" name="report">
        <select name="eid" size="1" onChange="this.form.submit()">
          <option value="">All employers 
          <?
                    show_employers(employer,$eid);
                ?>
        </select>
      </form>
      <table cellpadding="2" cellspacing="5" width="100%">
        <tr> 
          <td><b>Name</b></td>
          <td><b>Employer</b></td>
          <td><b>Classification</b></td>
        </tr>
        <?  
                if ($eid) {
                    $query = "SELECT * FROM student WHERE eid = $eid ORDER BY lastname, firstname";
                }
                else {
                    $query="SELECT * FROM student ORDER BY lastname, firstname";
                }
                $result=mysql_query($query); 
                $total = mysql_num_rows($result);
                
                while($array=mysql_fetch_array($result)) 
                {
                    $uid=$array["uid"];
                    $firstname=$array["firstname"];
                    $lastname=$array["lastname"];
                    $eid=$array["eid"];
                    
                    $query="SELECT * FROM employer WHERE eid = $eid";
                    $empresult=mysql_query($query);
                    $emparray=mysql_fetch_array($empresult);
                    $employer=$emparray["company"];

$module_query="SELECT * FROM certification WHERE uid = $uid ";
$module_result=mysql_query($module_query) or die(mysql_error()); 
$num_rows=mysql_num_rows($module_result);
if ($num_rows >0) {
    while($module_array=mysql_fetch_array($module_result)) 
    {
        $moduleid=$module_array["moduleid"];
        $module_query="SELECT * FROM module WHERE moduleid = $moduleid";
        $modmodule_result=mysql_query($module_query) or die(mysql_error());
        $modarray=mysql_fetch_array($modmodule_result);
        $moduledesc=$modarray["moduledesc"];
    }
}


                   ?>
        <tr valign="top"> 
          <td><a href="<? echo $_SERVER['PHP_SELF']; ?>?report=studentdetail&uid=<? echo $uid; ?>&eid=<? echo $eid; ?>"> 
            <? echo $lastname; ?>
            , 
            <?  echo $firstname; ?>
            </a></td>
          <td><a href="<? echo $_SERVER['PHP_SELF']; ?>?report=employerdetail&eid=<? echo $eid; ?>"> 
            <?  echo $employer; ?>
            </a></td>
          <td> 
            <? echo $moduledesc; ?>
            <p>&nbsp;</p></td>
        </tr>
        <?
                }
                ?>
        <tr> 
          <td colspan="4"> 
            <hr>
          </td>
        </tr>
        <tr> 
          <td colspan="4"><b>Total students: 
            <? echo $total; ?>
            </b></td>
        </tr>
      </table>
      <?
            }
            elseif ($report == "employers") {
            ?>
      &nbsp;<b>[Employers]</b> 
      <table cellpadding="2" cellspacing="5">
        <tr> 
          <td><b>Company</b></td>
          <td><b>City, State</b></td>
          <td></td>
        </tr>
        <?  
                $query="SELECT * FROM employer ORDER BY company";
                $result=mysql_query($query); 
                $total=mysql_num_rows($result);


                while($array=mysql_fetch_array($result)) 
                {
                    $eid=$array["eid"];
                    $name=$array["company"];
                    $city=$array["city"];

                    $state=$array["state"];
                                        
                    ?>
        <tr> 
          <td><a href="<? echo $_SERVER['PHP_SELF']; ?>?report=employerdetail&eid=<? echo $eid; ?>"> 
            <? echo $name; ?>
            </a></td>
          <td> 
            <? echo $city; ?>
            , 
            <? echo $state; ?>
          </td>
          <td><a href="delete.php?eid=<?echo $eid;?>">Delete</a></td>
        </tr>
```

---

### Post by SteveHillier on 2012-08-14
First I am going to guess.
I see nowhere in your code where the variable '$report' is ititialised.
You have an error code saying undefined variable at line 231.  Use that information but.....

You are using an include file.  When php parses the file it will include the file and adjust all it's line numbers accordingly, so to find the error you have to undertake some investigation but my guess would be to check where $report is being initialised first.

---

### Post by arizonanoob on 2012-08-14
Thanks - but all the errors reported in the log file refer to every instance and line that the variable $reports is used - not just one error.

The real question is - is some of this code deprecated?? The code is about 10 yrs old, but it does work on at least two different commercial web servers.

---

### Post by SteveHillier on 2012-08-14
Your response cements for me that the variable $report is not initialised.

It might be a scoping issue - ie what is the scope of the variable.  On other servers is this being used with some sort of global property which makes it visible in your routine.  

Have a quick look at your include file and see if that variable is used there, in particular if it is initialised in the include file.  If it is and it is then not visible in your routine then scoping rises higher up the list of solutions.

Somewhere before you use the construct if ( $report == anything ) there must be a line that says $report = something otherwise it just won't work as expected.

---

### Post by arizonanoob on 2012-08-14
Definitely appreciate your assistance. Here is the include file. It is the only include file being used (other than header & footer for a html wrapper - contains no php code)

```

<?php
$host = "localhost";
$dbusername = "xxxxxxxxxx";
$dbpassword = "xxxxxxxxxxx";
$database = "xxxxxxxxxxxxxx";
// connect to the database, since each part of this uses 
// the connection, we can just connect once at the beginning   
$dbh = mysql_pconnect($host, $dbusername, $dbpassword) or die(mysql_error());    
//select our database
mysql_select_db($database)  or  die(mysql_error());       
?>

```

If **$reports == employers** then it pulls the data from the employer table and echoes it in the report. Similarly with students table and financial table.

On the servers where the code works, $reports is not defined beyond something like **$reports == employers**

---

### Post by SeijiSensei on 2012-08-14
If this code is ten years old, then it was written at a time when PHP was much less stringent about things like undefined variables.  Modern PHP releases will complain about any variable that is used without initialization, and even undefined array indexes.

The solution is simply to add a line like

```
$reports='';
```

before the variable is used.

In the code you post at the top of this thread, there's no handler for the case where $reports isn't one of the tested strings like "students" or "employers".  

In general, those kind of if() tests are often best handled with the switch() function like this:

```

<?php

switch($reports) {

    case "employers":
        stuff;
        break;
   
    case "students":
        other stuff;
        break;

    case "affiliates":
        still other stuff;
        break;

    default:
        do this when all else fails;

}
?>

```

"Notices" logged by PHP are not fatal errors.  They're simply warnings that your code doesn't meet the current standards which expect all variables and array indexes to be initialized before use.

---

### Post by arizonanoob on 2012-08-14
I'm thinking that the $reports variable is created here:

```

      <form action="reports.php" method="post">
        <select name="report" onChange="this.form.submit()">
          <option value="">Choose Report</option>
          <option value="students">Students</option>
          <option value="employers">Employers</option>
          <option value="financial">Financial</option>
        </select>
      </form>

```

But, as my forum username indicates, I'm far from a php guru

---

### Post by spjackson on 2012-08-14
I've only been using PHP for a year or so, so I don't know what it used to be like. However, I think [this page]("http://www.lunarforums.com/web_hosting_help_and_troubleshooting/php_and_register_global_variables-t46641.0.html") explains what's going on. In the code you have shown us, $report is never set anywhere, so how can it work on some server? It must be some kind of global variable. Modern php doesn't have this kind of global variable, but that page explains that it  once did.
> 
Once upon a time, most PHP programmers simply grabbed variables and  values by using them in their code. Let's say you had two fields in a  form, named "user_name" and "user_email". You could simply *use* **$user_name** and **$user_email**  in your code (the receiving, or target, page), and they would have the  values filled in by the user in the form. Life was simple, wasn't it? **$user_name** and **$user_email** were examples of a special kind of PHP variable, called a ***register global variable***. You simply used it, and it was magically there to pull in data transferred from a form or a link on another page.

<snip>

You've been happily using register global variables for years, and all  of a sudden, your code doesn't work anymore. You might get PHP or MySQL  errors, or a blank page, or your system just isn't working as expected.  Maybe you added some debug print statements, and discovered that these  register global variables are now simply undefined (have no value).


---

### Post by lisati on 2012-08-14
> **arizonanoob said:**
> I'm thinking that the $reports variable is created here:

```

      <form action="reports.php" method="post">
        <select name="report" onChange="this.form.submit()">
          <option value="">Choose Report</option>
          <option value="students">Students</option>
          <option value="employers">Employers</option>
          <option value="financial">Financial</option>
        </select>
      </form>

```

But, as my forum username indicates, I'm far from a php guru

Not quite. "reports.php" is the name of the script that gets run when the form is submitted.

---

### Post by spjackson on 2012-08-14
> **arizonanoob said:**
> I'm thinking that the $reports variable is created here:

```

      <form action="reports.php" method="post">
        <select name="report" onChange="this.form.submit()">
          <option value="">Choose Report</option>
          <option value="students">Students</option>
          <option value="employers">Employers</option>
          <option value="financial">Financial</option>
        </select>
      </form>

```But, as my forum username indicates, I'm far from a php guru
OK, so I think that basically to translate from ancient PHP to modern PHP, you need to add this to your other script.
```

  $report = $_POST['report'];

```However, it is a bit more complicated than that because the script reposts to itself and it will need to repost this report data item - or it could be converted to a session variable. Needs more work and it's bedtime here ;-)

---

### Post by arizonanoob on 2012-08-14
THAT WAS IT!!!!!!!!!!!! WOOOOHOOOOO!

register_globals needed to be turned on.

Thank you, thank you, thank you, thank you, thank you, thank you, thank you, thank you, thank you, thank you.

---

### Post by cryptotheslow on 2012-08-14
Take a lot of care if you decide to update your PHP version.

What version are you running?

If I remember correctly register_globals was depracted in v.5.3 and **removed entirely** in v.5.4

Could be problematic if one of your web hosters decides to upgrade!

My memory is fallible but I'm fairly sure the above is correct, been while since I did php stuff in earnest though :/

---

### Post by SeijiSensei on 2012-08-14
No, enabling register_globals is the *wrong approach*.  Not only is it insecure, but as cryptotheslow observes, it has been deprecated in the most recent PHP versions.

All the POST information is stored in the $_POST array (and also the $_REQUEST array which includes both GET and POST input).  You can create a local $reports variable from $_POST['reports'], as spjackson observes.  However any script that includes user-generated input, unless it is running in a closed environment like an intranet, needs to have that input validated.  So, again, make sure you have something to handle values that don't match the ones you expect.  

I've seen all sorts of things attached as values to exposed variables. The cardinal rule is not to trust user input.

---

### Post by arizonanoob on 2012-08-15
Understood - but until the client is ready to spend the money to have the code updated, I have to take what I can get... and this is a temporary fix.

---

### Post by SeijiSensei on 2012-08-15
Well, I'd make sure you activate register_globals only for this client.  You can [do this]("http://php.net/manual/en/configuration.changes.php") in .htaccess or in the <Directory> stanza for the client's virtual host by adding "php_flag register_globals on".  I wouldn't turn it on globally via php.ini if you can avoid it.

---

### Post by SteveHillier on 2012-08-19
> **SeijiSensei said:**
> Well, I'd make sure you activate register_globals only for this client.  You can [do this]("http://php.net/manual/en/configuration.changes.php") in .htaccess or in the <Directory> stanza for the client's virtual host by adding "php_flag register_globals on".  I wouldn't turn it on globally via php.ini if you can avoid it.

Echo this comment.
On our server we have some systems that rely on register variables being on (older shopping carts) and others that rely on register variables being off.
This has to be set by domain / client.
Ultimately you have to write your code to meet the current standards to avoid wholsale collapse of your site one day.

---


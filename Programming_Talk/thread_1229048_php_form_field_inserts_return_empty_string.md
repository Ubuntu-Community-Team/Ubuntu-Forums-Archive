---
title: "php form field inserts return empty string"
date: 2009-08-01
forum: Programming Talk
---

### Post by wizardry on 2009-08-01
hello -

i've created a form that has multiple inserts. it inserts the data fine if i manually parse the data to it but when i use the form to test the inserts it errors out.

it errors out at the title/comments table. the 2 tables before are inserted fine.

i've used echo $_post variable and the variable is their. but its not being inserted into the database.

```

******************************************************************************** ******************************************************************************

 

  1 <?php require_once('Connections/upics.php'); ?>$
  2 <?php$
  3 if (!function_exists("GetSQLValueString")) {$
  4 function GetSQLValueString($theValue, $theType, $theDefinedValue = "", $theNotDefinedValue = "") $
  5 {$
  6   if (PHP_VERSION < 6) {$
  7     $theValue = get_magic_quotes_gpc() ? stripslashes($theValue) : $theValue;$
  8   }$
  9 $
10   $theValue = function_exists("mysql_real_escape_string") ? mysql_real_escape_string($theValue) : mysql_escape_string($theValue);$
11 $
12   switch ($theType) {$
13     case "text":$
14       $theValue = ($theValue != "") ? "'" . $theValue . "'" : "NULL";$
15       break;    $
16     case "long":$
17     case "int":$
18       $theValue = ($theValue != "") ? intval($theValue) : "NULL";$
19       break;$
20     case "double":$
21       $theValue = ($theValue != "") ? doubleval($theValue) : "NULL";$
22       break;$
23     case "date":$
24       $theValue = ($theValue != "") ? "'" . $theValue . "'" : "NULL";$
25       break;$
26     case "defined":$
27       $theValue = ($theValue != "") ? $theDefinedValue : $theNotDefinedValue;$
28       break;$
29   }$
30   return $theValue;$
31 }$
32 }$
33 $
34 $
35 $uname="guest";$
36 $uname_id = '1' ;$
37 $pt="pictures";$
38 $picPath="pt/img_0.gif"; $
39 $picSize="1024";$

40 $
41 $editFormAction = $_SERVER['PHP_SELF'];$
42 if (isset($_SERVER['QUERY_STRING'])) {$
43   $editFormAction .= "?" . htmlentities($_SERVER['QUERY_STRING']);$
44 }$
45 $
46 if ((isset($_POST["MM_insert"])) && ($_POST["MM_insert"] == "form1")) {$
47 $
48 $insertSQL_0 = sprintf("INSERT INTO album (album_id, album_nm, album_dt, album_pt) VALUES ( %s, %s, curdate(), '$pt')",$
49                        GetSQLValueString($_POST['album_id'], "int"),$
50                        GetSQLValueString($_POST['album_nm'], "text"),$
51                        GetSQLValueString($_POST['album_dt'], "date"),$
52                        GetSQLValueString($_POST['album_pt'], "text"));$
53 $
54 $insertSQL_1 = sprintf("insert into album_has_user (album_album_id, user_user_id, user_admin_id) values (last_insert_id(), '$uname_id', '$uname_id')",$
55 GetSQLValueString($_POST['album_has_user'], "int"),$
56 GetSQLValueString($_POST['user_user_id'], "int"),$
57 GetSQLValueString($_POST['user_admin_id'], "int"),$
58 $
59 $insertSQL_2 = sprintf("insert into title (title_id, title_title, title_dt, album_album_id, title_memo) values (last_insert_id(), %s, curdate(), last_ins    ert_id(), %s)",$
60 GetSQLValueString($_POST['title_id'], "int"),$
61 GetSQLValueString($_POST['title_title'], "text"),$
62 GetSQLValueString($_POST['title_dt'], "date"),$
63 GetSQLValueString($_POST['album_album_id'], "int"),$
64 GetSQLValueString($_POST['title_memo'], "text"));$
65 $
66 $
67 $insertSQL_3 = sprintf("insert into picture (picture_id, picture_dp, picture_sz, picture_df, title_title_id) values  (last_insert_id(), '$picPath', '$pic    Size', 'N', last_insert_id())", $
68 GetSQLValueString($_POST['picture_id'], "int"),$
69 GetSQLValueString($_POST['picture_dp'], "text"),$
70 GetSQLValueString($_POST['picture_sz'], "text"),$
71 GetSQLValueString($_POST['picture_df'], "text"),$
72 GetSQLValueString($_POST['title_title_id'], "int"));$
73 $
74 echo $_POST['title_title'];

75 $
76 //insert users album if null$
77   mysql_select_db($database_upics, $upics);$
78   $Result1 = mysql_query($insertSQL_0, $upics) or die(mysql_error());$
79 $
80 //insert users many data$
81   mysql_select_db($database_upics, $upics);$
82   $Result2 = mysql_query($insertSQL_1, $upics) or die(mysql_error());$
83   $
84 //insert users title and comments  $
85   mysql_select_db($database_upics, $upics);$
86   $Result3 = mysql_query($insertSQL_2, $upics) or die(mysql_error());$
87   $
88 //insert users picuter path$
89   mysql_select_db($database_upics, $upics);$
90   $Result4 = mysql_query($insertSQL_3, $upics) or die(mysql_error());  $
91 $
92   $insertGoTo = "picture_edit.php";$
93   if (isset($_SERVER['QUERY_STRING'])) {$
94     $insertGoTo .= (strpos($insertGoTo, '?')) ? "&" : "?";$
95     $insertGoTo .= $_SERVER['QUERY_STRING'];$
96   }$
97   header(sprintf("Location: %s", $insertGoTo));$
98 }$
99 ?>$
100 <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">$
101 <html xmlns="http://www.w3.org/1999/xhtml">$
102 <head>$
103 <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />$
104 <title>Untitled Document</title>$
105 </head>$
106 $
107 <body>$
108 <form action="<?php echo $editFormAction; ?>" method="post" name="form1" id="form1">$
109   <table align="center">$
110     <tr valign="baseline">$
111       <td nowrap="nowrap" align="right">Album Name:</td>$
112       <td><input type="text" name="album_nm"  id="album_nm" value="default" size="32" /></td>$
113     </tr>$

114     <tr valign="baseline">$
115     <td nowrap="nowrap" align="center">Title:</td>$
116     <td><input name="title_title" id="title_title" type="text" value="" size="32" /></td>$
117     </tr>$
118     <tr valign="baseline">$
119     <td nowrap="nowrap" align="center">Date:</td>$
120     <td><input name="title_dt" id="title_dt" type="text" value="" size="32" /></td>$
121     </tr>$
122     <tr valign="baseline">$
123     <td nowrap="nowrap" align="center">Comments:</td>$
124     <td><textarea name="title_memo" cols="32" id="title_memo"></textarea></td>$
125     </tr>$
126     <tr valign="baseline">$
127       <td nowrap="nowrap" align="right"> </td>$
128       <td><input type="submit" value="Insert record" /></td>$
129     </tr>$
130   </table>$
131   <input type="hidden" name="album_id" value="" />$
132   <input type="hidden" name="album_dt" value="" />$
133   <input type="hidden" name="album_pt" value="" />$
134   <input type="hidden" name="MM_insert" value="form1" />$
135 </form>$
136 <p> </p>$
137 </body>$
138 </html>$

```this is echo:    this is the error:

default           Column 'title' cannot be null

it says that the string cannot be null?

where do i go from here for debugging?

 thanks, in advance for your help!

theo werntz ii

---

### Post by wrtpeeps on 2009-08-01
It's mysql saying that the table in question has a rule that the title column can't be null.

I think.

---

### Post by wizardry on 2009-08-01
yes it is mysql that has the not null definition.

please re-read the post.

i'm trying to debug why my data isn't being inserted into the database.

debuggin that i've tried so far:

1. manually put the data in the insert string 
  
this method works fine.

2. using the form to enter data into the insert statement.

this method errors out saying that the title string is null along with comments.

debug step 2. echo the $_Post ['title'] and the string was their but not being inserted into the database.

how else can i debug the php app to determine why its not being inserted.

thanks again for any help.

theo werntz ii

---

### Post by Mirge on 2009-08-01
Where are you using $_POST['title'] ? I don't see it anywhere in the code. What line # is erroring?

---

### Post by wizardry on 2009-08-01
this is the mysql insert.

61 GetSQLValueString($_POST['title_title'], "text"),$

it errors here as well if i manually insert the string in line 61.

64 GetSQLValueString($_POST['title_memo'], "text"));$

here is my checking that the element was captured by php.
74 echo $_POST['title_title'];

I dont know if it is the html form or what. but the field element is
being captured according to debug line 74. I dont understand y its not
inserting.


here is the table definition:
 1 -- -----------------------------------------------------$
  2 -- Table `title`$
  3 -- -----------------------------------------------------$
  4 DROP TABLE IF EXISTS 'title` ;$
  5 $
  6 SHOW WARNINGS;$
  7 CREATE  TABLE IF NOT EXISTS `title` ($
  8   `title_id` BIGINT(20) UNSIGNED NOT NULL AUTO_INCREMENT COMMENT 'picture ti    tle id' ,$
  9   `title` VARCHAR(255) NOT NULL COMMENT 'picture title' ,$
 10   `dt` DATE NOT NULL COMMENT 'date of picture' ,$
      `title` VARCHAR(255) NOT NULL COMMENT 'picture comment' ,
 11   `album_id` BIGINT(20) UNSIGNED NOT NULL ,$
 12   PRIMARY KEY (`title_id`, `album_id`) ,$
 13   CONSTRAINT `fk_album_id`$
 14     FOREIGN KEY (`album_id` )$
 15     REFERENCES `album` (`album_id` )$
 16     ON DELETE CASCADE$
 17     ON UPDATE CASCADE)$
 18 ENGINE = InnoDB$
 19 AUTO_INCREMENT = 1$
 20 COMMENT = 'picture title schema';$

thanks in advance for your help

theo werntz ii

---


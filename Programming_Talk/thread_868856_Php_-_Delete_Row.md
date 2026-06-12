---
title: "Php - Delete Row"
date: 2008-07-24
forum: Programming Talk
---

### Post by Dj-Dark-1 on 2008-07-24
Yeahh very basic question here, normally i am ok with php but im struggling with a part for this site i am making.

First i have made like a news page and admins can add news to a database through the admin section which works fine. Now i make the  home page display the newest five news in which i just limit the query and order by DESC.

Now i have made a feature, where if you were an admin you can see a delete option to delete the news id instead of manually through phpmyadmin. But when i press delete, it deletes the oldest out of the 5 posts on the page and not the one i click. Here is part of my code for this page.

[PHP]
mysql_select_db("MyDatabase");
$result = mysql_query("select * from updates ORDER BY id DESC LIMIT 0, 5"); 
while($r=mysql_fetch_array($result))
{	

   $id=$r["id"];
   $username=$r["username"];
   $uname=$r["uname"];
   $uinfo=$r["uinfo"];
   $upicture=$r["upicture"];
   $ip=$r["ip"];
   $date=$r["date"];

   $action = $_GET['act'];
?>
</div>
<div class="text_block">
              <div class="image"><img src="<? echo"$upicture"; ?>" width=\"250\" height=\"130\"/></div>
                <div class="text">
                  <font size="2"><h1 class="green"><? echo "$uname"; ?></h1>
                  <p><? echo "$uinfo"; ?></p><br />
                  <p><? echo "News id : $id"; ?>
                  <br />Posted By <? echo "<a href=\"userpage.php?user=$username\">$username</a>, $date. ";             
                  if($session->isAdmin()){ 
                  echo "[<a href=\"?act=delete\">Delete</a>]";
                  }
                  } 
                  ?>
                  </p>
                </div>
                </font>
            </div>
<?
if($action == "delete"){
$sql = "DELETE FROM `updates` WHERE `id` = $id LIMIT 1";
$res = mysql_query($sql) or die(mysql_error());
}
?>
[/PHP]

Can anyone help me, just delete the id which i pressed delete for and not the oldest one.

Thanks, Dj-Dark-1

---

### Post by henchman on 2008-07-25
Well you don't supply an id for the message to be deleted:

```
echo "[<a href=\"?act=delete\">Delete</a>]";
```

So what you do is delete the message with id $id and this variable is set in your while loop:

```
$result = mysql_query("select * from updates ORDER BY id DESC LIMIT 0, 5"); 
while($r=mysql_fetch_array($result))
{    
   $id=$r["id"];
   [...]
}
```

so that the variable $id is being set to the id of the last of the 5 messages in the last (5th) run of the loop...

what you have to do is supply an id to be deleted, eg:

```
echo "[<a href=\"?act=delete&deleteId=".$id."\">Delete</a>]";
```

and then do:

```

$action = $_GET['act'];
if($action == "delete"){
$sql = "DELETE FROM `updates` WHERE `id` = " . $_GET['deleteId'] . " LIMIT 1";
$res = mysql_query($sql) or die(mysql_error());
}
```

you should also put your delete code on top of the SELECT query, because otherwise it is printed out again for the first visit.

you should also consider checking all user input variables for invalid data, eg. use mysql_real_escape_string for strings and 

```
if( !isset( $_GET['deleteId'] ) || strval( intval( $_GET['deleteId'] ) ) !== $_GET['deleteId'] )
{
    // tell the user not to cheat ;)
} 
```

for integer variables...

hf :)

---


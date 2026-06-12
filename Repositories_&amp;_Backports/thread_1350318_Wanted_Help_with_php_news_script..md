---
title: "Wanted: Help with php news script."
date: 2009-12-09
forum: Repositories &amp; Backports
---

### Post by shakabra on 2009-12-09
I am building a website for a friend [http://tattoosbylaura.com]("http://tattoosbylaura.com"). I am looking for a way to allow my friend to add content to the "news" div on the homepage using php. As of now I have to manually edit the html when she wants to add something. She doesn't have much content so I didn't want to use MySQL (and I'm not very familiar with MySQL). Everything I find on google is overkill. I don't need a full blown CMS. I just need to add new content to the "news" div preferably with some kind of form. Can anyone please point me in the right direction?

P.S. tattoosbylaura.com is currently being forwarded to [http://dakinewebs.com/lauranayl]("http://dakinewebs.com/lauranayl") . If you go there you will be able to see the source w/out those frames.

---

### Post by Genius2999 on 2009-12-09
You could try using CuteNews ([http://cutephp.com/](http://cutephp.com/))..... easily customizable but make sure you remove the search.php file, mainly as I believe there to be an exploit within it.

---

### Post by shakabra on 2009-12-09
I've seen this before, but I want something smaller I don't need any other features. However I will take another look at this thanks.

---

### Post by Johnsie on 2009-12-09
if you're looking for a ready made solution check out [http://php.resourceindex.com/Complete_Scripts/News_Posting/](http://php.resourceindex.com/Complete_Scripts/News_Posting/)

However, if you know php and mysql or just php then it's pretty easy to make your own.

Just have a table record for each news entry.

---

### Post by shakabra on 2009-12-09
Thanks for the pointers. This is exactly was I was looking for. I just needed some direction.

---

### Post by madnessjack on 2009-12-09
I've used this before [http://snewscms.com/](http://snewscms.com/)

Did the job very well :)

---

### Post by Frant on 2010-02-19
I have found one. According to [php tutorials]("http://phpforms.net/tutorial/tutorial.html") it must work. 

News.php
[PHP]<? 


@$db=mysql_connect('localhost','user DB','password DB'); 
mysql_select_db('database name'); 

$per_page=10; 

@$action=$_GET['action']; 
@$id=$_GET['id']; 

if  (!$id &&  $action){ 

if  (isset($_GET['page'])) $page=($_GET['page']-1); else $page=0; 
$start=abs($page*$per_page); 
$q="SELECT  count(*) FROM `news`"; 
$res=mysql_query($q); 
$row=mysql_fetch_row($res); 
$total_rows=$row[0]; 
$num_pages=ceil($total_rows/$per_page); 

echo  '<h1>news projects</h1>'; 
$sql="SELECT * FROM `news` ORDER BY `id`  DESC LIMIT ".($page*$per_page).",".$per_page; 
$result=mysql_query($sql); 
$num_results=mysql_num_rows($result); 
for ($i=0; $i<$num_results; $i++) 
    { 
    $row=mysql_fetch_array($result); 

    $id=$row["id"]; 
    $author=$row["author"]; 
    $date=$row["date"]; 
    $tema=$row["tema"];     
    $text=$row["text"]; 

    echo '<b>'.$tema.'</b><br> 

    <a href="/news/'.$id.'/">added</a>:  <b>'.$author.'</b> 

('.$date.')<p> '.$text.'  <hr>'; 
    } 
     
for($i=1;$i<=$num_pages;$i++) { 
  if ($i-1  == $page) { 
    echo 

"[".(abs($i*$per_page)-$per_page+1)." -  ".abs($i*$per_page)."]  ";  
  } 
  else { 
    echo '[<a  

href="news.php?action=all&page='.$i.'">'.(abs($i*$per_page)-$per_page+1)." - ".ab 

s($i*$per_page)."</a>]  "; 
  } 
}     
     
} 

if (!$action && !$id){ 

$sql="SELECT  * FROM `news` ORDER BY `id` DESC LIMIT 0,10";  
$result=mysql_query($sql); 
$num_results=mysql_num_rows($result); 

for ($i=0; $i<$num_results; $i++) 
    { 
    $row=mysql_fetch_array($result); 
    $id=$row["id"]; 
    $author=$row["author"]; 
    $date=$row["date"]; 
    $tema=$row["tema"]; 
    echo '('.$date.')  <a href="news.php?id='.$id.'">'.$tema.'</a><p>'; 
    }      
} 


if (!$action && $id){ 

$sql="SELECT * FROM `news` WHERE  `id`=".$id; 
$result=mysql_query($sql);  

    $row=mysql_fetch_array($result);  
    $id=stripslashes($row["id"]; 
    $author=$row["author"]; 
    $date=$row["date"]; 
    $text=$row["text"]; 
    $tema= $row["tema"]; 
    echo '<h1>'.$tema.'</h1> 

    added: <b>'.$author.'</b> ('.$date.')<p> '.$text.' <p> 
    <a  href="news.php?action=all">&#8592; return to news</a>'; 
} 

?>  [/PHP]But before you need create a table "news" and then create an admin part of the code
news-admin.php

---

### Post by cariboo on 2010-02-19
This is not  Cafe thread. Moved

---


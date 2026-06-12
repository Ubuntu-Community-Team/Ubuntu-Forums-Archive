---
title: "a php code example that shows a pagination similar to google"
date: 2011-01-22
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-22
I gleaned this from that web site
[http://www.phpbuilder.com/board/showthread.php?t=10353797](http://www.phpbuilder.com/board/showthread.php?t=10353797)

I had to go thru the code to rework it too make it work.
These code examples often posted just dont work without a lot of thinking and tinkering into what is going on.

Anyway, it should work for you if you change the database connections and the two mysql  queries
and name this file paging3.php

I came across a lot of schemes and this one I got to work and looks nice.
If you can think of improvements, be nice to share them?

(I would like to hyperlink the titles that are printed out to send a user to a new page that enhances the data, just like clicking off a google search.) 

```
<?php
//http://www.phpbuilder.com/board/showthread.php?t=10353797
$host = "localhost";
$user = "root";
$pass = "New";
$db = "booksgood";

// open connection
$connection = mysql_connect($host, $user, $pass) or die ("Unable to connect!");
   
// select database
mysql_select_db($db) or die ("Unable to select database!"); 

// how many rows to show per page
$rowsPerPage = 10;

// by default we show first page
$page_num = 1;

// if $_GET['page'] defined, use it as page number, $_GET gets the page number out of the url
//set by the $page_pagination below
if(isset($_GET['page'])){$page_num = $_GET['page'];}

//the point to start for the limit query
$offset = $page_num; 

// Zero is an incorrect page, so switch the zero with 1, mainly because it will cause an error with the SQL
if($page_num == 0) {$page_num = 1;}

// counting the offset
$sql = "SELECT * FROM bookdata where titles like 's%' order by titles LIMIT $offset, $rowsPerPage ";
$res = mysql_query($sql) or die(mysql_error());

// how many rows we have in database
$sql2  = "SELECT COUNT(id) AS numrows FROM bookdata where titles like 's%'";
$res2  = mysql_query($sql2) or die(mysql_error());
$row2  = mysql_fetch_array($res2);
$numrows = $row2['numrows'];

// print the random numbers
while($row = mysql_fetch_array($res))
{
//Echo out your table contents here.

echo $row[1].'<BR>';
echo $row[2].'<BR>';
echo '<BR>';
}

// how many pages we have when using paging?
$numofpages = ceil($numrows/$rowsPerPage);

// print the link to access each page
$self = "/paging3.php?";

if ($numofpages > '1' ) {

            $range =15; //set this to what ever range you want to show in the pagination link
            $range_min = ($range % 2 == 0) ? ($range / 2) - 1 : ($range - 1) / 2;
            $range_max = ($range % 2 == 0) ? $range_min + 1 : $range_min;
            $page_min = $page_num- $range_min;
            $page_max = $page_num+ $range_max;

            $page_min = ($page_min < 1) ? 1 : $page_min;
            $page_max = ($page_max < ($page_min + $range - 1)) ? $page_min + $range - 1 : $page_max;
            if ($page_max > $numofpages) {
                $page_min = ($page_min > 1) ? $numofpages - $range + 1 : 1;
                $page_max = $numofpages;
            }

            $page_min = ($page_min < 1) ? 1 : $page_min;

            //$page_content .= '<p class="menuPage">';

            if ( ($page_num > ($range - $range_min)) && ($numofpages > $range) ) {
                $page_pagination .= '<a class="num"  title="First" href="'.$self.'page=1">&lt;</a> ';
            }

            if ($page_num != 1) {
                $page_pagination .= '<a class="num" href="'.$self.'page='.($page_num-1). '">Previous</a> ';
            }

            for ($i = $page_min;$i <= $page_max;$i++) {
                if ($i == $page_num)
                $page_pagination .= '<span class="num"><strong>' . $i . '</strong></span> ';
                else
                $page_pagination.= '<a class="num" href="'.$self.'page='.$i. '">'.$i.'</a> ';
            }

            if ($page_num < $numofpages) {
                $page_pagination.= ' <a class="num" href="'.$self.'page='.($page_num + 1) . '">Next</a>';
            }


            if (($page_num< ($numofpages - $range_max)) && ($numofpages > $range)) {
                $page_pagination .= ' <a class="num" title="Last" href="'.$self.'page='.$numofpages. '">&gt;</a> ';
            }
            
            //$page['PAGINATION'] ='<p id="pagination">'.$page_pagination.'</p>';
        }//end if more than 1 page 

echo $page_pagination.'<BR><BR>';

echo 'Number of results - '.$numrows ;
echo ' and Number of pages   - '.$numofpages.'<BR><BR>';

// Free resultset
mysql_free_result($res);

// and close the database connection
mysql_close($con); 

?>
```

---

### Post by ahieezer on 2012-10-12
Really Good Script working successfully For me...

---

### Post by lampels11 on 2013-04-16
Sir,
I am beginners in PHP, I was not able to call the function only, I have pasted the code in my function where i have other functions too. When i call the function from my index.php (i have search.php), its displaying blank page. Please any help would be greateful... Thanks

---

### Post by VinylSurrender on 2013-06-05
Hi,
Thanks for the post and the script. I've managed to get it working and it pulls the rows from my tables as per the contents of my query.

There is however a minor issue. Can you help me?

The first row of the table is not displayed, only the second, third, fourth row, etc.

There is a line in the code that states:
[PHP]
// by default we show first page
$page_num = 1;
[/PHP]

And further down:
[PHP]
// Zero is an incorrect page, so switch the zero with 1, mainly because it will cause an error with the SQL
if($page_num == 0) {$page_num = 1;}
[/PHP]

The variable $page_num needs to be set to 0 in order to view the first row from the table, but by changing it to 0 it causes problems with the code.

What can I do? I need to view that first row from my table, or the first row that my query specifies, not just the second row and beyond.

If anyone's got any tips or thoughts on this I would appreciate your input, thanks.

Richard

---

### Post by zobayer1 on 2013-06-05
> **VinylSurrender said:**
> 
The variable $page_num needs to be set to 0 in order to view the first row from the table, but by changing it to 0 it causes problems with the code.

What can I do? I need to view that first row from my table, or the first row that my query specifies, not just the second row and beyond.

If anyone's got any tips or thoughts on this I would appreciate your input, thanks.

Richard

I think the problem can be caused from here
[php]
//the point to start for the limit query
$offset = $page_num;
// Zero is an incorrect page, so switch the zero with 1, mainly because it will cause an error with the SQL
if($page_num == 0) {$page_num = 1;}
[/php]

$offset is used as an argument for LIMIT, but it is initialized by the page number, shouldn't it be
[php]
$offset = $page_num * $rowsPerPage
[/php]

And yes, with a little tweak, you can use $page_num starting from 0, as it makes the whole process more general.

---


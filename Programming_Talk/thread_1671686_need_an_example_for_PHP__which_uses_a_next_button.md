---
title: "need an example for PHP  which uses a next button"
date: 2011-01-20
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-20
I am just starting out in PHP
say your displaying some mysql data.
I know how to dump all the data in a table from a select query

BUT say I want to just show a single row at a time with a next button 
When the next button is pressed, it displays the next row.

can anyone post some a quick code example that would show how this is done?

---

### Post by Wtower on 2011-01-20
Hi sdowney717,

I will use the basic php example for mysql as shown on php.net, modified for your needs. The idea is that you need to pass an argument with the current record id. There are other ways to achieve this as well, for example to store session-state data on the php session or the database, we can get to that later. Haven't tested the example (I am on the go now).

[PHP]
  <?php
// Connecting, selecting database
$link = mysql_connect('mysql_host', 'mysql_user', 'mysql_password')
    or die('Could not connect: ' . mysql_error());
echo 'Connected successfully';
mysql_select_db('my_database') or die('Could not select database');

// Performing SQL query
$query = 'SELECT * FROM my_table';
$result = mysql_query($query) or die('Query failed: ' . mysql_error());

// Find row
$line = mysql_fetch_array($result, MYSQL_BOTH);
if (isset($_GET['id'])) { 
   do {
      if ($line[0] == $_GET['id']) break; // we assume col [0] is id
   } while ($line = mysql_fetch_array($result, MYSQL_BOTH));
}

// Printing results in HTML
if ($line) { 
       echo "<table>\n";
   echo "\t<tr>\n";
   foreach ($line as $col_value) {
       echo "\t\t<td>$col_value</td>\n";
   }
   echo "\t</tr>\n";
   echo "</table>\n";
}
else echo "Record not found.\n";

// Provide a link with the next row
$line = mysql_fetch_array($result, MYSQL_BOTH);
if ($line) echo "<a href=\"page.php?id=".$line[0]."\">Next Row</a>\n";
 else echo "End of set."; 
    
// Free resultset
mysql_free_result($result);

// Closing connection
mysql_close($link);
?>      [/PHP]

---

### Post by sdowney717 on 2011-01-20
thanks, I got it to display pages, I named it page.php

So, does this line
if ($line) echo "<a href=\"page.php?id=".$line[0]."\">Next Row</a>\n";

when click the next row link, reload this entire php file?
so it redoes the select statement every time?
how is line[0] array value incrementing?

---

### Post by sdowney717 on 2011-01-20
ok, I think what it does is set a value to id
which the form then gets with 

> if (isset($_GET['id'])) 

so it is not redoing the query over and over.

so how to create a previous link?

What I am still thinking of how to do this is this way.
do the query and collect the id numbers into an array
then every time you hit next, get the next sequential value  of the array.
then every time you hit previous, get the previous element in the array.

select * from table where id = array value' type of idea. And you cant go past the array boundaries.

---

### Post by Wtower on 2011-01-20
> **sdowney717 said:**
> when click the next row link, reload this entire php file?
so it redoes the select statement every time?

Exactly. I do not necessarily agree with this, but my understanding from what I have read is that there is no other way eg as with asp. Of course any other advice from the community is welcome. On the other hand, I find that the performance overhead for the select is not bad. The biggest lag is with mysql_connect, and for this reason there is a persistent connection alternative with mysql_pconnect: [http://php.net/manual/en/function.mysql-pconnect.php](http://php.net/manual/en/function.mysql-pconnect.php)

Because the php file reruns, explains why that if-conditional is there, checking whether a url parameter named id exists.

> **sdowney717 said:**
> how is line[0] array value incrementing? 	

Since we used [COLOR=#000000][COLOR=#0000BB]$line [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]mysql_fetch_array[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]$result[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]MYSQL_BOTH[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]
we instructed mysql to return a php array which indexes are both numeric and associative. In plain english, if your table record has two fields named id and descr, then $line[0] == $line['id'] and $line[1] == $line['descr']. Of course, the value of the id field changes as we fetch each record and it depends on the table sorting. Therefore, if the id field is autoincrement and the select query ordered, then we can relatively safely assume that the values are like 1, 2, 3 etc. (unless there has been some deletions or messing around).

More on fetch: [http://php.net/manual/en/function.mysql-fetch-array.php](http://php.net/manual/en/function.mysql-fetch-array.php)

---

### Post by Wtower on 2011-01-20
> **sdowney717 said:**
> ok, I think what it does is set a value to id
which the form then gets with 



so it is not redoing the query over and over.

so how to create a previous link?

What I am still thinking of how to do this is this way.
do the query and collect the id numbers into an array
then every time you hit next, get the next sequential value  of the array.
then every time you hit previous, get the previous element in the array.

select * from table where id = array value' type of idea. And you cant go past the array boundaries.

Yeah, then something like this:

[PHP] 
<?php
// Connecting, selecting database
$link = mysql_connect('mysql_host', 'mysql_user', 'mysql_password')
    or die('Could not connect: ' . mysql_error());
echo 'Connected successfully';
mysql_select_db('my_database') or die('Could not select database');

// Performing SQL query
$query = 'SELECT * FROM my_table';
$result = mysql_query($query) or die('Query failed: ' . mysql_error());

// Find row
$line = mysql_fetch_array($result, MYSQL_BOTH);
if (!$line) die('Empty table'); // This is new here
$previd = -1;
$currid = $line[0];
 if (isset($_GET['id'])) { 
   do {
           $currid = $line[0];
      if ($currid == $_GET['id']) break; // we assume col [0] is id
      $previd = $currid;
           $line = mysql_fetch_array($result, MYSQL_BOTH);
   } while ($line);
}

// Printing results in HTML
if ($line) { 
       echo "<table>\n";
   echo "\t<tr>\n";
   foreach ($line as $col_value) {
       echo "\t\t<td>$col_value</td>\n";
   }
   echo "\t</tr>\n";
   echo "</table>\n";
}
else echo "Record not found.\n";

// Provide a link for the prev row
if ($previd > -1) echo "<a href=\"page.php?id=$previd\">Next Row</a>\n";
 else echo "(Begin of set)"; 
    
// Provide a link for the next row
$line = mysql_fetch_array($result, MYSQL_BOTH);
if ($line) echo "<a href=\"page.php?id=".$line[0]."\">Next Row</a>\n";
 else echo "(End of set)"; 
    
// Free resultset
mysql_free_result($result);

// Closing connection
mysql_close($link);
?>
[/PHP]

---

### Post by Wtower on 2011-01-20
---

---

### Post by sdowney717 on 2011-01-20
> 
// Performing SQL query
$query = 'SELECT id FROM bookdata order by titles';
$result = mysql_query($query) or die('Query failed: ' . mysql_error());
//echo (mysql_num_rows($result));
$incr1 = 0;
while ($incr1 <= mysql_num_rows($result)) {   
   $id = mysql_fetch_row($result); //get first row data 
   echo $id[$incr1].'<BR>';
   echo $incr1.'<BR>';
   $incr1=($incr1+1);
   }

how would you load data into an array from the select query?
here I am selecting idnumber and was thinking to put it in an array.
It does not work. 
Can you tell me why?

---

### Post by sdowney717 on 2011-01-20
> 
// Performing SQL query
$query = 'SELECT id FROM bookdata order by titles';
$result = mysql_query($query) or die('Query failed: ' . mysql_error());
//echo (mysql_num_rows($result));
$incr1 = 0;
while ($incr1 <= mysql_num_rows($result)) {   
   $id = mysql_fetch_row($result); //get first row data 
   echo $id[$incr1].'<BR>';
   echo $incr1.'<BR>';
   $incr1=($incr1+1);
   }

how would you load data into an array from the select query?
here I am selecting idnumber and was thinking to put it in an array.
It does not work. 
Can you tell me why?

---

### Post by Wtower on 2011-01-21
Right. What strikes me is that mysql_fetch_row returns a numeric array containing all field values for the row.

[http://php.net/manual/en/function.mysql-fetch-row.php](http://php.net/manual/en/function.mysql-fetch-row.php)

Meaning that $id is actually an array with all field values, and $id[0] is field 1 value. Therefore the $id name is a bit misleading. Alternatively, you can use mysql_fetch_assoc to get an associative array wjich you could access like $id['id'].

Also, instead of $incr=($incr+1); you can simply type $incr++; as in the classic c++ syntax.

[http://php.net/manual/en/language.operators.increment.php](http://php.net/manual/en/language.operators.increment.php)

---

### Post by sdowney717 on 2011-01-21
finally got what I want .
as an example run this and click button 1
it displays and incrementing number every time the button is clicked.
I tried those increment functions, global but the form wont remember where it is when it reloads. So put the counter in a hidden field and get the value using

$a =  ($_POST['counter']);

funny thing is that arrays are remembered after the form is done
I finally got the array to store the id numbers from a query.

```
//load an array of idnumbers
$query = 'SELECT id FROM bookdata order by titles';
$result = mysql_query($query) or die('Query failed: ' . mysql_error());
echo 'results::'.mysql_num_rows($result).'<BR><BR>';
$incr1 = 0;
while ($incr1 <= mysql_num_rows($result)) {   
   $id = mysql_fetch_row($result); //get first row data 
   $idnum[$incr1]= $id[0];
 //  echo $idnum[$incr1].'<BR>';
 //  echo $incr1.'<BR>';
 //  echo $idnum[0].'<BR>';
   $incr1=($incr1+1);
   }
``` 

save it as "increment.php"
click button 1
watch it increment the number

```
<?php
//http://www.phpfreaks.com/forums/php-coding-help/create-a-counter-variable-that-increments-when-submit-button-is-pressed/

$a = 0;
if (!empty($_POST['button'])){
      switch ($_POST['button']){
        case 'button1':
          $a =  ($_POST['counter']);
          
          echo  'time '.time().'<BR>';
 
        //  echo 'increment number '.$inc.'<BR>';
          
       //   echo $f.'<BR>';
       //   echo 'increment number '.$f.'<BR>';

        //   $inc = sum();
       //   echo 'increment number '.$inc.'<BR>';
          echo "pushed button 1".'<BR>';
         
          //echo $inc; 
          //echo $inc;
          $q= "select titles, author from bookdata where id = '$a'";    
          echo "$q".'<BR>';
          $a=$a+1;
        break;
        case 'button2':
            echo "pushed button 2".'<BR>';
        break;
        case 'button3':
            echo "pushed button 3".'<BR>';
        break;
       

        default:
            echo "????/".'<BR>';            
        break;
      }
     }
 else
 { 
 //$inc = 0;
 }

?>


<form action="increment.php" method="post">
    <div>
    <input type="submit" name="submit" value="submit"/>
    <button type="submit" name="button" value="button1">Button 1</button>
    <button type="submit" name="button" value="button2">Button 2</button>
    <button type="submit" name="button" value="button3">Button 3</button>
    <input type="hidden" name="counter" value="<?php print $a; ?>" />  
    </div>
    </form>

<?php

function sumc($xa)
{
  global $xa;
 
  $xa = $xa + 1;
} 

function sub(&$value, $amount =1)
{
  $value= $$value - $amount;
} 

function sum() {
     static $a ;
     $a = $a + 1;
    // echo $c . "<br />\n";
    }

    add();
    add();
    add();
    add();
    $c= add();
echo "select $c";

```

---

### Post by Wtower on 2011-01-21
Cool \\:D/

---

### Post by sdowney717 on 2011-01-21
another example, here it is more cleaned up, shows previous, next, first, last button
moving thru a record set one by one.

call it page2.php

It shows how arrays are kept even when the form stops. Unlike a single variable. So I dont know but does the memory need to be destroyed for that array, otherwise does it create a memory leak?

```
<?php
// Connecting, selecting database
$link = mysql_connect('localhost', 'root', 'New') or die('Could not connect: ' . mysql_error());
echo 'Connected successfully<BR><BR>';

mysql_select_db('booksgood') or die('Could not select database');


//load an array of idnumbers
//$query = 'SELECT id FROM bookdata order by titles';
//$query = 'SELECT id FROM bookdata where id = '5' order by titles';
//$query = "SELECT id FROM bookdata where id <> '' ";
$query = "SELECT id FROM bookdata where titles like '%*science%'";
$query = "SELECT id  FROM bookdata where titles like '%science general%' order by titles";
$query = "SELECT id  FROM bookdata where titles like '%candle%' order by titles";
//$query = "SELECT id FROM bookdata where id not like '' ";

//$query = "SELECT id FROM bookdata where id <> '' ";

//$query = "SELECT id FROM bookdata where id <> '' order by titles";

echo $query.'<BR>';
$result = mysql_query($query) or die('Query failed: ' . mysql_error());
echo 'results::'.mysql_num_rows($result).'<BR><BR>';

$incr1 = 0;
while ($incr1 < mysql_num_rows($result)) {   
   $id = mysql_fetch_row($result); //get first row data 
   $idnum[$incr1]= $id[0];
 //  echo $id[0].'<BR>';
 //  echo $idnum[$incr1].'<BR>';
 //  echo $incr1.'<BR>';
 //  echo $idnum[0].'<BR>';
   $incr1=($incr1+1);
   }
   echo 'count array - '.count($idnum).'<BR>';
 //  echo $idnum[0].'<BR>';
 //  echo $idnum[1].'<BR>';

$incr1=($incr1-1);
//$column = mysql_fetch_row($result)
// Find row
//$line = mysql_fetch_array($result, MYSQL_BOTH);

//selects first row into array
//$line = mysql_fetch_array($result);
// fetches next row $column = mysql_fetch_row($result);

    $q= "select titles, author from bookdata where id = '$idnum[0]'";    
    $result2 = mysql_query($q) or die('Query failed: ' . mysql_error());
    //selects first row 
    $line = mysql_fetch_array($result2);
    echo $line[0];
    echo '<BR><BR>test print<BR><BR>';

//if (isset($_GET['idp'])){ //if the value is set
//if (isset($_POST['button'])) { 
 if (!empty($_POST['button'])){
      switch ($_POST['button']){
        case 'button1':
          $counter =  ($_POST['counter']);
          echo  time();
          echo "pushed button 1".'<BR>';
          
          echo "0:".$idnum[0]."--"; 
          echo "1:".$idnum[1]."--"; 
          echo "2:".$idnum[2]."--"; 
          echo "3:".$idnum[3]."--"; 
          echo "4:".$idnum[4]."--"; 
          echo "5:".$idnum[5]."--"; 
          echo "6:".$idnum[6]."--"; 
          echo "7:".$idnum[7]."--";      
          echo "8:".$idnum[8]."--"; 
          echo "9:".$idnum[9]."--"; 
          echo '<BR> count - '.count($idnum).'<BR>';

          $counter = $counter +1;
          if ($counter > (count($idnum)-1)) { $counter = ((count($idnum)-1));}

          $q= "select titles, author from bookdata where id = '$idnum[$counter]'";             
          echo "$q".'<BR>';
          $result2 = mysql_query($q) or die('Query failed: ' . mysql_error());
 
        break;
        case 'button2':
          $counter =  ($_POST['counter']);
          echo  time();
          echo "pushed button 2".'<BR>';

          echo "0:".$idnum[0]."--"; 
          echo "1:".$idnum[1]."--"; 
          echo "2:".$idnum[2]."--"; 
          echo "3:".$idnum[3]."--"; 
          echo "4:".$idnum[4]."--"; 
          echo "5:".$idnum[5]."--"; 
          echo "6:".$idnum[6]."--"; 
          echo "7:".$idnum[7]."--";      
          echo "8:".$idnum[8]."--"; 
          echo "9:".$idnum[9]."--"; 
          echo '<BR> count - '.count($idnum).'<BR>';

          $counter = $counter -1;

          if ($counter < 0){ $counter =0;}
          $q= "select titles, author from bookdata where id = '$idnum[$counter]'";    
          echo "$q".'<BR>';
          $result2 = mysql_query($q) or die('Query failed: ' . mysql_error());
 
        break;
        case 'button3':
          // pressed first 
          $counter =  0;
          echo  time();
          echo "pushed button 3".'<BR>';

          echo "0:".$idnum[0]."--"; 
          echo "1:".$idnum[1]."--"; 
          echo "2:".$idnum[2]."--"; 
          echo "3:".$idnum[3]."--"; 
          echo "4:".$idnum[4]."--"; 
          echo "5:".$idnum[5]."--"; 
          echo "6:".$idnum[6]."--"; 
          echo "7:".$idnum[7]."--";      
          echo "8:".$idnum[8]."--"; 
          echo "9:".$idnum[9]."--"; 
          echo '<BR> count - '.count($idnum).'<BR>';

          $q= "select titles, author from bookdata where id = '$idnum[$counter]'";    
          echo "$q".'<BR>';
          $result2 = mysql_query($q) or die('Query failed: ' . mysql_error());

        break;
        case 'button4':
          //pressed last
          $counter =  (count($idnum)-1) ;
          echo  time();
          echo "pushed button 4".'<BR>';

          echo "0:".$idnum[0]."--"; 
          echo "1:".$idnum[1]."--"; 
          echo "2:".$idnum[2]."--"; 
          echo "3:".$idnum[3]."--"; 
          echo "4:".$idnum[4]."--"; 
          echo "5:".$idnum[5]."--"; 
          echo "6:".$idnum[6]."--"; 
          echo "7:".$idnum[7]."--";      
          echo "8:".$idnum[8]."--"; 
          echo "9:".$idnum[9]."--"; 
          echo '<BR> count - '.count($idnum).'<BR>';

          $q= "select titles, author from bookdata where id = '$idnum[$counter]'";    
          echo "$q".'<BR>';
          $result2 = mysql_query($q) or die('Query failed: ' . mysql_error());

        break;


        default:
            $yes = 'yes default';
        break;
      }
     }
 else
 { 
 //$inc = 0;
 }



// Printing results in HTML
if ($line) { 
   echo "<table>\n";
   echo "\t<tr>\n";
  // foreach ($line as $col_value) {
  //     echo "\t\t<td>$col_value</td>\n";   }
  $column = mysql_fetch_row($result2);
   echo "\t\t<td>$column[0]</td>\n";   
   echo "\t\t<td>$column[1]</td>\n";   
   
  // echo $line[0];
  // echo $line[1];
   echo "\t</tr>\n";
   echo "</table>\n";
}
else echo "Record not found.\n";


// else echo "End of set.";    



// Free resultset
mysql_free_result($result2);

// Closing connection
mysql_close($link);
?>


<form action="page2.php" method="post">
    <div>
    <button type="submit" name="button" value="button2">Previous</button>
    <button type="submit" name="button" value="button1">Next</button>
    <button type="submit" name="button" value="button3">First</button>
    <button type="submit" name="button" value="button4">Last</button>
    <input type="hidden" name="counter" value="<?php print $counter; ?>" /> 
    </div>
    </form>

<?php

?>

```

---

### Post by Wtower on 2011-01-21
Nice. In theory, there is a garbage collector that removes from memory any object is allocated when the last reference to that object is removed. There is no explicit destructor or deallocator in php afaik. In practice, I haven't discovered any memory anomalies so far. 

I maintain a considerably large web app that was ported from asp c# to php and the memory demands are far smaller (as expected..). This app is a business app and is like a hobby to me. I aim towards opening it public at some point in my life.

---

### Post by sdowney717 on 2011-01-21
Well I found out something silly.
I am very new at this.

When you 'run' the page, it always runs the whole page again?
so, I think it just regenerates that array, every time you click next, etc...

---

### Post by Wtower on 2011-01-21
Exactly. This is why, as I mentioned earlier, you need session data.

---

### Post by sdowney717 on 2011-01-21
I was able to create an mysearch.htm page that collects the data and a mysearch.php that works on it to display the info.
I put the search query in a hidden field so after the first time thru, when the variables are all zeroed out it uses the saved query.

It does regenerate the array, which is a waste of time, but still quick.
What could be done is store the search in the mysql database in a unique table keyed to the search string. like a table of id numbers.
Then do a test against a database update to see if the search would have to be redone, otherwise just keep using the same results  over and over when a user does an identical search.

or

what is this about session data?
I read a little on it. Can it store the array data and then how would that data be destroyed when it is no longer needed?

---

### Post by sdowney717 on 2011-01-21
I was thinking are there some free IDE for PHP?
One that perhaps will show syntax errors, and step thru as it run and show variable values?

I am using gedit and it is a big help, but I have to be so careful with syntax when I make changes, errors can easily got lost in the code.

---

### Post by Wtower on 2011-01-21
> **sdowney717 said:**
> I was able to create an mysearch.htm page that collects the data and a mysearch.php that works on it to display the info.
I put the search query in a hidden field so after the first time thru, when the variables are all zeroed out it uses the saved query.

It does regenerate the array, which is a waste of time, but still quick.
What could be done is store the search in the mysql database in a unique table keyed to the search string. like a table of id numbers.
Then do a test against a database update to see if the search would have to be redone, otherwise just keep using the same results  over and over when a user does an identical search.

or

what is this about session data?
I read a little on it. Can it store the array data and then how would that data be destroyed when it is no longer needed?

The only reason I can think of for storing the search results on a table is performance issues. How long does it take to produce the search results? If not significantly slow, then why bother to do so and not re-run the search again? Still, if you prefer this, then such a table would be available to any user from any ip address at any time in the future. In contrast, session data is about one user at a specific time of use. If that user closes the browser, logs out, times out etc then that particular data couldn't be reused.

How exactly sessions are implemented can be a long conversation. PHP sessions in the default Ubuntu installation if I remember well are by default enabled, based on temporary cookies that get removed when the user closes the browser. There is a place to store session data: $_SESSION. In the beggining of each file that you wish to enable sessions, you have to run session_start(). Then you can set any associative value as for example $_SESSION['myvar'] = 'something' and of course access it on will.

Then you can have something like a page:

[PHP]
session_start();
if (!isset($_SESSION['myvar'])) {
  if ((!isset($_POST['username']) && !isset($_POST['pass'])) || ($_POST['username']=='sdowney717' && $_POST['pass']=='mypass'))
    // here you present the login form with 2 fields named username and pass
  }
  else {
  $_SESSION['myvar'] = 'we have a login session!';
  // here you present data not available otherwise
  }
}
[/PHP]

If you wish to store in session data anything way too complicated that ie needs object modelling or whatever then you could associate a session id to a record containing any relevant information in a sessions mysql table.

---

### Post by Wtower on 2011-01-21
> **sdowney717 said:**
> I was thinking are there some free IDE for PHP?
One that perhaps will show syntax errors, and step thru as it run and show variable values?

I am using gedit and it is a big help, but I have to be so careful with syntax when I make changes, errors can easily got lost in the code.

I understand. I use eclipse and I have also tried geany. Eclipse is somehow heavy, it tells you about syntax errors, for geany I don't remember, only that is lighter. Both of them give you a directory structure and organize projects etc. As for proper debugging, things get a bit messy, especially if you test on remote server. Take a read at:

[http://www.ibm.com/developerworks/library/os-debug/](http://www.ibm.com/developerworks/library/os-debug/)

---

### Post by sdowney717 on 2011-01-21
> Still, if you prefer this, then such a table would be available to any user from any ip address at any time in the future. In contrast, session data is about one user at a specific time of use. If that user closes the browser, logs out, times out etc then that particular data couldn't be reused.

yes, sort of makes session data for that array not very useful.
you would want the database to hold that data in a table available to all users.
the search is very fast, fast enough not to be a real concern.
I am querying against ~10000 rows including text fields.

I imagine if the database was really large might improve the speed.

---

### Post by Wtower on 2011-01-22
Forgot to mention. You can use javascript to make asynchronous requests to the server, ie without need to reload the page. This is called ajax. A good framework for that and my personal preference is ExtJS: [http://www.sencha.com/products/js/](http://www.sencha.com/products/js/)

---


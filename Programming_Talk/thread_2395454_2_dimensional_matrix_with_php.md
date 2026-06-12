---
title: "2 dimensional matrix with php"
date: 2018-07-02
forum: Programming Talk
---

### Post by ELMIT on 2018-07-02
Forgive me, that I ask this here, ... I stuck on that problem to long and don't know anymore where to ask.

From a database I retrieve data
try {
 
        $conec = new Connection();
        $con   = $conec->Open();
        if ($con) {
 
            $sql = "SELECT * FROM tss WHERE ....";
            $re  = $con->query($sql);
            foreach ($con->query($sql) as $row) {
                $lastT[$i]['t_ex'] 	= $Mar = $row['t_ex'];
                $lastT[$i]['t_sy'] 	= $Co = $row['t_sy'];
                $lastT[$i]['t_ba'] = $Mat = $row['t_ba'];
                ...
                $i++;
            }
        } else {
            echo $con;
        }
    } catch (PDOException $ex) {
        echo $ex->getMessage();
    }

After fetching the data, I do some calculations add them to a temporary array and list the data as a row:

for ($x = 0; $x < $Tsize; $x++) {
        $temparray[0] = $lastT[$x]['Co'];
        $temparray[1] = $lastT[$x]['LA'];
        $temparray[2] = $lastT[$x]['HB'];
....
echo $x . " " . $temparray[0] . " " . $temparray[1] . " " . $temparray[2] . " " . $temparray[3] . " " . $temparray[4] . " " . $temparray[5] . " " . $temparray[6] . " " . $temparray[7] . " " . $temparray[8] . $line_break;
} // close for loop

Perfect listing, just as I want it. However, I need to sort the list by the 6th column ($temparray[5])
Easy, just put the data of that temparray into a 2 dimensional array with each row exactly and do a sort by that column. 

I feel like an idiot, I cannot get the data into a 2 dimensional array. Whatever I tried ended up to put the last temparray into the matrix as ONLY entry. 

Can you give me a hint?

---

### Post by Holger_Gehrke on 2018-07-02
Why put the data into an array and sort that array when you can tell the SQL-Server to sort it and get it in the right order from the beginning ? Simply add an 'ORDER BY field_name' subclause to your query.

Holger

---

### Post by ELMIT on 2018-07-02
"After fetching the data, I do some calculations add them to a temporary array and list the data as a row"   - Thats why. ;-)

The lines are not anymore the mysql data, these are only used in the calculation with other data.

---

### Post by SeijiSensei on 2018-07-02
I don't understand these lines at all:

```

$lastT[$i]['t_sy'] = $Co = $row['t_sy'];

...

$temparray[0] = $lastT[$x]['Co'];

```

There is no entry called :"$lastT[$x]['Co'] in the earlier for loop.  

I've never written an expression in PHP with multiple equalities. The [PHP manual]("http://php.net/manual/en/language.expressions.php") describes their use this way:

> Thus, writing something like '$b = ($a = 5)' is like writing '$a = 5; $b = 5;'

So that second line of code sets both $Co and $lastT[$i]['t_sy'] to the value of $row['t_sy'].  It never creates something called $lastT[$x]['Co'].

---

### Post by QIII on 2018-07-02
Moved to Programming Talk

---

### Post by nlee2 on 2018-07-02
```
for ($x = 0; $x < $Tsize; $x++) {
        $temparray[0] = $lastT[$x]['Co'];
        $temparray[1] = $lastT[$x]['LA'];
        $temparray[2] = $lastT[$x]['HB'];
....
echo $x . " " . $temparray[0] . " " . $temparray[1] . " " .  $temparray[2] . " " . $temparray[3] . " " . $temparray[4] . " " .  $temparray[5] . " " . $temparray[6] . " " . $temparray[7] . " " .  $temparray[8] . $line_break;
$my2darray[$x] [0] = $temparray[0] ;
$my2darray[$x] [1] = $temparray[1] ;
$my2darray[$x] [2] = $temparray[2] ;
$my2darray[$x] [3] = $temparray[3] ;
$my2darray[$x] [4] = $temparray[4] ;
$my2darray[$x] [5] = $temparray[5] ;
$my2darray[$x] [6] = $temparray[6] ;
$my2darray[$x] [7] = $temparray[7] ;
} // close for loop

```

---

### Post by ELMIT on 2018-07-02
I don't use multiple = signs in a line either ;-) That was a copy error.

I made a short test program that shows, that my thought was actually correct:

```

<?php

$co = array();
$result = array();

for ($x=0; $x<=7; $x++) {
  $a=$x+1;
  $b=$x+2;
  $c=$x+3;
  $d=$x+4;
  $e=$x+5;
  $f=$x+6;
  $g=$x+7;
  $h=$x+8;

  $co = array($a, $b, $c, $d, $e, $f, $g, $h);
  $result[]=$co;
}
echo "<pre>";
print_r($result);
echo "</pre>";

```

That shows me that my loop must do something terrible to get me only the last row into the $result array. Based on the test program I will make comparisons to find out whats wrong.

I also noted that the program got extremely time consuming. Expecting only a flash of time, it takes 15 seconds. That might hint that I reset the array multiple times too.

Thanks for thinking with me. It was a great help, even I didn't find the solution, but it brings me on the right track.

---


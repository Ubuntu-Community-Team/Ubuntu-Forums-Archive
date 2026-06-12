---
title: "How to use php-gd with sqlite3?"
date: 2013-03-15
forum: Programming Talk
---

### Post by Newbie89 on 2013-03-15
firstly,I need to get the data from sqlite database,then php-gd is use to generate the graph which is related with the sqlite databse.I have see through the example of use php-gd to generate graph.How to connect my sqlite database with the php-gd?

---

### Post by greenpeace on 2013-03-16
Hi, 

Why don't you show us what you have so far, so we can point you in the right direction...  :)

Cheers!
Gp

---

### Post by Newbie89 on 2013-03-16
Below is the connection between sqlite and php which I have test the code and run successfully.

---

### Post by Newbie89 on 2013-03-16
<?php
  try
  {
    //open the database
    $db = new PDO("sqlite:/var/www/databases/dog.sqlite");

    //create the database
    $db->exec("CREATE TABLE Dogs (Id INTEGER PRIMARY KEY, Breed TEXT, Name TEXT, Age INTEGER)");    

    //insert some data...
    $db->exec("INSERT INTO Dogs (Breed, Name, Age) VALUES ('Labrador', 'Tank', 2);".
               "INSERT INTO Dogs (Breed, Name, Age) VALUES ('Husky', 'Glacier', 7); " .
               "INSERT INTO Dogs (Breed, Name, Age) VALUES ('Golden-Doodle', 'Ellie', 4);");

    //now output the data to a simple html table...
    print "<table border=1>";
    print "<tr><td>Id</td><td>Breed</td><td>Name</td><td>Age</td></tr>";
    $result = $db->query('SELECT * FROM Dogs');
    foreach($result as $row)
    {
      print "<tr><td>".$row['Id']."</td>";
      print "<td>".$row['Breed']."</td>";
      print "<td>".$row['Name']."</td>";
      print "<td>".$row['Age']."</td></tr>";
    }
    print "</table>";

    // close the database connection
    $db = NULL;
  }
  catch(PDOException $e)
  {
    print 'Exception : '.$e->getMessage();
  }
?>

---

### Post by Newbie89 on 2013-03-16
This is the function of php-gd to generate a graph.I have test the code and it run successfully.

<?php
error_reporting(E_ALL | E_STRICT);
ini_set('display_errors', TRUE);
    # ------- The graph values in the form of associative array
    $values=array(
  "Jan" => 110,
  "Feb" => 130,
  "Mar" => 215,
  "Apr" => 81,
  "May" => 310,
  "Jun" => 110,
  "Jul" => 190,
  "Aug" => 175,
  "Sep" => 390,
  "Oct" => 286,
  "Nov" => 150,
  "Dec" => 196
   &nbsp;);

 
    $img_width=800;
    $img_height=600; 
    $margins=20;

 
    # ---- Find the size of graph by substracting the size of borders
    $graph_width=$img_width - $margins * 2;
    $graph_height=$img_height - $margins * 2; 
    $img=imagecreate($img_width,$img_height);

 
    $bar_width=20;
    $total_bars=count($values);
    $gap= ($graph_width- $total_bars * $bar_width ) / ($total_bars +1);

 
    # -------  Define Colors ----------------
    $bar_color=imagecolorallocate($img,0,64,128);
    $background_color=imagecolorallocate($img,240,240,255);
    $border_color=imagecolorallocate($img,200,200,200);
    $line_color=imagecolorallocate($img,220,220,220);
 
    # ------ Create the border around the graph ------

    imagefilledrectangle($img,1,1,$img_width-2,$img_height-2,$border_color);
    imagefilledrectangle($img,$margins,$margins,$img_width-1-$margins,$img_height-1-$margins,$background_color);

 
    # ------- Max value is required to adjust the scale    -------
    $max_value=max($values);
    $ratio= $graph_height/$max_value;

 
    # -------- Create scale and draw horizontal lines  --------
    $horizontal_lines=20;
    $horizontal_gap=$graph_height/$horizontal_lines;

    for($i=1;$i<=$horizontal_lines;$i++){
  $y=$img_height - $margins - $horizontal_gap * $i ;
  imageline($img,$margins,$y,$img_width-$margins,$y,$line_color);
  $v=intval($horizontal_gap * $i /$ratio);
  imagestring($img,0,5,$y-5,$v,$bar_color);

    }
 
 
    # ----------- Draw the bars here ------
    for($i=0;$i< $total_bars; $i++){ 
  # ------ Extract key and value pair from the current pointer position
  list($key,$value)=each($values); 
  $x1= $margins + $gap + $i * ($gap+$bar_width) ;
  $x2= $x1 + $bar_width; 
  $y1=$margins +$graph_height- intval($value * $ratio) ;
  $y2=$img_height-$margins;
  imagestring($img,0,$x1+3,$y1-10,$value,$bar_color);
  imagestring($img,0,$x1+3,$img_height-15,$key,$bar_color);  
  imagefilledrectangle($img,$x1,$y1,$x2,$y2,$bar_color);
    }
    header("Content-type:image/png");
    imagepng($img);

?>

---

### Post by Newbie89 on 2013-03-16
Can show me the method to link between them?both php just an example.Data not related.:)

---


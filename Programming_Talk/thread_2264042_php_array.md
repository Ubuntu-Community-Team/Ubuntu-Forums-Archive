---
title: "php array"
date: 2015-02-05
forum: Programming Talk
---

### Post by shad2 on 2015-02-05
how can i display the contents of this array under respective headings :
[php]
$projects['p/z/1']['Title']=$row->Title; 
             $projects['p/z/2']['Project date']=$row->pdate;
             $projects['p/z/3']['Description']=$row->Description;[/php]
      like this:
```
id                 title                       date                          desc
p/z/1         yyyy                12/1/2104                yeee
```

---

### Post by schragge on 2015-02-05
```

foreach ($projects as $id => $project) {
    echo "id\t";
    foreach (array_keys($project) as $key) {
        echo "$key\t";
    }
    echo "\n";
    echo "$id\t";
    foreach ($project as $val) {
        echo "$val\t";
    }
    echo "\n";

```

---

### Post by slickymaster on 2015-02-05
*Moved to the ***Programming Talk*** sub-forum*

---

### Post by SeijiSensei on 2015-02-05
Do you want to display the results in a web page?  If so, use an [HTML table]("http://www.w3schools.com/html/html_tables.asp").

First, I'm guessing your array actually has entries like this:
```

$projects['p/z/1']['Title']=$row->Title;
$projects['p/z/1']['Project date']=$row->pdate;
$projects['p/z/1']['Description']=$row->Description;

```

So lets try:
```

<?php
echo "<table>\n<tr><td>ID</td><td>Title</td><td>Date</td><td>Description</td></tr>\n";

foreach ($projects as $key=>$data) {
     echo "<tr><td>$key</td>";
     echo "<td>".$data['Title']."</td><td>".$data['Project_date']."</td><td>".$data['Description']."</td></tr>\n";
}

echo "</table>\n";
?>

```

---


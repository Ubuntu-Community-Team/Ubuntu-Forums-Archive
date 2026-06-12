---
title: "use PHP to loop a JSON file"
date: 2019-06-03
forum: Programming Talk
---

### Post by cazz on 2019-06-03
To tell the truth I'm not sure if that is a JSON file but it looks like it.

```
{"energy":{"timeUnit":"DAY","unit":"Wh","measuredBy":"INVERTER","values":[{"date":"2019-05-27 00:00:00","value":14679.0},{"date":"2019-05-28 00:00:00","value":54992.0},{"date":"2019-05-29 00:00:00","value":56305.0},{"date":"2019-05-30 00:00:00","value":16947.0},{"date":"2019-05-31 00:00:00","value":57151.0},{"date":"2019-06-01 00:00:00","value":11576.0},{"date":"2019-06-02 00:00:00","value":49365.0},{"date":"2019-06-03 00:00:00","value":39619.0}]}}
```

That I trying to do is loop and show date (Maybe not the time but I can remove that later med dateformat I think) and value

I have try with this code


```
<?php
$string = file_get_contents("data.json");
$json_a = json_decode($string, true);

foreach($json_a as $item) {
   echo $item['values'];
}
?>
```


but the webpage just say "Array"


I have never work with JSON before so I'm not sure what to do

---

### Post by SeijiSensei on 2019-06-03
PHP has built-in support for JSON:  [https://www.tutorialrepublic.com/php-tutorial/php-json-parsing.php](https://www.tutorialrepublic.com/php-tutorial/php-json-parsing.php) and [https://www.php.net/manual/en/ref.json.php](https://www.php.net/manual/en/ref.json.php)
 
You'll probably need to add the JSON module with

```
sudo apt install php-json
```

---

### Post by cazz on 2019-06-03
hmm ok, not sure if it was JSON, do not look anything I have found and read about :)

The system also can give me XML file so now I trying to see if I can use that with Python to read and save the value in a textfile
I have work a little with XML so I hope it make it easy for me to use then JSON.

---

### Post by #&amp;thj^% on 2019-06-03
See if something like this works:
```
<?php 
$input = '06/03/2019 19:00:02'; 
$date = strtotime($input); 
echo date('d/M/Y h:i:s', $date); 
?> 

```
Out Put:
```
03/Jun/2019 07:00:02 
```
You can test your code here:[http://codepad.org/](http://codepad.org/) 
And plus 1 for  SeijiSensei advice

---

### Post by SeijiSensei on 2019-06-03
> **cazz said:**
> I have work a little with XML so I hope it make it easy for me to use then JSON.

PHP has a built-in XML parser: [https://www.php.net/manual/en/book.xml.php](https://www.php.net/manual/en/book.xml.php)

Again you'll need to install it with "sudo apt install php-xml".

---

### Post by cazz on 2019-06-03
Thanks, with you help I got more curious about JSON so I now try to see if I can got it to work :)

---

### Post by cazz on 2019-06-03
well with a little more reading and trying I got a little forward now

```
<?php

$json = file_get_contents('data.json');

$array = json_decode( $json, true );

foreach($array as $item) {
    echo $item['date'];
    echo $item['value'];

    // just to see what is in the array
    echo '<pre>'; var_dump($item);
}
?>

```


it does not loop and just show date and value but the last one show me that is a array inside


[HTML]array(4) {
  ["timeUnit"]=>
  string(3) "DAY"
  ["unit"]=>
  string(2) "Wh"
  ["measuredBy"]=>
  string(8) "INVERTER"
  ["values"]=>
  array(8) {
    [0]=>
    array(2) {
      ["date"]=>
      string(19) "2019-05-27 00:00:00"
      ["value"]=>
      float(14679)
    }
    [1]=>
    array(2) {
      ["date"]=>
      string(19) "2019-05-28 00:00:00"
      ["value"]=>
      float(54992)
    }
    [2]=>
    array(2) {
      ["date"]=>
      string(19) "2019-05-29 00:00:00"
      ["value"]=>
      float(56305)
    }
    [3]=>
    array(2) {
      ["date"]=>
      string(19) "2019-05-30 00:00:00"
      ["value"]=>
      float(16947)
    }
    [4]=>
    array(2) {
      ["date"]=>
      string(19) "2019-05-31 00:00:00"
      ["value"]=>
      float(57151)
    }
    [5]=>
    array(2) {
      ["date"]=>
      string(19) "2019-06-01 00:00:00"
      ["value"]=>
      float(11576)
    }
    [6]=>
    array(2) {
      ["date"]=>
      string(19) "2019-06-02 00:00:00"
      ["value"]=>
      float(49365)
    }
    [7]=>
    array(2) {
      ["date"]=>
      string(19) "2019-06-03 00:00:00"
      ["value"]=>
      float(39638)
    }
  }
}[/HTML]

---

### Post by spjackson on 2019-06-03
```

<?php
$string = file_get_contents("data.json");
$json_a = json_decode($string, true);

print_r($json_a); // debugging - show full structure

$records = $json_a['energy']['values'];

print_r($records); // debugging - show the 'values' array

foreach($records as $item) {
   echo $item['value'] . "\n";
}
?>

```

---

### Post by cazz on 2019-06-03
Hmm thanks, It did give me that info I need but now I going to read what that code do so I can understand myself how it works and after I have read you code I think I have a idea.

---


---
title: "php array from log file"
date: 2007-02-09
forum: Programming Talk
---

### Post by tocleora on 2007-02-09
[SIZE="3"]I'm storing data in a log file that I want to process each night.  The way I need to store it is something like:

first name,joe,last name,smith

and I need to pull it in a way that I can do something like $customerinfo['first name'] = "Joe".  I guess it could be $customerinfo[0]['first name'] = "Joe".  Is there an easy way to do this?  I tried storing it in the text file like this:

"first name" => "joe","last name" => "smith"

I pulled the line into a string and then tried to do this:

$customerinfo = array($logline);

But it just set $customerinfo[0] to '"first name" => "joe","last name" => "smith"'.  Any help would be greatly appreciated![/SIZE]

---

### Post by ohgod on 2007-02-09
If you store it in a csv-like way ('first name','last name',....), you could easily parse it using the split() or explode() functions.  Both of these functions will split up a string into an array using any delimiter.  You'd have to index into the array by number, though.

You could use it like this:
```

$customerinfo = explode(",",$logline);
$firstname = $customerinfo[0];
$lastname = $customerinfo[1];

```

Here's a page about the explode() function:
[http://us2.php.net/manual/en/function.explode.php](http://us2.php.net/manual/en/function.explode.php)

---

### Post by kidders on 2007-02-09
Hi there,

Here's one way of approaching your problem. I used the following test file for the sake of something to play with:

```
first name,joe,last name,smith,customer number,1
first name,something,last name,something else,customer number,2
```

If it were me, I would start with something like this...```
<?php
$info=read_log('test.txt');

function read_log($filename) {
	$fp=fopen($filename,'r');
	if (!$fp) return false;
	
	$data=array();
	
	while (!feof($fp)) {
		$line=trim(fgets($fp));
		if ($line) {
			preg_match_all('/([^,]*),([^,]*)(?:,|$)/',$line,$matches);
			$data[]=$matches;
		}
	}
	
	fclose ($fp);
	return $data;
}
?>
```
This script produces a matrix of customer information, where...[LIST]
[*]$info[0] is the first customer
[*]$info[0][1] is a list of parameters
[*]$info[0][2] is a list of values
[/LIST]
So, for customer #2, the value of the parameter at $info[1][1][1] is at $info[1][2][1].

Next, I would drop one of the dimensions from the matrix, to produce something closer to what you asked for:

```
<?php
$info=read_log('test.txt');

function read_log($filename) {
	$fp=fopen($filename,'r');
	if (!$fp) return false;
	
	$data=array();
	
	while (!feof($fp)) {
		$line=trim(fgets($fp));
		**$arr=array();**
		if ($line) {
			preg_match_all('/([^,]*),([^,]*)(?:,|$)/',$line,$matches);
			**foreach ($matches[1] as $idx=>$val) $arr[$matches[1][$idx]]=$matches[2][$idx];**
			$data[]=$arr;
		}
	}
	
	fclose ($fp);
	return $data;
}
?>
```

Now, the $info matrix only has two dimensions:
```
Array
(
    [0] => Array
        (
            [first name] => joe
            [last name] => smith
            [customer number] => 1
        )

    [1] => Array
        (
            [first name] => something
            [last name] => something else
            [customer number] => 2
        )

)
```

**Caveats**
[LIST]
[*]The input file must contain one array per line, composed of one or more **parameter,value** pairs, separated by commas.
[*]If **first name,joe,first name,peter** is encountered, the value "joe" will be lost.
[/LIST]

Before the "foreach" loop in my "read_log" function, I would recommend calling **array_map**, with a callback to normalise your customer information. For instance...
[LIST]
[*]"First Name" should be converted to "first name" (or vice versa), so you don't wind up with blank values later, due to capitalisation inconsistencies in array keys.
[*]" first name" should be converted to "first name" for the same reason. (People often have a tendancy to put spaces after commas!)
[*]You might like to perform some manipulations on the actual values themselves, for instance, padding invoice numbers out to a set number of digits, or normalising the capitalisation of peoples' names, etc.
[/LIST]

I hope that helps.

**Edit:**
> ```
$customerinfo = explode(",",$logline);
$firstname = $customerinfo[0];
$lastname = $customerinfo[1];
```This only works if you already know the variable names being stored about customers ... in which case there's no point in storing them in your log files ... and how many of them there are. It's soooo much more straightforward though. :-)

My suggestion makes the (possibly inappropriate) assumption that you don't know how much information the logs contain about customers, or what that information might be.

---


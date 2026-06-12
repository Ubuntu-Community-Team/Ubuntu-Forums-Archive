---
title: "noob php: arrays examples not working"
date: 2008-10-07
forum: Programming Talk
---

### Post by lunaz on 2008-10-07
i'm very noob to programming & php. i have the dumbest array question ever! i did search this forum first but couldn't find anything to help me.

i am going thru the 2nd ed. learning php & mysql book from o'reilly. i'm trying out examples 6-3 & 6-4 (iirc,don't have book w/ me). for some reason the results aren't printing.

```
<?php
$shapes=array('Soda Can' => 'Cylinder',
	'Note Pad' => 'Rectangle',
	'Apple' => 'Sphere',
	'Orange' => 'Sphere',
	'Phonebook' => 'Rectangle');
print "A note pad is a {$shapes['Note Pad']}.";
?>

<?php
$shapes=array('Soda Can' => 'Cylinder',
	'Note Pad' => 'Rectangle',
	'Apple' => 'Sphere',
	'Orange' => 'Sphere',
	'Phonebook' => 'Rectangle');
foreach ($shapes as $key => $value) {
	print "The $key is a $value.<br />";
?>
```

i tried this example from the errata and still it's a no go:

```
<?php
$shapes = array('Soda can' => 'Cylinder',
	'Notepad' => 'Rectangle',
	'Apple' => 'Sphere',
	'Orange' => 'Sphere',
	'Phonebook' => 'Rectangle');
foreach ($shapes as $key => $value) {  // every associative array has $key and $value pairs
	print "The $key is a $value.<br />";
}
?>
```

any idea what i'm missing? thanks :)

---

### Post by LaRoza on 2008-10-07
How are you running it and can your run PHP normally?

Works for me (using php5-cli)

```

~/p$cat p.php
<?php
$shapes = array('Soda can' => 'Cylinder',
        'Notepad' => 'Rectangle',
        'Apple' => 'Sphere',
        'Orange' => 'Sphere',
        'Phonebook' => 'Rectangle');
foreach ($shapes as $key => $value) {  // every associative array has $key and $value pairs
        print "The $key is a $value. \n";
}
?>
~/p$php p.php
The Soda can is a Cylinder. 
The Notepad is a Rectangle. 
The Apple is a Sphere. 
The Orange is a Sphere. 
The Phonebook is a Rectangle. 
~/p$

```

---

### Post by Reiger on 2008-10-07
Questions:
(1) Are you trying to view output in a webbrowser?
     - Do you have (stupid question) setup a server & php interpreter (cgi version)?
     - Do you view it in something slightly more advanced than, say MSIE 4? --> Try wrapping it in <html><head></head><body>[output goes here]</body></html>
     - Is your script world-readable? (Say: chmod 755 my_script.php)
(2) Is your script actually executable as well? (Say: chmod 755 my_script.php)
(3) If trying from the commandline:
     - Do you actually have the PHP CLI version installed?
     - Does the script declare a shebang line (#!/path_to/directory-of/interpreter-executable) OR do you make sure to execute it by typing: php my_script.php ?

---

### Post by lunaz on 2008-10-08
thanks for the replies guys :) i figured it out lol... the file got uploaded to the wrong directory. :)

i'm using an ubuntu lamp server, 8.04 & firefox for browser :)

---

### Post by drubin on 2008-10-08
> **lunaz said:**
> 
```
<?php
$shapes=array('Soda Can' => 'Cylinder',
	'Note Pad' => 'Rectangle',
	'Apple' => 'Sphere',
	'Orange' => 'Sphere',
	'Phonebook' => 'Rectangle');
**print "A note pad is a {$shapes['Note Pad']}.";**
?>

<?php
$shapes=array('Soda Can' => 'Cylinder',
	'Note Pad' => 'Rectangle',
	'Apple' => 'Sphere',
	'Orange' => 'Sphere',
	'Phonebook' => 'Rectangle');
foreach ($shapes as $key => $value) {
	print "The $key is a $value.<br />";
?>
```


Since you are learning and this example is from a book. I am going to give you a little bit of advice the bolded text is a very hard way to reading code.... it can lead to very confusing results.

rather contact the string. instead of embeding vars with in double quotes. Also single quotes are faster then double quotes.
[PHP]echo "My name is ". $user['name'];[/PHP]

here are a few other tips for you. 
[http://reinholdweber.com/?p=3](http://reinholdweber.com/?p=3)

---


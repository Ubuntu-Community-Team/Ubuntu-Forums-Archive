---
title: "PHP syntax question"
date: 2007-08-10
forum: Programming Talk
---

### Post by RocketRanger on 2007-08-10
I have been following a tutorial on PHP and mySql, however there seems to be some inconsistencies in the examples in the book. 

I am confused about when to used quotes in accessing an array. 

Here's a quote from one of the examples:
```

if (!checkdate($_POST[month], 1, $_POST[year])) {
	$nowArray = getdate();
	$month = $nowArray['mon'];
	$year = $nowArray['year'];
} else {
	$month = $_POST[month];
	$month = $_POST[year];
}
```

... and as you can see he's using single quotes to access the $nowArray but not when accessing the $_POST array.

Are there any reason for this? What is the 'rule(s)' about using quotes in php?

---

### Post by qix on 2007-08-10
I'm not sure, but my experience tells me that it's the same, whether or not you include quotes. It can be ' aswell as " and it can be omitted, and you will get the same results.

---

### Post by fppl on 2007-08-10
When selecting an array item by value (string or chat) you must put it in quotes. I'm 99% sure he'll get an error in the else{} commands.

---

### Post by fppl on 2007-08-10
But what you CAN do is "$_POST[str]" since the quotes surrounding the whole thing will count.

Same goes for "Hello my name is $_POST[name]. How are you doing?" or mysql_query("SELECT * FROM table WHERE column='$_POST[column]'");'

---

### Post by Occasionally Correct on 2007-08-10
The quotes are only optional on associative array indices because the behavior of PHP is that an unquoted "string" will result in a new constant whose value is its name. For example:

```
$test[something] = 'Hello!';
echo something; // "something"
```

While it works, that doesn't mean it should be used: It can cause conflicts if you have other constants in your scripts, and it's bad practice (it will also generate an E_NOTICE warning if you have them on); always quote your strings. This is [warned against](http://www.php.net/manual/en/language.types.array.php#language.types.array.foo-bar) in the documentation. If you're using it within a string, you can do this instead:

```
$x = "The number was {$_POST['n']}!";
```

Hope that helps. :)

---

### Post by RocketRanger on 2007-08-13
Brilliant. Thanks for the answers. 
Since I'm very much in the learning phase I don't think this is the time to pick up _any_ bad habits. So lesson learned. Always quote array index strings, unless it resides in an already strong quoted string. 

But no, I don't have e_warnings enabled. How do I do that?

---


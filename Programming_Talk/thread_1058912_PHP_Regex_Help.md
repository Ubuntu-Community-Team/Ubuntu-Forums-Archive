---
title: "PHP Regex Help"
date: 2009-02-03
forum: Programming Talk
---

### Post by cerealtx on 2009-02-03
```
<?php
			$vidmatch[1] = 'http://media.website.com/fbe0852e8512f1005d599498fddf602a/Exclusive_Dec9_1.flv';
			echo $vidmatch[1]; //Video
			echo "\n\n";
			$regex = ".*/(.*)";
			if(preg_match($regex, $vidmatch[1], $results))
			{
			echo $results[1];
			}
?>
```
when i try and run this php script i get
 ```
Warning: preg_match(): Unknown modifier '*' in /home/cereal/Documents/phpcode.php on line 6

```
... and im at a loss

---

### Post by stylishpants on 2009-02-03
You're specifying your regex wrongly, in two ways.

First, you have to surround it with a pair of slashes.  Slashes denote the start and end of the pattern.  Any characters that appear after the terminating slash are regex modifiers, and not part of the pattern.  That's the modifiers your error message is talking about.

Secondly, you have to escape any slash characters that appear inside your pattern, so that they will not be parsed as the terminating slash.

This should fix it:

```

$regex = '/.*\/(.*)/';

```

Note that PHP also allows you to use other characters as pattern delimiters.  If you use a character other than the slash for your delimiter, then you won't have to escape any slashes that appear within your pattern.  This makes a shorter and more readable pattern.

```

$regex = '|.*/(.*)|';

```

---

### Post by cerealtx on 2009-02-04
thank you very much stylishpants, help and info just what i was looking for! works like a charm thank you

---


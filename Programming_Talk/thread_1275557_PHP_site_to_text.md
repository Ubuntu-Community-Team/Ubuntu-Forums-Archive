---
title: "PHP site to text"
date: 2009-09-25
forum: Programming Talk
---

### Post by kumoshk on 2009-09-25
In PHP, how do I pull the text from some online website that is not mine (through inputting a URL into a function) and store that text in a variable?

I need to get some information from a limitless number of similarly formatted pages online.

---

### Post by -grubby on 2009-09-26
Shortcut:

[php]
$contents = file_get_contents("http://google.com");
[/php]

---

### Post by kumoshk on 2009-09-26
> **-grubby said:**
> Shortcut:

[php]
$contents = file_get_contents("http://google.com");
[/php]

Awesome. Thanks!

---

### Post by kumoshk on 2009-09-26
> **-grubby said:**
> Shortcut:

[php]
$contents = file_get_contents("http://google.com");
[/php]

Huh. This actually didn't do what I wanted after all. I mean, all I see is a bunch of css and JavaScript. A lot of the actual text is missing. How do I get rid of everything but the text displayed after the HTML is rendered?

---

### Post by -grubby on 2009-09-26
> **kumoshk said:**
> Huh. This actually didn't do what I wanted after all. I mean, all I see is a bunch of css and JavaScript. A lot of the actual text is missing. How do I get rid of everything but the text displayed after the HTML is rendered?

That just gets the source for the page. It isn't a browser engine, sorry

---

### Post by wojox on 2009-09-26
[php]
function get_string_between($string, $start, $end){ 
        $string = " ".$string; 
        $ini = strpos($string,$start); 
        if ($ini == 0) return ""; 
        $ini += strlen($start);    
        $len = strpos($string,$end,$ini) - $ini; 
        return substr($string,$ini,$len);

$contents = file_get_contents("http://google.com");  

$currentstring1=get_string_between($currentstring,"1","2");
[/php]Replace 1 with the first beginning of the file and 2 with the end of the file.
In other words find your main contents begining and ending.

---

### Post by credobyte on 2009-09-26
If it would be possible, we wouldn't need XML.

---


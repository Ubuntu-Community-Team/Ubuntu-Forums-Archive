---
title: "regex in PHP ..."
date: 2008-08-28
forum: Programming Talk
---

### Post by slavik on 2008-08-28
just ran across a problem with PHP's regex engine.

[php]
$keywords = array("key1" => "socket", "key2" => "pocket");
$string = "There is a {key1} in my {key2}!";
[/php]

Now, the idea is to take the string and replace the {(.*?)} with $keywords[$1], but alas, this does not work with preg_replace.

Any way to do such a substition? (I know that you can loop for all the keys and do an str_replace, but the regex way would be better).

in Perl, it would be a simple ```
$string =~ s/{(.*?)}/$keywords{$1}/g;
```

---

### Post by Reiger on 2008-08-29
Wait a few seconds, 'cause I *know* it's easy to do. (I've done such substitution.)

Two checks:

1) The preg_replace function goes [regex, substitute, target_string]
2) Use the single-quote-delimited strings instead of double quotes for avoiding escaping problems? In Single quoted strings little needs to be escaped.

Apart from that:
In double quoted strings such substitution is perfect over-kill and expensive over-kill at that:

[php]
$string = "There's a $keywords['key1'] in my $keywords['key2']";
[/php]

Does just that for you.

---

### Post by mike_g on 2008-08-29
> I know that you can loop for all the keys and do an str_replace, but the regex way would be better
str_replace will replace all instances, looping internally:
```
$string = "There is a key1 in my key2!";  
$before = array("key1", "key2");
$after =  array("socket", "pocket");
echo str_replace($before, $after, $string);
```
I dont see any real reason why a regex would be better for this. Maybe I'm missing something.

---

### Post by Reiger on 2008-08-29
Also: the /g modifier doesn't work in preg_replace; instead you should omit the modifier and call preg_replace_all.

AFAIK the proper syntax would be (in order to get multiple {.*} instances to be replaced with their proper substitute:

preg_replace_all($regex,$array_of_subsitutes,$target);

---

### Post by slavik on 2008-08-29
thanks for the code snippets, going to try them out. :)

---


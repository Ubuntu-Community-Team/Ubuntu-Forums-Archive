---
title: "Incrementing String"
date: 2009-10-17
forum: Programming Talk
---

### Post by Jekshadow on 2009-10-17
I'm building a program, and it needs to increment a string:

Example:
```

a
b
c
...
aa
...
aaa
(and so on)

```

Just a noob question, but how would you do that in PHP?

---

### Post by scragar on 2009-10-17
[php]
<?php

define('CHARS', 'abcdefghijklmnopqrstuvwxyz');

error_reporting(-1);
ini_set('display_errors', 'stdout');

function recletters($start='', $levels=2){
  foreach(preg_split('//', CHARS, -1, PREG_SPLIT_NO_EMPTY) as $f){
    echo $start.$f.'<br>';
    if($levels > 0)
      recletters($start.$f, $levels-1);
  }
}

recletters('', 2);
[/php]Not quite the way you want it, but by far the most efficient(or at least it would be if you used a few globals, see second code under here).
[php]

<?php

define('CHARS', 'abcdefghijklmnopqrstuvwxyz');

$chars = preg_split('//', CHARS, -1, PREG_SPLIT_NO_EMPTY);

function recletters($start='', $levels=2){
  global $chars;
  $levels--;
  foreach($chars as $f){
    echo $start, $f, '<br>';
    if($levels)
      recletters($start.$f, $levels);
  }
}

recletters('', 2);
[/php]Optimised a little.

---

### Post by Jekshadow on 2009-10-17
Works great, one question though:

It shows "a", then moves onto "aa", cant figure out why...

a
aa
ab
ac
ad
ae
af
ag
...

---

### Post by scragar on 2009-10-17
For efficiency it's faster to work like that, to do it the way you want would have to be implimented with several unrequired loops making already slow code even less efficient, as well as adding to the over all overhead of the code.
[php]<?php

define('CHARS', 'abcdefghijklmnopqrstuvwxyz');
$minChars = 1;
$maxChars = 3;


$chars = preg_split('//', CHARS, -1, PREG_SPLIT_NO_EMPTY);


for($i=$minChars; $i < $maxChars; $i++){
  recletters($i);
}

function recletters($levels. $start=''){
  global $chars;
  $levels--;
  foreach($chars as $f){
    if($levels)
      recletters($start.$f, $levels);
    else
      echo $start, $f, '<br>';
  }
}[/php]

---


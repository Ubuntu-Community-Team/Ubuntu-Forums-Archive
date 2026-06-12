---
title: "php split string function, can collect into an array?"
date: 2011-01-16
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-16
this will split a string into words using the space as the pattern
and collects 6 words.
but how would you do this with an array and catch however many words exist?
```
  

  list($andws1,$andws2,$andws3,$andws4,$andws5,$andws6) = split(' ', $andws); 
    echo $andws1;
    echo $andws2;
    echo $andws3;
    echo $andws4;
    echo $andws5;
    echo $andws6;
```

---

### Post by sdowney717 on 2011-01-16
Ok, I got it with this

>     $s = "Split this sentence by spaces";
    $words = split(' ', $s);
    print count($words);
    echo $words[0];
    echo $words[1];
    echo $words[2];

---

### Post by laceration on 2011-01-16
foreach ( $words as $key=>$val )
{
    echo $words[$key];
}

---


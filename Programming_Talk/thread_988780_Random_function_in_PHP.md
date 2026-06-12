---
title: "Random function in PHP"
date: 2008-11-20
forum: Programming Talk
---

### Post by niccholaspage on 2008-11-20
So now I need to use a random function, But instead of doing it like 100-300, I need to pick specific numbers. Anyone know how in PHP?

---

### Post by wrtpeeps on 2008-11-20
I don't believe there is a built in function for this, you'd have to write your own I recon.

---

### Post by Reiger on 2008-11-20
From "PHP" and "random" in Google we obtain (if you're using Opera anyways) [http://www.google.com/search?client=opera&rls=en&q=php+random&sourceid=opera&ie=utf-8&oe=utf-8](http://www.google.com/search?client=opera&rls=en&q=php+random&sourceid=opera&ie=utf-8&oe=utf-8) using the built-in search box. From there it's like the second link down?
[http://nl.php.net/rand](http://nl.php.net/rand)

Not specifically directed at the OP *only* but...
<rant>
Honestly, how hard can it be?!
</rant>

---

### Post by niccholaspage on 2008-11-20
> **Reiger said:**
> From "PHP" and "random" in Google we obtain (if you're using Opera anyways) [http://www.google.com/search?client=opera&rls=en&q=php+random&sourceid=opera&ie=utf-8&oe=utf-8](http://www.google.com/search?client=opera&rls=en&q=php+random&sourceid=opera&ie=utf-8&oe=utf-8) using the built-in search box. From there it's like the second link down?
[http://nl.php.net/rand](http://nl.php.net/rand)

Not specifically directed at the OP *only* but...
<rant>
Honestly, how hard can it be?!
</rant>
I mean I dont want to pick a number between those, I need to pick specific numbers.



I don't know much about PHP so me making a function isn't possible right now.

---

### Post by Reiger on 2008-11-20
Ehrm: what about using the random number as index to an array?
[php]
<?php

$vals=array(1,2,3,4,5);
$key=rand(0,4);
die(PHP_EOL. "Randomly drawn: {$vals[$key]}" .PHP_EOL);
?>
[/php]

---

### Post by wrtpeeps on 2008-11-20
Not 100% sure how you'd do it if I'm honest.

---

### Post by escapee on 2008-11-21
> **niccholaspage said:**
> I mean I dont want to pick a number between those, I need to pick specific numbers.



I don't know much about PHP so me making a function isn't possible right now.

Since you're trying to build an online game with PHP, as stated in your other PHP help thread about timers, I'd highly recommend you start learning PHP.

Other than that, Reiger had a very good solution for what it sounds like you're looking for.

---

### Post by drubin on 2008-11-21
> **Reiger said:**
> From "PHP" and "random" in Google we obtain (if you're using Opera anyways) [http://www.google.com/search?client=opera&rls=en&q=php+random&sourceid=opera&ie=utf-8&oe=utf-8](http://www.google.com/search?client=opera&rls=en&q=php+random&sourceid=opera&ie=utf-8&oe=utf-8) using the built-in search box. From there it's like the second link down?
[http://nl.php.net/rand](http://nl.php.net/rand)

Not specifically directed at the OP *only* but...
<rant>
Honestly, how hard can it be?!
</rant>

Things are hard when you are starting off... Often the simplest things are not clear when the problem is about something you have done.

---

### Post by drubin on 2008-11-21
> **wrtpeeps said:**
> Not 100% sure how you'd do it if I'm honest.

What is that an answer to?

---

### Post by bobbocanfly on 2008-11-21
If you put all the allowed numbers into an array you can select one randomly using array_rand():

```
<?php
$numbers = array(3, 7, 9, 12);
$num = array_rand($numbers);
?>
```

---

### Post by Reiger on 2008-11-21
> **drubin said:**
> Things are hard when you are starting off... Often the simplest things are not clear when the problem is about something you have done.

Well; I was talking about the Google bit. I mean: I can understand that you code without actually knowing the tools all that good, there's no problem with that -- it's what learning as you go is for. But I mean: somebody who has the resources to post on a forum, and a non-generic if not a highly niche one like this obviously can make use of the services provided by the Google search engine or similar search engines out there.

So hence: how hard can it be to simply type 2 words in an input field and hit enter?

---


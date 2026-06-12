---
title: "empty , how about not empty?"
date: 2011-01-14
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-14
[http://php.net/manual/en/function.empty.php](http://php.net/manual/en/function.empty.php)

say it has a value, how to use in an if statement?

I thought of this
 if ($bauthor <> ""){print "Subject $bsubject";}

then i thought
 if(empty($bauthor somehow false) type of idea?

---

### Post by sdowney717 on 2011-01-14
if (strlen($bsubject) >0){print "Subject $bsubject";}

ok this works, do a string length test

---

### Post by Barrucadu on 2011-01-14
[php]if (!empty ($bsubject))
  {
    // Do stuff
  }[/php]

---

### Post by sdowney717 on 2011-01-15
thanks, that was too easy.

---


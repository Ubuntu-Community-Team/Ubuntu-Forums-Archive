---
title: "Passing variables to php via url... with umlauts"
date: 2008-07-26
forum: Programming Talk
---

### Post by viciouslime on 2008-07-26
At the moment I can successfully process the following:
```
process.php?deword=Schlammstelzer&detype=2&enword=Banded%20Stilt
```

However, when a german word has an umlaut or an ß in it, the entry in the mysql database does not appear correctly. If I replace the umlauted character with the html code for that character, it contains an &, e.g. &auml; which also breaks things...

does anyone know the correct way to do this?

---

### Post by drubin on 2008-07-26
There is a function in php called url_decode($string)  url_encode($string)

Take a look at those first.
[http://www.php.net/urlencode](http://www.php.net/urlencode)

---


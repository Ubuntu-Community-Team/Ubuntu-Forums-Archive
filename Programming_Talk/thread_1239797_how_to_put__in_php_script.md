---
title: "how to put // in php script"
date: 2009-08-13
forum: Programming Talk
---

### Post by sandyd on 2009-08-13
Ive learned this ...previously... but how do i put // in a php script without making it a comment? (im trying to enter a url into a variable)

---

### Post by wojox on 2009-08-13
[PHP]header("Location: http://ubuntuforums.org/");[/PHP]

---

### Post by jeffathehutt on 2009-08-13
$site = 'http://www.site.com/';

Make sure you are including quotes around the url, and it should work.:)

---

### Post by wojox on 2009-08-13
opps didn't see the variable part.

---

### Post by credobyte on 2009-08-13
Where's the problem ? :roll:
[PHP]$variable = "http://www.google.com";
[/PHP]

---

### Post by wojox on 2009-08-13
No problem I just set the parameters for a function instead of assigning it to a variable. Time for bed. :confused:

---

### Post by sandyd on 2009-08-13
oops. turned out i was just being silly.
apparently, 
$url = "http://sitehere.com" is different than
$url = 'http://sitehere.com'
](*,)](*,) ](*,) ](*,) ](*,)

---

### Post by credobyte on 2009-08-13
> **wojox said:**
> No problem I just set the parameters for a function instead of assigning it to a variable. Time for bed. :confused:

Indeed, I don't understand, why he made this thread without trying it first ( w3schools second lesson ) ](*,)

---


---
title: "Regex help"
date: 2007-01-04
forum: Programming Talk
---

### Post by leep on 2007-01-04
Hi,
I need a little help writing a very simple regular expression for a php script. What I need to obtain is every occourrence of a char within a string only if this char is not contaiined within ''.

Example:

```

nome='simone',soprannome='leep',eta='30',peso='<=100'

```

In this string I need to identify the first 4 occourences of "=", not the last one within ''.
It should be a really easy regex to write, but I really don't know how to start.
If you got some link to any online resource about regex it would be appreciated.
Thank you in advance,
S.

---

### Post by DeadEyes on 2007-01-04
```

='(\w|<|<=|=|>=|>)*'

```
use the above regexp to do a global find, and replace with an empty string you should get:

nome,soprannome,eta,peso

in your example  there is a <=100, so I assume there could also be a <, <=,  =, > etc.
Edit:
this one will do the same if peso is not a whole number
```

(='\w*')|(='[<>]=?\d*\.*\d*')

```

Man I love messing around with RegExps
this one will match the words you want, no find and replace this time :)
```

\w+(?==)

```

---

### Post by leep on 2007-01-04
Thank you very much, I'll take a lok at your regex.
Just a note: I need to match "=" outside ' and '. 
I'm about to write something that needs to split the original string into an array containing on element 0 the string at the left side of "0", and on element 1 the string at the right.

```

Ciccio='1'
===> element[0] = Ciccio
===> element[1] = '1'

Peso='<=100'
===> element[0] = Peso
===> element[1] = '<=100'

```

---

### Post by slavik on 2007-01-04
%myhash = "nome='simone',soprannome='leep',eta='30',peso='<=100'" =~ m/(.*?)='(.*?)',?/g;

that hash will hold the key value pairs by making whatever is before the '=' a key, and whatever is in quotes a value.

@deadeyes, why do that weird thing when you can use (.*?) ... if whatever is in single quotes is a value, we want to get everything, even if there are whitespaces (which \w doesn't match)
\w is the same as [a-zA-Z0-9]

---

### Post by leep on 2007-01-04
Sorry slavik, how do you insert it into a php script?

---

### Post by slavik on 2007-01-04
look into preg_match() function ... you should be able to send it the regular expression unaltered (the regex is in perl syntax) ... gimmie some time, I will work out some simple php code.

here is the complete html/php code:
```

<html>
<body>
<pre>
<?php

$regex = "/(.*?)='(.*?)',?/";
$string = "nome='simone',soprannome='leep',eta='30',peso='<= 100'";
$matches;

preg_match_all($regex, $string, $matches);

print_r($matches);

?>
</pre>

</body>
</html>

```

---

### Post by DeadEyes on 2007-01-04
> **slavik said:**
> 
...
@deadeyes, why do that weird thing when you can use (.*?) ... if whatever is in single quotes is a value, we want to get everything, even if there are whitespaces (which \w doesn't match)
\w is the same as [a-zA-Z0-9]
I didn't fully understand I thought he was just looking for the names.

---


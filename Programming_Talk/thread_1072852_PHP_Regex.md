---
title: "PHP Regex"
date: 2009-02-17
forum: Programming Talk
---

### Post by cerealtx on 2009-02-17
can't seem to get it, this is what im looking for and what i have so far
```

<a href="viewprofile.aspx?profile_id=11214729">Dustergirl</a>
```

```
preg_match_all('/<a href=\"viewprofile\.aspx\?profile_id=(.*)\">(.*)<\/a>/', $result, $matches, PREG_PATTERN_ORDER);
```

---

### Post by digitalvectorz on 2009-02-17
How are you trying to access the $matches ?

are you accessing it like
```

echo $matches[1][0] . " , " . $matches[1][1];

```

in preg_match_all (ordered), to access the matches where the parentheses are, that should be $matches[1][n] (where n is a number identifying the individual match.


$matches[0] prints out the entire substring that matches were found.

[http://www.php.net/preg_match_all](http://www.php.net/preg_match_all)

---

### Post by cerealtx on 2009-02-17
didn't realise that, thank you well i have this now, but im still not getting any matches, i think i am missing escaping in my regex or something
```

	preg_match_all('/<a href\=\"viewprofile\.aspx\?profile_id\=(.*)\">(.*)<\/a>/', $result, $matches, PREG_SET_ORDER);
	foreach ($matches as $match)
	{
		echo $match[0];
		echo $match[1];
	}

```

---

### Post by digitalvectorz on 2009-02-17
> **cerealtx said:**
> didn't realise that, thank you well i have this now, but im still not getting any matches, i think i am missing escaping in my regex or something
```

	preg_match_all('/<a href\=\"viewprofile\.aspx\?profile_id\=(.*)\">(.*)<\/a>/', $result, $matches, PREG_SET_ORDER);
	foreach ($matches as $match)
	{
		echo $match[0];
		echo $match[1];
	}

```

If you're trying to get the individual values, try something like:
```

preg_match_all('/<a href\=\"viewprofile\.aspx\?profile_id\=(.*)\">(.*)<\/a>/', $result, $matches, PREG_SET_ORDER);
	foreach ($matches**[1]** as $match)
	{
		echo $match[0];
		echo $match[1];
	}

```

---

### Post by cerealtx on 2009-02-17
> **digitalvectorz said:**
> If you're trying to get the individual values, try something like:
```

preg_match_all('/<a href\=\"viewprofile\.aspx\?profile_id\=(.*)\">(.*)<\/a>/', $result, $matches, PREG_SET_ORDER);
	foreach ($matches**[1]** as $match)
	{
		echo $match[0];
		echo $match[1];
	}

```

ive done something like this before, that code gives errors for invalid argument
i got the code some what from that preg_match_all on php.net
```
preg_match_all("/(<([\w]+)[^>]*>)(.*)(<\/\\2>)/", $html, $matches, PREG_SET_ORDER);

foreach ($matches as $val) {
    echo "matched: " . $val[0] . "\n";
    echo "part 1: " . $val[1] . "\n";
    echo "part 2: " . $val[3] . "\n";
    echo "part 3: " . $val[4] . "\n\n";
}
```

---

### Post by digitalvectorz on 2009-02-17
So with the code you are currently using...what output are you getting?

---

### Post by cerealtx on 2009-02-17
none, thats why i think its a regex problem

---

### Post by digitalvectorz on 2009-02-17
the regex is fine.  I just ran it and it worked fine:

```

<?php

$result = '<a href="viewprofile.aspx?profile_id=11214729">Dustergirl</a>';

preg_match_all('/<a href\=\"viewprofile\.aspx\?profile_id\=(.*)\">(.*)<\/a>/',
    $result,
    $matches,
    PREG_SET_ORDER);

    foreach ($matches as $match)
    {
        echo $match[0];
        echo $match[1];
        echo $match[2];
    }

?>


```

---

### Post by cerealtx on 2009-02-17
> **digitalvectorz said:**
> the regex is fine.  I just ran it and it worked fine:

```

<?php

$result = '<a href="viewprofile.aspx?profile_id=11214729">Dustergirl</a>';

preg_match_all('/<a href\=\"viewprofile\.aspx\?profile_id\=(.*)\">(.*)<\/a>/',
    $result,
    $matches,
    PREG_SET_ORDER);

    foreach ($matches as $match)
    {
        echo $match[0];
        echo $match[1];
        echo $match[2];
    }

?>


```

lol, must be my input then lol! thanx i should have checked that first :)

---

### Post by digitalvectorz on 2009-02-17
Lol.  No worries!  Good luck.

---

### Post by cerealtx on 2009-02-17
didn't have curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1); lol

---

### Post by digitalvectorz on 2009-02-17
Neither did I.

---

### Post by digitalvectorz on 2009-02-17
P.S. - if the topic in discussion is resolved to your satisfaction, please mark is as solved;  Thanks!  :-)

---


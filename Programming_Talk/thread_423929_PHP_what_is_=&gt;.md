---
title: "PHP: what is =&gt;?"
date: 2007-04-26
forum: Programming Talk
---

### Post by eldersoares on 2007-04-26
hello
i've found in some codes this => but in the php docs it doesnt appear like an operator os smth like this... it seems to be somth related to arrays... but what is it exactly?!?!?!??!

thanks

---

### Post by jespdj on 2007-04-26
You can find everything you want to know about PHP on: [http://www.php.net](http://www.php.net)

For an anwer to your question have a look at this: [http://www.php.net/manual/en/language.types.array.php](http://www.php.net/manual/en/language.types.array.php)

---

### Post by eldersoares on 2007-04-26
ok thanks

---

### Post by maddog39 on 2007-04-27
It defines the value of the second parameter in a 2D array. If that even makes sense. If you take a look at the foreach() control structure, you will see how this exactly works. Hard to explain really.

---

### Post by Compyx on 2007-04-28
> **maddog39 said:**
> It defines the value of the second parameter in a 2D array. If that even makes sense. If you take a look at the foreach() control structure, you will see how this exactly works. Hard to explain really.

No, the => operator maps a key to a value in an array. In PHP these constructs are called associative arrays, in Perl they're called hashes.

This:
```

$MyArray = array (
    "cpu" => "Athon XP",
    "mem" => "1 GB",
    "hdd" => "120 GB"
);

```

Generates a 1-dimensional associative array (a hash actually), in which a value can be looked up by a label, eg:
```

echo $MyArray["cpu"];

```
will print "Athlon XP".

All this is explained in great detail on the PHP website, as mentioned in an earlier post.

---

### Post by smartbei on 2007-04-29
It is also used in:
```

$arr=array("x","y","z");
foreach($arr as $key => $val)
     echo "$key $val<br>";

```
would print out:
> 
0 x
1 y
2 z


---


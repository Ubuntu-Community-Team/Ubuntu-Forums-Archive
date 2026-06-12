---
title: "PHP:  If variable == A or variable == B, etc..."
date: 2010-11-26
forum: Programming Talk
---

### Post by Lucky. on 2010-11-26
I am sorry for such a silly question, but I cannot find the syntax for such a thing in PHP.

Looking for something easier to type than the following:

```

if( $someVar == "string1" || $someVar == "string2" || $someVar == "string3" )

```

I know in SQL, there's something like:

```

SELECT * WHERE Stuff IN( 'string1', 'string2', 'string3' )

```

Anything like this in PHP?  (Not trying to select data like in SQL, just trying to reduce the code I type).

---

### Post by schauerlich on 2010-11-26
[http://www.php.net/manual/en/function.in-array.php](http://www.php.net/manual/en/function.in-array.php)
You might also want:
[http://php.net/manual/en/control-structures.switch.php](http://php.net/manual/en/control-structures.switch.php)

---

### Post by Lucky. on 2010-11-27
Thank you so much.  in_array will work great.  Much appreciated!

---


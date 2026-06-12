---
title: "Number in string"
date: 2008-02-18
forum: Programming Talk
---

### Post by vicpascow on 2008-02-18
Trying to work this:

If a string contains a number, print that number, i.e.


ksajhdfkjas1

would print 1



I was thinking of something like:

if ($string =~ /\d+/g) {
print "\d+";
}

but of course that doesn't work...

Any tips?

---

### Post by Jessehk on 2008-02-18
It's possible to match and capture a pattern in a regex (read this: [http://perldoc.perl.org/perlre.html](http://perldoc.perl.org/perlre.html) for more).

I am not very familiar with Perl (although I do know regex), but I think it would be this:
```

if ( $string =~ /(\d+)/g ) {
    print $1;
}

```

Where the stuff in the brackets, \d+, is captured and assigned to the variables $1, $2, etc for the nth capture.

---

### Post by ghostdog74 on 2008-02-18
```

# echo "ksajhdfkjas1" | sed 's/[^0-9]*//'
1

```

---

### Post by stroyan on 2008-02-18
You could turn the non-digit characters into nothing or into spaces with bash shell's ${var//pattern/replacement} notation.
But what do you want to do if there are multiple numbers?
```
${n//[^[:digit:]]/}
``` would push all the digits together.
```
${n//[^[:digit:]]/ }
``` would keep separate numbers you could pick out.  They could be assigned to array elements like this-
```
$ n="ksajhdfkjas1"
$ nums=(${n//[^[:digit:]]/ }); echo "There are ${#nums[@]} numbers"; echo "${nums[@]}"
There are 1 numbers
1
$ n=ksajh33dfkjas1
$ nums=(${n//[^[:digit:]]/ }); echo "There are ${#nums[@]} numbers"; echo "${nums[@]}"
There are 2 numbers
33 1
```

---


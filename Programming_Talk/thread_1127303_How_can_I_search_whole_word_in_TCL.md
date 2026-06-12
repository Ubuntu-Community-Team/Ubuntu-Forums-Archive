---
title: "How can I search whole word in TCL?"
date: 2009-04-16
forum: Programming Talk
---

### Post by tusharv on 2009-04-16
Hi All,

I m working on TCL.
I have one variable that contains string.
suppose ```
set var ABC
```

Now I am reading one file line by line. If I want existance of this variable value in the line. so How can I make sure that it matches with ABC only not ABCD ?

Thanks,
Tusharv

---

### Post by stevescripts on 2009-04-16
Tusharv - a quickish hack:

```

proc search {word data} {
	set count 0
	foreach i $data {
		if [string eq $word $i] {
			incr count
		}
	}
	return $count
}

```
A quick test:
```

(Desktop) 1 % source search.tcl
(Desktop) 2 % set test The
The
(Desktop) 3 % set data "The quick brown fox"
The quick brown fox
(Desktop) 4 % search $test $data
1
(Desktop) 5 % search foo $data
0

```
Does this satisfy your requirements?

Steve

---

### Post by tusharv on 2009-04-17
Hi stevescripts,

A good hack, but in my program I am doing just like ```
if {[regexp "$var" $line]}
``` Here $line is the line read from a file. This syntax matches when var is ABC and ABCD is contained by $line.
So by using this syntax only can I make sure that, if $var is ABC and $line contains ABCD then it does not match.

Thanks,
Tusharv

---

### Post by stevescripts on 2009-04-17
regexp's are fine when you really need them, but sometimes they tend to be ... overkill (and complex) ...

Are your variables always one word?  Do they ever appear more than once in a line?

What I provided will provide a count of all instances of a single word search variable, and will not allow for example the var "ABC" to match the data "ABCD"

```

steveo@delldesktop:~/Desktop$ tclsh
% source search.tcl
% set test "ABC"
ABC
% set line "ABC abc ABCDE BCDE ABC CBA"
ABC abc ABCDE BCDE ABC CBA
% search $test $line
2
% set otherline "This is a test"
This is a test
% search $test $otherline
0

```

Steve

---

### Post by stevescripts on 2009-04-17
finding a bit of time on a friday afternoon ... ;)

If you feel you *must* use regular expressions to do this job:

```

(Desktop) 1 % set test ABC
ABC
(Desktop) 2 % set data {abc ABC ABCD BABC}
abc ABC ABCD BABC
(Desktop) 3 % set re "\\m$test\\M"
\mABC\M
(Desktop) 4 % regexp -all -inline -indices $re $data
{4 6}

```

BTW, string match is another good option.

Hope this helps clear things up a bit.

Steve

---


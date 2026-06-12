---
title: "test (bash builtin)"
date: 2013-02-04
forum: Programming Talk
---

### Post by Drenriza on 2013-02-04
Anyone know a good site that explains test
[LIST]
[*]What is "test"
[*]How to use "test"
[*]Good to know about "test"
[/LIST]

And so on and so forth.

The reason i ask, is that i'am currently going through a script written by a co-worker.
And test is used extensively, but my knowledge about test without a if, is very limited.
So a guide on how "what test is" and "how to use test" would be very appreciated.

I've searched a little around the web, but cant quite find what i'am looking for.

Also from what i remember (something i read once or was told). Is that you can use test as a if statement.
```
[something \< something]#If this is true
    execute underlaying commands
else
    something else
```
But if someone could let me know if i remember correctly or not, then that would be great. And if you also can give a example on the above then that would be
appreciated.

Thanks on advance.
Kind regards.

---

### Post by Lars Noodén on 2013-02-04
The [manual page for test](http://manpages.ubuntu.com/manpages/precise/en/man1/test.1posix.html) will answer your questions about what it can do.  There is the full list of conditions it can test for.  

Here is an example using if-then.

```

if [ -f /etc/squid/squid.conf ]; then
  if [ -x /usr/local/sbin/squid ]; then
    /usr/local/sbin/squid;
    echo -n "squid ";
  fi
fi

```

In addition to using it with if-then statements in the shell, you can also use it with conditionals.

```

test -f /var/tmp/sometempfile.txt && rm /var/tmp/sometempfile.txt

```

---

### Post by iMac71 on 2013-02-04
give a look to the following guide:
[http://tldp.org/LDP/abs/html/testconstructs.html](http://tldp.org/LDP/abs/html/testconstructs.html)

---

### Post by schragge on 2013-02-04
It's the same as '[...]' construct.

[LIST]
[*][Bash Manual]("http://www.gnu.org/software/bash/manual/html_node/Bourne-Shell-Builtins.html#index-test").
[*][POSIX]("http://pubs.opengroup.org/onlinepubs/9699919799/utilities/test.html").
[*][test(1)]("http://manpages.ubuntu.com/manpages/precise/en/man1/test.1.html") manual page (it describes an external command that does the same as eponymous bash builtin).
[*][A chapter]("http://tldp.org/LDP/abs/html/testconstructs.html") from "Advanced Bash-Scripting Guide" discussing tests.
[/LIST]

---

### Post by Drenriza on 2013-02-04
> **Lars Noodén said:**
> The [manual page for test](http://manpages.ubuntu.com/manpages/precise/en/man1/test.1posix.html) will answer your questions about what it can do.  There is the full list of conditions it can test for.  

Here is an example using if-then.

```

if [ -f /etc/squid/squid.conf ]; then
  if [ -x /usr/local/sbin/squid ]; then
    /usr/local/sbin/squid;
    echo -n "squid ";
  fi
fi

```

In addition to using it with if-then statements in the shell, you can also use it with conditionals.

```

test -f /var/tmp/sometempfile.txt && rm /var/tmp/sometempfile.txt

```

Looked through the manual and didn't really find the answer to my question.

Example.
```
[ "$(echo $value1 | tr ' ' '\n' | grep ';${value2};')" ] && continue
[ "$value3" ] && [ "value4" != "1" ] && continue
```

(why would one use test in its bracket format this way? Whats the trick?)

What does the **&& continue** mean after test has done it's thing?
Continue (from what i know) means "skip" something.

Example
```

for line in {1..5}
do
if [$line -eq 2]
then
    continue
    #if $line equals 2, skip.
else
    echo $line
fi
done

```
So here 1,3,4,5 would be echoed and 2 would not. If i'am not totally mistaken.

Can test in it's bracket form be used as a if without an if in front of it?
As asked in #1

Thanks on advance.
Kind regards.

---

### Post by Drenriza on 2013-02-04
> **iMac71 said:**
> give a look to the following guide:
[http://tldp.org/LDP/abs/html/testconstructs.html](http://tldp.org/LDP/abs/html/testconstructs.html)

Thanks for the link, did already look at it tho. And still wondering how the following works
```
[ "$(echo $value1 | tr ' ' '\n' | grep ';${value2};')" ] && continue
[ "$value3" ] && [ "value4" != "1" ] && continue
```

Their must be a "trick" to why someone would do the above, without using an if in front of test in its bracket format.

---

### Post by schragge on 2013-02-04
'continue' means "go right to the next loop iteration skipping the rest of the loop body".

```
[ "$(echo $value1 | tr ' ' '\n' | grep ';${value2};')" ] && continue
```is the same as
```

if [ -n "$(grep ';$value2;' <<<"$value1")" ]
then continue
fi

``````
[ "$value3" ] && [ "value4" != "1" ] && continue
```is the same as
```

if [[ -n $value3 && $value4 != 1 ]]
then continue
fi

```

---

### Post by schragge on 2013-02-04
> **Drenriza said:**
> Their must be a "trick" to why someone would do the above, without using an if in front of test in its bracket format. No "trick". There's simply no difference if you use it as 'test' or in the bracket form. Both can be used either after 'if', or as simple commands in its own right.

---

### Post by ofnuts on 2013-02-04
> **Drenriza said:**
> Thanks for the link, did already look at it tho. And still wondering how the following works
```
[ "$(echo $value1 | tr ' ' '\n' | grep ';${value2};')" ] && continue
[ "$value3" ] && [ "value4" != "1" ] && continue
```Their must be a "trick" to why someone would do the above, without using an if in front of test in its bracket format.
The trick is that a successful command (rc=0) is true, and a failed command (rc!=0) is False, combined with the property of "&&" and "||" to not execute the operand on the right if the result is already known:

[LIST]
[*] " bad_command && next_command"  will not execute "next_command", because "bad_command" evaluates to "false", and whatever you "and" it with you'll always have "false",
[*]"good_command && next_command" will execute "next_command", because its result will determine the result of the "&&".
[*]For the same reason, "good_commmand || next_command" won't execute "next_command" ("true" or'ed with whatever is always "true")
[*]and "bad_command || next_command" will execute "next_command".
[/LIST]

---

### Post by Drenriza on 2013-02-04
> **schragge said:**
> No "trick". There's simply no difference if you use it as 'test' or in the bracket form. Both can be used either after 'if', or as simple commands in its own right.

Uhmmmmm

So if i have an example as follows
```

for line in $numbers
do
   [ $line -eq 2] && continue
   echo $line
done

```

Is the above the same as saying (and works the same)
```

for line in $numbers
   if [ $line -eq 2 ]
   then
      continue
   else
      echo $line
   fi
done

```
???

---

### Post by Drenriza on 2013-02-04
> **ofnuts said:**
> The trick is that a successful command (rc=0) is true, and a failed command (rc!=0) is False, combined with the property of "&&" and "||" to not execute the operand on the right if the result is already known:

[LIST]
[*] " bad_command && next_command"  will not execute "next_command", because "bad_command" evaluates to "false", and whatever you "and" it with you'll always have "false",
[*]"good_command && next_command" will execute "next_command", because its result will determine the result of the "&&".
[*]For the same reason, "good_commmand || next_command" won't execute "next_command" ("true" or'ed with whatever is always "true")
[*]and "bad_command || next_command" will execute "next_command".
[/LIST]

So in this example "continue" is only executed if test equal true (0)?

---

### Post by schragge on 2013-02-04
Strictly speaking, 
```

for line in $numbers
do
   [ $line -eq 2 ] && continue
   echo $line
done

``` is the same as
```

for line in $numbers
do
   if [ $line -eq 2 ]
   then
      continue
   fi
   echo $line
done

```But in this particular case that doesn't make a difference.

---

### Post by schragge on 2013-02-04
> **Drenriza said:**
> So in this example "continue" is only executed if test equal true (0)?Yes

---

### Post by Vaphell on 2013-02-04
bash simply executes minimal set of operations to calculate the logical value of the whole expression. In other words if it can skip some part without changing the logical value of the whole, it does it.
That means that just like ofnuts said **FALSE && whatever** is always FALSE (doesn't matter if *whatever* is TRUE or FALSE), so you don't have to check *whatever* at all in order to evaluate the whole expression, same thing with **TRUE || whatever** (always TRUE)

somewhat similar to normal addition and multiplication of natural numbers (assuming 0=FALSE, not0=TRUE, +=||, *=&& )
0*x always 0
not0+x always not0

---


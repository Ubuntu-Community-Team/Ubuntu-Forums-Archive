---
title: "bash: differentiating between '\n' and ' ' with for loops"
date: 2012-06-07
forum: Programming Talk
---

### Post by Keiran230 on 2012-06-07
This is a predicament I keep running into with bash scripts. I need to iterate though each line in a variable with for, but for likes to grab each word instead of each line:

Example bash one-liner
```
EXAMPLE=$(echo -e "line 1\nline 2\nline 3"); for LINE in `echo "$EXAMPLE"`;do echo "iteration: $LINE"; done; unset EXAMPLE
```

Actual Output:
```
iteration: line
iteration: 1
iteration: line
iteration: 2
iteration: line
iteration: 3
```

Intended Output:
```
iteration: line 1
iteration: line 2
iteration: line 3
```

If you're curious what i'm up to, check this out:
[http://keiran-whitehat.com/stuff/check_mem](http://keiran-whitehat.com/stuff/check_mem)

---

### Post by Keiran230 on 2012-06-07
Wow... I've been Googling this for forever, post the question, then Google one more time and find it.

```
while read -r line; do
    echo "... $line ..."
done <<< "$list"
```

I have no idea what's up with the triple <, but it works

---

### Post by papibe on 2012-06-07
Hi Keiran230.

By default 'for' uses separators defined in a bash variable called IFS. By defualt IFS contains 'whitespaces'.

If you run this to see its value:
```
echo -n "$IFS" | od -a
```
The result will be:
```
0000000  sp  ht  nl
0000003
```
That is 3 characters: space, tab and newline.

If you need just the newline as separator you can set it on IFS:
```
IFS=$'\n'
```
Note that it is a good practice to restore IFS's default value if you changed it:
```
OLDIFS="$IFS"
IFS=$'\n'

for ....

IFS="$OLDIFS"
```

Now, that being said. In you case you just need to quote your variables ;)
```
for LINE in "$EXAMPLE";do
    echo "iteration: $LINE"
done
```

I hope that helps, and tell us how it goes.
Regards.

---

### Post by sisco311 on 2012-06-09
BashFAQ 001 (link in my sig). ;)
and
[http://mywiki.wooledge.org/DontReadLinesWithFor](http://mywiki.wooledge.org/DontReadLinesWithFor)

<<< is a here string, see:
```
man bash | less +/'^ +Here Strings'
```
It's a BASHISM, you can't use it in other shells.
[http://mywiki.wooledge.org/Bashism](http://mywiki.wooledge.org/Bashism)

---


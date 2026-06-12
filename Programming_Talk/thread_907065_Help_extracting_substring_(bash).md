---
title: "Help extracting substring (bash)"
date: 2008-09-01
forum: Programming Talk
---

### Post by MattUK on 2008-09-01
Hi all,

I have a string that will be in the format:

"text 04x01 text"

The digits may be double or single, and I need to extract just the 04 in the example above, or basically the first number in the NNxNN part, whether thats single or double digits.

This is for a bash script.

Any ideas? I've tried a few things but I keep getting stuck with bash's lack of decent regex support..

---

### Post by ghostdog74 on 2008-09-01
there's no need for regular expression if you know how to work with fields
```

# s="text 04x01 text"
# set -- $s
# echo $1
text
# echo $2
04x01
# IFS="x"
# set -- $2
# echo $1
04
#         

```

it happens for other tools that works with fields,eg awk
```

# echo $s | awk '{split($2,a,"x");print a[1]}'
04


```

---

### Post by MattUK on 2008-09-01
Interesting, thanks :)

The only bit I don't understand is how come it doens't split on any x? e.g. split at the first x in text, to return te instead of the desired 04?

---

### Post by MattUK on 2008-09-01
OK.. I think set -- $s splits it at spaces first? then you're doing the split on the x on the section with the 04x01..

That may not work if the string is:

"Hello World 4x01 - This is a test"

I don't actually know what will be surrounding the 4x01. Anything can be done there? (keeping in mind the format is (\d{1,2})x\d{1,2} in perl regex..

---

### Post by MattUK on 2008-09-01
Trying to do this:

```

var="hello world - 4x01 - test"
number=$(`perl -e '"$var" =~ /(\d{1,2})x\d{1,2}/; print $1'`)
echo $number

```

But failing miserably.. any idea how I can get that to work?

---

### Post by odyniec on 2008-09-01
Why not use good old sed?
```
number=`echo $var|sed 's/.*\([0-9]\+\)x[0-9]\+.*/\1/'`
```

---

### Post by MattUK on 2008-09-01
Thanks! that works great.

---

### Post by MattUK on 2008-09-01
Quick followup question: Can you use sed in a similar way to see if a string matches a pattern? i.e. in an if statement

---

### Post by MattUK on 2008-09-01
Also, how would you express number of instances in sed? like with perl using {1,2} for 1 or 2 copies?

If I can clear those two up, I'll be away with sed :)

---

### Post by ghostdog74 on 2008-09-01
i suggest you read [this](http://www.grymoire.com/Unix/Sed.html) is you want to know more about sed.

---

### Post by forger on 2008-09-01
Perl:
```
VAR="hello world - 4x01 - test"
number="`perl -e '$a = "$ARGV[0]"; $a =~ m/(\d{1,2})x\d{1,2}/; print $1;' "$VAR"`"
echo $number

```

or without quotes around number
```
VAR="hello world - 4x01 - test"
number=`perl -e '$a = "$ARGV[0]"; $a =~ m/(\d{1,2})x\d{1,2}/; print $1;' "$VAR"`
echo $number
```

Or bash with cut:
```
echo "hello world - 4x01 - test" | cut -d ' ' -f 4 | cut -d 'x' -f 1
```
(d=delimiter/separator,f=field to return)

---

### Post by MattUK on 2008-09-01
Thanks guys, its starting to make a bit more sense as I go - heh :)

---

### Post by stylishpants on 2008-09-01
For the record, the perl solution was like this:

```
$ var="hello world - 4x01 - test"

# Interpolate the bash variable directly into the perl code -- requires perl
# code to be encapsulated in double quotes, not single quotes, so bash will
# perform substitution inside the string before passing it to perl.  Note that
# this requires the $ in $1 to be escaped so bash will leave it alone.

$ number=$(perl -e "'$var' =~ /(\d{1,2})x\d{1,2}/; print \$1")
$ echo $number
4


# Avoid letting bash do substitution within your perl string by passing the
# input string to perl through a pipe -- this is slightly longer but easier to
# not screw up.

$ number=$(echo $var | perl -ne '/(\d{1,2})x\d{1,2}/; print $1')
$ echo $number
4



```

---


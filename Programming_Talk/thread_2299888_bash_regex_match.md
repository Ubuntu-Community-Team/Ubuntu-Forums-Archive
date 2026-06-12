---
title: "bash regex match"
date: 2015-10-22
forum: Programming Talk
---

### Post by maclenin on 2015-10-22
Within a bash script, I'd like to match 12345 in this file name / string:

test_12345

This does the trick (in one way):
```
a=test_12345
b=${a:5:9}
echo ${b} # 12345
```
However, I'd also like to be able to do it in this way:
```
b=${a:'[0-9]+'}

```
Thanks for any clarity!

---

### Post by Vaphell on 2015-10-22
the problem is that bash doesn't really support regexes and its native globs are functionally a barebone subset of true regexes. There is also an extended variant of globs but they still fall short. That means that you generally need to look for help outside pure bash, eg in sed or grep.
That said there is one place where true regexes are native, that can be used to achieve desired result without farming the job out to sed/perl/grep/awk or whatever
That place is **[[ ]]** combined with **=~**. It is a test against a regex and the details of the match are stored in BASH_REMATCH array. ${BASH_REMATCH[0]} is the whole match, indices 1+ are capturing groups if any were used.

```
$ a=test_12345
$ [[ $a =~ [0-9]+ ]]
$ for((i=0; i<${#BASH_REMATCH[@]}; i++)); do echo "BASH_REMATCH[$i]: ${BASH_REMATCH[i]}"; done
BASH_REMATCH[0]: 12345
```

only 1 item here, the whole matching sequence.

```
$ [[ $a =~ ([a-z]+)_([0-9]+) ]]
$ for((i=0; i<${#BASH_REMATCH[@]}; i++)); do echo "BASH_REMATCH[$i]: ${BASH_REMATCH[i]}"; done
BASH_REMATCH[0]: test_12345
BASH_REMATCH[1]: test
BASH_REMATCH[2]: 12345

```

the whole sequence plus 2 capturing groups.

---

### Post by maclenin on 2015-10-24
Perfect! Thank you!

I had, actually, been looking to post a link to (almost) exactly what you've articulated - but your answer arrived too quickly (and far more thoroughly)....

So:

[[ $a = 0 ]] = BASH_REMATCH[0]
[[ $a = ( 0 (1)_(2)  ) ]] = BASH_REMATCH[0], BASH_REMATCH[1], BASH_REMATCH[2]
[[ $a = (1) ]] = BASH_REMATCH[0]? or BASH_REMATCH[1]? or would one not use a capture group for a "single" regex "match" - so (1) would be BASH_REMATCH[0]?

One question, however:

What if the same bash script sees multiple [[]] instances - for $a, $b, $c and so on...would the BASH_REMATCH array simply "push()" to accommodate $b and $c...appending BASH_REMATCH[3] and BASH_REMATCH [4], and so on?

Thanks, again, for the wisdom!

---

### Post by Vaphell on 2015-10-26
> 
[[ $a = (1) ]] = BASH_REMATCH[0]? or BASH_REMATCH[1]? or would one not use a capture group for a "single" regex "match" - so (1) would be BASH_REMATCH[0]?


both [0] and [1]. It doesn't matter that they have the same value.

```
$ [[ '123' =~ (1) ]] && printf '%s\n' "${BASH_REMATCH[@]}"
1                 total match
1                 capturing group match
```  

> What if the same bash script sees multiple [[]] instances - for $a, $b, $c and so on...would the BASH_REMATCH array simply "push()" to accommodate $b and $c...appending BASH_REMATCH[3] and BASH_REMATCH [4], and so on?

some example of what you have in mind? Either way that array is a side effect of =~ and gets repopulated with each test. You don't have much control over it. You'd have to append elems by hand to some array you control. For example


```
$ my_stuff=()
$ [[ 'aa_bb' =~ ([a-z]+)_([a-z]+) ]] && my_stuff+=( "${BASH_REMATCH[@]:1}" )
$ [[ 'lol_wut' =~ ([a-z]+)_([a-z]+) ]] && my_stuff+=( "${BASH_REMATCH[@]:1}" )
$ printf '%s\n' "${my_stuff[@]}"
aa
bb
lol
wut
```

my_stuff is an array to which i appended all capturing groups of a given match

---

### Post by maclenin on 2015-10-26
I was more interested in understanding how without having any specifics in mind - and your "my_stuff=()" clarified!

...so if I were desperate to lol, I'd simply:
```
$ printf '%s\n' "${my_stuff[2]}"
```

...in this example, how do I print only 12 ([0] or [@]:0:1)?
```
$ [[ '123' =~ (1)2 ]] && printf '%s\n' "${BASH_REMATCH[@]:1}"
1

```

...this seems to "miss" adding aa_bb to my_stuff() -  unless the intention is to collect the matching groups only?
```
$ my_stuff=()
$ [[ 'aa_bb' =~ ([a-z]+)_([a-z]+) ]] && my_stuff+=( "${BASH_REMATCH[@]:1}" )
```

---

### Post by Vaphell on 2015-10-26
> .in this example, how do I print only 12 ([0] or [@]:0:1)?

well, both methods are logically equivalent, so whatever blows your hair back. Direct index is simpler though.

and yes, my example dealt with capturing groups only,  0-th element was intentionally skipped with [@]:1. My experience with capturing groups I guess - usually when I use them I am only interested in groups contents specifically and you can always rebuild the whole thing from submatches, so full match is kinda redundant to have in a tidy collection of extracted data.

---


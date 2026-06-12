---
title: "bash script"
date: 2014-02-11
forum: Programming Talk
---

### Post by Drenriza on 2014-02-11
Hi all.

If i wanted to make a script that can automatically generate a sequence of numbers with the following rules.

#1 The number can be no longer or less than 10 digits long.
#2 The first two digits needs to be the day of month, 01-31.
#3 The next two digits needs to be the month of year, 01-12.
#4 The next two digits needs to be the last two digits of the current year starting from 1970. Example for 2003 it would be 03.
#5 The next two digits needs to be a number a auto generated number between 01-99
#6 The last two digits needs to be a auto generated number between 01-99.

Where i also can say "generate 100 sequences" or "generate 1000", print it out to two different files for odd and even numbers in the last two digits, with a HTML tag sourounding the sequence.

Example
<p>190590-3132</p>

How would one do so?

Thanks on advance.
Kind regards.

---

### Post by ofnuts on 2014-02-11
This looks  a lot like homework, which is forbidden by the forum rules.

Otherwisen it looks like what you need is some random date from 01/01/1970 (properly formatted) followed two random numbers. It happens that 01/01/1970 is the start of the "epoch" (see what "date -d @0" outputs). Wink, wink, nudge, nudge.

---

### Post by Vaphell on 2014-02-11
given that epoch time is a signed 32bit int and bash $RANDOM yields a 15bit int, you might need this

```
rnd=$(( (RANDOM%2)<<30 | RANDOM<<15 | RANDOM ))
```

---

### Post by Drenriza on 2014-02-11
> This looks  a lot like homework, which is forbidden by the forum rules.

Otherwisen it looks like what you need is some random date from  01/01/1970 (properly formatted) followed two random numbers. It happens  that 01/01/1970 is the start of the "epoch" (see what "date -d @0"  outputs). Wink, wink, nudge, nudge.

Its not homework ,)

It's a dispute between the IT people + companies and over "dear" politicians.
Over social policy numbers which was stolen last year from over goverment mainframe, along with corrosponding names.
In which the IT people has reacted to create a new system and want to reveil all existing numbers with names to the public. 
Which also makes sense when you know the system.

The reason i ask for the script, is a running joke between the IT people and the politicians here.

Its a really long issue stretching back years, so if i was to explain it, it would take _**a lot**_ of lines xD

---

### Post by Vaphell on 2014-02-11
generate in some order or random conforming strings?

---

### Post by ofnuts on 2014-02-11
> **Vaphell said:**
> given that epoch time is a signed 32bit int and bash $RANDOM yields a 15bit int, you might need this

```
rnd=$(( (RANDOM%2)<<30 | RANDOM<<15 | RANDOM ))
```

You only need dates between epoch and now, so:

```

# in slow motion...
now=$(date +%s)
randomtimestamp=$(shuf -i0-$now -n1)
ddmmyy=$(date -d @$randomtimestamp +%d%m%y)

```

The last two number pairs are left as an exercise to the user.

---

### Post by Drenriza on 2014-02-11
> **Vaphell said:**
> generate in some order or random conforming strings?

Random, just aslong as the "rules" in #0 are kept.

---

### Post by Vaphell on 2014-02-11
pure bash + date
```
#!/bin/bash

n="$1"
out=( even.txt odd.txt )
now=$( date +%s )

for r in 0 1
do
  c=0
  while (( c<n ))
  do
    rnd=$(( (RANDOM%2)<<30 | RANDOM<<15 | RANDOM ))
    (( rnd>now )) && continue
    d=$( date -d @"$rnd" +%d%m%y )
    x=$(( RANDOM%99+1 ))
    y=$(( (RANDOM%(49+r))*2+2-r ))
    printf "<p>%s-%02d%02d</p>\n" "$d" "$x" "$y"
    (( c++ ))
  done > "${out[$r]}"
done
```

> ```
# in slow motion...
now=$(date +%s)
randomtimestamp=$(shuf -i0-$now -n1)
ddmmyy=$(date -d @$randomtimestamp +%d%m%y)
```

granted it doesn't matter much, but running shuf in loop only to get 1 number is dog slow due to the overhead and loses to pure bash hardcore. It becomes lightning fast only when you do this
```
while read -r rnd; do ...; done < <( shuf -i0-$now -n100000 )
```

```
$ c=0; now=$( date +%s ); time while (( c<100000 )); do x=$(( (RANDOM%2)<<30 | RANDOM<<15 | RANDOM )); (( c++ )); done

real	0m1.938s
user	0m1.944s
sys	0m0.000s
$ c=0; now=$( date +%s ); time while read -r rnd; do :; done < <( shuf -i 0-$now -n[COLOR="#0000FF"]100000[/COLOR] )

real	0m1.169s
user	0m0.920s
sys	0m0.276s

$ c=0; now=$( date +%s ); time while (( c<[COLOR="#0000FF"]1000[/COLOR] )); do x=$( shuf -i0-$now -n1 ); (( c++ )); done

real	0m1.189s
user	0m0.112s
sys	0m0.184s
```

2 orders of magnitude

---


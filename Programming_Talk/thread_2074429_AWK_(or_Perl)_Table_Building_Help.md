---
title: "AWK (or Perl) Table Building Help"
date: 2012-10-21
forum: Programming Talk
---

### Post by drmrgd on 2012-10-21
Once again, I spent most of the day trying to build a new table from components of an old table that looks a something like this:

```
track name="MPACT_Custom_Panel(IAD27536)_HotSpots_v2.0" description="HotSpots BED File for the MPACT Custom Amplicon Panel v2.0"     type=bedDetail
chr1    11169360        11169361        COSM26975       REF=C;OBS=G;ANCHOR=C    AMPL535569155
chr1    11169725        11169726        COSM13324       REF=G;OBS=A;ANCHOR=C    AMPL535311535
chr1    11174457        11174458        COSM51966       REF=A;OBS=G;ANCHOR=G    AMPL535573086
```

From this, after deleting the first line, which I could probably do with a sed command, I need columns (in order) columns 1, 3, 5, and 4.  That's easy enough.  However, the problem is that I need a subset of $5 for each line.  For each line, sometimes OBS= is null, and in that case, I want to print the character from REF=. 

I can get the correct output for that field with a simple if statement:

```
awk '
        # Get the simple base; either REF or OBS depending on deletion or not
        {
                { FS="="; }
                { if ($3 ~ /^\;/)
                        print substr($2,0,index($2,";")-1);
                else
                        print substr($3,0,index($3,";")-1);
                }
        }
        ' $1
```

However, I can't seem to figure out how to then add in the rest of the fields for every line so that I end up with something like this:

```
chr1    11169361    G        COSM26975
chr1    11169726    A        COSM13324
chr1    11174458    G        COSM51966

```

I tried to alter $5 on the fly, but couldn't get that to work.

Then I tried to build out an associative array with the values, which just ended up being a hot mess and not giving me what I wanted:

```
function simpleHotspot {
        base=$(awk '
        # Get the simple base; either REF or OBS depending on deletion or not
        {
                { FS="="; }
                { if ($3 ~ /^\;/)
                        print substr($2,0,index($2,";")-1);
                else
                        print substr($3,0,index($3,";")-1);
                }
        }
                ' testlist.txt)
}

function hotSpotRest {
        line="$(sed '1d' testlist.txt | awk '{ print $1,$3,$4 }')"
}

simpleHotspot
hotSpotRest

for ((i=0; i<${#line[@]}; i++));
do
        for ((j=0; j<${#base[@]}; j++))
        do
                list+=(${line[i]}:${base[j]});
        done
done

for i in ${list[@]}
do
        echo $i
done
```

What am I missing here?  Although I don't know Perl well at all, would this be easier to do with a Perl script?

---

### Post by Vaphell on 2012-10-21
```
awk 'NR>1 { split( $5, a, "=|;" ); print $1, $3, (a[4]=="")?a[2]:a[4], $4; }'
```

what split() does:
```
echo "REF=A;OBS=;ANCHOR=G" | awk '{ n=split($1,array,"=|;"); for(i=1;i<=n;i++) print i, array[i]; }'
1 REF
2 A
3 OBS
4 
5 ANCHOR
6 G

```

---

### Post by drmrgd on 2012-10-21
Ahhhh!!! This is a bit frustrating!  After spending all day and pages of code trying to parse this stupid file, you did it in 5 seconds with the shortest and most elegant awk statement I've seen so far.  I really need to get better at this.  The one-liner works beautifully.  Thank you!!!

I tried split early on, but couldn't figure out what field separator to use.  I never thought to use "=|;" like that.  I think I could have built the array correctly if I could have figured out how to split the line.  Another great tip and trick to add to my toolbox!

Thank you again Vaphell!  You are really teaching me a lot!

---

### Post by Vaphell on 2012-10-21
i admit it's the first time i see or use split() :) my first thought was 'i wonder if the separator does OR, that would make it easy...' and it worked :D
either way i'd use split, up to 3 times.

```
REF=A;OBS=;ANCHOR=G: split using ';'
a[1]: split using '=' and save the second part as ref
a[2]: split using '=' and save the second part as obs

(obs=="")?ref:obs
```

FS approach imho was a no-go from the start. It had to be something that is limited to the scope of a single string and using FS here was like nuking the ant.

---

### Post by drmrgd on 2012-10-21
> **Vaphell said:**
> i admit it's the first time i see or use split() :) my first thought was 'i wonder if the separator does OR, that would make it easy...' and it worked :D
either way i'd use split, up to 3 times.

```
REF=A;OBS=;ANCHOR=G: split using ';'
a[1]: split using '=' and save the second part as ref
a[2]: split using '=' and save the second part as obs

(obs=="")?ref:obs
```

FS approach imho was a no-go from the start. It had to be something that is limited to the scope of a single string and using FS here was like nuking the ant.

Yeah, I couldn't figure out how to use split quite right (throwing an 'or' at it was very clever!) and then dug myself a hole trying to work my way out of using FS.  That's the reason for my follow up ugly regex.  Your nuking an ant analogy, I think, is spot on!  I'll stick with rolled up newspapers from now on I think (I hope!).

---

### Post by Vaphell on 2012-10-22
just for kicks, similar thing with sed (assuming ref and obs are max 1 char long)
```
sed -r '1d;
        s/^([^ ]+) +([^ ]+) +([^ ]+) +([^ ]+) +REF=(.?);OBS=(.?);[^ ]+ +[^ ]+$/\1 \3 \6\5 \4/;
        s/(^[^ ]+ [^ ]+ .).?( [^ ]+)/\1\2/'
```

---


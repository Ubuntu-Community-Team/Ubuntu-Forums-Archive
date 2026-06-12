---
title: "sed matching within a line"
date: 2011-09-20
forum: Programming Talk
---

### Post by hailholyghost on 2011-09-20
Hello all :guitar:

I want to extract numbers/coordinates from files named like 

optppa18X270.49E179.970Z180.860.out

like grep would do, except *within* a single line.

For example, I would like to print *after* ppa and *before* the letter E, after E and before Z, and after Z but before .out.

I cannot find how to do this with sed or awk.  If there is a way, how can I do it?

thanks for your expertise!:popcorn:
-Dave

---

### Post by hailholyghost on 2011-09-20
I actually solved this on my own, the first coordinate is shown as follows:

```
#!/bin/bash

#extract energies from a dihedral scan

for i in $(ls optppa*.out)
do
	PPA="$(ls $i | sed -e 's/^o.*a//g' -e 's/X.*out//g')"
	ENERGY="$(grep RwB97XD optppa18X260.49E179.970Z180.860.out | awk '/SCF/{print $5}')"
	echo $PPA

done
```

---

### Post by sisco311 on 2011-09-20
ls shows the representation of files. They are not file names. For simple names, they mostly happen to be equivalent. So, do NOT try to parse it. See: [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

In most cases you can use parameter expansion instead of *echo "$var" | sed ...*. See: [http://mywiki.wooledge.org/BashSheet#Parameter_Operations](http://mywiki.wooledge.org/BashSheet#Parameter_Operations)

There is no need to pipe grep in awk: *awk '/FOO/ && /BAR/{whatever}' file*

You should double quote every expansion and anything that could possibly contain a special character: echo "$ppa". See: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

By convention, we capitalize environment variables (PAGER, EDITOR, SHELL, ...) and internal shell variables (BASH_VERSION, RANDOM, ...). All other variable names should contain at least one lowercase letter. Remember that variable names are case-sensitive; this convention avoids accidentally overriding environmental and internal variables.


```

for f in optppa*.out
do
    f="${f#optppa}"
    ppa="${f%%X*.out}"
    energy="$(awk '/RwB97XD/&&/SCF/{print $5}' "$f")"
    echo "$ppa"
done

```

---

### Post by Vaphell on 2011-09-20
if you want to extract multiple parts from string with single sed you can use subgroups

```
$ echo optppa18X270.49E179.970Z180.860.out | sed -r 's/[a-zA-Z]*[COLOR="Navy"](.*)[/COLOR]X[COLOR="Navy"](.*)[/COLOR]E[COLOR="Navy"](.*)[/COLOR]Z[COLOR="Navy"](.*)[/COLOR][.]out/[COLOR="Navy"]\1[/COLOR] : [COLOR="Navy"]\2[/COLOR] : [COLOR="Navy"]\3[/COLOR] : [COLOR="Navy"]\4[/COLOR]/'
18 : 270.49 : 179.970 : 180.860

```

each pair of parentheses gets an index that can be used to call it in the replacement part
we have 4 pairs here so \1 \2 \3 and \4

---

### Post by sisco311 on 2011-09-20
> **Vaphell said:**
> if you want to extract multiple parts from string with single sed you can use subgroups

```
$ echo optppa18X270.49E179.970Z180.860.out | sed -r 's/[a-zA-Z]*[COLOR="Navy"](.*)[/COLOR]X[COLOR="Navy"](.*)[/COLOR]E[COLOR="Navy"](.*)[/COLOR]Z[COLOR="Navy"](.*)[/COLOR][.]out/[COLOR="Navy"]\1[/COLOR] : [COLOR="Navy"]\2[/COLOR] : [COLOR="Navy"]\3[/COLOR] : [COLOR="Navy"]\4[/COLOR]/'
18 : 270.49 : 179.970 : 180.860

```

each pair of parentheses gets an index that can be used to call it in the replacement part
we have 4 pairs here so \1 \2 \3 and \4

Nice. And the output can be stored in an array:
```
{ IFS=: read -a arr <  <(echo optppa18X270.49E179.970Z180.860.out | sed -r 's/[a-zA-Z]*(.*)X(.*)E(.*)Z(.*)[.]out/\1 : \2 : \3 : \4/'); }
echo "${arr[0]}"
echo "${arr[1]}"
echo "${arr[2]}"
echo "${arr[3]}"

```

---

### Post by hailholyghost on 2011-09-20
Thank you so much sisco311 and Vaphell!

sisco: I took to hear the grep | awk advice you gave to me a while ago, and I implemented it, but I didn't know that they could be linked together with &&.  I guess you learn new things every day!

Vaphell: thanks for pointing the subgroups out.

I will study the links and advice you've given.  I appreciate your time!

---

